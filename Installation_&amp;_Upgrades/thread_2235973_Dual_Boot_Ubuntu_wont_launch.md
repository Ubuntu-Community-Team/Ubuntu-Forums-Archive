---
title: "Dual Boot Ubuntu wont launch"
date: 2014-07-23
forum: Installation &amp; Upgrades
---

### Post by Loki*PI on 2014-07-23
I have a new desktop. Gagabyte MB, 8 Gb memory, Toshiba 1 Tb hd, Nvidia video card. Running 64 bit.

I installed Windows 7, no problem on a 50 Gb partion. I then brought up Ubuntu 14.04 64 bit from bootable DVD. I went in with Try Ubuntu - everything looked ok so I clicked install. Install did not show the Windows installation.  I used 'other' and created / partion, swap, and /home partions. Ubutun had internet, saw the video card no problem, seems to install normally.

On reboot nothing, so I used the ubutu DVD in recover mode and updated grub. On reboot Windows 7 is in grub and boots no problem. Ubuntu is also in grub but when I launch it I get a blank screen - nothing.

In the BIOS I have it set to luanch from the hd. Also BIOS offers "UEFI and Legacy" as Boot mode. I have that selected. If I go to just UEFI my DVD is not recognized.

OK so what did I do wrong?

Thanks all.

---

### Post by oldfred on 2014-07-23
With nVidia card you need to boot with the nomodeset boot parameter. Then once in system go to system settings and install the nVidia driver.

 At grub menu you can use e for edit, scroll to linux line and replace quiet splash with nomodeset.
How to set NOMODESET and other kernel boot options in grub2 - both BIOS liveCD & grub first boot ( also UEFI with grub) 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)

Also shows boot stanza as seen from grub. End of linux line has quiet splash
       Editing the GRUB 2 Menu During Boot
