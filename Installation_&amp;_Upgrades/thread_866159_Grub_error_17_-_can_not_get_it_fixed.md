---
title: "Grub error 17 - can not get it fixed"
date: 2008-07-21
forum: Installation &amp; Upgrades
---

### Post by Acid Cool on 2008-07-21
Hi!

I recently bought an extrenal casing for my SATA drive. I took the drive out of my computer, installed it into the casing and connected it via USB 2.0. This drive had Ubuntu 6.06.1 installed. I have another IDE drive still in my computer on which I installed Windows XP Pro. This config work peachy until I move the SATA drive.

So first time I've tried booting up the computer after I moved the SATA drive, GRUB threw at me an error 17. I googled a lot on this and found that i might be caused becaus the computer has the order of the drives messed up. So I played with menu.lst and device.map, but nothing worked. I got tired of doing this so I went and boot for the Win XP CD and did the fixmbr from the Recovery Console. At least i got my win xp back for now.
I've been trying ever since to get the Ubuntu up again, but nothing works. I've tried almost everything I found (mind you I'm a preatty noobish linux user) - from Alternate Ubutnu Install CD, grub-install and may variations of this. The alternate CD throws an "exit code 20" when trying to install GRUB to just the SATA drive.

My device.map looks like this:
(hd0) /dev/hda
(hd1) /dev/sda
- i don't think there can be any mix-ups about the device orders here. I also checked the menu.lst and Windows links to (hd0) and all the linux stuff links to (hd1) as it's suposse to. My ubuntu install is on (hd1,2) partition.

So I'm stuck right now and I don't have the slightes idea what to do. The thing I do know is that I cannot install GRUB on my internal IDE drive, cause if I want to be able to boot to windows even if I don't have the extrenal drive connected of truned on. Also I can set the USB extrenal drive as my boot drive in bios so i guess that my computer has the boot-from-USB abilitty. Can anyone please explain to me what to do?

Thanks,
Acid Cool

---

### Post by wolfen69 on 2008-07-21
unplug your xp drive temporarily, and restore grub doing [this]("http://ubuntuforums.org/showthread.php?t=224351") 

then you can plug xp back in and boot to your xp cd. choose recovery console and type fixmbr. then you can choose which drive to boot to at start up via bios or quick boot option.

---

### Post by Acid Cool on 2008-07-24
i did this but, i still won't boot up...it's still throwing error 17 at me :S

---

### Post by dstew on 2008-07-24
So, you want the external hard drive to be able to boot when it is plugged in, but not put grub onto the internal hard drive, so XP boots directly when the external drive is not plugged in. Is that correct? Are you sure your BIOS can boot the USB external hard drive?

If you are confident that your BIOS can boot the external drive, you need to install grub directly to the MBR of the external drive. I guess that you get the error 17 when you try to boot the external drive, and there is no message attached. Am I right? That is, it says "Error 17", but it does not say "Cannot mount selected partition". If this is true, you are getting a grub stage 1 or 1.5 error, and you will need to re-install the grub boot loader. No amount of editing the menu.lst or changing device.map can fix this type of error.

Installing grub on an external USB drive can be a bit tricky, because when the USB drive is present it might be listed by the BIOS as drive #1 instead of drive #0. Assuming the drive is counted as #1, you would re-install grub this way.

With the external hard drive plugged in, boot an Ubuntu live CD. Open a terminal window and enter```
sudo grub
```That should get you the gurb shell, with the **grub>** prompt. At the grub prompt, enter```
find /boot/grub/stage2
```It should give you something like (hd1,0). Whatever it gives you, use as the argument for a grub root statement:```
root (hd1,0)
```Then, setup the grub boot loader in the MBR of the external drive (assuming it is counted as #1 by the BIOS):```
setup (hd1)
quit
```Then, quit the live CD session, and change your BIOS to boot the external USB drive. See if you get the grub menu when you boot. If so, that is good. We might have to edit the menu to get it completely fixed, but that is the next step.

---

