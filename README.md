# README

This README would normally document whatever steps are necessary to get the
application up and running.

Things you may want to cover:

* Ruby version

* System dependencies

* Configuration

* Database creation

* Database initialization

* How to run the test suite

* Services (job queues, cache servers, search engines, etc.)

* Deployment instructions

* ...
## usersテーブル

|column|Type|Options|
|------|----|-------|
|name|string|null: false|
|Email|string|null: false, unique: true|
|password|string|null: false|
|group_id|integer|null: false, foreign_key: true|

### Association
* has_many :groups,through::users_groups
* has_many :messages
* has_many :users_groups

## messagesテーブル

|column|Type|Options|
|------|----|-------|
|body|text|null: false|
|image|string|null: false|
|group_id|integer|null: false, foreign_key: true|
|user_id|integer|null: false, foreign_key: true|

### Association
* belongs_to :group
* belongs_to :user

## groupsテーブル

|cloumn|Type|Options|
|------|----|-------|
|name|string|null: false|
|user_id|integer|null: false,foreign_key: true|
 
### Association
* has_many :message,through: :users_groups
* has_many :users
* has_many :users_groups

## users_groupsテーブル

|colomn|Type|Options|
|------|----|-------|
|users_id|integer|null: false, foreign_key: true|
|groups_id|integer|null: false, foreign_key: true|

### Assciation
* belongs_to :group
* belongs_to :user