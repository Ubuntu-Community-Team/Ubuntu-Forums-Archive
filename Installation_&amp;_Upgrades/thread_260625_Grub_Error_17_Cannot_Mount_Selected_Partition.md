---
title: "Grub Error 17: Cannot Mount Selected Partition?"
date: 2006-09-19
forum: Installation &amp; Upgrades
---

### Post by uzd4ce on 2006-09-19
I'm very sorry about posting yet another Grub question, but I'm so close to getting my dual boot set up that I can't help posting just one more.

I'm trying to dual boot WinXP and Ubuntu. After several days of frustration, I finally got Grub to even come up at all at bootup. I have three drives, one  IDE and two SATA.  In my various efforts to get Grub to work I've installed Ubuntu both on a partition on the first SATA (which is where WinXP is also installed) and also on it's own on the second SATA.

When I boot now, Grub loads.  If I choose WinXP, it loads fine.  Grub sees both of the Ubuntu installs.  If I choose either, I get:
Error 17 : Cannot mount selected partition -     This error is returned if the partition requested exists, but the filesystem type cannot be recognized by GRUB. 

In Grub, "find /boot/grub/stage1" reports (hd0,1) and (hd1,0).  I believe hd0 is the IDE which has no OS installed on it.  I think hd1 is the WinXP drive.

Running setup (hd0,1) or (hd1,0) both shows as succeeding, but then I get the error 17 when I try to select either Ubuntu installation.

I'm so close to getting this to work.  I'd appreciate any help whatsoever.

Thanks

---

### Post by jd65pl on 2006-09-19
Just run 

```
setup(hd0)
```

**NOT**```
setup(hd0,x)
```

See if that works

