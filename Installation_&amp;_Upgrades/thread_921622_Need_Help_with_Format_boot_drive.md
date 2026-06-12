---
title: "Need Help with Format boot drive"
date: 2008-09-16
forum: Installation &amp; Upgrades
---

### Post by jakspanna27 on 2008-09-16
ok here's the deal I originally had windows xp on my c:\ , installed ubuntu 8.04 on my d:\, want to remove windows all together wipe the C:\ clean but my grub files is on there , and then my system wont be  able to reboot. what should I do?

---

### Post by Herman on 2008-09-16
> want to remove windows all together wipe the C:\ clean but my grub files is on there
Are you sure your GRUB is in drive C:? That would be a little unusual.
If you have been booting with WinGRUB or with EasyBCD, then GRUB could be in your C: drive.

If you were booting with GRUB in Ubuntu, (the standard GRUB that comes in Ubuntu by default), then your GRUB should be in /boot/grub/ in Ubuntu. You should be able to just delete Windows.
Later, you can edit /boot/grub/menu.lst and remove the Windows booting stanza from the bottom of it.

---

### Post by jakspanna27 on 2008-09-19
Thank you for the reply, I started off with windows . Thats why there is the need for Grub on my C:\ , ANd installed hardy on D:\  so i dont want to erase it and not be able to boot my system period . I so do not want to have to install Ubuntu again and loose my data

---

### Post by Herman on 2008-09-19
Well, it's extremely rare for GRUB to be installed in your Windows system, I don't know how that's even possible, but I'll take your word for it. :)

To install GRUB in Ubuntu you just need to use the grub-install command, 
```
sudo grub-install /dev/sda
```Where: '/dev/sda' is your first hard disk.

That will install a pointer in your first hard disk's MBR to make it point to GRUB in Ubuntu.
It will also install GRUB in your /boot/grub directory in Ubuntu.
If you don't already have a /boot/grub directory, you will need to make one yourself first,
```
sudo mkdir /boot/grub
```Then run the grub-install command (above) and it will fill up your /boot/grub directory with files.

The only file you won't have yet will be your /boot/grub/menu.lst file.
The command for automatically having one of those made for you is,
```
sudo update-grub
```That will run a script which will either make you a new menu.lst file if you don't already have one, or update your menu.lst file if you do have one.
You may need to edit the file to get your GRUB setting the way you need and like.

Now you should have GRUB in Ubuntu.

Regards, Herman :)

---

### Post by jakspanna27 on 2008-09-22
Thank you for the help i'll try it out and let you how it worked out

---

### Post by jakspanna27 on 2008-09-22
ok i installed the grub files on the drive with ubuntu and disconnect my hard drive with windows which was my primary and set my ubuntu drive as my primary and i get an error, yes i see grub loading now but it then it say specified drive not found

---

### Post by Herman on 2008-09-23
> ok i installed the grub files on the drive with ubuntu and disconnect my hard drive with windows which was my primary and set my ubuntu drive as my primary and i get an error, yes i see grub loading now but it then it say specified drive not foundOh. okay, you are talking about two hard drives. Sorry, I didn't realize that. Many Windows people use the term 'drive' to mean 'partition', so I thought you meant you had one hard drive with two partitions. Sorry about that.
Now I realize you are talking about two separate hard disks. :)

You probably just need to edit /boot/grub/menu.lst now, to tell GRUB that Ubuntu is in your first hard drive, which is number zero as far as GRUB is concerned. (GRUB always starts counting from zero). :)

```
gksudo gedit /boot/grub/menu.lst
``````
title        Ubuntu, kernel 2.6.20-15-generic
[COLOR=Red]**root        (hd1,0)**[/COLOR]
kernel        /boot/vmlinuz-2.6.20-15-generic root=UUID=fe7bf845-7ce9-4733-b6de-f70f2b62076d ro quiet splash
initrd        /boot/initrd.img-2.6.20-15-generic
quiet
savedefault
``````
title        Ubuntu, kernel 2.6.20-15-generic
**root        (hd0,1)**
kernel        /boot/vmlinuz-2.6.20-15-generic root=UUID=fe7bf845-7ce9-4733-b6de-f70f2b62076d ro quiet splash
initrd        /boot/initrd.img-2.6.20-15-generic
quiet
savedefault
```Regards, Herman  :)

---

### Post by jakspanna27 on 2008-09-28
thanks for your help it finds the secondary hard drive now but everytime i try to write to it , it say i do not have permission to write to this drive

---

### Post by Herman on 2008-09-28
> thanks for your help it finds the secondary hard drive now but everytime i try to write to it , it say i do not have permission to write to this drive 
Oh, wait a minute... which hard drive is your first and which is your second hard drive now?
You removed the hard drive with Windows on it and made your Ubuntu hard drive primary I think, so now you probably won't need to edit your /boot/grub/menu.lst, but instead you would need to install GRUB to MBR in your Ubuntu hard disk now.

...or am I getting all mixed up? :confused:

Can you please post the output from 'sudo fdisk -lu' from a Ubuntu Live CD? (Or any Live CD),
```
sudo fdisk -lu
```

---

### Post by jakspanna27 on 2008-10-11
thank for all you help I got it up now , yes my slave drive has ubuntu and my master had windows I worked it out my master is now my media drive in ubuntu. The only thing that sucks is have to mount it everytime I boot.

---

### Post by Herman on 2008-10-11
If you can mount it easily, just by going 'Places'-->'Removable Media'-->'Windows', it's a lot quicker and easier then the way we used to have to mount things back in the old days, (with linux commands).

If you use your computer in work environment and it's connected to a LAN, it's better security to leave other file systems unmounted except when you need to access them.

If you are a home user and you just want your other operating system to be mounted automatically on every boot-up, then all you need to do is edit /etc/fstab.

Here's a link that explains how to do that, [Edit /etc/fstab Method for Mounting]("http://users.bigpond.net.au/hermanzone/p10.htm#Mount_a_different_Linux_filesystem_operating_system_in_Ubuntu").
I hope you'll find that easy to follow, but let me know if  you have trouble and I'll edit that web page to try to make it clearer.

Regards, Herman :)

---

### Post by virtualsolutions004 on 2008-10-11
Ubuntu is doing great job and providing many useful software's free of cost. I send email to ubuntu and ask them to send me their windows operating system. And they deliver me free of cost even without any delivery charges.

Alex Peter

[Crystal Meth](http://www.crystalrecovery.com)

---

