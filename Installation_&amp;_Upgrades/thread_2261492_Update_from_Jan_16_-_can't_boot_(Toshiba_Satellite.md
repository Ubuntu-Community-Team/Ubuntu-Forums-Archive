---
title: "Update from Jan 16 - can't boot (Toshiba Satellite Pro)"
date: 2015-01-19
forum: Installation &amp; Upgrades
---

### Post by steven-misshula on 2015-01-19
Hi All,

the other night, i diligently installed my sofware updates and the computer went to reboot; but I was never able to get back to the regular start up screen.

My original thought was that I had this problem (or some variation therof): 

[B] [http://ubuntuforums.org/showthread.php?t=2261134](http://ubuntuforums.org/showthread.php?t=2261134)  
[/B]
Albeit slightly different as I don't have a black screen, but rather the 2nd image at this link:   
[B]
[http://www.howtogeek.com/196740/how-to-fix-an-ubuntu-system-when-it-wont-boot/](http://www.howtogeek.com/196740/how-to-fix-an-ubuntu-system-when-it-wont-boot/)[/B]

None of the recovery modes work (choices under "Advanced Options").

Any thoughts?

I'm using a Toshiba Satellite Pro (C675-S-7200 <ES5.0> ) and was on Ubuntu 14.04

Oh forgot to mention:

I do get the, "grub>" prompt if I choose "C"

and I can edit the launch commands by choosing "e"

And when I try a boot repair from:
[B]
[http://www.howtogeek.com/114884/how-to-repair-grub2-when-ubuntu-wont-boot/](http://www.howtogeek.com/114884/how-to-repair-grub2-when-ubuntu-wont-boot/)[/B]

sudo add-apt-repository ppa:yannubuntu/boot-repair
sudo apt-get update
sudo apt-get install -y boot-repair
boot-repair[/

I get:
Error: need a single repository as argument

so in my continued searching, i've tried using grub to salvage things and have come across this:

[B][http://www.linux.com/learn/tutorials/776643-how-to-rescue-a-non-booting-grub-2-on-linux/](http://www.linux.com/learn/tutorials/776643-how-to-rescue-a-non-booting-grub-2-on-linux/)
[/B]
when i get to the "Booting from Grub" section about 1/2 way down:grub> linux /boot/vmlinuz-3.13.0-29-generic root=/dev/sda1

i use:

grub> linux /boot/vmlinuz-3.13.0-44-generic root=/dev/sda1

and I get:

error: failure reading sector 0x681138 from 'hdo'
thoughts?

---

### Post by Bashing-om on 2015-01-19
steven-misshula; Hi ! Welcome to the forum .

1st, what results when you attempt to boot the "recovery console" from grub's advanced options ?

Next in order to guide you in booting from the grub prompt; What are we working with ?
Boot the liveDVD(USB) and
Post back the outputs - Between Code Tags - of terminal commands:
```

sudo fdisk -lu
parted -l
sudo blkid

``` so we know what to tell grub to do.
code tag tutorial:
[http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168](http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168)

To soon to say
[INDENT][INDENT][INDENT]but we poke at it 'til we know
[/INDENT][/INDENT][/INDENT]

---

### Post by steven-misshula on 2015-01-19
after 
sudo fdisk - lu:
____________________________________________________-
Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x00088545

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048   968564735   484281344   83  Linux
/dev/sda2       968566782   976771071     4102145    5  Extended
Partition 2 does not start on physical sector boundary.
/dev/sda5       968566784   976771071     4102144   82  Linux swap / Solaris

Disk /dev/sdb: 8019 MB, 8019509248 bytes
255 heads, 63 sectors/track, 974 cylinders, total 15663104 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *          32    15647309     7823639    b  W95 FAT32
ubuntu@ubuntu:~$ 

and then:

ubuntu@ubuntu:~$ parted -l
ubuntu@ubuntu:~$ sudo blkid
/dev/loop0: TYPE="squashfs" 
/dev/sda1: UUID="9ec31deb-19a4-4ffd-8b08-f2a547541258" TYPE="ext4" 
/dev/sda5: UUID="6084c0a8-5807-42e6-9739-189da99b3483" TYPE="swap" 
/dev/sdb1: LABEL="UUI" UUID="BCA4-6783" TYPE="vfat" 
ubuntu@ubuntu:~$ ^C
ubuntu@ubuntu:~$ 

_______________________________________________________

forgot to mention....i'm in "try Ubuntu:" mode after booting off my USB.

---

### Post by chris_h2 on 2015-01-19
I have a similar problem, except that I am using it inside VMware.
I have been using it for months without any issues, and when I first booted up today it told me there were updates and went ahead. I didn't reboot straight after the updates, I carried on with what I was doing.
I decided I was going to take a snapshot because I've made some progress, but decided to do it after rebooting to take the update into account.
After rebooting I get:
1. A very brief purple screen,
2. An underline, at which I can type stuff but doesn't appear to do anything
3. The purple screen with the dots being filled in
4. The black screen.
I'm not a regular Linux user and don't understand how to do these tweaks being talked about below (grub etc).
The web site I'm developing appears to be working and my SMB shares are working.
Unfortunately I hadn't set up remote telnet access, so using Putty with or without SSH doesn't seem to work. Standard tenet session just disappears and SSH gives me "Network Error: connection refused"
Hitting some random keys whilst booting sometimes takes me into a recovery menu, where I can select various options. Dropping to root doesn't let me do anything - it says it's in read-only mode. clean, dpkg and fsck seem to stick doing nothing after telling me how many files and blocks there are. The failsafe graphics boots back to the black screen. I don't know what to try next.
Any advice appreciated.
Thanks,
Chris

---

### Post by Bashing-om on 2015-01-19
chris_h2; Hi !

As you are working a VM, the solution(s) offered here may not apply to your situation.
I suggest that you start your own thread to get a more appropriate audience .
have you tried to boot up an older kernel ( grub's advanced options menu) ?
----------------------------------

steven-misshulal OK ..

Looks standard and only 'buntu installed to that hard disk. let's see if we can boot up from grub's boot menu as you have been trying:
Boot the install to the grub boot menu -> 
let's see what happens when we try and boot the current kernel.
With the latest kernel selected at the boot menu press 'c' -> grub command line:
```

set prefix=(hd0,1)/boot/grub
set root=(hd0,1)
linux (hd0,1)/vmlinuz root=/dev/sda1 ro
initrd (hd0,1)/initrd.img
boot

```
All we are doing here is telling grub the symmetry of the hard drive and the kernel where the boot files are located. 
Depending on what results, is what we do next.

[INDENT][INDENT]it's all in the process
[/INDENT][/INDENT]

---

### Post by steven-misshula on 2015-01-19
Hi Bashing-OM,
ok....typed in the first two lines...no problem, no errors

after the third line:  
linux (hd0,1)/vmlinuz root=/dev/sda1 ro

I received the following error after a long pause:
_________________
error: failure reading sector Ox681138 from 'hd0'
_____________

Here's a thought, this is a recently replaced hard drive in this machine...could it be a hard drive issue? (it's a Toshiba brand 500 GB)

Many thanks for the help...

Steve

but that doesn't make sense....it happened right after the update 
never mind..

---

### Post by Bashing-om on 2015-01-19
steven-misshula: Yeah ...

Tend to agree hardware pproblem.

It does warrant doing a file system check, and see if e2fsck also advises of problems;

From the live(usb), so the file systems are in a not-mounted condition; make sure in GParted that "swap" also is not mounted :
```

sudo e2fsck -C0 -p -f -v /dev/sda1

#if errors: -y auto answers yes for fixes needing response see man e2fsck
sudo e2fsck -f -y -v /dev/sda1

```
Post back any reported errors.

If there are no errors .. see now - after the file system check/repair - what results when attempting to boot the install .

[INDENT][INDENT]maybe YES
[INDENT][INDENT][INDENT]maybe not so yes
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by steven-misshula on 2015-01-19
Another thought....since I can "try Ubunut" from my USB, and thus have access to a terminal...is there a way in through that?

the prompt I get on the terminal is:  

ubuntu@ubuntu

from what  i can tell with my limited linux knowledge, i don't really ahve access to the install from the terminal (don't know how to change the directory...or whatever).  However, in the file manager, I do show the files from the local computer under the Device Name:  496 GB Volume (i.e. that is my hard drive - mentioned above).

Sorry for the rambling...just thought more info...the better.

Steve

---

### Post by chris_h2 on 2015-01-19
Thanks, yes I tried all the options. It's really frustrating because I was just about to take a snapshot.
I'll post it in a new thread as you suggest.

Chris

---

### Post by Bashing-om on 2015-01-19
steven-misshula; Yeah,

You have the right of it:
> 
Another thought....since I can "try Ubunut" from my USB, and thus have access to a terminal...is there a way in through that?


That is what I am suggesting to do.
From the live(USB) in terminal run the file system checks/repair commands. Do make sure about swap not being mounted. Fire up GParted in the live(USB) and IF there is a key icon on the swap partition - it is identified - then right click on the partition and choose "swap off" . Then run the terminal commands.

See how this goes, and if e2fsck comes back clean, we know to restore the boot code to the boot sector of the hard drive . But let us not cross bridges 'til we come to them.

[INDENT]knowledge.
[INDENT][INDENT][INDENT]that source of great power
[/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by steven-misshula on 2015-01-19
Hi Bashing Om,

Here's what I got:
_________________________________
ubuntu@ubuntu:~$ sudo e2fsck -C0 -p -f -v /dev/sda1
/dev/sda1 is mounted.
e2fsck: Cannot continue, aborting.

_______________________________________

I hate to say it...you lost me a little bit on post #15... do you have a specific code line for me to enter?

Also, on post #12 -not sure what to do with the following:
_________________________________
#if errors: -y auto answers yes for fixes needing response see man e2fsck
sudo e2fsck -f -y -v /dev/sda1
_________________________________________
I did get the error from the first posted in my response #16...so, didn't think that there was anything for me to do...

Again Thanks!!!  (p.s. my brother is very impressed with your guidance - check him out on git hub:  [https://github.com/EvanMisshula](https://github.com/EvanMisshula)  )

Hi Basher -
Also, wanted to let you know i tried doing this (option #2):
[B]
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)[/B]

and got the following (pasted in order):
__________________________________________________________________
ubuntu@ubuntu:~$ **sudo add-apt-repository ppa:yannubuntu/boot-repair**
 Simple tool to repair frequent boot problems.

Website: [https://launchpad.net/boot-repair](https://launchpad.net/boot-repair)
 More info: [https://launchpad.net/~yannubuntu/+archive/ubuntu/boot-repair](https://launchpad.net/~yannubuntu/+archive/ubuntu/boot-repair)
Press [ENTER] to continue or ctrl-c to cancel adding it

gpg: keyring `/tmp/tmp90d3um/secring.gpg' created
gpg: keyring `/tmp/tmp90d3um/pubring.gpg' created
gpg: requesting key 60D8DA0B from hkp server keyserver.ubuntu.com
gpg: /tmp/tmp90d3um/trustdb.gpg: trustdb created
gpg: key 60D8DA0B: public key "Launchpad PPA for YannUbuntu" imported
gpg: Total number processed: 1
gpg:               imported: 1  (RSA: 1)
OK
ubuntu@ubuntu:~$ **sudo apt-get update**
Ign cdrom://Ubuntu 13.10 _Saucy Salamander_ - Release i386 (20131016.1) saucy InRelease
Ign cdrom://Ubuntu 13.10 _Saucy Salamander_ - Release i386 (20131016.1) saucy/main Translation-en_US
Ign cdrom://Ubuntu 13.10 _Saucy Salamander_ - Release i386 (20131016.1) saucy/main Translation-en
Ign cdrom://Ubuntu 13.10 _Saucy Salamander_ - Release i386 (20131016.1) saucy/restricted Translation-en_US
Ign cdrom://Ubuntu 13.10 _Saucy Salamander_ - Release i386 (20131016.1) saucy/restricted Translation-en
Ign [http://security.ubuntu.com](http://security.ubuntu.com) saucy-security InRelease                        
Hit [http://security.ubuntu.com](http://security.ubuntu.com) saucy-security Release.gpg                      
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) saucy InRelease                                
Hit [http://security.ubuntu.com](http://security.ubuntu.com) saucy-security Release
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) saucy InRelease                         
Hit [http://security.ubuntu.com](http://security.ubuntu.com) saucy-security/main i386 Packages      
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) saucy Release.gpg 
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) saucy-updates InRelease
Hit [http://security.ubuntu.com](http://security.ubuntu.com) saucy-security/restricted i386 Packages
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) saucy Release     
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) saucy Release.gpg                       
Hit [http://security.ubuntu.com](http://security.ubuntu.com) saucy-security/main Translation-en
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) saucy-updates Release.gpg
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) saucy/main i386 Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) saucy-security/restricted Translation-en
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) saucy Release    
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) saucy/main Translation-en                
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) saucy-updates Release                   
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) saucy/main i386 Packages               
Ign [http://security.ubuntu.com](http://security.ubuntu.com) saucy-security/main Translation-en_US
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) saucy/restricted i386 Packages
Ign [http://security.ubuntu.com](http://security.ubuntu.com) saucy-security/restricted Translation-en_US
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) saucy/main Translation-en
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) saucy/restricted Translation-en
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) saucy-updates/main i386 Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) saucy-updates/restricted i386 Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) saucy/main Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) saucy/restricted Translation-en_US
Reading package lists... Done
ubuntu@ubuntu:~$ [B]sudo apt-get install -y boot-repair && boot-repair
[/B]Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package boot-repair
ubuntu@ubuntu:~$ ^C
ubuntu@ubuntu:~$ 
_______________________________________________________

