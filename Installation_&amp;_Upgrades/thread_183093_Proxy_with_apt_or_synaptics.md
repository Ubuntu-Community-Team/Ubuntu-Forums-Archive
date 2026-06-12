---
title: "Proxy with apt or synaptics"
date: 2006-05-27
forum: Installation &amp; Upgrades
---

### Post by Lunar_Lamp on 2006-05-27
I have just installed Dapper, and want to get synaptics set up.
I have set my proxy up in the network connection place, and in firefox.  I can use GAIM and Firefox just fine.
I went into Synaptics and put my proxy settings in, with the correct details (checked for certainty), and clicking "update" cannot download any files.

I have edited /etc/apt/apt.conf to include:
acquire::http::proxy "http://proxyaddress:theport";

Exactly the same as in network settings (and similar to firefox, except I am able to use a .pac setup for that).

Still it doesn't work.


I have edited my ~./bashrc to include:

http_proxy=http://yourproxyaddress:proxyport
export http_proxy

Still doesn't work, after all this the error I get is:
```

ed@PMSEH:~$ sudo apt-get update
Password:
Errhttp://security.ubuntu.com dapper-security Release.gpg
  Could not connect to security.ubuntu.com:80 (82.211.81.138), connection timed out
Errhttp://gb.archive.ubuntu.com dapper-updates Release.gpg
  Could not connect to gb.archive.ubuntu.com:80 (85.133.25.8), connection timed out
Errhttp://archive.ubuntu.com dapper Release.gpg
  Could not connect to archive.ubuntu.com:80 (85.133.25.8), connection timed out
Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/dapper-updates/Release.gpg  Could not connect to gb.archive.ubuntu.com:80 (85.133.25.8), connection timed out
Failed to fetch http://security.ubuntu.com/ubuntu/dists/dapper-security/Release.gpg  Could not connect to security.ubuntu.com:80 (82.211.81.138), connection timed out
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/dapper/Release.gpg  Could not connect to archive.ubuntu.com:80 (85.133.25.8), connection timed out
Reading package lists... Done
W: Some index files failed to download, they have been ignored, or old ones used instead.

``` 

