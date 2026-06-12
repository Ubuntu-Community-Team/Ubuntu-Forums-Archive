---
title: "Installing Ubuntu alongside Windows 10 and Mint 18"
date: 2016-11-12
forum: MINT
---

### Post by elogikal on 2016-11-12
Hi guys,

Trying to set my HP Envy X360 to tri-boot into Windows 10 Enterprise, Mint 18 and Ubuntu.  I currently have Win10 and Mint dualbooting using GRUB 2.02.  I would like to also install Ubuntu with Win10 being primary OS.  I have GRUB Customiser which I have set up to boot to Win10 by default and everything is working great.  I don't want to mess anything up in my partitions or other OS installations during the install.  I am relatively new to Linux drive partitioning and set up so before I do anything stupid I am asking for your help in helping me achieve what I am trying to.  I would like to primarily keep my HDD dedicated to Win10.  My Mint setup is currently partitioned for 29 GB or so with an 8 GB swap.  Preferably I would like 32 GB dedicated to Mint and 32 GB dedicated to Ubuntu and the rest to Win10.  Can anyone please provide me with a step by step on how to achieve this?  Any and all help is greatly appreciated.  I have attached screenshots of how the HDD is partitioned in both Windows and GParted.  Thanks again guys!!!

---

### Post by wildmanne39 on 2016-11-12
*Thread moved to **MINT**.*

---

### Post by oldfred on 2016-11-15
I might suggest 25GB for each Linux system as that is what I do. Your swap is probably large, unless you want to hibernate. But if you hibernate you cannot share swap between Linux and default install in Ubuntu will auto mount/use the swap you already have.

Then create a large NTFS shared data partition for all 3 systems and maybe a shared ext4 data partition for any data you may want to share in Linux only.
Back when still using XP I have shared NTFS with all my photos, Firefox & Thunderbird profiles & various text files folders. Then I could see & use data in whatever system I was booted into. Made conversion to Ubuntu easier.

Because your NTFS partition is a primary, you have to shrink it. Use Windows to shrink NTFS & boot Windows immediately so it can run chkdsk & update to its new size. Do not create partitions with Windows, but use gparted. You will have to move/expand extended partition left to include the new unallocated into the extended partition & then can make as many logical partitions as you want.

---

### Post by elogikal on 2016-11-17
Thank you for the response.  I guess the real issue comes when trying to install.  It only shows that Mint is installed.  Screenshots posted below.  Suggestions?

---

### Post by oldfred on 2016-11-17
Have you turned off Windows fast start up or hibernation?
And since both installs are BIOS, you need to install Ubuntu in BIOS mode.
With new UEFI system you can boot install in either UEFI or BIOS boot mode, so you must boot installer in BIOS mode.

You want the BIOS screen.
 Shows install with screen shots. Both BIOS purple accessibility screen & UEFI black grub menu screen
 [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI) 

      
 Fast Start up off (always on hibernation)
[http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472](http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472)
[http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html](http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html)
[http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html](http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html)

---

### Post by elogikal on 2016-11-22
Thank you again for the suggestions.  I've now run into an even larger issue.  Initially when asking this question I already had Win10 and Mint.  I did a fresh install of Win10 and now I can't even get any Distro to even load into Live mode.  If I boot in UEFI mode it shows the GRUB menu and when I select Boot *distro* now, the USB will flicker for about 5 seconds likes it's trying and then stop and nothing happens but black screen, if I boot in regular BIOS mode it will just go black screen and nothing else.  This has happened with Mint Cinnamon, Mint KDE, Ubuntu, Kubuntu and ElementaryOS.  The BIOS is up to date, Legacy turned on, Secure boot off, fast start turned off within Win10, boot order correct, etc.  I'm at a loss bc I did have dual boot and now no combo of BIOS settings is even letting me get back to that point.  It's very frustrating.  I've also attempted creating my media with LiLi, Rufus and Unetbootin all with the same results except Lili and Rufus show GRUB2 and Unetbootin shows a more old school DOS like select screen with the same options.  HELP!

---

### Post by elogikal on 2016-11-22
If I remember correctly though, in my previous dual boot  installation I believe that Hibernate was still on for some reason in Win10.  Not 100% positive but I feel like it was still there when there were no issues.  Also another BIOS setting that I read about in my research was USB 3.0 which should be set to Auto instead of Enabled which has been toggled but to no avail on any combo of BIOS settings.

---

### Post by yancek on 2016-11-22
The GParted image in post 1 above shows there is no space to install a  new system so your first step would have to be booting into windows and  shrinking it's large partition to make unallocated space on which to  install.  Have you done that?  It also shows an Extended partition which means it is an MBR install.

