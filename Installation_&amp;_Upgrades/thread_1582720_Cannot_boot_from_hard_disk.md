---
title: "Cannot boot from hard disk"
date: 2010-09-26
forum: Installation &amp; Upgrades
---

### Post by Rogue_417 on 2010-09-26
This afternoon I finally had the time to run this Ubuntu KK CD and load over my old xp/Jaunty J partition.  I had previously run the distro. through the CD, without harming my old partition.  On doing so the system consistently reported my Toshiba ATA 120 gig hard disk had multiple bad sectors and was failing.  As a true end user (who mucks only when necessary with the CLI) I just figured writing over the partition would end the failure.  To be sure I ran Memtest8.66 v2.11 from the LiveCD; everything checked out fine.  So I installed KK.  I got my six questions, took some time to help my daughter put on her shoes, took extra pleasure writing over that Windows partition, and voila I was done.

Or was I?  Why did it still have the "Install ubuntu 9.10 ISO" icon on the left hand side of the screen?  How did the CD come to whir when I tried starting apps like Open Office?  Something wasn't right.  So I rebooted, this time from the HDD.  The start up looked predictable - there's that PXE-E361 Media Test Failure on some cable, I've been staring at that since I built the dual partition.  But what's this?  PXE-MOF: exiting EXE ROM.  Huh?  Oh and then the letter j..

This is a Toshiba Satellite A105 with a 200 gH 1gig Pentium M.  When I boot the liveCD I get this trial environment that works fine.  When I try installing from it I can even see that I'm writing over the previous, whole 9.10 partition I created this afternoon.  Regardless when I boot from HDD I get that weird letter j..

