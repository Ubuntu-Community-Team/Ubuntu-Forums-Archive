---
title: "Another noob's install probs-grub error 15"
date: 2007-11-30
forum: Installation &amp; Upgrades
---

### Post by padraic99 on 2007-11-30
Hey folks,

I thought I'd try several distros installed at the same time, on different partitions (XP on the box first,) Each installation left me unable to access the previous installation; I've gathered this is because grub was written (& overwritten) on the MBR? No prblems deleting partitions and running fdisk, or now, using SuperGrub to fix things.

Decided to go back to Kubuntu 7.10 last night. Used "Manual" setup for install and created a 100MB "/boot" prt before my Windows partition, after reading a post about the BIOS limits (though I'm not sure it applies here? A8N-SLI Deluxe mobo); a 20GB "/" prt; an 82 GB "/home" prt; and a 1GB swap prt. 

Now I get "Grub Error 15" upon reboot. I have to use SuperGrub to boot into XP. After Googling this I've tried some commands from the Live CD, which gives me some info, but I can't find menu.lst anywhere. I'm very new to Linux (noooooooob) so detailed advice would be appreciated. The contents of sudo fdisk -1 is as follows:

> 
Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

Device Boot Start End Blocks Id System
/dev/sda1 * 14 5352 42885486 7 HPFS/NTFS
/dev/sda2 5353 30401 201206092+ f W95 Ext'd (LBA)
/dev/sda3 1 13 104391 83 Linux
/dev/sda5 5353 11089 46082421 7 HPFS/NTFS
/dev/sda6 11090 11095 48163+ 6 FAT16
/dev/sda7 11096 19290 65826306 b W95 FAT32
/dev/sda8 19291 19539 2000061 83 Linux
/dev/sda9 19540 30276 86244921 83 Linux
/dev/sda10 30277 30401 1004031 82 Linux swap / Solaris

Partition table entries are not in disk order

Disk /dev/sdb: 320.0 GB, 320072933376 bytes
16 heads, 63 sectors/track, 620181 cylinders
Units = cylinders of 1008 * 512 = 516096 bytes

Device Boot Start End Blocks Id System
/dev/sdb1 1 326021 164314552+ f W95 Ext'd (LBA)
/dev/sdb5 2 313953 158231808 7 HPFS/NTFS
ubuntu@ubuntu:~$

I see that the boot partition which was supposed to come before Windows is actually sda3 (hd0,2), and I'm thinking this may have something to do with it? I have a 2nd HD that I just use for multimedia files.


Then, ran this:

> 
ubuntu@ubuntu:~$ sudo less /boot/grub/menu.lst[/code]
/boot/grub/menu.lst[/code]: No such file or directory
ubuntu@ubuntu:~$ sudo less /boot/grub/menu.lst
/boot/grub/menu.lst: No such file or directory
ubuntu@ubuntu:~$

Wouldn't know what to do with it when I find it either! :shock:

Any help is much appreciated,

Cheers!
padraic

---

### Post by Pumalite on 2007-11-30
Get a Knoppix and go looking for menu.lst in sda8 and sda9

---

### Post by padraic99 on 2007-11-30
Well, unfortunately the Knoppix DVD won't boot. It looks like everything loads fine until right before the splash screen and then I  see (it goes quickly, so it's hard to read) "Unable to load AGP modules" or something like that. I've tried starting it at various res, also with "no acpi..." ventured briefly into "Expert" mode and was going to try to change the display there but it blew my confirmation. It just hangs at the splash screen. If it did boot, am I correct in assuming that Knoppix automatically mounts all the partitions it finds, or is that something I'd have to do manually?

I may have to reinstall, but I feel like it's almost there, and it's a good way to learn my way around. 

So, if I do have to reinstall Kubuntu, does the installer not install the startup info in the /boot partition if it's set as such? 

Thanks for any help,

padraic

---

