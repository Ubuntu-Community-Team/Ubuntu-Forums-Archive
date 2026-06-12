---
title: "Update Error: NO_PUBKEY 54422A4B98AB5139"
date: 2010-06-08
forum: Installation &amp; Upgrades
---

### Post by moonport on 2010-06-08
The error occurs every time I want to update Lucid Lynx through update manager:

W: An error occurred during signature verification. The repository has been updated and will use the previous index files.
GPG Error: [http://download.virtualbox.org](http://download.virtualbox.org) lucid Release
The following signatures could not be verified because the public key is not available: NO_PUBKEY 54422A4B98AB5139

W: Unable to obtain [http://download.virtualbox.org/virtualbox/debian/dists/lucid/Release](http://download.virtualbox.org/virtualbox/debian/dists/lucid/Release)  

Any clues?.
TIA

---

### Post by zvacet on 2010-06-08
In terminal 

```
gpg --keyserver hkp://subkeys.pgp.net --recv-keys 54422A4B98AB5139
gpg --export --armor 54422A4B98AB5139 | sudo apt-key add -
```

Press enter after each command.

---

### Post by moonport on 2010-06-08
Thanks, zvacet. 
The issue persists, but apparently it's a problem at Oracle 
Servers.

---

### Post by aaronLund on 2010-06-20
I'm getting the same error on Hardy.

---

### Post by Thatlinuxguy on 2010-06-23
I am having same prob on 10.04 and this is the output I get
```
W: GPG error: http://security.ubuntu.com lucid-security Release: Unknown error executing gpgv
W: GPG error: http://archive.canonical.com lucid Release: Unknown error executing gpgv
W: GPG error: http://archive.canonical.com lucid Release: Unknown error executing gpgv
W: GPG error: http://ppa.launchpad.net lucid Release: Unknown error executing gpgv
W: GPG error: http://us.archive.ubuntu.com lucid Release: Unknown error executing gpgv
W: GPG error: http://ppa.launchpad.net lucid Release: Unknown error executing gpgv
W: GPG error: http://us.archive.ubuntu.com lucid-updates Release: Unknown error executing gpgv
W: GPG error: http://ppa.launchpad.net lucid Release: Unknown error executing gpgv
W: GPG error: http://us.archive.ubuntu.com lucid-backports Release: Unknown error executing gpgv
W: Failed to fetch http://ppa.launchpad.net/merlwiz79/aurora/ubuntu/dists/lucid/main/binary-i386/Packages.gz  404  Not Found

E: Some index files failed to download, they have been ignored, or old ones used instead.

```

---

### Post by gmjs on 2010-07-13
Hello,

Can you try the following line at the terminal to reinstall 'Ubuntu Keyring' to see if it resolves the issue or provides a clue as to what's causing the problem:

```
$ **sudo aptitude reinstall ubuntu-keyring**
```

---

### Post by phy4eveything on 2010-07-13
i have the problem with update

---

