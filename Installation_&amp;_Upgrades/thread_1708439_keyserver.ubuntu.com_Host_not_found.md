---
title: "keyserver.ubuntu.com: Host not found"
date: 2011-03-16
forum: Installation &amp; Upgrades
---

### Post by pwabrahams on 2011-03-16
One thing leads to another.  While trying to solve a problem with streaming audio, I was advised to install the medibuntu repository. But when I do a reload in Synaptic, I get a complaint ```
GPG error: http://ppa.launchpad.net maverick Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY E38FDEE72D75E850GPG error: http://archive.getdeb.net lucid-getdeb Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY A8A515F046D7E7CFFailed to fetch http://ppa.launchpad.net/pcf/cd/ubuntu/dists/maverick/main/source/Sources.gz  404  Not Found
Failed to fetch http://ppa.launchpad.net/pcf/cd/ubuntu/dists/maverick/main/binary-amd64/Packages.gz  404  Not Found
Some index files failed to download, they have been ignored, or old ones used instead.
```
So I tried this:
```
sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com 313D312748A22A95
```
and got this:
```
Executing: gpg --ignore-time-conflict --no-options --no-default-keyring --secret-keyring /etc/apt/secring.gpg --trustdb-name /etc/apt/trustdb.gpg --keyring /etc/apt/trusted.gpg --primary-keyring /etc/apt/trusted.gpg --recv-keys --keyserver keyserver.ubuntu.com 313D312748A22A95
gpg: requesting key 48A22A95 from hkp server keyserver.ubuntu.com
?: keyserver.ubuntu.com: Host not found
gpgkeys: HTTP fetch error 7: couldn't connect: Success
gpg: no valid OpenPGP data found.
gpg: Total number processed: 0

```
Yet the host keyserver.ubuntu.com is reachable:
```
PING keyserver.ubuntu.com (91.189.89.49) 56(84) bytes of data.
64 bytes from boquila.canonical.com (91.189.89.49): icmp_req=1 ttl=49 time=89.3 ms
64 bytes from boquila.canonical.com (91.189.89.49): icmp_req=2 ttl=49 time=87.8 ms
64 bytes from boquila.canonical.com (91.189.89.49): icmp_req=3 ttl=49 time=88.7 ms

```

How can I deal with this?

---

### Post by tommcd on 2011-03-16
That PPA repo seems to be not available at the moment.
[http://ppa.launchpad.net/pcf/cd/ubuntu/dists/maverick/main/binary-amd64/Packages.gz](http://ppa.launchpad.net/pcf/cd/ubuntu/dists/maverick/main/binary-amd64/Packages.gz)
If you remove it then updates should work ok.
> **pwabrahams said:**
> 
 While trying to solve a problem with streaming audio, I was advised to install the medibuntu repository.
That PPA is not the medibuntu repo. Here is how to add medibuntu to your APT sources : [http://medibuntu.org/repository.php](http://medibuntu.org/repository.php)

---

### Post by pwabrahams on 2011-03-16
I apparently had two problems: an unavailable repository and a nonresponsive keyserver. I solved the problem of the unavailable repository by removing it from the Synaptic repository list.  But the keyserver is a different matter.  I don't see how to reconcile the message "keyserver.ubuntu.com: Host not found" with the fact that a ping on keyserver.ubuntu.com gets a response (and a fairly quick one).

---

### Post by tommcd on 2011-03-16
I am not sure about the key server issue. Perhaps the fact that (it) is trying to import a key for a repo that is not available is the source of the problem. 
Did you install the medibintu repo ok?

---

### Post by pwabrahams on 2011-03-16
The medibuntu repository seems to be installed correctly.  If I uncheck some other repositories in Synaptic's list but leave medibuntu, I don't get the error.  In fact, the error seems independent of the key that I provide to apt-key.  Moreover, I can access the URL keyserver.ubuntu.com and even managed to submit a key to it. I wonder if the "Host not found" message is bogus, and really indicates that the keyserver couldn't retrieve the key when the search string is presented to it.

So maybe the public keys for these repositories were never registered with the keyserver.

---

### Post by pwabrahams on 2011-03-17
apt-key calls gpg, which in turn tries to access the keyserver.  Apparently there's a bug in gpg (which I've reported): if the keyserver doesn't have the requested key, then gpg misinterprets that as "host not found".  I tried calling the keyserver directly with the key and found that the keyserver really doesn't know about it.  Why*that* should be the case, I don't know.  Maybe someone just forgot to do something.

---

### Post by coolbrook on 2011-03-17
Try this

keyserver.pgp.com

---

### Post by pwabrahams on 2011-03-20
The key is missing from keyserver.gpg.com also.  But here's a real weirdness: if I use apt-key under Natty (in a virtual machine), the retrieval works, and the key I get also works.  I can even turn it into Ascii and use it in the Maverick environment.

---

