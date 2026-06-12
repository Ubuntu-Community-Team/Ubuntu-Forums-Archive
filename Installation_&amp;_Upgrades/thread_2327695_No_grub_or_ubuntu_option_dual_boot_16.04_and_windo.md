---
title: "No grub or ubuntu option: dual boot 16.04 and windows 8.1"
date: 2016-06-13
forum: Installation &amp; Upgrades
---

### Post by jed5 on 2016-06-13
Computer: HP dv6t-7000 laptop, 500gb ssd, Windows 8.1 installed

I want to dual boot Ubuntu and Windows 8.1. These are the steps I followed:

Shrink volume: ~100Gb of unallocated space
Disabled fast boot in control panel
Disabled hibernation via command line
Enabled UEFI in bios (see picture)
Installed Ubuntu 16.04 from USB drive (created with Rufus) using "install alongside" automatic option
Shutdown and unplugged usb stick

Upon starting up the computer, it boots straight into Windows 8.1. I can't get grub to come up, and Ubuntu is not an option in boot order. I spent about 2 hours trying various fixes. Holding down "shift" while booting does not bring up grub. I tried putting the usb drive back in, selecting "try ubuntu without installing", and following the instructions for installing boot-repair. I ran it a couple times (once with the purge option selected), and it didn't work. This is a link to the output file from "create bootinfo summary": [http://paste2.org/p2FcY4dL](http://paste2.org/p2FcY4dL) . I tried the following with an admin command prompt: ```
bcedit /set {bootmgr} "path\EFI\ubuntu\grubx64.efi"
```. It said it completed successfully, but the computer still boots straight into windows.
 [COLOR=#111111][FONT=Consolas][/FONT][/COLOR]
Pic of bios boot settings:
[ATTACH=CONFIG]269565[/ATTACH]

Any ideas about what's wrong with grub's setup and how to fix it?

Thanks!

---

### Post by X-RED_Tech on 2016-06-13
You should be able to boot pressing ESC immediately after powering on and then F9. This seems to be the standard menu for UEFI HP.
There are many threads here describing the same as you just did and I remeber something about some HPs needing additional tweaking, renaming of efi files and stuff... At least temporarily you can use the above workaround.

---

### Post by oldfred on 2016-06-13
I do not know HP, but the entry at top says Post Hotkey delay sec. I might make that a couple or few seconds. At least until fully configured.
UEFI with Windows had fast boot which is different than Windows fast startup or hibernation.
The UEFI fast boot skips all hardware checks & updates, it assumes system is identical to when shutdown. And most of the time that is true. But then the only way to get into UEFI is from Windows or now Grub menu. If system has major issues, you may not have time to press key(s) to get into UEFI. 
Often cold boot still works to force system to check hardware again, but some do not do that.

My motherboard had fast boot settings for both cold & warm (reboot) boot which I could set. I set UEFI to 3 sec and grub to 3 sec which almost doubles my boot time with my SSD, but gives me chances to get into system or choose something in grub.

       May be best to see details:
Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)

Best to backup ESP - efi system partition.
Is  UEFI the latest version for your system from HP?
Do you have additional options under UEFI and the OS Boot Manager?

HP has not been dual boot friendly. It modifies UEFI to boot by description which UEFI standard says not to do. And only valid description is "Windows Boot Manager". But there are multiple work arounds. The one you tried should work by booting into Windows and then using UEFI one time boot to reboot into Ubuntu.
UEFI systems also have a fallback or hard drive boot entry /EFI/Boot/bootx64.efi. That is the same path/file used by installers on external drives.

Boot-Repair's advanced mode has an option :
           'Use the standard EFI file' in advanced options. 
Then if you have a hard drive boot entry in UEFI that should boot grub.

Some manual copy of shimx64.efi to be /EFI/Boot/bootx64.efi for ubuntu boot on HP:
HP Check if Customized UEFI settings available like this  HP ProBook 4340
[http://askubuntu.com/questions/244261/how-do-i-get-my-hp-laptop-to-boot-into-grub-from-my-new-efi-file](http://askubuntu.com/questions/244261/how-do-i-get-my-hp-laptop-to-boot-into-grub-from-my-new-efi-file)
HP Envy 700-430QE desktop used bcdedit to dual boot
[URL="http://ubuntuforums.org/showthread.php?t=2260681"]http://ubuntuforums.org/showthread.php?t=2260681
[/URL]
 HP ProBook 450 G1 Custom UEFI boot or copy to bootx64.efi, delay of a so called "Express Multiboot menu"
[http://forums.linuxmint.com/viewtopic.php?f=46&t=164076](http://forums.linuxmint.com/viewtopic.php?f=46&t=164076)
HP 4545s Secure boot off, manually copy files.
[http://ubuntuforums.org/showthread.php?t=2133796](http://ubuntuforums.org/showthread.php?t=2133796)
HP Manually renamed files to make it work.
[http://ubuntuforums.org/showthread.php?t=2131886](http://ubuntuforums.org/showthread.php?t=2131886) 

[URL="http://ubuntuforums.org/showthread.php?t=2260681"]
[/URL]

---

### Post by jed5 on 2016-06-13
Yes, I can start Ubuntu from the boot options menu, but I have to go into boot options every time. Also, there are 8 entries for Ubuntu in boot options:  [ATTACH=CONFIG]269566[/ATTACH] 

So I guess there are two problems now:
1. How do I make grub come up instead of windows automatically booting?
2. How do I remove extra Ubuntu entires in boot menu?

---

### Post by jed5 on 2016-06-13
More info: Ubuntu isn't in the UEFI boot order (just OS boot manager. see pic attached in first post), and I can't move Ubuntu to the top of the list in boot options menu (see pic in my 2nd post).

---

### Post by jed5 on 2016-06-13
oldfred - I will try some of the manual fixes in those links. I already tried using boot-repair.

I think I can use the bcedit tool from an admin command prompt to delete the extra ubuntu entries in the boot options menu. Does that sound correct?

---

### Post by oldfred on 2016-06-13
I do not know bcedit, but have seen efibootmgr.

Post link from Boot-Repair's summary report.

Ubuntu normally has two entries, one grub and the other shim.

       # from liveDVD or flash booted in UEFI mode and use efibootmgr
sudo efibootmgr -v
The "-v" option displays all the entries so you can confirm you're deleting the right one, and then you use the combination of "-b ####" (to specify the entry) and "-B" (to delete it). Examples #5 is delete:, with Ubuntu you need sudo, others must be at root.
efibootmgr -b XXXX -B
[http://linux.die.net/man/8/efibootmgr](http://linux.die.net/man/8/efibootmgr)
[http://linux.dell.com/cgi-bin/gitweb/gitweb.cgi?p=efibootmgr.git;a=blob_plain;f=README;hb=HEAD](http://linux.dell.com/cgi-bin/gitweb/gitweb.cgi?p=efibootmgr.git;a=blob_plain;f=README;hb=HEAD)

---

### Post by jed5 on 2016-06-13
I fixed the extra entry problems with bcdedit before I saw your post about efibootmgr. I think they end up doing the same thing. I used these commands in an admin command prompt: 
```
bcdedit /enum firmware 
bcdedit /export newbcd
copy newbcd bcdbackup
bcdedit /store newbcd /delete {copy paste identifier of each extra Ubuntu listings here. repeat this step as necessary}
bcdedit  /import newbcd /clean

```

Still need to try the manual uefi file fixes. Stupid HP...

Thanks!

---

### Post by jed5 on 2016-06-13
Is the summary report the same as the boot repair info link in my first post?

Thanks,
Jed

---

### Post by ubfan1 on 2016-06-13
Yes.

---

### Post by oldfred on 2016-06-13
I missed report in first post.

It did show the duplicate entried.

Not sure if any of the Internal Hard Disk entries are for UEFI or BIOS boot?
But if you use Boot-Repair and 'Use the standard EFI file' in advanced options, then try booting with those entries for hard drive.

Most with HP end up with /EFI/Boot/bootx64.efi and a hard drive boot entry. HP just will not let you boot the ubuntu entry directly.

---

### Post by jed5 on 2016-06-21
Update: I started a new [thread]("http://ubuntuforums.org/showthread.php?t=2327910") for the extra "Ubuntu" entries that keep getting added to the UEFI boot options menu. Making progress on that.

I'm a little nervous about doing the manual modifications (link in oldfred's earlier post) that force grub to start instead of using the UEFI boot options menu (hitting F9 at start up). Has anyone successfully done this on an HP laptop of similar vintage to this one (dv6t-7000 bought in 2010)?

---

### Post by oldfred on 2016-06-21
Have not seen or saved your model HP.

Some possibly similar as vendors often use same or similar UEFI with just options different for each model.
 Installing Ubuntu on HP Envy-6  Details of what worked post #11
[http://ubuntuforums.org/showthread.php?t=2123975](http://ubuntuforums.org/showthread.php?t=2123975)
HP ProBook 450 G1 Custom UEFI boot or copy to bootx64.efi, delay of a so called "Express Multiboot menu"
[http://forums.linuxmint.com/viewtopic.php?f=46&t=164076](http://forums.linuxmint.com/viewtopic.php?f=46&t=164076)
HP 4545s Secure boot off, manually copy files.
[http://ubuntuforums.org/showthread.php?t=2133796](http://ubuntuforums.org/showthread.php?t=2133796)
HP Manually renamed files to make it work.
[http://ubuntuforums.org/showthread.php?t=2131886](http://ubuntuforums.org/showthread.php?t=2131886)
HP p6-2326 Ubuntu and windows 8 Boot DVD
[http://ubuntuforums.org/showthread.php?t=2093445](http://ubuntuforums.org/showthread.php?t=2093445)
HP to get into UEFI/BIOS menu - escape then f10 as soon as it starts. Key board issues try different USB ports maybe  front.
[http://h10025.www1.hp.com/ewfrf/wc/document?docname=c01443329&lc=en&cc=us&dlc=en&product=5171079](http://h10025.www1.hp.com/ewfrf/wc/document?docname=c01443329&lc=en&cc=us&dlc=en&product=5171079)

---

