---
title: "Ultimate edition"
date: 2011-03-16
forum: Installation &amp; Upgrades
---

### Post by gdonwallace on 2011-03-16
I decided to download and burn the live DVD for Ultimate Edition 2.9.  Wanted to see if it would work on my laptop and just check it out.

Everything went fine, messed around with it for a couple hours, then rebooted so that I could get back to Ubuntu.  That's where the problem is. The boot process gets as far as "Checking battery state" and hangs.  I let it sit thinking that there was something Ubuntu was doing in the background, not the case.  

Any thoughts or ideas?

---

### Post by gdonwallace on 2011-03-16
Have some additional information.

I see the following on the screen as the laptop is booting up:

fsck from util=linix-ng 2.17.2
/dev/sda6 clean
  Stopping Gnome Display Manager
  Starting kernel oops catching service
speech-dispatcher disabled
  Starting the Winbind daemon 
  starting bluetooth
  Pulseaudo configured for per-user session
  Enabling additional executable binarmy formats
  checking battery state

All these have the customary [OK] by them.  But once it gets to that last option, the laptop hangs and refuses to boot.  I have tried booting with different kernels from the grub menu, no effect.  I can boot into recovery mode though.  Tried to start x there, and it would not start up.  Hope this sheds some more light on the situation

---

### Post by gdonwallace on 2011-03-16
update:

I was able to boot up with the Ubuntu 10.10 live CD.  I can see both the partitions on my laptop, the Ubuntu and Windows.

I was able to get the data I needed off the Ubuntu partition and copy to another machine.  So I am thinking that there is nothing wrong with the partition manager, or the way the hard drive is reporting the partitions.  Still a little stumped as to why it will not boot up though.  Very odd.

---

