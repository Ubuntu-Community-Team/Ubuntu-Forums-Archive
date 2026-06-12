---
title: "dual boot XP and 7.10 on separate HDD's"
date: 2008-04-05
forum: Installation &amp; Upgrades
---

### Post by BobAngelFire on 2008-04-05
I have an install problem on a Dell Optiplex PC.  (I'm already running Gutsy on a laptop, so I'm not a complete beginner.)

The dell has two HDD: sda was intended to install Gutsy and sdb has XP already installed.  I  followed several posts for instruction on dual booting Gutsy and xp with two HDD.

Problem:  Although grub menu looks normal at startup and XP boots ok, Gutsy doesn't boot up at all.  I just see blinking cursor on a blank screen.  

I think the problem is related to partitioning of sda because:
* during installation from live CD, sda wasn't given as a choice on the Select Disk screen, only sdb was given.  So, I had to manually partition sda.  Maybe I made a mistake here.
* when I look at sda with xp's disk management tool, it detects sda OK and says it contains a 3.8 GB partition (the swap I tried to create) as Healthy (Unknown partition).  That tool also shows a second 70 GB partition on sda as Healthy (active).
* After seeing this problem, I started the install from the live CD again, and it still doesn't show sda as an option on the Select Disk screen.

Maybe I need to create or fix the swap partition on sda, but I'm not sure how to do that.

Or maybe I'm wrong about having a partition problem, because I noted this msg just before instal started: "Following partitions were formatted.  Partition #1 of sda as swap.  Partition #2 of sda as ext3."

Please help because I'd really like gutsy to run on my desktop as well as it runs on my laptop.

thanks

---

### Post by Pumalite on 2008-04-05
Boot your Live CD and post:
sudo fdisk -lu

---

### Post by BobAngelFire on 2008-04-05
Here is output from sudo fdisk -lu (without the Start, End, Blocks and ID columns)

Device        Boot           System
/dev/sda1                     Linux swap / Solaris
/dev/sda2     *               Linux

Any ideas on next step?

thanks very much

---

### Post by Pumalite on 2008-04-05
Where is your 2nd drive?
Copy and paste the entire output here.

---

### Post by BobAngelFire on 2008-04-05
Sorry for late response!

Here is fdisk output for 2nd disk which has Windows XP as OS:

Disk /dev/sdb: 160.0 GB, 160000000000 bytes
255 heads, 63 sectors/track, 19452 cylinders, total 312500000 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xd0f4738c

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1              63       80324       40131   de  Dell Utility
/dev/sdb2   *       80325   312480314   156199995    7  HPFS/NTFS

Thanks for continuing to look at my problem.

---

### Post by Pumalite on 2008-04-05
Do you see Grub? Which hard drive is first in the boot order in BIOS?
Windows likes to be in the drive that boots and in sda1

---

### Post by BobAngelFire on 2008-04-05
I do see Grub, and I have no problem using it to boot into XP, which is on sdb.

My bios boot sequence doesn't distinguish between my two SATA drives.  It only lists "Onboard SATA hard drive" after the floppy and before CD drive.

Reason why XP is on sdb:  I wanted to leave the xp drive completely unchanged since my Dell Optiplex is has over two years of warranty left.  I followed several posts on the forum, which recommended calling my existing xp drive  sdb and  loading ubuntu onto sda.  One of these threads I followed is
 ubuntuforums.org/showpost.php?p=2195398&postcount=47  
It says that grub will figure out that xp is on sdb and ubuntu is on sda.  After completing the installation, I have been able to use Grub to boot into xp with no problem.  But I can't boot into ubuntu for some reason.

If there is a better way of installing Ubuntu to my second HDD without at all altering my windows drive, I'm open to that.  

Thanks for your continued interest.

---

