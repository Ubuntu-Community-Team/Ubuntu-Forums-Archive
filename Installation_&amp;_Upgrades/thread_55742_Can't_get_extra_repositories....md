---
title: "Can't get extra repositories..."
date: 2005-08-10
forum: Installation &amp; Upgrades
---

### Post by Yorak on 2005-08-10
I am using Kubuntu and followed ubuntuguide.org's guide to installing extra repositories...when I tried typing them into Konsole, it did nothing for the first command, and second command said gedit didn't exist.

---

### Post by heimo on 2005-08-10
Subsitute gedit with some KDE editor, perhaps kedit

If with first command you mean:
 ```
sudo cp /etc/apt/sources.list /etc/apt/sources.list_backup
``` 
.. when it succeeds, it doesn't give any output, so it probably went fine. You can confirm this by checking that new file was created:
 ```
ls -l /etc/apt/sources.list_backup

```

---

### Post by Yorak on 2005-08-10
Just downloaded it today and I don't know what I'm doing...

I don't know what kind of editor I have, I don't think I have any. Is there some editor I can get with regular repositories?

---

### Post by heimo on 2005-08-10
I don't know KDE too well, but it definitely has some editor installed by default. You can use any text editor to make those changes, just need to save it as text file. I believe kedit is one of those editors you have installed, so you can put kedit in place of gedit and you should be able to edit sources.list.

Other (text-based, "terminal") editors: nano, pico, emacs - it's possible that you also have xemacs installed. Any of those editors is fine. I recommend kedit, if that doesn't work, try nano.

---

### Post by Yorak on 2005-08-10
Alright, now anytime I try to install something, this is what I get:

root@MARK3:/home/yorak # apt-get install azureus
E: Type '' is not known on line 1 in source list /etc/apt/sources.list
E: The list of sources could not be read.
root@MARK3:/home/yorak #

I think I messed something up, Synaptic won't load right now either. Any suggestions?

---

### Post by heimo on 2005-08-10
Check the sources.list file, if possible copy paste it on this forum. You probably have "syntax error", some line split on two lines which shouldn't or something like that. Not a major problem. All the lines that don't begin with deb or deb-src should begin with symbol # (which marks that this line is just a comment).

---

### Post by Yorak on 2005-08-10
I found out I can open it in Open Office, anyways I think I saved something wrong because if I try to open it again I get:

root@MARK3:/home/yorak # openoffice /etc/apt/sources.list
Xlib: connection to ":0.0" refused by server
Xlib: No protocol specified

Xlib: connection to ":0.0" refused by server
Xlib: No protocol specified

/usr/lib/openoffice/program/soffice.bin X11 error: Can't open display: :0.0
   Set DISPLAY environment variable, use -display option
   or check permissions of your X-Server
   (See "man X" resp. "man xhost" for details)
root@MARK3:/home/yorak #

---

### Post by heimo on 2005-08-10
Well... it's time to take advantage of that backup file you created:
```
sudo cp /etc/apt/sources.list_backup /etc/apt/sources.list

```
this copies the backup file over the current configuration file and you can try to make the changes again. If you use OpenOffice.org, save as text.

---

### Post by Yorak on 2005-08-10
## Uncomment the following two lines to fetch updated software from the network
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary main restricted

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary universe
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary universe

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security main restricted

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security universe

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hoary multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hoary multiverse

## Backports
deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) hoary-backports main universe multiverse restricted
deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) hoary-extras main universe multiverse restricted



There it is.

---

### Post by heimo on 2005-08-10
At a quick glance, it looks just fine. I would run this in terminal (open Applications->System Tools->Terminal):

to update list of programs available from repositories (dpkg package database):
```
sudo apt-get update

``` 

to upgrade packages that are upgradable
```
sudo apt-get upgrade

``` 

to install package called "put_package_name_here":
```
sudo apt-get install put_package_name_here

``` 

Or you can just try to use synaptic, hit refresh button, search package you want installed, right click to select for installation and hit apply (I don't know the exact steps, but it's something like that).

Do you get any errors?

I recommend using some "simple" text editor and not "word processor" like OpenOffice to edit configuration files. You can also edit repositories list (sources.list) through synaptic (I think).

---

### Post by Yorak on 2005-08-10
Anytime I put apt-get anything, I get:

E: Type '' is not known on line 1 in source list /etc/apt/sources.list

So if I have everything else in that text file right I have no idea what to do. This is extremely fustrating since I've tried everything, and the repositories are at the center of everything I need to do.

---

### Post by Yorak on 2005-08-10
Okay, I'll try to explain this part, it's kinda weird. When I use Konsole to open up the file, it opens, when I go to save as, here is what I see.a folder that is called "apt.conf.d", and within that folder is "sources.txt". When I try to rename it to sources.list, it still doesn't work.

---

### Post by heimo on 2005-08-10
And is that after you copied the backup file back to /etc/apt/sources.list?

Run:
```
head -1 /etc/apt/sources.list

``` 
what did you get?

Then try copying the backup file over the actual configuration file:
 ```
sudo cp /etc/apt/sources.list_backup /etc/apt/sources.list

``` 
and do update again

If that fails - run *apt-setup*

---

### Post by heimo on 2005-08-10
[QUOTE=Yorak]Okay, I'll try to explain this part, it's kinda weird. When I use Konsole to open up the file, it opens, when I go to save as, here is what I see.a folder that is called "apt.conf.d", and within that folder is "sources.txt". When I try to rename it to sources.list, it still doesn't work.[/QUOTE]

sources.list file exists and it's in directory /etc/apt/. You don't need to make it yourself from scratch.

