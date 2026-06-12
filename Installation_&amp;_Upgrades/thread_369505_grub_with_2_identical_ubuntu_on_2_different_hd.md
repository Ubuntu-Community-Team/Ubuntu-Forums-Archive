---
title: "grub with 2 identical ubuntu on 2 different hd"
date: 2007-02-24
forum: Installation &amp; Upgrades
---

### Post by koho on 2007-02-24
Hi all, that's my situation.
hda1 8 Mb free space (to save mbr from winxp install)
hda2 / ubuntu
hda3 swap ubuntu

hdb1 / ubuntu
hdb2 wap ubuntu

hdb was the hd of another pc and now I plugged it to this pc.
I used ubuntu live cd to format hda and recreate partition table.
now I want to erase hda2-3 and install winxp here, but I suppose if I do that I'll lose all grub informations since at boot grub uses menu.list located in hda

how can I tell grub from hda mbr to look for menu.list in hdb/boot/grub?

hope to have been clear

thank you

---

### Post by Herman on 2007-02-24
Hello koho,
I would just install Windows and let it overwrite the MBR in hard disk 1.

Then you could use a LiveCD and re-install Grub.
[                                                       Re-install Grub with a GRUB shell eg; with Live CD]("http://users.bigpond.net.au/hermanzone/p15.htm#Re-install_Grub_with_Live_CD")
```
sudo grub
``````
find /boot/grub/stage1
``````
root (hd1,0)
``````
setup (hd0)
``````
quit
``````
exit
```Since you are installing Windows after you already have Ubuntu installed, you will have to add your Windows boot entry manually to the bottom of your /boot/grub/menu.lst file. So after you boot into Ubuntu, do this,
```
sudo gedit /boot/grub/menu.lst 
```Then copy this and paste it to your menu.lst.
```
### END DEBIAN AUTOMAGIC KERNELS LIST
                                                                       
# This is a divider, added to separate the menu items below from the Debian
# ones.
 title        Other operating systems:
 root
                                                                       
                                                                       
# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title        Microsoft Windows XP Home Edition
root        (hd0,0)
savedefault
makeactive
chainloader    +1
``` You can change the words on the line for 'title' to anything you like, so if your Windows is XP Professional, or Windows 98SE or something else, you can safely change that line to whatever you like.
If you choose to keep your /hda1 8 Mb MBR backup partition, you might end up with Windows on /hda2. If you do that you would also need to change the line for the 'root' command from (hd0,0) to (hd0,1) instead.

Regards, Herman :)

---

### Post by koho on 2007-02-24
thank you for your clear and easy solution.

ubuntu rocks! :guitar:

---

### Post by Herman on 2007-02-24
> thank you for your clear and easy solution. No problem! Glad to be able to help.


I just thought of something though,
>  hdb1 / ubuntu
hdb2 swap ubuntu

hdb was the hd of another pc and now I plugged it to this pc. If you mean you installed Ubuntu *after* you plugged this second hard disk into this PC, then things will be fairly simple, you might just need to delete your boot entries for Ubuntu on hard disk 1 from your menu.lst file.

If you mean Ubuntu was already installed when this disk was in another computer, you can still do it but it will take longer. You will have to mount your hard disk 2 Ubuntu in the LiveCD and edit the menu.lst to tell it it should look on hard disk 2 for the boot files.
[                            Mount a Ubuntu ext3 or reiserfs filesystem in the Ubuntu 'Desktop' Live/Install CD]("http://users.bigpond.net.au/hermanzone/p10.htm#Mounting_Ubuntu_with_Dapper_Desktop_LiveCD")
Let me know if you need more help with that and I'll be able to help or someone else will if I'm not here.

Once you get Ubuntu to boot, if it was installed while the hard disk was in a different computer, it might hang at starting the X-server. (Because it will be set up for the hardware of the other computer), so you might have to do this,             [sudo dpkg-reconfigure xserver-xorg]("http://users.bigpond.net.au/hermanzone/p7.html")

I didn't think of those possibilities when I typed the first post, but maybe you don't need to do those things anyway, if you installed Ubuntu *after* the hard disk was put in the computer it's in now. I just though it best to let you know just in case.

Regards, Herman :)

---

### Post by koho on 2007-02-24
> **Herman said:**
> If you mean Ubuntu was already installed when this disk was in another computer, you can still do it but it will take longer.
yes I meant :-$

>  You will have to mount your hard disk 2 Ubuntu in the LiveCD and edit the menu.lst to tell it it should look on hard disk 2 for the boot files.
[                            Mount a Ubuntu ext3 or reiserfs filesystem in the Ubuntu 'Desktop' Live/Install CD]("http://users.bigpond.net.au/hermanzone/p10.htm#Mounting_Ubuntu_with_Dapper_Desktop_LiveCD")
Let me know if you need more help with that and I'll be able to help or someone else will if I'm not here.

Once you get Ubuntu to boot, if it was installed while the hard disk was in a different computer, it might hang at starting the X-server. (Because it will be set up for the hardware of the other computer), so you might have to do this,             [sudo dpkg-reconfigure xserver-xorg]("http://users.bigpond.net.au/hermanzone/p7.html")

actually no errors with xorg, linux boots fine both from hda and hdb
I'll give a try to mounting hd in livecd, if I fail, I'll post all errors.

thank you again!

---

### Post by Herman on 2007-02-24
> actually no errors with xorg, linux boots fine both from hda and hdb Oh, that's good, you must be lucky then! If you already have it booting then you'll be fine. I was probably just worrying too much. :)

You probably don't need to do anything extra then.

---

### Post by koho on 2007-02-25
ok, I've taken a look at "mounting in livecd" but I realized my problem is easier.
when I boot my pc, grub installed in hda/mbr looks for menu.list in hda and I need to make it look for it in hdb (even installed in mbr/hda)
however the situation is more easy than in that howto because my grub from hda boots both partitions, hda and hdb (the other sistem on hdb has been detected during installation and perfectly configured in menu.list)

I just need to make mbr/hda point to hdb for boot files

thank you!

---

### Post by Herman on 2007-02-25
Okay, you are welcome.

Let me know if you need any more help. :)

Regards, Herman

---

### Post by koho on 2007-02-25
maybe I need your help now.. :( 
I think I need to do a sort of
grub> root (hd1,0)
where hd1 is hdb, but cannot resolve the problem..
shall I do that using hda ubuntu or hdb?
thank you

---

### Post by Herman on 2007-02-25
Hello koho,
You can do the work with grub from the hda ubuntu or the hdb ubuntu, it doesn't matter, whichever you prefer.
hda's Grub was already installed in MBR in hard disk 1, and you want to erase  hda2 / ubuntu and hda3 swap ubuntu and replace those with Windows.

Therefore it will be hdb ubuntu's grub that you want to install the first stage to MBR in disk1. When you do 'sudo grub', and have a grub>_ prompt, it doesn't matter which operating system you are in. 

The command 'root (hd1,0)' will let grub know you want the grub from hard drive2, first partition to be installed somewhere.

The next command, 'setup (hd0)', tells grub you want the grub from (hd1,0) to be installed to the MBR of (hd0), your first hard disk.

Those are the three most important parts of the commands. You can run those commands from any operating system, even from a Live CD if the Live CD has a grub shell and they will work.

Here is a link with an example showing what it might look like, with more explanations, maybe that will help,                                                        [Re-install Grub with a GRUB shell eg; with Live CD]("http://users.bigpond.net.au/hermanzone/p15.htm#Re-install_Grub_with_Live_CD")

Please let me know again if you still want any more help and I will explain more.

Regards, Herman

---

