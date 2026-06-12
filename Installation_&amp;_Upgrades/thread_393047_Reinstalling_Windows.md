---
title: "Reinstalling Windows"
date: 2007-03-25
forum: Installation &amp; Upgrades
---

### Post by ComputerGuy56 on 2007-03-25
I currently have WinXP and Ubuntu 6.10 Dual Booting on two HDD's.(One hard drive contains Ubuntu, other contains WinXP) I want to fully get rid of Windows and re-install it. I googled this but I don't want emulators. If I didn't have Ubuntu, then I would install WinXP a little funny. I have a Win98 Disc and WinXP Update Disc. I install Win98, then upgrade to WinXP. How would I re-install Windows XP, still having Ubuntu? Should I just take out the Linux HDD, install WinXP, then put in my Linux HDD?(Grub would get messed up.)

[EDIT: I also have my WinXP HDD mounted in Ubuntu so I can see all my files(and write them)using Ubuntu]

---

### Post by bulldog on 2007-03-25
You can do several things.
Just install windows with the ubuntu disk connected or disconnected what ever you prefer.

Question,on which hdd is GRUB installed?

If you're not changing your partitions you should be fine,reinstall GRUB after the windows install and off you go.

---

### Post by ComputerGuy56 on 2007-03-25
I think... GRUB is installed on the disk which Linux is on. WinXP was installed then I cleared out a HDD and used that as the Linux.
1. Had WinXP
2. Got another HDD. Installed it.
3.Cleared the second HDD.
4. Installed Ubuntu on the second HDD.

I don't really know where GRUB is installed.

---

### Post by bulldog on 2007-03-25
Do you know from which disk you're booting?
It' not that important,but it's real handy to install GRUB onto the disk you're booting from.:)

The fact you installed ubuntu to a particular hdd,says nothing about the hdd where GRUB is installed.
By default it will be installed into the MBR of the first hdd (hd0)

---

### Post by ComputerGuy56 on 2007-03-25
What do you mean by "disc"? When GRUB starts I have either WinXP or Ubuntu. If I select WinXP, it will boot from let's say HDD1. If I select Ubuntu, it will boot from HDD2... Is there a way to find where GRUB is?

---

### Post by bulldog on 2007-03-25
Well there are a view options someone with a little knowledge about GRUB could tell.
But if you can tell me which disk is the first boot device on your computer.
You can perform ```
cat /boot/grub/device.map
``` to see how ubuntu handles your hdd's

And if you installed it into the default device it should be on (hd0).

EDIT:
But this isn't important at all,just reinstall windows and after that reinstall GRUB if necessary.
Boot into the live Ubuntu cd. 
When you get to the desktop open a terminal and enter. 
```
sudo grub
```
This will get you a "grub>" prompt 
```
find /boot/grub/stage1
```
This will return a location.Use that location in the next line 
```
root (hd?,?)
```
Next enter the command to install grub to the mbr
```
setup (hd0)
```
Exit the grub shell
```
quit
```

---

### Post by ComputerGuy56 on 2007-03-25
```
sly@sly-desktop:~$ cat /boot/grub/device.map
(hd0)   /dev/hda
(hd1)   /dev/hdb

```

I'm guessing hd0 is my primary hdd. (I gotta check if that's Windows or Linux) And if I were to reinstall Windows, I would install Windows, then run that sudo grub thing you posted? And would Windows install on the hdd it was last one?

---

### Post by bulldog on 2007-03-25
If you perform ```
sudo fdisk -l
``` you can see on which hdd windows is installed.
When reinstalling windows it would be a nice thing to use the same partition as you did before.

After windows is installed,reinstall GRUB if you choose 'setup (hd0)' it would be on on the hda disk and if you do 'setup (hd1)' it will be installed on the hdb disk.

But which disk you choose,make it your primary boot device to see GRUB.

---

### Post by ComputerGuy56 on 2007-03-25
I ran the live CD and got this through GParted.(View Pictures) I use a program called Secure Erase to format anything . It's a floppy which boots, and you can format any hdd, or partition.(In this case my Windows Hard Drive.

Edit:
I get this from sudo fdisk -l
```
sly@sly-desktop:~$ sudo fdisk -l
Password:

Disk /dev/hda: 40.0 GB, 40060403712 bytes
240 heads, 63 sectors/track, 5174 cylinders
Units = cylinders of 15120 * 512 = 7741440 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        5174    39115408+   7  HPFS/NTFS

Disk /dev/hdb: 30.0 GB, 30020272128 bytes
255 heads, 63 sectors/track, 3649 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           1        3560    28595668+  83  Linux
/dev/hdb2            3561        3649      714892+   5  Extended
/dev/hdb5            3561        3649      714861   82  Linux swap / Solaris

```

