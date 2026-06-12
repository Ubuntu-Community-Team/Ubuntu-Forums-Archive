---
title: "GRUB is missing after installing Ubuntu 12.04 LTS"
date: 2016-01-17
forum: Installation &amp; Upgrades
---

### Post by alfredo10 on 2016-01-17
Hi, as the title says, I just installed Ubuntu 12.04 LTS.

I had 10.04 installed and used the "Erase 10.04 and install 12.04" (or something like that) option on the install CD. It's shared with Windows XP on another partition.

However, now after installing Ubuntu boots automatically, I don't get the option to decide with OS I want to boot.

I run Boot Repair and the problem didn't solve, I just got the URL: [http://paste.ubuntu.com/14563402/](http://paste.ubuntu.com/14563402/) and as indicated in boot repair I'm posting it in this forum for help.

I've got a few other minor issues but lets get on with this one first ;)

Thanks for any info,

Alfredo

---

### Post by yancek on 2016-01-17
Your windows partitions are still there and Grub is installed correctly with entries to boot windows.  The only thing I saw that could be the problem, or at least part of it, is the info below:

> /usr/sbin/grub-setup: warn: Sector 50 is already in use by FlexNet; avoiding it.  This software may cause boot or other problems in future.

I've seen that before but not being a windows user, don't know how to solve.  Might google the above while you are waiting for a response.

---

### Post by Bucky Ball on 2016-01-18
After the manufacturer's splash screen at boot try hitting shift. That should get you to the menu where you can choose OSs. Failing that, open a terminal and open this file by using this command:

```
sudo nano /etc/default/grub
```

Change these lines to look like this (exactly):

```
GRUB_DEFAULT=0
# GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
```

Control+x, 'y' and enter to save and close, then:

```
sudo update-grub
```

Reboot. Get a menu? 

* By the way, this doesn't appear to be a UEFI install (as there is no EFI boot partition) so disregard info related to that. From your output:

```
=================== UEFI/Legacy mode:
This installed-session is not EFI-compatible.
SecureBoot disabled.
```

This is a regular legacy install. Re-reading your post it makes sense as you are using XP and that wasn't preinstalled using UEFI. :)

---

