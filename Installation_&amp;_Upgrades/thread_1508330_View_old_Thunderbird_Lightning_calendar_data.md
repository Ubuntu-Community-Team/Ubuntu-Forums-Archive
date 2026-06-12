---
title: "View old Thunderbird Lightning calendar data"
date: 2010-06-12
forum: Installation &amp; Upgrades
---

### Post by njsharp on 2010-06-12
I have just migrated my main work from 9.04 on a Toshiba Satellite A10 to using 10.04 64bit on a Dell Dimension 9150.  (Aside: I tried 10.04 on the Toshiba first, but hacked my shins on the 855GM problem, so decided it was time to retire the Toshiba to being my house firewall, which runs Centos, but that's another story!)

I decided to go cold turkey, rather than prepare for the transfer for ever, but I've put the Toshiba disk into a 2.5" IDE external USB enclosure (AU$19!), so it is totally accessible from the Dell.

I've lots more left to do, but today's fun was to view the old Thunderbird Lightning calendar data, and review it by hand.  I knew it was littered with trash, so I did NOT want to do an automatic conversion.

I got over the issue of a 64 bit Lightning to go with the 10.04 repository Thunderbird.  Go Google for that - it's not hard.

Then I wanted to look at the old calendar data.  In my old version it was on the old disk as
~/.mozzila-thunderbird/<8chars>.default/storage.sdb
where ~ is home directory of course, and <8chars>.default is the main folder, in my case 439w7c8x.default
YMWV (your mileage WILL vary!)

I then installed the beautiful Sqliteman tool from the standard 10.04 repo:

 Sqliteman - SQLite databases made easy
Version 1.2.1
 (c) 2007 Petr Vanek

NICE one Petr!  That allowed me to open and view storage.sdb which is a sqlite database.  Not that it matters in this thread, but it is 13 tables whereas the new version has 11 tables and is in:
~/.thunderbird/<8chars>.default/calendar-data/local.sqlite
Both have the cal_events table, which is the data I wanted.

On the left pane, click the triangles against 'main' then 'tables'.

Just double clicking on cal_events brings up the entire contents of the table in the bottom right window

Clicking on the top left (blank) box of that window (where the titles row intersects with the row number column) selects the whole table, just like in OO CALC.  Press CTRL C to copy.

Paste into a new OO CALC sheet at A1 (using TAB separator) to get the entire data as a spreadsheet.

If you want to view the date/time fields (format: UNIXTIME in microseconds), divide by 86400000000 (micro seconds in a day), add 25569 (to convert from UNIXTIME to days since 1900-01-01), and custom format eg as YYYY-MM-DD HH:MM:SS (I'm an ISO date 24hr time fanatic).

EG: where C2=1.174784302E+015
C2/86400000000+25569 formatted as YYYY-MM-DD HH:MM:SS
shows: 
2007-03-25 00:58:22
                                    
Now I can browse through my entire, but rather trashy old calendar entries, and key in new ones for the events that still matter in my life.

I rather enjoyed that, tortuous though it may seem, and hope it helps someone else.

---

