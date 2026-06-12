---
title: "Gutsy live CD won't load properly - PC reboots."
date: 2007-10-28
forum: Installation &amp; Upgrades
---

### Post by Prestwick on 2007-10-28
Hi there, trying to install 7.10 on a system with:

[LIST]
[*]An AMD X2 4200+ processor
[*]An ECS nforce 4 based motherboard
[*]An ATI x850 gfx card
[*]A Creative Sound Blaster x-fi card
[*]A Samsung 250gb Hard Drive
[/LIST]

Essentially the CD boots to the initial ubuntu menu. When you choose to load Ubuntu it goes through the initial stage, only for the screen to go blank and the system to reboot.

Can anyone tell me whats going wrong here and what I need to go to get myself going?

---

### Post by skompier on 2007-10-28
1) Did you [md5sum]("https://help.ubuntu.com/community/HowToMD5SUM") the download?

2) Did you burn the cd at 4x or less? (Faster can corrupt the burn.)

3) Did you check if the disk is good?

---

### Post by Prestwick on 2007-10-28
I did all that and the ISO downloaded is fine and it burnt onto the CD correctly. 

In the end I did manage to get the live CD to work but I had to subtly change the boot command (removed quiet and splash) when at the Ubuntu menu before it would boot properly.

Now its installed, it repeats the same problem (rebooting) but now after grub! The menu loads fine and grub boots the recovery mode option fine, it just seems to be something to do with the boot command with the generic option. I try to remove "quiet" from the generic boot command but it just seems to boot using the original command anyway.

Any ideas?

---

### Post by Prestwick on 2007-11-13
***bump***

Aw c'mon guys, this is ruining my usually scerene Ubuntu experience. There is nothing wrong with the CD as I successfully concluded an install after twiddling with the boot options without any actual read or write errors.

Basically you see the grub boot screen, you wait for it to time out and then the screen goes blank and it reboots without showing an error or a kernel panic. Booting to recovery mode however works perfectly.

Any ideas at all?

---

### Post by zetaghost on 2007-11-13
Here is an Idea, Dont know if this will help but I had the same problem with my laptop. It had 3 gig ram in it I took out 1 leaving 2 gig in and it works fine now.

---

### Post by torgrot on 2007-11-13
Try putting  pci=biosirq acpi=off on the kernel line in menu.lst or just add it to the kernel line before grub starts linux.  I have the exact same problem with a Dell and those two options are the only way I can boot.

torgrot

---

### Post by Prestwick on 2007-11-14
I tried it first with both of those options but that didn't work but then I had the brainwave of removing any mention of quiet and splash and then adding just acpi=off and lo! It worked!

Huzzah! Mission accomplished!

---

