---
title: "New territory for me"
date: 2008-03-20
forum: Installation &amp; Upgrades
---

### Post by djmoore85 on 2008-03-20
Hey yall I am new at Linux in general, I am getting tired of Windows BS and want something more flexible and more customizable for me and my needs. Here's my setup: basic laptop, wireless card of course, and an external that I pretty much run everything off of. I have parted magic for my partitioner, however when I went to install Ubuntu from the LiveCD, I can't make it install to the partition I set aside for it so I can run XP and Ubuntu until I get everything compatible and moved over to Ubuntu. I am looking for what root file system I need to use for Ubuntu's partition, what steps I need to take so that when I start my computer it will give me the choice to boot either windows or Ubuntu, just a general instruction on what I need to be doing when I go to install Ubuntu. Any help or information yall can give me is much appreciated.

---

### Post by dstew on 2008-03-20
If you are able to run the Live CD, you should be able to install Ubuntu from there. It seems you got stuck on the partitioning step. It seems you created a partition using Partition Magic before you started to install Ubuntu, correct? Once you get to the partitioner step, select Manual, and take a screenshot of the partitioner window (Alt-PrtScr). Post the screenshot to the forum.

---

### Post by confused57 on 2008-03-20
> **djmoore85 said:**
> Hey yall I am new at Linux in general, I am getting tired of Windows BS and want something more flexible and more customizable for me and my needs. Here's my setup: basic laptop, wireless card of course, and an external that I pretty much run everything off of. I have parted magic for my partitioner, however when I went to install Ubuntu from the LiveCD, I can't make it install to the partition I set aside for it so I can run XP and Ubuntu until I get everything compatible and moved over to Ubuntu. I am looking for what root file system I need to use for Ubuntu's partition, what steps I need to take so that when I start my computer it will give me the choice to boot either windows or Ubuntu, just a general instruction on what I need to be doing when I go to install Ubuntu. Any help or information yall can give me is much appreciated.
Here's an excellent guide for installing with the desktop live cd:
[http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)

You should be able to use gparted on the live cd(System---Administration---Gnome Partition Editor), resize the partition you set up for Ubuntu by 1 Gb, which you'll need for  a swap partition.  Then when you install Ubuntu, select "Manual" partitioning, for your root partition, you can select primary partition, mountpoint /(not /root), format as ext3...then for the 1 Gb you freed up, select as a logical(or extended) partition, mountpoint swap, formatted as swap.  Grub should add an entry to boot both Ubuntu and Windows.

I would recommend that you burn a copy of the Super Grub Disk, before installing Ubuntu:
[http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html)

This should help on partitioning basics:
[http://www.users.bigpond.net.au/hermanzone/p17.htm#help_on_partitioning](http://www.users.bigpond.net.au/hermanzone/p17.htm#help_on_partitioning)

---

### Post by djmoore85 on 2008-03-22
Hey yall thnk you so much for the help. Only have a couple issues now after install. Every other time my computer boots up GRUB works fine. But only every other time. I also can't get Ubuntu to load unless it is in recovery mode. I talked to a co-worker who is running a quad-booting system in his home and he suggested reloading GNOME from the recovery mode, and if that didn't work to re-install ubuntu altogether. My question is, how do I reload/reinstall GNOME from the command line? And how do I get GRUB to pop up every time I turn on my computer instead of every other time? Thank you again for any help, this is going to be a good learning experience for me

---

### Post by PmDematagoda on 2008-03-22
Did you try booting the normal mode of Ubuntu with no splash?

You can do this by:-
1) Pressing "E" at the GRUB entry for Ubuntu(normal).

2) Change the word "splash" to "nosplash".

3) Pressing "B" to boot Ubuntu with the new settings.

If that works then you can make the change permanent.

---

### Post by djmoore85 on 2008-03-22
Thanx man I appreciate it, that helped out. Now my question is how to make the change permanent, and also will that fix my problem with GRUB only loading every other time the computer is started? And last thing, how do I get Ubuntu to load up and log into my home's wireless network?

---

### Post by PmDematagoda on 2008-03-22
> **djmoore85 said:**
> Thanx man I appreciate it, that helped out. Now my question is how to make the change permanent, and also will that fix my problem with GRUB only loading every other time the computer is started? And last thing, how do I get Ubuntu to load up and log into my home's wireless network?

I am not sure about the wireless network, but concerning the boot parameter change:-

1) Open the menu.lst file for editing with:-
```
gksudo gedit /boot/grub/menu.lst
```

2) Go to the GRUB menu entry of the normal Ubuntu boot(usually found near the last lines).

3) Make the change and save the file.

That should fix your booting problem.

---

### Post by Kiri on 2008-03-22
> **djmoore85 said:**
>  And last thing, how do I get Ubuntu to load up and log into my home's wireless network?

Once you choose the network and put in the password etc in ubuntu and get it connected, it should connect automatically every time you boot into ubuntu I think

---

### Post by djmoore85 on 2008-03-22
I will go ahead and edit that line in and let you know how it went. My issue with the network is how do I make it recognize the wireless card, it's a built-in with the laptop, Broadcom 802.11b/g WLAN is the card.

*EDIT* Thanks for that code line it worked great, no problems booting into Ubuntu anymore. Now I need to figure out what my network key is for my wireless network, my wife threw out the paper from the cable company that has the key and network ID on it, and I don't know how to find the key in windows. Any suggestions?

---

