---
title: "Ubuntu doesn't boot after dual boot install with Win 10 on Dell xps 15 9550"
date: 2020-07-26
forum: Installation &amp; Upgrades
---

### Post by crazybear on 2020-07-26
I have tried  many things and followed many 'recepies' others have suggested, but it only boots back to Win 10 although I can see that a new sector is there. 
Here is the report on the grub/boot situation - can someone tell me what needs to be done?! Many thanks in advance.

[https://paste.ubuntu.com/p/cB3jx5chtT/](https://paste.ubuntu.com/p/cB3jx5chtT/)

most of this is Greek to me, but I do notice there are 2 Win 10 OS systems listed and there should only be one!

---

### Post by ubfan1 on 2020-07-26
With grub in the MBR, but no /EFI/ubuntu/... files in your EFI partition, I'd guess you did a legacy install of Ubuntu on a Windoes UEFI machine.  How the install media boots (legacy vs. UEFI) is how the install is made.  How did you create the install media?  What choices in your BIOS/UEFI settings have you made for legacy/csm/UEFI mode preferences?

---

### Post by oldfred on 2020-07-26
Generally you do not want to mix UEFI & BIOS/Legacy/CSM boot modes. 
Since Windows is in UEFI boot mode, you should install Ubuntu in UEFI boot mode.
You do not have to reinstall, but just install the UEFI version of grub2 to replace the BIOS version of grub.

If you boot Ubuntu live installer in UEFI boot mode & rerun Boot-Repair it should offer to install the UEFI version of grub. You can do it manually, but often easier to use Boot-Repair.

Shows installer with screen shots. Both BIOS purple accessibility screen & UEFI black grub menu screen
 [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

Also make sure Windows fast start up is off.
Fast Start up off (always on hibernation), note that Windows turns this back on with updates, SHIFT + Shut down button
[http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472](http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472)
[http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html](http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html)
[http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html](http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html)

---

### Post by crazybear on 2020-07-27
> **ubfan1 said:**
> With grub in the MBR, but no /EFI/ubuntu/... files in your EFI partition, I'd guess you did a legacy install of Ubuntu on a Windoes UEFI machine.  How the install media boots (legacy vs. UEFI) is how the install is made.  How did you create the install media?  What choices in your BIOS/UEFI settings have you made for legacy/csm/UEFI mode preferences?


Your questions are perhaps a bit beyond my understanding them 100%. In this Dell BIOS under 'boot sequence' one can choose Legacy or UEFI. UEFI has always been checked and Legacy has not been checked. However, in 'Advanced Boot Options' there are [confusingly to me] three options: Enable Legacy Option ROMs; Enable Attempt Legacy Boot; and Enable UEFI Network Stack. When I did the install the first and last [as I listed them] were checked. I just unchecked 'Enable Legacy Option ROMs'...but I do NOT understand what all that means. Did I do the correct thing now and the wrong thing before. There is a written explanation, but it makes no sense to me.

---

### Post by crazybear on 2020-07-27
> **oldfred said:**
> Generally you do not want to mix UEFI & BIOS/Legacy/CSM boot modes. 
Since Windows is in UEFI boot mode, you should install Ubuntu in UEFI boot mode.
You do not have to reinstall, but just install the UEFI version of grub2 to replace the BIOS version of grub.

If you boot Ubuntu live installer in UEFI boot mode & rerun Boot-Repair it should offer to install the UEFI version of grub. You can do it manually, but often easier to use Boot-Repair.

Shows installer with screen shots. Both BIOS purple accessibility screen & UEFI black grub menu screen
 [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

Also make sure Windows fast start up is off.
Fast Start up off (always on hibernation), note that Windows turns this back on with updates, SHIFT + Shut down button
[http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472](http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472)
[http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html](http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html)
[http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html](http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html)

Again, Thanks, but your speaking over my head. I have NO idea how to control/turn on/off 'Windows fast start up'..... The closest I see [maybe] is 'Fastboot' which has three choices Minimal, Thourough, Auto. It was on Thourough before - on a guess and only a guess, I just moved it to Auto as it says 'allows BIOS to decide initialization during boot'. Again, it would be helpful for some feedback...as I'm flying blind here. There is also 'extend BIOS Post time' and no idea what that is. 

Wen you say 'run boot-repair' you mean go into the 'try Ubuntu' install disk and just run the command 'boot-repair' and it should fix it? This is on a MVe M.2 SSD and there are a hell of a lot of small and strange partitions besides the three I know of from normal disks. I'll give it a shot......but feedback would be helpful if I don't succeed. I'm changing several things which always makes one nervous - especially when one doesn't understand what one is doing.

OK, I noticed in the edit window that one tutorial you posted was how to turn off fast start up and think I did so. But when I went and selected the install drive for Ubuntu the text was SO small I had to put on magnifying glasses...and when I pushed the enter when it was at 'Ubuntu', it did nothing - black screen...nothing happened, unlike in the past...so I think I've made too many changes, but do NOT know which. Help kindly appreciated.

Perhaps associated with this, I have an external drive [it has Win 10 on it] but can not when it is plugged in even get it to show up as an option to boot to....strange. If I can, I might leave it as the Windows 10 drive [which I don't use much] and have the entire other drive be Ubuntu...haven't decided...but even if I just want to use it for data storage, I need it to be recognized.....but let's try dual booting first..... but I'm at an impass already.
Question: Under UEFI BOOT there are now three options: the MVe M.2 disk, the USB flash drive and 'Windows Boot Manager'. What is and why would one want to use Windows Boot Manager?

---

### Post by crazybear on 2020-07-27
Now, the Ubuntu install flash drive [with 20.04] will NOT start. I inserted an install flash drive with 18.04 and put in the commands to run boot-manager, but it froze. Very frustrating. The machine is as confused as I at this point. I still do not understand why the Dell won't recognize the bootable external drive...it did once [yesterday], but not now...... In boot-manager should I choose the 'most common' repair choice. I noticed in the advanced there was something about deleting and re-installing the Windows 10 boot...but left it alone.

---

### Post by oldfred on 2020-07-27
Windows only boots from internal drives. It is designed & licensed for only one system, so cannot be on a portable drive that you can then use on other systems.

You ran the Boot-Repair report as part of first post, so I thought you new how to add it to live installer.

I posted three similar links on how to turn off fast start up in Windows. Windows also turns that back on with some updates and then you have to boot Windows from UEFI boot menu as grub only boots working Windows.

What brand/model system?
What video do you have?
If you have nVidia, you may need nomodeset or the safe graphics boot option now available on the newest versions of Ubuntu.
If newer system, best to only use newest Ubuntu or 20.04 as Dell does release drivers, but it can take a bit before included in a kernel or drivers and even longer to be in a distribution like Ubuntu. 

Did you look at link in my signature?

[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair) & 
[https://sourceforge.net/p/boot-repair/home/Home/](https://sourceforge.net/p/boot-repair/home/Home/)

---

### Post by crazybear on 2020-07-27
> **oldfred said:**
> Windows only boots from internal drives. It is designed & licensed for only one system, so cannot be on a portable drive that you can then use on other systems.

You ran the Boot-Repair report as part of first post, so I thought you new how to add it to live installer.

I posted three similar links on how to turn off fast start up in Windows. Windows also turns that back on with some updates and then you have to boot Windows from UEFI boot menu as grub only boots working Windows.
What brand/model system?
What video do you have?
If you have nVidia, you may need nomodeset or the safe graphics boot option now available on the newest versions of Ubuntu.
If newer system, best to only use newest Ubuntu or 20.04 as Dell does release drivers, but it can take a bit before included in a kernel or drivers and even longer to be in a distribution like Ubuntu. 

Did you look at link in my signature?


[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair) & 
[https://sourceforge.net/p/boot-repair/home/Home/](https://sourceforge.net/p/boot-repair/home/Home/)


OK, some good progress... I am watching the new Ubuntu [20.04]  and it seems to be working fairly well....some glitches and I have read  there are quite a few changes of settings and drivers that need to be  made...but it is working. I haven't tried to boot to the Win 10 on that  disk again yet. So, Win 10 won't work on a external drive? That is NO  problem, I was going to erase it and use it for storage, but it doesn't  seem to be recognized. I have my desktop with an older Ubuntu here....is  there some way I can use aptik and transfer lots of things from the old  Ubuntu to the laptop?! Doing it with even very large zip drives would  be problematic and I don't have any really big ones. I have a USB-C ver  2.1 to USB cable - can that be made to transfer between two Ubuntus? 

Here is the results of the grub-repair report: [URL="http://paste.ubuntu.com/p/ZmtfR2vdxK/"]http://paste.ubuntu.com/p/ZmtfR2vdxK/
[/URL]Seem to be a lot of problem listed in the above report!!!! ;-(
It also suggested I add a line to Win 10s command line: /set (bootmgr) PATH \EFI\Ubuntu\shimx64.efi
My question is will this help or be necessary and what do I put in place of bootmgr and path?

Thanks  very much. I had to try several times for some strange reason...but it  worked the last time......Ubuntu seems stable if not yet perfect..I see  some minor problems so far...nothing major yet.

I've got a four year old Dell XPS 15 9550 with 4K touch screen i7 processor and NVidea graphics card, 1TB MVe M.2 that is VERY fast - will I need a swap space? How does one tell or are they for the older HDD? This is a great laptop!.....the ONLY down point thus far is the battery doesn't last long on a charge.....I've got to find some settings to maximize that....... I do not use Windows much.....but it is good to have it there....I'd use it about 1-2% of the time.

---

### Post by ubfan1 on 2020-07-27
That shimx64.efi suggestion was in case you are using the Windows bootloader, but you aren't, so ignore it.  The only USB to USB transfers I've done have been from an android tablet, so I'll let others suggest the best way to do that.

---

### Post by pbear42 on 2020-07-27
Not sure I can help with the overall installation, but will mention one little tip which might be useful.  As mentioned, it's important you boot the live session in UEFI mode.  To make sure you have, open Terminal and run [COLOR=#ff0000]ls /sys/firmware[/COLOR] (ls=list).  The response will be three words or four (they're sub-directories).  If one of them is **efi**, you're good to go.

---

### Post by ubfan1 on 2020-07-27
See  [https://askubuntu.com/questions/905926/is-data-transfer-between-2-ubuntu-machines-possible-via-usb-cable](https://askubuntu.com/questions/905926/is-data-transfer-between-2-ubuntu-machines-possible-via-usb-cable)  Be careful, note the warnings at the end.  The ethernet cable might be easier, and probably does not even need a crossover cable these days (depending upon how old your machines are).

---

### Post by crazybear on 2020-07-27
I celebrated too early!....after turning off computer and turning it back on, I can only boot into Win 10 again, even though Ubuntu is set to be the first boot option. Suggestions appreciated oldfred - or anyone else. I can't see running grub-repair every time I want to get into Ubuntu........

By the way, I did fix the BIOS so that the external drive is now recognized. Other than that, I'm back to where I was before. Ubuntu 20.04 is there for sure....but doesn't want to boot. I don't want to mess things up, so will wait for instructions from you gurus with grey hair. This old gray hair here is no guru.

---

### Post by oldfred on 2020-07-27
It looks like you have Windows fast start up still on.
It does turn it back on with updates, so it you turned it off, but Windows did an update, it may be back on.

You have grub installed to MBR of NVMe drive. That grub will only give errors, so never boot in legacy/BIOS/CSM boot mode.

UEFI install of Ubuntu looks ok. 
If you use f12 from UEFI does Ubuntu boot?
Not sure why you are getting Windows first or by default.

Have you updated UEFI from Dell?
Note that some setting may revert to defaults and some remembered. I keep a list as I change 7 or 8 settings typically on my system.  With old BIOS all settings were reverted to defaults.
And updated the SSD firmware?

Dell was one of the first to support UEFI updates from Linux. Is your system on the list?
[https://github.com/rhboot/fwupdate/blob/master/README.md](https://github.com/rhboot/fwupdate/blob/master/README.md)
[https://fwupd.org/lvfs/devicelist](https://fwupd.org/lvfs/devicelist) & 
[https://fwupd.org/vendorlist](https://fwupd.org/vendorlist)

---

### Post by ubfan1 on 2020-07-27
Your disk is gpt, so Windows is definitely installed in  UEFI mode.  Since you have grub installed for both legacy and UEFI, it's harder to tell which you boot, but I think the UEFI boot had a black rub backgound, and the legacy grub a purple (?).  Anyway, when you get to Windows, you might as well fix the unclean shutdown -- probably the fast-start option, which is under the Power options, advanced,hidden,(then you get the choice to make shutdown really shutdown and not hibernate).    Anyway, you should be able to get the EFI menu at power up, and select whether Windows or ubuntu (or the disk itself since it looks like grub too that bootx64.efi EFI/Boot/bootloader too).  From Ubuntu, efibootmgr can change your boot order, but I think that may also be done from your BIOS/UEFI setings.

---

### Post by crazybear on 2020-07-27
> **ubfan1 said:**
> That shimx64.efi suggestion was in case you are using the Windows bootloader, but you aren't, so ignore it.  The only USB to USB transfers I've done have been from an android tablet, so I'll let others suggest the best way to do that.

In the Dell BIOS there is a box to check Windows Bootloader and I don't know if I need  it or not. When I turned it off recently, I could not get into Ubuntu...but I did other things too, so don't know which one caused the problem - or none of them. When does one use the Windows Bootloader?!

---

### Post by crazybear on 2020-07-27
> **ubfan1 said:**
> Your disk is gpt, so Windows is definitely installed in  UEFI mode.  Since you have grub installed for both legacy and UEFI, it's harder to tell which you boot, but I think the UEFI boot had a black rub backgound, and the legacy grub a purple (?).  Anyway, when you get to Windows, you might as well fix the unclean shutdown -- probably the fast-start option, which is under the Power options, advanced,hidden,(then you get the choice to make shutdown really shutdown and not hibernate).    Anyway, you should be able to get the EFI menu at power up, and select whether Windows or ubuntu (or the disk itself since it looks like grub too that bootx64.efi EFI/Boot/bootloader too).  From Ubuntu, efibootmgr can change your boot order, but I think that may also be done from your BIOS/UEFI setings.

No offense, but that paragraph above is so full of information that his hard to parce and I really can get little useful information from it. Maybe try stating the various parts in simpler ways. Yes, everything is booting in UEFI mode. I do not boot legacy. More than that I can't respond to  what you said as I can't fully understand it.

---

### Post by crazybear on 2020-07-27
> **oldfred said:**
> It looks like you have Windows fast start up still on.
It does turn it back on with updates, so it you turned it off, but Windows did an update, it may be back on.

You have grub installed to MBR of NVMe drive. That grub will only give errors, so never boot in legacy/BIOS/CSM boot mode.

UEFI install of Ubuntu looks ok. 
If you use f12 from UEFI does Ubuntu boot?
Not sure why you are getting Windows first or by default.

Have you updated UEFI from Dell?
Note that some setting may revert to defaults and some remembered. I keep a list as I change 7 or 8 settings typically on my system.  With old BIOS all settings were reverted to defaults.
And updated the SSD firmware?

Dell was one of the first to support UEFI updates from Linux. Is your system on the list?
[https://github.com/rhboot/fwupdate/blob/master/README.md](https://github.com/rhboot/fwupdate/blob/master/README.md)
[https://fwupd.org/lvfs/devicelist](https://fwupd.org/lvfs/devicelist) & 
[https://fwupd.org/vendorlist](https://fwupd.org/vendorlist)

It is a Gigabyte new 1TB MVe M.2 and the internet says there is no firmware update available or even mentioned. Its very new. Made two months ago.
If I use F12 and go to Ubuntu and press enter, now, I only get three short lines of tiny text that do nothing or it boots into Windows - it doesn't boot into Ubuntu only into Windows. Ubuntu is listed as the default boot and it was working very well when I was working on it. No Fast Startup was not changed - it is off! I'm exhausted now. I'm in Europe and it is late.....will try more in the morning.

---

### Post by oldfred on 2020-07-27
From UEFI boot press escape before Dell screen ends to get to grub menu.
Try the recovery mode or second entry in grub menu.

---

### Post by pbear42 on 2020-07-27
> **crazybear said:**
> I do not boot legacy. 
Perhaps not intentionally, but you have booted in legacy mode at least twice, during installation and when running boot repair for the first report posted in the thread.

Not advising on substance, as too many cooks spoils the broth.  Will suggest this, though.  Boot Ubuntu one way or another, with the firmware boot options if you can, otherwise with the USB flash drive.  Run **[COLOR=#ff0000]efibootmgr -v[/COLOR]** and report the result.  This will tell whether the Ubuntu boot entry is still in NVRAM.

---

### Post by crazybear on 2020-07-27
OK, I found a way not mentioned here, but mentioned on a Dell Forum that seemed to help. There is a small button with no words next to it in BIOS boot sequence. When one pushes it. it lists [I forget all listed] a few things and one was EFI. I clicked on EFI and it listed about six things and two that looked familiar were the sequence that had been suggested to add to the Windows 10 command line and the other was something like \EFI\ubuntu\grubx64.efi

I chose that and named it Ubuntu and put it as first to boot. I let it reboot. It brought up a Ubuntu boot screen but the font size must be .003 and at my age only a magnifiying glass could I determine it was a standard Ubuntu boot screen. It didn't want to boot on it own, so I hit enter for Ubuntu and Ubuntu opened. How can I make those letters BIGGER??!! the size is insanely small!!! The four lines togther with space between them is less than .5 cm. 

As far as Legacy boot, yes earlier it was on, but NOT since I put in Ubuntu.

---

### Post by crazybear on 2020-07-27
**[COLOR=#ff0000]efibootmgr -v[/COLOR]**  got me this - interpretation????

```

BootCurrent: 0003
Timeout: 0 seconds
BootOrder: 0003,0001,0000,0002
Boot0000  Windows Boot Manager    HD(1,GPT,5f7dd662-4e83-48b2-ada8-7f591aa5bdd6,0x800,0xfa000)/File(\EFI\ubuntu\grubx64.efi)WINDOWS.........x...B.C.D.O.B.J.E.C.T.=.{.9.d.e.a.8.6.2.c.-.5.c.d.d.-.4.e.7.0.-.a.c.c.1.-.f.3.2.b.3.4.4.d.4.7.9.5.}...d................
Boot0001* ubuntu    HD(1,GPT,5f7dd662-4e83-48b2-ada8-7f591aa5bdd6,0x800,0xfa000)/File(\EFI\ubuntu\shimx64.efi)
Boot0002* UEFI: GIGABYTE GP-GSM2NE3100TNTD, Partition 1    HD(1,GPT,5f7dd662-4e83-48b2-ada8-7f591aa5bdd6,0x800,0xfa000)/File(EFI\Microsoft\Boot\bootmgfw.efi)..BO
Boot0003* Ubuntu 20.04    PciRoot(0x0)/Pci(0x1d,0x0)/Pci(0x0,0x0)/NVMe(0x1,64-79-A7-36-70-61-0A-08)/HD(1,GPT,5f7dd662-4e83-48b2-ada8-7f591aa5bdd6,0x800,0xfa000)/File(\EFI\ubuntu\grubx64.efi)
Boot0080* Mac OS X    PciRoot(0x0)/Pci(0x1d,0x0)/Pci(0x0,0x0)//HD(2,GPT,94231e40-23ac-4197-9ebe-f681b9589716,0x64028,0x1dcd6500)/VenMedia(be74fcf7-0b7c-49f3-9147-01f4042e6842,2f97dcea294ee04fb7f2d4dea93661c3)/File(\AB266C56-0437-4B08-9C21-A053870AE164\System\Library\CoreServices\boot.efi)
Boot0081* Mac OS X    PciRoot(0x0)/Pci(0x1d,0x0)/Pci(0x0,0x0)//HD(1,GPT,2d02e4c5-095f-48c1-a383-1381552396f0,0x28,0x64000)/File(\EFI\APPLE\UPDATERS\MULTIUPDATER\MultiUpdater.efi)S.m.c.F.l.a.s.h.e.r...e.f.i. .(.-.w.v. .-.L.o.a.d.D.i.r. .e.f.i.-.a.p.p.l.e.-.p.a.y.l.o.a.d.1.-.d.a.t.a. .-.n.o.r.e.s.t.a.r.t. .). ...
Boot0082* UEFI: PM951 NVMe SAMSUNG 512GB, Partition 1    HD(1,GPT,2d02e4c5-095f-48c1-a383-1381552396f0,0x28,0x64000)/File(EFI\Microsoft\Boot\bootmgfw.efi)..BO512
Boot008A* UEFI: PM951 NVMe SAMSUNG 512GB, Partition 2    HD(2,GPT,da51aa45-e81e-46f4-a673-14378c405ee6,0x109000,0x32000)/File(EFI\Microsoft\Boot\bootmgfw.efi)..BO

```

I note that the SSD is not Samsung, but Gigabyte....and 1TB not 512....the samsung was the original drive I replaced. And the person who sold the XPS to me had a hackintosh OS on it too....how is this old stuff possible as I just ran it now?

---

### Post by crazybear on 2020-07-27
Now, other than making the letters in Ubuntu Boot readable - they are NOT!, I have to find a way to use aptik to transfer much from my old Ubutu to the laptop. Sadly, I have not found any way at all. There must be a way...and why does dell not put a LAN connector on the damn laptop? My desktop doesn't have wifi.....it is going to have to be some cable of some kind. Any suggestions? It has a USB-C port, if that will help. I can NOT see doing it with 500 moves with a flash drive and I would not know where some of the data is stored, as aptik does.

---

### Post by oldfred on 2020-07-27
Your Dell does not have Ethernet port?
And you can connect Wi-Fi system to one with Ethernet if you have a router.

UEFI remembers installs, and often reset entry to something if drive is removed.
I suggest removing all entries you know are incorrect to avoid confusion.

# from liveDVD or flash booted in UEFI mode and use efibootmgr
sudo efibootmgr -v
The "-v" option displays all the entries so you can confirm you're deleting the right one, and then you use the combination of "-b ####" (to specify the entry) and "-B" (to delete it). Examples #5 is delete:, with Ubuntu you need sudo, others must be at root. some need all 4 hex chars, others only need significant digits
sudo efibootmgr -b XXXX -B
man efibootmgr
[http://linux.die.net/man/8/efibootmgr](http://linux.die.net/man/8/efibootmgr)
[http://linux.dell.com/cgi-bin/gitweb/gitweb.cgi?p=efibootmgr.git;a=blob_plain;f=README;hb=HEAD](http://linux.dell.com/cgi-bin/gitweb/gitweb.cgi?p=efibootmgr.git;a=blob_plain;f=README;hb=HEAD)
[http://software.intel.com/en-us/articles/efi-shells-and-scripting/](http://software.intel.com/en-us/articles/efi-shells-and-scripting/)

---

### Post by crazybear on 2020-07-28
No, it has no ethernet port! Stupid! It is, I assume, to be only by wifi and the USB-C port
I would not know how to remove entries from UEFI [I don't really even know what it is] and I'm not sure if I know all that no longer apply. some are obvious, others not.
Are there somekind of adapter that could add an ethernet port to the laptop?

---

### Post by crazybear on 2020-07-28
Ugh! It seems that Aptik no longer is available to install in a new Ubuntu!!! However, there are USB and USB-C to RJ45 adapters [expensive!]. Without Aptik, I'm not sure how I'd do what I want to do.....data transfer would be easy, but not programs and the data stored in those programs, etc.

---

### Post by crazybear on 2020-07-28
Perhaps I should make a new thread for this 'other matter', but I don't know how [but know one can] tell two Ubuntu computers to connect/talk/share with one another. I believe it can be done using LAN cables. I'd have to get a UCB-C to LAN adapter [about $50 and up!], but if it will work, it is worth it. I'd like to always be able to move things from one to another. Now it seesm Aptik is no longer available except for $$$, but he doesn't say if it will work on 20.04, but one assumes it would. If I have the package for aptik from 16.04, could I move it and set it  up and expect it to work in 20.04? I like supporting people, but I'm very poor and have not earned any money the last six months due to the pandemic. The XPS was a bargain and took the last of my money - and much needed, as my desktop will be packed away while I'm semi-homeless in the near future for some unknown time period.

---

### Post by oldfred on 2020-07-28
Posted exact commands & links to more info in post above on how to remove UEFI entries with efibootmgr.

Per this you have LAN connector:
[https://laptopmedia.com/laptop-specs/dell-xps-15-9550/](https://laptopmedia.com/laptop-specs/dell-xps-15-9550/)
> 
[LIST]
[*]Ethernet LAN
[*]Wi-Fi *802.11ac*
[/LIST]


---

### Post by crazybear on 2020-07-28
> **oldfred said:**
> Posted exact commands & links to more info in post above on how to remove UEFI entries with efibootmgr.

Per this you have LAN connector:
[https://laptopmedia.com/laptop-specs/dell-xps-15-9550/](https://laptopmedia.com/laptop-specs/dell-xps-15-9550/)

_**NO LAN port on this 9550 - NONE~! I wish it were true. I can buy a USB-C to LAN adapter for a pretty penny.**_
YES, Wifi, but my desktop doesn't have wifi, and setting it up I once tried long ago - took days and days....not going there. I'm doing it with an external drive.
I find the paucity of programs I'm used to from 16.04 that just are missing in 20.04 a problem.....but I'll survive - somehow. Many I love and use all the time have been shelved. I imagine I can get the ppa's and try to install and see if they work and are still supported.

---

### Post by pbear42 on 2020-07-28
Often in error, but never in doubt.  Good luck.

---

### Post by crazybear on 2020-07-29
Oh, my.....I'm an idiot and somehow made a mistake I have spent hours trying to undo and cannot. I'm not even sure of the correct terminology to explain. When I log into Ubuntu I see the proper name [I gave] for user name. However, when I open a terminal it is NOT the username I assigned - I don't know if I made the mistake or the computer did...likely me. I'm 70 and my vision is not great at that distance [close] and the text is small to tiny on the xps. the letters are the same, but not in the correct order. I created a false user: tempuser to try to correct, but it would not let me because one of the names [old or new] it said was using a process. I believe this is the reason I can look at the external drive and even open up things from inside it; I can move things into it, but I CAN NOT MOVE ANYTHING OUT OF IT. HELP!....Until I solve this one, my 'transfer' technique will not work. Thanks in advance.

---

### Post by crazybear on 2020-07-29
New Problem! Seems big and I'm stupped. I had added some new software and two different types of desktops. Now nothing with boot....not Windows and not Ubuntu. I tried about six times repair-boot and sometimes it would not run - just freeze. The last time it seemed to run, but gave strange messages and I think there is no grub now. Here is the file: [http://paste.ubuntu.com/p/h8JrMfkKVd/](http://paste.ubuntu.com/p/h8JrMfkKVd/)
HELP! This is getting very frustrating.....things work for a while, then collapse totally.

---

### Post by oldfred on 2020-07-29
It looks like at one time you installed in BIOS boot mode as you have a bios_grub partition.
Be sure to always boot in UEFI mode.
That should be a default setting for your actual installs, but the flash drive installer will normally have two choices, one UEFI and one CSM/BIOS/Legacy. Only use UEFI option.

You have Windows fast start on. Windows turns that back on with updates, so even if you turned it off before, you have to turn it off again.
Grub will not boot Windows with fast start as that sets hibernation flag. Also if Windows has other issues like needing chkdsk, grub will not boot it.
But then you should always be able to directly boot from UEFI boot menu, f12 with most Dell systems. If still issues, those are Windows issues, not related to grub or Ubuntu. 
Once fast start up is off, grub should then boot Windows.

Fast Start up off (always on hibernation), note that Windows turns this back on with updates, SHIFT + Shut down button
[http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472](http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472)
[http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html](http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html)
[http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html](http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html)

Your Ubuntu entries looks ok for booting, but then may be graphical related.
Can you  get grub menu?
From UEFI Dell screen, press escape key near end of Dell logo showing. You should get grub menu.
If too quick, you may have UEFI fast start up on and need to turn that off.  Sometimes you do have to try more than once or press escape more than once.

From grub menu then try booting recovery mode, second entry in grub menu.

---

### Post by pbear42 on 2020-07-29
> **crazybear said:**
> New Problem! Seems big and I'm stupped. I had added some new software and two different types of desktops.
Piling on more stuff when you're trouble shooting is bad strategy.  At this point, probably nothing will work except to start over and be more careful next time.

---

### Post by crazybear on 2020-07-30
> **oldfred said:**
> It looks like at one time you installed in BIOS boot mode as you have a bios_grub partition.
Be sure to always boot in UEFI mode.
That should be a default setting for your actual installs, but the flash drive installer will normally have two choices, one UEFI and one CSM/BIOS/Legacy. Only use UEFI option.

You have Windows fast start on. Windows turns that back on with updates, so even if you turned it off before, you have to turn it off again.
Grub will not boot Windows with fast start as that sets hibernation flag. Also if Windows has other issues like needing chkdsk, grub will not boot it.
But then you should always be able to directly boot from UEFI boot menu, f12 with most Dell systems. If still issues, those are Windows issues, not related to grub or Ubuntu. 
Once fast start up is off, grub should then boot Windows.

Fast Start up off (always on hibernation), note that Windows turns this back on with updates, SHIFT + Shut down button
[http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472](http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472)
[http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html](http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html)
[http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html](http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html)

Your Ubuntu entries looks ok for booting, but then may be graphical related.
Can you  get grub menu?
From UEFI Dell screen, press escape key near end of Dell logo showing. You should get grub menu.
If too quick, you may have UEFI fast start up on and need to turn that off.  Sometimes you do have to try more than once or press escape more than once.

From grub menu then try booting recovery mode, second entry in grub menu.

Thank you, but confusing answers. First, I have NEVER seen any choice in install from an Ubuntu install disk. I never see but one choice 'Install Ubuntu xx.04'. I ONLY installed the one time - not again - and everything was working well...so your 'choice' 'two ways' comment is confusing and I don't know what it means. I would not know how to [or if] I installed in BIOS mode - but that the Ubuntu was working well for many days should rule that out logically - no? Again, I have NEVER seen any option of how to install.

Fast start was off and I have not been in Windows for it to update. How can it update if it is not on? Also to turn off fast start up one MUST be able to boot into Windows. I can neither boot into Windows NOR Ubuntu. I can boot to NOTHING....and I'm trying not to have to start all over again and consider the last week lost [I have to go on vacation with this laptop soon and time is desperately short!]

When you ask 'can I get grub menu' I presume you mean the four lines...yes, but they are so small I literally have to use a magnifying glass at may age. But if I press enter on any of them, nothing happens - not even on recovery mode. How can these miniscule text be made larger?

I will try the recovery mode via delete key.....but what on the recovery menu will I want to try to use? Thanks and sorry I sound frustrated. I am. [Just tried getting into grub menu via delete key - same as without delete key. Any option I press enter on does nothing.

---

### Post by crazybear on 2020-07-30
I was able to get into Win 10. Fast startup is still off. Should I try to do another try [last time was five tries] at boot-repair OR must I try to re-install Ubuntu?

---

### Post by crazybear on 2020-07-30
now it is giving me a grub> prompt, but I'd not know what to enter. ran repair-grub many times. It would halt at last command to remove or re-install grub, I believe...never went through complete proceedure it usually does.

---

### Post by crazybear on 2020-07-30
I just made a boot-repair boot USB drive and tried that...it worked better, but the letters were SO small on the 4K screen, I had to get jewler's glasses to see what I was doing. However, despite trying several options other than upgrade to newest version of grub or to do anything with Win, all failed. I can only boot into Win, NEVER into Ubuntu!!! [which I use 99% of the time!] the latest information is here: [https://paste.ubuntu.com/p/hj64CBXfV8/](https://paste.ubuntu.com/p/hj64CBXfV8/) Any help or suggestions MUCH appreciated. I'm to go on holiday and the laptop was to be able to keep in contact with the world and be able to do work when away......I leave in about 10 days and at this pace......I'm worried.

---

### Post by oldfred on 2020-07-30
If traveling with a system, you must take a Windows repair flash drive and your Ubuntu live installer. And those should be for a current version of installed system. We have had users half way around world asking for help to fix system and without any tools it can be impossible.

You may not get choice as some tools to create flash drive installer only create a BIOS/CSM/Legacy version or only a UEFI version even though ISO is for both and many install tools create flash drive that can boot both ways. If UEFI Secure Boot is on, then only UEFI Secure Boot will be an option.

Shows one example of a Hitachi flash drive. First entry is obviously UEFI, but third is for same flash drive but does not say what it is, so it is the BIOS boot.
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)
Some UEFI have all UEFI first & then all BIOS options second with a label on the group.

Grub tries to use the graphics you have in your install. You can set X by Y size (gfxmode) in grub, but most complaints I have seen was it Ubuntu defaulted to something too large and only showed part of screen.  Also many answers are on creating larger fonts, when it probably should be gfxmode settings.
[https://ubuntuforums.org/showthread.php?t=2284477](https://ubuntuforums.org/showthread.php?t=2284477)
See in Advanced mode, the grub options and gfxmode. You later may want to change back once system working in /etc/defaults/grub.
[https://sourceforge.net/p/boot-repair/home/Home/](https://sourceforge.net/p/boot-repair/home/Home/)

I do not recommend Boot-Repair ISO as it is normally an older copy. Better to use Ubuntu live installer so you have current Ubuntu and then add ppa which is updated regularly.

It says it reinstalled grub ok and it looks like it was in UEFI mode.

You still have not removed obsolete UEFI entries with efibootmgr as posted above.
You should remove 
0001 ubuntu 20.04
0080 Mac
0081 Mac

Also  008A looks like it is obsolete also as there is no ESP gpt2 partition.

---

### Post by crazybear on 2020-07-30
> **oldfred said:**
> If traveling with a system, you must take a Windows repair flash drive and your Ubuntu live installer. And those should be for a current version of installed system. We have had users half way around world asking for help to fix system and without any tools it can be impossible.

You may not get choice as some tools to create flash drive installer only create a BIOS/CSM/Legacy version or only a UEFI version even though ISO is for both and many install tools create flash drive that can boot both ways. If UEFI Secure Boot is on, then only UEFI Secure Boot will be an option.

Shows one example of a Hitachi flash drive. First entry is obviously UEFI, but third is for same flash drive but does not say what it is, so it is the BIOS boot.
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)
Some UEFI have all UEFI first & then all BIOS options second with a label on the group.

Grub tries to use the graphics you have in your install. You can set X by Y size (gfxmode) in grub, but most complaints I have seen was it Ubuntu defaulted to something too large and only showed part of screen.  Also many answers are on creating larger fonts, when it probably should be gfxmode settings.
[https://ubuntuforums.org/showthread.php?t=2284477](https://ubuntuforums.org/showthread.php?t=2284477)
See in Advanced mode, the grub options and gfxmode. You later may want to change back once system working in /etc/defaults/grub.
[https://sourceforge.net/p/boot-repair/home/Home/](https://sourceforge.net/p/boot-repair/home/Home/)

I do not recommend Boot-Repair ISO as it is normally an older copy. Better to use Ubuntu live installer so you have current Ubuntu and then add ppa which is updated regularly.

It says it reinstalled grub ok and it looks like it was in UEFI mode.

You still have not removed obsolete UEFI entries with efibootmgr as posted above.
You should remove 
0001 ubuntu 20.04
0080 Mac
0081 Mac

Also  008A looks like it is obsolete also as there is no ESP gpt2 partition.

Yes, there are for reasons I do not understand entries from the past owner's set up. I do NOT know how to remove them...please explain. Are they likely a cause of problem? If so, why were they not two days ago when the computer was running well in Ubuntu [although I had a few messages something like 'problem detected' and it offered to send it to Ubuntu - not tell me, so I did not]. It was after I put in Mint and one other 'flavor' that all booting to Linux stopped [and Windows for a while - but it is back now]. In the BIOS set up, I find it nearly impossible to choose what is what other than the Windows 10. Sometimes it creates a new entry and sometimes it lists many with long letter and number names that mean nothing to me and don't mention if even Ubuntu. Should it be shimx or ubuntu on the efi line for the Ubuntu boot? The last person to own this laptop and the only other person to own it had Win 10 and hackintosh on it. they never used Linux in any form. Sorry,  I must be very dense today, but you say correctly I have not removed obsolete UEFI entries with efibootmgr [as posted above]. I don't see it posted above.....in this or some earlier post? OK, will not use boot-repair disk, but it halted and did NOT complete sometimes using an install disk. I'd put in a line it said to put in terminal and it never went back to a prompt...never seen that before. Had to bail out and try again several times.

Do we understand that at this time and for the past 36 hours or so, I have NOT been able to boot into Ubuntu. I can ONLY boot into Win 10. I just asked on a search engine about efibootmgr and it is to be run in Ubuntu - but I can not get into Ubuntu. Can it be run from a live install disk Ubuntu. Some of the entries I am not sure about. Some I am clear they are from the past owner or old things I did and don't want...but that still leaves some I would be nervous deleting. Am I correct to assume that it only deletes the boot entry and boot-repair will put back any needed entry for a OS that it finds?

---

### Post by oldfred on 2020-07-30
See:
[https://ubuntuforums.org/showthread.php?t=2447801&p=13975545#post13975545](https://ubuntuforums.org/showthread.php?t=2447801&p=13975545#post13975545)
Posted efibootmgr commands to use. 
sudo efibootmgr -v  # to confirm correct entry to delete.
sudo efibootmgr -b XXXX -B
See also
man efibootmgr

If doing the major updates with Boot-Repair, it is walking you thru a chroot. You have to have exact command or it will fail. Usually best to copy & paste. And Internet has to be working as it will download new files to update system. If Internet not working it crashes.

---

### Post by crazybear on 2020-07-30
> **oldfred said:**
> See:
[https://ubuntuforums.org/showthread.php?t=2447801&p=13975545#post13975545](https://ubuntuforums.org/showthread.php?t=2447801&p=13975545#post13975545)
Posted efibootmgr commands to use. 
sudo efibootmgr -v  # to confirm correct entry to delete.
sudo efibootmgr -b XXXX -B
See also
man efibootmgr

If doing the major updates with Boot-Repair, it is walking you thru a chroot. You have to have exact command or it will fail. Usually best to copy & paste. And Internet has to be working as it will download new files to update system. If Internet not working it crashes.

Yes, BUT I did NOT have any guidline other than for those I was SURE were from the last owner which to delete.
I deleted all but three. I have NO GRUB. I tried boot-repair and it would NOT run after a certain point - same point as last time [there are three command lines it give one to put in...the last of the three never completes!!
I do not know either if the Ubuntu should be shimx.efi or ubuntu.efi - please someone tell me
I still can ONLY get into Win 7. I can not and have not for two days been able to boot into Ubuntu. Boot-Repair is NOT working and I don't know how to make it work. The best I get is a grub> prompt. I wrote help and it gave lots of choices, but I don't know how to use any of them.

I'm STUCK! Is there something short of trying to re-install Ubuntu and loose all the work I did on it?! [I hope so]
I see some websites talking about adding lines to Win 10 as to where the Ubuntu boot is. I'm afraid to try it without guidance as it also says one can loose Windows being able to boot.

I'm exhausted. I have spent all day for three days on this and I'm NOT moving forward.....perhaps a little backwards.
Thanks in advance.

current state of the computer boot is: [https://paste.ubuntu.com/p/DPYQmvTNS4/](https://paste.ubuntu.com/p/DPYQmvTNS4/)

---

### Post by oldfred on 2020-07-30
Not sure if UEFI entries changed, but you deleted the working ubuntu entry and still have as 0005 an ubuntu 20.04 entry.

Delete 0005 but rerun sudo efibootmgr -v to double check that it is 0005.

Then add new Ubuntu entry.
sudo efibootmgr -c -g -w -L "ubuntu" -l "\EFI\ubuntu\shimx64.efi" -d /dev/nvme0n1 -p 1

And backup drive boot entry:
sudo efibootmgr -c -g -w -L "UEFI NVMe drive" -l '\EFI\Boot\bootx64.efi'  -d /dev/nvme0n1 -p 1

Then see if either of those boot entries boot to a grub menu. You may need to press escape to get menu.

Exactly what error are you getting in Boot-Repair or what is last command you ran that then does not end.

---

### Post by crazybear on 2020-07-31
> **oldfred said:**
> Not sure if UEFI entries changed, but you deleted the working ubuntu entry and still have as 0005 an ubuntu 20.04 entry.

Delete 0005 but rerun sudo efibootmgr -v to double check that it is 0005.

Then add new Ubuntu entry.
sudo efibootmgr -c -g -w -L "ubuntu" -l "\EFI\ubuntu\shimx64.efi" -d /dev/nvme0n1 -p 1

And backup drive boot entry:
sudo efibootmgr -c -g -w -L "UEFI NVMe drive" -l '\EFI\Boot\bootx64.efi'  -d /dev/nvme0n1 -p 1

Then see if either of those boot entries boot to a grub menu. You may need to press escape to get menu.

Exactly what error are you getting in Boot-Repair or what is last command you ran that then does not end.

I deleted 005. By the way the system usually does NOT name the files - I usually have to give them a name.
No, neither of those commands booted to a grub menu even when I pressed escape.
Then, I again [10th time perhaps] to run Boot Repair - and it got stuck where is always gets stuck.
After I enter "sudo chroot "/mnt/boot-sav/nvme0n1p9" apt-get install -y grub-efi-amd64-signed shim-signed linux-headers-generic" it just sits and does NOTHING further. This has happened every time the last few days. Having used Boot Repair many times before, I know there is much more....but not on this machine now.

Ideas?

Also, strangely, the flash drive with Ubuntu 20.04 that I used to install it will not boot. I even downloaded another version of 20.04 and made a new install USB - but it will not. I must use a 18.04 install USB. I do NOT understand why. It is very very strange and do not know how I would re-install 20.04 if I need to!

After all the above, I rebooted.....it did not boot to Ubuntu, but only gave the 'grub>' prompt.
In the BIOS there was one boot option I thought I had deleted - and did in BIOS. The system had also added a NEW boot option...forget exact title, but seemed to be to the SSD and not to any OS.

It does boot to Win 10, but not to Ubuntu. I use Ubuntu 99% of the time.

No one has told me [though twice I have asked] if the Ubuntu should be shimx or grubx. Please let me know.

Latest report: [http://paste.ubuntu.com/p/TYDCD6f3h6/](http://paste.ubuntu.com/p/TYDCD6f3h6/)  [which doesn't exist - strangely - must have copied it wrong]
Earlier report: [http://paste.ubuntu.com/p/gT756mXMmW/](http://paste.ubuntu.com/p/gT756mXMmW/) [which ALSO doesn't exist - strangely - something strange is going on with boot-repair!][ ]("http://paste.ubuntu.com/p/TVDCD6f3h6/")

---

### Post by crazybear on 2020-07-31
just going to post the terminal text - maybe this will help someone figure out the problem why boot-repair is NOT working  now or for several days [for me].

```

ubuntu@ubuntu:~$ sudo efibootmgr -v
BootCurrent: 0005
Timeout: 0 seconds
BootOrder: 0003,0000,0002,0001,0005
Boot0000  Windows Boot Manager    HD(1,GPT,5f7dd662-4e83-48b2-ada8-7f591aa5bdd6,0x800,0xfa000)/File(\EFI\ubuntu\grubx64.efi)WINDOWS.........x...B.C.D.O.B.J.E.C.T.=.{.9.d.e.a.8.6.2.c.-.5.c.d.d.-.4.e.7.0.-.a.c.c.1.-.f.3.2.b.3.4.4.d.4.7.9.5.}...d................
Boot0001* UBUNTU 20.04 - grubx64    PciRoot(0x0)/Pci(0x1d,0x0)/Pci(0x0,0x0)/NVMe(0x1,64-79-A7-36-70-61-0A-08)/HD(1,GPT,5f7dd662-4e83-48b2-ada8-7f591aa5bdd6,0x800,0xfa000)/File(\EFI\ubuntu\grubx64.efi)
Boot0002* UEFI: GIGABYTE GP-GSM2NE3100TNTD, Partition 1    HD(1,GPT,5f7dd662-4e83-48b2-ada8-7f591aa5bdd6,0x800,0xfa000)/File(EFI\Microsoft\Boot\bootmgfw.efi)..BO
Boot0003* Ubuntu 20.04 shimx    PciRoot(0x0)/Pci(0x1d,0x0)/Pci(0x0,0x0)/NVMe(0x1,64-79-A7-36-70-61-0A-08)/HD(1,GPT,5f7dd662-4e83-48b2-ada8-7f591aa5bdd6,0x800,0xfa000)/File(\EFI\ubuntu\shimx64.efi)
Boot0005* UEFI: SanDisk Cruzer Glide 1.26, Partition 1    PciRoot(0x0)/Pci(0x14,0x0)/USB(1,0)/HD(1,MBR,0x6e037a9d,0x2eec,0x1340)..BO
ubuntu@ubuntu:~$ sudo efibootmgr -b 0001 -B
BootCurrent: 0005
Timeout: 0 seconds
BootOrder: 0003,0000,0002,0005
Boot0000  Windows Boot Manager
Boot0002* UEFI: GIGABYTE GP-GSM2NE3100TNTD, Partition 1
Boot0003* Ubuntu 20.04 shimx
Boot0005* UEFI: SanDisk Cruzer Glide 1.26, Partition 1
ubuntu@ubuntu:~$ sudo efibootmgr -v
BootCurrent: 0005
Timeout: 0 seconds
BootOrder: 0003,0000,0002,0005
Boot0000  Windows Boot Manager    HD(1,GPT,5f7dd662-4e83-48b2-ada8-7f591aa5bdd6,0x800,0xfa000)/File(\EFI\ubuntu\grubx64.efi)WINDOWS.........x...B.C.D.O.B.J.E.C.T.=.{.9.d.e.a.8.6.2.c.-.5.c.d.d.-.4.e.7.0.-.a.c.c.1.-.f.3.2.b.3.4.4.d.4.7.9.5.}...d................
Boot0002* UEFI: GIGABYTE GP-GSM2NE3100TNTD, Partition 1    HD(1,GPT,5f7dd662-4e83-48b2-ada8-7f591aa5bdd6,0x800,0xfa000)/File(EFI\Microsoft\Boot\bootmgfw.efi)..BO
Boot0003* Ubuntu 20.04 shimx    PciRoot(0x0)/Pci(0x1d,0x0)/Pci(0x0,0x0)/NVMe(0x1,64-79-A7-36-70-61-0A-08)/HD(1,GPT,5f7dd662-4e83-48b2-ada8-7f591aa5bdd6,0x800,0xfa000)/File(\EFI\ubuntu\shimx64.efi)
Boot0005* UEFI: SanDisk Cruzer Glide 1.26, Partition 1    PciRoot(0x0)/Pci(0x14,0x0)/USB(1,0)/HD(1,MBR,0x6e037a9d,0x2eec,0x1340)..BO
ubuntu@ubuntu:~$ sudo add-apt-repository ppa:yannubuntu/boot-repair
 Simple tool to repair frequent boot problems.

Website: https://sourceforge.net/p/boot-repair/home
 More info: https://launchpad.net/~yannubuntu/+archive/ubuntu/boot-repair
Press [ENTER] to continue or Ctrl-c to cancel adding it.

Ign:1 cdrom://Ubuntu 18.04.4 LTS _Bionic Beaver_ - Release amd64 (20200203.1) bionic InRelease
Hit:2 cdrom://Ubuntu 18.04.4 LTS _Bionic Beaver_ - Release amd64 (20200203.1) bionic Release
Hit:4 http://archive.ubuntu.com/ubuntu bionic InRelease
Get:5 http://ppa.launchpad.net/yannubuntu/boot-repair/ubuntu bionic InRelease [15.4 kB]                                     
Get:6 http://archive.ubuntu.com/ubuntu bionic-updates InRelease [88.7 kB]                                                   
Get:7 http://security.ubuntu.com/ubuntu bionic-security InRelease [88.7 kB]                                         
Get:8 http://ppa.launchpad.net/yannubuntu/boot-repair/ubuntu bionic/main amd64 Packages [1972 B]                                  
Get:9 http://archive.ubuntu.com/ubuntu bionic-updates/main amd64 Packages [1032 kB]                  
Get:10 http://ppa.launchpad.net/yannubuntu/boot-repair/ubuntu bionic/main Translation-en [1688 B]
Get:11 http://security.ubuntu.com/ubuntu bionic-security/main amd64 Packages [805 kB]              
Get:12 http://archive.ubuntu.com/ubuntu bionic-updates/main Translation-en [346 kB]
Get:13 http://archive.ubuntu.com/ubuntu bionic-updates/main amd64 DEP-11 Metadata [295 kB]     
Get:14 http://archive.ubuntu.com/ubuntu bionic-updates/main DEP-11 48x48 Icons [81.9 kB]         
Get:15 http://archive.ubuntu.com/ubuntu bionic-updates/main DEP-11 64x64 Icons [157 kB]      
Get:16 http://archive.ubuntu.com/ubuntu bionic-updates/restricted amd64 Packages [84.8 kB]
Get:17 http://archive.ubuntu.com/ubuntu bionic-updates/restricted Translation-en [18.7 kB] 
Get:18 http://security.ubuntu.com/ubuntu bionic-security/main Translation-en [252 kB]            
Get:19 http://security.ubuntu.com/ubuntu bionic-security/main amd64 DEP-11 Metadata [46.1 kB]
Get:20 http://security.ubuntu.com/ubuntu bionic-security/main DEP-11 48x48 Icons [25.7 kB]
Get:21 http://security.ubuntu.com/ubuntu bionic-security/main DEP-11 64x64 Icons [58.0 kB]
Get:22 http://security.ubuntu.com/ubuntu bionic-security/restricted amd64 Packages [75.6 kB]
Get:23 http://security.ubuntu.com/ubuntu bionic-security/restricted Translation-en [16.5 kB]
Fetched 3491 kB in 2s (2040 kB/s)                                         
Reading package lists... Done
ubuntu@ubuntu:~$ sudo apt-get update
Ign:1 cdrom://Ubuntu 18.04.4 LTS _Bionic Beaver_ - Release amd64 (20200203.1) bionic InRelease
Hit:2 cdrom://Ubuntu 18.04.4 LTS _Bionic Beaver_ - Release amd64 (20200203.1) bionic Release
Hit:4 http://security.ubuntu.com/ubuntu bionic-security InRelease                                                                                                                   
Hit:5 http://archive.ubuntu.com/ubuntu bionic InRelease                  
Hit:6 http://ppa.launchpad.net/yannubuntu/boot-repair/ubuntu bionic InRelease
Hit:7 http://archive.ubuntu.com/ubuntu bionic-updates InRelease          
Reading package lists... Done                      
ubuntu@ubuntu:~$ sudo apt-get install -y boot-repair && boot-repair
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following additional packages will be installed:
  boot-sav boot-sav-extra gawk glade2script glade2script-python3 libsigsegv2 pastebinit
Suggested packages:
  boot-info mdadm os-uninstaller gawk-doc gir1.2-appindicator3-0.1
The following NEW packages will be installed:
  boot-repair boot-sav boot-sav-extra gawk glade2script glade2script-python3 libsigsegv2 pastebinit
0 upgraded, 8 newly installed, 0 to remove and 307 not upgraded.
Need to get 1068 kB of archives.
After this operation, 4740 kB of additional disk space will be used.
Get:1 http://archive.ubuntu.com/ubuntu bionic/main amd64 libsigsegv2 amd64 2.12-1 [14.7 kB]
Get:2 http://ppa.launchpad.net/yannubuntu/boot-repair/ubuntu bionic/main amd64 glade2script-python3 all 3.2.4~ppa23 [35.9 kB]
Get:3 http://archive.ubuntu.com/ubuntu bionic/main amd64 gawk amd64 1:4.1.4+dfsg-1build1 [401 kB]
Get:4 http://ppa.launchpad.net/yannubuntu/boot-repair/ubuntu bionic/main amd64 glade2script all 3.2.4~ppa23 [2204 B]
Get:5 http://archive.ubuntu.com/ubuntu bionic/main amd64 pastebinit all 1.5-2 [14.6 kB]
Get:6 http://ppa.launchpad.net/yannubuntu/boot-repair/ubuntu bionic/main amd64 boot-sav all 4ppa125 [443 kB]
Get:7 http://ppa.launchpad.net/yannubuntu/boot-repair/ubuntu bionic/main amd64 boot-repair all 4ppa125 [12.5 kB]
Get:8 http://ppa.launchpad.net/yannubuntu/boot-repair/ubuntu bionic/main amd64 boot-sav-extra all 4ppa125 [143 kB]
Fetched 1068 kB in 1s (1181 kB/s)      
Selecting previously unselected package libsigsegv2:amd64.
(Reading database ... 145386 files and directories currently installed.)
Preparing to unpack .../libsigsegv2_2.12-1_amd64.deb ...
Unpacking libsigsegv2:amd64 (2.12-1) ...
Setting up libsigsegv2:amd64 (2.12-1) ...
Selecting previously unselected package gawk.
(Reading database ... 145393 files and directories currently installed.)
Preparing to unpack .../0-gawk_1%3a4.1.4+dfsg-1build1_amd64.deb ...
Unpacking gawk (1:4.1.4+dfsg-1build1) ...
Selecting previously unselected package glade2script-python3.
Preparing to unpack .../1-glade2script-python3_3.2.4~ppa23_all.deb ...
Unpacking glade2script-python3 (3.2.4~ppa23) ...
Selecting previously unselected package glade2script.
Preparing to unpack .../2-glade2script_3.2.4~ppa23_all.deb ...
Unpacking glade2script (3.2.4~ppa23) ...
Selecting previously unselected package boot-sav.
Preparing to unpack .../3-boot-sav_4ppa125_all.deb ...
Unpacking boot-sav (4ppa125) ...
Selecting previously unselected package boot-repair.
Preparing to unpack .../4-boot-repair_4ppa125_all.deb ...
Unpacking boot-repair (4ppa125) ...
Selecting previously unselected package boot-sav-extra.
Preparing to unpack .../5-boot-sav-extra_4ppa125_all.deb ...
Unpacking boot-sav-extra (4ppa125) ...
Selecting previously unselected package pastebinit.
Preparing to unpack .../6-pastebinit_1.5-2_all.deb ...
Unpacking pastebinit (1.5-2) ...
Setting up gawk (1:4.1.4+dfsg-1build1) ...
Setting up pastebinit (1.5-2) ...
Setting up glade2script-python3 (3.2.4~ppa23) ...
Setting up glade2script (3.2.4~ppa23) ...
Setting up boot-sav (4ppa125) ...
Setting up boot-repair (4ppa125) ...
Setting up boot-sav-extra (4ppa125) ...
Processing triggers for desktop-file-utils (0.23-1ubuntu3.18.04.2) ...
Processing triggers for libc-bin (2.27-3ubuntu1) ...
Processing triggers for man-db (2.8.3-2ubuntu0.1) ...
Processing triggers for gnome-menus (3.13.3-11ubuntu1.1) ...
Processing triggers for mime-support (3.60ubuntu1) ...

(glade2script-python3:5601): IBUS-WARNING **: 10:29:12.240: The owner of /home/ubuntu/.config/ibus/bus is not root!
ubuntu@ubuntu:~$ sudo boot-repair

(glade2script-python3:25785): IBUS-WARNING **: 10:30:57.572: The owner of /home/ubuntu/.config/ibus/bus is not root!
sudo chroot "/mnt/boot-sav/nvme0n1p9" dpkg --configure -a
sudo chroot "/mnt/boot-sav/nvme0n1p9" apt-get install -fy
sudo chroot "/mnt/boot-sav/nvme0n1p9" apt-get install -y grub-efi-amd64-signed shim-signed linux-headers-generic
ubuntu@ubuntu:~$ sudo chroot "/mnt/boot-sav/nvme0n1p9" dpkg --configure -a
ubuntu@ubuntu:~$ sudo chroot "/mnt/boot-sav/nvme0n1p9" apt-get install -fy
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  efibootmgr mokutil shim
Use 'sudo apt autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 955 not upgraded.
ubuntu@ubuntu:~$ sudo chroot "/mnt/boot-sav/nvme0n1p9" apt-get install -y grub-efi-amd64-signed shim-signed linux-headers-generic
Reading package lists... Done
Building dependency tree       
Reading state information... Done
linux-headers-generic is already the newest version (5.4.0.42.46).
The following additional packages will be installed:
  grub-common grub-efi-amd64 grub-efi-amd64-bin grub2-common os-prober
Suggested packages:
  multiboot-doc grub-emu xorriso desktop-base
The following NEW packages will be installed:
  grub-common grub-efi-amd64 grub-efi-amd64-bin grub-efi-amd64-signed grub2-common os-prober shim-signed
0 upgraded, 7 newly installed, 0 to remove and 955 not upgraded.
Need to get 0 B/4031 kB of archives.
After this operation, 28.6 MB of additional disk space will be used.
Preconfiguring packages ...
E: Can not write log (Is /dev/pts mounted?) - posix_openpt (2: No such file or directory)
Selecting previously unselected package grub-common.
(Reading database ... 291971 files and directories currently installed.)
Preparing to unpack .../0-grub-common_2.04-1ubuntu26.1_amd64.deb ...
Unpacking grub-common (2.04-1ubuntu26.1) ...
Selecting previously unselected package grub-efi-amd64-bin.
Preparing to unpack .../1-grub-efi-amd64-bin_2.04-1ubuntu26.1_amd64.deb ...
Unpacking grub-efi-amd64-bin (2.04-1ubuntu26.1) ...
Selecting previously unselected package grub2-common.
Preparing to unpack .../2-grub2-common_2.04-1ubuntu26.1_amd64.deb ...
Unpacking grub2-common (2.04-1ubuntu26.1) ...
Selecting previously unselected package grub-efi-amd64.
Preparing to unpack .../3-grub-efi-amd64_2.04-1ubuntu26.1_amd64.deb ...
Unpacking grub-efi-amd64 (2.04-1ubuntu26.1) ...
Selecting previously unselected package grub-efi-amd64-signed.
Preparing to unpack .../4-grub-efi-amd64-signed_1.146+2.04-1ubuntu26.1_amd64.deb ...
Unpacking grub-efi-amd64-signed (1.146+2.04-1ubuntu26.1) ...
Selecting previously unselected package os-prober.
Preparing to unpack .../5-os-prober_1.74ubuntu2_amd64.deb ...
Unpacking os-prober (1.74ubuntu2) ...
Selecting previously unselected package shim-signed.
Preparing to unpack .../6-shim-signed_1.40.3+15+1533136590.3beb971-0ubuntu1_amd64.deb ...
Unpacking shim-signed (1.40.3+15+1533136590.3beb971-0ubuntu1) ...
Setting up grub-common (2.04-1ubuntu26.1) ...
Created symlink /etc/systemd/system/multi-user.target.wants/grub-initrd-fallback.service &#8594; /lib/systemd/system/grub-initrd-fallback.service.
Created symlink /etc/systemd/system/rescue.target.wants/grub-initrd-fallback.service &#8594; /lib/systemd/system/grub-initrd-fallback.service.
Created symlink /etc/systemd/system/emergency.target.wants/grub-initrd-fallback.service &#8594; /lib/systemd/system/grub-initrd-fallback.service.
update-rc.d: warning: start and stop actions are no longer supported; falling back to defaults
invoke-rc.d: could not determine current runlevel
Setting up os-prober (1.74ubuntu2) ...
Setting up grub-efi-amd64-bin (2.04-1ubuntu26.1) ...
Setting up grub2-common (2.04-1ubuntu26.1) ...
Setting up grub-efi-amd64 (2.04-1ubuntu26.1) ...

Creating config file /etc/default/grub with new version
Setting up grub-efi-amd64-signed (1.146+2.04-1ubuntu26.1) ...
Setting up shim-signed (1.40.3+15+1533136590.3beb971-0ubuntu1) ...
Processing triggers for systemd (245.4-4ubuntu3.2) ...
Processing triggers for man-db (2.9.1-1) ...
Processing triggers for install-info (6.7.0.dfsg.2-5) ...

```

and pastebin from sometime - I'm loosing track of this...have spent about 60+ hours on this over several days and loosing 'it'....\
[http://paste.ubuntu.com/p/g3twyrdKDz/](http://paste.ubuntu.com/p/g3twyrdKDz/) 
I think that was from before I started...not sure any more....loosing it...

the pastebin [I'm NO expert] looks OK, but I only boot into the 'grub>' prompt in TINY, TINY letters. HOW DO I MAKE THE GRUB LETTERS BIGGER? I'm 70 and can NOT see these small letters without putting on jewlers glasses.

There are ONLY TWO entries now in the boot sequence - one for Ubuntu; one for Windows 10, but [I think] grub is missing and boot-repair will NOT work; will not complete. What to do?

---

### Post by dragonfly41 on 2020-07-31
This is an **experiment** ...
Common ground .. I am a Dell 3268 user.
Windows 10 on /dev/sda
Ubuntu 18.04 on /dev/sdb (external SSD)

I will throw in an idea .. a "get me out of jail" card I have used.

Referring to your last pastebin

[http://paste.ubuntu.com/p/g3twyrdKDz/](http://paste.ubuntu.com/p/g3twyrdKDz/)


line 178
[COLOR=#bb4444]nvme0n1p1[/COLOR][COLOR=#bb4444]       2048    1026047    1024000   500M EFI System[/COLOR]


line 247
[COLOR=#bb4444]nvme0n1p1[/COLOR][COLOR=#bb4444]/[/COLOR][COLOR=#bb4444]efi[/COLOR][COLOR=#bb4444]/ubuntu/grub.[/COLOR][COLOR=#bb4444]cfg[/COLOR]

...

In your Dell boot options (on rebooting) boot up a LiveUSB Ubuntu

Install rEFInd while in "Try Ubuntu" mode in LiveUSB (do not enter Install mode!).

```
sudo apt-add-repository ppa:rodsmith/refind
sudo apt-get update
sudo apt-get install refind
```


above instructions taken from here ...

[https://www.rodsbooks.com/refind/installing.html](https://www.rodsbooks.com/refind/installing.html)

During rEFInd installation you will be prompted to select the** refind EFI **installation directory (we are not installing Ubuntu only **refind**)
 target the nvme0n1p1 (it might be nvme0n1p1/efi .. I don't remember)

This installation should end up with with refind loader installed alongside ubuntu (not replacing it)[COLOR=#bb4444]

[/COLOR]nvme0n1p1/efi/refind/

When you boot up you should see in the grub menu a new reference to /EFI/

You can see what (rEFInd) boot up menu looks like at this site.

[https://www.rodsbooks.com/refind/](https://www.rodsbooks.com/refind/)

If this works (fingers crossed) we can discuss how to configure the menu theme to be easier to view.

Note that installing rEFInd does not negate/remove your earlier grub installations .. just adds to them.

---

### Post by oldfred on 2020-07-31
I do not know where your UEFI boot entries are coming from.
The two I gave you should have been just "ubuntu" and "UEFI NVMe drive" as UEFI boot entries.
The first is booting using shimx64.efi and second uses /EFI/Boot/bootx64.efi which grub and Boot-Repair make as a copy of shimx64.efi.
The shimx64.efi is required if you boot in UEFI Secure Boot mode as it is the signed version. You can use either shimx64.efi or grubx64.efi if booting in UEFI mode with Secure Boot off.

Did you try changing gfxmode in Boot-Repair settings? With the reinstall of grub, it would have reverted to defaults.

I have several old flash drives that are now too small for installers, and put rEFInd on them. My system sometimes locks up & I have to disconnect every drive and boot with rEFInd. Then I can get grub entry to work again, so go back to grub.
Some just use rEFInd, so try dragonfly41's suggestion. Boot-Repair will use /EFI/Boot/bootx64.efi as its boot file, so grub entries will still work. It just is using the fallback or drive boot option.

---

### Post by crazybear on 2020-07-31
This is all new to  me. I just read up on it on the internet, but will it conflict with anything? As far as I know there is no grub intalled now in my Ubuntu 20.04 - at least that is what Boot-Repair told me [although it clearly was having problems and not running properly on my system]. I guess what I'm asking, is will I be able to uninstall refind if needed, without any residual damage or problems should it not work? In theory, it sounds good and interesting, but I'm not interested in 'theory', but in practice.


So, I took the gambler's chance and installed refind....but I still only get to a TINY 'grub>' screen....so how does that help me?~! I can only boot into Win 10, as before.

Does it need some configuration to work in order to boot the Ubuntu. I tried moving to both the Linux and Ubuntu icons on the boot screen and pressed enter, but I only get a black screen with about the upper left 1% in tiney tiney letters saying grub> and waiting for me to input something.....

---

### Post by oldfred on 2020-07-31
Because rEFInd uses the /EFI/Boot/bootx64.efi, that is a totally separate fallback default UEFI boot entry using the hard drive label in most systems. It will change the drive boot entry to rEFInd. You will still have UEFI entries for Windows & ubuntu.
And it installs to a separate folder in /EFI, so you can later remove UEFI entry and folder in ESP and then it is totally deleted.

Because of the announcement of boothole, new versions of grub were released. My Ubuntu updated grub a couple of days ago. So you may be in middle of that update to grub, but need to have the updated version fully installed. If only partially installed then you will get issues. 

When you get a fully working version, create another 30GB partition for another / (root). And do another install and do all you experiments on that install. And only if then you like what you have changed, you can do those changes to your main working install. I typically have at least one additional version of my current LTS version for experiments and also install each new release to see differences.

---

### Post by dragonfly41 on 2020-07-31
[COLOR=#000000]```
I guess what I'm asking, is will I be able to uninstall refind if needed, without any residual damage or problems should it not work? In theory, it sounds good and interesting, but I'm not interested in 'theory', but in practice.
```

I will stick my neck out here and write that I have had no problems with rEFInd and it can be uninstalled easily enough. As I have written it sits **alongside** other loaders I think one of the main risks is placing Windows and Ubuntu on the same internal drive and I have gradually weaned myself away from that model. I now happily run Ubuntu on an external SSD but that requires more outlay and we are discussing here getting it to work on a single drive as far as I can see. So go ahead and ensure that you have a LiveUSB and I will walk you through any reversal if needed .. but I don't think that will be needed.

Even OldFred writes that he has used it on occasions. So "dinna fear".

[Footnote] After reading post from OldFred ..
[/COLOR][COLOR=#000000]"Because rEFInd uses the /EFI/Boot/bootx64.efi"

as I have written earlier be aware that I use [/COLOR][COLOR=#000000]/EFI/refind/refind_x64.efi in grub menu to boot up.[/COLOR]

---

### Post by crazybear on 2020-07-31
> **oldfred said:**
> I do not know where your UEFI boot entries are coming from.
The two I gave you should have been just "ubuntu" and "UEFI NVMe drive" as UEFI boot entries.
The first is booting using shimx64.efi and second uses /EFI/Boot/bootx64.efi which grub and Boot-Repair make as a copy of shimx64.efi.
The shimx64.efi is required if you boot in UEFI Secure Boot mode as it is the signed version. You can use either shimx64.efi or grubx64.efi if booting in UEFI mode with Secure Boot off.

Did you try changing gfxmode in Boot-Repair settings? With the reinstall of grub, it would have reverted to defaults.

I have several old flash drives that are now too small for installers, and put rEFInd on them. My system sometimes locks up & I have to disconnect every drive and boot with rEFInd. Then I can get grub entry to work again, so go back to grub.
Some just use rEFInd, so try dragonfly41's suggestion. Boot-Repair will use /EFI/Boot/bootx64.efi as its boot file, so grub entries will still work. It just is using the fallback or drive boot option.

oldFred, First, why is Boot-Repair getting stuck?!?!?!?! I says it is stuck and leaving grub _removed_. Is it or not? I can't tell - but know I'm in trouble if that is so. Second, I certainly do not know where the UEFI entries are coming from. Third, should I have the path be with shimx64.efi or something else. In the BIOS I have to choose this path and I have tried several, NOT KNOWING what the hell I'm doing...just trying to find one that works...but maybe making things worse. Only with the intitial install of Ubuntu did the system itself set the path and I did NOT take note of what it was. Since then it gives ME a choice - and I'm confused beyond confused. I don't think I ever chose bootx64.efi and will look if it is listed. Now I'm even more confused what I should choose or if having more than one at the same time causes problems. Secure Boot is off - set to be off.

No, I did not try changing gfxmode in Boot-Repair settings. By this you mean to use gfxmode or to turn it off? Should I try this; I assume that must be in the advanced section. Each time I do it it is exhausting. I have tried many more times than I have indicated here.

Last question: Boot-Repair will not be flumuxed by refind? It is OK to try it with refind installed. I don't know the order in which I should attempt doing attempted changes nor repairs and don't want to make anything worse. This is now the third day without Ubuntu and most of the waking hours spend on this.

---

### Post by dragonfly41 on 2020-07-31
[COLOR=#000000]"Last question: Boot-Repair will not be flumuxed by refind? "

No.

I have timed out and rebooted to take a note of my GNU GRUB menu to give you some reference to work from.
"I will return". In a short time.[/COLOR]

---

### Post by oldfred on 2020-07-31
Your UEFI will not tell you if the "ubuntu" entry is grub or shim and if UEFI Secure boot is off, it does not matter at all.
It used to be that you had two UEFI ubuntu entries, one using shim & one using grub.
I just ran efibootmgr and after latest update I only have shimx64.efi as my default ubuntu entry.
But in checking I do see I still have a new grubx64.efi dated July 30th.

Since shimx64.efi always worked on UEFI whether Secure Boot on or not, I always wondered why we even have had the grubx64.efi boot entry.

If at grub> we can try a manual boot. Type each of these after your grub> appears.
But this error may be from trying to boot the obsolete BIOS boot version of grub? Make sure you are booting in UEFI mode.

grub> set root=(hd0,9)
grub> linux /vmlinuz root=/dev/nvme0n1p9
grub> initrd /initrd.img
grub> boot

---

### Post by crazybear on 2020-07-31
I almost don't know what I did, but I'm in Ubuntu now.....will report after try a few things

---

### Post by dragonfly41 on 2020-07-31
If it helps here is a comparison

These are notes of my GNU GRUB menu when I first boot up ..

In this example on a Dell 3268 we have ..
Windows 10 in internal drive (/dev/sda1)
and old (unused) dual boot version of Ubuntu 16.04 in shared internal drive (/dev/sda7)

a current version of Ubuntu 18.04 LTD on an external USB drive 

There is an EFI partition on internal drive AND
another EFI partition on external drive (/dev/sdb1).

rEFInd is installed on _both_ EFI partitions, each EFI with boot flags set.

This duplication of EFI allows me to switch off power to Windows internal drive (if needed) and still boot up external drive using rEFInd.

Now when I boot up I see this GNU GRUB menu

GRUB MENU

Ubuntu
Advanced options for Ubuntu
Boot UEFI bkpbootx64.efi
Boot UEFI fbx64.efi
EFI/refind/refind_x64.efi
EFI/ubuntu/mmx64.efi
EFI/refind/drivers_x64/ext4_x64.efi
Windows UEFI bootmgfw.efi
Windows Boot UEFI loader
Windows Boot UEFI fbx64.efi
EFI/refind/refind/refind_x64.efi sda1
EFI/ubuntu/fwupx64.efi
EFI/ubuntu/mmx64.efi sda1
EFI/dell/SOS/bootmgfw.efi
EFI/dell/SOS/bootX64.efi
EFI/refind/drivers_x64.efi sda1
Windows Boot Manager (on /dev/sda1)
Ubuntu 16.04.6 LTD (16.04) (on /dev/sda7)
Advanced options for Ubuntu 16.04.6 LTS (16.04) (on /dev/sda7)
System setup


20 items in total

3 Operating systems (Windows 10, Ubuntu 16, Ubuntu 18)

Grub and rEFInd (rEFInd installed in two EFI partitions for flexibility although one installation in Windows 10 EFI will also work)

Dell EFI/dell/SOS options for recovery and firmware (fw) update

---

### Post by crazybear on 2020-07-31
So, now I can sort of get into Ubuntu. But when I closed the cover of the laptop and re-opened it, I was at the Windows login. But, if I hit a 'button' on the lower-right, the Ubuntu came back on. VERY strange! One time Ubuntu was all wrong graphically and had to turn off completely. Now it looks OK, except there is a window that says 'System program problem detected' and offers to send a report [but not tell me]. oldFred, if I get a grub screen again, I'll try what you wrote. I actually did try Boot-Repair once more and checked the advanced feature you mentioned...but boot-repair did only a short 'routine' and then offered if I wanted to send to pastebin. IT HAD ME DO NOTHING ON TERMINAL. I removed the grubx64.efi entry in BIOS. Some weird and some unstable behavior.....let me try it a bit longer before I say more.

---

### Post by dragonfly41 on 2020-07-31
[COLOR=#000000]"System program problem detected' and offers to send a report [but not tell me]. "

When you get back into Ubuntu you can clear that crash report by deleting files in /var/crash/[/COLOR]

---

### Post by oldfred on 2020-07-31
Boot-Repair saves into this location. Since you ran it many times, you may want to houseclean most or all the old reports & logs as they do not apply anymore.
reports
ls /var/log/boot-repair
I might run one final report one with system that works and save that report. I typically run it and copy it into /home so my normal backup of /home includes it. 

Boot-Repair also added additional grub menu boot items into /etc/grub.d/25_custom.
Some are duplicate Windows entries or others you may not need. You can houseclean at will as these are all added options boots. Or you can just delete or turn off execute bit so it does not run on a grub update. To see if it added entries:
cat /etc/grub.d/25_custom

---

### Post by crazybear on 2020-08-04
Welll........ I still get a LOT and REGULAR 'sytem problem reports'! and every now and then strange visual anomalies [hard to describe - sometimes one object flashing; other times as if one expanded window was superimposed on the entire screen, but if I click on the 'X' in the upper right it closes and the screen looks normal. With the flashing, I had to do a hard shut down]. None of those in the last hours, but worrying. If I put an entry in the Windows efi line [as it mentions on some websites - don't have the text in front of me], should I be able to at least try to see if it will boot without the refind. Refind is working well 95% of the time...sometimes it boots into Windows even though Ubuntu is selected. It also is one more screen to go through, if not two more. I can live with it if need be. I looked at the location you mentioned that would be storing those system error messages and it was NOT one thing...almost every message seemed to indicate another program or thing. Confusing why that would be on a new install. Now the big problem with this laptop is very high drain of battery even though I've tried to set all to minimize battery drain. I have the nvidea turned off, and the intel gpu on and other software that is supposed to minimize battery usage..but it [with a NEW battery] says 4.5 hours is all I'll get without being plugged in with minimal internet and 6,5 hours if I'm only doing word processing and not on internet or have any other programs open. That nice screen obviously takes its toll. I'm trying to find a power bank that might supplement, but all that can handle this kind of laptop one seems to have to order from China [two months or more] and I'm going on a trip soon...so..... One that recharges from a car is only available in from USA and takes a month to get here [and there would be a 30% surcharge in tax too]. Anyway, all that is not related to Ubuntu. The battery useage is about the same in Windows as in Ubuntu as far as I can tell so far.  Will see if any more problems and report. Thanks for all the help and information! I need to find out what is causing the visual disturbances and the reports of system problems - they are likely related and THEY are ONLY in Ubuntu - not in Windows.....so will try to run some test and look at the reports. I'll do one more boot-repair report and post. Sorry, I've been a few days away,...was not away....just fussing with all this information and trying to not make this longer than it needed to be. I'll post again soon.

---

### Post by crazybear on 2020-08-08
OK, it is fairly stable now and I can always get into Ubuntu...Windoz most of the time. I'd like to be able to customize the refind screens, but can NOT find the conf file in which to do that - if anyone can help. I do get a LOT of system error messages and when I look at details they are a variety of things and some are worrying, but with the exception of a few times in Ubuntu some desktop items were missing - they always reappeared if I rebooted. I don't know if this is because I have it set to use the Intel GPU most of the time, and the Nvidea only when needed [to save battery life]. By the way the XPS with 4K touch screen is very nice with ONE exception - battery life is horrible! 4.5 hours seems to be the most I can manage if I use the internet even lightly. Double that if I just do word processing and nothing else. That is insane and bad. I have ordered a huge power bank, but that defeats the idea of a light portable laptop ;-(...oh, well....it was used and at a great price (the XPS). I made the Win 10 partition too small, but know no way to now change it...there are SO MANY tiny partitions the system or the MVeM.2 set up. I tried once in Gparted, but stopped before I destroyed everything. Nothing was working as I'm used to on a HDD or even a normal SSD. Other that that, it is working. A few bugs to work out. For some reason the Ubuntu Software Center is totally messed up and doesn't display correctly...I've tried several times totally removing and re-installing it, to no avail. All other programs seem to work. Thanks for all the help and patience. If anyone can help with these few other last battles, it would be much appreciated.

---

### Post by dragonfly41 on 2020-08-08
I suggested trying rEFInd so I will chip in with a fuller explanation of how to custom the GUI theme.

[I]Side note: I use as file manager Krusader for my development work. It is a twin panel file manager.
Under Tools I click "Start Root Mode Commander" when I need root permissions to access /boot/efi/EFI files. But you can use Nautilus or command line if you are more comfortable with that.
[/I]
...

Here we go.

First navigate the file system (where rEFInd is installed in ESP).

Look for /boot directory and in there we see ..

/boot/efi/EFI

and deeper .. (I have a Dell PC)

/boot/efi/EFI/Boot
/boot/efi/EFI/Dell
**/boot/efi/EFI/refind   <<<**
/boot/efi/EFI/ubuntu

The folder /boot/efi/EFI/ubuntu is the usual GRUB installation which most forum posts refer to.

We are interested only in the folder [B]/boot/efi/EFI/refind/
[/B]
Inside there (under the bonnet) we have ..

/drivers_x64
/icons
/icons_backup
/keys
BOOT.CSV
refind_x64.efi
refind.conf
refind.conf-sample


We will add a custom theme to this file system.

If you google search for "[refind]("file://refind-theme-regular")[-theme-regular]("file://refind-theme-regular")"
you see 

[https://www.rodsbooks.com/refind/themes.html](https://www.rodsbooks.com/refind/themes.html)

This gives examples of various themes.

I have not experimented with all themes but here is the one I adopted.

[http://munlik.deviantart.com/art/rEFInd-boot-manager-theme-Regular-theme-512091944](http://munlik.deviantart.com/art/rEFInd-boot-manager-theme-Regular-theme-512091944)

Hosted here ..

[https://github.com/bobafetthotmail/refind-theme-regular](https://github.com/bobafetthotmail/refind-theme-regular)

Click on the green button .. Code .. then Download zip.

In your ~/Downloads folder you see ..

refind-theme-regular-master.zip

This zip folder has to be opened and inside the folder we see

refind-theme-regular-master

This should be copied into /boot/efi/EFI/refind/

and renamed to /refind-theme-regular (drop "-master" from folder name)

The reason for using the name refind-theme-desktop instead of refind-theme-desktop-master is that internal files theme.conf (used to tweak the theme) refers to icons path .. 

icons_dir refind-theme-regular/icons/128-48

Thus the size of the GUI icons (at boot up) can be varied by editing theme.conf

Also in theme.conf at the bottom we see reference to fonts ..

e.g.

font refind-theme-regular/fonts/source-code-pro-extralight-14.png

I find that font to be too light so referring to available fonts I tried others ...

ubuntu-mono-14.png

You can choose larger font sizes 14, 16, 18 .. to 46

Similarly different icon sizes can be set in theme.conf.


....

Instructions also are given here ...

[https://github.com/bobafetthotmail/refind-theme-regular](https://github.com/bobafetthotmail/refind-theme-regular)


Note item 5 in instructions ...

To enable the theme add include refind-theme-regular/theme.conf at the end of refind.conf, and comment out or delete any other themes you might have installed.

....

Now when rebooting it is true that the initial GRUB menu appears and you need to select the menu item containing refind_x64.efi

/EFI/refind/refinx_x54.efi


....

The rEFInd GUI shows a lot of options some of which you might prefer to disable. For example some icons point to firmware updates etc.

These GUI display options are itemised in /boot/efi/EFI/refind/theme.conf.

Read all the commented out notes in theme.conf.

For example at line #372 we read ..

#dont_scan_dirs ESP:/EFI/boot,EFI/Dell,EFI/memtest86

If that line is uncommented we can disable GUI showing these options.

So read and customise the theme.conf carefully to understand the many options.

There must be a way of suppressing this GRUB menu and going directly to rEFInd GUI on first boot but I have not researched how to do this.

---

### Post by crazybear on 2020-08-08
I have a moderately large .jpg file I want as background. How do I insert it? Also, when I initially installed refind I had mint installed - now I do not - but it goes to a 'Mint' start screen....not horrible...but I'd rather it not and if it has to use the one for Ubuntu 20.04 Gnome.

---

### Post by dragonfly41 on 2020-08-08
Open theme.conf as explained earlier (post #60) and search "background" for full instructions on adding custom background.

[P.S.] Ensure that you only have one theme installed at a time. Clear out Mint theme (backup first in case you need to revert). Then install refind-theme-regular.

---

### Post by crazybear on 2020-08-08
I give up on trying to change refind. I tried and nearly blew it up....but got back in and put it back to default. The only real problem now with my set up is ubuntu software 3.36.1 strangely never [except the first time I used it] displays correctly. It is SO deformed on the screen it can NOT be used. I have tried to uninstall and reinstall, but the same happens every time. Very strange. No other program has that problem, although one time some of the folders on my desktop were missing. That only happened once. I still get LOTS of system error messages....and don't know if that is normal or not. I know one can turn them off from displaying...but want to keep an eye on them.

---

