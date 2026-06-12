---
title: "Software sources"
date: 2009-12-17
forum: Installation &amp; Upgrades
---

### Post by Robbyx on 2009-12-17
How do I handle the following error message in the update manager:

> GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 9780C41BBDFD6D77GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY EF4186FE247510BEFailed to fetch [http://mirror.noreply.org/pub/tor/dists/karmic/main/binary-i386/Packages.gz](http://mirror.noreply.org/pub/tor/dists/karmic/main/binary-i386/Packages.gz)  404  Not Found
Some index files failed to download, they have been ignored, or old ones used instead.

Robin

---

### Post by oldos2er on 2009-12-17
You're missing an authentication key. Try ```
gpg --keyserver subkeys.pgp.net --recv 9780C41BBDFD6D77

gpg --export --armor 9780C41BBDFD6D77 | sudo apt-key add -
```

---

### Post by slakkie on 2009-12-17
And in one command:

sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys KEYID

keyserver.ubuntu.com is sometimes acting up, you can then use: wwwkeys.eu.pgp.net

---

### Post by Robbyx on 2009-12-17
> **slakkie said:**
> And in one command:

sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys KEYID

keyserver.ubuntu.com is sometimes acting up, you can then use: wwwkeys.eu.pgp.net

Thanks. This is what I put into the command line:

gpg --keyserver subkeys.pgp.net --recv EF4186FE247510BE

This is what I got back:

> rob@rob-desktop:~$ gpg --keyserver subkeys.pgp.net --recv EF4186FE247510BE
gpg: requesting key 247510BE from hkp server subkeys.pgp.net
gpgkeys: key EF4186FE247510BE not found on keyserver
gpg: no valid OpenPGP data found.
gpg: Total number processed: 0
rob@rob-desktop:~$ 


This is the error message, which is where I found the keyid:
> 
GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY EF4186FE247510BEFailed to fetch [http://mirror.noreply.org/pub/tor/dists/karmic/main/binary-i386/Packages.gz](http://mirror.noreply.org/pub/tor/dists/karmic/main/binary-i386/Packages.gz)  404  Not Found
Some index files failed to download, they have been ignored, or old ones used instead.

I also tried the key 9780C41BBDFD6D77  as in the reply by oldos2er below and it worked in that the key was updated,except it made no difference to the error  message when updating the files from the repository indexes.

Would you mind telling what I should do next?

Robin

---

### Post by oldos2er on 2009-12-17
The 404 error has nothing to do with the gpg key error. It appears the directory "karmic" does not exist at [http://mirror.noreply.org/pub/tor/dists/](http://mirror.noreply.org/pub/tor/dists/).

---

### Post by slakkie on 2009-12-18
> **Robbyx said:**
> Thanks. This is what I put into the command line:

gpg --keyserver subkeys.pgp.net --recv EF4186FE247510BE



Would you mind telling what I should do next?

Robin

Use a different keyserver, eg keyserver.ubuntu.com or the one I provided from pgp.net, I use those two for Ubuntu/Debian and had no problems importing keys for PPA's.

---

### Post by Robbyx on 2009-12-18
I disabled the tor update in the sources and that has removed one of the error messages.

I am still left with the following:

W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY EF4186FE247510BE

I had assumed the numbers above each description is the public key.
I have gone through the authentication list of the trusted software providers in Software Sources. I can not find an entry for EF4186FE247510BE. 

Please, how do I find the entry to which it relates?

---

### Post by Robbyx on 2009-12-20
I would very much appreciate a reply. This error message arose after I upgraded to Karmic.

---

### Post by Robbyx on 2009-12-20
I found the answer here:

[http://ubuntuforums.org/showthread.php?t=1271353&highlight=software+sources](http://ubuntuforums.org/showthread.php?t=1271353&highlight=software+sources)

---

### Post by slakkie on 2009-12-20
> **Robbyx said:**
> I found the answer here:

[http://ubuntuforums.org/showthread.php?t=1271353&highlight=software+sources](http://ubuntuforums.org/showthread.php?t=1271353&highlight=software+sources)

Which post exactly?

---

### Post by Robbyx on 2009-12-20
Number 2 worked for me. 

BTW how do I copy the url of a message?  I have seen others point to a thread or a message. I assume they do not copy the URL from the address bar.

---

