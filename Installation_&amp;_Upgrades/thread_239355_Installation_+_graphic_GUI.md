---
title: "Installation + graphic GUI"
date: 2006-08-19
forum: Installation &amp; Upgrades
---

### Post by YigalB on 2006-08-19
My target is to install Ubuntu+GUI+ games for kids (i found Gcompris intersting.
1- I downloaded the Sever install CD (because I want it to run from the hard drive), but I dot no graphic GUI. What GUI and how do I install GUI?
2- I followed the installation and login into my user ID. How do I login the root? I think I must be also a root in order to install and maintain.
3- The only Gcompris download I found (again - on hard drive) was with torrent. I never used torrents - and other way to do it? or... recommend me easy to use torent software?

Thanks!

---

### Post by HanZo on 2006-08-19
1. I'd say you'd better use the regular install cd, not the server one. server install is for setting up a server, and as far as I can read you don't want that, do you? the regular install cd boots as a live cd, then you just have to click on the install icon on the desktop and answer the usual questions... in 20 minutes on a new computer you should have everything set up.
if by GUI you mean window manager/desktop environment, the default is gnome and is installed automatically (server install maybe lacks the GUI, since you don't really need it... but I'm just guessing since I never installed an Ubuntu server).
2. root is disabled in ubuntu but you can have all the root functionality by using the command "sudo"
example, if you want to edit a system file from console, like xorg.conf you'll just type:
sudo gedit xorg.conf
the system will ask you for your user password and ther you go.
3. I'm not running ubuntu right now, but I suggest you take a look at synaptic (the software management tool) you'll find it in the gnome menu System>Administration. take a look at wiki.ubuntu.com to learn some more on how to install software, repositories and all the other stuff.
A good bittorrent client is Azureus (well... it's the best IMHO), you'll find it in Synaptic.

---

### Post by ajgreeny on 2006-08-19
Login to your user account, then in the terminal type:-
sudo apt-get install ubuntu-desktop
for the gnome version (Ubuntu), or:-
sudo apt-get install kubuntu-desktop
for the KDE version (Kubuntu), or
sudo apt-get install xubuntu-desktop for the xfce desktop version (Xubuntu).

You can then add gcompris easily using synaptic or still using apt-get if you prefer that way.

---

### Post by YigalB on 2006-08-19
HanZo: thanks. Good advise. I was thiking that LiveCD is Live only - I didnt know you can install from it. I started downloading it but it seems SO slow. in 11 hours I will have it.
I was stuck at the "root" things from the Unix I used to work with years ago. 

Ajgreeny: Thanks, I followed your advice and it start working installing the xubuntu. However, it started to ask me to change CD media, and all I have is the Server CD. Can I tell it to take whatever it needs from the web? I am stucked at this point

---

### Post by HanZo on 2006-08-19
in fact  ajgreeny's solution is better if you don't want to download a new cd... full desktop live cd is a bit larger than server i suppose.

anyway if you succeded in installing the server version you should have the base system running just fine... you just need the x-k-ubuntu-desktop files... are you sure you have internet access? synaptic is just a frontend to apt-get, which is a console app and uses a config file called sources.list wich can be found under /etc/apt/ (if my memory does not fail me... otherwise somebody pls correct me).
do the following... try this:
nano /etc/apt/sources.list
it should look something like this:
```
deb-src http://au.archive.ubuntu.com/ubuntu/ dapper main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://au.archive.ubuntu.com/ubuntu/ dapper-updates main restricted
deb-src http://au.archive.ubuntu.com/ubuntu/ dapper-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://archive.ubuntu.com/ubuntu/ dapper universe main restricted multiverse
deb-src http://au.archive.ubuntu.com/ubuntu/ dapper universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://au.archive.ubuntu.com/ubuntu/ dapper-backports main restricted universe multiverse
deb-src http://au.archive.ubuntu.com/ubuntu/ dapper-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu dapper-security main restricted
deb-src http://security.ubuntu.com/ubuntu dapper-security main restricted
deb http://security.ubuntu.com/ubuntu dapper-security universe
deb-src http://security.ubuntu.com/ubuntu dapper-security universe

```

if you don't have all this stuff in the file maybe you just don't have the repositories in apt... which would really surprise me.. but you never know... otherwise maybe the install did not recognize the network card. unfortunately I don't remember how you can check that... but I'm sure somebody here knows how.

---

### Post by YigalB on 2006-08-19
When I did the nano command i got into somekind of an editor, which was empty inside. What does it mean?

Also, how do I check my internet connection? I think the installation found it alright, but now I dont know how to check it from the command line.

I dont mind downloading again the new CD, if it will solve the problems easier. Does it matter from which region do I download it ? (i.e. is the file region-depended?)

---

### Post by HanZo on 2006-08-19
I'm not the uber-linux-guru... kind of newb myself nut I'd say the easiest way to solve all the problems is to just download a new cd.
I don't think it matters where you download it from... it's always the same iso, just download speed could vary, so choose the one nearest to you. all regional settings, like language and stuff can be set during istall.

---

### Post by ajgreeny on 2006-08-20
If you're still having problems I think hanZo is right, it's easiest to just download a new iso of whichever desktop version you prefer, and go from there.  It does sound as though you have a dead network connection to the internet from your server install which will make it impossible to get the various desktops from the repos.
Good luck if you're still trying.

---

### Post by YigalB on 2006-08-20
Thanks guys.
I downloaded the CD from other location. This was MUCH faster and it worked great. 

So now I got Linux running, but I am sure I will come up with other issues.

Thanks again - case closed.

---

### Post by HanZo on 2006-08-20
you're welcome! you'll certainly encounter some other problems soon :D sp, if you get stuck, just ask!

---

