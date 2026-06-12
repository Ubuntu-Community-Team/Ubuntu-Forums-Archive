---
title: "Error messages after updating the apt-get"
date: 2012-07-05
forum: Installation &amp; Upgrades
---

### Post by em wai zee on 2012-07-05
Hi, I'm new to Ubuntu 12.04. I just did a regular 

> sudo apt-get update

through the terminal and got these errors after finishing the updating. Could anyone help me to understand these errors and overcome it. Thank you!

[QUOTE W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release: The following signatures were invalid: BADSIG FC0D5CCAEDFBD1F9 Launchpad Bleeding-Edge OpenShot PPA
W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 531EE72F4C9D234C
W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 6AF0E1940624A220
W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release: The following signatures were invalid: BADSIG C2518248EEA14886 Launchpad VLC
W: Failed to fetch [https://private-ppa.launchpad.net/commercial-ppa-uploaders/tiberiumalliances/ubuntu/dists/precise/main/binary-amd64/Packages](https://private-ppa.launchpad.net/commercial-ppa-uploaders/tiberiumalliances/ubuntu/dists/precise/main/binary-amd64/Packages)  gnutls_handshake() failed: A TLS packet with unexpected length was received.

W: Failed to fetch [https://private-ppa.launchpad.net/commercial-ppa-uploaders/tiberiumalliances/ubuntu/dists/precise/main/binary-i386/Packages](https://private-ppa.launchpad.net/commercial-ppa-uploaders/tiberiumalliances/ubuntu/dists/precise/main/binary-i386/Packages)  gnutls_handshake() failed: A TLS packet with unexpected length was received.

W: Failed to fetch gzip:/var/lib/apt/lists/partial/archive.ubuntu.com_ubuntu_dists_precise-backports_main_i18n_Translation-en  Encountered a section with no Package: header

E: Some index files failed to download. They have been ignored, or old ones used instead.
][/QUOTE]

---

### Post by dino99 on 2012-07-05
[http://askubuntu.com/questions/1877/what-is-the-easiest-way-to-resolve-apt-get-badsig-gpg-errors](http://askubuntu.com/questions/1877/what-is-the-easiest-way-to-resolve-apt-get-badsig-gpg-errors)

---

### Post by cortman on 2012-07-05
Hi, GPG errors are easy enough to fix. Instructions available [here]("http://cortman.wordpress.com/2012/02/27/how-to-fix-gpg-errors-in-ubuntu/").

---

### Post by em wai zee on 2012-07-06
> **dino99 said:**
> [http://askubuntu.com/questions/1877/what-is-the-easiest-way-to-resolve-apt-get-badsig-gpg-errors](http://askubuntu.com/questions/1877/what-is-the-easiest-way-to-resolve-apt-get-badsig-gpg-errors)

TQ so much ... I'm digesting it right now! Will update you on the aftermath!

---

### Post by em wai zee on 2012-07-06
> **cortman said:**
> Hi, GPG errors are easy enough to fix. Instructions available [here]("http://cortman.wordpress.com/2012/02/27/how-to-fix-gpg-errors-in-ubuntu/").

I'm digesting it right now ... Thank U so much! Will update you on the aftermath!

---

