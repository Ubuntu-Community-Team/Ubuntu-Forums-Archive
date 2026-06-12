---
title: "installer crash while partitioning"
date: 2011-10-27
forum: Installation &amp; Upgrades
---

### Post by DC80 on 2011-10-27
Hi All,

I do not really have a problem but i think this should be reported, however, if you have a solution I would like to hear it.

The following happend as i was trying to install Kubuntu 32-bit on my portable harddrive.

Step 1: Download the live cd (doh)
Step 2: I got it installed on a 4.0Gb thumb/usb drive with pendrivelinux.
Step 3: Boot up the computer and walkthrough the wizard to install Kubuntu.

Attempt 1: The wizard closes without reason and no reports or crashes while attempting to partition my harddrive.

Attempt 2: Boot into live desktop and install it from there. The wizard closes again while attempting partitioning my harddrive.

Attempt 3: Finally, i tried it again but this time i got an error report which states:

```

Traceback (most recent call last)
File
"/usr/lib/ubiquity/frontend/kde_components/PartitionModel.py", line 99, in parent

parentItem = childItem.parent()

AttributeError: 'Element' object has no attribute 'parent'

```

After this message it hangs/froze, so i was not able to file a bugreport.

I will give some extra information to the setup and hardware i was using:

- OS: none (however, the thumbdrive was installed on Windows Server 2008 R2 this morning)
- Hardware: WD passport 750 Gb, Sandisk Cruzer 4 Gb. (I did check them for errors)
- Download: [http://www.kubuntu.org](http://www.kubuntu.org)
- Partition config: "/" 100 Gb, swap 4 Gb and the remaining space on "/home". 

I do have a question about this. Maybe, for myself at least, can i install ubuntu with the partitioning above and then reinstall Kubuntu on it?

Let's say:
- "/" for the system <-- replace ubuntu for Kubuntu
- "swap"
- "/home" for backup or in case of a crash/upgrade/reinstall. <-- will kubuntu recognize this partition (probably will) and use it for this purpose?

In any case, thanks in advance

DC80

---

### Post by Quackers on 2011-10-27
Have you checked the md5sum of the downloaded iso file?

[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

You should also check the cd/usb for errors.

---

### Post by DC80 on 2011-10-27
Hi Quackers,

I did check the thumbdrive already. However i did not check the MD5sum. 

For now, i'm gonna try the 64-bit version on my desktop. 

Thanks for the input.

DC80

---

### Post by scientastic on 2011-10-27
> **DC80 said:**
> ...
Step 1: Download the live cd (doh)
Step 2: I got it installed on a 4.0Gb thumb/usb drive with pendrivelinux.
Step 3: Boot up the computer and walkthrough the wizard to install Kubuntu.

Attempt 1: The wizard closes without reason and no reports or crashes while attempting to partition my harddrive.

Attempt 2: Boot into live desktop and install it from there. The wizard closes again while attempting partitioning my harddrive.

Attempt 3: Finally, i tried it again but this time i got an error report which states:
...
- Partition config: "/" 100 Gb, swap 4 Gb and the remaining space on "/home". 
...


I also have almost the same problem.  In this case, I'm installing on a Toshiba laptop from CD.  Here's my story:

Step 1. Download the 64-bit Kubuntu 11.10 ISO.  Burn to CD.  Verified correct by K3B and also by the live CD's own "Check disc for defects" program.
Step 2. Boot into live desktop and install from there.  On the partitioning step, I choose "manual," because I have a /home directory and a number of other partitions already set up.
Step 3. Well, I never got this far most of the time.

Attempt 1: the install wizard crashed (closed with no warning or error or explanation) *while* I was trying to specify the partitions.

Attempt 2: it crashed immediately after I specified the partitions and clicked the "Install Now" button.

Attempt 3: it got about 30 seconds into the install (about long enough for me to specify my time zone and keyboard layout), then crashed again.

Attempt 4: I'm trying it now-- rebooted and am trying with several options from the F6 menu turned off.  I hope that helps but not sure yet.

My configuration: I have a Toshiba Satellite P205-S6297, with 4GiB of memory, and a hard drive partitioned into several partitions.  I have three OS partitions-- so I can install a new Kubuntu while keeping an old one around in case my new install fails-- and a boot partition, and a /home partition, and a couple others.

The common denominator seems to be the /home partition.  I also recall having a similar problem installing Kubuntu 10.10 on this laptop-- I don't recall how I resolved it; maybe by just trying again and again until it randomly worked.  But this is definitely a recurring issue, not just a one-off or random problem.

---

### Post by scientastic on 2011-10-27
> **scientastic said:**
> 
Attempt 4: I'm trying it now-- rebooted and am trying with several options from the F6 menu turned off.  I hope that helps but not sure yet.


Sure enough, that seemed to do it.  I turned acpi off, and a few other options that I don't remember (not having the menu in front of me now).  It's now done copying files and is now downloading things from the network to install.

DC80: try this-- does it work for you?

UPDATE: Spoke too soon.  Installer crashed while "Installing system 64%"... this time, though, a semi-helpful dialog came up saying that the installer had crashed and asking me to report it.  I'm pretty sure it's an unrelated issue, though...

UPDATE 2 (Attempt 5): This time I de-selected the option to update packages from the Internet.  It still started to download stuff from the Internet and again crashed at "Installing system 64%".  Will try again, this time with Internet disconnected...

UPDATE 3 (Attempt 6): Turned off my wireless connection altogether.  No good.  Still crashes at "Installing system 64%."  Giving up, after using the 'ubuntu-bug ubiquity' tool as suggested by the dialog.

UPDATE 4 (Attempt 7).  Sorry, this is unrelated to the original post.  But just in case, yes, I solved it-- I was trying to use 'btrfs' as the root filesystem, and a comment on [https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/220961](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/220961) led me to try again with ext4, which works.  So I am good to go now.

---

### Post by DC80 on 2011-10-28
Uhm, no i didn't try that, thanks for the information. I have found a workaround in the ubuntu wiki. 

The strange thing is that a clean install on two partitions (the "/" (ext4) and the "swap") works fine.

The workaround in short:

Step 1: Prepare a partition for the "/home" folder. (doing so with a ubuntu live cd, at least i did)

Step 2: Follow the instructions on the ubuntu wiki about moving your "/home" folder into the newly created partition.

This workaround did it for me.

Kind regards,

DC80

---

### Post by scientastic on 2011-10-28
So the common denominator, again, seems to be the desire to use a separate /home partition, combined with (apparently on some machines) some of the default boot options.

Workaround 1: don't use a /home partition at install time, but set it up afterwards.
Workaround 2: boot the livecd with some options turned off from the F6 menu (e.g. turn off acpi, etc.)

And a separate problem-- if your installer crashes partway through, and you are using btrfs on the root partition, try ext4 instead next time.

---

### Post by DC80 on 2011-10-29
> **scientastic said:**
> 
UPDATE 2 (Attempt 5): This time I de-selected the option to update packages from the Internet.  It still started to download stuff from the Internet and again crashed at "Installing system 64%".  Will try again, this time with Internet disconnected...


Allthough the crash is not normal, Kubuntu is doing an attempt to download extra files and language packages. This is since i can remember. It looks like a normal procedure to me. 

However, why the crash happens, that i do not know.

DC80

---

