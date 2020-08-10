#### Домашнее задание по теме «Работа с PostgreSQL. Создание БД»
студент: Сергей Романов

группа: SQLPY-1
```
create table if not exists Genre (
	GenreID integer unique,
	GenreName varchar(20) unique
);

create table if not exists Artist (
	ArtistID serial primary key,
	Name varchar(20) unique,
	GenreID integer references Genre(GenreID)
);

create table if not exists Album (
	AlbumID integer unique,
	AlbumName varchar(40) not null,
	Year integer check(Year > 1887),
	ArtistID integer references Artist(ArtistID)
);

create table if not exists Track (
	TrackID integer unique,
	TrackName varchar(30) not null,
	TrackLength integer not null,
	ArtistID integer references Artist(ArtistID),
	AlbumID integer references Album(AlbumID)	
)
```