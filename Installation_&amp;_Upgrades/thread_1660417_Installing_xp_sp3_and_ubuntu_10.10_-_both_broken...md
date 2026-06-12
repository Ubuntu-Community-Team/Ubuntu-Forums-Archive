---
title: "Installing xp sp3 and ubuntu 10.10 - both broken..."
date: 2011-01-05
forum: Installation &amp; Upgrades
---

### Post by Relief on 2011-01-05
Okay... so this is what I have done twice now...

I am rebuilding my computer with new raptor drives (yay) and wanted an install of both xp and ubuntu since it's a house computer and don't want the roommates using a windows os to go online. That being said here is what is happening. 

I have partitioned the drive into three parts, first part is the XP partition, it's 15 gigs large, then there is the partition for files which is 110 gigs, then there is another 15 gig partition for ubuntu. So it looks like this 

XP NTFS -------------- 15 gigs
Shared space NTFS --- 110 gigs
Ubuntu ext4 journal -- 15 gigs 

So first I install XP and create the partitions without formatting the back end 15 gigs, just the first two. Once it's installed I check and make sure XP runs fine, loads, reboots, etc, then move onto Ubuntu. I load the disk, and manually choose the unformatted 15 gig partition and use the ext4 file system. It formats and installs Ubuntu (i have Ubuntu set to download updates). At this point everything is great, it's done and says to restart, so I say, YES! And here is where things get weird, it goes through the reboot mode and then I see a bunch of sector errors and it hangs for awhile, then eventually completes the reboot... here is the kicker:

If I load XP I see this 
"Windows could not start because the following file is missing or corrupt: 
<Windows root>\system32\ntoskrnl.exe.
Please re-install a copy of the above file"

Here is what happens if I load Ubuntu:
It loads up to the login screen, I can login, but then nothing... nothing at all, it just hangs up. 

I have now tried this twice, thinking that something just got corrupted on a format or install... but now I'm not sure and don't want to keep installing over and over. 

So.... any ideas? Is installing Ubuntu on the back end of the drive causing issues? Is there a better way to install Ubuntu rather than the way I have things partitioned? 

Thanks, 
- Relief

---

### Post by Relief on 2011-01-06
anyone?

---

### Post by pricetech on 2011-01-06
I'd use a larger partition, but that's just me.

I'd start with XP and not partition the rest of the drive, then let Ubuntu create its partition next, then create the shared data partition after that, using whichever OS you prefer.

See if that make a difference.

---

### Post by Relief on 2011-01-07
Quick question: I am currently setting up ubuntu again and was wondering where the boot loader should be mounted, here are the options

sda1 NTFS 15360megs
sda5 ext4 mount point / 15360 megs
-- I left 11875 unpartitioned 
or /dev/sda ATA wdc wd 1500HLFFS-0 (150gigs)

those are the three options, I have been telling it to install on the last option, is that wrong?

---

### Post by Relief on 2011-01-07
Here is the error I see after the installtion is complete and it asks to restart:

2.311228] end_request: I/0 error, dev sr0, sector 533512

It shows this error in many sectors...

---

### Post by Relief on 2011-01-07
sorry, double post.

---

### Post by Relief on 2011-01-07
sorry, double post.

---

### Post by oldfred on 2011-01-07
Does it give that error after it pops the CD out? It is a minor bug and supposed just pressing enter works. It is still trying to shutdown something on the CD (dev sr0) but it is missing as it already was ejected.

You should install grub only to the MBR or the drive. /dev/sda and not to any partitions.

---

### Post by Relief on 2011-01-07
> I'd use a larger partition, but that's just me.

I'd start with XP and not partition the rest of the drive, then let Ubuntu create its partition next, then create the shared data partition after that, using whichever OS you prefer.

See if that make a difference. 

Just tried that, didn't make a difference... still the same issues. I setup the windows partition and installed and left the rest of the drive unformatted, then had ubuntu setup it's own partition and share space then install; I get the same windows missing file problem:

"Windows could not start because the following file is missing or corrupt:
<Windows root>\system32\ntoskrnl.exe.
Please re-install a copy of the above file"

And I can make it to the login screen for ubuntu, but it will not actually login... just hangs up. 

Any thoughts?

> Does it give that error after it pops the CD out?

The CD is out, and the installation is asking to restart. Once that happens it goes to a black screen with information on the shutdown, and before it ends it comes up with those errors. 

Thanks
- Relief

---

### Post by oldfred on 2011-01-08
Have you tried the recovery mode that should boot to a command line. You may have the very common video issues problem. What video card do you have? 

If nvidia you can add nomodeset to the linux line in grub to see if it will load a low quality video mode.

On first boot after install, press e on getting the GRUB bootloader. 
Hold shift from BIOS boot to get menu if only one system installed.
Using arrow keys navigate to and delete quiet and splash and type the word nomodeset in their place
Press Ctrl and X to boot (low graphics mode)

After I installed Nvidia driver (default from pop up) then it has worked without issue.
gksudo nvidia-settings
Or it should be in System>administration>Hardware drivers.

---

### Post by Relief on 2011-01-08
> Have you tried the recovery mode that should boot to a command line. You may have the very common video issues problem. What video card do you have?


Well that helped a bit. The card I have is a ATI x1600, I did as you suggested and ubuntu will load when booting like that but if I try to restart, I get the same problem as before. Also, the Radion x1600 cards don't seem to have a driver set... Also, no matter how I format and install, Ubuntu destroys my xp partition, for whatever reason it corrupts system files and xp no longer is bootable... here are the things I have tried:

Install xp and set up partitions, install ubuntu... kills xp
install xp and don't set up other partitions, let ubuntu set up the remaining partitions... kills xp
Install xp on a larger partition and let ubuntu's partition shifter do it's thing... kills xp....

I'm at a loss here....

Any thoughts?

Thanks
- Relief

---

### Post by oldfred on 2011-01-09
When you say it kills XP, I do not understand what is not working with XP. Sometimes a fix or two is required for XP, but as long as you do not totally overwrite the entire drive the XP partition should be there & bootable.

So we can see your entire configuration.

Boot Info Script courtesy of forum member meierfra
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste results.txt, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the post's menu and then paste the contents between the generated [ code] paste here [ /code] tags.

---

