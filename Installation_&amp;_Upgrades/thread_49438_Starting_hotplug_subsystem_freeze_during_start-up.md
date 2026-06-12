---
title: "Starting hotplug subsystem freeze during start-up"
date: 2005-07-16
forum: Installation &amp; Upgrades
---

### Post by Rabelais on 2005-07-16
The title of the message says everything...
I installed Ubuntu on a machine in which there are Suse and WinXP too.
I rightly configurated GRUB (created by Suse) but when Ubuntu starts it arrives at the voice
Starting hotplug subsystem
it freezes there and I can't move it from there.
I've read that it may happen if there is a blank CD into the CD-Rom, but there is nothing in mine.
What can I do?
Maybe retry the installation configuring manually all the ethernet cards (2)??
Thanks to all!!

RB
 ](*,)

---

### Post by ProNoblem on 2005-07-16
I thought this was a common problem with Warty (4.10), you can try to upgrade to Hoary (5.04) if you have the time/internet connection through the following method:
In a terminal:
Type: $ sudo gedit /etc/apt/souces.list
Search for the words Warty and replace these with Hoary
Save the file
Return to the terminal and type apt-get update
Next, do apt-get dist-upgrade
Now you'll have a upgraded Ubuntu Hoary Hedgehog !

The other way is to disable the hotplug subsystem (If you don't want to download/install the new Ubuntu):
Open a terminal
sudo nano -w /etc/hotplug/blacklist
Go way down, and add hw_random
Save with ctrl+o

Edit: To cancel the Hotplug waiting, you can press ctrl+c, now it will pass the hotplug without trying (once)

---

