---
title: "GRUB error - arghhh"
date: 2006-09-07
forum: Installation &amp; Upgrades
---

### Post by gollyg on 2006-09-07
Hi,
I recently installed Ubuntu (after much pain :( ) and am ecstatic with it. However, in my excitement I set the system to hibernate. When I rebooted there was still an install disk in the cd. This booted, perhaps wiping the RAM data that was stored on the hd during hibernation?

Now, when I try to start the system, I get an error
"error loading stage1.5Read error"
which I have googled and tells me, well, it is a read error.

I have used the alternate cd to repair a broken system. This gets me to a screen where I can reinstall GRUB. Hooray. But I don't know where to set the primary boot disk.

I have tried /dev/hda, /dev/hda0, /dev/hda/1 all to no avail.

Ubuntu is the only os on this system (wonder: do i need grub at all?) and I used the automated install on a non-partitioned hd. This is the only hd on the system.

I have looked in fstab via a shell and there is no entry for the boot sector.

What do I need to do to boot my beautiful new os???

Much appreciate your support!

---

### Post by whizbaby on 2006-09-07
In your case the *primary boot disc* should be **hd0**, GRUB starts counting at 0.
You can use grub to boot different kernels (e.g. useful after kernel upgrade) or to boot a rescue system or to perform a memory test (and of course booting other OS)

---

### Post by gollyg on 2006-09-07
Thanks for the lightning response!

I have set GRUB to (hd0).

I am still getting the read error. Is this error indicative of an actual disk error, or is it more a sign of a configuration error?

---

### Post by whizbaby on 2006-09-07
I'm not as deep in *hibernation* to say what exactly happens, but I don't believe (and I repeat, I know nothing about it) that any configuration  should be changed...(sorry, can't really help you there). If grub was correctly reinstalled it should boot.

---

### Post by gollyg on 2006-09-07
Thanks for trying ;)

---

### Post by whizbaby on 2006-09-07
But you could check if you can access the data on the HD by booting the live-cd.

---

### Post by loney on 2006-09-07
The read error indicates that stage1 can't find stage1.5. Stage 1 is in the MBR, stage 1.5 is usually embedded in the disk directly after the MBR. Try booting from the LiveCD, open a terminal, then:

sudo mkdir /target
sudo mount /dev/hda1 /target
sudo mount --bind /dev /target/dev 
sudo mount -t proc proc /target/proc
sudo mount -t sysfs sysfs /target/sys
sudo chroot /target
grub
device (hd0) /dev/hda
root (hd0,0)
setup (hd0)
quit
update-grub
exit

The setup should print whether it found the 1.5 stage.
Then remove the CD and reboot.

---

### Post by whizbaby on 2006-09-07
> **loney said:**
> 
sudo mount -t proc proc /target/proc
sudo mount -t sysfs sysfs /target/sys

Only for personal interest:
I use to do the proc-thing like this (at work)
mount --bind /proc /target/proc
What is the difference to your's, and what is the second line for?

---

### Post by gollyg on 2006-09-07
Thanks for the detailed instructions. It all seemed to go well - when I was in Grub it found the stage 1.5, wrote the changes back to file.

However the same error occurred on reboot.

hmmm. Perhaps a complete reinstall. But that means reconfiguring everything?

BTW is it possible on a single boot install to get rid of grub alltogether? I don't need multiple boot options at this point.

---

### Post by loney on 2006-09-10
> **whizbaby said:**
> Only for personal interest:
I use to do the proc-thing like this (at work)
mount --bind /proc /target/proc
What is the difference to your's, and what is the second line for?

No difference. --bind /dev is necessary to share the /dev tree but proc is not a hard location so -t and --bind are synonymous.

sysfs exports h/w info to user space, e.g. for use by udev. I don't know if grub needs this, but it doesn't hurt. chroot is a handy way to explore a broken install and rebuild the kernel. I set up a relatively complete chroot environment just to be safe.

---

### Post by loney on 2006-09-10
> **gollyg said:**
> 
However the same error occurred on reboot.

hmmm. Perhaps a complete reinstall. But that means reconfiguring everything?

BTW is it possible on a single boot install to get rid of grub alltogether? I don't need multiple boot options at this point.

I'd say you were hosed and should reformat the device and reinstall.

You must have a boot loader, either grub or lilo. Too bad you had to delve into this; typically users can remain blissfully ignorant of grub. I can't imagine how hbernate results in such a corrupted state.

---

### Post by gollyg on 2006-09-11
I actually reformatted and reinstalled everything. Same result - GRUB read error for stage 1.5.

After pressing the start button several dozen times, convinced it was something to do with the *way* i press the switch I went back into the BIOS. Given that it was a read error I went to the ide config settings. There was a setting PCI-Master Bus that was set at enabled. I disabled it, tried again, and low and behold it started working. I dont know what this setting does, hell, in many ways I dont want to know - all that i know for sure is something happened that night, something good. And that's enough for me.

im luvin ubuntu again.

---

### Post by whizbaby on 2006-09-11
For similar issues:
What BIOS do you have (and which version)?
Where *exactly* was the option located (menu context) and what is it's name literally?

---

