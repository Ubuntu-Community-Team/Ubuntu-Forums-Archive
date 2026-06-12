---
title: "ubuntu on an external drive without the alternate cd or a broken windows MBR"
date: 2007-08-08
forum: Installation &amp; Upgrades
---

### Post by defrex on 2007-08-08
Hello, and thanks in advance for the help.

I'm trying to install Ubuntu on an external hard drive without borking windows on the internal drive. That is, I want to be able to switch off the external and have windows boot normally.

I'm aware that this is done by putting grub on the external, and not erasing the windows MBR. However, it seems the only way to do this is with the alternate install cd (the live cd puts grub on hd0 automatically).

However, I'm using a brand new Dell system which only accepts DVI monitors, and it refuses to display the resolution that the alternate wants to put out. Damn pretentious computer.

All that is to say, does anyone know a way of installing ubuntu, with grub not on hd0, without using the alternate install cd?

---

### Post by MQMike on 2007-08-08
Use the regular Live CD.
Choose manual partitioning method.
Work through the simple 6 steps.
At Step 6, see the Advanced button at the lower right?
Click it.
Behind that you will find a chance to specify where to put GRUB.
You type it in the box, (hdx) or (hdx, y).

---

### Post by defrex on 2007-08-08
Ah, I hadn't noticed an advanced button. Than you, sir.

---

### Post by MQMike on 2007-08-08
Ah, don't feel bad, you are not alone!  I found it quite by chance.  :)

---

### Post by Saponsky09 on 2007-08-08
I also have the same problem, for the boot loader i put (sdb), it says (hd0) by default, but i couldn't install it on my hard drive i think "sdb" is wrong. Does anyone knows how to find out which one is my external hard drive??? I read on the previous reply something about hdx and hdx, y. Are those external drive's path by default or something?

---

### Post by merlinus on 2007-08-08
If you want grub on your second hard drive, then it is (hd1).  Numbering for these things starts at zero.

-merlin

---

### Post by MQMike on 2007-08-08
Two methods to find out what’s on your hard drives:

--   The 
sudo fdisk –lu 
command at the Ubuntu Terminal prompt.  It gives you a list of your hard drives and filesystems.  (-lu is “l” as  in “list,” “u” as in “units.”)

--   Or, 
at a GRUB prompt, grub>, try geometry (hdz), for some specific z value, and see if you recognize what comes back for that drive.
Try
geometry (hd0)
geometry (hd1)
… etc …

(To get a GRUB prompt, get a regular Ubuntu terminal (perhaps using a Live Ubuntu CD if necessary) and type sudo grub, press Enter, wait awhile, and up it comes:  grub>)

---

