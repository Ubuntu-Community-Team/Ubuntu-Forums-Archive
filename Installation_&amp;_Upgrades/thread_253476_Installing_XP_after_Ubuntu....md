---
title: "Installing XP after Ubuntu..."
date: 2006-09-08
forum: Installation &amp; Upgrades
---

### Post by Xiol on 2006-09-08
Hey all.

I installed Ubuntu on my laptop a while ago and left a 15GB partition for XP to go on later. I know XP should've gone on first as it's going to molest my MBR during installation, but due to factors at the time I was not able to install XP first (factors being sheer laziness and not necessarily requiring XP at the time).

What do I have to do once I've installed Windows to restore grub back to my MBR and successfully boot to either Ubuntu or Windows?

I'm not a Linux newbie (5 years exp with other distros) and I work as a sysadmin, so don't worry about being technicial! I've just not had to install XP after Linux so I'm a bit concerned. I've got access to Knoppix LiveCDs if that will make things easier.

Presumably I'll just need to boot up a LiveCD, chroot into my Ubuntu install and run a command to reinstall Grub... At least, that's how I'd do it, but is there an easier way, and what is the command that Ubuntu uses to auto generate the menu.lst file, etc?

Cheers.

---

### Post by zxee on 2006-09-08
If you chroot into your ubuntu install > grub-install should should do it.
You could also type grub (in the chroot) at the grub prompt type find /boot/grub/stage1
grub should respond with the root partition and then you type
setup hdX with the X being the actual drive letter that your mbr is on.
One of those methods should work-good luck.

---

