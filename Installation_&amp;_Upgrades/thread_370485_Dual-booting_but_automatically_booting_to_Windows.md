---
title: "Dual-booting but automatically booting to Windows"
date: 2007-02-25
forum: Installation &amp; Upgrades
---

### Post by Genecks on 2007-02-25
Alright, I want to use dual-booting on this computer system.

Here's what I want to do:

Dual-boot with Windows Millenium and Xubuntu. Be able to turn on the computer and have it automatically go to Windows ME. Why? Because certain people don't know how to use Linux or a bootscreen. And I don't want any complaints.

When I use the computer, however, I want to use Xubuntu. I figure I would have to use some kind of boot floppy for this, right? In other words, I can setup the system to automatically load to windows; but if I want to load into Xubuntu, I have to use a floppy and use a command to get there.

How would I do all of this?
How exactly would I dual-boot this way?

Is this even dual-booting? Is this more like having Xubuntu on its own partition and using a boot floppy to access it? Would that be the better way to go about things?

How would I go about making a boot floppy for Xubuntu?

---

### Post by solar george on 2007-02-25
Once you have xubuntu installed you can change your grub menu to automatically boot into windows - you can then use the menu to select ubuntu.

---

### Post by Genecks on 2007-02-25
> **solar george said:**
> Once you have xubuntu installed you can change your grub menu to automatically boot into windows - you can then use the menu to select ubuntu.

I remember some stuff about GRUB when I was using fedora core 4. How do I get into GRUB again if it boots automatically into Windows? And will that menu show up if I want it to automatically boot into Windows ME? I don't want it to "automatically" do it by countdown.

---

### Post by eapache on 2007-02-25
It will boot automatically into the grub os list, but with a time-out to automatically boot to whatever is the default selection. So at boot it will say something like:

Ubuntu
Ubuntu Recovery
Memory Test
Windows ME

5 seconds until grub automatically boots <insert preferred os here>

It starts with Ubuntu as default os, but it is easily changed. You won't need any floppies at all, just tell people not to press arrow keys while it's booting :)

EDIT: you posted while I was typing, so I'll try to answer your other questions. You can create a grub floppy that auto-detects every time, and set the mbr to automatically boot straight to windows, but that's a lot more trouble than it's worth (and auto-configuring grub every linux boot is terribly inefficient). The simplest option is to set the timer to 1, and hide the menu unless a key is pressed, so that there is very little chance of someone stumbling on it by accident

---

### Post by Kateikyoushi on 2007-02-25
Here is how to change the default OS grub boots, you can reduce the countdown (timeout value) to one second so they don't have to wait long and boot to win while you still have time to change to linux.

If this is still disturbing can hide grub totally with uncommenting the hiddenmenu line.

---

### Post by confused57 on 2007-02-26
You might want to move your Windows ME entry just above the line:
###BEGIN AUTOMAGIC KERNELS LIST

leave the default at 0, uncomment(take out the # in front of) hiddenmenu, and change the timeout to something like 3 seconds.

This way Windows ME will boot automatically each time, there will be a prompt to press "Esc" within 3 seconds to access the grub menu, where you can choose to boot Ubuntu...no one else will really be the wiser, except you.

You might want to look over this thread:
[http://www.ubuntuforums.org/showthread.php?t=179902](http://www.ubuntuforums.org/showthread.php?t=179902)

It's for dualbooting, but it explains how to edit your menu.lst, change timeout, etc.

---

### Post by Kateikyoushi on 2007-02-26
I left out the link from my previous post. Sorry, take a look here for an in depth grub explanation.
[LINK]("http://users.bigpond.net.au/hermanzone/p15.htm#osprefernc")

---

### Post by orb9220 on 2007-02-26
[https://help.ubuntu.com/community/GrubHowto/ChangeDefaultOS](https://help.ubuntu.com/community/GrubHowto/ChangeDefaultOS)

---

### Post by Sasquatch2000 on 2008-04-14
> **solar george said:**
> Once you have xubuntu installed you can change your grub menu to automatically boot into windows - you can then use the menu to select ubuntu.

How does one do this? I don't see any language in the installer saying how to install to allow "dual booting". I thought it was installing right over Windows. This is very unclear.

---

