---
title: "installing Ubuntu 7.04
the Feisty Fawn but no partition found"
date: 2007-03-25
forum: Installation &amp; Upgrades
---

### Post by hatari on 2007-03-25
I am trying to install Ubuntu 7.04-the Feisty Fawn on my laptop from a liveCD. When I double click on the install icon on the desktop, I get asked the time zone, keyboard and then the problem starts on the next screen: Prepare disk space.

I have two options: 

Guided
Manual

When I click Guided and click next, nothing happens. When I click Manual and click next I get the Prepare Partitions screen but the box is empty. I do not see any partitions.

What should I do next? I want to install this as a dual boot with my Vista on my second hard drive.

---

### Post by mardawi on 2007-03-25
I'm not an expert and i'm having partitions problems myself, but i was reading about GParted liveCD and it seems it can help in resizing the vista partition, but you will have to re-install vista afterwards (that's what they say)

[http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php)

good luck!

---

### Post by bulldog on 2007-03-25
> **hatari said:**
> I am trying to install Ubuntu 7.04-the Feisty Fawn on my laptop from a liveCD. When I double click on the install icon on the desktop, I get asked the time zone, keyboard and then the problem starts on the next screen: Prepare disk space.

I have two options: 

Guided
Manual

When I click Guided and click next, nothing happens. When I click Manual and click next I get the Prepare Partitions screen but the box is empty. I do not see any partitions.

What should I do next? I want to install this as a dual boot with my Vista on my second hard drive.

If you have two hdd's,the safest option should be to disable the Vista hdd.
Install Ubuntu and install GRUB on the same hdd.
Make this hdd the first boot device in your BIOS,you can add an entry for Vista later on in the menu.lst if you wish.

Or choose from which hdd you want to boot from BIOS or what other option you have to boot ubuntu or vista.

---

### Post by hatari on 2007-03-25
I think the problem right now is that the LiveCD does not recognize the harddrives that is why I get a blank box under the select partition screen. 

So how do I fix that?

FYI, the very time I booted from the the LiveCD it showed the drives in the partition box screen. But I didn't know which partition was the windows vista and which was my second HD. 

Now everytime I boot from the LiveCD to install Ubuntu, I get nothing!!

---

### Post by hatari on 2007-03-25
The command "sudo fdisk -l" gives me a blank line.

---

### Post by bulldog on 2007-03-25
Hmmm......odd.

You can try the GParted live cd ,it's only a 30MB download,burn it to a disk and boot from it.
It gives you a nice graphical interface and it's easier to use.

See if your hdd's will be recognized by GParted live cd

[http://gparted.sourceforge.net/](http://gparted.sourceforge.net/)

EDIT:
Are you using external drives [USB] by any chance?

---

### Post by xsist10 on 2007-03-25
Might this not be a problem with Vista's encrypted HDD format (lockbox or something like that)? Which version of Vista are you running?

---

### Post by hatari on 2007-03-25
I have Vista Ultimate. I am not installing it on an external/usb drive.

---

### Post by trents on 2007-03-25
I just posted with a problem which may be similar. I was trying to install Feisty over an existing Dapper install so the extended partitions and the swap were already there. The partitioner showed my two NTFS partitions (one for Vista and one for XP) and my two linux partitions but it wouldn't let me put a check in the swap partition box so I couldn't proceed with the install.

Steve

---

### Post by hatari on 2007-03-25
I ran GParted Live and it detected my two ntsf drives. I resized one drive with ext2 linux. 

When I boot off the Ubuntu liveCD again nothing comes up under partitions! Argh!

---

