---
title: "How do I boot from 9.10 CD without the Desktop Effects?"
date: 2010-04-04
forum: Installation &amp; Upgrades
---

### Post by psyopper on 2010-04-04
OK, so this has become alarmingly annoying. Like I may actually want to give up on Ubuntu annoying. 

I broke down and installed Windows 7 on top of my existing 9.10 installation. I was following the instructions here: [http://ubuntuforums.org/showthread.php?t=1035999&page=22](http://ubuntuforums.org/showthread.php?t=1035999&page=22)

The problem is that this is on an Intel Clarkdale machine. The integrated graphics on Clarkdale aren't supported very well (nearly not at all) until 2.6.33 which I have up and running. The problem is that the live cd for 9.10 has 2.6.31 and Compiz enabled by default which forces the hardware video buffer to choke (making going to a tty impossible). 

So I can't boot from a 9.10 (or 9.04) CD without bringing on Compiz because the OS recognizes that I have "compatable" hardware and crashes me out. I can boot from an earlier version but it's not the correct version of Grub. I'd really REALLY like to get grub going once again.

I'd like it even more if the "Recovery CD" actually had an option to boot to a command line, you know... something to recover with.

My fear is that I have to reinstall 9.10 with the alternate CD text installer, let it fail on the first boot, boot to the command line, apt-get purge compiz and finally get into a working OS. Then I have the lovely task of getting it pointed to the correct /home partition.

Any suggestions? Love? Hope?

---

### Post by mikewhatever on 2010-04-04
Try hitting f4 at the boot screen and selecting 'safe mode'.

---

### Post by psyopper on 2010-04-04
Safe Mode still loads Compiz/ Desktop Effects. 

The solution was deceptively simple. An Analog solution to a Digital problem...

Once the desktop completes loading... DONT TOUCH THE MOUSE!

Alt+F2: metacity --replace

---

