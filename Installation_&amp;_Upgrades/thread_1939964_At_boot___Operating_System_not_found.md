---
title: "At boot :  Operating System not found"
date: 2012-03-12
forum: Installation &amp; Upgrades
---

### Post by Mlok on 2012-03-12
Hello!

I have bought a brand new Lenovo x121e and wiped out everything on the disk (removed all windows 7 partitions) to install ubuntu 11.10. Installation went fine.

Then I tried to boot but it stops after a few seconds : "Operating System not found"
(I used to also have a PXE-M0F error, but I removed the "boot on LAN" option so this error doesn't show up anymore)

I haven't been able to find an answer on the forums.
Can anybody help?

Thanks a lot!

---

### Post by Mlok on 2012-03-12
Update :
I tried to flag my Ubuntu partition (/dev/sda1) with the flag "boot" and rebuild the MBR with
```
sudo install-mbr -i n -p D -t 0 /dev/sda
```
-i n = no prompt
-p D = boot on partition with flag "boot"
-t 0 = do not wait before booting

but it does not change a thing. Still stuck with a "bricked" brand new laptop...

Help is much needed... Thank you!

---

### Post by acc61287 on 2012-03-12
> **Mlok said:**
> Update :
I tried to flag my Ubuntu partition (/dev/sda1) with the flag "boot" and rebuild the MBR with
```
sudo install-mbr -i n -p D -t 0 /dev/sda
```
-i n = no prompt
-p D = boot on partition with flag "boot"
-t 0 = do not wait before booting

but it does not change a thing. Still stuck with a "bricked" brand new laptop...

Help is much needed... Thank you!

Did you try sudo os-prober?

---

### Post by Mlok on 2012-03-12
Hi, thank you for your advice

I just tried it now and it returns
/dev/sda1:Ubuntu 11.10 (11.10):Ubuntu:linux
...but still no luck.

---

### Post by Mlok on 2012-03-12
I read somewhere that the boot sequence for a computer was this (with possible errors):

> 
0. Power on
1. BIOS (Self-test of hardware, looks for bootable device)
2. BIOS loads MBR
[INDENT]=> Read MBR and executes content[/INDENT]
3. Load Stage 1 Grub from MBR
[INDENT]=> (if error) BIOS reports "Missing operating system"[/INDENT]
4. Load Stage 1.5 then stage 2 of GRUB
[INDENT]=> "GRUB" displayed[/INDENT]
5. GRUB reads menu.lst
    [INDENT]=> Drop into GRUB command line[/INDENT]
6. Present boot-time menu
7. GRUB loads kernel image and initial RAM disk
[INDENT]    => (if error) Grub reports "Error 15: File not found"[/INDENT]
8. Kernel mounts root file system
[INDENT]    => (if error) Kernel reports panic, or just freeze[/INDENT]
9. Kernel runs init
[INDENT]    => (if error) Kernel may panic or drop you into a root shell[/INDENT]
10. init runs scripts to start user-level services



So I guess I am stuck at step 3?

---

### Post by Mlok on 2012-03-12
New informations : from my live ubuntu thumbdrive GRUB prompt I tried this command to detect devices & partitions :
```
grub> ls
(memdisk) (hd0) (hd0,msdos1) (hd1) (hd1,gpt6) (hd1,gpt5) (hd1,gpt4) (hd1,gpt3) (hd1,gpt2) (hd1,gpt1)

```
First thing : I wonder what this (hd0,msdos1) is? In this computer there is only one HDD, and I formatted it. Could this be a leftover from the Windows install? Could it be some security boot partition preventing me from installing a new system or a new MBR ?

The (hd1) device has many partitions I recognize :
[LIST]
[*]1:installed ubuntu system
[*]2:ubuntu swap
[*]3:future mint system
[*]4:future mint swap
[*]5:installed home partition
[*]6:tiny partition at the very beginning of the disk (this is how it is showed on gparted) that I tried to use some time ago with a "bios_grub" flag ; but I have now removed this flag
[/LIST]

So I went on and tried to set grub on the installed ubuntu partition :
```

grub> set root=(hd1,1)

```
No error message, but then :
```
set prefix=(hd1,1)/boot/grub
error: file not found.
error: file not found.
error: file not found.
error: file not found.

```
(yes the error message repeats 4 times!)
So it looks like I need to make the link to GRUB somehow.
(Help is still welcome)

---

### Post by Mlok on 2012-03-12
For some reason, I launched the same command and it did not give an error.
So I went on :
```
grub> insmod normal
grub> normal

```
This gives me GRUB!
But no entry works : I get this error now :
```
error: invalid arch independant ELF magic.
```
(and without the live ubuntu thumbdrive I still don't get to GRUB)

ELF Magic...
It's getting close to 5am here. I think I need to sleep now, dream of that invalid arch, find that independant Elf and steal his magic.

I'll be back.
Help is welcome.

---

### Post by lisati on 2012-03-12
Just a quick aside: the grub tutorial that refers to menu.lst is for an older version of grub that works differently to the versions installed with recent versions of Ubuntu.

Have a look here for more information: [https://help.ubuntu.com/community/DualBoot/Grub](https://help.ubuntu.com/community/DualBoot/Grub)

---

### Post by acc61287 on 2012-03-13
> **Mlok said:**
> Hi, thank you for your advice

I just tried it now and it returns
/dev/sda1:Ubuntu 11.10 (11.10):Ubuntu:linux
...but still no luck.

Sad to say, but I guess you delete your window partition :(

---

### Post by Mlok on 2012-03-13
Thank you lisati for that link.

acc61287, yes I wanted to get rid of Windows. And removed all its partitions.

I have been working on this issue for maybe twelve hours, and in my dreams I found an wrecked arch, on which an elf was using its magical powers to stay independant from the proprietary world. He told me (in elvish, which I speak fluently) to not just remove partitions and install ubuntu on the remains, but that I shall simply choose the option to "erase everything and install ubuntu" right from the installer.

So simple.
It works well now.
I spent twelve hours on this...
(well I got to learn a bit about the boot sequence...)

Thank you all for your help.
I truly hope this will help someone someday.
I spent twelve hours on this.

---

### Post by adstri on 2012-03-13
Hello!! 

I am having a similar issue but need to keep the windows OS installed because there are a few programmes I struggle to run in a virtual box if anyone can help it would be greatly appreciated: 

[http://ubuntuforums.org/showthread.php?t=1940167](http://ubuntuforums.org/showthread.php?t=1940167) 

:)

---

### Post by Thebuntuway on 2012-03-13
I have learn this on ICT class..hope these works well on you
1.***Get/download*** ubuntu (what ever version) in others computer. i hope it using windows 7 because im also new in linux.
2.Buy usb stick at least had ***8 gb*** for great perfomance. This is important because the more gb you pendrive is, the more fast it install
3.Go download [pendrivelinux.com]("http://www.pendrivelinux.com/universal-usb-installer-easy-as-1-2-3/#button") and open it up. then install your ubuntu in you usb stick. If not understand, go to [http://www.ubuntu.com/download/ubuntu/download](http://www.ubuntu.com/download/ubuntu/download) for information and more guide
4.Now, go to your 'no operating system' computer and start it. These time, insert your usb stick before start you machine.
5.When the bios appears, open it up and go to 'boot' menu. Make the 'usb hdd' be the first boot section. Save and exit
6.After that, ubuntu menu will appears and pick 'install ubuntu in this hard drive'
7.Go on, install your os and wait for it to finish...
8.Restart your pc, and it will give you a new os inside your pc!..
**HOPE THESE HELP!**

---

### Post by Thebuntuway on 2012-03-13
> **adstri said:**
> Hello!! 

I am having a similar issue but need to keep the windows OS installed because there are a few programmes I struggle to run in a virtual box if anyone can help it would be greatly appreciated: 

[http://ubuntuforums.org/showthread.php?t=1940167](http://ubuntuforums.org/showthread.php?t=1940167) 

:)

Actually, using virtual box in no operating system computer will never be work. It need os anyway...:guitar:

---

### Post by Mlok on 2012-03-13
Theubuntuway : Yes that is what I did to solve my problem, when installing ubuntu from my live ubuntu thumbdrive, I chose the option to "Erase everything and install Ubuntu" and it worked.

Previously, what did not work, I used to choose the wrong option : "Something else" because it lets you create partitions the way you want. That did not work.

---

### Post by critin on 2012-03-13
> **Mlok said:**
> Thank you lisati for that link.

acc61287, yes I wanted to get rid of Windows. And removed all its partitions.

I have been working on this issue for maybe twelve hours, and in my dreams I found an wrecked arch, on which an elf was using its magical powers to stay independant from the proprietary world. He told me (in elvish, which I speak fluently) to not just remove partitions and install ubuntu on the remains, but that I shall simply choose the option to "erase everything and install ubuntu" right from the installer.

So simple.
It works well now.
I spent twelve hours on this...
(well I got to learn a bit about the boot sequence...)

Thank you all for your help.
I truly hope this will help someone someday.
I spent twelve hours on this.

Miok, are you a writer?  If not, you could be.

Simple after you fix it.  lol  This is the point of (my) using ubuntu--learning something new and interesting.

---