---

### Post by Bashing-om on 2015-01-19
steven-misshula; Well ..

You are working from the live(USB), correct ?
Then I must surmise that given:
> 
ubuntu@ubuntu:~$ sudo e2fsck -C0 -p -f -v /dev/sda1
[color=red]/dev/sda1 is mounted.[/color]
e2fsck: Cannot continue, aborting.

You were mucking about and forgot to UN-mount the partition, as advised the partition MUST be unmounted and swap must be turned off.

So, let's see what the system says is mounted:
From that live(USB) in terminal:
```

mount
cat /etc/mtab
sudo blkid
df -h
free -m

```

bk

as to boot-repair ..
You are using an obsolete release -  Saucy Salamander - that no longer has support. It has no access to the software repository ! IF we are to effect ANY repair to the boot code on the install then we MUST have a live(USB)/DVD of the version that is installed !! gotta !
--------------------------
off topic:
> 
Again Thanks!!! (p.s. my brother is very impressed with your guidance

Appreciate that vote of confidence ( I can use all the help I can get) .

get our ducks all in a row;
[INDENT][INDENT][INDENT]on the same page
[INDENT][INDENT][INDENT]and we take off again
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by steven-misshula on 2015-01-20
Hi Basher,


> That is what I am suggesting to do.
From the live(USB) in terminal run the file system checks/repair  commands. Do make sure about swap not being mounted. Fire up GParted in  the live(USB) and IF there is a key icon on the swap partition - it is  identified - then right click on the partition and choose "swap off" .  Then run the terminal commands.

I don't know how to do this...^ (above)  :confused:

Unless it is this:

> So, let's see what the system says is mounted:
From that live(USB) in terminal:
 	Code:

 	mount
cat /etc/mtab
sudo blkid
df -h
free -m 


---

### Post by Bashing-om on 2015-01-20
steven-misshula; Hey, hey

I am with you ... what ever it takes is what we do .
so:
> 
I don't know how to do this...^ (above)  &#65532;

Let's insure we are on the same page so my instruction is more to the point. What release and what Desktop Environment are you running ?
Presently all we want to know is that the file system is intact, and then we can move on.

[INDENT][INDENT]ain't no step for a stepper
[/INDENT][/INDENT]

---

### Post by steven-misshula on 2015-01-20
**The laptop:**
Release:  14.04
Desktop Env:  Ubuntu (default - I guess UNITY)

**USB Stick:** 
Release 13.1
Desktop Env - same UNITY or whatever the default)

---

### Post by Bashing-om on 2015-01-20
steven-misshula; Screech, from the brakes .

Ok ya got 14.04 installed, and we are going to run a file system check from the live(USB) . That is all well good fine and dandy .. What is not is the USB version at 13.10 or any other release .. We are working with a dedicated file system and in doing that check we really really want that check done from the same release as e2fsck is checking.

Take a bit and download/burn 14.04 .

and then we go
[INDENT][INDENT][INDENT]merrily on
[/INDENT][/INDENT][/INDENT]

---

### Post by steven-misshula on 2015-01-20
Also - need to mention, I'm at work during the day(M-F), so my responses are slow..... please know, I'm very interested in the responses/direction.

---

### Post by Bashing-om on 2015-01-20
steven-misshula; Hey;

> **steven-misshula said:**
> Also - need to mention, I'm at work during the day(M-F), so my responses are slow..... please know, I'm very interested in the responses/direction.

That is good info to know, but, we always try to go at your pace .
I prefer to work slowly, one step at a time.
Once we have the preliminaries out of the way, and are on firm footing, this may go very quickly to a conclusion .. BUT, no crossing bridges (good and bad) 'til we get to them.

