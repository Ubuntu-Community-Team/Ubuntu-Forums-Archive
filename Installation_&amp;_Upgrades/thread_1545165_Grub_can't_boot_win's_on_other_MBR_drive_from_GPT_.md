---
title: "Grub can't boot win's on other MBR drive from GPT drive"
date: 2010-08-03
forum: Installation &amp; Upgrades
---

### Post by HarmCla on 2010-08-03
Hi guys,

I'm having a problem here.
My laptop has two internal HDD's (500GB each),
and grub can't boot operating systems from the other harddrive.

Before this problem showed up, I had the "No such device..." error,
and fixed it with this:
[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/604743](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/604743)
but now the errors are different, and I still can't boot windows from grub :cry:

I'll write things short, I believe it's easier for you to understand what I mean.

HDD0: MBR Partition Table:
   OS: Windows 7 and Windows XP Embedded
HDD1: GUID Partition Table:
   OS: Ubuntu Lucid, Mac OS X Snow Leopard and Leopard

When I boot from HDD0, Windows 7 boots just fine.
So this means nothing is wrong with windows 7 so I believe
windows xp is fine too, but I can't test that.

When I boot from HDD1, Grub2 pops up with every OS i have.
All operating systems on HDD1 boot fine,
but when I try to boot Win7, my laptop instantly reboots.
and when I try to boot winxp, i get the error:
> **Windows could not start because the following file is missing or corrupt:**
  **<Windows root>\system32\hal.dll.**
  **Please re-install a copy of the above file**What I've tried so far:
- I checked if the hal.dll exists, it does.
- I replaced it with another hal.dll file, nothing happened.
- I fixed the MBR of the winxp partition, nothing happened.

Since Windows 7 boots fine without grub,
I think it's another grub2 bug.

Has someone experienced this problem before?
Can someone help me with this?

---

### Post by oldfred on 2010-08-03
Yes:

