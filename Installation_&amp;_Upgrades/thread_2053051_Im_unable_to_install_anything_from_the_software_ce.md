---
title: "Im unable to install anything from the software center"
date: 2012-09-04
forum: Installation &amp; Upgrades
---

### Post by Snoodles on 2012-09-04
Ubuntu 12.04 32-bit here. 
I tried going into the software sources tab and clicking "restore defaults" in the authentication section but it doesn't seem to change anything. 

This is what I get when I run apt-get update:

```
W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used. GPG error: http://deb.torproject.org precise InRelease: The following signatures were invalid: KEYEXPIRED 1346668560 KEYEXPIRED 1346668560 KEYEXPIRED 1346668560 KEYEXPIRED 1346668560

W: GPG error: http://ppa.launchpad.net precise Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY FAEB83059BD4ED25
W: Failed to fetch http://deb.torproject.org/torproject.org/dists/precise/InRelease  


```

---

### Post by matt_symes on 2012-09-04
Hi

Open a terminal and type

```
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys FAEB83059BD4ED25
```

Enter your password. It will not be echoed to the screen. This should import the key you are missing.

Then type

```
sudo apt-get update
```

Kind regards

---

### Post by Snoodles on 2012-09-04
> **matt_symes said:**
> Hi

Open a terminal and type

```
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys FAEB83059BD4ED25
```

Enter your password. It will not be echoed to the screen. This should import the key you are missing.

Then type

```
sudo apt-get update
```

Kind regards

Hello, thanks for your help. I pasted your command and this is what I got: 

```
K53SV:~$ sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys FAEB83059BD4ED25
Executing: gpg --ignore-time-conflict --no-options --no-default-keyring --secret-keyring /tmp/tmp.N6ydXrZXSv --trustdb-name /etc/apt/trustdb.gpg --keyring /etc/apt/trusted.gpg --primary-keyring /etc/apt/trusted.gpg --keyserver keyserver.ubuntu.com --recv-keys FAEB83059BD4ED25
gpg: requesting key 9BD4ED25 from hkp server keyserver.ubuntu.com
gpg: key 9BD4ED25: "Launchpad Trimage" not changed
gpg: Total number processed: 1
gpg:              unchanged: 1

```

I'm still getting this error:
```
W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used. GPG error: http://deb.torproject.org precise InRelease: The following signatures were invalid: KEYEXPIRED 1346668560 KEYEXPIRED 1346668560 KEYEXPIRED 1346668560 KEYEXPIRED 1346668560

W: GPG error: http://ppa.launchpad.net precise Release: The following signatures were invalid: BADSIG FAEB83059BD4ED25 Launchpad Trimage
W: Failed to fetch http://deb.torproject.org/torproject.org/dists/precise/InRelease  

W: Some index files failed to download. They have been ignored, or old ones used instead.
arturo@arturo-K53SV:~$ 

```

---

### Post by alizard on 2012-09-05
this will update your keyring for deb.torproject.org 

sudo apt-get install deb.torproject.org-keyring

I had the same problem.

---

### Post by Snoodles on 2012-09-05
> **alizard said:**
> this will update your keyring for deb.torproject.org 

sudo apt-get install deb.torproject.org-keyring

I had the same problem.

Thanks alizard. This seems to have solved half of the problem. What I'm getting now is this:
```
Reading package lists... Done
W: GPG error: http://ppa.launchpad.net precise Release: The 
following signatures were invalid: BADSIG FAEB83059BD4ED25
Launchpad Trimage

```

---

### Post by oldos2er on 2012-09-05
[http://www.ubuntugeek.com/how-to-fix-the-ubuntu-gpg-error-badsig.html/comment-page-1#comment-119310](http://www.ubuntugeek.com/how-to-fix-the-ubuntu-gpg-error-badsig.html/comment-page-1#comment-119310)

---

### Post by wiljago on 2012-09-07
> **alizard said:**
> this will update your keyring for deb.torproject.org 

sudo apt-get install deb.torproject.org-keyring

I had the same problem.
  
Thank you!

---

### Post by kagz on 2012-09-07
thanks Snoodles..that worked for me in my backtrack 5 os..

---

### Post by earthmeLon on 2012-10-10
Here are the 'Official' instructions: [https://www.torproject.org/docs/debian.html.en#packages](https://www.torproject.org/docs/debian.html.en#packages) (in case things change in the future).  
Here is how you can add individual developers' keys: [https://www.torproject.org/docs/verifying-signatures.html](https://www.torproject.org/docs/verifying-signatures.html).

Don't forget to contribute back to TorProject (if you have the means).  The most simple way is setting up a 'Tor Cloud': [https://cloud.torproject.org/](https://cloud.torproject.org/)

---