### Post by meierfra on 2007-11-30
Boot from the ubuntu live CD.  menu.lst should be on your boot partition. So you should be able to open menu.lst via


```

sudo mkdir /media/sda3
sudo mount   -t ext3 /dev/sda3 /media/sda3
gksudo gedit /media/sda3/grub/menu.lst
```

(This assumes that your boot partition is  formated as ext3. If not use the proper format, or leave out the ´-t ext3´) If this does not work, try 

```

sudo mkdir /media/sda8
sudo mount  -t ext3 /dev/sda8  /media/sda8
gksudo gedit /media/sda8/boot/grub/menu.lst
```

or  sda9 in place of sda8.  You also might be able to get to your boot partition via Places->Computer

---

### Post by padraic99 on 2007-12-01
Meierfra,
Thanks for the reply. Tried as you suggested and got this error for all 3 attempts sda3, 8 & 9):

> X Error: BadDevice, invalid or uninitialized input device 167
  Major opcode:  144
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 167
  Major opcode:  144
  Minor opcode:  3
  Resource id:  0x0
Failed to open device

Where would I find the "Places->Computer" menu, or info?

P

---

### Post by meierfra on 2007-12-01
> X Error: BadDevice, invalid or uninitialized input device 167
Major opcode: 144
Minor opcode: 3
Resource id: 0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 167
Major opcode: 144
Minor opcode: 3
Resource id: 0x0
Failed to open device 

This is a standard error message caused by a bug in "gksudo".    You can ignore it.

You didn't have a new window open up after "gksudo gedit ...."? 


Try this

```
cd /media/sda3/grub
ls
cd /media/sda8/boot
cd grub
ls
cd /media/sda9/boot
cd grub
ls
```

 (If you turned your computer off since the last time you will first have to repeat     the mounting commands:
"sudo mkdir /media/sda3
sudo mount   -t ext3 /dev/sda3 /media/sda3"
and the same for sd8 and sda9)

Copy the whole content of the  terminal and post it here.


Places should be on the menu in the top left corner of your computer screen. (Applications  Places ....)  Click on Places and pull down to "computer"
This assumes that you are using Ubuntu and not some other flavor like Kubuntu or Xubuntu

---

### Post by padraic99 on 2007-12-01
Wow Meierfra, thnx for the quick reply. 

Ok, first off, I'm using Kubuntu so I guess that's why I didn't see Places. Only Install icon is showing on the desktop.

Intially, I don't have gksudo installed but I just install it according to the prompt. Then it's the same error again. Here's what it looks like below (very sorry for the verbiage-I've edited out the download part)

> ubuntu@ubuntu:~$ sudo mkdir /media/sda3
ubuntu@ubuntu:~$ sudo mount   -t ext3 /dev/sda3 /media/sda3
ubuntu@ubuntu:~$ gksudo gedit /media/sda3/grub/menu.lst
The program 'gksudo' is currently not installed.  You can install it by typing:
sudo apt-get install gksu
bash: gksudo: command not found
ubuntu@ubuntu:~$ sudo apt-get install gksu
Reading package lists... Done
Building dependency tree
Reading state information... Done
The following extra packages will be installed:
  gconf2 gnome-keyring libgksu2-0 libgnome-keyring0 libgtop2-7 libgtop2-common
The following NEW packages will be installed:
  gconf2 gksu gnome-keyring libgksu2-0 libgnome-keyring0 libgtop2-7
  libgtop2-common