[INDENT]we get the fulcrum
[INDENT][INDENT][INDENT]we have the lever
[INDENT][INDENT][INDENT][INDENT]we will move it
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by steven-misshula on 2015-01-25
:-(
Hi Bashing-Om:

So, I finally have a bootable USB stick... but somewhere in the process, i screwed up the broken machine even further - specifically, I can no longer boot via a USB ('ya know, by holding "F12" during boot up).

So literally now, all I get is the, "GNU GRUB version 2.02~beta2-9ubuntu1" screen after boot completes...

I tinker beyond my capabilities as you've guessed already.....and found the following:
[http://www.linux.com/learn/tutorials/776643-how-to-rescue-a-non-booting-grub-2-on-linux/](http://www.linux.com/learn/tutorials/776643-how-to-rescue-a-non-booting-grub-2-on-linux/) 
____________________________________________
[h=3]Booting From grub>[/h] This is how to set the boot files and boot the system from the grub> prompt. We know from running the ls command that there is a Linux root filesystem on (hd0,1), and you can keep searching until you verify where /boot/grub is. Then run these commands, using your own root partition, kernel, and initrd image:

> 

grub> set root=(hd0,1)
grub> linux /boot/vmlinuz-3.13.0-29-generic root=/dev/sda1
grub> initrd /boot/initrd.img-3.13.0-29-generic
grub> boot

THIS GETS ME A KERNEL PANIC!!!  

Ack...help?
Thanks...

---

### Post by Bashing-om on 2015-01-25
steven-misshula; UnGood;

Is this a lap top or a desktop machine ?
How many years has the present CMOS battery been in use ?
If this is a desk top, no big deal to replace that battery.

Until such time as you can access the bios setup, we are dead in the water.

[INDENT][INDENT][INDENT]maybe all it will take
[INDENT][INDENT][INDENT]a good power source
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by steven-misshula on 2015-01-27
Ugh.... crestfallen.

This is a laptop.

battery in use about 2.5-3.5 yrs.

I will try again tonight...I'll keep you posted.

Steve

---

### Post by Bashing-om on 2015-01-27
steven-misshula; Humm ..

Battery should not be an issue as battery life is @ 5 years .
Reset bios to defaults ?

[INDENT][INDENT]where there is a will ->
[/INDENT][/INDENT]

---

### Post by steven-misshula on 2015-01-29
Hi Bashing Om,

so...can't seem to get the pen drive running but can boot it from an install CD/DVD.

thoughts..?

I tried installing, but I get error code 1

Steve

---

### Post by Bashing-om on 2015-01-29
steven-misshula; Humm ...
pendrive failed ?

Can you see what is on the pen drive from the liveDVD ?
Boot the liveDVD in "try ubuntu mode" to terminal;
what results:
```

sudo fdisk -lu
sudo parted -l
df -h

```

[INDENT][INDENT]so a tale is told
[/INDENT][/INDENT]

---

### Post by steven-misshula on 2015-01-30
Hi - 

> ubuntu@ubuntu:~$ sudo fdisk -lu

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x0005aa47

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1            2048   968564735   484281344   83  Linux
/dev/sda2       968566782   976771071     4102145    5  Extended
Partition 2 does not start on physical sector boundary.
/dev/sda5       968566784   976771071     4102144   82  Linux swap / Solaris

Disk /dev/sdb: 8166 MB, 8166703104 bytes
224 heads, 63 sectors/track, 1130 cylinders, total 15950592 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000423ab

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *          56    15950591     7975268    c  W95 FAT32 (LBA)
ubuntu@ubuntu:~$ 



> ubuntu@ubuntu:~$ sudo parted -l
Model: ATA TOSHIBA MQ01ABD0 (scsi)
Disk /dev/sda: 500GB
Sector size (logical/physical): 512B/4096B
Partition Table: msdos

Number  Start   End    Size    Type      File system     Flags
 1      1049kB  496GB  496GB   primary   ext4
 2      496GB   500GB  4201MB  extended
 5      496GB   500GB  4201MB  logical   linux-swap(v1)


Model: PNY USB 2.0 FD (scsi)
Disk /dev/sdb: 8167MB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type     File system  Flags
 1      28.7kB  8167MB  8167MB  primary  fat32        boot, lba


Warning: Unable to open /dev/sr0 read-write (Read-only file system).  /dev/sr0
has been opened read-only.
Error: Can't have a partition outside the disk!                           

ubuntu@ubuntu:~$ 



> ubuntu@ubuntu:~$ df -h
Filesystem      Size  Used Avail Use% Mounted on
/cow            2.0G   68M  1.9G   4% /
udev            2.0G  4.0K  2.0G   1% /dev
tmpfs           396M  1.1M  394M   1% /run
/dev/sr0        987M  987M     0 100% /cdrom
/dev/loop0      952M  952M     0 100% /rofs
none            4.0K     0  4.0K   0% /sys/fs/cgroup
tmpfs           2.0G   16K  2.0G   1% /tmp
none            5.0M  4.0K  5.0M   1% /run/lock
none            2.0G   76K  2.0G   1% /run/shm
none            100M   52K  100M   1% /run/user
/dev/sdb1       7.6G  2.0G  5.7G  26% /media/ubuntu/USB20FD

ubuntu@ubuntu:~$ 


From File system vew:

> 
/media/ubuntu/USB20FD/boot
/media/ubuntu/USB20FD/casper
/media/ubuntu/USB20FD/dists
/media/ubuntu/USB20FD/install
/media/ubuntu/USB20FD/pics
/media/ubuntu/USB20FD/pool
/media/ubuntu/USB20FD/preseed
/media/ubuntu/USB20FD/syslinux
/media/ubuntu/USB20FD/autorun.inf
/media/ubuntu/USB20FD/casper-rw
/media/ubuntu/USB20FD/ldlinux.sys
/media/ubuntu/USB20FD/md5sum.txt
/media/ubuntu/USB20FD/README.diskdefines
/media/ubuntu/USB20FD/wubi.exe


forgot to mention - the file system view is a view of the pendrive.

also, if the hardrive needs to be removed at some point and played with from a working machine, I think i can do that, as I have cables.

Thanks.
steve

---

### Post by Bashing-om on 2015-01-31
steven-misshula; Morning: 

OK, that tells us that the file systems(s) are still there.
We continue to work toward verifying the file system on the hard drive is intact ( maybe a bad partition table, maybe the boot code in sector 0 is corrupt).

As the install is release 14.04 we must have a liveDVD(USB) of that release ; in order to effect any repairs.

a) Have you now burned a DVD of the 14.04 release ?

b) Are we working now to get the USB pen drive in a bootable state ? So we can work from the pen drive to effect the repair of the install on the hard drive ?

Remember, we must have the install ( sda1) in an un-mounted state to work on that file structure . And mount it as needed to effect those repairs.

Keep things simple
[INDENT][INDENT][INDENT]one step at a time
[/INDENT][/INDENT][/INDENT]

---

### Post by steven-misshula on 2015-01-31
Oh Wise One:

The dvd is 14.04 and is bootable...that is what I used to get the machine started.

I'm not sure what the issue is with the pendrive...I will try again.   It seems to have the correct files/folders though, no?  I will try again from "pendrivelinux.com"  unless you have another suggestion.

> 
Remember, we must have the install ( sda1) in an un-mounted state to  work on that file structure . And mount it as needed to effect those  repairs.

   -- this is above my level, don't quite get it...but willing to learn under your tutelage.

Ok -- new view of files on pendrive (done from "startup disk creator":

> /media/estelle/USB20FD/boot
/media/estelle/USB20FD/casper
/media/estelle/USB20FD/dists
/media/estelle/USB20FD/install
/media/estelle/USB20FD/pics
/media/estelle/USB20FD/pool
/media/estelle/USB20FD/preseed
/media/estelle/USB20FD/syslinux
/media/estelle/USB20FD/autorun.inf
/media/estelle/USB20FD/casper-rw
/media/estelle/USB20FD/ldlinux.sys
/media/estelle/USB20FD/md5sum.txt
/media/estelle/USB20FD/README.diskdefines
/media/estelle/USB20FD/wubi.exe

---

### Post by Bashing-om on 2015-01-31
steven-misshula; Yeah ;

The files are present on the pen drive. If it does not boot :
a) the machine may not support booting from USB IF it is an older generation machine
b) the boot code is corrupt on the pend drive, -> reburn the .iso to the pen drive.

As to the current install situation.

Boot the liveDVD in "try ubuntu" mode to the desk top. key combo ctl+alt+t to gain a terminal:
In this terminal execute terminal commands: _ and nothing nothing nothing else, so only this terminal is in an active state.
```

sudo e2fsck -C0 -p -f -v /dev/sda1

```
Wait for the command to complete and return to a prompt.

