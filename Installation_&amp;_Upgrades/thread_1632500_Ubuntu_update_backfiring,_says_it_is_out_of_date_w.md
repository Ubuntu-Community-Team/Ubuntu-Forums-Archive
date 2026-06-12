---
title: "Ubuntu update backfiring, says it is out of date while it is not"
date: 2010-11-28
forum: Installation &amp; Upgrades
---

### Post by CMDRSweeper on 2010-11-28
My Ubuntu got updated today, with a new kernel appearently, however the problems started with the fact that my "X amount of days / hours since you last updated" stayed at 18 days (Laptop have been powered off for that amount of time.) 
So I got a warning triangle up by the clock concerning this update problem as well, with a quick google I found an old thread from 2008 and tried a few of the tricks, reverting between the servers to reload the packages if I am correct, and that fails with the following outputed error:

```
W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used. GPG error: http://extras.ubuntu.com maverick Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY DB141E2302FDF932

W: Failed to fetch http://extras.ubuntu.com/ubuntu/dists/maverick/Release  

W: Some index files failed to download, they have been ignored, or old ones used instead.
```

Any idea how to fix this annoyance?

---

### Post by wet-willy on 2010-11-28
This error has nothing to do with date, it has to do with not having the gpg key for the extras repository. Run the command below to acquire it:
```
sudo gpg --keyserver hkp://wwwkeys.eu.pgp.net --recv-keys 02FDF932 && gpg --armor --export 02FDF932 | apt-key add -
```

---

### Post by CMDRSweeper on 2010-11-28
Did not work appearently :S
```
cmdrsweeper@sweeperlaplinux:~$ sudo gpg --keyserver hkp://wwwkeys.eu.pgp.net --recv-keys 02FDF932 && gpg --armor --export 02FDF932 | apt-key add -
[sudo] password for cmdrsweeper: 
gpg: directory `/home/cmdrsweeper/.gnupg' created
gpg: new configuration file `/home/cmdrsweeper/.gnupg/gpg.conf' created
gpg: WARNING: options in `/home/cmdrsweeper/.gnupg/gpg.conf' are not yet active during this run
gpg: keyring `/home/cmdrsweeper/.gnupg/secring.gpg' created
gpg: keyring `/home/cmdrsweeper/.gnupg/pubring.gpg' created
gpg: requesting key 02FDF932 from hkp server wwwkeys.eu.pgp.net
gpg: /home/cmdrsweeper/.gnupg/trustdb.gpg: trustdb created
gpg: key 02FDF932: public key "Launchpad Application Review Board PPA" imported
gpg: Total number processed: 1
gpg:               imported: 1  (RSA: 1)
gpg: failed to create temporary file `/home/cmdrsweeper/.gnupg/.#lk0x88798e0.sweeperlaplinux.8135': Permission denied
gpg: keyblock resource `/home/cmdrsweeper/.gnupg/secring.gpg': general error
gpg: failed to create temporary file `/home/cmdrsweeper/.gnupg/.#lk0x8879d08.sweeperlaplinux.8135': Permission denied
gpg: keyblock resource `/home/cmdrsweeper/.gnupg/pubring.gpg': general error
gpg: WARNING: nothing exported
gpg: no valid OpenPGP data found.

```

---

### Post by wet-willy on 2010-11-28
It did import the key, just couldn't use it due to permission issues. Hmmm!
I always do this as root and have no issues, try without sudo.
I changed my post, it failed to create temp files which I originally was looking for attributes, files that don't exist.
I'm done for now.

---

### Post by plucky on 2010-11-28
The last part of the command should be ```
sudo apt-key add -
```

So the command would be 
```
sudo gpg --keyserver hkp://wwwkeys.eu.pgp.net --recv-keys 02FDF932 && gpg --armor --export 02FDF932 | sudo apt-key add -
```


Good Luck

---

### Post by CMDRSweeper on 2010-11-28
Ah solved it, what I basically had to do was run the command you initially gave me as root.
By using the "sudo su" command first then removing sudo from your command and I got to do what I wanted to.

---

### Post by wet-willy on 2010-12-07
Not sure what I did, if I even enabled that repo in Ubuntu, can't tell right now as that machine is tied up. I have three pre-written 'fetch key commands' in notes and just copy and past the appropriate one when needed, same command for all, just change the 8 digit ID to match the key apt says your missing.

Anyway, I'm migrating to Debian Live as I can design my own rather than use a pre-configured live distribution that requires too much persistence space to get it the way you like on a USB key. Plus a live Debian boots as fast as a Ubuntu hard drive install, Ubuntu live USB using the image is nothing short of retarded at bootup. So I have to include the keys to the repositories I plan on adding to the live USB image, the two keys I know I'll need to include are:

dmo-archive-keyring
debian-multimedia-keyring

Both of which can be installed from package manager in a running system. Have a look in your package manager for something like that, in synaptic, use "keyring" in the quick search field.

---

