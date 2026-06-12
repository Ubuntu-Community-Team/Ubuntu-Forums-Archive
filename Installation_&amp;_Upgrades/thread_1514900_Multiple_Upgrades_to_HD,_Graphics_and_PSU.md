---
title: "Multiple Upgrades to HD, Graphics and PSU"
date: 2010-06-21
forum: Installation &amp; Upgrades
---

### Post by 8jwong14 on 2010-06-21
Hey everyone,
I currently have a HP Pavilion a6554f with dual booted Windows and Ubuntu.  I plan on upgrading from the stock integrated Intel graphics to a EVGA videocard.  I also plan on adding a second harddrive.  To support these upgrades I'm also getting a new OCZ power-supply.

My question or rather questions is how exactly do I do this.  What process should I go about?  Which do I install first and sequence?  Also, since I would have 2 harddrives, the first one would be the boot partition for both Windows Vista and Ubuntu.  I want the second drive to be shared files such as music and videos so I won't store any personal stuff on the first HD except for programs and software.  What format should the second HD be so both Vista and Ubuntu can read them?  Also, how do I make Ubuntu automatically have full access to the second HD without asking me for any passwords or require me to manually mount it via Nautilus and still make sure Banshee can access the media there?

Please help me.  I'd appreciate it.

---

### Post by davidmohammed on 2010-06-21
I'm sure there is lots of ways, but my suggestion would be

1. install the power supply - make sure both windows and ubuntu power up OK.
2. install the second hard-drive.  Format it as ntfs in windows.  
3. in Ubuntu, install ntfs-config (install from synaptic) - it will automatically recognise your second drive.  Just give it full read and write rights.
4. Install you new graphics card.

---

### Post by 8jwong14 on 2010-06-21
> **davidmohammed said:**
> I'm sure there is lots of ways, but my suggestion would be

1. install the power supply - make sure both windows and ubuntu power up OK.
2. install the second hard-drive.  Format it as ntfs in windows.  
3. in Ubuntu, install ntfs-config (install from synaptic) - it will automatically recognise your second drive.  Just give it full read and write rights.
4. Install you new graphics card.
Thanks.  But one thing, would the second HD automatically mount on boot with full access without asking for any password or such so Banshee can run right away and play from its library containing songs located in 2nd HD?  I.E. currently I have 1 HD and 3 partitions (Vista, Ubuntu, and shared)  I tried to put all my media only on the shared partition but Rhythmbox could not play music in its library if the songs were located in a different partition.

---

### Post by davidmohammed on 2010-06-21
yes - ntfs-config will make the necessary changes in your /etc/fstab to mount your second drive automatically and it will connect without a password - that's what I did to my PC when I fitted a second drive.

---

### Post by 8jwong14 on 2010-06-21
> **davidmohammed said:**
> yes - ntfs-config will make the necessary changes in your /etc/fstab to mount your second drive automatically and it will connect without a password - that's what I did to my PC when I fitted a second drive.
Thank you so much.  :)  This is why Ubuntu or rather open source is so great.  A great helpful community and a lot of software and programs to do so much.

---