Have a look at this link it may help you a little
[http://www.sorgonet.com/linux/grubrestore/]("http://www.sorgonet.com/linux/grubrestore/")

J

---

### Post by uzd4ce on 2006-09-19
Well, I kind of figured out something, but I'm not sure why it's happening this way.

When Grub loads, and I get the error, it's showing Root (hd1,1).  If I go into edit and manually change that to Root (hd1,0), then reboot, everything works fine and I can finally boot into my Ubuntu install.

However, when I reboot again, Grub has gone back to thinking the wrong partition is root again.  

So, now my question is where do I go to permanently tell Grub that root is (hd1,0)?

---

### Post by jd65pl on 2006-09-19
Have you tried the above do

```
grub
root(hd1,0)
setup(hd1)
quit
```

reboot to see if that works

---

### Post by Donnut on 2006-09-19
[http://ubuntuforums.org/showthread.php?t=244788](http://ubuntuforums.org/showthread.php?t=244788)

Try this, worked for me!

---

### Post by undertherift on 2006-09-19
uzd4ce:

All the grub/grub related stuff resides in /boot/grub/menu.lst.  

Sooooo... 
1. Boot your machine into Ubuntu
2. sudo your way into that menu.lst file (using whatever text editor you like  ex. sudo vi /boot/grub/menu.lst)
3. At the very bottom (under the ##DEBIAN AUTO SOMETHING SEOMTHING ###) it should say something like 

```

  Title WindowsXP
  root  (hd1,1)    ## CHANGE THIS TO (hd1,0)
  savedefault
  makeactive
  chainloader +1

```

Save that file, reboot, and you're good to go.  
jd65pl's method should work - but if you didnt know about this menu, you can do other things to control the boot, like hide the grub screen or change the default, or the countdown timer (that was a big one for me).  Just read the comments in the file and have fun.  

-Vik

---

### Post by Robbyx on 2006-11-12
My problem is similar but I need some clarification as to what is going wrong:

According to fdisk -l my linux partition is at /dev/hda1

grub>root(0,0)
  produces Error 21 selected disk does not exist

How should I describe hda1 in Grub?

Upon rebooting, Grub comes up and shows linux as an option. I choose that and get the following error message:

filesystem type unknown, partition type 0xf
error 17 can not mount selected partition

What should I do to change my settings so that I can at least start Ubuntu on this machine, rather than use the liveCD.

Should I reformat the HD and start again?

Robin

---

### Post by bulldog on 2006-11-12
Well hi there,
Start by giving the outcome of```
sudo fdisk -l  (l as in like)
```

Then I would like to see a copy of your menu.lst```
cat /boot/grub/menu.lst
```

Than we have a starting  point to begin to examine the trouble.

---

### Post by Robbyx on 2006-11-12
thank you for helping me. I think I have misubderstood how to apply th cat comd. See below

Robin


fdisk:

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1912    15358108+   c  W95 FAT32 (LBA)

Disk /dev/sdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        1912    15358108+   c  W95 FAT32 (LBA)

Disk /dev/hda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1       13999   112446936   83  Linux
/dev/hda2           14000       14593     4771305    5  Extended
/dev/hda5           14000       14593     4771273+  82  Linux swap / Solaris

Disk /dev/hdb: 41.1 GB, 41174138880 bytes
255 heads, 63 sectors/track, 5005 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1            2708        5005    18458685    f  W95 Ext'd (LBA)
/dev/hdb5            2708        3699     7968208+   7  HPFS/NTFS
/dev/hdb6            3700        4591     7164958+   7  HPFS/NTFS
/dev/hdb7            4592        5005     3325423+   7  HPFS/NTFS

menu.list

ubuntu@ubuntu:~$ cat /boot/grub/menu.lst
cat: /boot/grub/menu.lst: No such file or directory

---

### Post by Robbyx on 2006-11-12
sda & sdb are mirrored rade drives under wi2k. I hope to keep them that way in Ubuntu. They are fake raides.

Robin

---

### Post by geek_Man on 2006-11-12
Robbyx, it appears that you're using a Live CD. What you should type is:```
cat /media/(whatever the drive name is, mine was usbdisk)/boot/grub/menu.lst
``` I ran into that type of problem myself. Hope this helps.

---

### Post by jd65pl on 2006-11-12
Robbyx

Bulldog wishes to see the file so. Boot using the live disk and open terminal.

```
cd ~
```
To change directory to your home folder on the live disk

Do
```
cat /media/(whatever the drive name is, mine was usbdisk)/boot/grub/menu.lst > myGrubList.txt
```
As the poster above said, but this command will output the information to a file called myGrubList.txt in your home folder. Post this file for inspection.

---

### Post by Robbyx on 2006-11-15
I appreciate I have posed a difficult problem, but is anyone able to reply? Without your reply I can not install Ubuntu.

---

### Post by jd65pl on 2006-11-15
Try having a look at this it should help you to re-install grub with the live CD
[http://users.bigpond.net.au/hermanzone/p15.htm#reinstallgrub](http://users.bigpond.net.au/hermanzone/p15.htm#reinstallgrub)

---

### Post by geek_Man on 2006-11-15
If you can display your menu.lst file Bulldog and I and anyone else would be more than happy to help.

---

### Post by Robbyx on 2006-11-15
I did not realise that there were replies on the second page. Thank you all  for replying.  I will come back after digesting them. I appologise for some of my earlier typing errors. I usually type in dvorak and  I have not found it on  the live cd of 6.06.01. I have tried 6.10 but I am concerned that my md5 checks never matched the correct hash.

Robin

---

### Post by midra on 2006-11-30
> **jd65pl said:**
> Have you tried the above do

```
grub
root(hd1,0)
setup(hd1)
quit
```

reboot to see if that works

Sorry to be a total daft, but where do you put this, in the terminal or when editing grub in the boot menu? ](*,)

---

### Post by jd65pl on 2006-11-30
> **midra said:**
> Sorry to be a total daft, but where do you put this, in the terminal or when editing grub in the boot menu? ](*,)
You would put the series of commands into the terminal.

---

### Post by hotani on 2007-04-26
I've got this error too, and installing/reinstalling grub has not fixed it. The only way I can get into my system is by putting in an install CD then choosing "boot from first hard drive."

---

### Post by daynah on 2007-11-16
> **midra said:**
> Sorry to be a total daft, but where do you put this, in the terminal or when editing grub in the boot menu? ](*,)

Maybe I'm daft, too, but I boot to the Grub, pick Ubuntu, get the error and press Ctrl Alt F1 for the terminal and I just get brought back to the grub. With the other Fs too.

This is going to be so obvious, I can feel it.

---

### Post by bulldog on 2007-11-16
> **daynah said:**
> Maybe I'm daft, too, but I boot to the Grub, pick Ubuntu, get the error and press Ctrl Alt F1 for the terminal and I just get brought back to the grub. With the other Fs too.

This is going to be so obvious, I can feel it.
What error doe you get?
Installing grub is easy,but maybe is it's  just a faulty menu.lst  entry.

---

### Post by daynah on 2007-11-16
> **bulldog said:**
> What error doe you get?
Installing grub is easy,but maybe is it's  just a faulty menu.lst  entry.

The same error 17

---

### Post by mrcbldn on 2007-12-14
I installed XP over my native Vista, obviously the grup installation was covered from Windows bootloader.

Following this guide: [https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows#head-bf3232f10ddf1b078de064622ccbb25225cdb3c0]("https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows#head-bf3232f10ddf1b078de064622ccbb25225cdb3c0")

I was able to reinstall grup into linux partition (hd0,2); when I rebooted my computer I saw rightly grub menu, if I choosed Windows boot everything was ok but if I choosed Linux Partition appeared:

"Error 17: Cannot mount selected partition"

I choosed 'e' on linux entry into grup menu; the first voice appeared as root (hd0,3) but I saw that the ext2fs partition was into 2!!!
So I changed it into root(hd0,2) with 'e' option.

After the changed it i pressed 'b' (boot); then my linux starded!!!

The changes was not persistant, so after boot, I needed to permanent change the grup configuration.
I went into /boot/grub/menu.lst and I changed the entries for linux into root (hd0,2) (they where to (hd0,3) )

Now everything works well but I still does not understand how my new xp install dropped an existent partition!!
Unlikely I have not the output of previous fdisk command :-(

---