The image on the left in post 4 shows you have Install Alongside selected.  Don't do that as you already have two OS's installed, use the manual method which is Something Else.
The second image in post 4 shows you are booting the installation DVD/flash drive in UEFI mode, don't do that as you have an MBR install and that will mess things up.  See the link below which explains booting UEF or MBR.

 [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

---

### Post by oldfred on 2016-11-22
Usually black screen is  a video issue.
What video card/chip?

       At grub menu you can use e for edit, scroll to linux line and replace quiet splash with nomodeset.
How to set NOMODESET and other kernel boot options in grub2 - both BIOS liveCD & grub first boot ( also UEFI with grub) 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
How to add boot parameters,  grub menu after install (also grub when UEFI)
[https://wiki.ubuntu.com/Kernel/KernelBootParameters](https://wiki.ubuntu.com/Kernel/KernelBootParameters)

Did you reinstall Windows in BIOS or UEFI boot mode? 
How you boot install media for both Windows & Ubuntu is then how it installs.

---

### Post by elogikal on 2016-11-22
It's a Intel(R) HD Graphics 5500.  Nothing special obviously.  The thing that perplexes me is that I has zero issues installing on my last clean install of Win10.  I used the same iso file and everything.  I'm not really convinced it would be a video issue though considering that the flash drive just stops blinking after 5 seconds like it's not being accessed anymore...

---

### Post by oldfred on 2016-11-22
UEFI may have USB settings to allow boot?

But if you get grub menu from flash drive and not from hard drive then it should be ok. But grub menu would be an UEFI boot. If you want BIOS you have to get purple screen. 
       Shows install with screen shots. Both BIOS purple accessibility screen & UEFI black grub menu screen
 [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

---

### Post by elogikal on 2016-11-23
I get to GRUB in UEFI but I only get the option to install, install for OEM or check drive for errors, no try option and when I choose install is when I get the black screen with an unresponsive flash drive.  I don't get the purple screen in BIOS mode, just black screen.

---

### Post by oldfred on 2016-11-23
Is this the server version, as it has no live mode? Only the standard Desktop flavors have live mode.

What video card/chip? You may need nomodeset.

       At grub menu you can use e for edit, scroll to linux line and replace quiet splash with nomodeset.
How to set NOMODESET and other kernel boot options in grub2 - both BIOS liveCD & grub first boot ( also UEFI with grub) 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
How to add boot parameters,  grub menu after install (also grub when UEFI)
[https://wiki.ubuntu.com/Kernel/KernelBootParameters](https://wiki.ubuntu.com/Kernel/KernelBootParameters)

---

### Post by elogikal on 2016-11-23
It's Kubuntu 16.04 LTS but I have the same issue with standard LTS Mint Cinnamon and KDE variants and Ubuntu.  It's a Intel HD 5500 built into the motherboard.

---

### Post by elogikal on 2016-11-23
I've also tried with persistence and no persistence on all OS install attempts.

---

### Post by oldfred on 2016-11-23
I have not installed Kubuntu nor Mint, but thought installer was essentially the same with different graphics/colors.
Post exact ISO you downloaded.

---

### Post by elogikal on 2016-11-23
nomodeset did not work either and provided the same result.  This is the link to the torrent file for the iso I used:  [http://cdimage.ubuntu.com/kubuntu/releases/16.04.1/release/kubuntu-16.04.1-desktop-amd64.iso.torrent](http://cdimage.ubuntu.com/kubuntu/releases/16.04.1/release/kubuntu-16.04.1-desktop-amd64.iso.torrent)

---

### Post by oldfred on 2016-11-23
I do not understand what is different, other than now you reinstalled Windows.
Install of Ubuntu should not be a lot different than Mint. Never installed Mint but those that have seem to be very similar.

Are you able to boot in any mode?

---

### Post by elogikal on 2016-11-23
I am at a loss as well.  No matter what distro it is, it's the same thing.  Choose to install and then black screen with flash drive unresponsive.  I installed Windows using the same flash drive so I know the flash drive is okay.  Unfortunately, I don't have another drive to try and this laptop does not have a DVD drive.

---

### Post by oldfred on 2016-11-23
I do not see anything consistently different with other HP Envy, but that seems to include many different models.

 HP Envy 700-430QE desktop used bcdedit to dual boot
[http://ubuntuforums.org/showthread.php?t=2260681](http://ubuntuforums.org/showthread.php?t=2260681)
Boot Ubuntu 14.04 LTS 64-bits on external hdd - HP Envy 17 w/Windows 8.1 Details
[http://ubuntuforums.org/showthread.php?t=2256244](http://ubuntuforums.org/showthread.php?t=2256244) 

 HP Envy M6
[http://askubuntu.com/questions/346257/install-alongside-windows-8-is-not-working](http://askubuntu.com/questions/346257/install-alongside-windows-8-is-not-working)
HP Envy - Legacy boot seems to mean either UEFI or Legacy depending on which is found to boot from
[http://ubuntuforums.org/showthread.php?t=2167063](http://ubuntuforums.org/showthread.php?t=2167063)
Installing Ubuntu on HP Envy-6  Details of what worked post #11
[http://ubuntuforums.org/showthread.php?t=2123975](http://ubuntuforums.org/showthread.php?t=2123975)

---