I should also add that I am able to use firefox to get to [http://security.ubuntu.com]("http://security.ubuntu.com") and navigate the directories and download files that I want to at will.


The error when using Synaptics is:

"The repository might be no longer available or could not be contacted because of network problems. If available an older version of the failed index will be used. Otherwise the repository will be ignored. Check your network connection and the correct writing of the repository address in the preferences."

---

### Post by osd_daedalus on 2006-05-27
[QUOTE=Lunar_Lamp]I have just installed Dapper, and want to get synaptics set up.
I have set my proxy up in the network connection place, and in firefox.  I can use GAIM and Firefox just fine.
I went into Synaptics and put my proxy settings in, with the correct details (checked for certainty), and clicking "update" cannot download any files.

I have edited /etc/apt/apt.conf to include:
acquire::http::proxy "http://proxyaddress:theport";

Exactly the same as in network settings (and similar to firefox, except I am able to use a .pac setup for that).

Still it doesn't work.
[/QUOTE]

Same for me. I'm behind a http proxy with authentication.. before upgrading (with Breezy) all was fine with *[http://username:password@address:port](http://username:password@address:port)*. Now both with synaptic and aptitude the response is always **407 Proxy Authentication Required** ](*,) why?:-k

---

### Post by osd_daedalus on 2006-05-27
[QUOTE=osd_daedalus]Same for me. I'm behind a http proxy with authentication.. before upgrading (with Breezy) all was fine with *[http://username:password@address:port](http://username:password@address:port)*. Now both with synaptic and aptitude the response is always **407 Proxy Authentication Required** ](*,) why?:-k[/QUOTE]

strange... I tried with apt-get and IT WORKS!!!
And guess what? MAGICALLY either aptitude works :cool: 

Only Synaptic continues to give me auth errors :-k

---

### Post by snipe122 on 2006-05-27
sometimes Ive got to use a proxy as well. But I dont have to change the settings in synaptic. there its always no proxy. I just change the settings under system --> properties --> network-proxy.

and there I just put in name:passwd@xxx.xxxxxxx.xxx:PORT

this works like a charme for me...


greetz
snipe

---

### Post by Lunar_Lamp on 2006-05-27
I retried this:

export http_proxy="cache:port/"

And now apt-get works :-D

However, I cannot get synaptics to work :-( - of course I have to set the variable each time I open a new bash window, so obviously I didn't edit my bashrc correctly...

---

### Post by Lunar_Lamp on 2006-05-27
After editing my bashrc correctly, I can run synaptic from the command line and it appears to be functioning grandly (though I haven't heavily tested it - just reloaded packages etc).

I cannot however run it from the system>administration>synaptic shortcut however.  What on earth is going on here?!  I have the same proxy settings set up inside synaptic...

---

### Post by osd_daedalus on 2006-05-28
[QUOTE=Lunar_Lamp]After editing my bashrc correctly, I can run synaptic from the command line and it appears to be functioning grandly (though I haven't heavily tested it - just reloaded packages etc).
[/QUOTE]

I tried as you did and now it's worse. Now synaptic doesn't find the archive index...
:confused: :confused: :confused:

---

### Post by osd_daedalus on 2006-05-28
Look what I have discovered...

_PREAMBLE_

I used Slackware and because I don't want to *sudo* for every root action, I assigned a root password launching xterm from root and then passwd. So I can use root commands with **su** and **su -**

_AND NOW..._

P.S. I'm Italian so many messages are in italian. ;) 
$ sudo apt-get update
```

Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper Release.gpg
Ign [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security Release.gpg
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper Release
Ign [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) dapper-updates Release.gpg
Ign [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) dapper-backports Release.gpg
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/main Packages
Ign [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security Release
Ign [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) dapper-updates Release
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/restricted Packages
Ign [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) dapper-backports Release
Ign [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/universe Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/multiverse Packages
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/main Packages
  407 Proxy Authentication Required
Ign [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) dapper-updates/main Packages
Ign [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/restricted Packages
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/restricted Packages
  407 Proxy Authentication Required
Ign [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) dapper-updates/restricted Packages
Ign [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/universe Packages
Ign [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) dapper-updates/multiverse Packages
Ign [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/multiverse Packages
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/universe Packages
  407 Proxy Authentication Required
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/multiverse Packages
  407 Proxy Authentication Required
Ign [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) dapper-updates/universe Packages
Err [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main Packages
  407 Proxy Authentication Required
Ign [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) dapper-backports/main Packages
Err [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/restricted Packages
  407 Proxy Authentication Required
Ign [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) dapper-backports/restricted Packages
Ign [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) dapper-backports/universe Packages
Err [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/universe Packages
  407 Proxy Authentication Required
Ign [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) dapper-backports/multiverse Packages
Err [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/multiverse Packages
  407 Proxy Authentication Required
Err [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) dapper-updates/main Packages
  407 Proxy Authentication Required
Err [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) dapper-updates/restricted Packages
  407 Proxy Authentication Required
Err [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) dapper-updates/multiverse Packages
  407 Proxy Authentication Required
Err [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) dapper-updates/universe Packages
  407 Proxy Authentication Required
Err [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) dapper-backports/main Packages
  407 Proxy Authentication Required
Err [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) dapper-backports/restricted Packages
  407 Proxy Authentication Required
Err [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) dapper-backports/universe Packages
  407 Proxy Authentication Required
Err [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) dapper-backports/multiverse Packages
  407 Proxy Authentication Required
Impossibile ottenere [http://archive.ubuntu.com/ubuntu/dists/dapper/main/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/dapper/main/binary-i386/Packages.gz)  407 Proxy Authentication Required
Impossibile ottenere [http://archive.ubuntu.com/ubuntu/dists/dapper/restricted/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/dapper/restricted/binary-i386/Packages.gz)  407 Proxy Authentication Required
Impossibile ottenere [http://security.ubuntu.com/ubuntu/dists/dapper-security/main/binary-i386/Packages.gz](http://security.ubuntu.com/ubuntu/dists/dapper-security/main/binary-i386/Packages.gz)  407 Proxy Authentication Required
Impossibile ottenere [http://archive.ubuntu.com/ubuntu/dists/dapper/universe/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/dapper/universe/binary-i386/Packages.gz)  407 Proxy Authentication Required
Impossibile ottenere [http://archive.ubuntu.com/ubuntu/dists/dapper/multiverse/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/dapper/multiverse/binary-i386/Packages.gz)  407 Proxy Authentication Required
Impossibile ottenere [http://it.archive.ubuntu.com/ubuntu/dists/dapper-updates/main/binary-i386/Packages.gz](http://it.archive.ubuntu.com/ubuntu/dists/dapper-updates/main/binary-i386/Packages.gz)  407 Proxy Authentication Required
Impossibile ottenere [http://security.ubuntu.com/ubuntu/dists/dapper-security/restricted/binary-i386/Packages.gz](http://security.ubuntu.com/ubuntu/dists/dapper-security/restricted/binary-i386/Packages.gz)  407 Proxy Authentication Required
Impossibile ottenere [http://it.archive.ubuntu.com/ubuntu/dists/dapper-updates/restricted/binary-i386/Packages.gz](http://it.archive.ubuntu.com/ubuntu/dists/dapper-updates/restricted/binary-i386/Packages.gz)  407 Proxy Authentication Required
Impossibile ottenere [http://security.ubuntu.com/ubuntu/dists/dapper-security/universe/binary-i386/Packages.gz](http://security.ubuntu.com/ubuntu/dists/dapper-security/universe/binary-i386/Packages.gz)  407 Proxy Authentication Required
Impossibile ottenere [http://it.archive.ubuntu.com/ubuntu/dists/dapper-updates/multiverse/binary-i386/Packages.gz](http://it.archive.ubuntu.com/ubuntu/dists/dapper-updates/multiverse/binary-i386/Packages.gz)  407 Proxy Authentication Required
Impossibile ottenere [http://security.ubuntu.com/ubuntu/dists/dapper-security/multiverse/binary-i386/Packages.gz](http://security.ubuntu.com/ubuntu/dists/dapper-security/multiverse/binary-i386/Packages.gz)  407 Proxy Authentication Required
Impossibile ottenere [http://it.archive.ubuntu.com/ubuntu/dists/dapper-updates/universe/binary-i386/Packages.gz](http://it.archive.ubuntu.com/ubuntu/dists/dapper-updates/universe/binary-i386/Packages.gz)  407 Proxy Authentication Required
Impossibile ottenere [http://it.archive.ubuntu.com/ubuntu/dists/dapper-backports/main/binary-i386/Packages.gz](http://it.archive.ubuntu.com/ubuntu/dists/dapper-backports/main/binary-i386/Packages.gz)  407 Proxy Authentication Required
Impossibile ottenere [http://it.archive.ubuntu.com/ubuntu/dists/dapper-backports/restricted/binary-i386/Packages.gz](http://it.archive.ubuntu.com/ubuntu/dists/dapper-backports/restricted/binary-i386/Packages.gz)  407 Proxy Authentication Required
Impossibile ottenere [http://it.archive.ubuntu.com/ubuntu/dists/dapper-backports/universe/binary-i386/Packages.gz](http://it.archive.ubuntu.com/ubuntu/dists/dapper-backports/universe/binary-i386/Packages.gz)  407 Proxy Authentication Required
Impossibile ottenere [http://it.archive.ubuntu.com/ubuntu/dists/dapper-backports/multiverse/binary-i386/Packages.gz](http://it.archive.ubuntu.com/ubuntu/dists/dapper-backports/multiverse/binary-i386/Packages.gz)  407 Proxy Authentication Required

```

$ su
/home/daedalus # apt-get update

[COLOR="Blue"]idem[/COLOR]

but...

$ su -
#apt-get update

[COLOR="Green"]works finely[/COLOR]

While I'm in a root shell with X launched as user, I cannot run synaptic for control. I'll try launching development mode (root without X) and launching *startx* from there. I will notice you if there are news.

---

### Post by osd_daedalus on 2006-05-29
> While I'm in a root shell with X launched as user, I cannot run synaptic for control. I'll try launching development mode (root without X) and launching *startx* from there. I will notice you if there are news.

Just tried (i'm posting as root :p ) and works finely.

Ok developers, now it's your turn :mrgreen: :mrgreen:

---

### Post by Lunar_Lamp on 2006-05-31
I have found a work-around to get synaptic working once I have it working from the command line:

I used "applications>accessories>alacarte menu editor" to edit the menu entry for synaptic "gksudo synaptic" (which performs a graphical-sudo and opens synaptic).


I wouldn't risk running anything as root without a very good reason personally...

---

### Post by osd_daedalus on 2006-06-11
Now I'm at home and I don't have a fast connection for upgrading Dapper. Someone could tell me if this issue has been fixed with the official release?

---

### Post by BoomAM on 2006-07-27
> **osd_daedalus said:**
> Same for me. I'm behind a http proxy with authentication.. before upgrading (with Breezy) all was fine with *[http://username:password@address:port](http://username:password@address:port)*. Now both with synaptic and aptitude the response is always **407 Proxy Authentication Required** ](*,) why?:-k
Same here.
My apt.conf file is setup as follows:
```
ACQUIRE { 
http::proxy "http://[Administrator]:[Change_Me]@[192.168.3.253]:[80]/" 
}
```
But it doesnt work from either the command line or the menu items.

Ideas?

---

### Post by tty01 on 2006-07-27
sounds like you guys are behind a ISA proxy.  try

> export http_proxy=http://domainname\\user: password@yourproxy:8080/

without any spaces between user: password.....had to put space in so the smiley face icons wouldnt show up

---

### Post by BoomAM on 2006-07-27
> **tty01 said:**
> sounds like you guys are behind a ISA proxy.  try



without any spaces between user: password.....had to put space in so the smiley face icons wouldnt show up
Thanks, i'll give that a try when i get into work tomorrow. :)

So that goes in the *.conf file, with me then clearing the enteries from network proxy & synaptics? Or does that go in the properties for synaptic & network proxy?

---

### Post by tty01 on 2006-07-27
simply type it into terminal :)

---

### Post by BoomAM on 2006-07-28
Do i have to remove the settings i put into Synaptics and/or Network proxy though?

After ive put it in, i take it that i can run Synaptics properly then?

---

### Post by BoomAM on 2006-07-28
> **tty01 said:**
> simply type it into terminal :)
Well ive just typed it into terminal without doing anything else and now its not doing anything at all when i run apt-get update or synaptics.

This is what i get:
```
chs@chs-desktop:~$ export http_proxy=http://rmcomms\\Administrator\Change_Me@192 .168.3.253:80/
chs@chs-desktop:~$ sudo apt-get update
Errhttp://security.ubuntu.com dapper-security Release.gpg
  Temporary failure resolving ‘rmcomms\AdministratorChange_Me@192.168.3.253’
Errhttp://gb.archive.ubuntu.com dapper Release.gpg
  Temporary failure resolving ‘rmcomms\AdministratorChange_Me@192.168.3.253’
Errhttp://gb.archive.ubuntu.com dapper-updates Release.gpg
  Temporary failure resolving ‘rmcomms\AdministratorChange_Me@192.168.3.253’
Errhttp://gb.archive.ubuntu.com dapper-backports Release.gpg   ^[
  Temporary failure resolving ‘rmcomms\AdministratorChange_Me@192.168.3.253’
Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/dapper/Release.gpg  Temporary failure resolving ‘rmcomms\AdministratorChange_Me@192.168.3.253’
Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/dapper-updates/Release.gpg  Temporary failure resolving ‘rmcomms\AdministratorChange_Me@192.168.3.253’
Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/dapper-backports/Release.gpg  Temporary failure resolving ‘rmcomms\AdministratorChange_Me@192.168.3.253’
Failed to fetch http://security.ubuntu.com/ubuntu/dists/dapper-security/Release.gpg  Temporary failure resolving ‘rmcomms\AdministratorChange_Me@192.168.3.253’
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
chs@chs-desktop:~$

```

Ive tryed putting the same code into synaptics & network proxy with no luck either?

---

### Post by tty01 on 2006-07-28
> Do i have to remove the settings i put into Synaptics and/or Network proxy though?

After ive put it in, i take it that i can run Synaptics properly then?

im behind a isa proxy at work as well.  My network proxy fields are all blank.  only entries i have is for mozilla, apt-get, and synaptic.  maybe you should try authenticating in mozilla first to make sure you have the right proxy address/port.  So yes you can remove the network proxy fields.

> Well ive just typed it into terminal without doing anything else and now its not doing anything at all when i run apt-get update or synaptics.
that command was not meant to be entered into synaptic.  If you want to enter your proxy into synaptic the syntax is username: password@yourproxy. (again no spaces between : and password) 

> chs@chs-desktop:~$ export http_proxy=http://rmcomms\\Administrator\Change_Me@192 .168.3.253:80/
chs@chs-desktop:~$ sudo apt-get update
Errhttp://security.ubuntu.com dapper-security Release.gpg
  Temporary failure resolving ‘rmcomms\AdministratorChange_Me@192.168.3.253’
Errhttp://gb.archive.ubuntu.com dapper Release.gpg
  Temporary failure resolving ‘rmcomms\AdministratorChange_Me@192.168.3.253’
Errhttp://gb.archive.ubuntu.com dapper-updates Release.gpg
  Temporary failure resolving ‘rmcomms\AdministratorChange_Me@192.168.3.253’
Errhttp://gb.archive.ubuntu.com dapper-backports Release.gpg   ^[
  Temporary failure resolving ‘rmcomms\AdministratorChange_Me@192.168.3.253’
Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/dapper/Release.gpg](http://gb.archive.ubuntu.com/ubuntu/dists/dapper/Release.gpg)  Temporary failure resolving ‘rmcomms\AdministratorChange_Me@192.168.3.253’
Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/dapper-updates/Release.gpg](http://gb.archive.ubuntu.com/ubuntu/dists/dapper-updates/Release.gpg)  Temporary failure resolving ‘rmcomms\AdministratorChange_Me@192.168.3.253’
Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/dapper-backports/Release.gpg](http://gb.archive.ubuntu.com/ubuntu/dists/dapper-backports/Release.gpg)  Temporary failure resolving ‘rmcomms\AdministratorChange_Me@192.168.3.253’
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/dapper-security/Release.gpg](http://security.ubuntu.com/ubuntu/dists/dapper-security/Release.gpg)  Temporary failure resolving ‘rmcomms\AdministratorChange_Me@192.168.3.253’
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
chs@chs-desktop:~$

look at the way you typed it and look at the way i typed it....notice any difference?

export http_proxy=http://domainname\\user**:** password@yourproxy:8080/
and those last 2 errors are due to synaptic being still open while trying to run apt-get.  You can only use either or. Not two at the same time.  Let me know how it turns out :)

---

### Post by BoomAM on 2006-07-28
> **tty01 said:**
> maybe you should try authenticating in mozilla first to make sure you have the right proxy address/port.
It does work in Mozilla.


> look at the way you typed it and look at the way i typed it....notice any difference?
You said ignore the spaces because they were there to prevent the emoticons from kicking in on here?

> and those last 2 errors are due to synaptic being still open while trying to run apt-get.  You can only use either or. Not two at the same time.  Let me know how it turns out :)
Synaptic wasnt open?

Wont be able to test again till im next in work, on monday.
So i'll try then and report back. :)

---

### Post by tty01 on 2006-07-28
you:
chs@chs-desktop:~$ export http_proxy=http://rmcomms\\Administrator**\**Change_Me@192 .168.3.253:80/

me:
export http_proxy=http://domainname\\user: password@yourproxy:8080/

between administrator and password you put a slash in instead of colon....you got the spacing right though.

also forgot to mention.  Seems like your isa proxy doesnt require you to authenticate the domain.  You can type this instead
export http_proxy=http://username:yourpassword@yourproxy:yourport/

---

### Post by BoomAM on 2006-07-28
> **tty01 said:**
> you:
chs@chs-desktop:~$ export http_proxy=http://rmcomms\\Administrator**\**Change_Me@192 .168.3.253:80/

me:
export http_proxy=http://domainname\\user: password@yourproxy:8080/

between administrator and password you put a slash in instead of colon....you got the spacing right though.

also forgot to mention.  Seems like your isa proxy doesnt require you to authenticate the domain.  You can type this instead
export http_proxy=http://username:yourpassword@yourproxy:yourport/
Thanks.
I'll give that a bash when im next in work. :)

---

### Post by BoomAM on 2006-07-31
> **tty01 said:**
> you:
chs@chs-desktop:~$ export http_proxy=http://rmcomms\\Administrator**\**Change_Me@192 .168.3.253:80/

me:
export http_proxy=http://domainname\\user: password@yourproxy:8080/

between administrator and password you put a slash in instead of colon....you got the spacing right though.

also forgot to mention.  Seems like your isa proxy doesnt require you to authenticate the domain.  You can type this instead
export http_proxy=http://username:yourpassword@yourproxy:yourport/
Unsuprisingly, neither the above, nor the command for synaptics, works.
```
chs@chs-desktop:~$ export http_proxy=http://rmcomms\\Administrator:Change_Me@192 .168.3.253:80/
chs@chs-desktop:~$ export http_proxy=http://Administrator@Change_Me@192.168.3.25 3:80/
chs@chs-desktop:~$ apt-get update
E: Could not open lock file /var/lib/apt/lists/lock - open (13 Permission denied )
E: Unable to lock the list directory**<- I forgot synaptics was open at that point so i closed it**
chs@chs-desktop:~$ sudo apt-get update
Password:
chs
Sorry, try again.
Password:
Errhttp://gb.archive.ubuntu.com dapper Release.gpg
  Temporary failure resolving ‘Administrator@Change_Me@192.168.3.253’
Errhttp://security.ubuntu.com dapper-security Release.gpg
  Temporary failure resolving ‘Administrator@Change_Me@192.168.3.253’
Errhttp://gb.archive.ubuntu.com dapper-updates Release.gpg
  Temporary failure resolving ‘Administrator@Change_Me@192.168.3.253’
Errhttp://gb.archive.ubuntu.com dapper-backports Release.gpg
  Temporary failure resolving ‘Administrator@Change_Me@192.168.3.253’
Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/dapper/Release.gpg  Temporary failure resolving ‘Administrator@Change_Me@192.168.3.253’
Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/dapper-updates/Release.gpg  Temporary failure resolving ‘Administrator@Change_Me@192.168.3.253’
Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/dapper-backports/Release.gpg  Temporary failure resolving ‘Administrator@Change_Me@192.168.3.253’
Failed to fetch http://security.ubuntu.com/ubuntu/dists/dapper-security/Release.gpg  Temporary failure resolving ‘Administrator@Change_Me@192.168.3.253’
Reading package lists... Done
W: Some index files failed to download, they have been ignored, or old ones used instead.
chs@chs-desktop:~$

```

---

### Post by Psychoscorpic on 2006-07-31
I may as well add myself to this mix.
Also sitting behind an ISA Proxy firewall.
Tried all from the last 3 pages of this thread.

Interesting thing is, though, that when I started there were around 300 packages in the list to update, and all gave the 407 Proxy Authentication Required error.
Then one of the admins fiddled with the server for something else, and all of a sudden most went through fine. I now only have 88 stubborn ones. All give this error:
W: Failed to fetch [http://za.archive.ubuntu.com/ubuntu/pool/main/l/language-pack-en/language-pack-en_6.06+20060705_all.deb](http://za.archive.ubuntu.com/ubuntu/pool/main/l/language-pack-en/language-pack-en_6.06+20060705_all.deb)
  407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy service is denied.  )

As with others, I can happily browse there with Firefox, so it doesn't seem to be a "blocked" address in the ISA list.

But I do find it interesting that a changed setting on the ISA server allowed most packages to go through. (And before you ask, no, I don't know what was changed)

---

### Post by Leslie Viljoen on 2006-09-14
Anyone still struggling with Apt Proxy Auth behind an ISA server should just install NTLMAPS and you should be up and going in a few minutes.

Go to:

[http://michaelcarden.net/blog/index.php?p=58](http://michaelcarden.net/blog/index.php?p=58)

For instructions.


In brief, you need to get the package here:
[http://packages.ubuntulinux.org/dapper/web/ntlmaps](http://packages.ubuntulinux.org/dapper/web/ntlmaps)

Install it with dpkg -i, and it should prompt you to configure the proxy authentication. Then, within the Gnome environment, under system->preferences->network proxy, enter:

  127.0.0.1, port 5865 

under manual proxy configuration.

apt-get update should then work perfectly.

Good luck!
Leslie

---

### Post by bullit on 2006-09-26
Let's hope this works. 

I'm behind a proxy in my home network (there are 5 desktops connected to the ne). 

I tried everything but nothing works (not sure what everything really means because I skipped a page in this thread :-# 

Here's what I did to use Synaptics whenever I had to update behind a proxy:

1) Launch Synaptics.

2) Go Settings > Preferences > Network

3) Key in your proxy address and port. 

4) You're done.

Hope I'm not embarassing myself.

---

### Post by Bachstelze on 2006-09-26
```
export http_proxy="http://username:password@host.domain:port"
```

---

### Post by cakmin on 2006-10-17
> **Leslie Viljoen said:**
> Anyone still struggling with Apt Proxy Auth behind an ISA server should just install NTLMAPS and you should be up and going in a few minutes.

Go to:

[http://michaelcarden.net/blog/index.php?p=58](http://michaelcarden.net/blog/index.php?p=58)

For instructions.


In brief, you need to get the package here:
[http://packages.ubuntulinux.org/dapper/web/ntlmaps](http://packages.ubuntulinux.org/dapper/web/ntlmaps)

Install it with dpkg -i, and it should prompt you to configure the proxy authentication. Then, within the Gnome environment, under system->preferences->network proxy, enter:

  127.0.0.1, port 5865 

under manual proxy configuration.

apt-get update should then work perfectly.

Good luck!
Leslie

I followed the instructions from that website and managed to installed the ntlmaps however I still get the "407 error Proxy authentication required" whenever I tried to download the updates. I can use it for browsing though. Anyone has any suggestion to sort this out apart from burning an update CD?

---

### Post by yellow beard on 2006-10-17
> **HymnToLife said:**
> ```
export http_proxy="http://username:password@host.domain:port"
```
I have to do this every time i run apt or it doesn't work. Also if i try to use the software updater it updates but wont download. I get this:

```
W: Failed to fetch http://security.ubuntu.com/ubuntu/pool/main/g/gzip/gzip_1.3.5-12ubuntu0.1_i386.deb
  407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy service is denied.  )
```

Yummy

---

### Post by cakmin on 2006-10-17
> **yellow beard said:**
> I have to do this every time i run apt or it doesn't work. Also if i try to use the software updater it updates but wont download. I get this:

```
W: Failed to fetch http://security.ubuntu.com/ubuntu/pool/main/g/gzip/gzip_1.3.5-12ubuntu0.1_i386.deb
  407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy service is denied.  )
```

Yummy

Where do we have to the type the command? I tried to type it in the terminal and run sudo apt-get update it still gives me the 407 proxy error. I think another type of workaround is needed.

---

### Post by Leslie Viljoen on 2006-11-09
> **cakmin said:**
> I followed the instructions from that website and managed to installed the ntlmaps however I still get the "407 error Proxy authentication required" whenever I tried to download the updates. I can use it for browsing though. Anyone has any suggestion to sort this out apart from burning an update CD?

Make sure you set the username and password in the server.cfg file. These questions should have been asked when the package was installed.

My ntlmaps installed in /usr/lib/site-python/ntlmaps. You can check where yours is with dpkg -L ntlmaps.

To make sure it's running:

root@blah:~# netstat -antpu |grep python
tcp        0      0 0.0.0.0:5865            0.0.0.0:*               

...it listens on port 5865 by default. 

For all users to have their proxy set by default, you can put:
http_proxy="http://127.0.0.1:5865"

in /etc/environment



-- Les

---

### Post by blitzschlag on 2006-11-20
u guys need to remember that some chars need protection

like $,&," in passwords
protect em with a backslash
\$ etc. pp.

---

### Post by kOoLiNuS on 2006-11-29
> **bullit said:**
> Let's hope this works. 

I'm behind a proxy in my home network (there are 5 desktops connected to the ne). 

I tried everything but nothing works (not sure what everything really means because I skipped a page in this thread :-# 

Here's what I did to use Synaptics whenever I had to update behind a proxy:

1) Launch Synaptics.

2) Go Settings > Preferences > Network

3) Key in your proxy address and port. 

4) You're done.

