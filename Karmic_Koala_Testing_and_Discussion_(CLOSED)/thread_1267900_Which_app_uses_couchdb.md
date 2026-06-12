---
title: "Which app uses couchdb?"
date: 2009-09-16
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by MacUntu on 2009-09-16
I haven't seen this on an upgraded system but with a fresh Karmic install I got this couchdb thing installed and I cannot figure out which app uses couchdb. Starting it takes like a second during boot and I'm pretty sure I don't need it.

The only reverse dependent package that's installed is python-couchdb and non of this package's reverse dependent packages is installed - I'm confused. Using Synaptic to search for dependencies, ubuntu-desktop shows up but it doesn't directly depend on/recommend couchdb/python-couchdb.

Any ideas?

---

### Post by lucazade on 2009-09-16
I believe was evolution-related, maybe i'm wrong!

---

### Post by zekopeko on 2009-09-16
It looks like the app that use couchdb aren't yet built with support for couchdb. They should enable it a few days.

---

### Post by 23meg on 2009-09-16
[QUOTE=MacUntu]I haven't seen this on an upgraded system but with a fresh Karmic install I got this couchdb thing installed and I cannot figure out which app uses couchdb.[/QUOTE]

*desktopcouch* and *evolution-couchdb* require it.

---

### Post by tekstr1der on 2009-09-16
couchdb is a dependency of desktopcouch which is a depedency of evolution-couchdb, which is now a dependency of ubuntu-desktop. I would say evolution is your answer.

---

### Post by Paqman on 2009-09-16
AFAIK the idea is to get CouchDB onto every machine, so that devs can make use of it for whatever they want.

[https://wiki.ubuntu.com/MeetingLogs/devweek0909/CouchDB](https://wiki.ubuntu.com/MeetingLogs/devweek0909/CouchDB)

From the sound of it Ubuntu One might be one of the first apps you see using it.

---

### Post by 23meg on 2009-09-16
> **Paqman said:**
> AFAIK the idea is to get CouchDB onto every machine, so that devs can make use of it for whatever they want.

[https://wiki.ubuntu.com/MeetingLogs/devweek0909/CouchDB](https://wiki.ubuntu.com/MeetingLogs/devweek0909/CouchDB)

From the sound of it Ubuntu One might be one of the first apps you see using it.

It can be used to store and sync [Evolution contacts]("http://www.kryogenix.org/days/2009/06/19/using-couchdb-to-store-contacts") and [Firefox bookmarks]("http://www.kryogenix.org/days/2009/07/06/firefox-bookmarks-in-couchdb"), through evolution-couchdb and Bindwood respectively. I've been testing them for a while - the best part is that you don't need a cloud service such as Ubuntu One to sync data across your machines; it works just as fine on your local network.

More on Desktop Couch:

[http://www.kryogenix.org/days/2009/07/09/desktop-couch-initial-code](http://www.kryogenix.org/days/2009/07/09/desktop-couch-initial-code)

---

### Post by MacUntu on 2009-09-16
Thanks for all your answers and links!

---

### Post by VMC on 2009-09-16
> **MacUntu said:**
> Thanks for all your answers and links!

This might help in the future. Aptitude is a great tool:
[B]$ aptitude show couchdb
[/B]```
Package: couchdb
State: not installed
Version: 0.10.0~svn813472-0ubuntu1
Priority: optional
Section: misc
Maintainer: Ubuntu MOTU Developers <ubuntu-motu@lists.ubuntu.com>
Uncompressed Size: 2044k
Depends: libc6 (>= 2.3.6-6~), libcurl3 (>= 7.16.2-1), libicu40 (>= 4.0-1),
         erlang-base (>= 1:13.b.1-dfsg) | erlang-base-hipe (>= 1:13.b.1-dfsg),
         erlang-crypto (>= 1:13.b.1-dfsg), erlang-inets (>= 1:13.b.1-dfsg),
         erlang-xmerl (>= 1:13.b.1-dfsg), erlang-abi-13.a, adduser,
         libjs-jquery, lsb-base, xulrunner-1.9.1
Description: RESTful document oriented database
 Apache CouchDB is a distributed, fault-tolerant and schema-free
 document-oriented database accessible via a RESTful HTTP/JSON API. Among other
 features, it provides robust, incremental replication with bi-directional
 conflict detection and resolution, and is queryable and indexable using a
 table-oriented view engine with JavaScript acting as the default view
 definition language. 
 
 CouchDB is written in Erlang, but can be easily accessed from any environment
 that provides means to make HTTP requests. There are a multitude of third-party
 client libraries that make this even easier for a variety of programming
 languages and environments.
Homepage: http://couchdb.apache.org/

```

---

### Post by MacUntu on 2009-09-16
How would that have helped me? :)

---

### Post by VMC on 2009-09-16
> **MacUntu said:**
> How would that have helped me? :)

You were asking about CouchDB. It's a data base. Did you see the homepage listing at the bottom of aptitude output:
 [http://couchdb.apache.org/](http://couchdb.apache.org/)

---

### Post by Paqman on 2009-09-16
> **23meg said:**
> It can be used to store and sync [Evolution contacts]("http://www.kryogenix.org/days/2009/06/19/using-couchdb-to-store-contacts") and [Firefox bookmarks]("http://www.kryogenix.org/days/2009/07/06/firefox-bookmarks-in-couchdb"), through evolution-couchdb and Bindwood respectively.

Awesome. Bye-bye Xmarks!

---

### Post by FuturePilot on 2009-09-16
> **23meg said:**
> the best part is that you don't need a cloud service such as Ubuntu One to sync data across your machines; it works just as fine on your local network.


Wow, that sounds awesome! :D

---

### Post by castrojo on 2009-09-16
> **MacUntu said:**
> Starting it takes like a second during boot and I'm pretty sure I don't need it.

Right now couch is accidentally starting xulrunner(!), which really sucks for boot time, there's a bug filed and the ubuntuone guys are working on it.

[https://bugs.edge.launchpad.net/desktopcouch/+bug/427036](https://bugs.edge.launchpad.net/desktopcouch/+bug/427036)

---

### Post by MacUntu on 2009-09-16
Damn how good I started this thread. Thanks! :D

---

### Post by DougieFresh4U on 2009-09-17
Current update wants to remove **couchdb**
Do I really need this package?

---

