---
title: "GUIDE for people WITHOUT BROADBAND and their firends wiTH BORADBAND"
date: 2005-10-29
forum: Installation &amp; Upgrades
---

### Post by kakashi on 2005-10-29
people without broadband have many issuses running linux like slow download and problems installing packages.
so heres a small guide for them.
if you can get access to broadband somewhere then do this. 
also i know there are many threads already about this but none contains all this

first of all you can mirror the entire ubuntu repositories on you hdd and save it to dvds. the advantage is that you only have to downlaod once and you can also givethe dvds to anyone who wants to install. 

 here are 2 guides on that topic. 
[guide 1]("http://www.jochenskulj.de/ubuntu/CreatingMirrorDVD.html")
[more detailed guide2]("http://cargol.net/~ramon/ubuntu-dvd-en")



the second guide also has torrents for those who would rather dl the isos.


for those who want to mirror the repos themselves or use a different architecture 
here is a what to do.

1.make sure you have a parition with atleast 11GB free.
2. make a directory 
3. cd into that directory.
4. use this command 

     debmirror -v [COLOR="Blue"]--host=archive.ubuntu.com[/COLOR] --method=http --root=ubuntu [COLOR="RoyalBlue"]--arch=i386 --dist=hoary,hoary-updates,hoary-security [/COLOR][COLOR="Blue"]--section=main,multiverse,restricted,universe[/COLOR] --nosource --passive hoary --ignore-release-gpg --progress --verbose --debug 


you can look the debmirror help and edit the commands that are blue but i would not recommend editing any other unless you know what you doing.

well have fun 
if anyone can add more to this guide please post ti and i will add. 

i have been seeing a lot of threads with this so 1 consise guide is better imo. 
have fun mirroring.

ooops seems i mispelt broadband in the title could a mod fix that cuz i can't find the option to do that.

---

### Post by UbuWu on 2005-10-30
You should edit the second link, because the duplicate http:// will make firefox goto microsoft.com (!).

---

### Post by kakashi on 2006-02-17
bump

---

### Post by Bartender on 2006-02-17
Hi, kakashi -
Those of us without broadband are up the creek without a paddle and it's good to see someone trying to help.  Link #1 contains references to Warty.  Pretty sure that you'd have to make changes in order to access Breezy data but don't know how to address that.
We don't want someone with a fresh Breezy install to download data from a different version of Ubuntu.  That would make a mess of things.

---

### Post by kakashi on 2006-02-17
sorry. i just bumped the thread and forgot that i created it at a tiome when hoary was the distro, i'll see if i can make new ones and upload it some where.

---

### Post by Xecuter on 2006-02-17
THANK YOU!!! I LOVE YOU!!! allmost :P

Just what i needed.

EDIT: The torrents from that site doesn't work. You know anywhere else to get it?

---

