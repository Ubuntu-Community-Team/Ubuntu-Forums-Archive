---
title: "Ubuntu is asking me for a &quot;passphrase&quot;?! before login??"
date: 2014-07-11
forum: Installation &amp; Upgrades
---

### Post by smokingates on 2014-07-11
Hi, I have recently gone the length to do a fresh install of Ubuntu 14.04 LTS and this time around I decided to encrypt the installation with the option provided and also the home folder. Now when I boot it's asking me for a passphrase to unlock the hard disk but I never created one, the only 2 security measures I have created whilst installing (delete previous and install new) are a standard user account password and the encryption key. At first I thought it must mean the encryption key so I tried that several times to no avail.

After 3 or 4 attempts it drops me to a shell with a message saying about root folder missing I can't recall exactly because the machine in question is in my bedroom and this machine is downstairs in the house where I live.

Any help much appreciated. Thanks.

---

### Post by smokingates on 2014-07-11
Never Mind. I decided to do yet another install without any encrytion. Seems to be working ok so far.

---

### Post by brianmc on 2014-07-12
What you've obviously done is picked the encrypted LVM option on install. That's significantly different from just having an encrypted user directory.

---

