---
title: "[SOLVED] Fixing XP partition from Ubuntu"
date: 2008-10-02
forum: Installation &amp; Upgrades
---

### Post by Lao_Tzu on 2008-10-02
Hi guys

I'm running Hardy and Windows XP (SP2) on a Dell Inspiron 1525. Today my computer crashed spectacularly ([while I was playing Armagetron]("http://ubuntuforums.org/showthread.php?p=5892732")) and now my XP partition seems to be screwed.

GRUB still works. I can boot Ubuntu. When I try to boot XP I get the Windows error menu (i.e. safe mode, safe mode with networking, last safe configuration, boot normally) but no matter which I choose the result is more or less the same: the windows logo appears briefly, then the BSoD flashes and my laptop resets.

If I choose safe mode, the list of loaded files appears up to a certain point and then stops (at MUP.ini I think). I'm offered the choice to press Esc and skip the loading of a certain file, but whether I do or don't press Esc the laptop resets either immediately or after a pause.

Choosing to load the factory pre-installed recovery OS (Vista) from GRUB gives me a "Device Not Detected" message and a restart.

Here are the results of fdisk -l

```
patrick@Patrick:~$ sudo fdisk -l
[sudo] password for patrick: 

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x90000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1           19131       19458     2620416    c  W95 FAT32 (LBA)
/dev/sda2   *          13        1317    10482412+   7  HPFS/NTFS
/dev/sda3            1318        5173    30973320    7  HPFS/NTFS
/dev/sda4            5174       19458   114736839+   f  W95 Ext'd (LBA)
Partition 4 does not end on cylinder boundary.
/dev/sda5           19131       19458     2620416   dd  Unknown
/dev/sda6            5174       18558   107514949+  83  Linux
/dev/sda7           18559       19130     4594558+  82  Linux swap / Solaris

Partition table entries are not in disk order
```

I would like to fix the XP partition without in any way compromising GRUB or my Ubuntu installation. *As a last resort* I wouldn't be too worried about having to reformat the XP partition and reinstall from scratch, as long as Ubuntu remains unaffected. Can anyone help? I would be hugely appreciative.

---

### Post by Lao_Tzu on 2008-10-02
I am screwed, aren't I?

---

### Post by tangibleorange on 2008-10-02
> **Lao_Tzu said:**
> I am screwed, aren't I?

don't worry! all is not lost. could you post the output of:

```
cat /boot/grub/menu.lst
```

also, can you access the windows partition from ubuntu? does it mount automatically?

---

### Post by caljohnsmith on 2008-10-02
Do you have a Windows Install CD? I think your first step should be to run a chkdsk on your Windows XP partition. If you have the Windows Install CD, boot it, and in the first main menu press "r" to get the recovery console, and then do:
```
map
```
That will show your Windows XP partition drive letter, so then do:
```
chkdsk /r <drive letter>
```
If you don't have a Windows XP Install CD, you can download a Windows XP Recovery CD from [here]("http://www.webtree.ca/windowsxp/tools/bootdiscs/xp_rec_con.zip"). But it's quite likely that a simple "chkdsk" is not going to be enough to fix your Windows, and you will probably have to do a "Windows Repair" from a Windows Install CD.

---

### Post by Lao_Tzu on 2008-10-02
Thanks very much! Will report back in two hours ish.

---

### Post by Lao_Tzu on 2008-10-02
Thanks guys.

tangibleorange,

The results of ```
cat /boot/grub/menu.lst
``` are attached as menu.txt. I hope it's illuminating!

And yes, the Windows partition does mount automatically in Ubuntu and I can access the files.

caljohnsmith,

That sounds like a plan. But in the name of caution (uber alles), I want to check that those actions won't compromise the GRUB or the Ubuntu partition at all... right? I don't have an Ubuntu live CD available at the moment.

---

### Post by caljohnsmith on 2008-10-02
> **Lao_Tzu said:**
> 
That sounds like a plan. But in the name of caution (uber alles), I want to check that those actions won't compromise the GRUB or the Ubuntu partition at all... right? I don't have an Ubuntu live CD available at the moment.
No, your Ubuntu and Grub should be just fine. :) By the way, you never mentioned, but do you have your Windows Install CD?

---

### Post by Lao_Tzu on 2008-10-02
Yes, I do. Sorry, I should have mentioned that.

---

### Post by Lao_Tzu on 2008-10-02
Okay, caljohnsmith, I tried using the Windows Install CD and the method you mentioned. I booted from the CD and went through the process (refrained from pressing F6 for a RAID driver, and refrained from pressing F2 to run automated system recovery). It did various things like loading the Kernel Debugger DLL and so forth, but when it got to "... is starting Windows" it came up with a Blue Screen of Death.