Ok ya get some errors, next in that terminal try:
```

sudo e2fsck -f -y -v /dev/sda1

```
Copy and paste any errors the tool reports.

If none reboot and see if you can now boot into the install ...

Else, we go deeper .

[INDENT][INDENT]ain't no big deal, yet
[/INDENT][/INDENT]

---

### Post by steven-misshula on 2015-01-31
WOW!  So, not sure what happened, but this time when I went to boot up, i now have access to F2 & F12 (i.e. boot loader menu)!  

That said, from the CD with the pendrive stuck in the side of my machine like a bull in the ring:

> 
ubuntu@ubuntu:~$ sudo e2fsck -C0 -p -f -v /dev/sda1
Error reading block 788 (Attempt to read block from filesystem resulted in short read).  

/dev/sda1: UNEXPECTED INCONSISTENCY; RUN fsck MANUALLY.
    (i.e., without -a or -p options)
ubuntu@ubuntu:~$ 



and from the second command:

> ubuntu@ubuntu:~$ sudo e2fsck -f -y -v /dev/sda1
e2fsck 1.42.9 (4-Feb-2014)
Pass 1: Checking inodes, blocks, and sizes
Error reading block 788 (Attempt to read block from filesystem resulted in short read).  Ignore error? yes

Force rewrite? yes

Inode 7, i_blocks is 143288, should be 143152.  Fix? yes

Pass 2: Checking directory structure
Pass 3: Checking directory connectivity
Pass 4: Checking reference counts
Pass 5: Checking group summary information

/dev/sda1: ***** FILE SYSTEM WAS MODIFIED *****

       13681 inodes used (0.05%, out of 30269440)
           4 non-contiguous files (0.0%)
           7 non-contiguous directories (0.1%)
             # of inodes with ind/dind/tind blocks: 0/0/0
             Extent depth histogram: 12088
     2070318 blocks used (1.71%, out of 121070336)
           0 bad blocks
           1 large file

       10231 regular files
        1706 directories
          57 character device files
          25 block device files
           0 fifos
           0 links
        1653 symbolic links (1503 fast symbolic links)
           0 sockets
------------
       13672 files
ubuntu@ubuntu:~$ 


Exercising patience and waiting for your next move.

---

### Post by Bashing-om on 2015-01-31
steven-misshula; Well !

Looks promising ...
reboot and lets see what is  ->

[INDENT][INDENT]it could happen
[/INDENT][/INDENT]

---

### Post by mörgæs on 2015-01-31
steven-misshula, please use CODE and not QUOTE tags for terminal output.

---

### Post by steven-misshula on 2015-02-01
ok -- didn't boot by itself, but I can do "try Ubuntu" with the USB.....took a while to come up, but its here!

Should I try an install...?

Steve

sorry 'bout that....couldn't figure it out...I think I'm good now...

---

### Post by Bashing-om on 2015-02-01
steven-misshula; Well, well ...

When you reset the boot priority in bios to the hard drive as 1st priority, do you now boot up ?

I am a simple person, and work hard to keep things simple -> one item at a time; presently working the install on the hard drive.

[INDENT][INDENT]which way did he go, George
[/INDENT][/INDENT]

---

### Post by steven-misshula on 2015-02-01
So when i boot without the USB, it gets hung up.  I took a picture of the screen (i can email it to you i guess..)

the last three lines of that black screen are the MAC Address, GUID and then...

[CODE]
PXE-E53: No boot filename received
PXE-M0F: Exiting PXE ROM
[CODE]

---

### Post by Bashing-om on 2015-02-01
steven-misshula; OK ....

If you boot up fine to the install on sda1 with the USB pen drive inserted, then we know that grub needs to be installed to the MBR of sda:
From the liveDVD of release 14.04; "try ubuntu" mode, execute terminal commands:
```

sudo mount /dev/sda1 /mnt
sudo grub-install --boot-directory=/mnt /dev/sda
sudo umount /mnt

```

reset the boot priority in bios to boot from the hard drive.
Boot the install and now in the install execute terminal command:
```

sudo update-grub

```

Once more reboot to verify the effect.

[INDENT][INDENT][INDENT]all finer than a frog's hair
[/INDENT][/INDENT][/INDENT]

---

### Post by steven-misshula on 2015-02-01
> If you boot up fine to the install on sda1 with the USB pen drive  inserted, then we know that grub needs to be installed to the MBR of  sda:
From the liveDVD of release 14.04; "try ubuntu" mode, execute terminal commands:
 	Code:
 	sudo mount /dev/sda1 /mnt
sudo grub-install --boot-directory=/mnt /dev/sda
sudo umount /mnt 


--did that, told me no errors.

> 
reset the boot priority in bios to boot from the hard drive.
Boot the install and now in the install execute terminal command:
 	Code:

 	sudo update-grub 


did that -- got me back to:

[code]
PXE-E53: No boot filename received
PXE-M0F: Exiting PXE ROM
[code]

but instead of getting hung up indefinitely, I now have a, "GNU GRUB version2.02~beta2-9ubuntu1" screen with a grub> prompt.

If I understood your 2nd direction in post #47, I was supposed to have the computer set to boot from the hard drive, with no USB nor Live CD, correct? (that is what i did).  So, was unable to execute command:

[code]
sudo update-grub
[code]

Thanks again.... exercising patience..

---

### Post by Bashing-om on 2015-02-01
steven-misshula; not all bad;

Your bios can not find grub's boot code on the hard drive and is trying to boot to a network through your ethernet card, huh ? Why ?
Let's look and see a possibility of that why:

Maybe:
In your BIOS, look in the boot options and take the "other devices" or "other" out of the boot sequence. Also check to see if boot from LAN is enabled. If it is, disable it. PXE is a protocol that will enable you to boot from a network drive or server. When it says that it failed, it is because it could not find an OS on the "network".

else, we look and see what grub is up to:
boot the liveDVD to terminal:
execute:
```

sudo mkdir /mnt/test
sudo mount /dev/sda1 /mnt/test
cat /mnt/test/etc/default/grub
sudo umount /mnt/test

```
Post back the output of the cat command.

[INDENT][INDENT]gotta be a cause
[/INDENT][/INDENT]

---

### Post by steven-misshula on 2015-02-02
Hi,
OK -- so I went into boot menu and could not seem to find a way to disable LAN.  So, I put the LAN option at the bottom and Hard Drive at the top.  That yielded nothing great.  I wound up at the grub> prompt.....but without the hang time.  

So, then I switched to the DVD and the terminal window.  I got the following:

```

ubuntu@ubuntu:~$ sudo mkdir /mnt/test
ubuntu@ubuntu:~$ sudo mount /dev/sda1 /mnt/test
ubuntu@ubuntu:~$ cat /mnt/test/etc/default/grub
# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.
# For full documentation of the options in this file, see:
#   info -f grub -n 'Simple configuration'

GRUB_DEFAULT=0
GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""

# Uncomment to enable BadRAM filtering, modify to suit your needs
# This works with Linux (no patch required) and with any kernel that obtains
# the memory map information from GRUB (GNU Mach, kernel of FreeBSD ...)
#GRUB_BADRAM="0x01234567,0xfefefefe,0x89abcdef,0xefefefef"

# Uncomment to disable graphical terminal (grub-pc only)
#GRUB_TERMINAL=console

# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
#GRUB_GFXMODE=640x480

# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID=true

# Uncomment to disable generation of recovery mode menu entries
#GRUB_DISABLE_RECOVERY="true"

# Uncomment to get a beep at grub start
#GRUB_INIT_TUNE="480 440 1"
ubuntu@ubuntu:~$ sudo umount /mnt/test
ubuntu@ubuntu:~$ 



```

---

### Post by Bashing-om on 2015-02-02
steven-misshula; Sheessshhh;

Grub file looks do-able too:
OK, Try this:
Boot the install to that grub boot menu, 'c' key for (C)ommand line interface.
Execute:
```

linux (hd0,msdos1)/vmlinuz root=/dev/sda1 ro
initrd (hd0,msdos1)/initrd.img
boot

```

Now, IF you do boot to the install proper, log in and now execute:
```

sudo update-grub

```

advise of these results. ->

[INDENT][INDENT][INDENT]maybe yes
[INDENT][INDENT][INDENT]maybe not so yes
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by steven-misshula on 2015-02-02
Grrr...some set backs.

1. Somehow, lost the F2 & F12 option during boot up
2. got to grub menu, but only limited commands, so "c" key gave me an error, "could not be found"

Thoughts...?

I can go back to post #47 and see if that restores the F1 /F12 options...

---

### Post by Bashing-om on 2015-02-03
steven-misshula; Yuk .
This:
> 
1. Somehow, lost the F2 & F12 option during boot up

