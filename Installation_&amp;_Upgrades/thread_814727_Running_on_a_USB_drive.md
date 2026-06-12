---
title: "Running on a USB drive"
date: 2008-06-01
forum: Installation &amp; Upgrades
---

### Post by distortedvortex on 2008-06-01
Hey I have a 8gig USB drive and I want to run ubuntu on that because I don't want to partition out my harddrive is it possible to install and boot from a usb drive? Thank you

---

### Post by tamoneya on 2008-06-01
there are many guides on the internet about it.  I quick google returns many useful results.  This however should do nicely:
[http://www.teamteabag.com/2008/03/07/install-ubuntu-804-hardy-heron-from-usb/](http://www.teamteabag.com/2008/03/07/install-ubuntu-804-hardy-heron-from-usb/)

---

### Post by issih on 2008-06-01
The answer is ....probably.

You need hardware that can boot a usb drive (not all can), if your bios has options for booting from usb you will probably be fine.

Assuming your hardware is up to snuff, you then have two options:

1) Install onto the flash drive exactly as if it was a hard drive. Major downside here is that the flash drive may die sooner than you'd like as the OS treats it as if it is a normal hard drive, and doesn't worry about writing lots of times to the drive. Also this means the install will be customised to one pc.

[http://www.pendrivelinux.com/2008/04/14/ubuntu-804-usb-hard-drive-install/](http://www.pendrivelinux.com/2008/04/14/ubuntu-804-usb-hard-drive-install/)

P.S. the article posted by the previous poster is not ideal if you want to store anything, that makes a live cd type install, but no persistance of data, all work is lost when you turn off.


2) Make a persistant live install. This will try and limit writes to the flash drive, and allows you to run it on any pc (like a live cd), whilst letting you store data, and install new programs. I believe you can't update the kernel easily however (I could be wrong there though).