So I didn't even get to the first main menu where I could have pressed "r" for recovery. Problemos.

---

### Post by tangibleorange on 2008-10-02
what does the BSOD say? i know it probably won't be very illuminating but you never know...
are you still wanting to boot to Vista recovery? i think i know why that isn't working - try changing line 199 of your /boot/grub/menu.lst to read this:

```
root		(hd0,0)
```

then try booting what it claims is XP embedded. that might boot the vista recovery program.

---

### Post by Lao_Tzu on 2008-10-02
Thanks, tangibleorange.

I did what you suggested and tried to boot the Vista Recovery partition. It brought up an initial loading screen which said "Dell" and had a scrolling progress indicator like you usually see on the XP loading screen. Then, BSOD:

> Plug and Play detected an error most likely caused by a faulty driver.

Technical information:
*** STOP: 0x000000CA (0x00000001,0x82ED2E30,0x82FCDC08,0x00000000)

I suspect that /dev/sda4 is screwed in some way I can't define, and that all attempts to run programs that access that location will fail BSoD-style. (But I can't explain why I can access files in the Windows partition that mounts automatically in Ubuntu. I can also access the files in the recovery partition.)

GParted is seeing one large /dev/sda1 of unallocated space, 149.06 GB in size.

---

### Post by caljohnsmith on 2008-10-02
So is everything working OK in Ubuntu? Because it seems possible you could have some sort of hardware issue at this point. Also, do you know what is supposed to be on sda5? I'm wondering because fdisk doesn't even know what file system that partition has.

---

### Post by Lao_Tzu on 2008-10-02
Yes, everything is working fine in Ubuntu, as far as I can tell. I can even play mp3s off the Windows partition.

