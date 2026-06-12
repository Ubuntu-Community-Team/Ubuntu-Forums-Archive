---
title: "Feisty Fawn Installation errors"
date: 2007-06-07
forum: Installation &amp; Upgrades
---

### Post by Cilionelle on 2007-06-07
Installing Feisty from an Alternative CD, onto a Dell Inspiron 1100, 640 Mb RAM, 30 Gb HDD, integrated Intel 845G chipset, I got these messages:

Warning: file:///cdrom/pool/main/p/perl/perl_5.8.8-7build1_1386.deb was corrupt
Warning: Failure while configuring base packages.  This will be attempted 5 times [this one occurs 5 times!]
Unable to install initramfs-tools.  An error was returned while trying to install the initramfs-tools package onto the target system.  Check /var/log/syslog or see virtual console 4 for details.
Installation step failed.  You can try to run the failing item again from the menu, or skip it and choose something else.  The failing step is: Install the base system.

Then it bumps me to the installation menu.  The CD is fine tho, check on my other comp both prior to installing and after this message came up.  Would it be some residual thing on the system?  Should I skip "Installing the base system" and move on (which seems inherently problematic to me!)?

Ta!

---

### Post by Cilionelle on 2007-06-08
Could it be a problem with the CD?

---

### Post by zvacet on 2007-06-08
Chek Cd for errors(you have that option when you boot up)and see what result will be.If cheking shows that is no errors you probably burned CD to fast,so burn it in lower possible speed nex time.If you find errors download iso with torrent and direct download to the folder where your iso is.torrent will just chek your iso and if find some corrupted files will replace them with good ones.After that burn it to CD very slow.

---

### Post by Cilionelle on 2007-06-08
Tried reburning the CD very slowly, to no avail.  The .deb packages are still corrupted, and I get the same messages every time. The disc (new one) comes back with errors on it, and so won't work... what now?

---

### Post by Cilionelle on 2007-06-08
bump...

---

### Post by merlinus on 2007-06-08
This may help, especially the information about checksums.

[http://www.psychocats.net/ubuntu/iso](http://www.psychocats.net/ubuntu/iso)

-merlin

---

### Post by Cilionelle on 2007-06-09
Checksums match.  Still no luck.  I have also done a complete series of checks on the laptop to make sure it is not hardware related.

---

### Post by pt123 on 2007-06-09
I had a similar problem, 2 packages were corrupt and then it wanted to download all the packages from the internet. 

Dumb logic.

The testing on the upgrade for Feisty has been very poor.

---

### Post by Cilionelle on 2007-06-09
Well, currently, I haven't been able to get *any* versions of Ubuntu to work right... with 6.06 and 6.10, resolution was stuck at 640x480, then with Feisty, I can't even get it off the ground.  I am seriously thinking of dumping Ubuntu and checking out other versions of Linux - to see if maybe the problem is not it, but me!

---

### Post by Cilionelle on 2007-06-09
bump...

---

### Post by Cilionelle on 2007-06-09
And again...

---

### Post by Cilionelle on 2007-06-09
And one last time...

---

### Post by hugstari on 2007-06-09
I'm doing a clean Feisty alternative dual boot install and am getting the same error messages, only difference for me is different packages. Checksum is correct and the installer tells me the CD is ok.

Perhaps i burned the iso to fast and that's my problem, going to try and burn it again slower and see what happens but going to keep an i on this tread in the mean time. Anyways first post here, alot of great info and nice people it seems and i´m looking forward to get Ubuntu up and running :)

edit: Worked like a charm the second time, burning the CD at 1X speed might have been it, otherwise everything was done the same as before. Well next step is configuration...

---

### Post by pt123 on 2007-06-09
You are better of reporting this to 
[https://launchpad.net/distros/ubuntu](https://launchpad.net/distros/ubuntu)

There are lot more technical people there.

---

### Post by PilotJLR on 2007-06-16
I just now encountered a similar error. First time I've seen it on many installs. This is what I did.
- tried to boot from normal Desktop Live CD (won't get t past splash screen)
- boot alternate cd (freezes at 6% when installing packages)
- boot from canonical-pressed CD (same results as with the cd 1 burned).

Each CD passes md5sum on individual packages, as well as on the whole disk.

I fixed this by:
- booting Alternate install mode CD
- selecting "Install command-line only system)
- Once it's installed (yay!) install the graphical desktop (ubuntu-desktop) using apt-get.

---

### Post by nzcyclone on 2007-06-17
I had the same problem when trying to burn it to disk. I found the problem eventually after bashing my head against the wall a few times. Solution when burning was to go into options and disable "Write at once" and i then manually lowered the burn speed to 16x since done that the ISO burns fine no errors and cd passing checks.

---

