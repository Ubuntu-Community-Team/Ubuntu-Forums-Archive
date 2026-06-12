---
title: "Software Centre authentication error"
date: 2012-12-29
forum: Installation &amp; Upgrades
---

### Post by swarfega on 2012-12-29
Hi all.

First apologies if this is posted in the wrong area.

I recently installed Ubuntu 12.10. I have since added a few repositories while installing various software.

However when I try to install anything from Software Centre I get the following error:

> Software can't be installed or removed because the authentication service is not available. (org.freedesktop.PolicyKit.Error.Failed: ('system-bus-name', {'name':  ':1.68'}): org.debian.apt.install-or-remove-packages

Can anyone help me remedy this please.

---

### Post by fantab on 2012-12-29
Welcome!

From the Terminal run the following command while connected to internet:

```
$ sudo apt-get update
```And then post the output you get here.

Also tell us what Ubuntu you are using. 

EDIT: Close "software center" and 'update manager' if they are running, before you run the above command.

---

### Post by swarfega on 2012-12-29
Thanks for getting back to me.

Here is the output from update: [http://pastebin.com/41KbfkNG](http://pastebin.com/41KbfkNG)

Im using Ubuntu 12.10 64-bit.

Software I've installed so far includes amarok, nvidia drivers, kde desktop, kkmail, google chrome, vlc, kvirc for starters.

---

### Post by fantab on 2012-12-29
Do you have any incomplete installations? Looks like it to me. From the Terminal run:

```
sudo dpkg --configure -a
```

Update UBUNTU using Update-Mangager. 

Then check with The Software Center to see if its working again. If yes good. If not then, From terminal run:

```
$ sudo apt-get update 
$ sudo apt-get install idle3
```

---

### Post by swarfega on 2012-12-29
I followed the instructions and it installed a few python packages.

But I'm still getting the following in software Centre:

> Software can't be installed or removed because the authentication service is not available. (org.freedesktop.PolicyKit.Error.Failed: ('system-bus-name', {'name':  ':1.88'}): org.debian.apt.install-or-remove-packages

notice the slight difference in the name numeric.

---

### Post by ibjsb4 on 2012-12-29
Could be

[https://bugs.launchpad.net/ubuntu/+source/software-center/+bug/1045186](https://bugs.launchpad.net/ubuntu/+source/software-center/+bug/1045186)

[http://askubuntu.com/questions/218961/policykit-error-when-trying-to-install-remove-programs-in-the-software-center](http://askubuntu.com/questions/218961/policykit-error-when-trying-to-install-remove-programs-in-the-software-center)

more here

[http://www.google.com/search?client=ubuntu&channel=fs&q=Software+can%27t+be+installed+or+removed+because+the+authentication+service+is+not+available&ie=utf-8&oe=utf-8](http://www.google.com/search?client=ubuntu&channel=fs&q=Software+can%27t+be+installed+or+removed+because+the+authentication+service+is+not+available&ie=utf-8&oe=utf-8)

---

### Post by swarfega on 2012-12-29
How do I do this:

> Add the below line to startup applications.

 /usr/lib/policykit-1-gnome/polkit-gnome-authentication-agent-1

---

### Post by ibjsb4 on 2012-12-29
> **swarfega said:**
> How do I do this:

Sorry, I run the Classic desktop and not familiar Unity, but look here.

[http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=add+startup+app+to+unity&as_qdr=all&sa=Google+Search&lang=en](http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=add+startup+app+to+unity&as_qdr=all&sa=Google+Search&lang=en)

---

### Post by swarfega on 2012-12-29
Im running kde 4.9.3 :D

---

### Post by ibjsb4 on 2012-12-29
> **swarfega said:**
> Im running kde 4.9.3 :D

Ok, Im still running Classic and not familiar with kde  :p

[http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=add+startup+app+to+kubuntu&as_qdr=all&sa=Google+Search&lang=en&siteurl=http%3A%2F%2Fubuntuforums.org%2Fshowthread.php%3Ft%3D2099334](http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=add+startup+app+to+kubuntu&as_qdr=all&sa=Google+Search&lang=en&siteurl=http%3A%2F%2Fubuntuforums.org%2Fshowthread.php%3Ft%3D2099334)

And welcome to the forums  :D

---

### Post by swarfega on 2012-12-29
Thanks for the welcome :D

I think I've managed to locate a place to store auto start items. In kde system config theres an option for startup and shutdown at the bottom of the list.

---

### Post by swarfega on 2012-12-29
After rebooting I can confirm that software centre is now working! Thanks for the help everyone!

---

### Post by ibjsb4 on 2012-12-29
Congratulations  :)

  [https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

---

### Post by quneur on 2013-06-16
I rather new to ubuntu so take this at what it's worth. I am having the same problems with not authenticating. I believe it has something to do with the window manager. I use E17 because of the un-windows look and finding it won't allow password authentification in Software Center or in term, ie. sudo software-center. Updates won't work either. I have to log out to default ubuntu (KDE?) in order for everything to work.

---

