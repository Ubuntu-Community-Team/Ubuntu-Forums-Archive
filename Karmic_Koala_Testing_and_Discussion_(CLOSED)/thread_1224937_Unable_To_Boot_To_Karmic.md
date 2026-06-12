---
title: "Unable To Boot To Karmic"
date: 2009-07-28
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by jlacroix on 2009-07-28
I decided to install Karmic on my test box today, one that shares a home with Windows XP. (Don't worry, I imaged my Windows XP partition so I don't care what happens to it). I installed Karmic and told it to take over the second drive. (The first is a 40GB PATA and the second is a 160GB SATA). Installation finished but when I reboot, it boots directly into Windows XP. I don't see any options to boot to Karmic. (Which should be the default). Is this a bug, and if so is there a work around? Thanks!

---

### Post by psyke83 on 2009-07-28
> **jlacroix said:**
> I decided to install Karmic on my test box today, one that shares a home with Windows XP. (Don't worry, I imaged my Windows XP partition so I don't care what happens to it). I installed Karmic and told it to take over the second drive. (The first is a 40GB PATA and the second is a 160GB SATA). Installation finished but when I reboot, it boots directly into Windows XP. I don't see any options to boot to Karmic. (Which should be the default). Is this a bug, and if so is there a work around? Thanks!

I doubt it's a bug - it seems you misunderstand how the bootloader works. On one of the last pages of Ubiquity it asks where you wish to install the bootloader - did you see that?

Nevertheless, since GRUB was installed to the second drive, then I suspect that your BIOS is still trying to boot from your first drive, which completely bypasses GRUB. You need to change your BIOS configuration or use your system's boot keystroke to select the second drive as the boot device.

---

### Post by ranch hand on 2009-07-28
Try this;

[https://wiki.ubuntu.com/Grub2#Recover%20Grub%202%20via%20LiveCD](https://wiki.ubuntu.com/Grub2#Recover%20Grub%202%20via%20LiveCD)

My /etc/default/grub file looks like this;
```

# This file is sourced by update-grub, and its variables are propagated
# to its children in /etc/grub.d/
GRUB_DEFAULT=0
GRUB_TIMEOUT=100
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"

# Uncomment to disable graphical terminal (grub-pc only)
#GRUB_TERMINAL=console

# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
#GRUB_GFXMODE=640x480

# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID=true

```
The timeout in yours should read 5.  Mine is on a drive with 7 other OS' and I want time to look at it.

I recommend reading the whole page in the wiki.  It may help you understand grub2 better.

When you can boot to 9.10 run "sudo update-grub" and it should pick up your XP and put it in the correct possition in your boot sequence if it is not when you get to booting anyway.

---

### Post by psyke83 on 2009-07-28
> **ranch hand said:**
> Try this;

[https://wiki.ubuntu.com/Grub2#Recover%20Grub%202%20via%20LiveCD](https://wiki.ubuntu.com/Grub2#Recover%20Grub%202%20via%20LiveCD)


I don't think that's necessary, mr hand ;). At least not yet.

The OP's configuration is as follow:

Disk 1 - Windows XP with standard Windows MBR
Disk 2 - Ubuntu with GRUB MBR.

BIOS Configuration: Boot from Disk 1

With this configuration, the PC will boot directly into Windows XP. Only when you boot from Disk 2 will you get the GRUB menu (and confusingly, the option to boot from XP will also be present as an item there).

---

### Post by budluva04 on 2009-07-28
psyke83's is right, sounds like he needs to set bios to boot from disk2

---

### Post by jlacroix on 2009-07-28
I never got anything that asked me where to install the boot loader.

In Jaunty, this configuration worked fine. Install Windows XP on the first drive, install Ubuntu on the second drive, and then Grub is automatically installed on the first disk.

---

### Post by ranch hand on 2009-07-28
You should be able to, from the live CD set up grub2 so that it is booting from disk 1 when you use the command
```

sudo grub-install /dev/sda (or hda - hatever you have)

```
You have set your default to whichever you want to in /etc/default/grub and this command has you booting from sda from 9.10 as boot/root on sdb.

---

### Post by psyke83 on 2009-07-28
> **ranch hand said:**
> You should be able to, from the live CD set up grub2 so that it is booting from disk 1 when you use the command
```

sudo grub-install /dev/sda (or hda - hatever you have)

```
You have set your default to whichever you want to in /etc/default/grub and this command has you booting from sda from 9.10 as boot/root on sdb.

That's not going to work. It's necessary to mount, bind devices and chroot into the installation. You're better off directing people to the "If you messed up" instructions on the [Grub2Testing]("https://wiki.ubuntu.com/KernelTeam/Grub2Testing") wiki.

---

### Post by psyke83 on 2009-07-28
> **jlacroix said:**
> I never got anything that asked me where to install the boot loader.

In Jaunty, this configuration worked fine. Install Windows XP on the first drive, install Ubuntu on the second drive, and then Grub is automatically installed on the first disk.

Keep in mind that Karmic has only recently switched to GRUB2, so the supporting infrastructure may not have caught up yet.

If you installed onto the second drive, GRUB's bootloader should have been installed to the MBR of that drive as well - which is what occurred in your case.

---

### Post by ranch hand on 2009-07-28
> **psyke83 said:**
> That's not going to work. It's necessary to mount, bind devices and chroot into the installation. You're better off directing people to the "If you messed up" instructions on the [Grub2Testing]("https://wiki.ubuntu.com/KernelTeam/Grub2Testing") wiki.
You know, I really hate to say this but, I stand corrected.  Thanks.

Like all of us I am trying to get "up to speed" on a new system that is not completely up to speed itself.  It is a lot of fun but there is a lot to learn.

Geeze I hate it when someone else is right.  It is a good thing that some folks are watching.

---

### Post by psyke83 on 2009-07-28
> **ranch hand said:**
> You know, I really hate to say this but, I stand corrected.  Thanks.

Like all of us I am trying to get "up to speed" on a new system that is not completely up to speed itself.  It is a lot of fun but there is a lot to learn.

Geeze I hate it when someone else is right.  It is a good thing that some folks are watching.

;)

I was getting quite irritated when trying to re-install GRUB2 and none of the instructions worked (even from the release notes, IIRC). 

Only the steps on the Grub2Testing page (which is the same as the link you originally provided) worked.

---

### Post by jlacroix on 2009-07-28
I figured out the problem. Karmic is seeing my 40GB drive as the secondary, which is not the case according to the bios. This must be a bug because Ubuntu shouldn't be reordering the drives like that. (This worked fine in Jaunty).

With that said, even though I know the problem, I have not yet found the solution. The instructions you guys have provided did not do the trick so far. /dev/sdb1 is where the root of the Linux install is, and Grub won't even consider touching it with any of the commands. :(

---

