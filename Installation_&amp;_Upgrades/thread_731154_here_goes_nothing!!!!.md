---
title: "here goes nothing!!!!"
date: 2008-03-21
forum: Installation &amp; Upgrades
---

### Post by k33bz on 2008-03-21
Ok, I am curently running Fiesty Fawn on my laptop. I am going to go ahead and Install Gutsy Gibbon.

Here is the problem, only conection I have is through wireless, I have no other way to hook up to the net. The things I have done so far is saved all my things onto 2 thumb drives that I want to keep. Including the wireless drivers and WICD, as well as made an aptoncd. I already tried to get my wirelss conection going off the live cd with out any success.  What are the steps I need to do to make my conversion from 7.04 to 7.10, as far as geting my wireless set up???

As already said my only way to connect to the net is via wireless. Please help!?!?!?!

and before any one sugest, i do not do upgrades, rather have fresh install, had problems with upgrading on my desktop (which is down) from dapper to edgy, so I no longer go that route.

---

### Post by dstew on 2008-03-21
You can do a network install with [unetbootin]("http://lubi.sourceforge.net/unetbootin.html").

---

### Post by k33bz on 2008-03-21
ok, how is doing a usb bootable goin 2 help me with that

---

### Post by k33bz on 2008-03-21
[CENTER]bump[/CENTER]

---

### Post by dstew on 2008-03-21
Check out the [unetbootin site]("http://lubi.sourceforge.net/unetbootin.html"). You install unetbootin into Feisty Fawn. Presumable you can connect to the internet through your Feisty install. Unetbootin adds a boot menu item that lets you install a new Ubuntu distribution over your wireless network. It runs just like an installation CD, including a partition step.

---

### Post by k33bz on 2008-03-21
ok, let em get this right. This installation goes from over the net, installing my os onto a new partition, or will it completly over write the os I have now? Hope you say it will complelty over write my old os, dont want a seperate partition, gotta small hd, well not small, avg, but small for me.

---

### Post by dstew on 2008-03-22
Just like the Alternate Install CD, it will either overwrite your old system or you can create a new partition and dual boot. It's your choice.

EDIT: Some advice if you are going to do a network install. The installer seems to get stuck at 6%. It is actually downloading packages, but it gives you no feedback. You have to wait about an hour at DSL speeds for it to finish. If this is unnerving, you can install a base (server) system, then go into that system and do ```
sudo apt-get install ubuntu-desktop
```At least that way, you get to see the packages coming in.  Also, if the installation fails for some reason, and if you had already deleted the Feisty partition, you will be left without an operating system, and to do another network install you will have to install some minimum system, like a Debian minimal install, to try again. So, it might be good to create a say 2 Gb partition, install the server system over the network there. Then, use the server system to do Unetbootin again, and install it over the Feisty partition. That way, you won't be without an operating system at any time.

---

### Post by k33bz on 2008-03-22
wow, I think I might wait, this is my only working laptop I have at the moment, and I cannot afford to mess up during installation, its got a weak wifi connection in my opinion. 

Unless you or someone else has another option.  Like I said, I have the driver for my wireless card, as well as ndiswrapper, and a deb package of wicd.

---

### Post by zvacet on 2008-03-22
You can upgrade with alternate CD.In some very bad scenario you will still have Cd for fresh install or reinstall Feisty.You said that you backed up all important files,so you can not lose anything important.

---

### Post by Pumalite on 2008-03-22
Courage!

---

### Post by k33bz on 2008-03-22
and that is what i am asking, i was having problem installing those drivers from usb while running the 7.10 live cd

---