I've checked on line for boot issues, and the forum too, but so far haven't seen an issue booting from the HDD, especially when the distro. is already loaded.  What am I missing here, and how do I install it from a live CD environment? :(

---

### Post by Herman on 2010-09-27
Ubuntu Lucid Lynx is a more stable 'LTS' version of Ubuntu and that would probably suit you better than Karmic Koala if you can afford the internet bandwidth to download another (newer) Ubuntu CD.
Ubuntu Karmic Koala was more of a ground breaking version of Ubuntu. It was the first to feature GRUB2, and GRUB2 was fairly new back when Karmic Koala was first released. It's still under development.
GRUB2 should be very good for people who don't like the command line too much. It's more automatic, (well... normally it is). It could be there's a bug that's causing you problems and trying an up to date version of Ubuntu might solve your problem.
The disk utility in Karmic was new back then too, and was at the time well known to be a little hypersensitive, it's still a useful indicator but I wouldn't rely on it too much.
The 'badblocks' command is useful for a second opinion.
Memtest 86+ is for testing your computer's RAM modules and not your hard disk, but it's a good idea to test your RAM too.

It seems like GRUB is not being installed in your hard disk's MBR. It could be due to a bug in Karmic Koala, but I wonder if it is being installed somewhere else by mistake maybe? Check to make sure you have no USB external flash memory drives plugged in or SD camera cards inserted just in case your computer's BIOS is reporting those as the first hard disk for some reason and GRUB is going to the wrong disk maybe.

---

### Post by Rogue_417 on 2010-09-27
Following your lead Herman I hit the CLI and typed "grub."  Oh look at that; it isn't installed!  So I install it, and run it.  Your website makes available a number of commands for grub 1.97 (sudo apt-get install only nabs me grub 0.97, oh well).  Thinking grub installed and ready to roll I hit ctrl-alt-del and restart, making sure to remove the CD so as to boot from the HDD.

Cute eh?

Well the Yukon PXE v. 3.03 (or is it 2.01?) doesn't think so, as that j.. shows up again.  Booting again from CD I see that no, grub is not in fact installed.  Sooo.. I'm confused.  If grub isn't installed how do I install it from the LiveCD environment to the HDD so it will boot from the HDD?  Your website provides a large number of grub commands.  Perhaps you might help a fresh young bean (Okay, not quite so young) find the right combo.. ?

---

### Post by Rogue_417 on 2010-09-27
I open the terminal - 

To run a command as administrator (user "root"), use "sudo <command>".
See "man sudo_root" for details.

ubuntu@ubuntu:~$ ls /boot/grub/
grubenv
ubuntu@ubuntu:~$ grub2
No command 'grub2' found, did you mean:
 Command 'grub' from package 'grub' (main)
grub2: command not found
ubuntu@ubuntu:~$ sudo apt-get install grub2
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package grub2 is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
However the following packages replace it:
  grub-pc
E: Package grub2 has no installation candidate

Okay, so I apt-get install grub, just grub.  It installs.  I type ctrl-alt-del and restart, removing the cd to see if perhaps it has auto-installed (or some such thing) to the MBR.  Nope; Yukon PXE 3.03 (or is it 2.01?) is still clueless, bringing in that damned j..

I boot from the CD, give the ls command from terminal, and lo and behold grub isn't there!  I have to install it again!   Grrr.. So how do I enter the right grub version to the MBR of the HDD, rather than the LiveCD environment?

---

### Post by Herman on 2010-09-27
The Ubuntu Live CD boots with isolinux, like most Live CDs. It's possible to make a LiveCD boot with GRUB, I don't know why they don't, maybe it takes too much space or something. 
It is possible to install software in a Live CD, but it only lives in the computer's memory for the duration of one session and is lost on reboot, so it's no use installing GRUB in the Ubuntu Live CD. 

Alternative 1
You can, however, install GRUB using your Live CD if GRUB is already installed in Ubuntu but just didn't make it to the MBR for some reason.
If you boot your Ubuntu Live CD and take a look inside your Ubuntu hard-disk-installed operating system and you can see files in /boot/grub, you can follow the steps outlined in the following linked thread, [Computer won't boot to 9.10; No Grub Menu]("http://ubuntuforums.org/showthread.php?t=1306900"), Moderate command line ability required

Alternative 2
If you boot your Ubuntu Live CD and take a look inside your Ubuntu  hard-disk-installed operating system and you do not see files in  /boot/grub, you may need to take a look at the following Ubuntu Web Forums thread: [how to chroot, simple and fast]("http://ubuntuforums.org/showthread.php?t=1156240"), by taavikko and 'sudo apt-get install grub-pc'. That should be easy enough for users experienced with the command line but may test ability and patience for those who are learning. Maybe skip this and use for a last resort if you're not into command line work.

Alternative 3 - Easier for new users:
Download an .iso for a [Parted Magic Live CD]("http://partedmagic.com/"), burn it to disk, and look for the option in the boot menu to go to Super GRUB2. 
Or, download a Super Grub Disk, [Super Grub Disk]("http://developer.berlios.de/projects/supergrub/").
Use Super GRUB2 to boot your Ubuntu with (from the Live CD).
Once your hard-disk-installed Ubuntu is up and running, re-install GRUB with 'sudo grub-install /dev/sda'. 
That should fix it. (I hope). :)

---

### Post by Rogue_417 on 2010-09-28
Herman I appreciate the alternatives you've outlined above.  

Alternative 1: Can you tell me how to find grub in the hdd installed os?  ls /root/grub as I outline above brings me a grub-env.  What is that?  Your previous correspondence on this involves "mounting" the hdd installed os.  Would that be mt /dev/sda or some such thing?

Alternative 2: "Jailed copies" of an os?  Is that like a bondage inspired version of a virtual box?  Just kidding!  So essentially I'd load grub-pc inside this chroot copy, yes?

Alternative 3: I currently have one CDRW; not such an option.

ALTERNATIVE 4: download an .iso for Lucid Lynx, save it to my Passport drive, and install it from there.  It SOUNDS good, and could ostensibly solve the hypersensitive grub2 issue.  Can I install an os from a USB drive to a system running on a LiveCD?

---

### Post by lisati on 2010-09-28
> **Rogue_417 said:**
> Following your lead Herman I hit the CLI and typed "grub."  Oh look at that; it isn't installed!  So I install it, and run it.  Your website makes available a number of commands for grub 1.97 (sudo apt-get install only nabs me grub 0.97, oh well).  Thinking grub installed and ready to roll I hit ctrl-alt-del and restart, making sure to remove the CD so as to boot from the HDD.


Grub/grub2 isn't something you run from the terminal, it's meant to be run when the computer starts..... :D

---

### Post by oldfred on 2010-09-28
One of the best ways to see what is installed where. You can run from liveCD or most installs:

Boot Info Script courtesy of forum member meierfra
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste results.txt, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the post's menu and then paste the contents between the generated [ code][ /code] tags.

---

### Post by Rogue_417 on 2010-09-28
Herman I followed your advice from your 10/30/2009 'Computer won't boot' exchange - however I couldn't rename the partition  :( 

ubuntu@ubuntu:~$ sudo grub-setup -d /media/2e55a127-04b7-46d1-8d42-b4f501a3a012/boot/grub dev/sda
grub-setup: error: Cannot open `/boot/grub/device.map'
ubuntu@ubuntu:~$ sudo grub-setup -d /media/2e55a127-04b7-46d1-8d42-b4f501a3a012/boot/grub -m /media/2e55a127-04b7-46d1-8d42-b4f501a3a012/boot/grub/device.map dev/sda
grub-setup: error: Cannot open `/media/2e55a127-04b7-46d1-8d42-b4f501a3a012/boot/grub/device.map'
ubuntu@ubuntu:~$ sudo grub-setup -d /media/2e55a127-04b7-46d1-8d42-b4f501a3a012/boot/grub -m /media/2e55a127-04b7-46d1-8d42-b4f501a3a012/boot/grub/device.map dev/sda1
grub-setup: error: Cannot open `/media/2e55a127-04b7-46d1-8d42-b4f501a3a012/boot/grub/device.map'
ubuntu@ubuntu:~$ 

You then recommend investigating the CMOS "and disabling any MBR write-protect feature you may have left enabled, it may also be called something like 'boot sector antivirus' or some other name."  How do I do that?  Oh and every time I load the LiveCD it gives GMT, not our Central Standard Time.  Could I have an issue with CMOS?

---

### Post by Herman on 2010-09-29
I don't think you'll need to do anything in your BIOS since you have had  your MBR written previously by Jaunty Jackalope successfully, or at  least I presume so.
I'm not sure if your displayed time could indicate a problem or not, a  weak motherboard battery can cause some weird problems, but I have also  noticed that sometimes the time is not displayed correctly or it's not  local time when running a live CD.

You weren't able to set a label for your file system?
Maybe you should try meierfra's script as oldfred suggested, it might reveal some clues about why your computer seems to be having so many difficulties. Maybe the Disk Manager was telling the truth and maybe you really do have a flaky hard disk?

Here is a test that reads the hard disk's own log files and reports on the condition of the hard disk, it runs on smartmontolls which Disk Manager uses,
```
sudo smartctl -a /dev/sda >> harddisk.report 
``` That report, (if successful), will be filled with information about your hard disk that is difficult for most people to understand, but may be interesting nevertheless.

Here's a command for testing for bad blocks (areas where the disk's magnetic properties are getting weak) in your hard disk,
```
sudo badblocks -sv /dev/sda1 >> badblocks.report
```That command will only check your first partition, but that should be enough to start with.
It takes a long time for that command to run, so if you don't see anything happening, just leave it for a while and eventually it will finish and there will be a file called 'badblocks.report. If that file is empty, your hard disk has passed, if it is full with a big long list of bad sectors, then you probably need to new hard disk.

If your hard disk passes, then you probably just have software problems and you might need to look those other three alternatives to continue trying to solve your problem.
If you can, try to get yourself some blank CDs and/or even a flash memory stick of over 4 GB, you will find that those can save you a lot of work if you can possibly get them somehow, especially if you like to avoid typing commands. I'm sorry for suggesting so many commands to you already. :)
EDIT: You are doing very well for a person who doesn't like using commands, thank you for your patience and persistence so far.

---

### Post by Rogue_417 on 2010-09-29
Oh Herman thank YOU for your patience and involvement!  You have helped me decide my next steps - 

1. Download Lucid Lynx to my Passport drive.
2. Run smartctl and badblocks and bring the output back here for analysis.
3. Unless I report issues I'll load LL from the USB drive.

Believe it or not I've been running some form of Linux from home since 2003.  However while I feel comfortable executing simple commands a real grasp of the shell, much less a computer's anatomy escapes me.  Family, business (not in computing or networking, but medical sales mind you) and volunteer work leave me enough time to fix what's broken and not much more.  And as you know, no play = no learn linux.  So its been through the kind auspices of users like you and oldfred (and SnowDog, Vinnywright et al on the Kubuntu forums) that I muddle through.  I will close this post and open a new one once I've hit the points above.  Wish me luck!

---

### Post by Herman on 2010-09-30
:) That sounds like a good plan, Rogue_417, because the GRUB boot loader has improved a lot between the time Karmic Koala was released and Lucid Lynx's release date. 
GRUB2 was one of the new programs in Karmic, so a few teething problems are par for the course. Lucid Lynx is an 'LTS' version of Ubuntu which the developers put a lot more effort into debugging as opposed to introducing new programs.  I think Lucid Lynx will suit you a lot better and if it's software problems that you are experiencing, there's a good possibility that those would have been fixed in Lucid Lynx.
The badblocks command should show any problems with your hard disk.
Good luck with it and I hope we'll be hearing from you again soon! :)

---

### Post by Rogue_417 on 2010-10-01
PS: After the challenge of downloading the Lucid Linx Live CD, and an interesting first boot, the second install went smoothly.  I'm in with the Linx and moving right along.  Thanks again for the help!

---

### Post by Herman on 2010-10-02
:cool: Cool!

---

