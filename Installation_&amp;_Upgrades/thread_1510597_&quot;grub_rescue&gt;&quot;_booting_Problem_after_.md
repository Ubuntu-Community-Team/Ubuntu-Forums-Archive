---
title: "&quot;grub rescue&gt;&quot; booting Problem after upgrading from 9.10 to 10.4"
date: 2010-06-15
forum: Installation &amp; Upgrades
---

### Post by keamkaze on 2010-06-15
Hi,

I had windows 7     and I just wanted to try ubuntu and I am totally new to linux, however, I installed ubuntu 9.10 using wubi and it was fine when I boot it asks me for windows or ubuntu no problems. Then it asked me to upgrade to 10.04 I agreed and installed it. After installition restrting it gave me this grub thing I don't know what to do I googled it but I couldn't fix the problem please help I need my computer soon.

Also I tried but I couldn't boot from windows or ubuntu cd.

this may help: if I printed "ls"   it gives me "(hd0)" 

I attached a screenshot check attachment...

---

### Post by bcbc on 2010-06-16
Do you have an ubuntu CD you can boot in live CD mode (try without any changes)?

If so download and run the [bootinfoscript]("http://bootinfoscript.sourceforge.net/") and post the results back here.

---

### Post by bumanie on 2010-06-16
Important Note to Wubi (Windows Ubuntu) Users:
Grub2 updates in the spring of 2010 triggered a bug in the ntfs module causing Wubi boot failures. The solution to this boot problem was posted by Agostino Russo and is found in this Lucid Lynx LaunchPad Bug Report #477169, Post 210. The module causing the errors has been fixed and replacing the "wubildr" file in Windows permanently solves this problem. meierfra has kindly provided clear instructions on how to fix this problem at [http://sourceforge.net/apps/mediawik...lems:Wubi_9.10](http://sourceforge.net/apps/mediawik...lems:Wubi_9.10)

Taken from [here]("http://ubuntuforums.org/showthread.php?t=1195275").

---

### Post by darkod on 2010-06-16
First you need to boot into live mode with the ubuntu cd. You must be able to boot from the cd if cd-rom is before hdd in boot devices.