Is a function of bios, and has nothing to do with the operating system.
bios hands off to grub what the condition of the hardware is, and grub loads the boot code (according to what is set in bios) and  hands off to the kernel to start the system
I do make the suggestion that in bios you reset "defaults". If there continues to be a problem booting to bios set up, time to clean the machine. I have seen many cases of updating the bios to the current version resolves may issues. BUT that is a means of last resort. Messing about with bios is risky risky business.

If grub still will not load - once bios is under control - , we get the more drastic, and CHange Root into the install from that liveDVD and re-write the boot codes in that install.

We do nothing to the operating system at large until you control bios. (remember, bios == Basic Input Output System )

[INDENT][INDENT]all in the process
[/INDENT][/INDENT]

---

### Post by steven-misshula on 2015-02-06
OK - somehow I finally got to grub>

Which got me the following when I attempted your grub> commands:

1. ```

linux (hd0,msdos1)/vmlinuz root=/dev/sda1 ro

```

Gets me:

```

error: attempt to read of write outside of disk 'hd0'

```

When I attempt the "initrd" it just rebooted.

---

### Post by Bashing-om on 2015-02-06
steven-misshula; Humm ...

Let's do the numbers  " error: attempt to read of write outside of disk 'hd0' " see what the possible reason is:

Boot the liveDVD and post back:
```

sudo fdisk -lu
sudo parted -l

```

[INDENT][INDENT]I hate when that happens
[/INDENT][/INDENT]

---

### Post by steven-misshula on 2015-02-07
I feel like I owe you tuition at this point....

OK
```

ubuntu@ubuntu:~$ sudo fdisk -lu

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x000c0632

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048   968564735   484281344   83  Linux
/dev/sda2       968566782   976771071     4102145    5  Extended
Partition 2 does not start on physical sector boundary.
/dev/sda5       968566784   976771071     4102144   82  Linux swap / Solaris
ubuntu@ubuntu:~$ 


```

And on the second command:
```

ubuntu@ubuntu:~$ sudo parted -l
Model: ATA TOSHIBA MQ01ABD0 (scsi)
Disk /dev/sda: 500GB
Sector size (logical/physical): 512B/4096B
Partition Table: msdos

Number  Start   End    Size    Type      File system     Flags
 1      1049kB  496GB  496GB   primary   ext4            boot
 2      496GB   500GB  4201MB  extended
 5      496GB   500GB  4201MB  logical   linux-swap(v1)


Warning: Unable to open /dev/sr0 read-write (Read-only file system).  /dev/sr0
has been opened read-only.
Error: Can't have a partition outside the disk!                           

ubuntu@ubuntu:~$ 

```

---

### Post by Bashing-om on 2015-02-07
steven-misshula; Hummmm ...

We have :
> 
error: attempt to read of write outside of disk 'hd0'
&&
Partition 2 does not start on physical sector boundary.

Where the start of the partition is sector number 968566782.
We do the arithmetic:
968566782 divided by 8 = 12107084 ; a whole number, so that is good;
I do not see the problem that 'fdisk' sees.

Let me do some research and homework, see if I can come up with a means to find out the why of the read/write outside of the sector constraints exists. 

When we do not know
[INDENT][INDENT][INDENT]we are preparing to learn something
[/INDENT][/INDENT][/INDENT]

---

### Post by steven-misshula on 2015-02-07
Is this relevant:

