---
title: "Can't boot from USB,starts booting from HDD instead"
date: 2015-11-24
forum: Installation &amp; Upgrades
---

### Post by l1nux2 on 2015-11-24
Hey, I want to install Ubuntu 12.04 alongside with Linux mint 17.2. 
I've successfully done it once but this time I just can't boot from USB stick. 


The BIOS settings are well-configured,I've set the USB stick as the first boot device but when I hit F10 and system starts loading,instead of booting from the USB device, it starts the system that I've installed on HDD. 


I do all the things as I used to do before,but the results are different- I'm not able anymore to boot from USB.


Note that :

* [COLOR=#ff0000]I had installed Puppy alongside with Mint,then I removed it 
but grub is still installed(Can it be a cause of the problem?) and grub menu pops up everytime I turn the computer on[/COLOR]


[COLOR=#ff0000]*Once I used "usb stick formatter"(a default application that comes with Mint) instead of GParted to format the USB


*The problem also occurs when trying to test any other distros too...[/COLOR]


Hope you'll be able to solve the problem,thank in adavnce !!!

---

### Post by v3.xx on 2015-11-24
> *The problem also occurs when trying to test any other distros too...

Then it has to be your computer.  BIOS is first to load, followed by the operating system.  Is the usb port is being detected by your OS?

```
lsusb
```

---

### Post by Bucky Ball on 2015-11-24
Welcome. What are you using to create the USB installer and how? What are you formatting the USB to? Where did you get 12.04 LTS?

---

### Post by l1nux2 on 2015-11-25
> **Bucky Ball said:**
> Welcome. What are you using to create the USB installer and how? What are you formatting the USB to? Where did you get 12.04 LTS?
I'm using unetbootin like I used to do in the past...
I've tried FAT32,ext,ext3 and ext4 at all,but the problem still occurs. 
As I remember ,Ubuntu 12.04 is uploaded on the official Ubuntu website
Would I be able to format the USB or move files from computer to it if the USB is damaged?

> **v3.xx said:**
> Then it has to be your computer.  BIOS is first to load, followed by the operating system.  Is the usb port is being detected by your OS?

```
lsusb
```
Yes,the usb port is being detected by the OS,I've already checked it :)
This isn't first time of me installing a distro,I've done it 7-8 times with the same USB

---

### Post by Bucky Ball on 2015-11-25
Well, USBs don't last forever. Have you another you can try it with? Stick with FAT32 prior to using Unetbootin, by the way. That is the one. Forget the other file systems. :)

---

### Post by l1nux2 on 2015-11-25
I think that's the solution :) I don't got any this time,but I'll get soon,hope this helps. Thanks !!!

---

### Post by sudodus on 2015-11-25
If the pendrive hardware is good, but the partition table or file system is bad, you can repair it by overwriting the first megabyte and create a new partition table and file system. It can be done with mkusb. Otherwise I think the pendrive is damaged beyond repair. See this link

[Pendrive lifetime]("http://ubuntuforums.org/showthread.php?t=2196858&p=13199297#post13199297")

---

### Post by l1nux2 on 2015-11-25
I'had been using the USB as a temporary storage while trying a distro "live". They told me,testing a distro live includes many write/read processes so it would shorten lifespan of the pendrive. That's why I thought it couldn't be repaired. 
 I always try to avoid working with terminal when it comes to using unknown commands,because I'm not educated enough :) so would deleting partition on the USB and recreating it again with Gparted(instead of doing it with terminal as you suggested) fix the problem? Thanks for the informative link :)

---

### Post by sudodus on 2015-11-25
The current version of ***mkusb has a graphical user interface***. In addition to what you can do with gparted, mkusb can also wipe the first megabyte automatically.

But you need these terminal window commands to install mkusb (you can copy and paste them from here into a terminal window to avoid mistakes).

```
sudo add-apt-repository ppa:mkusb/ppa  # and press Enter
sudo apt-get update
sudo apt-get install mkusb
```

---

### Post by yancek on 2015-11-25
> I'had been using the USB as a temporary storage while trying a distro "live".

If you had a Live CD on the flash drive created with unetbootin, you would have needed to create a separate partition on which to copy data for "temporary storage".  You might have overwritten some files necessary to boot.  Might try using unetbootin again to see if the flash will work.  This has been my experience with flash drives.

---

