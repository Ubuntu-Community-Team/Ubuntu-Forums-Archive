---
title: "Could not download all repository indexes"
date: 2006-07-17
forum: Installation &amp; Upgrades
---

### Post by spahn on 2006-07-17
I have a fresh install of Dapper (i am fairly familiar with Ubuntu), and i keep getting the following error:


**Could not download all repository indexes**

The repository might be no longer available or could not be contacted because of network problems. If available an older version of the failed index will be used. Otherwise the repository will be ignored. Check your network connection and the correct writing of the repository address in the preferences.
```

http://archive.ubuntu.com/ubuntu/dists/dapper/main/binary-i386/Packages.gz: Sub-process gzip returned an error code (1)

```

i have had all sorts of troubles with the packages on this installation of Ubuntu- either because it is on a Dell or because it is at work (routers and network stuff)

the major problem is that i can't find the packages i need, i can't do an apt-get install, and the dependancies are bad....

Any ideas???

Thanks!

---

### Post by spahn on 2006-07-18
Can anyone please help me???

---

### Post by aysiu on 2006-07-18
Well, I just did this five seconds ago, and it seemed fine: ```
sudo aptitude update
Password:
Reading package lists... Done
Building dependency tree... Done
Reading extended state information
Initializing package states... Done
Building tag database... Done
Get:1 http://archive.canonical.com dapper-commercial Release.gpg [191B]
Get:2 http://archive.ubuntu.com dapper Release.gpg [189B]
Get:3 http://archive.ubuntu.com dapper-updates Release.gpg [189B]
Get:4 http://security.ubuntu.com dapper-security Release.gpg [189B]
Get:5 http://archive.ubuntu.com dapper-backports Release.gpg [189B]
Hit http://archive.canonical.com dapper-commercial Release
Hit http://archive.ubuntu.com dapper Release
Get:6 http://security.ubuntu.com dapper-security Release [30.9kB]
Get:7 http://archive.ubuntu.com dapper-updates Release [30.9kB]
Hit http://archive.canonical.com dapper-commercial/main Packages
Get:8 http://archive.ubuntu.com dapper-backports Release [19.6kB]
Hit http://archive.ubuntu.com dapper/main Packages
Hit http://archive.ubuntu.com dapper/restricted Packages
Hit http://archive.ubuntu.com dapper/main Sources
Hit http://archive.ubuntu.com dapper/restricted Sources
Hit http://archive.ubuntu.com dapper/universe Packages
Hit http://archive.ubuntu.com dapper/universe Sources
Hit http://archive.ubuntu.com dapper/multiverse Packages
Hit http://archive.ubuntu.com dapper/multiverse Sources
Get:9 http://security.ubuntu.com dapper-security/main Packages [36.8kB]
Get:10 http://archive.ubuntu.com dapper-updates/main Packages [42.8kB]
Get:11 http://archive.ubuntu.com dapper-updates/restricted Packages [14B]
Get:12 http://archive.ubuntu.com dapper-updates/main Sources [24.9kB]
Get:13 http://archive.ubuntu.com dapper-updates/restricted Sources [14B]
Get:14 http://archive.ubuntu.com dapper-backports/main Packages [14B]
Get:15 http://archive.ubuntu.com dapper-backports/restricted Packages [14B]
Get:16 http://archive.ubuntu.com dapper-backports/universe Packages [14B]
Get:17 http://archive.ubuntu.com dapper-backports/multiverse Packages [14B]
Get:18 http://security.ubuntu.com dapper-security/restricted Packages [4558B]
Get:19 http://security.ubuntu.com dapper-security/main Sources [9118B]
Get:20 http://security.ubuntu.com dapper-security/restricted Sources [974B]
Get:21 http://security.ubuntu.com dapper-security/universe Packages [6951B]
Get:22 http://security.ubuntu.com dapper-security/universe Sources [902B]
Ign http://packages.freecontrib.org dapper Release.gpg
Ign http://packages.freecontrib.org dapper Release
Ign http://packages.freecontrib.org dapper/free Packages
Ign http://packages.freecontrib.org dapper/non-free Packages
Ign http://packages.freecontrib.org dapper/free Sources
Ign http://packages.freecontrib.org dapper/non-free Sources
Hit http://packages.freecontrib.org dapper/free Packages
Hit http://packages.freecontrib.org dapper/non-free Packages
Hit http://packages.freecontrib.org dapper/free Sources
Hit http://packages.freecontrib.org dapper/non-free Sources
Fetched 209kB in 6s (31.7kB/s)
Reading package lists... Done
``` So see if you still get that error after following these instructions (this is how I got my sources.list):