[http://askubuntu.com/questions/530343/adding-another-ubuntu](http://askubuntu.com/questions/530343/adding-another-ubuntu)  ??

or this:

[http://superuser.com/questions/863073/ubuntu-14-04-doesnt-see-my-ssd-drive](http://superuser.com/questions/863073/ubuntu-14-04-doesnt-see-my-ssd-drive) ??

---

### Post by Bashing-om on 2015-02-07
steven-misshula; Well;

The 1st link is relevant IF you are going to (RE-)install ubuntu, and you want to control the partitioning.
The 2nd link is relevant in that it is always a good thing to read the logs, if for no other reason than generally just to see. I do make it a habit to scan the logs occasionally - just to see if there are anythings changed or something that 'should' have my attention. As to adding a boot parameter: you were booting, no hardware was changed, should not require a boot parameter alteration.

Refocus of our attention: Booting
How far do you get when you try and boot now ?
Do you boot and get a grub prompt still ?
IF at that 'grub >' prompt what results from the commands:
```

ls
ls (hd0,msdos1)
search -f /vmlinuz
search -f /sbin/init

```
and we try and relate these outputs to what the partitions are and the files they contain.

Tell grub what to do,
tell the kernel where the files are
[INDENT][INDENT]this sucker should boot !
[/INDENT][/INDENT]

---

### Post by steven-misshula on 2015-02-07
When I booted, as of last, it just hangs with the Toshiba logo....And my f2 / f12 options.   if I press f1 I get grub....

I'm out right now but will try those commands Around 10 EST.

THANKS

OK - here we go:

```

grub> ls
(hd0) (hd0,msdos5) (hd0,msdos1)

grub> ls (hd0,msdos1)
           Partition hdo, msdos1: Filesystem type ext* - Last modification time 2015-02-07 12:58:48 Saturday, UUID 4e1dd776-c7cb-46ae-87cb-482b679e9654 - Partision start at 1024KiB - Total size 484281344Kib

grub> search -f /vmlinuz
hd0, msdos1

grub> search - f /sbin/init
hd0, msdos1


```

---

### Post by Bashing-om on 2015-02-08
steven-misshula; Sheesshh ..

Those outputs indicate that grub is in fact installed, grub knows where the config files are. We should be able to boot.
So why not ?

This machine, it is UEFI (Unified Extensible Firmware Interface) capable, such that in the firmware you must set to boot 'ccsm' ( as ubuntu is installed MBR and the partitioning is the legacy 'msdos') ? If this machine is UEFI it would explain away a lot of the difficulties booting the legacy MBR ! 
BIOS uses MBR for initial boot code on the hard drive. And each hard drive has only one MBR, so only one system can be default boot.
UEFI uses an efi partition for initial boot code - which we do not have - and each system installed has a separate folder with its boot files. Somewhat like having many MBR's in old BIOS configuration. And from UEFI menu you can choose to boot any system (if not one of those where vendor modifies it to only boot Windows).
&&
Some systems have UEFI only, UEFI or BIOS, or BIOS only as boot option settings in UEFI. [color=red]If secure boot is on, then it will only boot in UEFI mode.[/color]

Still holding in the back of my mind that there might exist hardware problems at the 0th sector level. However, a lot depends on the booting firmware.

[INDENT][INDENT]seek to understand
[/INDENT][/INDENT]

---

### Post by steven-misshula on 2015-02-08
Any steps, or should we seek to wipe the drive...?(I'm ok with that....I managed to get my work files off the drive....)

Exercising patience...

(also, just wanted to mention again -- things were working fine until I installed the update of January 16th around 7:30 pm).  <sigh>

---

### Post by Bashing-om on 2015-02-08
steven-misshula; Well, Like this:

Your call. There is always that nuclear solution to (RE-)install. However, doing so we learn nothing.
To continue to find a fix for this install, aid my thought process -> is this a UEFI system ?

And yeah, an update when 3rd party software is installed often times break the system. ubuntu has no control over what results when some excellent coder works up outstanding code that works for a particular release of ubuntu software, then that base software changes in the update process and that 3rd party software is left high and dry. OR that 3rd party software tries to interact, and can not -> system crash !

Before we go back to the booting issue, look and see what 3rd party stuff might be a factor ?
as before mount the install partition from the liveDVD (/mnt/test);
```

cat -n /mnt/test/etc/apt/sources.list
tail -v -n +1 /mnt/test/etc/apt/sources.list.d/*

```
To get an idea of what the system is fetching .

YeaH, good thing to keep in mind:
> 
(also, just wanted to mention again -- things were working fine until I installed the update of January 16th around 7:30 pm). <sigh>

All we know is that something broke, somewhere, and we are trying to find out the why/where and how it affects grub. (hummmmm ... graphics driver ??)

I do learn the most
[INDENT][INDENT][INDENT]when I break it the hardest ( been there, done that, many many times)
[/INDENT][/INDENT][/INDENT]

---

### Post by steven-misshula on 2015-02-08
Well....

```


ubuntu@ubuntu:~$ cat -n /mnt/test/etc/apt/sources.list
cat: /mnt/test/etc/apt/sources.list: No such file or directory

ubuntu@ubuntu:~$ tail -v -n +1 /mnt/test/etc/apt/sources.list.d/*
tail: cannot open &#8216;/mnt/test/etc/apt/sources.list.d/*&#8217; for reading: No such file or directory

ubuntu@ubuntu:~$ 

```

---

### Post by Bashing-om on 2015-02-08
steven-misshula; Hey ;

That output looks like this:
> 
as before mount the install partition from the liveDVD (/mnt/test);

was not done.
```

sudo mkdir /mnt/test
sudo mount /dev/sda1 /mnt/test

```
Now we should get the files on the install:
```

cat -n /mnt/test/etc/apt/sources.list
tail -v -n +1 /mnt/test/etc/apt/sources.list.d/*

```

I betcha, 
[INDENT][INDENT]I betcha
[/INDENT][/INDENT]

---

### Post by steven-misshula on 2015-02-08
hmmm....

```


ubuntu@ubuntu:~$ sudo mkdir /mnt/test
mkdir: cannot create directory ‘/mnt/test’: File exists

ubuntu@ubuntu:~$ sudo mount /dev/sda1 /mnt/test
mount: /dev/sda1 already mounted or /mnt/test busy
mount: according to mtab, /dev/sda1 is already mounted on /mnt/test

ubuntu@ubuntu:~$ cat -n /mnt/test/etc/apt/sources.list
     1    #deb cdrom:[Ubuntu 14.04.1 LTS _Trusty Tahr_ - Release i386 (20140722.2)]/ trusty main restricted
     2    
     3    # See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
     4    # newer versions of the distribution.
     5    deb http://us.archive.ubuntu.com/ubuntu/ trusty main restricted
     6    deb-src http://us.archive.ubuntu.com/ubuntu/ trusty main restricted
     7    
     8    ## Major bug fix updates produced after the final release of the
     9    ## distribution.
    10    deb http://us.archive.ubuntu.com/ubuntu/ trusty-updates main restricted
    11    deb-src http://us.archive.ubuntu.com/ubuntu/ trusty-updates main restricted
    12    
    13    ## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
    14    ## team. Also, please note that software in universe WILL NOT receive any
    15    ## review or updates from the Ubuntu security team.
    16    deb http://us.archive.ubuntu.com/ubuntu/ trusty universe
    17    deb-src http://us.archive.ubuntu.com/ubuntu/ trusty universe
    18    deb http://us.archive.ubuntu.com/ubuntu/ trusty-updates universe
    19    deb-src http://us.archive.ubuntu.com/ubuntu/ trusty-updates universe
    20    
    21    ## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
    22    ## team, and may not be under a free licence. Please satisfy yourself as to 
    23    ## your rights to use the software. Also, please note that software in 
    24    ## multiverse WILL NOT receive any review or updates from the Ubuntu
    25    ## security team.
    26    deb http://us.archive.ubuntu.com/ubuntu/ trusty multiverse
    27    deb-src http://us.archive.ubuntu.com/ubuntu/ trusty multiverse
    28    deb http://us.archive.ubuntu.com/ubuntu/ trusty-updates multiverse
    29    deb-src http://us.archive.ubuntu.com/ubuntu/ trusty-updates multiverse
    30    
    31    ## N.B. software from this repository may not have been tested as
    32    ## extensively as that contained in the main release, although it includes
    33    ## newer versions of some applications which may provide useful features.
    34    ## Also, please note that software in backports WILL NOT receive any review
    35    ## or updates from the Ubuntu security team.
    36    deb http://us.archive.ubuntu.com/ubuntu/ trusty-backports main restricted universe multiverse
    37    deb-src http://us.archive.ubuntu.com/ubuntu/ trusty-backports main restricted universe multiverse
    38    
    39    deb http://security.ubuntu.com/ubuntu trusty-security main restricted
    40    deb-src http://security.ubuntu.com/ubuntu trusty-security main restricted
    41    deb http://security.ubuntu.com/ubuntu trusty-security universe
    42    deb-src http://security.ubuntu.com/ubuntu trusty-security universe
    43    deb http://security.ubuntu.com/ubuntu trusty-security multiverse
    44    deb-src http://security.ubuntu.com/ubuntu trusty-security multiverse
    45    
    46    ## Uncomment the following two lines to add software from Canonical's
    47    ## 'partner' repository.
    48    ## This software is not part of Ubuntu, but is offered by Canonical and the
    49    ## respective vendors as a service to Ubuntu users.
    50    # deb http://archive.canonical.com/ubuntu trusty partner
    51    # deb-src http://archive.canonical.com/ubuntu trusty partner
    52    
    53    ## This software is not part of Ubuntu, but is offered by third-party
    54    ## developers who want to ship their latest software.
    55    deb http://extras.ubuntu.com/ubuntu trusty main
    56    deb-src http://extras.ubuntu.com/ubuntu trusty main
ubuntu@ubuntu:~$ tail -v -n +1 /mnt/test/etc/apt/sources.list.d/*
tail: cannot open ‘/mnt/test/etc/apt/sources.list.d/*’ for reading: No such file or directory

ubuntu@ubuntu:~$ 


```

back in 10-15 mins.

---

### Post by Bashing-om on 2015-02-08
steven-misshula; Well ??

I see nothing in the source.list file that could possibly cause an update issue.
Surprised at no return form the tail request .
what returns:
```

ls -al /mnt/test/etc/apt/sources.list.d

```

Is this machine UEFI ?

[INDENT][INDENT]not making much sense, yet
[INDENT][INDENT][INDENT]why it no boot
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by steven-misshula on 2015-02-08
OK:

```

ubuntu@ubuntu:~$ ls -al /mnt/test/etc/apt/sources.list.d
total 8
drwxr-xr-x 2 root root 4096 Apr 10  2014 .
drwxr-xr-x 6 root root 4096 Feb  7 12:58 ..
ubuntu@ubuntu:~$ 


```

> Is this machine UEFI ?

do not know...

also - just went into the DISK utility and it says - under Assesment   [COLOR=#ff0000]**DISK is likely to fail soon**[/COLOR]

---

### Post by Bashing-om on 2015-02-08
steven-misshula; OK;

3rd party software IS NOT an issue, you have none installed.
BUT yeah,
> 
DISK utility and it says - under Assesment DISK is likely to fail soon

Is cause to put the brakes on hard and double check:
I do not recall if the tool is installed by default, so:
From the liveDVD
```

sudo apt-get install smartmontools
sudo smartctl --all /dev/sda

```
Maybe then 'see' what is going on.

Hardware failure can be 
[INDENT][INDENT]a horrible thing -> nothing last forever
[/INDENT][/INDENT]

---

### Post by steven-misshula on 2015-02-08
```

ubuntu@ubuntu:~$ sudo apt-get install smartmontools
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  bsd-mailx postfix
Suggested packages:
  procmail postfix-mysql postfix-pgsql postfix-ldap postfix-pcre sasl2-bin
  dovecot-common postfix-cdb postfix-doc gsmartcontrol smart-notifier
Recommended packages:
  mailx mailutils
The following NEW packages will be installed:
  bsd-mailx postfix smartmontools
0 upgraded, 3 newly installed, 0 to remove and 0 not upgraded.
Need to get 1,541 kB of archives.
After this operation, 4,984 kB of additional disk space will be used.
Do you want to continue? [Y/n] y
Abort.
ubuntu@ubuntu:~$ sudo apt-get install smartontools
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package smartontools
ubuntu@ubuntu:~$ sudo smartctl --all /dev/sda
sudo: smartctl: command not found
ubuntu@ubuntu:~$ 



```

---

### Post by Bashing-om on 2015-02-08
steven-misshula; Sheeessshhh;

That does not compute:
> 
sysop@1404mini:~$ apt-cache show smartmontools
Filename: pool/main/s/smartmontools/smartmontools_6.2+svn3841-1.2_amd64.deb

That tool is there in the 'main' repository !
> 
sysop@1404mini:~$ sudo apt-get install smartmontools
[sudo] password for sysop: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
smartmontools is already the newest version.


The 'abortion' does not indicate, but as I can come up with no other rationale, do you have internet connectivity ?
```

ping -c3 ubuntu.com

```

this time,
[INDENT][INDENT][INDENT]I really do not know
[/INDENT][/INDENT][/INDENT]

your second attempt " install smartontools " misspelled .

---

### Post by steven-misshula on 2015-02-08
hmmm... must have internet connectivity, cuz I am posting from the FUBAR machine.

OK tried this again:
```

sudo apt-get install smartmontools

```


and got:

```

 &#9484;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9508; Postfix Configuration &#9500;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9488;   
  &#9474;                                                                         &#9474;   
  &#9474; Please select the mail server configuration type that best meets your       
  &#9474; needs.                                                                      
  &#9474;                                                                             
  &#9474;  No configuration:                                                          
  &#9474;   Should be chosen to leave the current configuration unchanged.            
  &#9474;  Internet site:                                                             
  &#9474;   Mail is sent and received directly using SMTP.                            
  &#9474;  Internet with smarthost:                                                   
  &#9474;   Mail is received directly using SMTP or by running a utility such         
  &#9474;   as fetchmail. Outgoing mail is sent using a smarthost.                    
  &#9474;  Satellite system:                                                          
  &#9474;   All mail is sent to another machine, called a 'smarthost', for            
  &#9474; delivery.                                                                   
  &#9474;  Local only:                                                                
  &#9474;                                                                             
  &#9474;                                 <Ok>                                        
  &#9474;                                          



```

---

### Post by steven-misshula on 2015-02-08
the terminal output disappeared into that, "Postfix Configuration"....and now, nothing else is happening in the terminal

---

### Post by steven-misshula on 2015-02-08
and in a new terminal - i get the following on the second command:

```

ubuntu@ubuntu:~$ sudo smartctl --all /dev/sda
sudo: smartctl: command not found
ubuntu@ubuntu:~$ ^C
ubuntu@ubuntu:~$ 



```

---

### Post by steven-misshula on 2015-02-08
oh...crab cakes... got it now...to highlight the ok...

---

### Post by Bashing-om on 2015-02-08
steven-misshula; Beats me 

Where that output originates .
You are on the liveDVD, yes ?

Reboot the liveDVD, and try again:
```

ping -c3 ubuntu.com

```
> 
--- ubuntu.com ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 2002ms
rtt min/avg/max/mdev = 134.021/134.925/136.110/0.875 ms
sysop@1404mini:~$


If that ping is positive. try again:
```

sudo apt-get install smartmontools

```

[INDENT][INDENT]sometimes I wonder
[INDENT][INDENT][INDENT]othertimes I just do not know
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by steven-misshula on 2015-02-08
OK -- and now:

```


ubuntu@ubuntu:~$ sudo apt-get install smartmontools
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  bsd-mailx postfix
Suggested packages:
  procmail postfix-mysql postfix-pgsql postfix-ldap postfix-pcre sasl2-bin
  dovecot-common postfix-cdb postfix-doc gsmartcontrol smart-notifier
Recommended packages:
  mailx mailutils
The following NEW packages will be installed:
  bsd-mailx postfix smartmontools
0 upgraded, 3 newly installed, 0 to remove and 0 not upgraded.
Need to get 1,541 kB of archives.
After this operation, 4,984 kB of additional disk space will be used.
Do you want to continue? [Y/n] y
Get:1 http://archive.ubuntu.com/ubuntu/ trusty/main postfix i386 2.11.0-1 [1,047 kB]
Get:2 http://archive.ubuntu.com/ubuntu/ trusty/main bsd-mailx i386 8.1.2-0.20131005cvs-1 [64.6 kB]
Get:3 http://archive.ubuntu.com/ubuntu/ trusty/main smartmontools i386 6.2+svn3841-1.2 [429 kB]
Fetched 1,541 kB in 2s (661 kB/s)  
Preconfiguring packages ...
Selecting previously unselected package postfix.
(Reading database ... 174162 files and directories currently installed.)
Preparing to unpack .../postfix_2.11.0-1_i386.deb ...
Unpacking postfix (2.11.0-1) ...
Selecting previously unselected package bsd-mailx.
Preparing to unpack .../bsd-mailx_8.1.2-0.20131005cvs-1_i386.deb ...
Unpacking bsd-mailx (8.1.2-0.20131005cvs-1) ...
Selecting previously unselected package smartmontools.
Preparing to unpack .../smartmontools_6.2+svn3841-1.2_i386.deb ...
Unpacking smartmontools (6.2+svn3841-1.2) ...
Processing triggers for man-db (2.6.7.1-1) ...
Processing triggers for ureadahead (0.100.0-16) ...
Processing triggers for ufw (0.34~rc-0ubuntu2) ...
Setting up postfix (2.11.0-1) ...
Adding group `postfix' (GID 125) ...
Done.
Adding system user `postfix' (UID 116) ...
Adding new user `postfix' (UID 116) with group `postfix' ...
Not creating home directory `/var/spool/postfix'.
Creating /etc/postfix/dynamicmaps.cf
Adding tcp map entry to /etc/postfix/dynamicmaps.cf
Adding sqlite map entry to /etc/postfix/dynamicmaps.cf
Adding group `postdrop' (GID 126) ...
Done.
setting myhostname: ubuntu
setting alias maps
setting alias database
mailname is not a fully qualified domain name.  Not changing /etc/mailname.
setting destinations: ubuntu, localhost.localdomain, , localhost
setting relayhost: 
setting mynetworks: 127.0.0.0/8 [::ffff:127.0.0.0]/104 [::1]/128
setting mailbox_size_limit: 0
setting recipient_delimiter: +
setting inet_interfaces: all
/etc/aliases does not exist, creating it.
WARNING: /etc/aliases exists, but does not have a root alias.

Postfix is now set up with a default configuration.  If you need to make 
changes, edit
/etc/postfix/main.cf (and others) as needed.  To view Postfix configuration
values, see postconf(1).

After modifying main.cf, be sure to run '/etc/init.d/postfix reload'.

Running newaliases
 * Stopping Postfix Mail Transport Agent postfix                         [ OK ] 
 * Starting Postfix Mail Transport Agent postfix                         [ OK ] 
Setting up smartmontools (6.2+svn3841-1.2) ...
Processing triggers for ureadahead (0.100.0-16) ...
Processing triggers for ufw (0.34~rc-0ubuntu2) ...
Setting up bsd-mailx (8.1.2-0.20131005cvs-1) ...
update-alternatives: using /usr/bin/bsd-mailx to provide /usr/bin/mailx (mailx) in auto mode
Processing triggers for libc-bin (2.19-0ubuntu6) ...
ubuntu@ubuntu:~$ 


```

---

### Post by steven-misshula on 2015-02-08
And now second command:

```


ubuntu@ubuntu:~$ sudo smartctl --all /dev/sda
smartctl 6.2 2013-07-26 r3841 [i686-linux-3.13.0-32-generic] (local build)
Copyright (C) 2002-13, Bruce Allen, Christian Franke, www.smartmontools.org

=== START OF INFORMATION SECTION ===
Model Family:     Toshiba 2.5" HDD MQ01ABD...
Device Model:     TOSHIBA MQ01ABD050
Serial Number:    54UTTPO7T
LU WWN Device Id: 5 000039 581e099f7
Firmware Version: AX001A
User Capacity:    500,107,862,016 bytes [500 GB]
Sector Sizes:     512 bytes logical, 4096 bytes physical
Rotation Rate:    5400 rpm
Device is:        In smartctl database [for details use: -P show]
ATA Version is:   ATA8-ACS (minor revision not indicated)
SATA Version is:  SATA 2.6, 3.0 Gb/s (current: 1.5 Gb/s)
Local Time is:    Sun Feb  8 23:35:45 2015 UTC
SMART support is: Available - device has SMART capability.
SMART support is: Enabled

=== START OF READ SMART DATA SECTION ===
SMART overall-health self-assessment test result: FAILED!
Drive failure expected in less than 24 hours. SAVE ALL DATA.
See vendor-specific Attribute list for failed Attributes.

General SMART Values:
Offline data collection status:  (0x00)    Offline data collection activity
                    was never started.
                    Auto Offline Data Collection: Disabled.
Self-test execution status:      (   0)    The previous self-test routine completed
                    without error or no self-test has ever 
                    been run.
Total time to complete Offline 
data collection:         (  120) seconds.
Offline data collection
capabilities:              (0x5b) SMART execute Offline immediate.
                    Auto Offline data collection on/off support.
                    Suspend Offline collection upon new
                    command.
                    Offline surface scan supported.
                    Self-test supported.
                    No Conveyance Self-test supported.
                    Selective Self-test supported.
SMART capabilities:            (0x0003)    Saves SMART data before entering
                    power-saving mode.
                    Supports SMART auto save timer.
Error logging capability:        (0x01)    Error logging supported.
                    General Purpose Logging supported.
Short self-test routine 
recommended polling time:      (   2) minutes.
Extended self-test routine
recommended polling time:      ( 122) minutes.
SCT capabilities:            (0x003d)    SCT Status supported.
                    SCT Error Recovery Control supported.
                    SCT Feature Control supported.
                    SCT Data Table supported.

SMART Attributes Data Structure revision number: 16
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x000b   100   100   050    Pre-fail  Always       -       0
  2 Throughput_Performance  0x0005   100   100   050    Pre-fail  Offline      -       0
  3 Spin_Up_Time            0x0027   100   100   001    Pre-fail  Always       -       1047
  4 Start_Stop_Count        0x0032   100   100   000    Old_age   Always       -       661
  5 Reallocated_Sector_Ct   0x0033   032   032   050    Pre-fail  Always   FAILING_NOW 15872
  7 Seek_Error_Rate         0x000b   100   100   050    Pre-fail  Always       -       0
  8 Seek_Time_Performance   0x0005   100   100   050    Pre-fail  Offline      -       0
  9 Power_On_Hours          0x0032   099   099   000    Old_age   Always       -       720
 10 Spin_Retry_Count        0x0033   113   100   030    Pre-fail  Always       -       0
 12 Power_Cycle_Count       0x0032   100   100   000    Old_age   Always       -       390
191 G-Sense_Error_Rate      0x0032   100   100   000    Old_age   Always       -       7
192 Power-Off_Retract_Count 0x0032   100   100   000    Old_age   Always       -       10
193 Load_Cycle_Count        0x0032   100   100   000    Old_age   Always       -       8036
194 Temperature_Celsius     0x0022   100   100   000    Old_age   Always       -       34 (Min/Max 20/43)
196 Reallocated_Event_Count 0x0032   100   100   000    Old_age   Always       -       500
197 Current_Pending_Sector  0x0032   100   100   000    Old_age   Always       -       504
198 Offline_Uncorrectable   0x0030   100   100   000    Old_age   Offline      -       0
199 UDMA_CRC_Error_Count    0x0032   200   253   000    Old_age   Always       -       0
220 Disk_Shift              0x0002   100   100   000    Old_age   Always       -       0
222 Loaded_Hours            0x0032   099   099   000    Old_age   Always       -       443
223 Load_Retry_Count        0x0032   100   100   000    Old_age   Always       -       0
224 Load_Friction           0x0022   100   100   000    Old_age   Always       -       0
226 Load-in_Time            0x0026   100   100   000    Old_age   Always       -       261
240 Head_Flying_Hours       0x0001   100   100   001    Pre-fail  Offline      -       0

SMART Error Log Version: 1
ATA Error Count: 1441 (device log contains only the most recent five errors)
    CR = Command Register [HEX]
    FR = Features Register [HEX]
    SC = Sector Count Register [HEX]
    SN = Sector Number Register [HEX]
    CL = Cylinder Low Register [HEX]
    CH = Cylinder High Register [HEX]
    DH = Device/Head Register [HEX]
    DC = Device Command Register [HEX]
    ER = Error register [HEX]
    ST = Status register [HEX]
Powered_Up_Time is measured from power on, and printed as
DDd+hh:mm:SS.sss where DD=days, hh=hours, mm=minutes,
SS=sec, and sss=millisec. It "wraps" after 49.710 days.

Error 1441 occurred at disk power-on lifetime: 719 hours (29 days + 23 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  04 51 00 28 c8 80 e1  Error: ABRT at LBA = 0x0180c828 = 25217064

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  35 00 00 00 c5 80 e0 00      00:16:28.426  WRITE DMA EXT
  ef 10 02 00 00 00 a0 00      00:16:28.426  SET FEATURES [Enable SATA feature]
  27 00 00 00 00 00 e0 00      00:16:28.426  READ NATIVE MAX ADDRESS EXT [OBS-ACS-3]
  ec 00 00 00 00 00 a0 00      00:16:28.425  IDENTIFY DEVICE
  ef 03 45 00 00 00 a0 00      00:16:28.425  SET FEATURES [Set transfer mode]

Error 1440 occurred at disk power-on lifetime: 719 hours (29 days + 23 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  04 51 00 28 c8 80 e1  Error: ABRT at LBA = 0x0180c828 = 25217064

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  35 00 00 00 c5 80 e0 00      00:16:24.293  WRITE DMA EXT
  ef 10 02 00 00 00 a0 00      00:16:24.292  SET FEATURES [Enable SATA feature]
  27 00 00 00 00 00 e0 00      00:16:24.292  READ NATIVE MAX ADDRESS EXT [OBS-ACS-3]
  ec 00 00 00 00 00 a0 00      00:16:24.291  IDENTIFY DEVICE
  ef 03 45 00 00 00 a0 00      00:16:24.291  SET FEATURES [Set transfer mode]

Error 1439 occurred at disk power-on lifetime: 719 hours (29 days + 23 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  04 51 00 28 c8 80 e1  Error: ABRT at LBA = 0x0180c828 = 25217064

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  35 00 00 00 c5 80 e0 00      00:16:20.141  WRITE DMA EXT
  ef 90 03 00 00 00 a0 00      00:16:20.127  SET FEATURES [Disable SATA feature]
  ef 10 02 00 00 00 a0 00      00:16:20.127  SET FEATURES [Enable SATA feature]
  27 00 00 00 00 00 e0 00      00:16:20.126  READ NATIVE MAX ADDRESS EXT [OBS-ACS-3]
  ec 00 00 00 00 00 a0 00      00:16:20.126  IDENTIFY DEVICE

Error 1438 occurred at disk power-on lifetime: 719 hours (29 days + 23 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  04 51 00 28 c8 80 e1  Error: ABRT at LBA = 0x0180c828 = 25217064

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  35 00 00 00 c5 80 e0 00      00:16:15.292  WRITE DMA EXT
  ef 10 02 00 00 00 a0 00      00:16:15.292  SET FEATURES [Enable SATA feature]
  27 00 00 00 00 00 e0 00      00:16:15.292  READ NATIVE MAX ADDRESS EXT [OBS-ACS-3]
  ec 00 00 00 00 00 a0 00      00:16:15.291  IDENTIFY DEVICE
  ef 03 45 00 00 00 a0 00      00:16:15.291  SET FEATURES [Set transfer mode]

Error 1437 occurred at disk power-on lifetime: 719 hours (29 days + 23 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  04 51 00 28 c8 80 e1  Error: ABRT at LBA = 0x0180c828 = 25217064

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  35 00 00 00 c5 80 e0 00      00:16:11.315  WRITE DMA EXT
  ef 10 02 00 00 00 a0 00      00:16:11.314  SET FEATURES [Enable SATA feature]
  27 00 00 00 00 00 e0 00      00:16:11.314  READ NATIVE MAX ADDRESS EXT [OBS-ACS-3]
  ec 00 00 00 00 00 a0 00      00:16:11.313  IDENTIFY DEVICE
  ef 03 45 00 00 00 a0 00      00:16:11.313  SET FEATURES [Set transfer mode]

SMART Self-test log structure revision number 1
No self-tests have been logged.  [To run self-tests, use: smartctl -t]


SMART Selective self-test log data structure revision number 1
 SPAN  MIN_LBA  MAX_LBA  CURRENT_TEST_STATUS
    1        0        0  Not_testing
    2        0        0  Not_testing
    3        0        0  Not_testing
    4        0        0  Not_testing
    5        0        0  Not_testing
Selective self-test flags (0x0):
  After scanning selected spans, do NOT read-scan remainder of disk.
If Selective self-test is pending on power-up, resume after 0 minute delay.

ubuntu@ubuntu:~$ 




```

---

### Post by steven-misshula on 2015-02-08
i'm guessing based upon:

```

=== START OF READ SMART DATA SECTION ===
SMART overall-health self-assessment test result: FAILED!
Drive failure expected in less than 24 hours. SAVE ALL DATA.
See vendor-specific Attribute list for failed Attributes.
```

that my Jan 16 update and crash was coincidence....? no?

---

### Post by Bashing-om on 2015-02-08
steven-misshula; Yukkie Poo !!

After all this time and effort - beating a dead horse !
These tell the tale:
> 
SMART overall-health self-assessment test result: FAILED!

  5 Reallocated_Sector_Ct   0x0033   032   032   050    Pre-fail  Always   FAILING_NOW 15872

196 Reallocated_Event_Count 0x0032   100   100   000    Old_age   Always       -       500
197 Current_Pending_Sector  0x0032   100   100   000    Old_age   Always       -       504


That drive is toast. replace it.
[https://help.ubuntu.com/community/Smartmontools](https://help.ubuntu.com/community/Smartmontools)
[http://ubuntuforums.org/showthread.php?t=2192335](http://ubuntuforums.org/showthread.php?t=2192335) <-How to read output of smartctl

[INDENT][INDENT]sad but true
[/INDENT][/INDENT]

---

### Post by steven-misshula on 2015-02-08
good grief...

The thing is only 2.5 months old....grrrr....

Many thanks for all the help....  for whatever it is worth the failure happened immediately after the update.

Please don't consider it a waste of time...I did learn quite a bit from the back and forth.

Steve

---

### Post by Bashing-om on 2015-02-08
> **steven-misshula said:**
> good grief...

The thing is only 2.5 months old....grrrr....

Many thanks for all the help....  for whatever it is worth the failure happened immediately after the update.

Please don't consider it a waste of time...I did learn quite a bit from the back and forth.

Steve

Yeah, I had the same thought, the uptime and hours on that hard drive are not much !

RMA that drive .. at least let the OEM bear some of the brunt of this.

[INDENT][INDENT]I hate when this happens
[/INDENT][/INDENT]

---

