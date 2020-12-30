# テーブル設計

## users テーブル

| Column     | Type   | Options     |
| ---------- | ------ | ----------- |
| name       | string | NOT NULL    |
| email      | string | NOT NULL    |
| password   | string | NOT NULL    |
| profile    | text   | NOT NULL    |
| occupation | text   | NOT NULL    |
| position   | text   | NOT NULL    |

### Association

- has_many :prototypes
- has_many :comments

## prototypes テーブル

| Column     | Type       | Options                     |
| ---------- | ---------- | --------------------------- |
| title      | string     | NOT NULL                    |
| catch_copy | text       | NOT NULL                    |
| concept    | text       | NOT NULL                    |
| user       | references | NOT NULL, foreign_key: true |

### Association

- belongs_to :user
- has_many :comments

## comments テーブル

| Column    | Type       | Options                     |
| --------- | ---------- | --------------------------- |
| text      | text       | NOT NULL                    |
| user      | references | NOT NULL, foreign_key: true |
| prototype | references | NOT NULL, foreign_key: true |

### Association

- belongs_to :user
- belongs_to :prototype