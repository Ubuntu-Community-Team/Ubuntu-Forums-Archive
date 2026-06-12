---
title: "Dual Boot: Windows 7 &amp; Ubuntu -- serious confusion"
date: 2009-11-27
forum: Installation &amp; Upgrades
---

### Post by Xenzaka on 2009-11-27
This is a long read, I don't think my problem is too common :|

I have two HDDs, a 250GB and a 1TB. 

We're going to focus on one single HDD, the 250GB, this is my "Operating Systems & Programs" disc. Everything else from music to games has been partitioned on my 1TB HDD, my 1TB disc is entirely irrelevant to my problem. 

My 250GB is first in boot order. 

My 250GB disc is divided in this fashion (and in this order, left to right):
NTFS (Windows 7) HD(0,0) @ 75GiB >>> .EXT3 "/" (Ubuntu) HD(0,1) @ 75GiB >>> Swap Partition HD(0,2) >>> /home .EXT3

I have heard once before that for some reason, Ubuntu should be the very first partition. Is that right?

I've done everything "right". 

Here is my problem starting from the point I press the on-button to where I am, typing this message now, and so on. It will be step by step for better readability. 

1) Post

2) Grubs loads, and in this case, I have quite a few options. (Hey, and they all work 

3) I choose Windows 7 on sda1 

3.5) This is where things get weird: NOW I'm brought to Windows Boot Manager to select either Windows 7 or Ubuntu...if I select Windows 7, everything and anything works. If I select Ubuntu from the WBM, it tries to "install" and asks for the Ubuntu live CD (or source, rather) **What the hell?! **

4) Windows boots, I go into my (C:) drive to find bootmgr as a single file, not in any folder (I feel this is a "hidden" file). As far as I know, this is normal, but I believe this is the file that holds this stupid obsession with showing Ubuntu, a version that doesn't even work!

5) I cannot uninstall Ubuntu, I have provided a screen shot of the error. In Windows, it clearly shows that Ubuntu has been installed (of course, it doesn't work, I can't uninstall it, or anything for that matter. 

5.5) IF Ubuntu is truly installed on other partitions, can I uninstall Ubuntu located on Windows 7 (wow, that seems time consuming and perhaps impossible).

6) My overall problem is I have Ubuntu installed on my machine, apparently some of it (not of all of it) is on my C: drive. 
[B]
7) [/B][B]THE PROBLEM: I don't understand why my NTFS Windows 7 partition is showing Ubuntu crap on my NTFS. I installed Ubuntu on a separate partition (on the same hdd as win7) 

Synopsis: [/B]I have Ubuntu installed .ext3 with it's directory of "/", I also have a swap partition and I was going to create a new /home partition until I realized my system is not recognizing the two operating systems as two different entities, it almost seems like they have been installed side by side. I'm severely frustrated, all I want to do is learn and start creating code. I've done everything "right" step by step tutorials, the FaQs, now I'm reaching out, what the hell is going on here? 

If need be, I'm willing to go out and purchase an external HDD, back up all of my data and (for a fourth time, now) try to dual boot Windows 7 and Ubuntu without files and folders getting "mixed up". 

Basically, I just want a clean install of Windows 7 on (C:), on my 250GiB that occupies about 79GiB of space. On THE SAME 250GiB disc, I want the other half to be Ubuntu, where they both can share resources from my 1TB HDD. 

Ubuntu works just fine from the original grubs menu, forgot to mention that. But like I mentioned earlier, it DOES NOT WORK when I'm brought to the Windows Boot Manager. 

I would like to UNINSTALL UBUNTU from Windows, and allow access to Ubuntu ONLY from Grubs, not Windows Boot Manager. On the other hand, I do like Windows Boot Manager because if I press F8, I'm given a list of options I can do before Windows 7 boots up, like safe mode, etc, all with out the CD. 

So, what is going on here? What can I do? 

I'm sorry for any poor grammar / typos, I'm in a hurry and very frustrated. Thanks for all or any input & reply!

---

