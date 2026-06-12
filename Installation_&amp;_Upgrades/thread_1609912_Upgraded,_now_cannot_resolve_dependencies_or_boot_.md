---
title: "Upgraded, now cannot resolve dependencies or boot to live CD"
date: 2010-10-31
forum: Installation &amp; Upgrades
---

### Post by theronb on 2010-10-31
I upgraded from 10.04 to 10.10 using Synaptic and the system boots and runs fine, but Synaptic tells me there are four broken packages: lib-dev-bin, libc6 libc6-dev and libnih1. When I try to fix them, Synaptic gives this message:

[INDENT]E: Could not perform immediate configuration on already unpacked 'libgcc1'.Please see man 5 apt.conf under APT::Immediate-Configure for details.[/INDENT]

Running sudo dpkg --configure lubgcc1 in terminal gives this message:

[INDENT]dpkg: dependency problems prevent configuration of libgcc1:
 libgcc1 depends on libc6 (>= 2.2.4); however:
  Package libc6 is not configured yet.
dpkg: error processing libgcc1 (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 libgcc1[/INDENT]

Trying to configure libc6 tells me that it depends on libgcc1, which is not configured yet. This appears to be circular. I checked for unresolved dependencies and got quite a long list and was unable to correct this using aptitude.

I reasoned (?) that it was time to reinstall from CD (I do have home in a separate partition to minimize the pain) but after burning the ISO, when I try to boot it hangs after asking for the desired language - won't continue on to either live CD or install. I'm pretty much a beginner and am stumped at this point, would much appreciate help - especially spelled out in simple terms. Let me know if I need to provide additional information. Thanks!

---

### Post by tommcd on 2010-10-31
> **theronb said:**
> ... after burning the ISO, when I try to boot it hangs after asking for the desired language - won't continue on to either live CD or install. ...
Be sure to run the option "*check CD for defects*" when you first boot the live CD. This will take a minute or two to run. If it reports errors then you need to burn a new CD. 
Also verify the md5sum of the iso image of Ubuntu 10.10 that you downloaded to ensure that it is valid.

---

### Post by P4man on 2010-10-31
for the record, to access the 'check cd for errors' you have to press a key when the purple screen with the keyboard logo at the bottom appears, so well before the language choice.

If the cd checks out allright, in that same menu press f6 to enable nomodeset and see if that helps.

---

### Post by theronb on 2010-10-31
Thanks for the quick responses. The MD5 checked good when I downloaded the iso; I checked the disk as you suggested and it's good, too. Tried the disk on another machine and it loads fine, runs live from CD (didn't try an actual install but the screens came up). 

Tried F6 > nomodeset on the problem machine but this didn't make any difference; selecting either Try Ubuntu or Install results in CD drive running for ~30 sec, then nothing but blank screen and blinking cursor. Is it time to wipe the hard drive and start all over? At least I have backups...

---

### Post by P4man on 2010-10-31
formatting the drive normally wont help boot the livecd. Since 10.04 worked for you earlier, I would try booting a 10.04 liveCD. if that also fails, then the only thing I can think off is that something went wrong with your harddrive since the livecd tries to mount swap partitions on the harddrive. Try disabling the harddrive in the bios and see if it boots then.

If it does boot fine with a 10.04 cd.. then, well you probably want to stick with it, then its something in the new kernel doesnt like your system.

---

### Post by theronb on 2010-11-28
Update - better late than never: Tried booting 10.04 live disk, no luck - still stuck with blank screen and blinking cursor after selecting either Try Ubuntu or Install. Tried the same only from USB, still no luck. Yesterday, my sysadmin, Ubuntu user son-in-law came over and fixed it. Took about four hours of terminal commands alternating with lengthy downloads. 

I don't have all the details but the gist of it was he found that during the version upgrade some files had not installed properly but were still in the archive folder, so he ran dpkg on those and installed. This gave some dependency errors, so next was force-depend. This left some files still missing, so he ran apt-get -f install. 

That's the general outline - anyway, all is good now; Synaptic is working, no broken packages listed. Today, I'm glad my daughter married him. Thanks, Charles!

---

