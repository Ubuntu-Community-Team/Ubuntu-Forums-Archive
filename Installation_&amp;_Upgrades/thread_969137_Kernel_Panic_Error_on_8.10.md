---
title: "Kernel Panic Error on 8.10"
date: 2008-11-03
forum: Installation &amp; Upgrades
---

### Post by dethredic on 2008-11-03
So, I upgraded to 8.10, and now I get the boo up error:

kernel panic : not syncing; VFS; Unable to mount root fs on unknown-block

---

### Post by dethredic on 2008-11-04
anyone?

---

### Post by dethredic on 2008-11-06
?

---

### Post by ramaswamyps on 2008-11-06
boot with cd and post the /var/log/dmesg from partition so we can find what is wrong.

you can try to boot with old kernel also

check if the disk vol id is correct in the kernel line.

from boot cd you can check fsck of the partition.

---

### Post by tihut100 on 2008-11-06
hi 
i am having a big problem and i have no idea what is going on cause i am not the best with computers. but when i insert the cd in and press on "instal ubuntu" during the reboting procces i get an error that says something like kernel error need x86-94 cpu and have i684. 
i have no idea what this means and i am really interested in using this operating system, if anyone has the answer please let me know.

---

### Post by Jedi1usa on 2008-11-06
> **ramaswamyps said:**
> boot with cd and post the /var/log/dmesg from partition so we can find what is wrong.

you can try to boot with old kernel also

check if the disk vol id is correct in the kernel line.

from boot cd you can check fsck of the partition.

I am having the same kernel panic issue when I try to boot from CD. I don't see how I can get to the "/var/log/dmesg" because it instantly panics after selecting the boot option. In fact I don't see how it could possibly have a log because the kernel panic occurs because it is unable to mount the FS. 

Any other suggestions?

---

### Post by halfmanhalfbug on 2008-11-07
Hi Jedi1usa
I think this thread [http://ubuntuforums.org/showthread.php?t=966939]("http://ubuntuforums.org/showthread.php?t=966939") may describe your problem. Apparently some upgrades do not add the 
"initrd		/boot/initrd.img-2.6.27-7-generic"
line to the listing for the new 2.6.27-7 kernel in /boot/grub/menu.lst. If you can boot an old kernel (should be possible if this is actually the problem) then check your /boot/grub/menu.lst using a text editor. Is there a line for the initrd for the new kernel?
Good luck,
hmhb

---

### Post by halfmanhalfbug on 2008-11-07
And tihut100, it looks like you downloaded the 64-bit version (for x86_64 cpu) of Ubuntu when you actually need the 32-bit version (for i686 cpu). Simply go to the downloads page and be sure the radio button for "32bit version" is checked, then download that version.

---

### Post by Jedi1usa on 2008-11-07
> **halfmanhalfbug said:**
> Hi Jedi1usa
I think this thread [http://ubuntuforums.org/showthread.php?t=966939]("http://ubuntuforums.org/showthread.php?t=966939") may describe your problem. Apparently some upgrades do not add the 
"initrd		/boot/initrd.img-2.6.27-7-generic"
line to the listing for the new 2.6.27-7 kernel in /boot/grub/menu.lst. If you can boot an old kernel (should be possible if this is actually the problem) then check your /boot/grub/menu.lst using a text editor. Is there a line for the initrd for the new kernel?
Good luck,
hmhb


OK. I was not really doing an upgrade or install, just trying to run off the CD. I'll check to see if I have the correct (32bit) version as mentioned in another post.

---

### Post by halfmanhalfbug on 2008-11-07
Oops, sorry. I should have directed my comment about the initrd more to dethredic, who is having the upgrade problem.

---

### Post by ramaswamyps on 2008-11-07
> **Jedi1usa said:**
> I am having the same kernel panic issue when I try to boot from CD. I don't see how I can get to the "/var/log/dmesg" because it instantly panics after selecting the boot option. In fact I don't see how it could possibly have a log because the kernel panic occurs because it is unable to mount the FS. 

Any other suggestions?

you probably have to check md5 of the iso file downloaded.
if checks ok make another cd at the slowest possible speed in nero in windows.or any other recorder.

---

### Post by dethredic on 2008-11-21
> **halfmanhalfbug said:**
> Hi Jedi1usa
I think this thread [http://ubuntuforums.org/showthread.php?t=966939]("http://ubuntuforums.org/showthread.php?t=966939") may describe your problem. Apparently some upgrades do not add the 
"initrd		/boot/initrd.img-2.6.27-7-generic"
line to the listing for the new 2.6.27-7 kernel in /boot/grub/menu.lst. If you can boot an old kernel (should be possible if this is actually the problem) then check your /boot/grub/menu.lst using a text editor. Is there a line for the initrd for the new kernel?
Good luck,
hmhb

Sorry for the delayed response.

That line was not there.
I went into command line and added the line:
initrd /boot/initrd.img-2.6.27-7-generic

I booted again, and I got some error 15 file not found or something like that.

---

### Post by cigtoxdoc on 2008-11-27
I had same thing happen while doing an on-line upgrade from 8.04 to 8.10.  I stopped PC when it looked like it was upgrading files (314 total) to 8.04 when 8.10 had already downloaded and installed.  I know get Kernel panic - not syncing: Attempted to kill the idle task!  I am down loading ISO image for 8.10 as there is apparently no way to recover.

JHL

---

