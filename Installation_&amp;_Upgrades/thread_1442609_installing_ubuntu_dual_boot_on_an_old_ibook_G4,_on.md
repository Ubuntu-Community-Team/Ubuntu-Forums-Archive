---
title: "installing ubuntu dual boot on an old ibook G4, on a ext. fw drive help needed"
date: 2010-03-30
forum: Installation &amp; Upgrades
---

### Post by bjaz on 2010-03-30
hello all

I'm running into some difficulties installing Ubuntu on an old mac ibook G4 I was given.
sepcs are fine (1. something Ghz processor, 700mb RAM)--yet the internal drive and CD player are dead.
I installed MAC OS 10.4 PPC on a firewiredrive and boot from there.
But how can I install Ubuntu ? I understood that I need to use the non supported PPC version which I downloaded and have burned a CD of. I have an external CD player which works. The Cd's appears in the firewire mac os, and the external FW disk still has 200 Gigs free.
I plan to let the instaler choose this freespace to create the partitions, but how do I get to the installer ?

When i boot with the CD in the drive and press C, nothing happens.
when I press options / alt, ubuntu the ubuntu install CD doesn't show up

I've read that I must use open firmware, and found some key combination, but this doesn't change anything (command, option O F).

I have Gparted if the 200gig partition needs to be repartitioned.
I'm trying to install Ubuntu as a dual boot on this old ibook G4

thanks in advance for your help

ben

---

### Post by bjaz on 2010-03-30
I really don't get why I cannot boot from the external cd player--
the version i'm trying to install is ubuntu-powerpc-karmic, it appears on the mac os 10.4 desktop, but when I reboot and hold C or D, the cd turns, yet it boots into mac os again

have i got the wrong version ?

again, the system i'm booting from is on a firewire drive since the the harddisk is dead, and the CD player is external since the ibook's cd player is also dead...

i've been reading up but don't really understand why i can't boot into the cd

i've tried [https://help.ubuntu.com/community/Installation/PowerPC](https://help.ubuntu.com/community/Installation/PowerPC)
can get into open firmware using 
sudo nvram autoboot?=false -

but then when I type 

boot cd:,\\:tbxi   (difficult, keyboard is azerty so i'm looking for the keys)
i get :

can't OPEN: cd:,\\:tbxi
can't open device or file

i then tried 

**[B]boot usb/node/sbp-2/disk:,\install\yaboot**[/B]
and got a big "no" sign...

thanks

I was thinking about making a .cdr image from the cd and the restoring that onto this 10gig partition i have, i'm really lost

b

---

### Post by bjaz on 2010-03-31
can anyone help ? I'm wondering what could be causing the ubuntu ppc live cd to be unbootable at startup-i've burned 3 so far, no avail. what else could i try to install ubuntu on this machine with no internal HD or CD player ?

thanks in advance for your help

all the best

ben

---

### Post by bjaz on 2010-04-02
bumpity bump.
any clue as to what I could do to install ubuntu on this machine ?
it's fine under mac os 10.4 ppc on a firewire drive.
thanks

---

### Post by bjaz on 2010-04-05
from the lack of answers i'm figuring that this might be the wrong place to ask, or that there is a forum policy against helping out for non officially supported distros ? if this is the case, could someone please point me in the right direction ?

thanks

b

---

### Post by bjaz on 2010-04-07
still not getting anywhere on my own. I'm starting to think that it's not possible to install ubuntu on this machine with a broken internal CD player and Hard disk.
it's sad because mac os 10.4 ppc is up and running, yet the whole point was to install a ubuntu version.

b

---

### Post by bmbufalo on 2010-05-26
Not sure if this applies, happened across it...


[http://www.ppcnux.com/?q=upgrade-from-ubuntu-910-to1004]("http://www.ppcnux.com/?q=upgrade-from-ubuntu-910-to1004")
If you prefer a clean install, it is simple and fast and you will run into little trouble. Installation will go fine, without a problem on my PowerBook G4 1.67GHz. You should burn the big image (daily over 700MB) on a DVD disk which speed up installation.

After the installation you'll have a fine and nice GNU/Linux ... but a link is missing in /dev

Link your optical drive to /dev/cdrom.

i.e. ln -s /dev/hdb /dev/cdrom

After a reboot you can eject the installation disk and when you insert an optical disk it will be mounted by the system.

---

