---
title: "Ubuntu installer fails to create swap partition ?"
date: 2016-02-21
forum: Installation &amp; Upgrades
---

### Post by oisin_nz on 2016-02-21
Hi, 

I have installed 14.04 on my laptop following C.S.Cameron's instructions in [http://ubuntuforums.org/showthread.php?t=2060493](http://ubuntuforums.org/showthread.php?t=2060493). Specifically it includes instructions for creating 'swap space' 

(Optional swap space, allows hybernation)
Click "free space" and then "Add".
Select "Primary", "New partition size ..." = remaining space, (1000 to  2000 megabytes, or same size as RAM), Beginning and "Use as" = "swap  area" then OK.

The problem is that when the install is complete Ubuntu doesn't seem to recognize this swap space. The system monitor (ksysguard) lists swap as 0.0 GiB. I can see from Gparted that there is clearly some sort of partition (/dev/sda6) where I intended the swap space to be (see attached pic) but I don't understand why the system isn't recognizing it as swap space ? Does anyone understand why this is happening and is there any way I can use this 3.72GB partition as swap space now that the install is complete ?

[ATTACH=CONFIG]267419[/ATTACH]

Thanks, 

Usjes

---

### Post by Bucky Ball on 2016-02-21
Something's gone wrong there, not sure what. 

Right click sda6 and delete it. Right click the free space and recreate 'swapspace'. Make sure sda6 is now seen as /swap and close Gparted.

Open a terminal and:

> sudo blkid

Make sure /dev/sda6 is showing as /swap. Next to that you should see 'UUID=<a_long_number>'. Should look something like this:

> /dev/sda6: UUID="f4180623-88c3-4d50-bce5-ab0867735daa" TYPE="swap"

Make a note of that long number and post it here. We can add the /swap to your fstab file so it boots with the computer.

Just a note: You are intending to use hibernate? If so, the /swap should be the same size or larger than your physically installed RAM. If no hibernation (don't confuse this with suspend), then 2Gb /swap is all that is required. Some people don't bother with /swap at all if they have plenty of RAM, but I have heard of this causing the odd issue so best to leave a small /swap.

---

### Post by oldfred on 2016-02-21
Did you install with encrypted /home?
Then gparted will not be able to see swap as it also is encrypted.

Post this:
cat /etc/fstab

---

### Post by Bucky Ball on 2016-02-21
Well picked by oldfred. Yes, this could be the issue. Best post what oldfred has requested prior to going ahead with my advice. :|

---

### Post by oisin_nz on 2016-02-21
> **oldfred said:**
> Did you install with encrypted /home?
Then gparted will not be able to see swap as it also is encrypted.

Post this:
cat /etc/fstab

Yes, I did indeed opt for an encrypted /home, does this mean that I wont be able to use swap space ?

Latitude-E6410:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sda3 during installation
UUID=a9031d77-ff86-47a3-a2f1-6b03ba5470d3 /               ext4    errors=remount-ro 0       1
# /home was on /dev/sda5 during installation
UUID=2f7a5af5-3b0c-4b3e-b29b-90c055b0462c /home           ext2    defaults        0       2
# swap was on /dev/sda6 during installation
#UUID=c0a95783-058e-4505-a7fb-f9097bfe8e8e none            swap    sw              0       0
/dev/mapper/cryptswap1 none swap sw 0 0

---

### Post by oldfred on 2016-02-21
I am asssuming swap is working. 
It just is that since encrypted, other tools cannot see it.

What does this show? Once you have unencrypted system, it is essentially seen as a standard install.
free

If you have encryption, back up which always is recommended becomes vital. All the requests we get for repairs will not typically work on encrypted partitions. Or recovery from backup is about the only way to restore data.

---

### Post by oisin_nz on 2016-02-21
Okay, so if I understand you are saying that I do actually have a functioning swap partition its just that it doesn't show up in applications like ksysguard. What about hibernation ? When I try to hibernate my machine the screen briefly turns blank before returning to my desktop. Is this due to the encryption or should it be possible to hibernate even though I have chosen to encrypt the home drive ?

---

### Post by oldfred on 2016-02-21
Generally best not to use hibernation. 
Linux boots much faster than Windows normally.

And some systems have issues with hibernation. Is swap as large as RAM in GiB, not GB? Or about 10% larger than in GB?

Best to post a new thread with that in title, if you want hibernation and have issues.

---

