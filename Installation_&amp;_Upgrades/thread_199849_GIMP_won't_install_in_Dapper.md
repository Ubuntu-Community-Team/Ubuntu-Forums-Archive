---
title: "GIMP won't install in Dapper"
date: 2006-06-19
forum: Installation &amp; Upgrades
---

### Post by Optiker on 2006-06-19
When I updated to Dapper last week (clean install), I tried install GIMP using Adept, but it wouldn't let me. I got an error dialog box titles "Could not commit changes - Adept Manager" with the message...

"There was an error commiting changes. Possibly there was a problem downloading some packages or the commit would break packages."

I tried again since then with the same result.

Help please?

Thanks!
Optiker

---

### Post by Lord Illidan on 2006-06-19
```
sudo apt-get install gimp
``` Type this in a terminal, and post the output here.

---

### Post by Optiker on 2006-06-19
Done...

--------------------
Reading package lists... Done
Building dependency tree... Done
The following extra packages will be installed:
  gimp-data libaa1 libgimp2.0 libwmf0.2-7
Suggested packages:
  gimp-help-en gimp-help gimp-python libgimp-perl gimp-data-extras
Recommended packages:
  gimp-svg gimp-print
The following NEW packages will be installed:
  gimp gimp-data libaa1 libgimp2.0 libwmf0.2-7
0 upgraded, 5 newly installed, 0 to remove and 5 not upgraded.
Need to get 5504kB of archives.
After unpacking 31.5MB of additional disk space will be used.
Do you want to continue [Y/n]? Y
WARNING: The following packages cannot be authenticated!
  gimp-data libaa1 libgimp2.0 libwmf0.2-7 gimp
Install these packages without verification [y/N]? y
Err [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) dapper/main gimp-data 2.2.11-1ubuntu3
  The HTTP server sent an invalid reply header
Err [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) dapper/main libaa1 1.4p5-30
  The HTTP server sent an invalid reply header
Err [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) dapper/main libgimp2.0 2.2.11-1ubuntu3
  The HTTP server sent an invalid reply header
Err [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) dapper/main libwmf0.2-7 0.2.8.3-3.1
  The HTTP server sent an invalid reply header
Err [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) dapper/main gimp 2.2.11-1ubuntu3
  The HTTP server sent an invalid reply header
Failed to fetch [http://au.archive.ubuntu.com/ubuntu/pool/main/g/gimp/gimp-data_2.2.11-1ubuntu3_all.deb](http://au.archive.ubuntu.com/ubuntu/pool/main/g/gimp/gimp-data_2.2.11-1ubuntu3_all.deb)  The HTTP server sent an invalid reply header
Failed to fetch [http://au.archive.ubuntu.com/ubuntu/pool/main/a/aalib/libaa1_1.4p5-30_i386.deb](http://au.archive.ubuntu.com/ubuntu/pool/main/a/aalib/libaa1_1.4p5-30_i386.deb)  The HTTP server sent an invalid reply header
Failed to fetch [http://au.archive.ubuntu.com/ubuntu/pool/main/g/gimp/libgimp2.0_2.2.11-1ubuntu3_i386.deb](http://au.archive.ubuntu.com/ubuntu/pool/main/g/gimp/libgimp2.0_2.2.11-1ubuntu3_i386.deb)  The HTTP server sent an invalid reply header
Failed to fetch [http://au.archive.ubuntu.com/ubuntu/pool/main/libw/libwmf/libwmf0.2-7_0.2.8.3-3.1_i386.deb](http://au.archive.ubuntu.com/ubuntu/pool/main/libw/libwmf/libwmf0.2-7_0.2.8.3-3.1_i386.deb)  The HTTP server sent an invalid reply header
Failed to fetch [http://au.archive.ubuntu.com/ubuntu/pool/main/g/gimp/gimp_2.2.11-1ubuntu3_i386.deb](http://au.archive.ubuntu.com/ubuntu/pool/main/g/gimp/gimp_2.2.11-1ubuntu3_i386.deb)  The HTTP server sent an invalid reply header
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?
-----------------------

Optiker

---

### Post by Lord Illidan on 2006-06-19
Do a ```
sudo apt-get update
``` in the terminal, and try again.

And if that fails, post your /etc/apt/sources.list here.

---

### Post by aysiu on 2006-06-19
Maybe the Australian mirrors are temporarily down? Or is *au* Austria?

---

### Post by Optiker on 2006-06-19
[QUOTE=Lord Illidan]Do a ```
sudo apt-get update
``` in the terminal, and try again.

And if that fails, post your /etc/apt/sources.list here.[/QUOTE]

Tried the above and it failed. Also, the "update notifier" said Ihad 5 updates available and when I ran it, it also failed - similar message to the one originally posted when I tried to install GIMP.

Here's sources.list...

----------------------------
deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) dapper main restricted
deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) dapper main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) dapper-updates main restricted
deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) dapper-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
 deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) dapper universe
 deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) dapper universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
 deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse
 deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse

