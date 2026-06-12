---
title: "Gutsy not booting"
date: 2007-10-21
forum: Installation &amp; Upgrades
---

### Post by skm376 on 2007-10-21
I am attempting a fresh install of Gutsy.  When I boot up the liveCD I see the start screen and select start/install Ubuntu (pretty standard).  Then the fun begins.  I see the following text appear on the screen:

BusyBox v1.1.3 (Debian 1:1.1.3-5ubuntu7) Built-in shell (ash)
Enter 'help' for a list of commands.

(initramfs) [79.114623] ata1.00: failed to set xfermode (err_mask=0x40)

I can't type anything because if I type a letter, it gets repeated.  So, if I type 'h', two h's appear on the screen (hh).  If I hit delete/backspace, it removes two characters.  No idea what to do.  I am running a Dell inspiron 530.  The machine is basically brand new.  It was one of the machines Dell is selling Ubuntu on.  Ideas?

---

### Post by tajreed on 2007-10-21
Try the 2.6.22-12 kernel rather than the 2.6.22-14. Hit Esc. just as install starts to see the choices of boot kernel.

---

### Post by ntetreau on 2007-10-21
Start by doing a CD check instead of choosing Install after the Live CD boot.  If the CD is fine, then try the alternate CD instead of the Live CD.

---

### Post by trevorparsons on 2007-10-26
I had the same error with precisely the same hardware as you, skm376. Alternate install discs didn't work, not any of the huge pile of live CDs in my collection. I was stumped. Then I searched on the error message 'failed to set xfermode' and found several pages suggesting adding the boot option 'irqpoll', which does indeed solve the problem.

Do as follows: boot the Gutsy CD, press F6 for 'more options', and you'll be presented with an editable boot options string. Delete the two dashes off the end, and in their place add 'irqpoll' (without the quotes). Thus amended, Gutsy should boot up fine for you.

Once you've installed the system to disk, you'll need to add the 'irqpoll' option to the boot options in /boot/grub/menu.lst, or else you'll have the same problem on reboot.

As 'Shady explains in [this thread]("http://ubuntuforums.org/showthread.php?t=420338"), you can then make sure the 'irqpoll' option gets set every time the kernel gets updated, by adding it to the 'defoptions' section of menu.lst:

```
## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet splash
```

Add your new option to the '# defoptions=quiet splash' line and you're done.

---