The possibility of a hardware issue is disquieting, but it may be the case. (Thing is, this problem seemed to start today when Armagetron crashed - that was the first time I saw a BSoD on this laptop - and I don't know whether that could cause a hardware problem.)

I don't know what's supposed to be on sda5, I'm afraid.

In case it is helpful, the output of ```
cat /etc/fstab
``` is attached as fstab.txt.

Thanks for all your help so far...

---

### Post by Lao_Tzu on 2008-10-02
OK, this might help. System Monitor throws up the attached screenshot.

It seems that /sda5 is being seen as a more or less direct copy of /sda1.

And another piece of information that MAY be helpful. The second time that Armagetron crashed, I pressed the "home" button on the laptop's dashboard instead of the power button. That produced the BSoD. I see that this button is supposed to start MediaDirect... so perhaps that's the cause of the problem -- that I pushed this button in the midst of a crash -- and not a problem with Armagetron itself.

---

### Post by tangibleorange on 2008-10-02
> **Lao_Tzu said:**
> OK, this might help. System Monitor throws up the attached screenshot.

It seems that /sda5 is being seen as a more or less direct copy of /sda1.

And another piece of information that MAY be helpful. The second time that Armagetron crashed, I pressed the "home" button on the laptop's dashboard instead of the power button. That produced the BSoD. I see that this button is supposed to start MediaDirect... so perhaps that's the cause of the problem -- that I pushed this button in the midst of a crash -- and not a problem with Armagetron itself.

hmm i'm afraid im kinda out of ideas. if even the windows recovery CD is BSODing, it would definitely suggest a hardware failure...

---

### Post by Lao_Tzu on 2008-10-03
OK. Well, thanks for your help, tangible!

Does anyone else have any ideas? Is there anything I could do, like trying to format the faulty partitions, or something? A friend suggested I delete sda5 and try to reinstall windows (but said I should keep an Ubuntu Live CD around so I could reinsert the GRUB and get back to my Ubuntu afterwards).

Another suggestion was to check the state of the disk using a program like [SpinRite]("http://www.grc.com/sr/spinrite.htm"). So I guess I'm going to do that first to see the state of the disk, then try deleting sda5 and reinstalling Windows.

In the meantime, if anyone has any ideas I'd be hugely appreciative! I'm off to buy some blank CDs.

---

### Post by caljohnsmith on 2008-10-03
I would recommend at least checking your HDD's partition table at this point just in case that is the issue. First enable all your repositories in System > Prefs > Software Sources, and then download and run testdisk with:
```
sudo apt-get install testdisk
sudo testdisk
```
After starting testdisk with the above command, choose "no log", select HDD and "proceed", "Intel", "Analyze", and see what it shows for your HDD and what errors it might give. Post the output of that screen and we can check it.

---

### Post by Lao_Tzu on 2008-10-03
Thanks! Here's the output:

```
Disk /dev/sda - 160 GB / 149 GiB - CHS 19457 255 63
Current partition structure:
     Partition                  Start        End    Size in sectors

 1 * FAT32 LBA            19130 218 33 19457  21 20    5240832 [MEDIADIRECT]
 2 P HPFS - NTFS             12   0  1  1316 254 63   20964825
 3 P HPFS - NTFS           1317   0  1  5172 254 63   61946640
 4 E extended LBA          5173   1 62 19457  21 20  229473679
Space conflict between the following two partitions
 4 E extended LBA          5173   1 62 19457  21 20  229473679
 1 * FAT32 LBA            19130 218 33 19457  21 20    5240832 [MEDIADIRECT]
 5 L Sys=DD               19130 218 33 19457  21 20    5240832
   X extended              5173   1 63 18557 254 63  215029900
 6 L Linux                 5173   2  1 18557 254 63  215029899
   X extended             18558   0  1 19129 254 63    9189180
 7 L Linux Swap           18558   1  1 19129 254 63    9189117


*=Primary bootable  P=Primary  L=Logical  E=Extended  D=Deleted

```

When I "Proceed" it says this:

```
Disk /dev/sda - 160 GB / 149 GiB - CHS 19458 255 63
     Partition               Start        End    Size in sectors
* FAT16 >32M               0   1  1    11 254 63     192717 [DellUtility]
P HPFS - NTFS             12   0  1  1316 254 63   20964825
P HPFS - NTFS           1317   0  1  5172 254 56   61946633
L Linux                 5173   2  1 18557 254 60  215029896
L Linux Swap           18558   1  1 19129 254 42    9189096
L FAT32 LBA            19130 218 33 19457  21 20    5240832 [MEDIADIRECT]

```

* = Bootable, P = Primary partition, L = Logical partition

---

### Post by caljohnsmith on 2008-10-03
> **Lao_Tzu said:**
> 
```
Disk /dev/sda - 160 GB / 149 GiB - CHS 19457 255 63
Current partition structure:
     Partition                  Start        End    Size in sectors

 1 * FAT32 LBA            19130 218 33 19457  21 20    5240832 [MEDIADIRECT]
 2 P HPFS - NTFS             12   0  1  1316 254 63   20964825
 3 P HPFS - NTFS           1317   0  1  5172 254 63   61946640
 4 E extended LBA          5173   1 62 19457  21 20  229473679
[COLOR="Red"]Space conflict between the following two partitions[/COLOR]
 4 E extended LBA          5173   1 62 [COLOR="Red"]19457[/COLOR]  21 20  229473679
 1 * FAT32 LBA            [COLOR="Red"]19130[/COLOR] 218 33 19457  21 20    5240832 [MEDIADIRECT]
 5 L Sys=DD               19130 218 33 19457  21 20    5240832
   X extended              5173   1 63 18557 254 63  215029900
 6 L Linux                 5173   2  1 18557 254 63  215029899
   X extended             18558   0  1 19129 254 63    9189180
 7 L Linux Swap           18558   1  1 19129 254 63    9189117


*=Primary bootable  P=Primary  L=Logical  E=Extended  D=Deleted

```

Well it looks like we may have found your problem--your partition table definitely appears to be corrupt. Notice the above partition overlapping error where the FAT32 partition overlaps with your extended partition. Also, fdisk previously didn't even see that FAT32 partition that testdisk found above. 

> ```
Disk /dev/sda - 160 GB / 149 GiB - CHS 19458 255 63
     Partition               Start        End    Size in sectors
* FAT16 >32M               0   1  1    11 254 63     192717 [DellUtility]
P HPFS - NTFS             12   0  1  1316 254 63   20964825
P HPFS - NTFS           1317   0  1  5172 254 56   61946633
L Linux                 5173   2  1 18557 254 60  215029896
L Linux Swap           18558   1  1 19129 254 42    9189096
L FAT32 LBA            19130 218 33 19457  21 20    5240832 [MEDIADIRECT]
```
It looks like testdisk figured out your correct partition table above, so when you get to the screen above, press "enter" to continue, and then select "write" to write the new partition table above to your HDD's MBR (Master Boot Record). Reboot, and see what happens when you boot Windows again. Probably Windows will still crash, but we need to know for sure. If Windows still crashes, go ahead and boot your Windows Install CD, and hopefully with a fixed partition table the install CD should work now; then run the chkdsk command on Windows from post #4. Let me know how it goes. :)

---

### Post by Lao_Tzu on 2008-10-03
Roger that. I'm going in. If I'm not back in thirty minutes... just wait longer.

If I'm not back in a day, it's because my computer is dead.

---

### Post by Lao_Tzu on 2008-10-04
Okay, I wrote the new Master Boot Record. Then I rebooted, and immediately got Grub Error 17. (I'm now writing from my g/f's computer.)

New development: this is hilarious, but it may be an improvement! I used the Ubuntu Live CD to reinstall Grub (a la [http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)). Then I rebooted and I got to the Grub menu.

At the Grub menu, grub couldn't find the partition of any of the linux options (it displayed the option, but said no (Error 17 - could not find partition) when I pressed enter on them) but I managed to boot windows! Amazingly.

So now all I have to do (somehow) is get the grub to find the Ubuntu partition again. i can access my ubuntu partition from Windows. Wondering how to do this...

P.S. I ran chkdisk from the Windows terminal... it went okay, I think. Stage 1 went fine. In Stage 2, it "deleted an index entry from index $0 of file 25" many times, but then got a grip and continued, exiting with: "errors found. chkdsk cannot continue in read-only mode". Scheduled a check for startup and restarted, but to no avail. Will probably have to do this using the WinXP Install CD, but - later. For now, I want to get GRUB to see Ubuntu.

---

### Post by Lao_Tzu on 2008-10-04
Here is what testdisk (run from the Ubuntu live CD) says about my disk:

```
Disk /dev/sda - 160 GB / 149 GiB - CHS 19458 255 63
Current partition structure:
     Partition                  Start        End    Size in sectors

 1 P FAT16 >32M               0   1  1    11 254 63     192717 [DellUtility]
 2 * HPFS - NTFS             12   0  1  1316 254 63   20964825
 3 P HPFS - NTFS           1317   0  1  5172 254 56   61946633
 4 E extended LBA          5173   0  1 19457 254 63  229488525
 5 L Linux                 5173   2  1 18557 254 60  215029896
   X extended             18558   0  1 19129 254 42    9189159
 6 L Linux Swap           18558   1  1 19129 254 42    9189096
   X extended             19130 217  1 19457  21 20    5240927
 7 L FAT32 LBA            19130 218 33 19457  21 20    5240832 [MEDIADIRECT]

```

and here are the results of fdisk -l

```
ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x90000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1          12       96358+   6  FAT16
/dev/sda2   *          13        1317    10482412+   7  HPFS/NTFS
/dev/sda3            1318        5173    30973316+   7  HPFS/NTFS
/dev/sda4            5174       19458   114744262+   f  W95 Ext'd (LBA)
/dev/sda5            5174       18558   107514948   83  Linux
/dev/sda6           18559       19130     4594548   82  Linux swap / Solaris
/dev/sda7           19131       19458     2620416    c  W95 FAT32 (LBA)

```

---

### Post by Lao_Tzu on 2008-10-04
Do you think there is hope, or should I format my whole HDD and re-install WinXP and Ubuntu? It would be a mission, but it might be quicker. I have all my documents and program install files backed up.

---

### Post by tangibleorange on 2008-10-04
> **Lao_Tzu said:**
> Do you think there is hope, or should I format my whole HDD and re-install WinXP and Ubuntu? It would be a mission, but it might be quicker. I have all my documents and program install files backed up.

to be honest, if you're willing to reinstall, i think its the best option. the partitions are a mess, mostly owing to that stupid mediadirect dell partition (What is that anyway?). if you do decide to reinstall, install XP first and then ubuntu - this way GRUB installs after NTLDR, allowing you to boot both.

---

### Post by bigken on 2008-10-04
the media direct is probably a recovery partition

---

### Post by Lao_Tzu on 2008-10-04
Yeah, I think it is a recovery partition.

Thanks for your help, everyone. I'm taking a few hours' break from this. Then I'll check back here to see if anyone has a caution or another idea that might be better than reformatting and starting from scratch. If nothing, I'll redo my whole system after that.

In that process I think I'll get rid of the recovery partition if possible, integrating it with the rest of the HDD.

Thanks again for the help and feedback!

---

### Post by caljohnsmith on 2008-10-04
Actually that is great news; getting Grub to boot Ubuntu may actually be really easy now, since it looks like your partition table is in good shape again. From your original post, Ubuntu was on sda6 when you had that erroneous "unknown" sda5 partition, but now Ubuntu is sda5, which is why I think you are getting the Grub error.

So on start up, when you get the Grub menu, select Ubuntu, hit "e" to edit it, select the line that says "root (hd0,5)", press "e" to edit it, change it to "root (hd0,4)", press return to save the change, then press "b" to boot. Based on the info you gave, I think that should be all it takes. If not, let me know what Grub error it gives or what happens. If it works, you'll need to make the change permanent by changing your menu.lst when you get into Ubuntu:
```
gksudo gedit /boot/grub/menu.lst
```
Change all the Ubuntu entries to use (hd0,4), and also change the line that says "#groot=(hd0,5)" and make it "#groot=(hd0,4)". Let me know how it goes or if you run into problems. :)