[https://help.ubuntu.com/community/Grub2/Troubleshooting](https://help.ubuntu.com/community/Grub2/Troubleshooting)

    
When you see you are in the desktop but no icon or bar, right click to change desktop background
When the window appear, click all settings, now you see the system settings window.
Next, click on Software source, go in the additional drivers tab.
Select the 3 rd option, using video driver for the nvidia or AMD... fglrx-upgrade

---

### Post by Loki*PI on 2014-07-24
Thank for the reply oldfred. I worked through it and ended up no where actually, I'm still trying to get the dual boot to work.  

Using the nomodeset did get me into the U-14 desktop in low graphics 800x600. I looked for additoinal divers but it was empty. I went to Nvidea and downloaded the .run file. I had to stop xserver to install it. The installation fail and I was never able to get back into the desktop, a blank purple screen was the best I got. I have reinstalled U-14 a couple times more trying different things, also reinstalled Win7, no joy.

It appears that my DVD is not recognized by UEFI, although it is a new unit. I have boot device set to UEFI and legacy. Win7 installs with BIOS. The only way I can get U-14 installed is UEFI. I have read that both OS must be the same either UEFI or BIOS.

My first install did get me to a working Win7, with working U-14, and grub2 working. The problem was the Nvidea drivers. I haven't been able to get back to that point even with complete reinstalls. 

There are too many variables. This is way to complicated. Dual Boot is a standard install, this should be worked out better, easier. Nothing I've read here indicated incompatability between UEFI and BIOS installs. I found that somewhere else. I've been at this for 3 days. 

My next step is to disable the Nvidia card and use the MB video. Hopefully I can get the dual install working and then upgrade the OSs to Nivida. 

Open to suggestions - -   thanks in advance

---

### Post by oldfred on 2014-07-24
Only if you have a very new nVidia card should you download drivers from nVidia. If Ubuntu did not offer the driver you may have then booted with the Intel chip? I do not know dual video systems.
If not reinstalling, you have to totally purge one version of nVidia driver to install another version. Otherwise they conflict.

Even Intel needs boot parameters and some very new Intel chips need the next kernel, support software and video driver from Intel.
       Possible boot options suggested by ubfan1
[http://ubuntuforums.org/showthread.php?t=2184839&p=12871710#post12871710](http://ubuntuforums.org/showthread.php?t=2184839&p=12871710#post12871710)

    
       Broadwell (future) fix for use with 14.04's 3.13 kernel. Fixes really in 3.15 kernel
[http://www.phoronix.com/scan.php?page=news_item&px=MTY0ODY](http://www.phoronix.com/scan.php?page=news_item&px=MTY0ODY)
Haswell improvements thru 2013
[http://www.phoronix.com/scan.php?page=article&item=intel_2013haswell_end&num=1](http://www.phoronix.com/scan.php?page=article&item=intel_2013haswell_end&num=1)

If you want lots of detail on differences between UEFI & BIOS.

 Technical info on Legacy BIOS and  UEFI AMI AptioMar 2012 -  20 MIn
[http://www.youtube.com/watch?v=dRMIvY7BiL4](http://www.youtube.com/watch?v=dRMIvY7BiL4)

Ubuntu & Windows only install in BIOS mode from MBR drives.
Windows only installs in  UEFI mode from gpt partitioned drives.
Ubuntu will install in either UEFI or BIOS from gpt partitioned drives.
Since they are not really compatible, how you boot install media is how it will install. Boot-Repair can convert an install from one version to the other by uninstalling grub-pc (BIOS) and installing grub-efi-amd64 (UEFI).

It has become more complex with secure boot, Windows always on hibernation and dual video systems. But even back in 2006, I had to manually configure nVidia and xorg.conf. Since then installs got easier, but part of that was experience both with my hardware & Ubuntu, as I know I have to use nomodeset and it is automatic for me. And on the occasion I forget it I know immediately when boot stops what my issue is.

Windows 7 DVD is BIOS only, you have to convert to flash drive and do updates to make it UEFI.

 Only 64 bit supported for UEFI boot
[http://www.sevenforums.com/tutorials/186875-uefi-unified-extensible-firmware-interface-install-windows-7-a.html](http://www.sevenforums.com/tutorials/186875-uefi-unified-extensible-firmware-interface-install-windows-7-a.html)
Prepare an usb thumb drive, to boot windows 7 in UEFI mode
[http://www.sevenforums.com/tutorials/186875-uefi-unified-extensible-firmware-interface-install-windows-7-a.html](http://www.sevenforums.com/tutorials/186875-uefi-unified-extensible-firmware-interface-install-windows-7-a.html)
[http://forums.lenovo.com/t5/tkb/articleprintpage/tkb-id/Beta_OS@tkb/article-id/177](http://forums.lenovo.com/t5/tkb/articleprintpage/tkb-id/Beta_OS@tkb/article-id/177)
[http://technet.microsoft.com/en-us/library/hh304353%28v=ws.10%29.aspx](http://technet.microsoft.com/en-us/library/hh304353%28v=ws.10%29.aspx)

---

### Post by Loki*PI on 2014-07-27
Again thanks oldfred, I read through the stuff and have tried numerous things. If I had your depth of understanding I could work through this, but I'm getting no joy and spending lots of time I don't have.

I don't remember how many times I've reinstalled both OSs. Using GDisk it showed numerous problems on the hd. Partitions that I didn't installed. Partitions that overlapped . Total partition size was way over the size of the hd. I was able to clear all that using GDisk more than once.  GParted always comes up with an error that there is an abandoned GPT table. I have cleared this with GDisk also. Then when I go back and check the Win7 installation on boot I get a screen full of machine language. I've told GDisk not to wipe the MBR but it is gone. Then when I reinstall Windows the strange partitions and GPT table reappears. 

I've set the BIOS to legacy only, UEFI only, and both. Each creates a different problem. I've put what free time I have into this for, I think now, 6 days. I did 18 years of IT. I started with MS Dos, did WFWG (anyone remember that?), etc. Honestly I don't remember how many MCSEs I have. I always did MS and CISCO, little bit of Linux, little Solaris. My point is that if I cannot make these to OSs play nice on a new box, in a resonable amount of time, something is wrong, too complicated, too many variables.

So here is my solution, not very elegant but . . .  I have 3 SATA drives, I'm going to install U-14 using two of them and Win7 on the other. 99% of my time I use Ubuntu, (I'm complaining a little here but what you guys have done is amazing). In that little bit of goof-off time I have I like to game. For those rare occasions I can reach in the box and disconnect the U-14 drives and connect up the Win7 drive. Not elegant but looking forward I see a never ending series of problems trying to dual boot. One OS has a problem and the other becomes toast. I don't have time for it.

I'll keep reading and maybe later, after some good backups, I'll try again.  Do like giving up on it.

---

### Post by webusr1 on 2014-07-27
Hi,
I had a somewhat similar problem with my new system. I had to re-install Windows 7 and Ubuntu to finally get dual boot working. What I learned was that I had to have Secure Boot OFF, and both installs (Win7 & Ubuntu) require UEFI mode when booting up with DVD for Windows 7 and for Ubuntu 14.04. I noticed that the Windows 7 OS had to have an "EFI" partition created in the hard drive. As I stated, that EFI partition was created during the Windows 7 install by booting the DVD device in UEFI mode. Once you install Windows 7 you will have a Windows partiton labeled EFI that you can verify in Ubuntu using Gdisk or Windows using diskmgmt.msc (see thumbnail). Remember you have to Shrink your drive to allocate space for Linux and at least create a root and swap partiton for Ubuntu. See that attached thumbnail and the output from Gdisk below. Notice that after the windows 7 install you will have patitions 1,2, and 3. Then, partitons 4 and 5 are for root and swap. You're really close to solving your problem. Don't give up now.

Found valid GPT with protective MBR; using GPT.
Disk /dev/sda: 1953525168 sectors, 931.5 GiB
Logical sector size: 512 bytes
Disk identifier (GUID): 23E5278E-3ED9-4D4E-8C94-CB1891768CFD
Partition table holds up to 128 entries
First usable sector is 34, last usable sector is 1953525134
Partitions will be aligned on 2048-sector boundaries
Total free space is 3437 sectors (1.7 MiB)

Number  Start (sector)    End (sector)  Size       Code  Name
   1            2048          [206847   100.0]("tel:206847%C2%A0%C2%A0%20100.0") MiB   EF00  EFI system partition
   2          206848          468991   128.0 MiB   0C01  Microsoft reserved part
   3          468992      1543923711   736.0 GiB   0700  Basic data partition
   4      1543923712      1937141759   187.5 GiB   8300  
   5      1937141760      1953523711   7.8 GiB     8200

---

### Post by oldfred on 2014-07-27
The Windows installer in BIOS mode converts a gpt partitioned drive to MBR(msdos). But does it incorrectly and creates lots of issues. It leaves the backup gpt partition table, so Linux tools see both MBR & gpt and fail or only offer to install to entire drive. Fixparts then is the better tool to just remove backup gpt table.

If you have multiple drives I really do suggest each operating system on each drive. And you do want to install so each drive can work without any other drive. Some suggest disconnecting all but the drive you are installing to, to make sure that is the case. With Ubuntu you have to use Something Else, so you have the option on which drive to install grub boot loader.

You still should install all systems in same boot mode, both UEFI or both BIOS. Otherwise you can only dual boot from UEFI/BIOS menu or perhaps one time boot key like f12 on many systems. Grub only dual boots systems installed in same boot mode.

I only have BIOS but now only use gpt partitioned drives with my Linux installs. I do have to have the bios_grub partition for BIOS boot, and I now add an efi partition even though I will not use it, but may move drive to a new system soon.

       UEFI install,windows 8 with Something Else screen shots
[http://www.everydaylinuxuser.com/2014/05/install-ubuntu-1404-alongside-windows.html](http://www.everydaylinuxuser.com/2014/05/install-ubuntu-1404-alongside-windows.html)
[http://www.everydaylinuxuser.com/2013/09/install-ubuntu-linux-alongside-windows.html](http://www.everydaylinuxuser.com/2013/09/install-ubuntu-linux-alongside-windows.html)
But I suggest using Windows to shink Windows and reboot Windows first. But do not create any partitions with Winodws disk tools.
[http://www.dedoimedo.com/computers/dual-boot-windows-8-ubuntu.html](http://www.dedoimedo.com/computers/dual-boot-windows-8-ubuntu.html)


 Install to external drive. Also any second drive. Or any install with Something Else
Also shows combo box with location of grub2 boot loader
[https://help.ubuntu.com/community/Grub2/Installing](https://help.ubuntu.com/community/Grub2/Installing)
Does not hightlight changing boot loader to sdb, but shows other install screenshots:
[http://askubuntu.com/questions/312782/how-to-install-ubuntu-on-separate-hard-drive-in-a-dual-boot](http://askubuntu.com/questions/312782/how-to-install-ubuntu-on-separate-hard-drive-in-a-dual-boot)
[http://askubuntu.com/questions/274371/install-on-second-hard-drive-with-startup-boot-option](http://askubuntu.com/questions/274371/install-on-second-hard-drive-with-startup-boot-option)
Install 14.04 Something Else explanation and screenshots (note boot load to VM, most may install to MBR of drive sda, or sdb)
[http://www.tecmint.com/ubuntu-14-04-installation-guide/](http://www.tecmint.com/ubuntu-14-04-installation-guide/)
And you want this screen to choose where to install the grub2 boot loader which is only available with Something Else or manual install
[https://help.ubuntu.com/community/Grub2/Installing#Installing_Ubuntu_to_a_Specific_Partition_.28.22Something_Else.22.29](https://help.ubuntu.com/community/Grub2/Installing#Installing_Ubuntu_to_a_Specific_Partition_.28.22Something_Else.22.29):

---

### Post by Loki*PI on 2014-07-28
Thank you oldfred and webusr1 for responding. I will read the references and return to this in the near future. For the moment I'll take the easy way out, I hope it will be easy. I'll mark this a solved though we know it isn't.

---

