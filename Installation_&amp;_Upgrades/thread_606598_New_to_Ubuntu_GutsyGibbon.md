---
title: "New to Ubuntu GutsyGibbon"
date: 2007-11-08
forum: Installation &amp; Upgrades
---

### Post by kyouta on 2007-11-08
Hey people, i'm your average windows user ... decided to move on to linux and trying out the newbie friendly ubuntu. After doing research and manage to get it dual-booting along with my Win XP home on a Benq Joybook 5000, i encountered some problems that i hope the pros can guide me with:

1) It takes around 2-3 mins to actually load into the logon screen, which is quite long given the fast booting reputation of linux. Anything i missed out besides just installing from the live cd?

2) I want try out the fundamentals like changing wallpaper,but have absolutely no idea how to >.<. How do get those great wallpapers from art.gnome onto my desktop?

3) I understand that i can get most of the programs from sypnatic package manager. But the download time is very slow,and i also wish to learn how to install like the big boys. For a start, i wwanted to installFirestarter, but going to this page:

[http://www.fs-security.com/docs/installation.php](http://www.fs-security.com/docs/installation.php)

I was totally stumped. Being the pampered PC user, i have no idea how to browse to directories using the command prompt, HELP!

Thanks in advance for the help!

---

### Post by Sef on 2007-11-08
> 1) It takes around 2-3 mins to actually load into the logon screen, which is quite long given the fast booting reputation of linux. Anything i missed out besides just installing from the live cd?

What are your system specs?

> 3) I understand that i can get most of the programs from sypnatic package manager. But the download time is very slow,and i also wish to learn how to install like the big boys. For a start, i wwanted to installFirestarter, but going to this page:

[http://www.fs-security.com/docs/installation.php](http://www.fs-security.com/docs/installation.php)

First, firestarter (actually IPTables) is installed by default.   Firestarter itself is just a front end GUI for IPTables.   To download Firestarter:

Applications > Accessories > Terminal

Then type this command:

```
sudo apt-get update
```

(That updates your repositories.)

then type this command:

```
sudo apt-get install firestarter
```

---

### Post by bulldog on 2007-11-08
Hi,well we all are new to Gutsy in one way or another :)

Long loading time can be anything,can't say something usefull about it from my desktop.
Probably there are a lot of things [services] and it depend on your computer what you need and what not.

The walppaper is easy right click the desktop and choose change wallpaper or something like that [use the Dutch version]
The wallpapers you download with the art-manager are somewhere in your /home folder
Choose add from the change wallpaper app and point it to the art-manager wallpaper folder and choose the one you want.
Just like windows.:)

The last question is a little harder because I'm not sure what you mean.
The big boys getting their software with synaptic too,but some times something they want to use isn't in the repo's.
The easiest way to install something is finding a .deb package for your distro otherwise you have to compile it from source.
I shouldn't start with that one if you're a 'beginner' just start to read and learn your ubuntu and compiling software comes when the time is there.

---

### Post by kyouta on 2007-11-08
Thanks Sef and Bulldog for the reply! Ok system specs wise, my lappy is a pentium m 1.3 ghz, 512 ram and a ATI Mobility 9000 radeon.

For the installation part-wise, i was actually fiddling with the repositories and was able to get it to update. However, i was hoping to learn the hard way of downloading the package and manually installing as the download speed from the repositories is quite slow.

Btw, what is sudo and must it be keyed in every command? For the link i provided in my ealier post, how does one 'Navigate to the package folder' via the terminal?

Thanks for the help!

---

### Post by bulldog on 2007-11-09
Installing 'the hard way' will come in  time,do it only if you can't find it in the repo's.

Sudo means you get administrator rights for a short time or for a command.
You need to do this only when you want to perform actions,which include system files to be altered or written to.

When you want to open a application through the terminal and this application has a graphical interface,you need to do gksu instead of sudo.

Synaptic with a terminal goes ```
gksu synaptic
```
You can use ALT+F2 to open a launch box,type in the box the name of the app and hit enter.

Lots of info:

[http://psychocats.net/ubuntu/index](http://psychocats.net/ubuntu/index)

---

### Post by kyouta on 2007-11-09
Hey Bulldog thanks for the link! Will take time and read through the whole thing. Thanks!

---

