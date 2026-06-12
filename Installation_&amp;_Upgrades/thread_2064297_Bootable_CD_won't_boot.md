---
title: "Bootable CD won't boot"
date: 2012-09-28
forum: Installation &amp; Upgrades
---

### Post by mantisdolphin on 2012-09-28
Some background here: [http://ubuntuforums.org/showthread.php?p=12267344#post12267344.:sad:](http://ubuntuforums.org/showthread.php?p=12267344#post12267344.:sad:)

I was going to install Mint, but the DVD wouldn't boot.  So okay, I'll install Ubuntu.  The live CD won't boot.  I've checksummed the ISO file for ubuntu-12.04.1-desktop-amd64.iso.  

How do I go about figuring out what's wrong?

Thanks!

[system info]
 Microsoft Windows 7 Home Premium [sucks] 
 Version 6.1.7601 Service Pack 1 Build 7601 
 System Manufacturer Dell Inc. 
 System Model Studio XPS 9100 
 System Type x64-based PC 

 Processor Intel(R) Core(TM) i7 CPU 930 @ 2.80GHz, 2801 Mhz, 4 Core(s), 8 Logical 

 Installed Physical Memory (RAM) 9.00 GB 

 NVIDIA GeForce GTX 560 SE 

 Realtek High Definition Audio

 Drive C: 
 Description Local Fixed Disk 
 Compressed No 
 File System NTFS 
 Size 1.35 TB (1,487,107,256,320 bytes) 
 Free Space 887.15 GB (952,568,496,128 bytes)

---

### Post by agillator on 2012-09-28
Start by checking the boot sequence in your bios. Make sure the cd/dvd drive is listed in the boot sequence and it comes before anything else that might be present and contain bootable media.

---

### Post by mantisdolphin on 2012-09-28
Thanks for the reply.  On the initial starting screen, after power-up, Dell offers two options: F2 for setup and F12 for bootable device.

I install the CD and hit F12 and...hang, cursor-blink. I.e., I put in Ubuntu CD in the DVD/CD drive, turn on the power, hit F12, and I see a little person icon and I think a keyboard at the bottom of a screen that I think is Ubuntu trying to boot.  Then the screen goes blank with a cursor blinking, and that's all that ever happens.

With Unetbootin I created a pendrive version of Ubuntu 12.04.1 64-bit, but that would not boot.

Then I saw some advice on other forums about trying some different flavors of Linux.  I downloaded Crunchbang and Suse.  I burned an ISO of Crunchbang stable 64-bit.  It loaded.

Crunchbang ain't pretty, but I'm trying it out on a new second harddrive.

I'd like a more user-friendly, more polished Linux.  What's up with my Ubuntu CD and pendrive?  Is there any information I can provide about my hardware that might help?

Thanks!

---

### Post by agillator on 2012-09-29
How long are you waiting before you decide nothing is happening? Sometimes live cds take a very long time to boot and they don't show what they are doing. Other than that I can only guess there is something wrong with the cd itself since you are able to get at least one to boot. What is the source of the cd? Did you burn it yourself on the same drive you are using to read it? Once you machine is booted in any OS, can you load the cd and read it?

---

### Post by doktorOblivion on 2012-09-29
You do know the little person and keyboard icon is expecting you to hit a keyboard key, did you?

---

### Post by mantisdolphin on 2012-09-29
Thanks for the replies!!  :)

At one attempt I waited for 30 minutes plus for the cursor to show some other sign of life.

I got the ISO file from Ubuntu and the CD comes from a stack of them that I've used successfully for a variety of music files and ISO burns (e.g., my 4-year old is running Ubuntu Cinnamon on an old desktop he watches Mario runthrough videos and plays Lemmings and Pengu and Supertux on it!  lol.  I burned that disk this past summer with same equipment/software that I'm using now.) 

Yes, I did burn the CD on the same drive that I'm using to read it.  Sounds odd, but I think you have a real point there with that.

"Once you machine is booted in any OS, can you load the cd and read it?" 
Yes.  The disk will even come up with the Wubi.exe dialogue box in Windows, and I see the Ubuntu icon for the disk when I'm in the file manager. 

"You do know the little person and keyboard icon is expecting you to hit a keyboard key, did you?"

I can't say that I really knew that.  I think I've tried hitting a key at that time, when that screen shows, and nothing happened, so I have also tried just letting the install proceed with no intervention from me at all.  I will try to boot the CD again and hit a key when I see the little dude and keyboard icons to be sure.

---

### Post by oldfred on 2012-09-29
The accessibility icons only show for a few seconds and then it boots. But if you need boot parameters or any special settings you have to hit the "any"  :) to get to the menu.

With nVidia you have to hit any key and then f6 choose nomodeset. Some new systems like yours may need other settings also.

How to set NOMODESET and other kernel boot options in grub2 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

---

### Post by gordintoronto on 2012-09-29
[http://askubuntu.com/questions/162075/my-computer-boots-to-a-black-screen-what-options-do-i-have-to-fix-it](http://askubuntu.com/questions/162075/my-computer-boots-to-a-black-screen-what-options-do-i-have-to-fix-it)

---

### Post by mantisdolphin on 2012-09-30
Hitting the any key and F6 and selecting nomodeset did the trick.  So should I mark this Solved?  B/c I ran into a problem.

When I installed Ubuntu onto the second harddrive, overwriting Crunchbang, I could no longer boot my machine.

So, Boot Repair Disk to the rescue...AND I got Windows back up and booting, but without a dual-boot.  

Here's my boot info summary:

 => Syslinux MBR (3.61-4.03) is installed in the MBR of /dev/sda.
 => Grub2 (v1.99) is installed in the MBR of /dev/sdb and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for (,msdos1)/grub on this drive.
 => No boot loader is installed in the MBR of /dev/sdg.

[Full summary here: [http://paste.ubuntu.com/1252850/]](http://paste.ubuntu.com/1252850/])

---

### Post by oldfred on 2012-09-30
Glad you got it working.

You have noticed this? Windows only works well with 30% free.

> sda2 is 98 % full Warning: unknown mime-type for "/mnt/boot-sav" -- using "application/octet-stream" Error: no "view" mailcap rules found for type "application/octet-stream" The sda2 (Windows 7 (boot)) partition is still full. This can prevent to start it (e.g. you may get a Power Manager error). mount: special device /run does not exist

---

