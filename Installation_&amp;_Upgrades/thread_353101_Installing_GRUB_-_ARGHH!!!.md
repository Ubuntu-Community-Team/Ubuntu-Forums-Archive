---
title: "Installing GRUB - ARGHH!!!"
date: 2007-02-04
forum: Installation &amp; Upgrades
---

### Post by ramo on 2007-02-04
I currently have Ubuntu Linux 10.6 Desktop burnt on CD and installing it a secondary slave hard disk of 250GB (IDE). I physically unplug the IDE cable and molar connector of the primary master HDD of 80GB because I want to be 100% that nothing happens to that install of Windows XP.

I do not want GRUB to technically manage my two OSs, so I'm trying to have it installed on the second hard drive along with the install of Ubuntu. I know that this will mean that I have to choose where to boot from in BIOS whenever I want to switch between OSs - and that's fine by me.

So I boot up the install CD and start up the installation from the desktop and when I get to the partitioning part, I choose to format the entire disk (the 250gb) for the installation of Ubuntu and then I get to that confirmation screen where it tells me what it's going to do in terms of modifying the hard drives. At the top, there's white box that I can edit asking me what device to install Grub on. The default is HD0, which I'm assuming is the primary hard drive. When I look at the bottom of this confirmation screen, I see also some information about the hard drive I'm installing Ubuntu to, and it refers to the same hard drive as HDB. So I tried editing the white box near the top, where it supposedly installs Grub, and I've typed in HDB only to get an error at the end of installation. I've also tried HD1 and now I'm not so sure of what to type in anymore. How do I do this? And I'm really new to all of this - been using Windows since forever - so I will probably not understand any kind of Linux/Ubuntu lingo. 

Thanks in advance.

---

### Post by shareMenaPeace on 2007-02-04
What happens if you use the defaults?

---

### Post by PurplePenguin on 2007-02-04
If I were you, I'd just agree to use the defaults, turn off the computer, stick your windows drive in, turn computer back on and go back in and manually edit your grub config to point to the right drives.
Or maybe it's easier to install ubuntu without grub, put both drives back in and install grub on its own...
Hmmm...

---

### Post by louieb on 2007-02-04
Since you have your windows drive unplugged. Did you set the slave drive to master?
You can go ahead and install it and see what it does. But be warned that Ubuntu may get confused after its installed and the windows drive gets reconnected. but in any case the windows drive is untouched. 
I did almost the same thing with my first Linux install.
I unplugged the windows drive just to make sure it did not get touched.
I installed an empty hard drive as the master drive and installed Linux on it.
Linux now worked and it was time to get windows back.
I plugged the windows drive back in this time as the slave drive. (check the jumpers)
To dual boot Linux and windows I had to make changes to the file /boot/grub/menu.lst.
Boot to Ubuntu
Press Alt-F2. and enter
```
gksudo gedit /boot/grub/menu.lst
```Now make sure the GRUB menu appears look for the line ```
hiddenmenu 
``` and comment it like this  ```
#hiddenmenu
```Next you need to add an entry for windows. add the following to the end of the file.
```

title Win XP 
          map (hd0) (hd1)
          map (hd1) (hd0)
          rootnoverify (hd1,0)
          makeactive
          chainloader +1
          boot

```The window drive is untouched. And you can dual boot w/GRUB.

---

### Post by ramo on 2007-02-04
thanks louieb for a full-bodied response, that kind of installation seems a little complex for me though, atm. 

The reason guys that I can't install Grub on HD0 is because I don't have a standard copy of XP. I have this factory-installed HP version from 7 years ago that creates a hidden recovery partition that conflicts with Grub during Windows boot (it opens up the HP Recovery Utility rather than Windows)

Someone mentioned that I can install Ubuntu WITHOUT Grub... how can I do this?

---

### Post by louieb on 2007-02-04
You can install Ubuntu or any other Linux without installing GRUB. But if you don't install some boot loader such as GRUB, LILO, or GAG .... you can't boot it. If you really want to jump through hoops you can configure the windows boot loader to load Linux. But i am to lazy to go that route. Even using the windows boot loader requires chain loading some Linux friendly boot loader.   

One more idea. Do you have a floppy drive? If so you can install a boot loader on a floppy disk and use it when you need to boot Ubuntu.

Go ahead and install Ubuntu with windows drive unplugged. Then plug the windows drive back in. and see if you can use BIOS to select you operating system. 
Windows should boot. Ubuntu is a maybe.
If Ubuntu does not boot check out the reinstall GRUB link in my signature.          

BTW do a search I be someone has figured out how to boot XP w/GRUB on a computer that has a recovery partition.

---

### Post by ramo on 2007-02-04
gagh thanks for replying, unfortunatley I made another thread about installing without ubuntu - just very frustrating - I kind of got something to install with no errors, but booting was a no-go. I kept on getting "error 18" which had to do with LBA or something that I don't understand

---

### Post by louieb on 2007-02-04
Error 18 is usually a problem with older computers. But I thing in your case GRUB just got confused by not having a true master drive during the install.

One more thing to suggest then I give up. Download and burn a [Super Grub CD]("http://supergrub.forjamari.linex.org/") and use it to boot to your Ubuntu install.

---

