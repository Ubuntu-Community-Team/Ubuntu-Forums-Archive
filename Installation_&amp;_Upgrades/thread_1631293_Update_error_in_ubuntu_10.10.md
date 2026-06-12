---
title: "Update error in ubuntu 10.10"
date: 2010-11-26
forum: Installation &amp; Upgrades
---

### Post by macnomore on 2010-11-26
I recently reinstalled ubuntu 10.10 to clear it of junk(about 50% of my hard drive was used, and my hard drive is 80 GB- not very big!). Now when I try to update, this happens:
```
ubuntuzelda@ubuntuzelda-OptiPlex-GX260:~/Desktop/screensavers$ sudo apt-get update > text.txt
W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used. GPG error: http://extras.ubuntu.com maverick Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY DB141E2302FDF932

W: Failed to fetch http://extras.ubuntu.com/ubuntu/dists/maverick/Release  

W: Some index files failed to download, they have been ignored, or old ones used instead.

```Please note that I sent all the normal stuff that it spit out to a file to save what I copy for what really matters. I don't think it's that important.
The first time I reinstalled it, this happened, so I reinstalled it again and it happened again.
Anyway, I am an amateur, so I don't know how to fix this. Can anyone help?

Also, I am trying to download the code for the screen savers so that I can hack them and make my own. Here's what it spits out(again, all standard output goes to a text file):
```
ubuntuzelda@ubuntuzelda-OptiPlex-GX260:~/Desktop/screensavers$ apt-get source xscreensaver xscreensaver-data xscreensaver-data-extra xscreensaver-gl xscreensaver-gl-extra xscreensaver-screensaver-bsod xscreensaver-screensaver-webcollage >out.txt
E: Could not open file /var/lib/apt/lists/extras.ubuntu.com_ubuntu_dists_maverick_main_source_Sources - open (2: No such file or directory)

```Is this meant to happen? I was able to get the source before I reinstalled ubuntu 10.10... What should I do to get /var/lib/apt/lists/extras.ubuntu.com_ubuntu_dists_maverick_main_sources_Sources ?   I just reinstalled yesterday, so I don't have much installed.

---

### Post by plucky on 2010-11-26
> Now when I try to update, this happens:
Code:

ubuntuzelda@ubuntuzelda-OptiPlex-GX260:~/Desktop/screensavers$ sudo apt-get update > text.txt
W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used. GPG error: [http://extras.ubuntu.com](http://extras.ubuntu.com) maverick Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY DB141E2302FDF932

W: Failed to fetch [http://extras.ubuntu.com/ubuntu/dists/maverick/Release](http://extras.ubuntu.com/ubuntu/dists/maverick/Release)  

W: Some index files failed to download, they have been ignored, or old ones used instead.




See [color=red][Link](http://ubuntuforums.org/showpost.php?p=10162674&postcount=2)[/color]
```

E: Could not open file /var/lib/apt/lists/extras.ubuntu.com_ubuntu_dists_maverick_main_source_Sources - open (2: No such file or directory)
```

Probably because of the first error.
See if it now works after you have installed the GPG key for the extras repo.
Good Luck

---

### Post by kcode on 2010-11-26
I am having the same problem, and got this on following the link:```
$ gpg --keyserver keyserver.ubuntu.com --recv 02FDF932
gpg: requesting key 02FDF932 from hkp server keyserver.ubuntu.com
?: keyserver.ubuntu.com: Host not found
gpgkeys: HTTP fetch error 7: couldn't connect: No such file or directory
gpg: no valid OpenPGP data found.                                                            
gpg: Total number processed: 0                                                               

```Computer is successfully connected to the internet.

---

### Post by plucky on 2010-11-26
> **kcode said:**
> I am having the same problem, and got this on following the link:```
$ gpg --keyserver keyserver.ubuntu.com --recv 02FDF932
gpg: requesting key 02FDF932 from hkp server keyserver.ubuntu.com
?: keyserver.ubuntu.com: Host not found
gpgkeys: HTTP fetch error 7: couldn't connect: No such file or directory
gpg: no valid OpenPGP data found.                                                            
gpg: Total number processed: 0                                                               

```Computer is successfully connected to the internet.

Can you ping the keyserver ```
ping keyserver.ubuntu.com
```

This is what I got ```
$ ping keyserver.ubuntu.com
PING keyserver.ubuntu.com (91.189.89.49) 56(84) bytes of data.
64 bytes from boquila.canonical.com (91.189.89.49): icmp_seq=1 ttl=55 time=37.9 ms
64 bytes from boquila.canonical.com (91.189.89.49): icmp_seq=2 ttl=55 time=39.3 ms
64 bytes from boquila.canonical.com (91.189.89.49): icmp_seq=3 ttl=55 time=40.7 ms

```

Also the command worked for me ```
$ gpg --keyserver keyserver.ubuntu.com --recv 02FDF932
gpg: requesting key 02FDF932 from hkp server keyserver.ubuntu.com
gpg: key 02FDF932: "Launchpad Application Review Board PPA" not changed
gpg: Total number processed: 1
gpg:              unchanged: 1

```

Are you using a proxy or are ports blocked by a firewall?

---

