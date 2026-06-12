---
title: "Grub multiboot problem with 3 OSs on 2 HDDs"
date: 2014-11-30
forum: Installation &amp; Upgrades
---

### Post by zoltan-poloskei on 2014-11-30
[COLOR=#000000]Hello there,[/COLOR]

[COLOR=#000000]I've got a little problem.[/COLOR]
[COLOR=#000000]I have 3 OSs installed on 2 HDDs:[/COLOR]

[COLOR=#000000]sda1 W7 Prof SP1,[/COLOR]
[COLOR=#000000]sda5 ubuntu 14.04.1[/COLOR]
[COLOR=#000000]sdb1 WinXP SP3.[/COLOR]

[COLOR=#000000]The first one was of course XP on my old HDD, then W7 on the first partition of my new SSD, then finally Ubuntu on the other partition of the SSD.
After install W7 the Windows Boot Manager showed up and could start the 2 systems (W7, XP) properly.
After install ubuntu (and many one-click-repair with Boot Repair) the Grub now shows up all three of them but it can only start ubuntu.[/COLOR]
[COLOR=#000000]If I choose Win 7, or XP (it is called "W7 on sdb1" by grub) it only beeps short, but nothing else happens.[/COLOR]
[COLOR=#000000]One-click-repair with Boot Repair doesn't help.[/COLOR]
[http://paste.ubuntu.com/9273192/](http://paste.ubuntu.com/9273192/)
[COLOR=#000000]If I remove the HDD (sdb) with WinXP and boot ubuntu and ran Boot Repair with recommended settings (one click), my grub is still not able to load Win 7 on sda1, but again no problem to load ubuntu on sda5.[/COLOR]
[http://paste.ubuntu.com/9299637/]("http://paste.ubuntu.com/9273192/")
If I use *Hiren's Boot CD* => *Grub4Dos* => *"find and load NTLDR of Windows NT/2K/XP"* I can start my XP on sdb1.
If I use *Hiren's Boot CD* => *Grub4Dos* => *"find and load BOOTMGR of Windows Vista/Seven"* I can even choose to start my XP on sdb1 (as *"earlier version of windows"*) or to start W7 on sda1.
If I remove the HDD (sdb with the XP on it) and use *Hiren's Boot CD* => *Grub4Dos* => *"find and load BOOTMGR of Windows Vista/Seven"* my W7 Professional loads automatically (no options to choose).
This workaround to start MS systems with Hiren's Boot CD (or USB) could be helpful to others with problems to load MS systems when grub fails, but how can I repair the grub to load the non-linux systems properly? 
[COLOR=#000000]Any help is much appreciated![/COLOR]

[COLOR=#000000]Thanks in advance!
[/COLOR]
[COLOR=#000000]Z[/COLOR]

---

### Post by oldfred on 2014-11-30
The bootmgr & BCD in your sda1 install is just your Windows 7 install.
The bootmgr & BCD in your XP install in sdb1 has in BCD both XP & Windows 7, it also has the ntldr to boot XP, but the partition boot sector specifies which boot loader to use and it has been changed to use bootmgr.

Use Boot-Repair's advanced mode and install a Windows boot loader to sdb and then use BIOS which should boot the Windows on sdb using bootmgr (Win7) not XP's ntldr.

Also make a Windows repair flash drive or CD.
       Windows 7 repair USB, Also Vista if service pack installed
[http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/](http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/)
[http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html](http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html)

 Make your own Windows repairCD (not vendor recovery):
[http://forums.techarena.in/guides-tutorials/1114725.htm](http://forums.techarena.in/guides-tutorials/1114725.htm)

If you can directly boot Windows using BIOS and choosing sdb drive, then we may need to manually add boot stanza's to grub's 40_custom. They will be similar to the one's grub automatically created and we may have to experiment on what may work.

Part of issue is Windows is particular about drive order. It normally is first drive & first partition. BIOS reports to boot loader what drive it boots from and when using grub it often swaps BIOS setting so Windows thinks it is booting from the correct drive. With your two installs, and both drives having Windows 7 boot loaders, I think grub is not quite configuring boot correctly. But do not know details enough that I can just specify one thing, we will have to experiment if you are willing to try a few things.

---

### Post by zoltan-poloskei on 2014-11-30
Thank you oldfred again!
Are you sure that I need to install with Boot Repair the Windows Boot Manager on the sdb (with XP on it)?
To me it seems that it is the HDD which already has it! :confused:
When I remove these HDD (sdb) and start W7 with the Hiren's workaround the WBM doesn't show up, W7 boots up.
Anyway I can't really understand why Boot Repair is not able to repair Grub if I remove the sdb (with XP on it) and have only 2 systems on 1 drive (although on 2 partitions)???
Or am I totally wrong somehow?

---

### Post by oldfred on 2014-11-30
With multiple drives, Boot-Repairs default seems to be to install grub to the MBR of every drive. I assume that is so users do not have to go into BIOS and set one drive as the boot drive. 

But with multiple drives and multiple installs better to have different boot loaders on each drive and set grub drive as default in BIOS. Then if issue with grub you still should be able to use one time boot key often f10 or f12 to choose system to boot or go into BIOS and choose.

This was the last summary report & shows grub in both MBR.
```

 => Grub2 (v2.00) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for (,msdos5)/boot/grub.
 => Grub2 (v2.00) is installed in the MBR of /dev/sdb and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location.


```

Since your Windows 7 boot files, particularly BCD in sdb has both installs, it has to be the newest boot files. Windows normally adds all other Windows systems to BCD and typically only one NTFS partition with boot flag on the drive set as boot in BIOS is where bootmgr & BCD are stored. It overwrites the XP boot with the Windows 7 boot. Not sure how you installed BCD in sda, but that it works is good.

Lots of details on how Windows boots, but just reviewing pictures helps understand process.
 Pictures here worth 1000+ words - Vista but all Windows with BIOS/MBR
[http://www.multibooters.co.uk/articles/windows_seven.html](http://www.multibooters.co.uk/articles/windows_seven.html)
[http://www.multibooters.co.uk/multiboot.html](http://www.multibooters.co.uk/multiboot.html)

---

### Post by zoltan-poloskei on 2014-12-01
Thank you oldfred helping me!
I've done with Boot Repair what you recomended:
[https://drive.google.com/file/d/0B_Kv8cOSdpabUVg2OGZMcTJvck0/view?usp=sharing](https://drive.google.com/file/d/0B_Kv8cOSdpabUVg2OGZMcTJvck0/view?usp=sharing)
But no luck. :(
[http://paste.ubuntu.com/9334448/](http://paste.ubuntu.com/9334448/)
If I set in BIOS sdb to boot from the same thing happens (short beep, nothing else) but this time no choosing options by GRUB of course.
Anyway the same error-beep-sound could be heard as if I'd choose in sda's grub one of the windows OSs (XP or W7).
By the way BIOS...
I've got a very-very old ASUS M6N laptop from the year 2004, if this matters...

---

### Post by oldfred on 2014-12-01
Some of the old BIOS did not boot from a second drive. But usually that was a misconfigured jumpers or using 40 conductor cables, not the 80 conductor cables required for cable select. Very old system only had primary master and jumpers/BIOS made that the only boot drive.

That it does not boot from sdb may just be that the old XP will not boot? And that could be because it was converted to the Windows 7 boot partition that uses bootmgr not ntldr?

Using same process install the Windows boot loader to sda, and boot Windows. I expect that to work if Hirens can boot it.
Make a Windows 7 repairCD or flash drive.

       Make your own Windows repairCD (not vendor recovery):
[http://forums.techarena.in/guides-tutorials/1114725.htm](http://forums.techarena.in/guides-tutorials/1114725.htm)


   Windows 7 repair USB, Also Vista if service pack installed
[http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/](http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/)
[http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html](http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html)

We will run a set of repairs on each Windows install. In effect convert XP to stand alone boot so grub can directly boot it. And run repairs on Windows 7. Sometimes just a chkdsk fixes things or an update to BCD or boot sectors. My old XP would boot (but 5 min), but grub would not boot it. Ran chkdsk. Then Windows booted faster (3 min) and it would boot from grub.

---

### Post by zoltan-poloskei on 2014-12-01
Thanks but I think if I install Win Boot Loader on sda I can get only the status quo before installing ubuntu, can't I? At this time I had Windows Boot Manager with 2 options (W7 & XP as earlier version of windows) and it worked. Than I installed Ubuntu...
Right now booting from sdb does nothing but a short beep. No boot menu, no popups, no messages, nothing. Booting from sda shows up grub with options, but only ubuntu is working, choosing one of the windows options gets the short beep. With Hirens Boot I can load W7 and also XP.
I'm not an expert I have only feelings & suggestions but since Boot Repair was not able to fix the booting procedure of 2 systems on the same HDD I don't think that the problem is caused by the second HDD. Anyway I want to try to repair as you recommend, but before that (if I'll have time) I have to take serious precautions (eg. rescue usb) since 2 of the systems (ubuntu, W7) are really important for me...

---

### Post by oldfred on 2014-12-01
Please make sure you have good Windows repair disks, and Ubuntu live installer so you can fix things.
You should always have another way to boot and repair system.

Boot-Repair does not make Windows repairs except a few minor things & installing a Windows boot loader. 
Not sure why grub is not working but you can boot with Hiren's.

---

### Post by zoltan-poloskei on 2014-12-13
I've done a little experiment today. Since Boot Repair got updated I gave it a new try with recommended settings, but no luck, everything remained the same:
[http://paste.ubuntu.com/9506856/]("http://paste.ubuntu.com/9273192/")
Then I've tried to install GRUB legacy (0.97) with the advanced settings, but only to sdb:
[http://paste.ubuntu.com/950734/]("http://paste.ubuntu.com/9273192/")
If I booted from it I could see this text: >GRUB _< (_ is blinking).
I thought Boot Repair hasn't touched my GRUB on sda, but in fact booting from it led to this: >GRUB RESCUE<.
Than I was able to repair my boot only with a Boot-Repair-Disc-USB.
[http://paste.ubuntu.com/9507235/]("http://paste.ubuntu.com/9273192/")
Now I have the same old GRUB2 menu with a bootable Ubuntu on sda5 and 2 non-bootable-Windows-Versions (W7 on sda1, XP on sdb1).
Right now I really think that I can't stand more thrills and the advanced options of the Boot Repair are a way too risky for me.
At the moment I think I should live with my Hiren's-win-boot-workaround and perhaps wait for an update of Boot Repair to fix my problem... :o(
I'm just wondering how this very-very old Hiren's GRUB4DOS can find and load my 2 MS-OSes without any problem???

---

### Post by oldfred on 2014-12-13
It is not Boot-Repair.
Grub2's os-prober has always been better at finding Windows and creating correct boot stanza for booting Windows from grub. But it seems in your case the boot stanza is not correct.

       #Add menu entry to 40_custom
gksudo gedit /etc/grub.d/40_custom
The run this 
sudo update-grub

```
 menuentry " " {
set root= 
}


      # This method applies to Windows and to FreeDOS
menuentry &#8220;Windows XP on sdb1, by chainloader&#8221;  {
drivemap -s (hd0) (hd1)
set root=(hd0)
chainloader  (hd1,1)+1
 }

menuentry "Windows 7 (Chainloader) (on /dev/sda1)" {
insmod ntfs
set root=(hd0,1)
chainloader +1
}
    
menuentry "Windows 7 (bootmgr) (on /dev/sda1)" {
insmod ntfs
set root=(hd0,1)
ntldr /bootmgr     
}

```
Paste all three into 40_custom and then try booting each.

---

### Post by zoltan-poloskei on 2014-12-14
Done and WOW! :guitar:
Thank you, thank you, thank you oldfred, the 2 new rows at the end of the GRUB2 menu are working finally!!!
[IMG]https://drive.google.com/file/d/0B_Kv8cOSdpabanpMMXVKOUljRVU/view?usp=sharing[/IMG]
[https://drive.google.com/file/d/0B_Kv8cOSdpabanpMMXVKOUljRVU/view?usp=sharing](https://drive.google.com/file/d/0B_Kv8cOSdpabanpMMXVKOUljRVU/view?usp=sharing)
My last question:
If I make in future ubuntu major updates, do I have to do this "40_custom-thing" again, didn't I?

---

### Post by oldfred on 2014-12-14
Glad that worked. Not sure if I understand why the old (simplified) settings work and the os-prober versions did not.

Looks like there may be a typo somewhere in first boot stanza? Menu should now be showing "Windows on one line. Do {} match for each boot stanza?

You can turn off os-prober, so you do not have those incorrect settings. If you install a new system you can turn it back on or manually add settings.
 #Turn off prober
gksudo gedit /etc/default/grub
#Add this line
GRUB_DISABLE_OS_PROBER=true
#update grub menu after any change
sudo update-grub


Only if you reinstall, otherwise 40_custom should not get replaced. 

But any system file in /etc that I manually edit, I copy into a folder in my /home as then my backup procedure of /home will include that. Most suggest backing up /etc and you probably should, since most of those files are auto created and if installing a totally new version may need updated settings to work correctly. So I do not restore all of /etc, but have copies so I can find my settings if need be.

---

### Post by zoltan-poloskei on 2014-12-15
I don't know much about coding, but in your code there are two type of "-s and the first one with Windows XP seems not to work.
If I disable the os prober will I not lose the first row with the option of booting ubuntu?

---

### Post by zoltan-poloskei on 2014-12-15
Well, that's really interesting. I've corrected the "-s before and after the Windows XP in 40_custom, and got this:
[https://drive.google.com/file/d/0B_Kv8cOSdpabam1mT3ZNaG81YXc/view?usp=sharing](https://drive.google.com/file/d/0B_Kv8cOSdpabam1mT3ZNaG81YXc/view?usp=sharing)
Ubuntu works,
Windows 7 loader sda1 not working, only beeps once (as before),
Windows 7 loader sdb1 not working, only beeps once (as before),
Windows XP on sdb1 not working only a blinking "_",
Windows 7 chainloader boots W7 directly,
Windows 7 bootmgr boots W7 directly.

As far as I can remember with the "wrong" codes and the last option I could start MS boot manager where I could choose from "earlier version windows" and "W7", and both of them worked.
But anyway it is not a big issue if I can boot XP only with Hiren's grub4dos, since I use it rarely.
Thanks again!

---

### Post by oldfred on 2014-12-15
The os-prober only looks for other installs. So only the first two Windows entries will be eliminated.

The drivemap -s is to swap drive boot order. Windows has to see when booting that you booted from BIOS to the Windows drive. So when booting from another drive the swap is to tell Windows it booted from the drive it is installed into.

Another possible boot for Windows in sdb?

 menuentry "Windows " {

 drivemap -s (hd0) (hd1)
set root='(hd1,msdos1)'
ntldr /bootmgr

 }

---

### Post by zoltan-poloskei on 2014-12-16
Hey man, you're right again! If I booted from sdb the windows boot manager in fact showed up and I could also start the good old XP.
Bytheway your last menuentry is just soooo prrrrrrrrrrrrfect that I don't need the other ones anymore!
[https://drive.google.com/open?id=0B_Kv8cOSdpabempnTktsbkQ5bUU&authuser=0](https://drive.google.com/open?id=0B_Kv8cOSdpabempnTktsbkQ5bUU&authuser=0)
With this short code I can now boot from sda into anyone of the 3 systems (ubuntu / W7 or XP via windows boot manager) and from sdb into ubuntu and W7!!!
This is the solution I've been looking for months!!! \\:D/
Thank you, pls keep up the good work and merry X-mas!
Cheers!

---

### Post by oldfred on 2014-12-16
Glad that worked. :)

---