---

### Post by Yorak on 2005-08-10
I get this: ## Uncomment the following two lines to fetch updated software from the network

The update still didn't work.

I am using Kubuntu, and when I do the apt-setup it says there is a non-Ubuntu CD in.

---

### Post by heimo on 2005-08-10
[QUOTE=Yorak]I get this: ## Uncomment the following two lines to fetch updated software from the network

The update still didn't work.

I am using Kubuntu, and when I do the apt-setup it says there is a non-Ubuntu CD in.[/QUOTE]

Hmm... don't choose cdrom on the first question "Archive access method for apt". Choose http or ftp.

EDIT: remember to use *sudo apt-setup*

---

### Post by Yorak on 2005-08-10
Okay, got the setup to work. Hey do you have AIM or MSN? It would be alot easier to discuss that way. Just PM me your info if ya want. Thanks for all your help btw, it's my destiny to get the extra repositories working by the end of today.  :razz:

---

### Post by heimo on 2005-08-10
[QUOTE=Yorak]Okay, got the setup to work. Hey do you have AIM or MSN? It would be alot easier to discuss that way. Just PM me your info if ya want. Thanks for all your help btw, it's my destiny to get the extra repositories working by the end of today. :razz:[/QUOTE]

:) Takes some time at first when you have so many new things, new text editors, a bit different graphical user interface and new concepts to understand, but soon it'll be "second nature". I'm confident you can do it, just take it step by step and don't get frustrated.

I don't use instant messaging, sorry.

---

### Post by Yorak on 2005-08-10
So, after the setup, do I do the whole shabang over again?

---

### Post by heimo on 2005-08-10
[QUOTE=Yorak]So, after the setup, do I do the whole shabang over again?[/QUOTE]

Go ahead - follow the ubuntuguide, but use another editor. Don't use OpenOffice.org.
[http://www.ubuntuguide.org/#extrarepositories](http://www.ubuntuguide.org/#extrarepositories)

---

### Post by Yorak on 2005-08-10
I know man, but the only other editor on Kubuntu is Kate, and it doesn't work, it crashes upon loading. I don't understand how to download programs from the internet with Linux and install them...I only know how to do apt-get...and I can't apt-get another editor without the extra repositories.

---

### Post by heimo on 2005-08-10
[QUOTE=Yorak]I know man, but the only other editor on Kubuntu is Kate, and it doesn't work, it crashes upon loading. I don't understand how to download programs from the internet with Linux and install them...I only know how to do apt-get...and I can't apt-get another editor without the extra repositories.[/QUOTE]

nano is probably installed? [i]sudo nano /etc/apt/sources.list 
[/i]

---

### Post by Yorak on 2005-08-10
Okay I tried nano and this is what I got:

## Uncomment the following two lines to fetch updated software from the network
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary main restricted

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary universe
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary universe

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security main restricted

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security universe

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hoary multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hoary multiverse

## Backports
deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) hoary-backports main universe multiverse restricted
deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) hoary-extras main universe multiverse restricted

It looks right to me...

---

### Post by heimo on 2005-08-10
[QUOTE=Yorak]Okay I tried nano and this is what I got:

## Uncomment the following two lines to fetch updated software from the network
deb [http://us.archive.ubuntu.com/ubuntu]("http://us.archive.ubuntu.com/ubuntu") hoary main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu]("http://us.archive.ubuntu.com/ubuntu") hoary main restricted

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
deb [http://us.archive.ubuntu.com/ubuntu]("http://us.archive.ubuntu.com/ubuntu") hoary-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu]("http://us.archive.ubuntu.com/ubuntu") hoary-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://us.archive.ubuntu.com/ubuntu]("http://us.archive.ubuntu.com/ubuntu") hoary universe
deb-src [http://us.archive.ubuntu.com/ubuntu]("http://us.archive.ubuntu.com/ubuntu") hoary universe

deb [http://security.ubuntu.com/ubuntu]("http://security.ubuntu.com/ubuntu") hoary-security main restricted
deb-src [http://security.ubuntu.com/ubuntu]("http://security.ubuntu.com/ubuntu") hoary-security main restricted

deb [http://security.ubuntu.com/ubuntu]("http://security.ubuntu.com/ubuntu") hoary-security universe
deb-src [http://security.ubuntu.com/ubuntu]("http://security.ubuntu.com/ubuntu") hoary-security universe

deb [http://archive.ubuntu.com/ubuntu]("http://archive.ubuntu.com/ubuntu") hoary multiverse
deb-src [http://archive.ubuntu.com/ubuntu]("http://archive.ubuntu.com/ubuntu") hoary multiverse

## Backports
deb [http://ubuntu-backports.mirrormax.net/]("http://ubuntu-backports.mirrormax.net/") hoary-backports main universe multiverse restricted
deb [http://ubuntu-backports.mirrormax.net/]("http://ubuntu-backports.mirrormax.net/") hoary-extras main universe multiverse restricted

It looks right to me...[/QUOTE]

It's identical to the one on Ubuntuguide.

---

### Post by Yorak on 2005-08-10
Exactly, so I don't see why it shouldn't work...I still get this when I try to update:

yorak@MARK3:~$ sudo -s -H
Password:
root@MARK3:/home/yorak # apt-get update
E: Type '' is not known on line 1 in source list /etc/apt/sources.list
root@MARK3:/home/yorak #

---

### Post by Yorak on 2005-08-10
Okay I'm going to try something...how do I save over the sources.list with Nano?

---

### Post by Yorak on 2005-08-10
Okay, I got it, Thanks a bunch pal.

---

