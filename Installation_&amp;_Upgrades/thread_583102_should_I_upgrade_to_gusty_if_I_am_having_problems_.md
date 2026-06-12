---
title: "should I upgrade to gusty if I am having problems with feisty"
date: 2007-10-20
forum: Installation &amp; Upgrades
---

### Post by Tuxoid on 2007-10-20
I have been using feisty on my LG P1 notebook. It overheats like crazy (sometimes causing emergency shutdowns), has some hardware that needed packages or configurations to work (915 resolution and modification to get my audio to work), and does not recognize some of my hardware (specifically my ethernet adapter although wi-fi worked right out of the box). I'd love to upgrade to Gusty, but I don't want my configuration to go to pot. I also don't want to have urgent new problems that. If it does not work out, I can't use my computer, Ubuntu is my only OS.

---

### Post by Sef on 2007-10-20
I would download Gutsy's Live CD and run it.   See how it runs: better, the same, or worse, then make my decision about upgrading to Gutsy or not.

---

### Post by Tuxoid on 2007-10-20
It doesn't want to upgrade from the update manager. It does want to get my last updates for feisty; wine stuff. I can't get it to retrieve the update list. It's saying:

W: GPG error: [http://packages.medibuntu.org](http://packages.medibuntu.org) feisty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2EBC26B60C5A2783

---

### Post by Tuxoid on 2007-10-20
I tried:
```
 gpg --keyserver subkeys.pgp.net --recv 2EBC26B60C5A2783
gpg --export --armor 2EBC26B60C5A2783 | sudo apt-key add
```

with these results:

```
gpg: requesting key 0C5A2783 from hkp server subkeys.pgp.net
gpgkeys: HTTP fetch error 5: Couldn't resolve proxy ''
gpg: no valid OpenPGP data found.
gpg: Total number processed: 0

```

```
Password:gpg: WARNING: nothing exported

gpg: can't open `': No such file or directory
```

In other words, it still doesn't work.

---

### Post by Can+~ on 2007-10-20
Download the LiveCD via bitorrent and burn it ;D.

---

### Post by Tuxoid on 2007-10-20
very sorry, I didn't say that I actually followed the instructions of the first poster who said to use the LiveCD. It worked except for the audio (hda) and the title bars turned huge. I don't want to do a fresh install, if I can avoid it, so I have been trying to get the last updates for feisty so I can upgrade to Gusty when I hit the snag with the pubkeys. I don't plan on losing my files because of a fresh install.

---

### Post by Tuxoid on 2007-10-20
I got it to stop showing the error for the medibuntu repo, but I still can't get to the upgrade screen mentioned here:[http://www.ubuntu.com/getubuntu/upgrading](http://www.ubuntu.com/getubuntu/upgrading) (the one shown in the update manager).

---

