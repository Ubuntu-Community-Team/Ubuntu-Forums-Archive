---
title: "Attempts to upgrade from 18.04 to 20.04 result in EFI error"
date: 2020-11-09
forum: Installation &amp; Upgrades
---

### Post by Stan_Meissner on 2020-11-09
I have been a Ubuntu user for ten years but any time it becomes apparent that an issue will require anything beyond the basic terminal commands to resolve I am lost and require help.  This time I got a notice that 20.04 was available and I elected to install it but was stopped a few minutes into the process by the following error message:     "EFI System Partiton (ESP) not usable
Your EFI System Partition (ESP) is not mounted at /boot/efi. Please ensure that it is properly configured and try again."

I did a little bit of research and came across threads full of commands that are way over my head. Now what do I do?  Any instructions will have to assume that I am an end user so if you're asking me to enter a command and post the results I'll need an explanation how to do it.  I have a purpose built Ubuntu system purchased from Zareason and my wife has a System76 laptop so I may be facing the same situation with that.  Ironically my old junky Dell laptop that I use to look things up in the garage running on Xubuntu upgraded with no issues.

---

### Post by CelticWarrior on 2020-11-09
> [COLOR=#000000]"EFI System Partiton (ESP) not usable[/COLOR]
[COLOR=#000000]Your EFI System Partition (ESP) is not mounted at /boot/efi. Please ensure that it is properly configured and try again."[/COLOR]

Are you dual-booting with Windows? If so, boot Windows and disabled Fast Startup.

---

### Post by ubfan1 on 2020-11-09
First thing to determine is if the system to be upgraded is really in UEFI mode. That's pretty likely these days, but  an old machine may have started in legacy, and upgrades kept that mode -- until 20.04, where I think a bug has been reported on legacy upgrades failing because no efi ...

---

### Post by Stan_Meissner on 2020-11-09
I purchased my desktop from Zareason approximately two years ago and it is not a dual boot system and is only running 18.04.  What is UEFI mode and how do I determine that?  This is a relatively new computer and was purpose built for Linux.  My wife's System76 laptop is only a couple years old as well but I have not attempted to upgrade to 20.04 on that one.  Basically I am attempting an upgrade on a two year old purpose built for Linux tower style so this is some like of issue with the default settings in 18.04 preventing an upgrade to 20.04 as at my user level I would not have changed any settings that would cause this error.

This is the reason that I purchased purpose built Linux computers shortly before I retired.  So that I wouldn't be stuck with error messages trying to get Linux to work in an old Windows computer.  Ironically the old ten year old Dell laptop give to me for free that I use out in the garage that runs on Xubuntu upgraded with no issues.  My desktop computer purpose built for Linux is the one getting the error message.  I want to get this one resolved before I attempt it on the System76 laptop.  None of my computers are dual boot but I do run a few old Windows programs on the Wine layer and that is as close as I get to Windows anymore.

---

### Post by ajgreeny on 2020-11-09
Run command ```
[ -d /sys/firmware/efi ] && echo UEFI || echo BIOS
``` and the output will tell you if you are booted to BIOS or UEFI.

Copy and paste the command to make sure you get it right, and to ensure you don't miss the first [

If the machine is only 2 years old I think you will find it to be UEFI.

---

### Post by Stan_Meissner on 2020-11-09
It's showing UEFI.
```

stan@stan-MS-7A37:~$ [ -d /sys/firmware/efi ] && echo UEFI || echo BIOS
UEFI
stan@stan-MS-7A37:~$
```

---

### Post by ubfan1 on 2020-11-09
Good, base macihne boots in UEFI mode. Now perform the same test on the booted install media (Select "Try" mode, and start a terminal).  Booting mode may be either/or or prefer one over the other, depends upon the machine.  If your machine only ever had UEFI bootloadfers, but the UEFI Settings preferred legacy, you would never know, until you booted a media with both boot modes possible.

---

### Post by Stan_Meissner on 2020-11-09
I appreciate the suggestions but I don't think you're understanding me.  I am attempting an online upgrade as prompted by the software updated and not trying to install from a thumb drive or disc.  I accept the upgrade, it starts the download and errors out with that message.  If I was trying to upgrade to 20.04 by the regular installation method that wipes out all my data would that even produce this kind of error message?  Anyways, I am simply trying to do the upgrade to 20.04 using the software option so I don't end up wiping out my existing files.  Speaking of existing files I'm glad it came up as I have a few new files that aren't backed up to my external drive.  The way this is going I probably should do that.  I'm pretty sure that I started with 16.04 and upgraded that way to 18.04 which makes this latest issue even more baffling.  I've got a printer that can be a bit of a bloodbath to get the generic drivers properly configured and a few other similar issues so I was hoping for a smooth upgrade based on past experience.  So anyways, I do pretty well keeping this thing running but you lost me after start a terminal session and it looks like you're saying to do that in "try" mode with Ubuntu upgrade saved to removable media.

---

### Post by ubfan1 on 2020-11-09
Sorry, no need to check with the upgrade, but if you do reinstall with USB, check then to avoid surprises.  Now if the error message says the UEFI is unusable, it could be full, or damaged.  How big is it and how much free space? (Type df in a terminal).  run fsck.msdos on it. (Assuming it's moutned at /boot/efi, just unmount it, and in a terminal run sudo fsck.msdos /dev/sda1 (or whatever sda partition is used).

---

### Post by Stan_Meissner on 2020-11-10
This is the error message as noted in my original post.  

```
                                                         "EFI System Partiton (ESP) not usable
Your EFI System Partition (ESP) is not mounted at /boot/efi. Please ensure that it is properly configured and try again."
```

This is what I get when I type DF

```
tmpfs                5120         4       5116   1% /run/lock
tmpfs             8219660         0    8219660   0% /sys/fs/cgroup
/dev/loop0         241664    241664          0 100% /snap/kde-frameworks-5/27
/dev/loop1         166784    166784          0 100% /snap/gnome-3-28-1804/145
/dev/loop2          56192     56192          0 100% /snap/gtk-common-themes/1502
/dev/loop3          56704     56704          0 100% /snap/core18/1885
/dev/loop6         165376    165376          0 100% /snap/gnome-3-28-1804/128
/dev/loop7          96128     96128          0 100% /snap/mpv/1
/dev/loop10         75776     75776          0 100% /snap/wine-platform-3-stable/6
/dev/loop9         100096    100096          0 100% /snap/core/10185
/dev/loop5         100096    100096          0 100% /snap/core/10126
/dev/loop13         63616     63616          0 100% /snap/gtk-common-themes/1506
/dev/loop8          56704     56704          0 100% /snap/core18/1932
/dev/loop14        185472    185472          0 100% /snap/obs-studio/1141
tmpfs             1643932        16    1643916   1% /run/user/123
tmpfs             1643932        80    1643852   1% /run/user/1000
/dev/loop15        237312    237312          0 100% /snap/wine-platform-runtime/183
/dev/loop4          62464     62464          0 100% /snap/core20/634
/dev/loop16        207616    207616          0 100% /snap/obs-studio/1157
/dev/loop12        237056    237056          0 100% /snap/wine-platform-runtime/188
stan@stan-MS-7A37:~$
``` 

The rest of what you're saying is over my head without doing some more research.  

My thought is that since I'm seeing that Unbuntu 18.04 is supported through April 2023 that there is no need for me to upgrade to 20.04 at this time.  Furthermore, I'm guessing that I would be able to do a full install from a thumb drive and that would whipe out my current setup and I'm guessing it would install without getting this error message.  If that hunch is correct, and I'm basing on having done that in the past, I would be able to simply change the bios to read the thumb drive first like I did before and do a fresh install when I switch to 20.04.  That would buy me some time and perhaps I will learn how to resolve this error in the interim.  I would assume that I should be able to do a fresh install as time permits as a way to work around this issue after having done full installs in the past on this computer.  Am I correct in that assumption?

---

### Post by westie457 on 2020-11-10
What does ```
sudo blkid
``` show us ?

---

### Post by ubfan1 on 2020-11-10
Generally, you may always do a full install, unless supported is dropped for your processor (e.g. i386) or architecture.  Take a look at your EFI to see what's wrong.  In a terminal, 
Check that the /boot/efi directory exists:  
```
ls -ld /boot/efi
sudo ls /boot/efi
```
Without a mount there, it should be just an empty directory.
Next, mount your EFI partition there (assuming your EFI is on sda1, change to what it really is if necessary):  
```
sudo mount -tvfat /dev/sda1 /boot/efi  
```
And look again:  
```
sudo tree /boot/efi
```
Please post the results here, that should tell us a lot if there's a problem.

---

### Post by Stan_Meissner on 2020-11-11
> **westie457 said:**
> What does ```
sudo blkid
``` show us ?

```
/dev/loop0: TYPE="squashfs"
/dev/loop1: TYPE="squashfs"
/dev/loop2: TYPE="squashfs"
/dev/loop3: TYPE="squashfs"
/dev/loop4: TYPE="squashfs"
/dev/loop5: TYPE="squashfs"
/dev/loop6: TYPE="squashfs"
/dev/loop7: TYPE="squashfs"
/dev/sdb1: UUID="0495-F07E" TYPE="vfat" PARTLABEL="EFI System Partition" PARTUUID="d442ae4c-fb49-45f6-89fd-de80d788f5d3"
/dev/sdb2: UUID="faec216e-f4df-4492-bf53-306c0a52dd91" TYPE="ext4" PARTUUID="ea2db255-86b5-4d73-b6ce-56f151562cb5"
/dev/sdb3: UUID="2b868647-d3c3-429d-a61f-775497f5ede1" TYPE="swap" PARTUUID="2e557086-28fd-4434-a51a-45488988ce30"
/dev/loop8: TYPE="squashfs"
/dev/loop9: TYPE="squashfs"
/dev/loop10: TYPE="squashfs"
/dev/loop12: TYPE="squashfs"
/dev/loop13: TYPE="squashfs"
/dev/loop14: TYPE="squashfs"
/dev/loop15: TYPE="squashfs"
/dev/loop16: TYPE="squashfs"
stan@stan-MS-7A37:~$
```

---

### Post by Stan_Meissner on 2020-11-11
> **ubfan1 said:**
> Generally, you may always do a full install, unless supported is dropped for your processor (e.g. i386) or architecture.  Take a look at your EFI to see what's wrong.  In a terminal, 
Check that the /boot/efi directory exists:  
ls -ld /boot/efi
sudo ls /boot/efi
Without a mount there, it should be just an empty directory.
Next, mount your EFI partition there (assuming your EFI is on sda1, change to what it really is if necessary):  
sudo mount -tvfat /dev/sda1 /boot/efi  
And look again:  
sudo tree /boot/efi
Please post the results here, that should tell us a lot if there's a problem.

I use the "DISK" utility to mount my MP3 player.  I believe that the partition hilited in orange that says FAT32 is the EFI partition so couldn't I mount it using the Disk utility?  I took a screen shot but it's asking for a URL and I don't have anywhere to host the photo that I can think of off the top of my head.  I struggle without some kind of a GUI because I rarely have any issues with Ubuntu between installs so I don't use terminal enough to become proficient at the commands.  Usually I find a discussion of whatever issue I'm having and do a search for a solution and copy and paste the suggested commands so aside from a few basic commands I only dig into it when something isn't working which fortunately is rare.

---

### Post by DuckHook on 2020-11-11
@ Stan_Meissner,

Please post your output between [noparse]```
 and 
```[/noparse] tags for clarity. Or highlight the output and use the [img]http://ubuntuforums.org/images/editor/code.gif[/img] button in the *Adv Reply* toolbar.

---

### Post by ubfan1 on 2020-11-11
The df command you posted must have been cut off, since no / was listed at all.  The blkid command did show that /dev/sdb1 is the EFI partition, sdb2 the root, and sdb3 the swap.  Did the Contents line at the bottom of the Disks page for sdb with the first partition selected (orange like you describe), say ...mounted at /boot/efi?   If so, use my sudo tree /boot/efi to examine it.  Clicking on the Disks link will probably complain that you don't have the priv to look there!  If the mount is not present, you can mount it yourself using the previous commands I gave, changing sda1 to sdb1, since apparently that is the device show by blkid,

---

### Post by Stan_Meissner on 2020-11-13
> **Stan_Meissner said:**
> I use the "DISK" utility to mount my MP3 player.  I believe that the partition hilited in orange that says FAT32 is the EFI partition so couldn't I mount it using the Disk utility?  I took a screen shot but it's asking for a URL and I don't have anywhere to host the photo that I can think of off the top of my head.  I struggle without some kind of a GUI because I rarely have any issues with Ubuntu between installs so I don't use terminal enough to become proficient at the commands.  Usually I find a discussion of whatever issue I'm having and do a search for a solution and copy and paste the suggested commands so aside from a few basic commands I only dig into it when something isn't working which fortunately is rare.

stan@stan-MS-7A37:~$ sudo mount -tvfat /dev/sda1 /boot/efi 
mount: /boot/efi: mount point does not exist.
stan@stan-MS-7A37:~$

---

### Post by ubfan1 on 2020-11-13
The blkid command established that sdb seems to have an EFI on partition 1, a root on 2 and a swap on 3.  Nothing posted indicates what your current root is -- usually it would expected to be on sda?  Guessing your are trying to set up the sdbx partitions your blkid listed.   Earlier suggestions to use sda were just a guess, so try the mount on sdb1, and if your current root does not have a /boot/efi, mount it somewhere else or make the directory.  We're just trying to look at the files, there's nothing there needed for a running a system, so it may be mounted anywhere.

---

### Post by Stan_Meissner on 2020-11-14
> **ubfan1 said:**
> The blkid command established that sdb seems to have an EFI on partition 1, a root on 2 and a swap on 3.  Nothing posted indicates what your current root is -- usually it would expected to be on sda?  Guessing your are trying to set up the sdbx partitions your blkid listed.   Earlier suggestions to use sda were just a guess, so try the mount on sdb1, and if your current root does not have a /boot/efi, mount it somewhere else or make the directory.  We're just trying to look at the files, there's nothing there needed for a running a system, so it may be mounted anywhere.

I just looked at the EFI partition in the "discs" utility GUI and it gives me the option to mount the EFI.  As I mentioned, I'm already over my head on terminal commands so I am going to try two things.  To be clear I am attempting to upgrade when prompted to click the install button when the reminder pops up.  I'm thinking that the next time I am prompted I will go into disc and mount the EFI then try the install.  If I can do it through the GUI that would be my preferred method as someone who only touches terminal when absolutely necessary.  I was like that with DOS windows back in the day as well, I could never make sense of the commands and only learned the basics. 

If that doesn't work or I was to lock up my system I would get on my wife's laptop computer and create an install thumb drive and do it that way.  I believe that would wipe out the hard drive and solve my problem.  Again, this computer is three years old max and was purpose built to run Linux by one of several companies that builds Linux computers.  In addition to that I'm seeing that 18.04 is supported for two more years so there is no urgency, who knows, my hard drive could fail before then and I'd have to install a new drive and load the OS from scratch.

I thought this would be an easy fix and my lack of comfort with terminal commands is making this more difficult for everyone to help me.  I'm confident that I can do this the way I mentioned, after all, I installed Ubuntu 18.04 from a thumb drive shortly after I purchased the computer so I have some experience doing that.  Actually I have installed Linux distros on four or five computers since I first started experimenting with it in 2006 so I'm confident that I can handle this without having to bother anyone for help by doing it my way.  It may be more time consuming and not the way that an advanced user would do things but I have installed Linux probably a half dozen times and Windows many times before that on computers that I built.  

Thanks for the suggestions but I feel like I'm making this more difficult for everyone, myself included, than it needs to be.  I will figure out a work around and get it done.

---

### Post by Stan_Meissner on 2020-11-15
I though there was a way to turn threads off or mark them as answered on here but I'm not finding that option???

---

### Post by ubfan1 on 2020-11-15
Try the "Thread Tools" drop-down menu near the top right of the thread.

---

### Post by tea for one on 2020-11-15
> **Stan_Meissner said:**
>  Actually I have installed Linux distros on four or five computers since I first started experimenting with it in 2006 so I'm confident that I can handle this without having to bother anyone for help by doing it my way.  It may be more time consuming and not the way that an advanced user would do things but I have installed Linux probably a half dozen times and Windows many times before that on computers that I built.  

Many users (advanced or simply cautious) never upgrade in situ from current installation to new release.

There are too many threads where unexpected difficulties appear.

I always back up my data and freshly install the LTS release. It takes a couple of hours to double check the installation, download my required software packages, restore my backup and re-configure my desktop. 

However, it is time well spent every two years.

---

### Post by Stan_Meissner on 2020-12-02
I agree, my lack of experience working with the terminal command would make this a big hassle for everyone who attempts to help.  I have an external USB HD enclosure that I back up my files to and have installed Linux enough times to be confident that I can successfully install the next LTS version.  This whole mess started when I got the notice for 20.04 and I attempted an upgrade.  I will use the drop down menu to close this thread and upgrade with a full reinstall on my own schedule.

---

