---
title: "should I delete whats left of the harddrive"
date: 2010-11-14
forum: Installation &amp; Upgrades
---

### Post by Ka Fish on 2010-11-14
Something went tenably wrong during an install last night. I thought it just froze up, but when I rebooted...it takes about 5 minutes to detect drives. It won't read from my cd or thumb drives but see's them. When it finally gets past that to the log in screan, instead of showing my desktop, I get a command prompt. Is there an easy way to just erase the hard drive?

---

### Post by 73ckn797 on 2010-11-14
Boot from a LiveCD and go to System/Administration/Gparted and delete all partitions then reformat the drive.  

If you plan on installing Ubuntu I would recommend creating several partitions. One for system/program installation, designate that one as "/". You would not need more than 15GiB's. Create another large partition and designate it "/home" (size depends on how much personal data you will store there. Create a small partition for the swap. 1 to 1.5 the size of the RAM.

---

### Post by Ka Fish on 2010-11-15
I tried the disk, the light comes on & the disk will spin. It shows  "verifying dmi pool data....... boot from cd:" two minutes it boots the  hard drive. I have no idea what's going on with that. I can still see my  thumb-drive,which has a copy 10.10 on it. Is there a way to install  from there?

---

### Post by DasEi on 2010-11-15
Just go the above told way, erase hd from live cd via gparted, 
then use the cd to install fresh. Use the installer's option to check the cd, too.
You could use usb to install (saves a cd and is faster), unetbootin does it well. In your case you first would format (from live cd) let's say  1 gig for the installer-iso, then (also in live) install unetbootin, then run it on a usb stick with least 1 gb, using the iso from the hd.
Next boot pc from usb and fresh partition/install to harddrive.

---

### Post by Ka Fish on 2010-11-15
It's not giving me the option to boot from disk.

---

### Post by dino99 on 2010-11-15
you first need to set the bios to boot on the cd of course :)

---

### Post by 73ckn797 on 2010-11-15
I sounds as if you were able to get part of the way into the installation using a LiveCD?

Did you verify the iso md5sum before burning it to the disk?
Did you verify the disk integrity when initially booted on the original installation?
Did you burn the iso to disk at a slow speed?

---

### Post by Ka Fish on 2010-11-16
I'm no geek, sorry. I looked at the bios, & the cd rom is first, the burner is second, then the floppy & last is the hard drive in boot priority. I tried hooking the cd drive up without the hard-drive & got "disc error insert boot disc". I tried an older disk that I know works & changed the cd rom...still nothing. I got something saying there was some things wrong with grub & hardware drivers. I can still download threw apt-get, but I only know a few codes. Please tell me there is a way to fix this.

---

### Post by 73ckn797 on 2010-11-17
See post #7

---

### Post by TenPlus1 on 2010-11-17
Try downloading a new .iso image and burning it to CD at the slowest speed possible, this helps in making sure you have a working live cd...

Secondly, boot from the live cd and using gparted remove ALL partitions ready for install, then double click the install icon and continue...

When setting up the hard-drive partitions make sure format is always ticked...

<fingers crossed>

---

### Post by Ka Fish on 2010-12-09
I have attempted to reinstall again after replacing a faulty cpu. The loading bar at the bottom gets about half way across the screen, the screen blinks & then comes back scrambled. I tried plugging an older monitor up just to get an out of sinc message. I have an AOC flat screen model 919sw-1. Is there anything I can do to fix this?

---