### Post by Xenzaka on 2009-11-27
This is truly weird, the more I think about it, the more confusing it seems to be :|, I truly hope someone has had the same problem before. 

My system specs are irrelevant, but let me know if after all, I do need them. I feel my BIOS settings are just fine as well, but maybe that too -- I'm missing something, I really do not know at this point. I've never had such a strange problem. 

I have a hard time working on it because I don't want to destroy or lose any key/system files.

---

### Post by darkod on 2009-11-27
Did you ever try to install wubi.exe? It installs ubuntu sort of "virtually", inside windows and adds entry for Ubuntu in windows bootloader. That is the only way that option can get there, otherwise windows bootloader can't see the full Ubuntu installation or the partitions. Take a peek in Add/Remove programs and try to remove Ubuntu. That should not do any damage to the proper ubuntu on /dev/sda2.

---

### Post by phillw on 2009-11-27
Try ```
sudo update-grub
```

If that doesn't work for you, head over to [http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)  for a HowTo on MBRS in dual boot mode.

Should things be really broken, then you can re-install Grub2 via [http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)

If the update doesn't work - the 1st thread should get you and running.

Regards,

Phill.

---

### Post by phillw on 2009-11-27
The output of ```
sudo fdisk -l
```  would be of a help for us to see what partitions you have.

Regards,

Phill.

---

### Post by presence1960 on 2009-11-27
Let's get a better look at your setup & boot process. Boot into Ubuntu. Come back here and use the link in my signature to download the Boot Info Script to the desktop. Once on desktop open a terminal and run this command ```
sudo bash ~/Desktop/boot_info_script*.sh
``` This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text.

---

### Post by Xenzaka on 2009-11-27
All right, one last but friendly bump before I start hacking. I'm going to start working on this in about thirty minutes, any last input would be great, other than that I'll first work on supplying more detailed information as to my partition configuration and so on. 

Thanks again for all the support.

---

### Post by Xenzaka on 2009-11-27
> **phillw said:**
> The output of ```
sudo fdisk -l
```  would be of a help for us to see what partitions you have.

Regards,

Phill.

Here you are

[RIGHT]> xenzaka@xenzaka-desktop:~$ sudo fdisk -l

Disk /dev/sda: 203.9 GB, 203928109056 bytes
255 heads, 63 sectors/track, 24792 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xe9c121d8

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       10308    82798978+   7  HPFS/NTFS
/dev/sda2           10309       20616    82799010   83  Linux
/dev/sda3           20617       22704    16771860   82  Linux swap / Solaris
/dev/sda4           22705       24792    16771860   83  Linux

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xa8d1f950

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       38245   307200000    7  HPFS/NTFS
/dev/sdb2           38245       95612   460800000    7  HPFS/NTFS
/dev/sdb3           95612      121601   208758784    7  HPFS/NTFS
xenzaka@xenzaka-desktop:~$ ^C
xenzaka@xenzaka-desktop:~$**[SIZE=4][SIZE=2][/SIZE]  [/SIZE]**[/RIGHT]
 

More information coming shortly, work is still in progress.

---

### Post by Xenzaka on 2009-11-27
All right, RESULTS.TXT has been uploaded. Hopefully someone can help me! Thanks again for all the support!

---

### Post by Xenzaka on 2009-11-27
All right, I got everything Ubuntu related off the Windows 7 Partition, I'm sure it's ready for a defrag by now. 

My last issue is getting grubs back. I'm getting a lot of errors following many of the tutorials. 

Any help on how to recover grubs? I've tried many methods easily found by google searching.

---

### Post by presence1960 on 2009-11-27
> **Xenzaka said:**
> All right, RESULTS.TXT has been uploaded. Hopefully someone can help me! Thanks again for all the support!

```
sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe 
                       /grldr [COLOR="Red"]/wubildr.mbr /ubuntu/winboot/wubildr.mbr[/COLOR]

```

You did have Ubuntu installed via wubi at one point (see red text above).

To reinstall GRUB from Live CD/USB see [here]("https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD").

---