### Post by alfredo10 on 2016-01-18
Thanks Yancek and Bucky Ball, but no, still no luck :(

After this I even tried my XP install disc and see if I could do a repair but no luck either, it doesn't even tell the disc is there and boots straight into Ubuntu. The Ubuntu disc I used to install does work, don't know if this helps at all.

Any other thoughts?

Thanks again for your help, really appreciate it,

Alfredo

---

### Post by oldfred on 2016-01-18
Flexnet is from proprietary software in Windows that has DRM, flexnet is the DRM manager. It used to be that Flexnet & grub overwrote each other in sectors after MBR but before first partition. Now grub finds Flexnet and writes around it, so it should not be an issue, just a warning.

Did you run chkdsk on your NTFS partitions? That is always required after a resize.
And if errors you have to rerun until no errors.
chkdsk C: /r  
#(have to run /r or /f as separate entries) rerun until no errors

---

### Post by Bucky Ball on 2016-01-18
If you have done this:

```
GRUB_DEFAULT=0
# GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
```

... then this:

```
sudo update-grub 
```

... and you are not seeing a menu at boot I am truly puzzled. :-k

Could you open that file again and make sure those lines in your file are exactly identical to what I have here as an example, please?

```
sudo nano /etc/default/grub
```

If not, change them then run the 'sudo update-grub' command again. Reboot. Hitting the 'shift' key doesn't get you to a menu at boot either? You are going at it directly after the manufacturer's splash screen? Tapping, not one hit? 

It changed awhile ago and I get confused. I am 99% certain it is shift, but try the enter key and see if that makes a diff.

Also, this:

```
Warning: extended partition does not start at a cylinder boundary.
DOS and Linux will interpret the contents differently.
```

... may have something to do with it. Don't have the knowledge to t

---

### Post by oldfred on 2016-01-18
I do not think cylinder boundry is an issue, unless it means BIOS is not set correctly for drive, should be LBA or large or large block.

 [http://askubuntu.com/questions/156994/partition-does-not-start-on-physical-sector-boundary](http://askubuntu.com/questions/156994/partition-does-not-start-on-physical-sector-boundary)
Since drives became over 8GB CHS cylinders, heads, sectors has been obsolete and LBA is how drive is configured. For more compatibility with newer drives, 4k drives, SSDs and better configuration, partitions now start at sector 2048 rather than rounding to cylinders. With 512 bytes per sector that is 1MB at the beginning of the drive.
[http://en.wikipedia.org/wiki/Cylinder-head-sector](http://en.wikipedia.org/wiki/Cylinder-head-sector)

But new drives, SSD & 4K drives need sector boundries.

 Partition 4 does not start on physical sector boundary.
First, understand that most partitioning tools have moved to a policy of aligning partitions on 1 MiB (2048-sector) boundaries as a way of improving performance with some types of arrays and some types of new hard disks (those with 4096-byte physical sectors). See article by srs5694:
[http://www.ibm.com/developerworks/linux/library/l-4kb-sector-disks/](http://www.ibm.com/developerworks/linux/library/l-4kb-sector-disks/)
Post on 8-sector boundaries alignment by srs5694
[http://ubuntuforums.org/showthread.php?t=1685666](http://ubuntuforums.org/showthread.php?t=1685666)

---

### Post by alfredo10 on 2016-01-18
> **oldfred said:**
> Did you run chkdsk on your NTFS partitions? That is always required after a resize.
And if errors you have to rerun until no errors.
chkdsk C: /r  
#(have to run /r or /f as separate entries) rerun until no errors

oldfred, I did not do any resizing, I just replaced my old 10.04 with 12.04 automatically from the install cd, not sure what process it uses to do the replacement.
Also, I don't have access to my XP, can't run chkdsk :(

Bucky Ball, neither "Enter", "Shift" or even "Tab" works at start up, "Del" however does get me into BIOS Setup as it should, but I don't see any option that will help me fix this. I re-checked and this is as should be: ```
GRUB_DEFAULT=0
# GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
```

Along with this three other lines:
```
GRUB_DISTRIBUTOR='lsb_release -i -s 2> /dev/null ll echo Debian'
GRUB_CMDLINE_LINUX_DEFAULT=""
GRUB_CMDLINE_LINUX=""
``` replace the two ll before echo with vertical lines, I can't find them on my keyboard :)

I had not mentioned, but Gparted does show that the XP partitions do exist, I can even use the file manager to access drives C: and D: which I use in Windows (C: for program files, D: for documents and other files). Sorry I can't give more specific info, since other than basic programming and installation, I'm not too computer literate, but if you know any way of retrieving more in-depth info, I'm all ears ;)

Thanks again for your help and hope to hear any other ideas,

Alfredo

---

### Post by oldfred on 2016-01-18
On my keyboard the vertical line is more like two vertical dashes but is this: | 
And it is above \ backslash, but that can vary a lot.

---

### Post by alfredo10 on 2016-01-18
Yes, here they are: || I found it next to \ with Altgr, I just had selected the wrong keyboard (Latin Spanish instead of plain Spanish) Thanks ;) 

Still struggling with the boot issue though :(

---

### Post by oldfred on 2016-01-18
Using Boot-Repair's advanced options choose Windows and install boot loader to MBR. Then you should be able to directly boot Windows or see if you then can repair it.
Then once Windows boots ok, use Boot-Repair to restore grub to MBR. Grub really only boots working Windows. And you really need a repair disk or the original XP install disk to be able to make Windows repairs.

---

### Post by alfredo10 on 2016-01-19
Thanks oldfed, sorry to be such a pain but...

> **oldfred said:**
> Using Boot-Repair's advanced options choose Windows... 

Ok, I found this option and selected Windows, but:

> **oldfred said:**
> ... and install boot loader to MBR.

Not sure in which tab or which checkbox this is, there's an "MBR options" tab but it's grayed out.

And finally:

> **oldfred said:**
> Then once Windows boots ok, use Boot-Repair to restore grub to MBR.

Ok, so I do this after I figure out if the previous step works, but once again not sure where to find this, is it the one that says "Restore MBR"?

I really appreciate your help, have a great day,

Alfredo

---

### Post by oldfred on 2016-01-19
With the Windows option you are not restoring grub, It may default. I do not have Windows and cannot test it. If given a choice you must choose drive, not a partition.

[http://sourceforge.net/p/boot-repair/home/Home/](http://sourceforge.net/p/boot-repair/home/Home/)

---

### Post by alfredo10 on 2016-01-19
Ok, the "Place GRUB into" doesn't really give me any other options if I press the menu arrow, it only shows "sda"

I will hit apply and take my chances...

Thanks and hopefully will come back to report

---

### Post by oldfred on 2016-01-19
If you choose Windows, it should be installing syslinux to MBR, not grub. Syslinux is a Windows type boot loader that will directly boot Windows, if boot flag is on Windows NTFS partition.

---

### Post by alfredo10 on 2016-01-19
ok, so now I'm in the opposite situation, the computer boots directly into Windows XP.

Through Windows repair with the XP CD I managed to add a menu at boot that gives me two Windows boot options, I believe one is normal Windows and the other is repair mode.

However, non of the Windows solutions work either to make Ubuntu option appear at boot menu.

Just an idea:
What could happen if I re-installed Ubuntu? I didn't get the chance to get custom software installed in it so it wouldn't be difficult to start over with it.

Any thoughts?

---

### Post by oldfred on 2016-01-20
I might try Boot-Repair's advanced mode and choose the full uninstall/reinstall of grub2. That updates all grub and restores grub to MBR.
The auto fix in Boot-Repair just copys a new grub boot loader into MBR which you can also try.
If those do not work, you can try a full reinstall as it may be some other issue.

Does Windows boot without issue? Grub only boots working Windows.

---

### Post by alfredo10 on 2016-01-21
Hi oldfred,

Yes, Windows launches with no problem, I repaired the boot menu from Windows install CD, but now the Ubuntu CD doesn't work (it loads and gets stuck on a purlple-ish screen) so I will format the Ubuntu and swap partitions and try installing again, hopefully nothing goes wrong this time.

Thanks for your help, I'll come back later and let you know how it went.

Any suggestions on how to avoid the grub from not installing again?

Have a nice day,

Alfredo

Guys, I appreciate all your help but I gave up on this.

Formatted, reinstalled, repaired, nothing works. Now I can't even get the Live CD to work in "Try Ubuntu" mode, so that's it for me and Ubuntu, gave it a fair try.

I'll come back later whenever I have free time to fiddle with this stuff or Linuxcnc is available for a later Ubuntu version.

Won't mark as solved because, well, it didn't get solved.

Thanks again for your help,

Alfredo

---

### Post by Bucky Ball on 2016-01-22
In the absence of any appropriate tag, I am going to mark this as solved as you no longer want help with this and it will save potential helpers wasting time in future. 

Better luck next time.

---

### Post by alfredo10 on 2016-01-27
Just as a note, as I had no other choice but to insist on Ubuntu, I installed release 14.04 LTS and Grub is back as it should, so maybe it's a problem with the 12.04 Live CD? Not sure.

I don't require an answer, just in case someone comes by and reads this. Thanks again for all your help.

---

