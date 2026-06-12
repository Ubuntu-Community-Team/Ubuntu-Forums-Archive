---
title: "Grub Legacy versus GRUB2 for Ubuntu 10.04 LTS"
date: 2010-12-18
forum: Installation &amp; Upgrades
---

### Post by hpng on 2010-12-18
Grub Legacy versus GRUB2 for Ubuntu 10.04 LTS 

I like to thank folks who helped here. Some when out of their way to look up information.  Thank you.     

I am planning on installing Ubuntu 10.04 ( Lucid Lynx ).  I have a dv7-4173us laptop with AMD 64 bits processors.  It has Win 7 64-bits.  As with all new HP laptops, it already has 4 primary factory partitions. 
I have removed two partitions ( RECOVERY and HP_TOOLS) to make space for Lucid Lynx.  I read about Ubuntu installation at  ubuntuguide.org 

If you know of other sites with step by step install tutorial, please advice. Here is what   I found about partitioning for Linux. 

Using Grub Legacy for the boot partition :   [http://ubuntuguide.org/wiki/Multiple_OS_Installation#Using_Grub_Legacy_for_the_boot_partition](http://ubuntuguide.org/wiki/Multiple_OS_Installation#Using_Grub_Legacy_for_the_boot_partition)      

The author suggest using GRUB Legacy for most of the install versus using the default GRUB2 on Lucid. So I am confused.  

I am going to create two partitions in addition of existing Win 7 OS and Win 7 SYSTEM partitions. Here is what the author wrote for minimal partitions:      

At the minimum you will need:  one primary partition for each Windows OS  an extra small primary partition (which can be resized later, in case is needed).

 If a Windows boot partition exists as a second NTFS partition, it should be left alone. 

If there is a Windows recovery partition also installed, it can also be left alone as long as there are only two NTFS partitions total on the hard drive (i.e. there is no NTFS boot partition as well).

 If there are a total of 3 NTFS partitions on the hard drive, then the third Windows NTFS partition (the recovery partition) should be removed after creating Recovery CDs from it (see here). 

one primary partition for the small boot partition (for storing a set of GRUB files)  an extended partition for the Linux OSs (should be the last partition on the hard drive) …......... 

I still do not understand why GRUB2 is not recommended.  Please advice. 
I mean if it si not recommended, why is it included with LiveCD?

I like to know if anyone has successfully install Lucid from LiveCD onto two partitions with no additional GRUB2 patch or modifications ( or Win 7 boot loader reinstall ) to make Lucid works.    

FAN ISSUE: ??  By the way, for those who have Lucid (10.04 LTS) on laptop, when in SUSPEND mode, does the fan also stop or does it continue to run continuously?

---

### Post by wilee-nilee on 2010-12-18
If you install into partitions with the booted 10.04 cd you will have grub2. That link is probably old it talks about 9.04.

Grub2 has a a program included called os-prober, it does what the name suggests, it finds other OS and puts them in the grub menu for booting.....most of the time, always if everything is in order in all OS's pretty much.

Don't mess with downloading to grub-legacy unless you know what your doing, I doubt you would need it. You don't need a boot partition either the mbr will be where the bootloader resides calling out to the OS to boot at startup and choice of which OS you want to boot.

Give us a screen shot of gparted use the take screenshot from menu-accessories for this and attach it to a reply.

---

### Post by hpng on 2010-12-18
> **wilee-nilee said:**
> If you install into partitions with the booted 10.04 cd you will have grub2. That link is probably old it talks about 9.04.

Grub2 has a a program included called os-prober, it does what the name suggests, it finds other OS and puts them in the grub menu for booting.....most of the time, always if everything is in order in all OS's pretty much.

Don't mess with downloading to grub-legacy unless you know what your doing, I doubt you would need it. You don't need a boot partition either the mbr will be where the bootloader resides calling out to the OS to boot at startup and choice of which OS you want to boot.

Give us a screen shot of gparted use the take screenshot from menu-accessories for this and attach it to a reply.

When Gparted is running, how do you take a screen shot?
I assume when Gparted is running during partitioning and installation of Ubuntu, right?

Do I still go ahead and create a small partition for GRUB2 and then also an ext4 for Ubuntu?

---

### Post by kansasnoob on 2010-12-18
> I have removed two partitions ( RECOVERY and HP_TOOLS) to make space for Lucid Lynx. I read about Ubuntu installation at ubuntuguide.org 

Before installing anything be darn sure that Windows still boots!

Then use the Ubuntu Live CD, choosing "Try Ubuntu" rather than install. Once you're in the Live Desktop post the output of the Boot Info Script as described here:

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

That's just a starting point! Since you've already deleted partitions, but made sure Windows still boots, we'll likely need to see a screenshot of Gparted for each installed drive!

---

### Post by kansasnoob on 2010-12-18
BTW there's no need whatsoever with most recent hardware to create a separate /boot partition. That was written for Karmic when grub2 was very new, but IMHO it's one of the most confusing and poorly written guides I've ever seen!

Had I been confronted with that when I began I'd probably have just shot myself!

---

### Post by oldfred on 2010-12-18
In the beginning a lot of us had trouble understanding grub2, now we understand it and it is a lot better, but different and a bit more complex as it is designed for the future. Grub legacy was not maintained since 2005 and cannot handle a lot of new systems.

One real advantage of grub2 is its osprober. Old grub often could not find other systems and we had to manually maintain boot stanzas. Grub2 finds & sets up just about everything else now.

Create an extended partition and then all the logicals for Ubuntu.
For the Total space you want for Ubuntu:

Ubuntu's standard install is just / (root) & swap, but it is better to add another partition for /home:
1. 10-20 GB Mountpoint / primary or logical beginning ext4(or ext3)
2. all but 2 GB Mountpoint /home logical beginning ext3(or ext4)
3. 2 GB Mountpoint swap logical

Depending on how much memory you have you may not absolutely need swap but having some is still recommended. I do not hibernate (boots fast enough for me) but if hibernating then you need swap equal to RAM. And if dual booting with windows a shared NTFS partition is also recommended. But you usually cannot create that as part of the install, just leave some space.
One advantage of partitioning in advance is that the installer will use the swap space to speed up the install. Thanks Herman for the tip.
Then with partitions created you have to use manual install and tell it which partition is / (root) and its format, which is /home and if you wanted it formated (yes if first install, no on any reinstalls). It seems to find swap on its own.

Herman on advantages/disadvantges of separate system partitions post#3
[http://ubuntuforums.org/showthread.php?t=1410392](http://ubuntuforums.org/showthread.php?t=1410392)

---

### Post by hpng on 2010-12-18
> **kansasnoob said:**
> Before installing anything be darn sure that Windows still boots!

Then use the Ubuntu Live CD, choosing "Try Ubuntu" rather than install. Once you're in the Live Desktop post the output of the Boot Info Script as described here:

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

That's just a starting point! Since you've already deleted partitions, but made sure Windows still boots, we'll likely need to see a screenshot of Gparted for each installed drive!

Window is working.
When you mentioned using Ubuntu Live CD with "Try Ubuntu" option, is that sa,e as using Wubi?

---

### Post by Quackers on 2010-12-19
No, not at all. You would be using a Live cd desktop which is gone after you reboot. No changes are made to your system at all.
It is a very useful thing, as many repairs can be done via the Live cd environment, for times when your normal Ubuntu installation can't boot, or has other problems.

---

### Post by hpng on 2010-12-19
> **Quackers said:**
> No, not at all. You would be using a Live cd desktop which is gone after you reboot. No changes are made to your system at all.
It is a very useful this many repairs can be done via the Live cd environment, for times when your normal Ubuntu installation can't boot, or has other problems.

I download the desktop Ubuntu 64 Lucid Lynx and burnt it to CD
i put the CD in and the autorun ask if I want to run Wubi.
I thought Wubi installs Ubuntu in C: (windows ) partition, which is not what I want.
So I shut it down.  Did I download the incorrect distro?

There is no file I can click to run on the CD except Wubi and USB-Reater apps.
Please advice.

Thanks.

---

### Post by hpng on 2010-12-20
> **kansasnoob said:**
> Before installing anything be darn sure that Windows still boots!

Then use the Ubuntu Live CD, choosing "Try Ubuntu" rather than install. Once you're in the Live Desktop post the output of the Boot Info Script as described here:

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

That's just a starting point! Since you've already deleted partitions, but made sure Windows still boots, we'll likely need to see a screenshot of Gparted for each installed drive!

I downloaded the script and ran the command below.  

```
   
sudo bash ~/home/ubuntu/downloads/boot_info_script*.sh

```

I got errors.

```

ubuntu@ubuntu:~$ sudo bash ~/home/ubuntu/downloads/boot_info_script*.sh
bash: /home/ubuntu/home/ubuntu/downloads/boot_info_script*.sh: No such file or directory
ubuntu@ubuntu:~$ 


```
I could not take a screen shot.  I tried using GNOME screen shot, but nothing
happen.
But the file is in Downloads.  So this does not make sense.
I also notice my keyboard cursor (not mouse pointer ) is behaving strange as I am typing this posting..
The cursor here and there randomly.ow.
I also remove my optical mouse, but it is still a problem....


Please advice.  I do nnot have same problem on Win 7.
It is like something is making the cursor move randomly......

The cursor problem is more serious than anything else now.
 
Please advice.

---

### Post by wilee-nilee on 2010-12-20
just drag or copy and paste it to the desktop and copy and paste this command into the Ubuntu terminal. This command is on the bootscript page, which a link to, is in my signature.
```
sudo bash ~/Desktop/boot_info_script*.sh 
```

---

### Post by garvinrick4 on 2010-12-20
Put the script you downloaded on desktop and run this.


```
 sudo bash ~/Desktop/boot_info_script*.sh 
```

---

### Post by oldfred on 2010-12-20
Linux is case sensitive.

Your command:
sudo bash ~/home/ubuntu/[COLOR=Red]d[/COLOR]ownloads/boot_info_script*.sh

You mention the file is in[COLOR=Red] D[/COLOR]ownloads:
sudo bash ~/home/ubuntu/[COLOR=Red]D[/COLOR]ownloads/boot_info_script*.sh

---

