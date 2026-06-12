---
title: "&quot;ghosting&quot; Ubuntu HDD onto another drive"
date: 2005-11-18
forum: Installation &amp; Upgrades
---

### Post by brokenbones on 2005-11-18
Hi,

I am quite a beginner so please be patient and please answer in understandable terms...

I have a computer with a 250 GB HDD, with win2003 server installed  and configured on it. There are 30 GB on unused unformatted space on it.

I added an old 20 GB HDD and installed Breezy Badger. I like it so much that I would like to move it to the bigger, faster and more silent drive in the free 30 GB, without corrupting the current win2003 install. I would like to remove the old noisy slow 20 GB HDD after that. I need to dual boot this machine, and I am a bit worried about grub not finding the Ubuntu install after ghosting, if ghosting is even possible.

Any step-by-step directions ? Thank you in advance !

---

### Post by poptones on 2005-11-18
Why don't you just install ubuntu on the 30GB of free unpartitioned space and then copy your /home folder from the old drive to the new install?

---

### Post by brokenbones on 2005-11-19
Because:

1) I didn't know it was an option

2) I thought grub would then offer too many boot options after the 20 GB drive would be removed and I don't know yet how to edit grub options

3) my ubuntu install is already quite well personalized, and I was afraid to loose all I have done up to now. I have XAMPP for linux installed, with a PHPNuke portal and I would like to avoid doing the install again. I thought ghosting my current install would allow me to keep everything.

Are my reasons good enough ? ;)

---

### Post by poptones on 2005-11-19
Then you will want to copy over /opt, /srv, /usr and /var as well. You may also have to copy some files from /etc but if you do that willy-nilly you will make the new installation unbootable. 

Anyway, it sounds like you have the free space already set up, so you can install on the new drive and try it. If it doesn't work, do it again.  so long as you have the old install on the other drive, you get many shots at making it work. 

make a new installation on the newer drive, boot into it to make sure it works, then reboot to recovery mode. From the command line copy the folders I said  from the old drive to the new drive and reboot again.

---

### Post by matthewv on 2005-11-19
or you could just do a total fresh install...

---

