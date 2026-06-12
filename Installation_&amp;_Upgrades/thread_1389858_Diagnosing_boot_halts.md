---
title: "Diagnosing boot halts"
date: 2010-01-24
forum: Installation &amp; Upgrades
---

### Post by marty.lajeunesse on 2010-01-24
More often than not, Ubuntu boot halts at the circle logo, not responding to keyboard or mouse. This is fairly new behaviour, starting with the upgrade to 9.10. Powering down and restarting 1 or more times eventually gets to a normal startup.
How do I go about gathering diagnostics when the boot has halted?
thanks

---

### Post by Herman on 2010-01-25
One way to see what's happening *as your Ubuntu boots up* is to remove the boot options 'quiet' and 'splash' from your GRUB booting commands.
Then you'll be able to see the text scrolling up your screen and watch what's happening in real time as the kernel boots.
You might find it easiest to use the 'e' (for edit) key from your GRUB Menu to achieve that, (just delete those options and boot). The changes will be temporary so you'll need to repeat the same process each time you boot up.
You could edit your GRUB files with a text editor if you want the change to be persistent. You might edit /boot/grub/menu.lst if you have an older version of Ubuntu or edit /etc/default/grub and then run sudo grub-mkconfig -o /boot/grub/grub.cfg if you're using Karmic Koala or later.

Another way to see what happened *after your Ubuntu has booted* is to use the command [FONT=Bitstream Vera Sans Mono]dmesg, which will show you an interesting log of what happened as the kernel booted up.
[/FONT]```
dmesg
```[FONT=Bitstream Vera Sans Mono]
*If your system failed to boot *and you want to see what went wrong you might be able to use a live CD or another operating system to access the same log in the installed operating system's /var/log/dmesg.

There are some other interesting logs in /var/log/ that might also help you.
[/FONT]

---

