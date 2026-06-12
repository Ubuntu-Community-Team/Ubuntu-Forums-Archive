---
title: "Getting windows hd and Ubuntu hd to coexits"
date: 2006-11-20
forum: Installation &amp; Upgrades
---

### Post by dfro on 2006-11-20
With my computer, I started by putting Ubuntu on a hd.  Then I unplugged the hd and put Windows on a separate hd.  Both systems work by themselves, but how do I alter the grub settings to add the windows hd?  How do I figure out what label the windows hd will have (hd1,0 ??) ?

I am sorry if these are all to often asked questions.

---

### Post by taurus on 2006-11-20
It would be much better and simpler if you just connect those two harddrives at the same time when you install Ubuntu.  That way, Ubuntu will install GRUB (bootloader) on MBR to handle booting both OSes...

---

### Post by Gaweph on 2006-11-20
yes, if you install windows first, then install ubuntu, the installer (ubuntu installer) will see the windows drive, and will do everything for you.

Also, its best to do this, because windows doesnt like to be the slave, if you try and make the windows hdd the slave, then i have had problems with it not booting and such.  Its much better to make the windows hdd the master drive, and grub will just get intalled in its MDR (overrighting the windows boot manager)

---

### Post by confused57 on 2006-11-20
Just connect your Ubuntu drive as master and Windows as slave, as described here:
[http://www.ubuntuforums.org/showthread.php?t=179902](http://www.ubuntuforums.org/showthread.php?t=179902)

All you'll need to do is add the Windows boot entry to your /boot/grub/menu.lst.

---

### Post by dfro on 2006-11-20
confused57,
  Thanks for the links.  I have two SATA drives - Windows on one, Ubuntu on the other.  I did not see a thread on dual booting two SATA hd's.  Any advice on this situation?

---

### Post by dfro on 2006-11-20
I tried putting this at the end of /boot/grub/menu.lst:

title Windows XP
map (hd0,0) (hd1,0)
map (hd1,0) (hd0,0)
rootnoverify (hd1,0)
makeactive
chainloader +1

Then I plugged both SATA drives into the motherboard.  On restart, if I 'esc' into grub selection menu and choose 'Windows XP', windows starts with no problem.  But, if I choose ubuntu, the screen goes black and I get these messages:

BusyBox v1.1.3 (Debian 1:1.1.3-2ubuntu3) Built-in shell (ash)
Enter 'help' for a list of build-in commands.

/bin/sh: can't access tty; job control turned off
(initramfs) *blinking cursor here*

At this point the screen freezes and I have to reset the computer.
Does anyone have any suggestions?

---

### Post by confused57 on 2006-11-20
What you can try is to highlight the Ubuntu entry in grub, press "e" for edit...change the root to (hd0,0), then in the kernel line, if it says sdb1, change it to sda1(or vice versa)...then see if Ubuntu will boot.  These changes are temporary, so you won't hurt anything, but you'll determine if Ubuntu will boot with these parameters.  If Ubuntu boots, you can make the changes permanent in your /boot/grub/menu.lst entries for Ubuntu.

---

### Post by dfro on 2006-11-20
confused57,
  I tried this:

I rebooted and pressed 'e' at the grub screen.

I edited... > /vmlinuz-2.6.17-10-generic root=/dev/sda1 ro quiet splash to read... > /vmlinuz-2.6.17-10-generic root=/dev/sd[COLOR="Red"]b[/COLOR]1 ro quiet splash

I left 'root (hd0,5)' alone.

And grub booted into Ubuntu without the error message. Yes!  Windows XP boots when I select it, too.

I tried changing /boot/grub/menu.lst and it did not work.  Again I only changed 'sda1' to 'sdb1'.

I think I first need to understand what 'root (hd0,5)' is for in grub.
Could you explain why it got automatically set at (hd0,5)? If it is looking for partition 5, why would it be looking for the /swap partition? I will search for some grub tutorials.

Here is how I have partitioned my Linux hd:

sda1    /
sda2    free space
sda3    free space
sda4    *extended*
sda5    /swap
sda6    /boot
sda7    /home


Thanks for the help!  At least I can dual boot with a manual edit of the grub menu each time.

---

### Post by confused57 on 2006-11-20
There's some excellent guides on grub here:
[http://users.bigpond.net.au/hermanzone/](http://users.bigpond.net.au/hermanzone/)

root (hd0,5) is actually your /boot partition...your root partition is (hd0,0)...swap is (hd0,4).

(hd0,0) is the first partition on your #1 hard drive.

---

