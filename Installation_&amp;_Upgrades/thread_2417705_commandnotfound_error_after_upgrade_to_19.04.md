---
title: "commandnotfound error after upgrade to 19.04"
date: 2019-04-26
forum: Installation &amp; Upgrades
---

### Post by gjansen2 on 2019-04-26
After upgrade to 19.04 I get an ugly traceback every time I make a typo on the command line. I fixed the problem with the following command, but after the next aptitude update the db file was once again not readable for non-root users.

sudo chmod a+r /var/lib/command-not-found/commands.db

---------------------------------------------------------------------------
Sorry, command-not-found has crashed! Please file a bug report at:
[https://bugs.launchpad.net/command-not-found/+filebug](https://bugs.launchpad.net/command-not-found/+filebug)
Please include the following information with the report:

command-not-found version: 0.3
Python version: 3.7.3 final 0
Distributor ID:	Ubuntu
Description:	Ubuntu 19.04
Release:	19.04
Codename:	disco
Exception information:

unable to open database file
Traceback (most recent call last):
  File "/usr/lib/python3/dist-packages/CommandNotFound/util.py", line 23, in crash_guard
    callback()
  File "/usr/lib/command-not-found", line 89, in main
    cnf = CommandNotFound.CommandNotFound(options.data_dir)
  File "/usr/lib/python3/dist-packages/CommandNotFound/CommandNotFound.py", line 81, in __init__
    self.db = SqliteDatabase(dbpath)
  File "/usr/lib/python3/dist-packages/CommandNotFound/db/db.py", line 12, in __init__
    self.con = sqlite3.connect(filename)
sqlite3.OperationalError: unable to open database file

---

### Post by gjansen2 on 2019-04-26
I cannot file a bug report because when I try to log in to launchpad I get:

 [h=1]Oops![/h][COLOR=#333333][FONT=Ubuntu]Sorry, something just went wrong in Launchpad.[/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu]We&#8217;ve recorded what happened, and we&#8217;ll fix it as soon as possible. Apologies for the inconvenience.[/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu](Error ID: OOPS-6ff9c6402ac4d288436e88ce86a330b2)[/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu]
[LIST]
[*][Return to the Launchpad front page]("https://launchpad.net/")
[/LIST]
[/FONT][/COLOR]

---