---

### Post by Lao_Tzu on 2008-10-04
Awesome! Thanks, caljohnsmith, that worked perfectly. :D I'm back in my warm, safe Ubuntu OS and I made those changes to menu.lst without a hitch.

The 'other' Windows option in the grub is this one, which still targets (hd0,4). Chances are I'll never use it, but I wonder what change (if any) I should make to this entry in menu.lst:

```
# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda5
title		Microsoft Windows XP Embedded
root		(hd0,4)
savedefault
makeactive
chainloader	+1
```

I still think my partitions look a bit weird, though! Am I wrong, or is this likely to cause problems in future?

```
patrick@Patrick:~$ sudo fdisk -l

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x90000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1          12       96358+   6  FAT16
/dev/sda2   *          13        1317    10482412+   7  HPFS/NTFS
/dev/sda3            1318        5173    30973316+   7  HPFS/NTFS
[COLOR="Red"]/dev/sda4            5174       19458   114744262+   f  W95 Ext'd (LBA)
/dev/sda5            5174       18558   107514948   83  Linux[/COLOR]
/dev/sda6           18559       19130     4594548   82  Linux swap / Solaris
/dev/sda7           19131       19458     2620416    c  W95 FAT32 (LBA)
```

I would deduce from this that /dev/sda4 has effectively shuffled off this magnetic coil (since it begins at 5174 and ends at the very last cylinder, overlapping with sda5, 6, and 7 along the way). I could be wrong, of course. Illumination welcome, as always.

