---
title: "GRUB Boot Loader Failed"
date: 2005-06-27
forum: Installation &amp; Upgrades
---

### Post by Hugh Jass on 2005-06-27
I experienced a fatal error during GRUB Install. I was able to install LILO, but without the boot loader it seems I cannot make a choice between OS's, the computer just boots into Windows.

I do not have any drive overlay installed. In fact, the only thing on the machine is Win XP Pro, a fresh install with updates. The PC is a VAIO PIII, and despite numerous reformats, it is still SONY branded during boot.

I have a 40 gb disk clipped at 32 gb, partitioned into a 10 gb drive and a 22 gb drive. Windows is installed on the 10gb drive. I formatted the 22gb drive into ext3 and installed Ubuntu on it. Everything went off without a hitch (congrats!) except for GRUB.

Is that enough information to get started? Thank you for your time and help.

---

### Post by dialate on 2005-06-27
You need to add two lines to your /etc/lilo.conf

```
other=/dev/hda1
label=Windows
```

where hda1 is whatever partition your Windows is on

---

### Post by dialate on 2005-06-27
I guess I misread your post...could you post the error message GRUB gave?

Which partition did you make active when you ran fdisk?

---

### Post by Hugh Jass on 2005-06-27
[QUOTE=][/QUOTE]
 I don't have the error message - it's at home and I'm at work. It read very closely to: "GRUB Installation has failed. This is a fatal error" and gave the options to Go Back or Retry. No amount of retries worked. Selecting Go Back brought me to the installation menu, and from there I went on with the LILO installation, hoping it would cover me (I am new to Linux).

I don't know which partition I made active, at least by name. I do know that it is on my master hard disk, and I can tell you that my master hard disk is setup with a 10gb partition (C:) and a 22gb partition (G:). Windows is on C:, and I installed Ubuntu on G:

D: and E: are optical, and F: is my slave hard disk.

I apologize if I am not answering questions appropriately, but I assure you, I'm trying my best. Thanks for your help and time.

---

### Post by dialate on 2005-06-27
Boot loader issues are tough to fix, cause you can't just boot into the OS to fix it :/

I think your easiest bet is to go into fdisk, set the partition you want Ubuntu on to active, try reinstalling, and go from there.

---

### Post by dirkoneill on 2005-07-01
I had the same problem last night. I did a fresh install of windows xp and durring that install i partitioned the drive into 100gigs for windows and 55 gigs for ubuntu. I first installed windows and then installed ubuntu. At the end of ubuntu the GRUB isntall failed so I also had to use lilo. I had the opposite problem where it wouldn only boot into ubuntu. There was no menu that came up on boot. It just went right into linux. When i looked at the /etc/lilo.conf file it had that windows partition listed. So i changed the default=Linux to default=Windows3. Now it just boots into windows  with no menu to boot into linux. What default setting are we missing in the lilo.conf file to have a selection menu come up?

---

### Post by dialate on 2005-07-01
Perhaps there is no timeout setting? The first four lines should look something like this

boot=/dev/hda
prompt                    # Turns on boot menu
timeout=50                # 50 = 5 seconds
default=Linux

---

### Post by mingus on 2005-07-01
[QUOTE=dirkoneill]I had the same problem last night. I did a fresh install of windows xp and durring that install i partitioned the drive into 100gigs for windows and 55 gigs for ubuntu. I first installed windows and then installed ubuntu. At the end of ubuntu the GRUB isntall failed so I also had to use lilo. I had the opposite problem where it wouldn only boot into ubuntu. There was no menu that came up on boot. It just went right into linux. When i looked at the /etc/lilo.conf file it had that windows partition listed. So i changed the default=Linux to default=Windows3. Now it just boots into windows  with no menu to boot into linux. What default setting are we missing in the lilo.conf file to have a selection menu come up?[/QUOTE]

This is a different problem than Hugh Jass has . . . it would be better to create another thread for this.

---

### Post by mingus on 2005-07-01
*The PC is a VAIO PIII, and despite numerous reformats, it is still SONY branded during boot.*

The SONY logo is being called by the BIOS bootstrap.  It is not on the disk.  Not an issue.

*I have a 40 gb disk clipped at 32 gb*

Can you clarify this . . . is there another partition that is hidden or is a recovery partition?

*I experienced a fatal error during GRUB Install. I was able to install LILO, but without the boot loader it seems I cannot make a choice between OS's, the computer just boots into Windows.*

Is your notebook equipped with a bootable floppy drive?  If so, reinstalling Ubuntu and putting grub on a floppy will be by far the best avenue to get this fixed.

Take care to not entertain a lot of guessing and "trying stuff" given that you have W$ already on the disk, which is hostile to anything else . . . there is a whole lotta confusion about boot, partitions, and grub.

---