0 upgraded, 7 newly installed, 0 to remove and 0 not upgraded.
Need to get 471kB of archives.
After unpacking 4243kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/main gconf2 2.18.0.1-0ubuntu1 [139kB]
...
Fetched 471kB in 2s (219kB/s)
Selecting previously deselected package gconf2.
(Reading database ... 79002 files and directories currently installed.)
Unpacking gconf2 (from .../gconf2_2.18.0.1-0ubuntu1_amd64.deb) ...
Selecting previously deselected package gnome-keyring.
Unpacking gnome-keyring (from .../gnome-keyring_0.8.1-0ubuntu1_amd64.deb) ...
Selecting previously deselected package libgnome-keyring0.
Unpacking libgnome-keyring0 (from .../libgnome-keyring0_0.8.1-0ubuntu1_amd64.deb) ...
Selecting previously deselected package libgtop2-common.
Unpacking libgtop2-common (from .../libgtop2-common_2.14.8-0ubuntu1_all.deb) ...
Selecting previously deselected package libgtop2-7.
Unpacking libgtop2-7 (from .../libgtop2-7_2.14.8-0ubuntu1_amd64.deb) ...
Selecting previously deselected package libgksu2-0.
Unpacking libgksu2-0 (from .../libgksu2-0_2.0.3-3ubuntu5_amd64.deb) ...
Selecting previously deselected package gksu.
Unpacking gksu (from .../gksu_2.0.0-1ubuntu3_amd64.deb) ...
Setting up gconf2 (2.18.0.1-0ubuntu1) ...

Setting up gnome-keyring (0.8.1-0ubuntu1) ...
Setting up libgnome-keyring0 (0.8.1-0ubuntu1) ...

Setting up libgtop2-common (2.14.8-0ubuntu1) ...
Setting up libgtop2-7 (2.14.8-0ubuntu1) ...

Setting up libgksu2-0 (2.0.3-3ubuntu5) ...

Setting up gksu (2.0.0-1ubuntu3) ...

ubuntu@ubuntu:~$ gksudo gedit /media/sda3/grub/menu.lst
X Error: BadDevice, invalid or uninitialized input device 167
  Major opcode:  144
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 167
  Major opcode:  144
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
ubuntu@ubuntu:~$ cd /media/sda3/grub
bash: cd: /media/sda3/grub: No such file or directory
ubuntu@ubuntu:~$ ls
Desktop
ubuntu@ubuntu:~$ cd /media/sda8/boot
bash: cd: /media/sda8/boot: No such file or directory
ubuntu@ubuntu:~$ cd grub
bash: cd: grub: No such file or directory
ubuntu@ubuntu:~$ ls
Desktop
ubuntu@ubuntu:~$ cd /media/sda9/boot
bash: cd: /media/sda9/boot: No such file or directory
ubuntu@ubuntu:~$ cd grub
bash: cd: grub: No such file or directory
ubuntu@ubuntu:~$ cd /media/sda3/grub
bash: cd: /media/sda3/grub: No such file or directory
ubuntu@ubuntu:~$ cd /media/sda3/boot
bash: cd: /media/sda3/boot: No such file or directory
ubuntu@ubuntu:~$ cd /media/sda3
ubuntu@ubuntu:/media/sda3$ ls
abi-2.6.20-15-generic             memtest86+.bin
config-2.6.20-15-generic          System.map-2.6.20-15-generic
initrd.img-2.6.20-15-generic.bak  vmlinuz-2.6.20-15-generic
lost+found
ubuntu@ubuntu:/media/sda3$

> ubuntu@ubuntu:~$ sudo mkdir /media/sda9
ubuntu@ubuntu:~$ sudo mount   -t ext3 /dev/sda9 /media/sda9
ubuntu@ubuntu:~$ ls
Desktop
ubuntu@ubuntu:~$ cd /media/sda9
ubuntu@ubuntu:/media/sda9$ ls
lost+found
ubuntu@ubuntu:/media/sda9$


> ubuntu@ubuntu:~$ sudo mount   -t ext3 /dev/sda8 /media/sda8
mount: /dev/sda8 already mounted or /media/sda8 busy
mount: according to mtab, /dev/sda8 is already mounted on /media/sda8
ubuntu@ubuntu:~$ cd /media/sda8/
ubuntu@ubuntu:/media/sda8$ ls
bin    dev   initrd      lib64       mnt   root  sys  var
boot   etc   initrd.img  lost+found  opt   sbin  tmp  vmlinuz
cdrom  home  lib         media       proc  srv   usr
ubuntu@ubuntu:/media/sda8$ cd boot
ubuntu@ubuntu:/media/sda8/boot$ ls
ubuntu@ubuntu:/media/sda8/boot$ cd grub
bash: cd: grub: No such file or directory
ubuntu@ubuntu:/media/sda8/boot$     