Hope I'm not embarassing myself.

and what IF the proxy is authenticated ?
i can't find how to specify username and password

{yes, i did try putting user:password@IP-address in the HTTP Proxy field}

---

### Post by Leslie Viljoen on 2006-11-29
> **kOoLiNuS said:**
> and what IF the proxy is authenticated ?
i can't find how to specify username and password

{yes, i did try putting user:password@IP-address in the HTTP Proxy field}

You should read the other posts. If you are behind ISA, using NTLM authentication, no amount of putting in passwords in going to help. You need NTLMAPS. 

Les

---

### Post by zutroi on 2006-12-06
i've been playing with this all night and i think i've figured it out. just *why* this is happening is a little strange. i'll describe my experience. if this is relevant to you, cool. i'll make this as easy as i can, as i'm a n00b.

my Ubuntu has four (or more) main proxy setting mechanisms:
1. System->Preferences->Network Proxy
2. Firefox's proxy setting
3. Synaptic's proxy setting
4. the /etc/bash.bashrc proxy setting

#2 is irrelevant to this discussion. God bless Firefox.
#4 is obviously cool for my cmd-line stuff:
export http_proxy="http://user:password@x.x.x.x:port/" and
export ftp_proxy="http://user:password@x.x.x.x:port/"

#1 and #3 are completely mutually exclusive: this is why my Synaptic is screwed.

