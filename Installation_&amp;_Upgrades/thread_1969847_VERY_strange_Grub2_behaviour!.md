---
title: "VERY strange Grub2 behaviour!"
date: 2012-04-30
forum: Installation &amp; Upgrades
---

### Post by tigang on 2012-04-30
Well, after solving pretty much every issue I have ever come across with Ubuntu in the last 6 years, either myself or through reading threads on this forum, I have really come unstuck!

I have a Dell OptiPlex GX240 with a fairly new PATA 320GB HDD. Installed 12.04 32-bit, no problems, but get 'file not found' and Grub2 Rescue prompt.

The reason I get this error is because if I use 'ls /boot' from the rescue prompt, the directory is empty. If I boot the live cd, mount the HDD and look, /boot has the necessary files including the 'grub' directory with its files. Having performed all sorts of tests on the HDD and re-installed, trying a brand new HDD as well, I get the same result.

VERY strange that a live CD can see and read the /boot/grub files fine, but Grub2 cannot see them. It can see all the /etc files for example, but it appears that /boot is empty when Grub2 looks. I guess it could be some weird BIOS limitation that messes with large drives, but the BIOS (A05 latest) does correctly report a 320GB drive.

Have tried boot-repair et al - no joy, same result. Any ideas folks?

Many thanks.

---

### Post by darkod on 2012-04-30
You have only one hdd right?

You can try running the boot info script. You can do it with boot-repair and post the link it gives you.

---

### Post by tigang on 2012-04-30
Hi darkod

Many thanks for your reply. Yes, I only have one hdd. Happy to post the boot info script, but everything appears ok when examining the file system, including the necessary grub files in /boot/grub, from a live cd.

When I got the Grub Rescue prompt, I was hoping to manually load the linux module and take it from there, but as it cannot see anything in the /boot directory (appears blank) that is not possible.

I will go and run the boot info script now and post anyway... back in a tick

---

### Post by tigang on 2012-04-30
Dear darkod

As per your suggestion, the boot info script is:

[http://paste.ubuntu.com/958427/](http://paste.ubuntu.com/958427/)

Best regards
tigang

---

### Post by darkod on 2012-04-30
You are right. It all looks good.

You could try and reinstall grub2 to the MBR just in case. From live mode in terminal:
sudo mount /dev/sda1 /mnt
sudo grub-install --root-directory=/mnt /dev/sda

If that fails, you could try installing once more but this time use the manual partitioning and create a 300MB /boot partition at the start of the disk. Sometimes it can't reach grub files that are towards the end of the disk.

Other than that, I have no more ideas.

---

### Post by tigang on 2012-04-30
Just tried the reinstall - same result unfortunately.

Interesting point about creating the large /boot partition at the start of the disk... I will try that next!

One again, many thanks for your suggestions, much appreciated.

---

### Post by grahammechanical on 2012-04-30
Are you sure that this machine is using BIOS to boot and not UEFI?

[http://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface]("http://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface")

Just a wild guess. Most probably wrong.

Regards.

---

### Post by oldfred on 2012-04-30
Boot script is not showing a efi partition, which should be first.

Is this an older computer?

Then the separate /boot may work or you could just shrink / (root) to less than the 137GB BIOS limit and make the rest of the drive /home or data. I find with separate data my /home only needs to be 25GB with only 7GB used.

---

### Post by tigang on 2012-05-02
Hi grahammechanical and old fred

Apologies for the delay in responding; I have been away on business.

A really interesting link on UEFI - I am embarrassed to say that I had never heard of it :oops:. Really interesting and I intend to find out whether it can be implemented on my system, which is 2002 vintage.

I think the idea of shrinking the boot partition would work, but I was intrigued by the fact that Grub could see some (not all) files rather than a straight forward 'all or nothing'.  I played with the very limited BIOS settings and found that everything worked when I turned off UDMA support, which seems even more mysterious!

The controller is an ATA100 and the PATA HDD is ATA133. On paper that should not make a difference, but I used the HDD manufacturers firmware tweak tool to force the drive to ATA100 mode and still got the same problem.

The fact that the system boots fine with UDMA switched off on the BIOS is great, but I was worried about performance. However, it appears that the drive is operating at ATA100 speeds, so I assume linux has overridden the BIOS parameters. In fact, if I add an extra HDD to the system and tell the BIOS to ignore it, linux can still see it fine, so I guess once the BIOS has done its job and got the OS loaded, linux can override pretty much anything.

Anyway, many thanks folks, any other thoughts would be welcome to help me better understand the situation. I am off now to read up on UEFI.

Best regards
tigang

---

### Post by mips on 2012-05-02
Try this, fire up gparted and resize the /boot partition so it's leaves a 2MB gap/free space at the beginning of the drive. Then reinstall grub.

---

### Post by tigang on 2012-05-02
Hi mips

Many thanks for your suggestion, but with turning off UDMA in the BIOS my problem has gone away. My understanding is that the worst turning off UDMA in the BIOS will do is slow down booting, because Ubuntu will enable it by default when it comes up.

Best regards
tigang

---