Then download the boot info script from my signature, run it and post the content of the results file as explained here:
[http://ubuntuforums.org/showpost.php?p=8844901&postcount=4](http://ubuntuforums.org/showpost.php?p=8844901&postcount=4)

---

### Post by keamkaze on 2010-06-16
I couldn't boot from cd I tried ubuntu 9.10 cd, windows 7, and even I made a bootable usb flash with ubuntu 9.10 but nothing
and any thing I could get is that I hear the cd moves but it doesn't boot I don't know how to boot it...

also, I couldn't log to my bios screen, there is no option there
nothing to get out of this screen and any thing I type it gives me "unknown command"

I tried to hold "shift" but no command list appears also "Esc" and nothing happens.

---

### Post by darkod on 2010-06-16
> **keamkaze said:**
> I couldn't boot from cd I tried ubuntu 9.10 cd, windows 7, and even I made a bootable usb flash with ubuntu 9.10 but nothing
and any thing I could get is that I here the cd move but it doesn't boot I don't know how to boot...

also, I couldn't log to my bios screen, there is no option there
nothing to get out of this screen and any thing I type it gives me "unknown command"

It sounds like it still trying to boot only from hdd.

You should be able to enter in BIOS with some key, depending on the computer. It could be Delete, F2, F10, or something like that. Usually it says when the computer starts, but you have to be fast and read it. If you don't manage to press it, never mind. Just restart again and then press the button because you will know which one once you read the message.

Or look in your computer manual if there is one.

---

### Post by bcbc on 2010-06-16
or search on google for your brand of computer and model e.g. bios boot options toshiba model#

---

### Post by keamkaze on 2010-06-16
I tried every button they don't work...

del, f1,f2,f3.....,f12

and nothing,  I know before there is a screen shows and in the bottom there is a list of command list of how to go to bios or setup and I was using them before. But now it disappeared there is nothing.

---

### Post by darkod on 2010-06-16
> **keamkaze said:**
> I tried every button they don't work...

del, f1,f2,f3.....,f12

and nothing,  I know before there is a screen shows and in the bottom there is a list of command list of how to go to bios or setup and I was using them before. But now it disappeared there is nothing.

I have no idea what happened, but BIOS is independent of any OS. Ubuntu or windows can't make the option to enter BIOS go away.

Without being able to boot from a cd and use ubuntu in live mode, there is not much you can do to fix this.

Even if you decide to reinstall windows or ubuntu you still need to boot from a cd to do that.

PS. If everything else fails, one option could be to unplug the hdd and connect it to another computer and try to fix it there. Even if that computer doesn't have ubuntu, as long as you can boot the ubuntu cd there you can load the live mode.

---

### Post by keamkaze on 2010-06-16
I checked the user manual it says press f8, I tried it but nothing
also it says press 0 to log to system recovery but nothing happened I keep getting this stupid grub screen I don't know how to deal with it.......

by the way this is my computer model:

Toshiba satellite L500-21T

Processor 	Intel CoreTMi3  330M Processor
(2.13GHz GHz , FSB:1066 MHz ,3MB 2nd level cache)
Wireless 	Intel Wireless Network Connection
Memory 	2.048 MB DDr3 RAM (1066 MHz) system memory
Storage Controller 	320 GB Hard Disk sata
Graphics 	ATI mobility Radeon HD 5145 Up To 2810MB Total Graphics Memory
Wireless technologies 	802.11 a/B/G/N integrated Wi-Fi TM ;bluetooth
Optical 	DVD Super Multi Drive (double layer)
Monitor 	15.6 Toshiba TruBrite® HD TFT High Brightness display         ATI mobility Radeon HD 5145 Up To 2810MB Total

---

### Post by keamkaze on 2010-06-16
Thanx Darko for your help I think I will do that now and I will be back in about two hours...

---

### Post by oldefoxx on 2010-06-16
You have just a very bief span of time when first powering up in which to press the bottons that take you to Setup or Boot options.  For some BIOSes these choices are clumped together, so it is just a single button involved.  Others make it two separate choices, so there are two buttons, one for each,

How do you know exactly when to press the button?  By experimenting.  Some screens tell you when to press, but this message is sometimes turned off in Setup to leave you with a clean screen while booting up.  Once you get in there, you can turn it back on if you want.  But getting in the first time is the tick.

Even with a dark screen, you may be able to perceive faint light changes.  'When you see such a change, that would be a good moment to press the key in queston.  When the OS screen comes up, that is too late.
And it will not be exactly when you turn power on either.  This is actually a final function of BIOS on its own before it passes control to the boot loader, and the timing therefore is very critical.  Remember, all the keys on the keyboard have other fuctions during normal use, and this is just where the BIOS checks to see if some specific code is passed to it via the keyboard before it lets go and hands matters over to the boot process.

You cannot sit and hold the button down either, because that sends acontinuous signal from the keyboard, and an earlier process in BIOS would see that as an indication that the keyboard is bad.

What sometimes works is to sit there as power comes up and just jab at the key and see it you can hit the moment right.  Do this several times, and you likely will eventually hit it at the right moment.  Watch the screen at thes ame time, and you may spot a visible clue of when the best time might be in the future.

All you really need to do once there is to ensure that the use of a CD ROM or better drive is included in the boot order, and comes before the first hard drive.  There may be other choices to consider as well, such as a floppy, 

These methods do work, but not fpor every PC.  With newere PCs, the Setup key is likely to be F2, and the boot choice options, if separate, may be F10.

---

### Post by keamkaze on 2010-06-16
I took my laptop hardisk and plugged it into other laptop then I boot to ubuntu 9.10 using a flash usb

then I did as you said and this is the result.txt content:
```

      Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #256 for /boot/grub.
 => Syslinux is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /Boot/BCD

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /Windows/System32/winload.exe /wubildr.mbr /wubildr

sda3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sda3 and 
                       looks at sector 1932584 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location. No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /ubuntu/winboot/wubildr.mbr /ubuntu/winboot/wubildr 
                       /ubuntu/disks/root.disk /ubuntu/disks/swap.disk

sda3/Wubi: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Mounting failed:
mount: wrong fs type, bad option, bad superblock on /dev/loop1,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so


sdb1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Fat32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x9d493175

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048       206,847       204,800   7 HPFS/NTFS
/dev/sda2             206,848   327,679,999   327,473,152   7 HPFS/NTFS
/dev/sda3         327,680,000   625,139,711   297,459,712   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 2062 MB, 2062548992 bytes
16 heads, 32 sectors/track, 7868 cylinders, total 4028416 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x0c2d62e7

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             32     4,028,415     4,028,384   6 FAT16


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/loop1       8276bdc7-e9f8-462e-904b-5495b725291a   ext4                                     
/dev/sda1        E25E6FE55E6FB0C9                       ntfs       ?????? BLKID Trash            
/dev/sda2        C23679E23679D83D                       ntfs                                     
/dev/sda3        925674FB5674E201                       ntfs                                     
/dev/sdb1        38B0-26FE                              vfat                                     

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sdb1        /cdrom                   vfat       (rw)
/dev/loop0       /rofs                    squashfs   (rw)
```

---

### Post by darkod on 2010-06-16
OK, from live mode do:

sudo apt-get install lilo
sudo lilo -M /dev/sda mbr

After the first command there will be warnings that will sound bad. Just ignore them, don't do anything they say. Just run the second command after.

You should be able to boot your windows after that.

---

### Post by keamkaze on 2010-06-16
it gives me this line and nothing happen after

0% [Connecting to archive.ubuntu.com (91.189.88.30)]


I am behind a university proxy, do you think that it is because of it!!!...
???

---

### Post by darkod on 2010-06-16
> **keamkaze said:**
> it gives me this line and nothing happen after

0% [Connecting to archive.ubuntu.com (91.189.88.30)]


I am behind a university proxy, do you think that it is because of it!!!...
???

Probably. You need internet access for that, forgot to mention that.

Alternatively boot with the win7 dvd and select the Repair This Computer option after the language selection screen. You might need to run it 3 times.

---

### Post by keamkaze on 2010-06-16
I boot from windows 7 cd, and choose repair start up status

and it finished and said every thing is ok, but when I restart I get the same problem: "grub rescue>"



about the internet access is it necessary to do that operation you told me to do, I mean I use it now but I think the terminal doesn't connect through the proxy...

Is there any way to do it without the internet access???

---

### Post by darkod on 2010-06-16
> **keamkaze said:**
> I boot from windows 7 cd, and choose repair start up status

and it finished and said every thing is ok, but when I restart I get the same problem: "grub rescue>"



about the internet access is it necessary to do that operation you told me to do, I mean I use it now but I think the terminal doesn't connect through the proxy...

Is there any way to do it without the internet access???

Yes, the internet is necessary because it needs to download the package and install it. But if you can connect online I think it should work from terminal too. Strange.

Did you run the win7 repair three times? It needs to be run few times to repair.

---

### Post by keamkaze on 2010-06-16
I did it 6 times...

I really don't know what to do...

someone said do this I will try it now:

""1-log to windows repair
  2-choose log in to DOS
  3-write:
  bootrec.exe/flxboot

  bootrec.exe/flxmbr

  then restart and every thing should be ok.""

however, I will try it and tell you the result.

---

### Post by keamkaze on 2010-06-16
Finally the problem SOLVED

actually the last step I mentioned worked perfectly!!!

and here is the way to fix it:

1-Boot from windows 7 CD.

2-Pick the language, then choose repair windows.

3-click on DOS system button(the last choice I think).

4-print these commands:
      
      bootrec.exe/flxboot
(when you press enter it should give you four choices, you should write the first one which is "FixMbr" and you should write it like this  " bootrec.exe/FixMbr " ) with capiral letter for F and M.



if you do that your boot screen should be fixed and it will be like before which in my case was choosing between Win7 and ubuntu)



Thanx every one who helped with this post.

Best Regards,
KEAMKAZE.

---

