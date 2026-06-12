---
title: "&quot;Invalid or corrupt kernel image&quot; during install"
date: 2006-09-21
forum: Installation &amp; Upgrades
---

### Post by JonDaAzn on 2006-09-21
I am trying to install ubuntu onto a new computer, but when i scan the cd for defects (in the boot menu)i get "invalid or corrupt kernel image". I've tried re-downloading and re-burning the cd only to get the same result (x3)

i use isorecorder to burn the cds and have burnt at both 48x speed and 10x speed, i have also checked the files md5 checksum using fastsums and it came up clean

the computer is running an intel core 2 duo processor and the file i downloaded is ubuntu-6.06.1-desktop-i386

help!

:its also saying "could not find kernel image: /casper/vmlinuz" when i hit the "start ubuntu in safe graphics mode" button on the boot menu

---

### Post by JonDaAzn on 2006-09-22
bumpity bump

---

### Post by HACristian on 2007-03-29
.

---

### Post by scienceinc on 2007-04-07
got the same problem here!

anyone?

---

### Post by clucena on 2007-09-23
Take a look at [http://www.linuxforums.org/forum/redhat-fedora-linux-help/61074-could-not-load-kernel-image-linux.html]("http://www.linuxforums.org/forum/redhat-fedora-linux-help/61074-could-not-load-kernel-image-linux.html")

---

### Post by Steve White on 2007-10-20
Similar problem here, with Ubuntu and Kubuntu 7.10 (in a sense worse, because the GUI just fails silently).  This is a Dell D420, one of the images was kubuntu-7.10-desktop-i386.iso, downloaded today.
A Ubuntu 6.10 installer from earlier in the year works fine though.

By hitting F1 repeately I get a boot line.  I've tried lots of combinations.  I will try the 
[INDENT]vmlinuz initrd=initrd.img[/INDENT]
suggested in the above RedHat discussion, but since other people had no luck with it.

I checked the md5 sum on the ISO image, and it was OK.  I suspect something went fishy with the burning, but have no idea what (I burned with K3B in the way I always do...I tried it twice; it didn't mention any problems.)

---

### Post by Steve White on 2007-10-20
I mounted the CD image directly, and the CD, then did a diff of vmlinuz and initrd.img under casper/.
They were identical.

Tried the above suggestion of "vmlinuz initrd=initrd.img".  This will not work.  It gives 
[INDENT]Could not find kernel image: vmlinuz
[/INDENT]
But it also didn't work for the other RedHat people.

I tried several of the other boot parameters mentioned in the help under the various F-keys, including
[INDENT]live aic7xxx.aic7xxx=no_probe[/INDENT]
This also failed with the "corrupt image" message.

It looks as if a lot of the help in there is wrong.  It suggests to use various images "live-expert" and "rescue".  These all give 
[INDENT]Could not find kernel image: vmlinuz
[/INDENT]

---