### Post by Saponsky09 on 2007-08-08
but how do I find out which one is my external hard drive? ( i'm not sure "hd1" is my external drive)

---

### Post by merlinus on 2007-08-08
```

sudo fdisk -l

```

should give you a list of your drives and partitions.

You can run this command in a terminal using a live cd, if you cannot boot into ubuntu.

-merlin

---

### Post by Saponsky09 on 2007-08-08
thanks MQMike, the Grub prompt will do it, thank you very much

---

### Post by Saponsky09 on 2007-08-08
here i am again, I checked my externall hard drive with the grub prompt and found out it was hd1 :s, sorry i'm a noob on this.  The installation went perfect so far and the boot loader was installed on my external hard drive. Now the problem starts when I'm asked to eject the CD and restart.  I did it and when I get the message "eject the tray, remove the cd and close it if any" "Press enter to continue" I do all the steps but when I hit enter NOTHING happens, I waited a while but Nothing so i had to turn off the power and when I reboot I'm prompted to choose which OS I wan to use but when I go with Ubuntu it says ERROR 17: Cannot mount the partition .  Any idea??? (sorry for the extensive message but i wanted to be clear :D)

---

### Post by Saponsky09 on 2007-08-08
Maybe the problem starts at the point that the system won't restart well from the live CD, I really dunno.  When I run from the live CD i have the same "won't restart" problem. Tanx for any help.

---

### Post by confused57 on 2007-08-09
> **Saponsky09 said:**
> here i am again, I checked my externall hard drive with the grub prompt and found out it was hd1 :s, sorry i'm a noob on this.  The installation went perfect so far and the boot loader was installed on my external hard drive. Now the problem starts when I'm asked to eject the CD and restart.  I did it and when I get the message "eject the tray, remove the cd and close it if any" "Press enter to continue" I do all the steps but when I hit enter NOTHING happens, I waited a while but Nothing so i had to turn off the power and when I reboot I'm prompted to choose which OS I wan to use but when I go with Ubuntu it says ERROR 17: Cannot mount the partition .  Any idea??? (sorry for the extensive message but i wanted to be clear :D)

You can try highlighting your Ubuntu entry in your grub boot menu, press "e", then highlight the line with root, press "e" again, change root from (hd1,x) to (hd0,x) press "enter", then press "b" to boot...x means leave this entry as it is.  You can make this change permanent in your /boot/grub/menu.lst, if it works.

---

### Post by donovan1983 on 2007-08-09
> **Saponsky09 said:**
> here i am again, I checked my externall hard drive with the grub prompt and found out it was hd1 :s, sorry i'm a noob on this.  The installation went perfect so far and the boot loader was installed on my external hard drive. Now the problem starts when I'm asked to eject the CD and restart.  I did it and when I get the message "eject the tray, remove the cd and close it if any" "Press enter to continue" I do all the steps but when I hit enter NOTHING happens, I waited a while but Nothing so i had to turn off the power and when I reboot I'm prompted to choose which OS I wan to use but when I go with Ubuntu it says ERROR 17: Cannot mount the partition .  Any idea??? (sorry for the extensive message but i wanted to be clear :D)
At what point does it give you that error? If it is Linux giving you that error (as opposed to GRUB), then it's because the Linux kernel may not have the right drivers for your external drive built into the kernel. Or in other words, Ubuntu just doesn't support booting from that drive. What type of external drive do you have? As in USB, FireWire, eSATA, etc.

And I've experienced the "won't reboot" issue on the Live CD when installing on my iBook and when trying the Live CD on my desktop, so you aren't the only one ;)

---

### Post by Saponsky09 on 2007-08-09
Ok, the error comes when I boot the machine and the options of the OS's comes, I choose Ubuntu and right after that comes the screen with : Error 17: can't mount the partition (or something like this). And my external hard drive is connected via usb. Anyone knows how to resolve the problem about the drivers?

About the reply for changing root from (hd1,x) to (hd0,x) doesn't it affects if I want to boot Ubuntu only when my external drive is connected?

---

### Post by Saponsky09 on 2007-08-09
Ok apparently the boot error was corrected by changing root from (hd1,0) to (hd0,0) Thanx a lot for your help! Now the only problem is that when the X window loads it stays still with dotted screen and the boot won't go any further :(.  I had the same problem with the live CD but when I changed the VGA options to 1024 x 768 x 16 everything went out perfect. Anyone knows how to change the VGA options when booting? how do I make those changes permanent?

---

### Post by confused57 on 2007-08-09
> **Saponsky09 said:**
> Ok apparently the boot error was corrected by changing root from (hd1,0) to (hd0,0) Thanx a lot for your help! Now the only problem is that when the X window loads it stays still with dotted screen and the boot won't go any further :(.  I had the same problem with the live CD but when I changed the VGA options to 1024 x 768 x 16 everything went out perfect. Anyone knows how to change the VGA options when booting? how do I make those changes permanent?

You can edit your xorg.conf file, open a terminal(Applications---Accessories---Terminal):
```
cd /etc/X11
sudo cp xorg.conf xorg.conf_backup
gksudo gedit xorg.conf
```
Make sure to enter an uppercase X, followed by (one)(one).

Near the bottom of your xorg.conf file, change the "Default Depth" from 24 to 16...then make "1024x768", with quotes,  the first resolution listed in the Mode Line 16...You might want to remove any higher resolutions from this line.  Quit & Save.

Also, to permanently change your root to (hd0,0):
```
cd /boot/grub
sudo cp menu.lst menu.lst_backup
gksudo gedit menu.lst
```
menu.lst is short for menu.list

In the line with #groot, change your root to (hd0,0)...leave the # in front of groot.  Quit & Save.

Then from a terminal, run:
```
sudo update-grub
```

Added:  You can mount your root partition, using the Ubuntu live cd, then make the changes to your xorg.conf:
[http://users.bigpond.net.au/hermanzone/p10.htm#Mounting_Ubuntu_with_Dapper_Desktop_LiveCD](http://users.bigpond.net.au/hermanzone/p10.htm#Mounting_Ubuntu_with_Dapper_Desktop_LiveCD)

---

