---
title: "Internet upgrade problem"
date: 2007-04-20
forum: Installation &amp; Upgrades
---

### Post by Balaam's Miracle on 2007-04-20
I too am one of those that tried to upgrade from Edgy to Feisty using the update manager, only to find out that it was just not happening.
I've tried to figure out why it wouldn't work for me and here's the things i've tried:

**1: Using the first method from [http://www.ubuntu.com/getubuntu/upgrading](http://www.ubuntu.com/getubuntu/upgrading).**
This is my preferred method because it would initiate the upgrade with a single click. But what happens after clicking the "upgrade" button is that for a long time the update manager looks as if it hangs, but if i let it sit and not kill the process, eventually a dialog box comes up saying:
[INDENT]Could not download the release notes
Please check your internet connection[/INDENT]
There doesn't seem to be anything wrong with my connection though, because i have been surfing the net, checking mail and more of that stuff without any problems in the last 24 hours.
Trying something else then.

**2: Changed the location of the repos in System => Administration => Software Sources.**
My default location is the repository for the Netherlands because that's where i live. I figured that maybe the server was so busy that it couldn't handle the load and changing the repo might help in that case.
So i've changed from the server for the Netherlands to the server for the UK but that did not make any difference. Neither did changing to the main server so i've changed everything back to the server for the Netherlands.

**3: Started update-manager from within a terminal to see if there were any errors.**
This only  showed the following error:
[FONT="Courier New"]$ /usr/bin/update-manager 
Introspect error: The name org.freedesktop.UpdateManager was not provided by any .service files
no listening object (The name org.freedesktop.UpdateManager was not provided by any .service files) [/FONT]
I don't know what this error means, but since this message showed immediately after starting the update manager, i don't think that this causes update-manager not to upgrade.
Clicking the upgrade button does not produce any additional errors in the terminal but it does produces the same results as method #1 (faux stall + dialog box).

**4: Using the official upgrade method from [http://ubuntuforums.org/showthread.php?t=286599](http://ubuntuforums.org/showthread.php?t=286599)**
[FONT="Courier New"]$ gksu "update-manager -c"
warning: could not initiate dbus[/FONT]
The error message is given after entering the password, which was to be expected.
Clicking the "upgrade" button again did not produce any additional errors in the terminal. The symptoms as under #1 still apply.

**5: Replacing my edited sources.list with the backed up default one.**
This did not work either, same problem...

I can't begin to speculate what it is exactly that goes wrong here. I don't think it's the server load but obviously update-manager encounters some kind of error when retrieving package info. Just what package (or packages) it is that prevents my upgrade is a question that i can't answer.
Normal software updates still happen, so i have ruled out the possibility that update-manager might be broken.

I could have tried another method, using apt-get, but i didn't for fear of a possible incomplete upgrade which in the worst case would make it necessary for me to do a complete reinstall.

I have now downloaded and burned the alternate CD and will try upgrading that way tonight.
Anyway, maybe this description helps in figuring out what goes wrong in my case and why...

---

### Post by Paul41 on 2007-04-20
I was having the same problem you were having with the first option. I think there were just too many people on the server trying to download. I finally got it going this morning.

---

### Post by Balaam's Miracle on 2007-04-20
> **Paul41 said:**
> I was having the same problem you were having with the first option. I think there were just too many people on the server trying to download. I finally got it going this morning.

Upgrading with the alternate CD worked. But it did uninstall some stuff that i regularly use. To name but 3: Cream, Deluge and Amarok. Why Amarok? It beats me, but at least i have done the upgrade, now to reinstall the  programs i've lost.
About the uninstalls, it didn't remove a whole lot of programs, but enough to leave me slightly annoyed and puzzled. Luckily, the config files in my homedir were left untouched so i will get all of the settings 'n stuff back after installing those programs again.

---

### Post by spacedoubtman on 2007-04-25
I had the same thing and read somewhere to stop firestarter - seemed to work

maybe to do with not allowing icmp traffic on my firewall

---