### Post by Pumalite on 2008-04-05
Get Gparted Live CD: [http://gparted.sourceforge.net/download.php](http://gparted.sourceforge.net/download.php)
Burn to disk and boot from it. Right click on XP, choose 'resize from the menu. In the free space left, make 3 partitions:
10 GB for '/'
1 GB for /swap (/swap=RAM in laptops if you want to hibernate)
The rest for /home. Then install Ubuntu, go 'Manual' and choose already prepared partitions.

---

### Post by BobAngelFire on 2008-04-06
> **Pumalite said:**
> Get Gparted Live CD: [http://gparted.sourceforge.net/download.php](http://gparted.sourceforge.net/download.php)
Burn to disk and boot from it. Right click on XP, choose 'resize from the menu. In the free space left, make 3 partitions:
10 GB for '/'
1 GB for /swap (/swap=RAM in laptops if you want to hibernate)
The rest for /home. Then install Ubuntu, go 'Manual' and choose already prepared partitions.
Are your instructions aiming to install ubuntu to my windows drive, currently sdb?  
I intended to avoid changing anything on the windows drive due to warranty issues that I explained in previous posts.
Another idea.... should I be looking a "black screen on bootup" issues that I've seen elsewhere on the forum.  I'm considering looking at those issues, since I see a black screen when I try to boot to ubuntu from grub.  (My video adapter is an ATI Radeon Xpress 1100.)
Thanks very much for your continued interest.

---

### Post by Pumalite on 2008-04-06
Then I misunderstood you:
'If there is a better way of installing Ubuntu to my second HDD without at all altering my windows drive, I'm open to that. '

---

### Post by BobAngelFire on 2008-04-06
> **Pumalite said:**
> Then I misunderstood you:
'If there is a better way of installing Ubuntu to my second HDD without at all altering my windows drive, I'm open to that. '
Thanks much for bearing with me...
We did have a misunderstanding, mostly my fault.  
When I said "install ubuntu to my second HDD" I was referring to the new drive I added to my box, which is now connected as sda.  My "original" HDD, which has been running xp, and is now sdb, is the one I'd like to keep intact, due to warranty.  I can boot to that xp drive from grub with no problem.  My problem is that booting to ubuntu from grub gives me only a black screen with just a blinking cursor.

Any thoughts on my suggestion to look  at "black screen on bootup" posts on the forum?  Maybe ubuntu hasn't been configured correctly for my ATI Radeon Xpress adapter and LCD monitor?

Thanks again...

---

### Post by Pumalite on 2008-04-06
Try:
Ctrl+Alt+F1 to get a command line
Then:
sudo dpkg-reconfigure xserver-xorg
Accept most defaults, choose 'vesa' as the driver
Then: startx

---

### Post by BobAngelFire on 2008-04-06
In order to enter the commands you suggest, I'd guess that I'd have to boot up using the live CD, because that's the only way I can successfully boot to Ubuntu.
Question:  If I entered the commands you suggest, wouldn't they have no effect on the ubuntu installation that's on my sda drive?  I'm under the impression that any changes made after booting with live CD will disappear when the machine is shut down.
If I'm wrong, please tell me....

---

### Post by Pumalite on 2008-04-06
I thought you had installed Gutsy and when you chose it in Grub, you ended up with a blank screen with a blinking cursor:
'Problem: Although grub menu looks normal at startup and XP boots ok, Gutsy doesn't boot up at all. I just see blinking cursor on a blank screen.'

That's where I suggested to apply the commands I gave you.

---

### Post by BobAngelFire on 2008-04-06
> **Pumalite said:**
> I thought you had installed Gutsy and when you chose it in Grub, you ended up with a blank screen with a blinking cursor:
'Problem: Although grub menu looks normal at startup and XP boots ok, Gutsy doesn't boot up at all. I just see blinking cursor on a blank screen.'

That's where I suggested to apply the commands I gave you.
Unfortunately, I'm not able to get a command line.  
I tried "Ctrl+Alt+F1" at a) the blank screen with blinking cursor and (just in case) b) at the grub menu.

BTW, when I try booting from grub with the safe mode of ubuntu, I still get a blank screen.

BTW, I noticed when I was looking at the grub menu that it gave options of "e" to edit and "c" for command line.  

When the non-safe boot mode of grub was highlighted and I pressed e, I saw this:
root (hdo,1)
kernel /boot/vmlinux......(a long line, which I can pass on if it's meaningful)
instrd /boot/instrd......(line continues)
quiet 

When, instead, I pressed c when in the grub menu, I saw this:
grub>

When I tried to enter the commands you suggested, the response I got was "unrecognized command", not surprisingly.

I'm beginning to think I have a video driver and/or display  incompatibility in the ubuntu installed on my HDD.  However, I'm surprised that the live CD (64 bit version) does boot up with no problems.

---

### Post by Pumalite on 2008-04-06
Here are a few guides on how to use boot parameters and a collection of them:
[http://grumpymole.blogspot.com/2007/05/ubuntu-how-to-edit-grub-boot-parameters.html](http://grumpymole.blogspot.com/2007/05/ubuntu-how-to-edit-grub-boot-parameters.html)
[https://help.ubuntu.com/7.04/installation-guide/hppa/boot-parms.html](https://help.ubuntu.com/7.04/installation-guide/hppa/boot-parms.html)
Start with the most common:
noapic nolapic acpi=off pci=noacpi pnpbios=off vga=0x317 vga=791

---

### Post by BobAngelFire on 2008-04-06
Thanks very much for directing me to boot parameters.
It will take me a little while to study them and try them out.
I'll post later to report any success or failure that I have.
thanks again....

---

### Post by Pumalite on 2008-04-06
Good luck.

---

