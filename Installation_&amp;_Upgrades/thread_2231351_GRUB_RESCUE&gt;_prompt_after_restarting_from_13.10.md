---
title: "GRUB RESCUE&gt; prompt after restarting from 13.10 to 14.04 update"
date: 2014-06-25
forum: Installation &amp; Upgrades
---

### Post by Colby_Stott on 2014-06-25
I attempted to update from 13.10 to 14.04.

Running dual boot with Win 7Pro.

After update it stated that it completed with errors.  I figured that I would restart so maybe it would work out the errors.  Reboot and it gives an error message:

error:  symbol 'grub-term-highlight-color' not found.
grub rescue> _

not sure what to enter at the prompt.  if is ask for a list it gives me
(hd0) (hd0,mdos8) (hd0,msdos7) ... [hd0,msdos6, 5 and 1] (hd1) ... [hd16, 5 and 1] (hd2) )hd2,mdsos1)

the bracketed are the same sequence, didn't want to type it all out.

I have created a bootable USB stick in hopes that I could repair by running from that but it still puts me at the grub rescue prompt.

Please help.

---

### Post by LastDino on 2014-06-25
What kind of errors? Did you see anything specific?

Well, if its just ''highlight color'' you can edit it by simply typing the following

```
menu_color_highlight=text-color/bg-color
```

You need to put anything like ''yellow/black'' in place of ''color/bg-color'' part of it. Then see if shows up by pressing ''escape''.

I'm not sure if this is the problem though, so you may want to reinstall the grub by doing following

Boot into your Live Ubuntu DVD/USB
Mount the partitions and drive where Ubuntu is installed.
 ```
sudo mount /dev/sdXY /mnt
```
Then simply install the thing?
  ```
sudo grub-install --root-directory=/mnt /dev/sdX

```

Then see if you can get into grub.

Where /dev/sdX is the disk where Ubuntu is installed, and /dev/sdXY is  the partition on the disk where Ubuntu is installed. In other words,  /dev/sdXY contains /boot and so on.

Use fdisk -l to verify the Ubuntu installation location.

I'm assuming that you mean you're not able to boot into Live USB mode. If that's not the case please follow above instructions to install grub.
As for you not able to boot from Live USB, elaborate more, how did you make that bootable? Was ISO used checked with checksum? What software did you use? What format did you format the USB into?

---

### Post by Colby_Stott on 2014-06-25
The problem I am having is that it is not booting to the usb.  When i start the computer it give a quick splash screen of the MB maker and then goes right to the error screen.  It is not loading grub all the way and is not getting to any point that is loading the usb drive.

Used startup disk creator from the instructions given on the desktop download page, [http://www.ubuntu.com/download/desktop/create-a-usb-stick-on-ubuntu](http://www.ubuntu.com/download/desktop/create-a-usb-stick-on-ubuntu)

attached is an image of the error/screen.

---

### Post by oldfred on 2014-06-25
Ubuntu 14.04 Update breaks grub, resulting in "error: symbol 'grub_term_highlight_color' not found" 
[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1289977](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1289977)
You need to chroot &   use dpkg-reconfigure grub-pc instead of grub-install directly, so that the system knows that it needs to run grub-install on that drive the next time grub is upgraded.

You can use Boot-Repair's advanced mode to totally uninstall and reinstall grub.

Some are able to boot with Supergrub and then from inside Ubuntu run the full reinstall of grub or dpkg commands.
      
 [http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)
[http://www.supergrubdisk.org/wiki/Main_Page](http://www.supergrubdisk.org/wiki/Main_Page)

---

### Post by Colby_Stott on 2014-06-26
Well, I was able to get things fixed using Boot-Repair.

I ran it the first time and it told me that I had no boot or grub.  wasn't sure what that meant.  I rebooted without the bootable USB (it wasn't working previously i think because I didn't have boot disk priorities set properly).

I had two HDD and removed the one that was secondary.  It is still set up as dual boot with WinXP and OpenSUSE, but I have not been able to access them with the GRUB that I set up when I set up my primary HDD dual boot with Ubuntu and Win7.  I took it out to make sure that there was no confusion (all that bug info of not set up GRUB properly stuff).

Booted up with USB again and ran Boot-Repair again.  This time it went further and proceeded to install GRUB again and asked where I wanted it placed.  I have a boot partition, when I initially set this HDD up, and it had a GRUB folder so I put it there.  Went through the process, restarted after removing the USB and it is working.  Am able to get into Ubuntu and Win7.  Will install the secondary HDD again and see if there are any other issues.

Thanks for all the help, links, and insight.

cheers
colby

P.S.
[http://paste.ubuntu.com/7703957/](http://paste.ubuntu.com/7703957/)
for reference

---

### Post by LastDino on 2014-06-26
Good, glad to hear things are working now. 
Just a note: You can do the same (install grub) without needing boot repair by using commands in my post, so keep a note of them just in case you run into some trouble again.
I'm into multi booting as well, and it comes more than handy. I've never used boot repair or its grub installer.

---

