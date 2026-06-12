---
title: "Get a public key for Kali?"
date: 2015-01-02
forum: MINT
---

### Post by snitz2 on 2015-01-02
I'm trying to install Kali on LinuxMint 17 following this tutorial here
[https://www.youtube.com/watch?v=bk-GcvcToKE](https://www.youtube.com/watch?v=bk-GcvcToKE)


It says in order to fix the GPG error in updater "NO_PUBKEY", I have to use this command
> sudo apt-key adv --keyserver subkeys.pgp.net --recv-keys


But that keeps giving me "server timed out"


This is the initial error I got in the terminal


> W: GPG error: [http://repo.kali.org](http://repo.kali.org) kali-bleeding-edge InRelease: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY ED444FF07D8D0BF6
W: GPG error: [http://http.debian.net](http://http.debian.net) wheezy-updates InRelease: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 8B48AD6246925553
W: GPG error: [http://http.kali.org](http://http.kali.org) kali InRelease: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY ED444FF07D8D0BF6
W: GPG error: [http://security.kali.org](http://security.kali.org) kali/updates InRelease: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY ED444FF07D8D0BF6
W: GPG error: [http://security.debian.org](http://security.debian.org) wheezy/updates InRelease: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 8B48AD6246925553
W: GPG error: [http://http.debian.net](http://http.debian.net) wheezy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 8B48AD6246925553 NO_PUBKEY 6FB2A1C265FFB764


I've tried several other keyservers but no luck as well.


> gpg --keyserver pgpkeys.mit.edu --recv-key  ED444FF07D8D0BF6


How do I get around this?

---

### Post by howefield on 2015-01-02
Thread moved to the "*MINT*" section of the forums.

---

### Post by Habitual on 2015-01-02
[http://forums.linuxmint.com/viewtopic.php?f=47&t=186316](http://forums.linuxmint.com/viewtopic.php?f=47&t=186316)

---