[http://www.pendrivelinux.com/2008/04/14/ubuntu-804-usb-hard-drive-install/](http://www.pendrivelinux.com/2008/04/14/ubuntu-804-usb-hard-drive-install/)

The site I've linked to has a lot of resources about this topic in general, have a browse :)

---

### Post by distortedvortex on 2008-06-01
Well I installed it just fine on a USB disk but then it would require me to choose which os I wanted when booting and I just want to boot directly from the usb and not have to choose with grub. And when I would take out the usb it would not boot into windows. I would get grub error 21. I put the stick back in and was able to boot back into windows and I used easybcd to fix the boot problem but now when I try to boot just from the stick it says missin operating system. Anyone got any ideas?

---

### Post by Pumalite on 2008-06-01
Fix your Windows MBR with Super Grub:
[http://users.bigpond.net.au/hermanzone/supergrubdiskpage.html](http://users.bigpond.net.au/hermanzone/supergrubdiskpage.html)
Next time; at step 8, 'Advanced Tab', change (hd0) for /dev/???
where ??? is your USB. You can find out with:
sudo fdisk -lu

---

### Post by distortedvortex on 2008-06-01
I've already fixed the windows mbr. How do I find out where my usb is? Where do I type that? you'll have to forgive me I'm still a little new to this.

---

### Post by Pumalite on 2008-06-01
Copy and paste command to the Terminal:
Applications>Accessories>Terminal

---

### Post by distortedvortex on 2008-06-01
you know I was looking for that and couldn't find it and it was right there lol. Thanks. I'll let you know how it goes.

---

### Post by distortedvortex on 2008-06-01
Well I installed it and changed the bootloader to the usb drive like it was mentioned above but not when I select boot from USB it brings up the grub bootloader again asking which OS I want to boot from even though there is only one on the usb drive. When I select ubuntu it says error 17 cannot mount partition. 

oh and I also posted in the network section about how I would connect my cable modem with comcast using ubuntu and no one has replied. A little help please?

---

### Post by Pumalite on 2008-06-01
Boot your Ubuntu with Super Grub:
[http://users.bigpond.net.au/hermanzone/supergrubdiskpage.html](http://users.bigpond.net.au/hermanzone/supergrubdiskpage.html)
Post:
cat /boot/grub/menu.lst

---

### Post by distortedvortex on 2008-06-01
Do I just put that on the USB drive as well?

---

### Post by Pumalite on 2008-06-01
You have to get Super Grub, burn it to disk and boot from it. Then boot Ubuntu. Once in Ubuntu go to the Terminal and run the command I gave you. Copy and paste the output here.

---

### Post by distortedvortex on 2008-06-01
It didn't boot to the desktop. It was just a terminal kind like old msdos. It said this

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to seperate the menu items below from the Debian
#ones.
title                 Other operating systems:
root


# This entry automatically added by th Debian installer for a non-linux OS
#on /dev/sda1
title   Windows Vista/Longhorn (loader)
root    (hd0,0)
savedefault
chainloader      +1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title      Windows Vista/Longhorn (loader)
root        (hd0,1)
savedefault
chainloader  +1


And that is everything it said. Like I said it loaded up Ubuntu showed the loading screen and went straight to the terminal like dos thing.

---

### Post by Pumalite on 2008-06-01
Read the Documentation on how to use Super Grub.

---

### Post by distortedvortex on 2008-06-01
I'm lost!! lol. I tried using super grub to fix the mbr for linux and that didn't work. I still get error 17 when trying to boot unbuntu from my usb and when I try booting with supergrub it doesn't go to the main screen or it says failed to start the X server

---

### Post by Pumalite on 2008-06-01
Fix your Windows MBR with Super Grub. Start from scratch and follow my instructions.

---

### Post by distortedvortex on 2008-06-01
I fixed the mbr it's all good but I can't get this stupid ubuntu to load. oh well. I think I am going to scrap this project and try with a different os. I don't know I'll keep tinkering I guess.

---

### Post by distortedvortex on 2008-06-01
Is it possible to install on my second partition of my harddrive but not install the bootloader and just use supergrub to boot into it that way it will always automaticall boot into vista?

---

### Post by Pumalite on 2008-06-01
Any new OS has a learning curve.

---

### Post by issih on 2008-06-01
Just start again....wipe the flash drive and reinstall, following a guide carefully, the ones I posted earlier work fine. if you do a full install direct to the flash drive just take care to install the boot loader to the flash drive too. Hit advanced on the last page of the install option and select it.

I honestly think you'll be happier with a persistent install, but its up to you.

If you get the boot loader installed on the flash drive and then set the bios boot order so it tries to boot from usb first, the system should jsut boot as it always has, but will boot to the grub menu if you stick the usb stick in. 

It can be done, just take the time to have a clear understanding of what you are doing.

If you are in the dark about what is happening you are more likely to get messed up :)

---

### Post by distortedvortex on 2008-06-01
lol. I think I just might have fixed it. I don't know lets see.
I'll get back to you.

---

### Post by distortedvortex on 2008-06-01
nope. It booted up but it won't go to the desk top. It only shows that terminal look.

---

### Post by Pumalite on 2008-06-01
That would be great.

---

### Post by distortedvortex on 2008-06-01
So if I want to instal it on my second partition on my computers harddrive but I don't want it to boot at all unless I manually boot  it. How would I go about doing that?

---

### Post by Pumalite on 2008-06-01
Back to post # 16

---

### Post by distortedvortex on 2008-06-01
> **Pumalite said:**
> Fix your Windows MBR with Super Grub. Start from scratch and follow my instructions.

That? I fixed it but what instructions?

---

### Post by meierfra. on 2008-06-01
distortedvortex: You are almost there. There is just one more thing to do. Namely edit "menu.lst":

First you  need to boot into Ubuntu. You can use Supergrub for that, or do this


Boot from the USB drive. At the Grub menu select "ubuntu", but do not press "enter", press "e" instead. At the new screen press "e" again.  You get a line which looks like

root (hd1,0)

although the numbers might be different. Change the first number to "0", but do not change the second number:

root (hd0,0)

Press "enter" and then "b" to boot.


This will boot you into Ubuntu.
Type

```
gksudo gedit /boot/grub/menu.lst 
```


Look for the line

#groot (hd1,0)

Again change the first number to "0", but to not change the second number:

#groot (hd0,0)

Save the file.

Back in the terminal change type

```
sudo update-grub
```

Reboot from the USB drive and you should be able boot into ubuntu without any problems.  If this worked, I'll show you how to edit "menu.lst" so that you can also boot into Windows from the Grub Menu.

---

### Post by distortedvortex on 2008-06-02
Ok went through changed the number to zero but when I do that it comes up with an error saying it count mount the partition.

---

### Post by Pumalite on 2008-06-02
Ifr this is a Desktop: install with all internals disconnected.

---

### Post by distortedvortex on 2008-06-02
I'm actually running it on my laptop, I'm using my desktop right now.

---

### Post by Pumalite on 2008-06-02
Good luck.

---

### Post by meierfra. on 2008-06-02
Boot from the USB drive, Press "c" at the grub menu, type

```
find /boot/grub/stage1 
```
(last symbol is a one)

and post the output. 

If the numbers in the output  are  different than what you used the last time:
Press "Esc"  to get to the grub, try the instruction from my previous post again, using the  new numbers for  "root" and "#groot"


If this did not work:

I would like to make sure that I understand the situation correctly and request some more information (in addition to the output of "find /boot/grub/stage1")


1) If you boot from the windows drive,  to you boot directly into Visa? 

2)  If you boot from the USB drive, you get to the grub menu. But trying to boot "Ubuntu" gives grub error 17.?

3) Do you have more than two hard drives?

4)  Boot from the LiveCD, go the "Computer->Places". One of those icon is for your ubuntu partition. Double click it. Browse to "/boot" and than to "/boot/grub/". Open the file "menu.lst" and post the content. Also post the output of 

```
sudo fdisk -l
```
(l is a lowercase L)


> So if I want to instal it on my second partition on my computers harddrive but I don't want it to boot at all unless I manually boot it. How would I go about doing that?

This can be easily done my editing "menu.lst" (change "timeout 10" to "#timeout 10" or by installing "startupmanager".

---