[http://ubuntuforums.org/showthread.php?t=1405650](http://ubuntuforums.org/showthread.php?t=1405650)
Grub 2 malfunctions with a mixture of GPT and MS_DOS partition tables. But there is an easy fix, add to /etc/default/grub:
GRUB_PRELOAD_MODULES="part_msdos" meierfra.

[http://ubuntuforums.org/showpost.php?p=8822200&postcount=14](http://ubuntuforums.org/showpost.php?p=8822200&postcount=14)
For GPT sdc disk:
added the GRUB_PRELOAD_MODULES="part_msdos" to /etc/default/grub and ran grub-install /dev/sdc and it worked!
now see all the partitions on my IDE drives and boot from them too!!!!!
Fixed in Maverick:
[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/604743](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/604743)

---

### Post by HarmCla on 2010-08-03
> **oldfred said:**
> Yes:

[http://ubuntuforums.org/showthread.php?t=1405650](http://ubuntuforums.org/showthread.php?t=1405650)
Grub 2 malfunctions with a mixture of GPT and MS_DOS partition tables. But there is an easy fix, add to /etc/default/grub:
GRUB_PRELOAD_MODULES="part_msdos" meierfra.

[http://ubuntuforums.org/showpost.php?p=8822200&postcount=14](http://ubuntuforums.org/showpost.php?p=8822200&postcount=14)
For GPT sdc disk:
added the GRUB_PRELOAD_MODULES="part_msdos" to /etc/default/grub and ran grub-install /dev/sdc and it worked!
now see all the partitions on my IDE drives and boot from them too!!!!!
Fixed in Maverick:
[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/604743](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/604743)
Sorry, but I have done this already.
I also mentioned that in my original post.
That did the "No such partition" error disappear,
but I still can't reach Windows 7 nor Windows XP from Grub2.

---

### Post by oldfred on 2010-08-03
The hal error usually does not relate to hal, but to misconfigured boot.ini or bcd in 7 or vista that does not see XP correctly. If your windows boots directly it may have to do with drive numbering. When you boot grub on another drive the windows drive number changes (at least as far as grub is concerned). Usually grub adds a  drivemap command to make window still think it is first. Do you have windows as first or second drive?

Fix WinXP hal.dll 
[http://ubuntuforums.org/showthread.php?t=1410696](http://ubuntuforums.org/showthread.php?t=1410696)
Missing hal.dll not always missing, but other errors or boot.ini wrong partition
[http://members.iinet.net.au/~herman546/p15.html#hal.dll_is_missing_or_corrupt]("http://members.iinet.net.au/%7Eherman546/p15.html#hal.dll_is_missing_or_corrupt")
[http://pcsupport.about.com/od/findbyerrormessage/a/missinghaldll.htm](http://pcsupport.about.com/od/findbyerrormessage/a/missinghaldll.htm)
Error message: "Windows could not start because of a computer disk hardware configuration problem"
[http://support.microsoft.com/kb/314477](http://support.microsoft.com/kb/314477)

---

### Post by HarmCla on 2010-08-03
> **oldfred said:**
> The hal error usually does not relate to hal, but to misconfigured boot.ini or bcd in 7 or vista that does not see XP correctly. If your windows boots directly it may have to do with drive numbering. When you boot grub on another drive the windows drive number changes (at least as far as grub is concerned). Usually grub adds a  drivemap command to make window still think it is first. Do you have windows as first or second drive?

Fix WinXP hal.dll 
[http://ubuntuforums.org/showthread.php?t=1410696](http://ubuntuforums.org/showthread.php?t=1410696)
Missing hal.dll not always missing, but other errors or boot.ini wrong partition
[http://members.iinet.net.au/~herman546/p15.html#hal.dll_is_missing_or_corrupt]("http://members.iinet.net.au/%7Eherman546/p15.html#hal.dll_is_missing_or_corrupt")
[http://pcsupport.about.com/od/findbyerrormessage/a/missinghaldll.htm](http://pcsupport.about.com/od/findbyerrormessage/a/missinghaldll.htm)
Error message: "Windows could not start because of a computer disk hardware configuration problem"
[http://support.microsoft.com/kb/314477](http://support.microsoft.com/kb/314477)
Both windows installations (7 and xp) are on the first harddrive.
Grub is on the second harddrive.

---

### Post by HarmCla on 2010-08-03
> **HarmCla said:**
> Both windows installations (7 and xp) are on the first harddrive.
Grub is on the second harddrive.
YES!
Windows XP Embedded boots again! :D
Thanks to you!
Thank you thank you thank you!

The boot.ini file was indeed incorrect.

That only leaves Windows 7.
Perhaps something similar happened to Windows 7?
Hmm.. Windows 7 doesn't have a boot.ini file.

Oh, and, did I already thank you? ;)

---

### Post by oldfred on 2010-08-03
windows has BCDedit and there is EasyBCD that you can download. I do not have win7 and my only experience with either was trying to fix a repair USB that I was creating. 

[http://neosmart.net/wiki/display/EBCD/EasyBCD+Documentation+Home](http://neosmart.net/wiki/display/EBCD/EasyBCD+Documentation+Home)

[http://www.sevenforums.com/tutorials/2676-bcdedit-how-use.html](http://www.sevenforums.com/tutorials/2676-bcdedit-how-use.html)

And from grub you cannot boot both. Windows combines boots into one partition.
Multibooters, Pictures here worth 1000+ words
[http://www.multibooters.co.uk/multiboot.html](http://www.multibooters.co.uk/multiboot.html)

---

### Post by Computer Guru on 2010-08-06
There's actually a picture-by-picture tutorial for Windows 7 + Ubuntu with EasyBCD here: [http://neosmart.net/wiki/display/EBCD/Ubuntu](http://neosmart.net/wiki/display/EBCD/Ubuntu)

It's been recently updated for the 10.x release. 

btw, oldfred, what suburb are you from? I lived in the West Suburbs forever...

---

### Post by oldfred on 2010-08-06
I grew up in Plainfield but am now from Downers Grove. 

Are the EasyBCD more for using windows to boot Ubuntu. I tend to prefer grub. I downloaded the windows 7 repair and just for grins, installed it to a USB flash but it was so small I converted to grub2 and added a bunch of rescue CDs to also boot from same flash drive.

---

### Post by HarmCla on 2010-08-07
Ah, sorry you guys for not replying a while.
I have downloaded and used EasyBCD today,
but I messed up the bcd totally xD

When I booted straight from my HDD0 (Windows 7),
I got an error screen (not bluescreen).
Then I booted the windows 7 cd and used the command prompt there.
Here's what I did, to completely re-create the bcd:
```
bcdedit /export C:\BCD_Backup
c:
cd boot
attrib bcd -s -h -r
ren c:\boot\bcd bcd.old
bootrec /RebuildBcd
bootrec /FixMbr
bootrec /FixBoot
bootrec /ScanOs
bootrec /RebuildBcd
```I got it from [here]("http://support.microsoft.com/kb/927392").

Now, I have two Windows 7 entries when I do sudo update-grub.
**One that works**, :p
and the old one, probably. :-s

Now I only need to figure a way to remove that broken one.

But I'm very happy to be able to boot win7 from Grub2 again! :p

Thank you, oldfred, for the quick and helpful replies! :)
And thank you, Computer Guru, for the picture tutorial on EasyBCD.
(I should have watched it before messing with EasyBCD #-o)

I won't put a "SOLVED"-tag on this topic before I got rid of the faulty entry,
and then post the last things I did to solve that, if that's okay with you guys.
I know I can just cut it out of grub.cfg, but I would like to remove it so it
won't show up anymore after a kernel upgrade. :)

---

### Post by oldfred on 2010-08-07
If sudo update-grub is finding two entries, do you have two installs?

The workaround that I know is to copy the working windows entry into 40_custom and turnoff osprober so it does not find any entries.

I used drs305's command to limit ubuntu entries to two, turned off os_prober so it does not look for other systems and totally customized my 40_custom.
Copy the windows entries from this:
gedit /boot/grub/grub.cfg
Copy them to and edit :
gksudo gedit /etc/grub.d/40_custom

includes line to limit display to two
Grub 2 Title Tweaks Thread -drs305
[http://ubuntuforums.org/showpost.php...54&postcount=1](http://ubuntuforums.org/showpost.php...54&postcount=1)

I added this :
gksudo gedit /etc/default/grub:
GRUB_DISABLE_OS_PROBER=true
or
sudo chmod a-x /etc/grub.d/30_os-prober

If you want to know the details of what is installed where:

Boot Info Script courtesy of forum member meierfra
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste results.txt, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the post's menu and then paste the contents between the generated [ code][ /code] tags.

---

### Post by HarmCla on 2010-08-07
So, I'm having two Windows 7 entries, in grub2:
```
Windows 7 (loader) on /dev/sda1
Windows 7 (loader) on /dev/sda2
```
The sda1 entry doesn't work because Windows 7 is on sda2.
sda1 is a partition from my laptop's manufacturer to easily restore my system
to factory defaults.

I had once a Windows Vista (loader) on /dev/sda1,
(Windows Vista was my old OS)
and somehow it got away by doing some commands on the restore cd.

Hey, that's odd..
When I use the Boot Info Script, I see:
```
sda1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Vista: Fat 32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /boot/bcd
```
But I tried to delete /boot/bcd while on the restore cd,
it said that it couldn't find /boot/bcd. :confused:

...

And when I look into the drive while on Ubuntu, I find:
```
harm@Wildcat:~$ ls /media/PQSERVICE/boot
BCD              BCD.LOG2      da-DK  etfsboot.com  it-IT        nl-NL  sv-SE
BCD.Backup.0001  bootfix.bin   de-DE  fi-FI         ja-JP        pl-PL  tr-TR
BCD.Backup.0002  boot.sdi      el-GR  fonts         ko-KR        pt-BR  zh-CN
BCD.LOG          BootStat.dat  en-US  fr-FR         memtest.exe  pt-PT  zh-HK
BCD.LOG1         cs-CZ         es-ES  hu-HU         nb-NO        ru-RU  zh-TW
```

...

**YES!**

I moved the files
BCD; BCD.Backup.0001; BCD.Backup.0002; BCD.LOG; BCD.LOG1 and BCD.LOG2
to a folder on my desktop, ran sudo update-grub,
and Windows 7 (loader) on /dev/sda1 is gone!!!! :D:D

I'm so happy right now... :')

Thanks again, oldfred, you're a great helper on these forums!

---

### Post by oldfred on 2010-08-07
New installs of win7 have a separate 100MB boot/recovery partition. It seems repairs only fix the main install and then by pass the boot partition. Part of the reason for the boot partition is windows bitlocker encryption, the boot partition cannot be encrypted.

Not sure if your recover will work again. If you do not have a windows recovery disk I would download this just to have it. 

If your PC did not come with a complete Vista or Win7 installation CD, you can download a Recovery Disc at the following links:
Windows Vista/7 Recovery Disc - for repairs only
[http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/](http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/)
[http://neosmart.net/blog/2009/windows-7-system-repair-discs/](http://neosmart.net/blog/2009/windows-7-system-repair-discs/)
Vista will not repair XP (they create the boot sectors differently) but can run chkdsk.
[http://support.microsoft.com/kb/927392](http://support.microsoft.com/kb/927392)

---

### Post by HarmCla on 2010-08-07
Yeah, last time I tried that, it didn't work,
well, it worked partitially, but it couldn't get to the end.
But I remember it took a couple of attempts in the past to have it working.

I don't know how the recovery thing of my manufacturer works,
I have this 10GB partition, and I had to make 3 DVD's at the very first startup.

[QUOTE=oldfred]
New installs of win7 have a separate 100MB boot/recovery partition.[/QUOTE]
Oh, I didn't know that.

Well, I installed my Win7 by myself,
without that separate partition.
My cd didn't come with a vista cd. Nor a vista restore cd.
But I dow******d a vista one and 2 win7 one's.

One, last, off-topic question though:
Those discs you are referring to,
are they like the original repair tools ripped
off a full Windows cd, or are they different repair tools?

---

### Post by oldfred on 2010-08-07
From what I saw they seem to be the windows repair tools. I did download the win7 one just to see  (I only have XP) and it ran from the CD with the normal BCDedit and repair screens. I then copied it to a USB key but copy from linux did not work as it also needed the mbr and boot sector. fixboot & fixmbr did not seem to fix it, but following to full copy procedures from the repair console did work. I was then able to install grub2 to the flash drive and still boot the repair.

---

### Post by HarmCla on 2010-08-07
You run Windows XP, and you were able to
help me out with my Windows 7, you are a wise man ^^

Okay, thank you for the useful recovery tools.
I'm sure they'll be handy in the future x)

---