for Synaptic to work on my 6.10 Ubuntu, i must have *ONLY* one of these proxies set: not both! for example, to update my system using Synaptic, i must turn off the system proxy, System->Preferences->Network Proxy = Direct Internet Connection, even though i am behind an authority-requiring firewall. then, under Synaptic's Proxy setting: Administration->Synaptic Package Manager->Preferences->Network i must set Manual Proxy Configuration to the much acclaimed "user:password@ip-address" with the port "3128" in my case, for both http and ftp. now Synaptic will update without the error 407 authorisation failure.

i haven't yet had the chance to witness the impact of having no system-wide proxy setting for Gnome. all i know is that Synaptic can only use one of the two proxy settings: Gnome's or it's own. if you have both set, Synaptic only uses the proxy information from Gnome, but not Gnome's auth settings. Synaptic then won't use it's own proxy settings at all. if you turn off the system proxy settings under Gnome, and set the Synaptic proxy properly, it will run fine.

so now i have:
1. Firefox: you little ripper
2. cmd-line proxy via the bash login
3. Synaptic via its own settings
4. system-wide "Direct Internet Connection" even though i am behind an auth'ing firewall.

what does this all mean? somebody may be able to help me put all of this into perspective. all i know is that it works. phew.

zutroi (somewhere in Melbourne finally running an updated Ubuntu)