[http://www.psychocats.net/ubuntu/sources](http://www.psychocats.net/ubuntu/sources)

---

### Post by spahn on 2006-07-18
Thank you for the command tip and the link but nothing has changed.

I had read that similar problems came from router filtering enabled, we checked and ours was already disabled...

This is a really frustrating issue!

i can't get the programs i need and this is my work machine!!!

Any help would be greatly appriaciated!

---

### Post by Gyrotwister on 2006-07-20
I was just about to start a new threat about the exact same problem.  

Can anyone shed some light on this?  It's very frustrating.  ](*,)

---

### Post by spahn on 2006-07-20
Extremely Frustrating!!!!

Somebody has to know something about how to fix this!!!

---

### Post by Gyrotwister on 2006-07-21
Could somebody please interpret the last part of this error message?

```
Sub-process gzip returned an error code (1)
```

What is gzip?

What is error code (1)?

---

### Post by SkyNet2029 on 2006-07-22
Gzip is short for GNU Zip, a compression program, or the header for the compressed download (which I believe is what the archives spit out). It's also a couple of other things, too.
I used to have that same issue until I went with the Debian way and dropped my country code in front of the archive addy's. Works fine now.

---

### Post by Gyrotwister on 2006-07-23
Thanks for the reply, but I dont understand.  

Remove the country code from the what?

Could you please elaborate on this so I can give it a try?

---

### Post by SkyNet2029 on 2006-07-23
I meant for you to edit your /etc/apt/sources.list so as to pull the needed information from a different server than what is standard.
```
$sudo nano /etc/apt/sources.list 
```

As an example, in Aysiu's post it shows the sources.list as routing to 
```
deb http://archive.ubuntu.com dapper/main Packages
``` 
as opposed to 
(here the two letter country code for the United States is inserted before the 'archive.com' to route to that particular server as opposed to the general repository.
```
http://us.archive.ubuntu.com dapper/main Packages
```
Here is the humorous (maybe not so much for you) part: When I posted this last evening, the US servers were online as expected, but today I had to revert to the standard server (minus the country code, I mean), due to the US server stalling out on me. 
The short answer: I was meaning for you to attempt to get the packages you needed from a different server.

---

### Post by Gyrotwister on 2006-07-23
Thanks, that seems easy enough.  

I'll give it a try.

---

### Post by Gyrotwister on 2006-07-23
Hmm, I don't think I follow.  
I went back to Aysiu's site but couldn't find the text which you had indicated.  
```
deb http://archive.ubuntu.com dapper/main Packages
```
So I tried editing the lines which refer to the multiverse packages but that produced a different type of error.  

The alterations seem simple enough, just remove the "deb" at the front and insert a "us." after the double forward slashes, right?  

Which lines exactly should I try altering?  

Sorry to be such a pest but this is my first attempt at any kind of Linux distribution.

---

### Post by spahn on 2006-07-23
Cool Beans!
I am soo stoked! I had been wrestling with this problem for weeks- and to think that it was soo simple as to add "us.". Thank you [I]SkyNet2029
[/I]
Thank you Thank you!

---

### Post by stv453 on 2006-07-23
I get the error "temporary failure resolving security.ubuntu.com" 
(and all the other http links in souces.list failed as well,such as us.archive.ubuntu.com)

Is this due to the server being down or something wrong with my connection?

Is there any command such as ping in dos that i can use to check if my internet connection is working?

thanks

i'm trying to install xorg-driver-fglrx...


EDIT: never mind... it worked.  Now on to XGL!!! 8)

---

### Post by Gyrotwister on 2006-07-24
Well I'm glad Spahn, the originator of this thread finally got his problem solved but I'm still not sure how to apply this solution.  

Exactly which lines do I edit?
A copy of a working sources.list with the “us.”  inserted in just the right spots would be a helpful thing at the moment.  

Hey Spahn, care to spread some of that joy around?

---

### Post by Gyrotwister on 2006-07-24
Ok, after reading Spahn's most recent post again I tried adding only the “us.” to the line which seems to refer to the multiverse packages.  It worked!  Multiverse is enabled!  Getting java pluging as I type this!  

Now, just for the record, and to perhaps help the next user with this problem I'll try and illustrate the change required to avoid this frustrating mess.  

From aysiu's suggested sources.list...

[http://www.psychocats.net/ubuntu/sources.php](http://www.psychocats.net/ubuntu/sources.php)

Find

```
deb http://archive.ubuntu.com/ubuntu dapper multiverse
```

and change it to 

```
deb http://us.archive.ubuntu.com/ubuntu dapper multiverse
```
Don't delete the "deb" at the front like I did at first.  

Many thanks to SkyNet2029 and Aysiu.

---

### Post by spahn on 2006-07-24
> **Gyrotwister said:**
> Well I'm glad Spahn, the originator of this thread finally got his problem solved but I'm still not sure how to apply this solution.  

Exactly which lines do I edit?
A copy of a working sources.list with the “us.”  inserted in just the right spots would be a helpful thing at the moment.  

Hey Spahn, care to spread some of that joy around?

Yeah, i appended "us." before "archive" on all except the security ones.

```

deb http://us.archive.ubuntu.com/ubuntu/ dapper main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ dapper main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu/ dapper-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ dapper-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://us.archive.ubuntu.com/ubuntu/ dapper universe multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ dapper universe multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://us.archive.ubuntu.com/ubuntu/ dapper-backports main restricted universe multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ dapper-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu dapper-security main restricted
deb-src http://security.ubuntu.com/ubuntu dapper-security main restricted
deb http://security.ubuntu.com/ubuntu dapper-security universe multiverse
deb-src http://security.ubuntu.com/ubuntu dapper-security universe multiverse


```:D

---

### Post by matjaz_pirnovar on 2006-07-31
I'm having similar issue. When checking my system updates I get 4 failure notices with the same answer (or very similar).

I'm at work now, but will come back later.

M

---

### Post by spahn on 2006-07-31
Cool, just try appending the country code in front of the "archive"!

---