I'd also love to find out the technical details of what these numbers mean, so maybe I can self-diagnose similar problems in future. Do you know of any website that explains these details in a "for dummies" kind of way?

---

### Post by caljohnsmith on 2008-10-04
That's great news that both Windows and Ubuntu boot OK now, Lao_Tzu. :) Since your Windows partition is sda2, you can definitely get rid of that "Microsoft Windows XP Embedded" entry in menu.lst since it points to (hd0,4) which is sda5, or your Ubuntu partition. In case you haven't yet learned how Grub's numbering works, you just have to remember that everything starts with 0 and not 1:
```
(hdX,Y) --> X=HDD number Y=partition number
sda1 = (hd0,0)  1st HDD, 1st partition 
sda2 = (hd0,1)  1st HDD, 2nd partition
sda3 = (hd0,2)  1st HDD, 3rd partition
sdb1 = (hd1,0)  2nd HDD, 1st partition
sdb2 = (hd1,1)  2nd HDD, 2nd partition
sdc1 = (hd2,0)  3rd HDD, 1st partition
...etc.
```

And about your partition start/stop points from fdisk:
```
/dev/sda1               1          12       96358+   6  FAT16
/dev/sda2   *          13        1317    10482412+   7  HPFS/NTFS
/dev/sda3            1318        5173    30973316+   7  HPFS/NTFS
/dev/sda4            5174       19458   114744262+   f  W95 Ext'd (LBA)
/dev/sda5            5174       18558   107514948   83  Linux
/dev/sda6           18559       19130     4594548   82  Linux swap / Solaris
/dev/sda7           19131       19458     2620416    c  W95 FAT32 (LBA)
```
Note that sda4 is what is called an "extended" partition, meaning that it is merely a container for all your logical partitions (sda5, sda6, and sda7). That is why sda5 starts at cylinder 5174, which is the beginning of sda4, and also why sda7 ends on 19458, or the end of sda4. 

The main way to diagnose partition table problems is to first see if testdisk complains about your partition table (in your case it complained about overlapping partitions), and also to very carefully compare testdisk's results with fdisk's results to make sure they perfectly match. It is a little confusing though because fdisk starts cylinder numbering from 1, while testdisk starts at 0, so the start/stop points for partitions always are different by 1 cylinder when comparing testdisk with fdisk.

Anyway, glad your system is happy and healthy again (at least it seems to be now); cheers and have fun. :)

---

### Post by Lao_Tzu on 2008-10-04
Thanks very much for your help! :)

---

