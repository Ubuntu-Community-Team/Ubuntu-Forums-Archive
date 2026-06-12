---
title: "Dual boot ubuntu 10.10 and Windows XP via Burg"
date: 2010-10-24
forum: Installation &amp; Upgrades
---

### Post by JSLR on 2010-10-24
I run Ubuntu 10.10 and would like to dual boot XP along side with ubuntu, What are some things that I should be aware of:confused: I plan on installing XP via usb. It's my only option and would like a smooth running Burg boot but can't find any information on the subject](*,) enlighten me.

---

### Post by JSLR on 2010-10-24
Shamful self bump...

---

### Post by mikewhatever on 2010-10-24
Can you elaborate on what exactly you want to know.

---

### Post by jephrei on 2010-10-24
i'm not an expert, but i do know that installing windows after ubuntu will screw up the boot for linux. you're gonna have to restore the grub or something in order to use ubuntu again. google it, i don't think it's difficult. installing ubuntu after windows however will be handled smoothly by the ubuntu install.

---

### Post by Lrpbpb on 2010-10-24
Not to discourage you, but that is exactly why I procure to install windows before ubuntu....Now I must tell you I have never personally tried rescuing the grub/burg if it was overridden by the windows bootloader. 
I did a little searching and by far the easiest way that I found to fix your problem is by going here: [http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)
There are a number of boot recovery tools there, but we are particularly interested in rescatux.
1. You download rescatux from the page [http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)
2. You burn a cd with it or make a bootable flash with it[INDENT]As a side note, you are probably better off just using up a cd as making a bootable usb is somewhat of a pain. Having said that, if you don't want to spend half a dollar on a disk or otherwise prefer to use a usb, take a look at this page [http://www.pendrivelinux.com/universal-usb-installer-easy-as-1-2-3/](http://www.pendrivelinux.com/universal-usb-installer-easy-as-1-2-3/), at the bottom there is a tiny description on how to create a bootable flash with any linux distro, but not guaranteed.
[/INDENT]3. Boot rescatux
4.Then do the following (taken from [https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows):]("https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows")
[LIST]
[*]Select **Restore grub / Fix Linux Boot** option and click on OK button
[*]Select the **partition** where your **Ubuntu** is and click on OK button
[*]Select the **hard disk** where you want **Grub** to be installed (usually the first one)
[*]**Grub was installed OK** confirmation / Grub was not installed error will appear
[/LIST]
5. If you get the **Grub was installed OK** confirmation, smile:)
Alternatively, though as I'm also somewhat new to ubuntu I wouldn't necessarily recommend it, You could do the same described above but using Super Grub2 Disk instead of rescatux, and once you boot your ubuntu install just do:
```
sudo apt-get install grub
sudo update-grub
```Also, here is a great guide on how to install burg: [http://www.omgubuntu.co.uk/2010/01/make-grub-themes-beautiful-look-nicer.html](http://www.omgubuntu.co.uk/2010/01/make-grub-themes-beautiful-look-nicer.html) (if you have burg already installed, then replace the "grub" with "burg" in the commands above)

Hope this helps!!!

PS: Again, I'm not so sure about using super grub 2 disk, because I'm not sure on how exactly windows overrides grub, and if just doing a update-grub will be enough, you can always try, though ;).

---

### Post by Lrpbpb on 2010-10-24
> I plan on installing XP via usb. It's my only option I'm guessing you don't have a cd drive, do you? So regarding my previous post forget the burning a cd part. But I must tell you, out of experience, making a bootable usb (for linux and especially for windows) is a pain. Good luck! and please post back if you are able to restore burg after installing windows.

---

### Post by JSLR on 2010-10-25
> **Lrpbpb said:**
> I'm guessing you don't have a cd drive, do you? So regarding my previous post forget the burning a cd part. But I must tell you, out of experience, making a bootable usb (for linux and especially for windows) is a pain. Good luck! and please post back if you are able to restore burg after installing windows.

I fail'd hard at making a boot successful usb, I tried using unetbootin but it only lists default in the boot options and restarts when I try to enter. and yeah I can't use a cd because I'm using an acer aspire one laptop, so its not an option as I'm trying to use any bum style installation available. I have to figure out a way to make a bootable usb from an .iso, I even try'd to install windows via wine with the setup.exe that was generated with unetbootin but when i run the setup, a window pops up and says "no system partitions detected" or something similar  to that.

---

### Post by Lrpbpb on 2010-10-25
How about this, make a Maverick live-usb, boot then follow the instructions on this page: [http://ubuntuguide.net/how-to-restore-grub-2-after-reinstalling-windows-xpvistawin7](http://ubuntuguide.net/how-to-restore-grub-2-after-reinstalling-windows-xpvistawin7)
Basically it tells you to do:
```
sudo -i
mount /dev/sda7 /mnt
mount /dev/sda6 /mnt/boot  #skip this one if not have a separate /boot partition
grub-install --root-directory=/mnt/ /dev/sda
```
Where sda7 is your linux partition and sda6 is you boot partition (if you don't have a separate /boot partition then replace with sda7 or whatever)
Hope this helps.

---

### Post by jephrei on 2010-10-25
this usually worked for me quite well after my own failed attempts at unetbootin. it's called universal usb installer. good luck.

http://www.pendrivelinux.com/universal-usb-installer-easy-as-1-2-3/

---