---

### Post by bulldog on 2007-03-25
Well,windows is on the hd0 and ubuntu on the hd1.

Ok,I'm gonna tell you some thing which could be a handy setup for you.

I think you know how to change your first boot device in your BIOS.
If you know how to change that make, after you installed windows and before reinstalling GRUB,your hdb with ubuntu the master boot device.

Reinstall GRUB on this hdd which should be (hd0) when you have made the switch.
You can boot into ubuntu now,but **not** into windows.
To boot windows you have to make a little change in your menu.lst,because windows like to think it's the only OS installed.
You have to add two lines into the windows entry in menu.lst,to let it look like this,
```
# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hdb1
title		Microsoft Windows XP Professional
rootnoverify		(hd1,0)
map          (hd0) (hd1)
map          (hd1) (hd0)   
savedefault
makeactive
chainloader	+1 
```

The advantage you have with this way of doing it is,
1/you can boot windows and ubuntu from the GRUB menu
2/if you get any kind of trouble with GRUB,you can boot windows from it's own bootloader by changing the master boot device in the BIOS.
3/If you ever want to reinstall windows,you can do so without to worry about GRUB

Think about it and let me know if you encounter trouble.

---

### Post by ComputerGuy56 on 2007-03-25
Wait, unless I'm making a mistake, isn't GRUB already on the (hdb) hard Drive. Why would I have to reinstall it? And menu.lst is in boot/grub/ right?

---

### Post by bulldog on 2007-03-25
I think GRUB is on the windows hdd,currently (hd0),but reinstalling can't hurt anyone :) 

Do you know how to switch the master boot device?

After you have installed everything,you have to boot into ubuntu and perform```
gksudo gedit /boot/grub/menu.lst
```
Find the windows entry and make the modification,save the file and you're done.
When you reboot you can boot windows and ubuntu from the grub menu.

If you don't know how to change the menu.lst,you can post it here,and I make the changes for you.

---

### Post by ComputerGuy56 on 2007-03-25
1. Won't having two GRUBS basically kill my computer.

2. When my computer starts, press F1, then to Boot tab, Boot Options, Select Hard Drives, it will open up a sub thing of all my HDD's, move my... well, whichever HDD has Ubuntu installed. And I have to do this after I reinstall WinXP.

---

### Post by bulldog on 2007-03-25
Double post.

---

### Post by bulldog on 2007-03-25
You can't install it twice to the same hard disk.

2 Is a nice BIOS feature,I've got a similar thing.

But if you don't choose a drive to boot from,it wil make the decision for you.
And at that time it's convenient,it chooses the ubuntu disk to boot from.

But if you choose the manual boot you don't have to alter the menu.lst,you can boot directly from the windows/ubuntu disk.

You need the GRUB menu to start ubuntu,so a windows entry isn't even necessary.

---

### Post by ComputerGuy56 on 2007-03-25
But if GRUB is installed in Ubuntu, then I'm going to install GRUB in WinXP, GRUB will interact with each other and... I'll have a problem. And something else, I'm not going to do this whole process today. I'm still backing stuff up and getting ready.

---

### Post by bulldog on 2007-03-25
So basically,
1 / Reinstall windows on the same place as it was.
2 / Reinstall GRUB and use 'setup (hd1) instead of (hd0)

Use the boot utility to choose from which disk you want to boot,and you're done.
No switching boot devices or what ever,this is all you have to do for a proper dual boot machine.

EDIT:
No,you won't install GRUB on the windows hdd,just on the ubuntu hdd.
Installing windows will overwrite the existing GRUB with the windows boot loader,so don't you worry.
Just leave everything as it is,reinstall windows.
After installing windows pop in the live cd and perform the GRUB install,only use the 'setup (hd1) instead of (hd0) and everything will work like a charm.

---

### Post by ComputerGuy56 on 2007-03-25
*The Steps:*

[LIST=1]
[*]Format the Hard Drive that Windows is on.
[*]Reinstall Windows on the Hard Drive I just erased.
[*]Do that whole process of re-installing GRUB but install GRUB on (hd1) instead of (hd0).
[*]Don't change any boot orders, don't change any menu.lst's. Basically, don't change anything.
[/LIST]

Is that correct. And when I said > Don't change any boot orders, don't change any menu.lst's. Basically, don't change anything. Only do the steps that were said. Everything's right?

---

### Post by bulldog on 2007-03-25
You've got it :) 

You can make a choice with the boot utility which hdd you want to boot,so that shouldn't be to difficult.

If you run into trouble,give me a PM and I look into it.

Good luck.

---

### Post by ComputerGuy56 on 2007-03-25
Thanks:popcorn:

---