[INDENT]"You didn't have a new window open up after "gksudo gedit ...."?"[/INDENT] 
-Nope, nada.

---

### Post by meierfra on 2007-12-01
Sorry,  you said that you were using Kubuntu in your  very first post, but I missed that. It  explains some of the problems. For example Kubuntu uses "kdesu" in place of "gksudo". 

But it seems that Grub  never got install and  you do not have a menu.lst. So you will have to install grub.

Did you ever try to boot in Kubuntu with Super Grub? Installing Grub would be easier from Kubuntu when from the LiveCD. 

It is getting very late  here and I'm on my way to bed. But I'll check back in tomorrow morning.

---

### Post by padraic99 on 2007-12-01
No worries meierfra, I really appreciate you taking the time in the first place. I'm on my way to bed too. My brain's toast from this and my young ones staying up waaay past their bedtime.

I have tried to boot into K from SuperGrub, to no avail. I've tried variations in the menu but I don't remember which ones exactly. I'll have to delve a little deeper. I also have a Linux "rescue cd" that I dl'd a few days ago but it's even more confusing than Linux. :) 

Anyway, I'm still impressed with what I see so l'm willing to work towards a solution. Might as well get the full bang for my 64-bit buck too, and it ain't gonna be with Vista.

As you sip your morning java, lemme ask you your opinion on partitions--which ones are crucial to a stable install? Am I unnecessarily complicating things? (I'm still figuring out the directory structure, obviously) I'm guessing it depends on the user's needs--

If I can get comfortable enough I suspect it'll be my main OS. I do lots of writing, image manipulation, video editing, ripping and archiving music, etc. Nothing highly specialized.

Anyway, thanks again. Looking forward to your reply.

---

### Post by meierfra on 2007-12-01
O.K. I'm back. 

> partitions--which ones are crucial to a stable install? Am I unnecessarily complicating things? 

Your  home partition is a good idea (Doesn't  make the system more stable, but makes your life easier if you ever do a fresh install)   A separate  /boot partition is usually not necessary, but it doesn't hurt either. So your partitioning is just fine. 

Your /boot partition  actually is at the beginning at the drive. You can see that from the numbers in fdisk

> /dev/sda3 1 13 104391 83 Linux

This says that  "dev/sda3" (your boot partiton) sits on tracks   1 to 13.

After  that comes your Windows partition (starting at track 14)

> dev/sda1 * 14 5352 42885486 7 HPFS/NTFS

Well,  now you know why  "fdisk" said:

> Partition table entries are not in disk order

This happens if  you create a partition in front of an already existing partition. But Iit should not course any problems.


To install grub:

Step 1: Save the the attached "menu.txt"  as "menu.lst" in your home folder:

You probably know how to do that but here are the instructions anyway:
Click on "menu.txt" at the bottom of this post.
This should open a file browser. 
Click on "ubuntu" in the left pane.
Change  "menu.txt" in the name field to "menu.lst"
Click on save.

Step 2 Move "menu.lst" to /boot/grub"

```
sudo mkdir /media/sda3
sudo mount   -t ext3 /dev/sda3 /media/sda3
sudo mkdir  /media/sda3/grub
cd
sudo mv  menu.lst  /media/sda3/grub

```

Step 3 Install grub

```
sudo grub-install --root-directory=/media/sda3 /dev/sda
```


Step 4 Just for later trouble shooting:

Copy  the content of the terminal and post it here.

Step 5  Reboot, remove the LiveCD and hope for the best.

---

### Post by padraic99 on 2007-12-01
Mornin' meierfra,

Right, I put that boot partition first so I wouldn't run into that BIOS problem, though lately I've been reading that it probably wouldn't have mattered on this box.

Alright, that seemed to go well, though I haven't yet rebooted. No errors reported. I used to Kate to open the txt file (nothing opened it by default) then saved it to /home/ubuntu/. Output as follows:

> ubuntu@ubuntu:~$ sudo mkdir /media/sda3
ubuntu@ubuntu:~$ sudo mount   -t ext3 /dev/sda3 /media/sda3
ubuntu@ubuntu:~$ sudo mkdir  /media/sda3/grub
ubuntu@ubuntu:~$ cd
ubuntu@ubuntu:~$ sudo mv  menu.lst  /media/sda3/grub
ubuntu@ubuntu:~$ sudo grub-install --root-directory=/media/sda3 /dev/sda
Probing devices to guess BIOS drives. This may take a long time.
Due to a bug in xfs_freeze, the following command might produce a segmentation
fault when /media/sda3/boot/grub is not in an XFS filesystem. This error is harmless and
can be ignored.
xfs_freeze: specified file ["/media/sda3/boot/grub"] is not on an XFS filesystem
Installation finished. No error reported.
This is the contents of the device map /media/sda3/boot/grub/device.map.
Check if this is correct or not. If any of the lines is incorrect,
fix it and re-run the script `grub-install'.

(fd0)   /dev/fd0
(hd0)   /dev/sda
(hd1)   /dev/sdb
ubuntu@ubuntu:~$   

I'm rebooting now...

---

### Post by padraic99 on 2007-12-01
Hmm, so close.

After rebooting I get to a grub prompt. I can use <Tab> to  see a list of commands (tried "boot" and "kernel" but I'm missing some parameters it seems). 

Does this sound like something that can be edited in the menu.lst file?

---

### Post by meierfra on 2007-12-01
Looking at  the output you posted, I was pretty sure that it would fail. (Sorry I have no real experience with a separate /boot partition) Try the following at the grub prompt at boot-up


root		(hd0,2)
kernel		/vmlinuz-2.6.22-14-generic root=/dev/sda8 ro quiet splash
initrd		/initrd.img-2.6.22-14-generic
boot

---

### Post by padraic99 on 2007-12-01
Ok, I'll try that. It looks like I'm pointing the boot to where the "/" lies- or the heart of the installed kernel?

Let's see what happens.

---

### Post by padraic99 on 2007-12-01
I've commandeered my wife's MacBook Pro so I'll just stay at the grub menu on my machine.

Ran the first line "root..."

Nothing appeared to happen, just returned me to the grub prompt.

Ran the 2nd line and got "Error 15: File not found"

Is this telling me it can't find the kernel anywhere?

(also tried sda9 in the 2nd command)

---

### Post by meierfra on 2007-12-01
My bad. I thought I had checked that you have the same kernel as I do. But you don't . You need to use different numbers:


root (hd0,2)
kernel /vmlinuz-2.6.20-15-generic root=/dev/sda8 ro quiet splash
initrd /initrd.img-2.6.20-15-generic
boot

---

### Post by padraic99 on 2007-12-01
Sorry for the delay meierfra, my llittle girl woke from nap.

So I got one step further before the 3rd command line returned a, "Error 15: File not found" and returned me to grub prompt.

Puzzling huh? 

I had made that boot partition with the idea that I may install another flavor down the road and this way the grubs wouldn't override each other, or the mbr. That may for an intermediate/advanced user I'm starting to think.

---

### Post by meierfra on 2007-12-01
> ubuntu@ubuntu:/media/sda3$ ls
abi-2.6.20-15-generic memtest86+.bin
config-2.6.20-15-generic System.map-2.6.20-15-generic
initrd.img-2.6.20-15-generic.bak vmlinuz-2.6.20-15-generic


You don't have "initrd.img-2.6.20-15-generic"  only the back up file!!!

Something did go wrong  fundamentally when you installed Kubuntu It might be time to call it
quit and do a fresh install.  But let me give it one  more try:

Boot from the Live CD..

Step 1) ``install-grub'' put the grub files in  the wrong folder. So we need to
move them.

```

sudo mkdir /media/sda3
sudo  mount -t ext3 /dev/sda3 /media/sda3
cd /media/sda3 
sudo mv  boot/grub/*  grub/  
 
```

Step 2) Recreate "intrd" from its backup:

```
  sudo cp initrd.img-2.6.20-15-generic.bak initrd.img-2.6.20-15-generic
```

Step 3) I used the wrong  kernel version  in ``menu.lst''
To fix that 

```
 kdesu kate grub/menu.lst 
```

Change all ``2.6.22-14'' to ``2.6.20-15'' (there are four of them)

Step 4) Reinstall Grub:


```
 sudo grub
```

and at the "grub>" prompt:

```

root (hd0,2)
setup (hd0)
quit
```

Step 5 Reboot.

---

### Post by padraic99 on 2007-12-01
Got this in first batch of commands:

> mount: mount point /media/sda3 does not exist
ubuntu@ubuntu:~$ sudo mkdir /media/sda3
ubuntu@ubuntu:~$ sudo  mount -t ext3 /dev/sda3 /media/sda3
ubuntu@ubuntu:~$ cd /media/sda3
ubuntu@ubuntu:/media/sda3$ sudo mv  boot/* ./
mv: cannot move `boot/grub' to a subdirectory of itself, `./grub'
ubuntu@ubuntu:/media/sda3$

But I think I'm seeing (sorta) what you're trying to do here.

** I know you have a life outside of this so I'll check back after running errands myself. I really appreciate everything you've suggested so far and if it comes down to a reinstall, so be it. I just have to figure out how to do that so that the files go where they're intended.

Cheers!

P

---

### Post by meierfra on 2007-12-01
Im not sure why you got that error  message.  Try 

```
sudo mv boot/grub/* grub/ 
```

instead of  "sudo mv  boot/* ./

(I changed my original post accordingly)

Edit: I figured out why my orginal command did not work (One cannot move a folder to a location which has a folder with the same name) So now I'm confident that my new command will work

---

### Post by padraic99 on 2007-12-01
Arrrrgh!! ](*,)  

So close it seems... 

So when I reboot I get the splash screen and Kubuntu appears to be loading. It never reaches the GUI login; just seems to freeze with a greenish brown screen. I can get a text prompt by hitting Ctrl+Alt+F1, (or ALt+F1), where it asks me for "king" logon. 

My original username and pw don't work here. I didn't try just hitting "Enter" for both.

Btw, I've always had to boot the live CD into safe graphics mode, and the first time I had it installed (only 2 partitions, couple of months ago) when I blindlyupdated the kernel (everything that was on the list) the same thing happened. My sense from what I read is that my Nvidia drivers need to be updated manually. I have a BFG GeForce 7800 GT OC graphics card.

Is this a whole new problem set you think?

---

### Post by meierfra on 2007-12-01
```
Is this a whole new problem set you think?
```

I think so. And its outside of my area of expertise. You might want to start a new thread. But I actually vote to reinstall. Basically everything we looked at so far had some kind of problem.  So it could be that your current problems are also just caused by a bad install.

If you reinstalled, I recommend to choose "check cd for defects" (or something like)  at the first screen of the LiveCD, to make sure that your CD is o.k.

---

### Post by padraic99 on 2007-12-01
Ya, I think I'm going to reinstall now. Thanks for all your help, meierfra. If this is a standard level of patience for problems it seems like a good place to be.

All the best, (until my next problems come up!)

P

---

### Post by meierfra on 2007-12-02
> Ya, I think I'm going to reinstall now 

Good luck.

> thanks for all your help, meierfra

You are welcome.

---