---

### Post by penno on 2007-08-10
Thanks everyone for these instructions. It worked for me. No problems with FF or apt-get/synaptic/etc.

One additional query - does anyone know how to make this work from the command line? I tried zutroi's instructions but suspect he wasn't behind an ISA server (as I had no luck anyways). 

Thanks!

Penno

---

### Post by pangenium on 2007-08-12
god bless you zutroi you're a genius :) your post really helped me to solve the problem with apt-get didn't connect to update
my problem was solved when i deleted the content of the apt.conf. Even default "Acquire::http::Proxy false" was pushing apt-get in wrong way; commenting lines didn't help so i deleted all content of the apt.conf and now i'm updating Ubuntu :)

---

### Post by Pontifex on 2007-10-08
Getting NTLMaps working under Ubuntu (6.10 and below).  Installation blatantly plagiarized and sanitized from here:

[http://michaelcarden.net/blog/index.php?p=58a](http://michaelcarden.net/blog/index.php?p=58a)
[http://ubuntuforums.org/showpost.php?p=1546675&postcount=25](http://ubuntuforums.org/showpost.php?p=1546675&postcount=25)
[http://ubuntuforums.org/showpost.php?p=1546675&postcount=31](http://ubuntuforums.org/showpost.php?p=1546675&postcount=31)


Step 1:

Download the package here:

[http://packages.ubuntu.com/dapper/web/ntlmaps](http://packages.ubuntu.com/dapper/web/ntlmaps)


Step 2:

Check your versions of 'debconf' and 'python'.  'Debconf' should be at least version .5 or the 2.0 virtual package.  Python should be at least version 2.4, but _not_ greater than v2.5.  Strange I know.

Debconf has no handy '--version' option, so check your synaptic (or similar package manager GUI) for the version.  'Python --version' should work for your needs.  If you have a Python version between 2.4 and 2.5, then you can use this command:

```

dpkg --install <package name>

```

If you have a Python version _greater_ than 2.5 you can use this:

```

dpkg --install --force-depends-version <package name>

```

NTLMaps will still work, but it will be flagged as "broken".


Step 3:

Configure the program:

[HTML]
Listen port:		5865

Parent Proxy:		your.proxy.com 
			(e.g. enter the name or address of your proxy, 
			do not enter the port as "your.proxy.com:number" 
			as this will be taken care of in the next step)

Parent Proxy Port:	port_number (usually 8080)

NT Windows Domain:	domain_name (your domain)

NT Windows Username:	user_name (the user name you will authenticate with)

NT Windows Password:	password 
			(the password you will use to authenticate with the
			ISA Proxy)
[/HTML]

If some or all of the configuration options aren't availble directly after install, you'll need to manually reconfigure.  This is a bug with the current release.

The NTLMaps service should restart:

```

Stopping ntlmaps: ntlmaps.
Starting ntlmaps: ntlmaps.

```


Step 4:

If it installed properly you should be able to see it with these commands:

```

ps aux | grep ntl

```

And...

```

netstat -antpu | grep python

```

Which should return something like this:

```

root      8244  0.0  0.5   7772  5328 ?        Ss   09:03   0:00 /usr/bin/python /usr/lib/site-python/ntlmaps/main.py -c /etc/ntlmaps/server.cfg

```

And...

```

tcp        0      0 0.0.0.0:5865            0.0.0.0:*               LISTEN     8244/python

```

For each command respectively.

Note: There is a bug that effects both the Ubuntu and Debian installation files.  Simply reconfigure the package to get the program to function correctly:

sudo dpkg-reconfigure ntlmaps

Which will prompt you to re-enter the information in Step 3 and restart the service.


Step 5:

Create a file /etc/apt/apt.conf.d/proxy and input the following line:

```

Acquire::http::Proxy "http://127.0.0.1:5865/";

```

For older versions of apt-get see [http://michaelcarden.net/blog/index.php?p=58a](http://michaelcarden.net/blog/index.php?p=58a) for an alternative configuration.


Step 6:

Reconfigure System->Preferences->"Network Proxy" to point to localhost:5865 with _no_ authentication.  Also reconfigure your GUI Package manager(s) similarly.

Make sure to restart your console and/or GUI package manager to apply the settings.  You should now be able to communicate normally with your repositories.

--Pontifex

---