# Line commented out by installer because it failed to verify:
#deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
# Line commented out by installer because it failed to verify:
#deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe
=============================

Thanks for continued assistance.
Optiker

---

### Post by aysiu on 2006-06-19
Can you try this for now (it makes a backup of your old sources.list, so you can always restore that later if it doesn't work)?

[http://www.psychocats.net/ubuntu/sources](http://www.psychocats.net/ubuntu/sources)

and then ```
sudo aptitude update
sudo aptitude install gimp
```

---

### Post by Optiker on 2006-06-19
[QUOTE=aysiu]Can you try this for now (it makes a backup of your old sources.list, so you can always restore that later if it doesn't work)?

[http://www.psychocats.net/ubuntu/sources](http://www.psychocats.net/ubuntu/sources)

and then ```
sudo aptitude update
sudo aptitude install gimp
```[/QUOTE]

DONE...here's the result...
-------------------------------------
optiker@optiker-desktop:~$ kdesu kwrite /etc/apt/sources.list
X Error: BadDevice, invalid or uninitialized input device 166
  Major opcode:  144
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 166
  Major opcode:  144
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 166
  Major opcode:  144
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 166
  Major opcode:  144
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
Link points to "/tmp/ksocket-root"
Link points to "/tmp/kde-root"
X Error: BadDevice, invalid or uninitialized input device 166
  Major opcode:  144
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 166
  Major opcode:  144
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
kbuildsycoca running...
ScimInputContextPlugin()
X Error: BadDevice, invalid or uninitialized input device 166
  Major opcode:  144
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 166
  Major opcode:  144
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
ScimInputContextPlugin()
~ScimInputContextPlugin()
optiker@optiker-desktop:~$ sudo aptitude update
Reading package lists... Done
Building dependency tree... Done
Initializing package states... Done
Building tag database... Done
Err [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security Release.gpg
  The HTTP server sent an invalid reply header
Ign [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security Release
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper Release.gpg
  The HTTP server sent an invalid reply header [IP: 85.133.25.7 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates Release.gpg
  The HTTP server sent an invalid reply header [IP: 85.133.25.8 80]
Ign [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main Packages
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports Release.gpg
  The HTTP server sent an invalid reply header [IP: 85.133.25.7 80]
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper Release
Ign [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/restricted Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates Release
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports Release
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/main Packages
Ign [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main Sources
Ign [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/restricted Sources
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/restricted Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/main Sources
Ign [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/universe Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/restricted Sources
Ign [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/universe Sources
Err [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main Packages
  Connection failed
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/universe Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/universe Sources
Err [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/restricted Packages
  The HTTP server sent an invalid reply header
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/multiverse Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/multiverse Sources
Err [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main Sources
  The HTTP server sent an invalid reply header
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/main Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/restricted Packages
Err [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/restricted Sources
  The HTTP server sent an invalid reply header
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/main Sources
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/restricted Sources
Err [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/universe Packages
  The HTTP server sent an invalid reply header
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/main Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/restricted Packages
Err [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/universe Sources
  The HTTP server sent an invalid reply header
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/universe Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/multiverse Packages
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/main Packages
  The HTTP server sent an invalid reply header [IP: 85.133.25.7 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/restricted Packages
  Connection failed [IP: 85.133.25.7 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/main Sources
  The HTTP server sent an invalid reply header [IP: 85.133.25.7 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/restricted Sources
  The HTTP server sent an invalid reply header [IP: 85.133.25.8 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/universe Packages
  The HTTP server sent an invalid reply header [IP: 85.133.25.8 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/universe Sources
  The HTTP server sent an invalid reply header [IP: 85.133.25.7 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/multiverse Packages
  Connection failed [IP: 85.133.25.7 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/multiverse Sources
  The HTTP server sent an invalid reply header [IP: 85.133.25.7 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/main Packages
  The HTTP server sent an invalid reply header [IP: 85.133.25.8 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/restricted Packages
  The HTTP server sent an invalid reply header [IP: 85.133.25.7 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/main Sources
  The HTTP server sent an invalid reply header [IP: 85.133.25.8 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/restricted Sources
  The HTTP server sent an invalid reply header [IP: 85.133.25.8 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/main Packages
  The HTTP server sent an invalid reply header [IP: 85.133.25.7 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/restricted Packages
  The HTTP server sent an invalid reply header [IP: 85.133.25.8 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/universe Packages
  The HTTP server sent an invalid reply header [IP: 85.133.25.7 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/multiverse Packages
  The HTTP server sent an invalid reply header [IP: 85.133.25.8 80]
Err [http://packages.freecontrib.org](http://packages.freecontrib.org) dapper Release.gpg
  The HTTP server sent an invalid reply header
Ign [http://packages.freecontrib.org](http://packages.freecontrib.org) dapper Release
Ign [http://packages.freecontrib.org](http://packages.freecontrib.org) dapper/free Packages
Ign [http://packages.freecontrib.org](http://packages.freecontrib.org) dapper/non-free Packages
Ign [http://packages.freecontrib.org](http://packages.freecontrib.org) dapper/free Sources
Ign [http://packages.freecontrib.org](http://packages.freecontrib.org) dapper/non-free Sources
Err [http://packages.freecontrib.org](http://packages.freecontrib.org) dapper/free Packages
  The HTTP server sent an invalid reply header
Err [http://packages.freecontrib.org](http://packages.freecontrib.org) dapper/non-free Packages
  The HTTP server sent an invalid reply header
Err [http://packages.freecontrib.org](http://packages.freecontrib.org) dapper/free Sources
  The HTTP server sent an invalid reply header
Err [http://packages.freecontrib.org](http://packages.freecontrib.org) dapper/non-free Sources
  The HTTP server sent an invalid reply header
Reading package lists... Done
optiker@optiker-desktop:~$ sudo aptitude install gimp
Reading package lists... Done
Building dependency tree... Done
Initializing package states... Done
Building tag database... Done
Couldn't find any package matching "gimp".  However, the following
packages contain "gimp" in their description:
  foomatic-db-gutenprint ijsgutenprint libijs-0.35 libgutenprint2
  cupsys-driver-gutenprint libglib2.0-0
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
-----------------------------------------

Now what...looks like a miserable failure on all counts!

Thanks!
Optiker

---

### Post by aysiu on 2006-06-19
Considering that I use that *exact* sources.list and used it today even, I would say that this message: ```
The HTTP server sent an invalid reply header
``` probably has to do with your internet configuration more than the repositories themselves.

Do you use a proxy for internet, by chance?

**Edit**: [I Googled your error and only 73 results turned up.](http://www.google.com/search?num=100&hl=en&lr=lang_en&safe=off&q=%22The+HTTP+server+sent+an+invalid+reply+header%22+&btnG=Search) That's weird. I'm not sure what's going on.

If you want your old sources.list back, just paste these commands in: ```
sudo cp /etc/apt/sources.list /etc/apt/sources.list_psychocats
sudo cp /etc/apt/sources.list_backup /etc/apt/sources.list
```

---

### Post by Optiker on 2006-06-19
[QUOTE=aysiu]Considering that I use that *exact* sources.list and used it today even, I would say that this message: ```
The HTTP server sent an invalid reply header
``` probably has to do with your internet configuration more than the repositories themselves.

Do you use a proxy for internet, by chance?[/QUOTE]

Uh....this is my work computer. I don't know, but I know I'm behind a firewall. How do I know if I'm using a proxy (sounds like a pretty dumb question, but I've never had to worry bout the details of my net connection).

Thanks!
Optiker

---

### Post by aysiu on 2006-06-19
I have no idea, as I've never had to worry about the details of my net connection either! And I don't use proxy.

I have seen other users have trouble with apt-get, though, because of proxy issues (even though their regular web browsers and email work fine).

---

### Post by Optiker on 2006-06-19
[QUOTE=aysiu]I have no idea, as I've never had to worry about the details of my net connection either! And I don't use proxy.

I have seen other users have trouble with apt-get, though, because of proxy issues (even though their regular web browsers and email work fine).[/QUOTE]

So now what? Dead end? Wipe and reinstall from scratch?

Optiker

---

### Post by aysiu on 2006-06-19
I don't know if reinstalling will help, since your internet would presumably be configured the same way, right?

You are able to do other things by internet, though, right? You can browse the web, check your email, etc. No problems there on that same connection?

---

### Post by Optiker on 2006-06-19
[QUOTE=aysiu]I don't know if reinstalling will help, since your internet would presumably be configured the same way, right?

You are able to do other things by internet, though, right? You can browse the web, check your email, etc. No problems there on that same connection?[/QUOTE]

Correct...no problems. In fact, until I tried to install GIMP, wasn't having any problems at all. I had even installed Firefox without any trouble using Adept.

Optiker

---

### Post by aysiu on 2006-06-19
That makes this situation even weirder.

So you have been able to install things with Adept... just not GIMP! I don't know what to tell you, then.

---

### Post by Optiker on 2006-06-19
[QUOTE=aysiu]That makes this situation even weirder.

So you have been able to install things with Adept... just not GIMP! I don't know what to tell you, then.[/QUOTE]

I installed Firefox right after clean install updating to Dapper. It was after that when I tried to install GIMP that it didn't work. Maybe something I did broke it.

I'll try updating on my home computer, then install these same things and see it it works. If it does, then maybe will try re-update.

Thanks!
Optiker

---

### Post by Optiker on 2006-07-03
I hate to open this can of worms again, but...

To first answer a previous question, I have had no problems using the internet, and am, in fact, replying from my Dapper installation. In addition, I installed Dapper on my computer at home, from teh same installation CD, and am having absolutely no problems using Adept. So, the followiong takes the next step in wieder yet!

I thought this problem was corrected. I noticed that I was only showing less than 2k packaged available, and I was expecting closer to 20k. So, I thought it must have somethign to do with our intranet and/or firewall. So, I finally gave up and got my company Linux IT guy in to sit down and work at it. One of the things that caught his attention was that for an apt-get update, every repository was returning an error message of the form...
-------------
Err [http://mirrors.uwa.edu.au](http://mirrors.uwa.edu.au) dapper-backports/main Packages
  The HTTP server sent an invalid reply header
-------------
I can get to [http://mirrors.uwa.edu.au](http://mirrors.uwa.edu.au) in my browser, and to get to the universe repository folder, for example, I use the URL... *[COLOR="DarkRed"]http://mirrors.uwa.edu.au/ubuntu/pool/universe/[/COLOR]*

He eventually decided that my requests from Adept, etc. were somehow rerouting and going to places that couldn't respond properly. So, he eventually replaced the sources.list with a different set of servers, and it seemed to fix the problem. I installed a few things at that time and it seemed to work. That was late in the week and when I came in the following week and tried to install something, nothing would install and I got the same kind of error messages, and the same small numbers of packages available.

My IT guy had me try replacing the URLs with a couple of others, but so far, nothing has worked. So, the reason for opening the can or worms again is that I again cannot install or update anything!

The only thing that comes to mind is that is the syntax in my sources.list correct? A typical line is as follows...
-------------
 deb [http://mirrors.uwa.edu.au/ubuntu/](http://mirrors.uwa.edu.au/ubuntu/) dapper universe
 deb-src [http://mirrors.uwa.edu.au/ubuntu/](http://mirrors.uwa.edu.au/ubuntu/) dapper universe
-------------
Suggestions are welcome and much appreciated!
Optiker

---

### Post by Optiker on 2006-07-03
I give up! Last week I couldn't make it work. This morning, I just tried it after sending the above reply, and no problem...18,303 packages available!

Is Kubuntu masculine, or feminine? :)

Optiker

---

### Post by Optiker on 2006-07-03
Guess what?

It _**[COLOR="Red"]WAS[/COLOR]**_ working!

After I sent the above reply, I used Adept to install Wine. It showed up as installed. Then I decided to try a different sources.list that I generated using the web site that lets you select the repositories, then generates the sources.list file - comebody had suggested it in one of the forums...don't have the URL handy.

I tried that and then did a kdesu aptitude update from the terminal and back to all of teh same error messages/symptoms.

Now it's broken again!

I replaced sources.list with the one that worked just before I sent the above reply, and doesn't work - it's the one that didn't work last week, worked earlier today, and back to not working!

Are we getting frustrated yet?  :confused: 

Help!

Thanks!
Optiker

---

### Post by GregMartyn on 2006-09-06
I'm having the exact same problem.

I can wget the files that apt-get mentions though, so I am very confused.

```
greg@greg-laptop:~$ sudo apt-get upgrade
Password:
Reading package lists... Done
Building dependency tree... Done
The following packages will be upgraded:
  xserver-xorg-core
1 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 3531kB of archives.
After unpacking 4096B of additional disk space will be used.
Do you want to continue [Y/n]? y
WARNING: The following packages cannot be authenticated!
  xserver-xorg-core
Install these packages without verification [y/N]? y
Err http://us.archive.ubuntu.com dapper-updates/main xserver-xorg-core 1:1.0.2-0ubuntu10.4
  The HTTP server sent an invalid reply header [IP: 146.137.96.15 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/x/xorg-server/xserver-xorg-core_1.0.2-0ubuntu10.4_i386.deb  The HTTP server sent an invalid reply header [IP: 146.137.96.15 80]
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?
```
then
```

greg@greg-laptop:~$ wget http://us.archive.ubuntu.com/ubuntu/pool/main/x/xorg-server/xserver-xorg-core_1.0.2-0ubuntu10.4_i386.deb
--23:16:04--  http://us.archive.ubuntu.com/ubuntu/pool/main/x/xorg-server/xserver-xorg-core_1.0.2-0ubuntu10.4_i386.deb
           => `xserver-xorg-core_1.0.2-0ubuntu10.4_i386.deb'
Resolving us.archive.ubuntu.com... 146.137.96.7, 146.137.96.15
Connecting to us.archive.ubuntu.com|146.137.96.7|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 3,530,826 (3.4M) [application/x-debian-package]

100%[==================================================================================================>] 3,530,826    231.17K/s    ETA 00:00

23:16:19 (226.16 KB/s) - `xserver-xorg-core_1.0.2-0ubuntu10.4_i386.deb' saved [3530826/3530826]

greg@greg-laptop:~$ 
```

..and yes, I'm posting this from my Kubuntu install.

---

