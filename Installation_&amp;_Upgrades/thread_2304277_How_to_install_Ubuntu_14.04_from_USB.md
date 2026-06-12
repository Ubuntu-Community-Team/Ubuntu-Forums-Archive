---
title: "How to install Ubuntu 14.04 from USB?"
date: 2015-11-25
forum: Installation &amp; Upgrades
---

### Post by milenko-markovic on 2015-11-25
I have downloaded ISO from Ubuntu downloads.What steps should I take to install it from grub?When I press F12,nothing happens.I have tried this
search -s -f -n /ubuntu/disks/root.disk
error: no such device: -s-.
root
error:can't find command 'root'

Any ideas,or any links how to solve this?

---

### Post by milenko-markovic on 2015-11-25
Kernel info
kernel /boot/vmlinuz-
Possible files are:

vmlinuz-3.13.0-32-generic vmlinuz-3.13.0-44-generic vmlinuz-3.13.0-32-generic.efi.signed

---

### Post by Melnik_Hoogland on 2015-11-25
First, make sure you properly put the ISO onto the USB stick. Did you just copy it? If you did, delete the copy of the ISO on the USB stick and refer to the "Put the installer on a memory stick" section of [https://help.ubuntu.com/community/Installation/FromUSBStickQuick](https://help.ubuntu.com/community/Installation/FromUSBStickQuick) for instructions to properly put the ISO onto the USB stick. (be warned that all the files on the USB stick will be deleted, so make sure you have a copy of any files you want to keep on another drive)

Once you've done that, you'll probably need to change the boot order of your BIOS. There are lots of possible keys you would need to try to enter it, so it's best to just search for "(your computer model here) enter bios" or something similar. Once you find out which key it is, tap that key rapidly while turning your computer on. It should go to the BIOS setup screen. From there, use the arrow keys to navigate to "Boot" or something similar, then move "USB", "USB HDD", or whatever your computer calls a flash drive to the top (the BIOS screen should tell you which keys to use to move the drives up or down. On my computer it's F5/F6, but your computer might be different), and save and quit.

Then you should be able to plug in the USB drive and boot, and it should boot from USB. You should be able to install ubuntu normally from there.

---

### Post by milenko-markovic on 2015-11-25
Ok,I have downloaded Universal USB installer,but can not install it on my Ubuntu laptop.Is there any alternative?

---

### Post by Melnik_Hoogland on 2015-11-25
Yes, on Ubuntu there is Startup Disk Creator, which is built-in, so you don't need to install anything. Start it, select your ISO file and USB stick (I'd recommend clicking "Erase Disk" unless you really don't want to back up your files to another disk; IMO it is better to do a clean install), tell it whether you want it to reserve some space for storing files you make on the USB stick, and if so, how much you want it to reserve, then click "Make Startup Disk".

Once it is done, refer to the second part of my original answer for instructions to boot from the USB stick.

---

### Post by arnold255 on 2015-11-26
[SIZE=3]You can also use **UNetbootin**, very simple, stable, and reliable, I have been using it for years now and never let me down, all you need is to install it ( **available in ubuntu software center**) and once installed, **select "ISO image"** then browse to where you have saved your ubuntu Iso image, then **select the USB to put in**, set the USB space to be used and **hit OK**.

your done.[/SIZE]

PLS: remember to come back and give feedback.

---

### Post by yancek on 2015-11-26
Universal USB installer is windows software and won't run on any Linux.  If you look at the download, you can see that the downloaded file has an .exe extension making it windows.  Use the other options suggested if you are running Ubuntu, Startup Disk Creator or Unetbootin.

---

### Post by sudodus on 2015-11-27
You find more details in these links

[Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

[Try Ubuntu (Kubuntu, Lubuntu, Xubuntu, ...) before installing it](http://ubuntuforums.org/showthread.php?t=2230389)

---

### Post by FerryGnu on 2015-11-27
> **milenko-markovic said:**
> When I press F12,nothing happens.

You may need to set that option in the BIOS/UEFI settings. My Acer laptop has "Allow F12 boot selection" disabled by default. Can't remember the section and you may need to first set a Supervisor password for the BIOS/UEFI. Change the setting for F12 then reset the password to empty. Then F10 and exit. F12 should then work for you.

---

