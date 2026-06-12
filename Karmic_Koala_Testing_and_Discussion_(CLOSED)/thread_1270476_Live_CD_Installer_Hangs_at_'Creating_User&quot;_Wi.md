---
title: "Live CD Installer Hangs at 'Creating User&quot; With Encrypted /home"
date: 2009-09-19
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by novafluxx on 2009-09-19
I've recently tried installing Alpha 6 the past couple days, clean install, formatting the old partitions. In the LiveCD, it hung around 83% for over 10 minutes and never progressed, with my HDD activity light on the entire time.

I had issues with the alternate install CD as well, but do not recall enough detail to make it worth while to post about.

I'm not sure if it has to do with this bug: [https://bugs.launchpad.net/bugs/430496](https://bugs.launchpad.net/bugs/430496)

Anyone else experiencing this issue or something like it?

Once 9.10 comes out I'd very much like to use an encrypted /home or whole-disk encryption.

---

### Post by andrewabc on 2009-09-19
Dunno about the problem, but thought I'd link to benchmarks comparing encrypted vs non encrypted.

[Ubuntu 9.10 Home Encryption Performance](http://www.phoronix.com/scan.php?page=article&item=ubuntu_910_encryption&num=1)
You're looking at a significant drop in performance.

I am very interested in encrypting /home as well. Hope the bugs are sorted out.

---

### Post by novafluxx on 2009-09-19
Thank you for the fast reply and the link to benchmarks. I'll check them out.

---

### Post by gnomeuser on 2009-09-19
It doesn't actually hang, it just sits there for an unreasonable amount of time. Wait and thee shall recieve. I am typing this from my 9.10 netbook remix with encrypted home+swap installed from Alpha6.

---

### Post by novafluxx on 2009-09-19
I sat there for what I consider to be reasonable. We're talking 10+ minutes at that point without the progress bar moving or the 83% changing. I'm not waiting 2 hours to install an OS.

I understand this IS an Alpha release, and I was just wondering if anyone else had experienced it.:guitar:

---

### Post by novafluxx on 2009-09-19
> **andrewabc said:**
> Dunno about the problem, but thought I'd link to benchmarks comparing encrypted vs non encrypted.

[Ubuntu 9.10 Home Encryption Performance](http://www.phoronix.com/scan.php?page=article&item=ubuntu_910_encryption&num=1)
You're looking at a significant drop in performance.

I am very interested in encrypting /home as well. Hope the bugs are sorted out.

WOW! Amazingly degraded performance! I had no idea the encrypted /home and SWAP were such a hit to performance.

Luckily, I don't use this system for anything performance intensive. Its for testing, mobile communications, etc. Thats why I'm always installing Alpha versions!:P

---

### Post by andrewabc on 2009-09-19
> **novafluxx said:**
> I sat there for what I consider to be reasonable. We're talking 10+ minutes at that point without the progress bar moving or the 83% changing. I'm not waiting 2 hours to install an OS.

I understand this IS an Alpha release, and I was just wondering if anyone else had experienced it.:guitar:

That could be the part where it checks server for new packages? Unless it is encrypted specific.


> **novafluxx said:**
> WOW! Amazingly degraded performance! I had no idea the encrypted /home and SWAP were such a hit to performance.

Luckily, I don't use this system for anything performance intensive. Its for testing, mobile communications, etc. Thats why I'm always installing Alpha versions!:P

Yah it depends if speed or security is more important. I would think if you have a netbook and taking with you places, might be a good idea to encrypt and that way no one will see your stuff if lost or stolen. Might still be fast enough for basic web browsing etc. You'd have to try with and without and see if you notice :)
Although according to read/write benchmarks, it should be noticeable.

---

### Post by novafluxx on 2009-09-19
> **andrewabc said:**
> Yah it depends if speed or security is more important. I would think if you have a netbook and taking with you places, might be a good idea to encrypt and that way no one will see your stuff if lost or stolen. Might still be fast enough for basic web browsing etc. You'd have to try with and without and see if you notice :)
Although according to read/write benchmarks, it should be noticeable.

I only use the notebook for testing Ubuntu really, when a stable comes out I fresh install the stable until Alpha 4-6 are released :-)

It has almost no personal data on it, I just wanna use encryption, cause thats my thing \\:D/

I don't have OOB wireless like I did in 8.10 and 9.04, I actually had to install the Broadcom drivers off the Live CD after first boot...not sure why this is but its just yet another extra step required...another issue I know :-)

---

### Post by novafluxx on 2009-09-19
What type of encryption does it actually do for the /home directory? AES-256? Blowfish? Where can I find the details on that?

---

### Post by andrewabc on 2009-09-19
> **novafluxx said:**
> 
I don't have OOB wireless like I did in 8.10 and 9.04, I actually had to install the Broadcom drivers off the Live CD after first boot...not sure why this is but its just yet another extra step required...another issue I know :-)

Hmm, maybe if you had connected to your wireless network before installing ubuntu it would have already been installed and remembered it?

---

### Post by novafluxx on 2009-09-19
> **andrewabc said:**
> Hmm, maybe if you had connected to your wireless network before installing ubuntu it would have already been installed and remembered it?

Never had to do that in 8.10 or 9.04 even in the pre-release Alpha's I used. Its okay, I've figured out how to get it all working now.

---

### Post by mikko.rantalainen on 2009-10-09
> **novafluxx said:**
> I've recently tried installing Alpha 6 the past couple days, clean install, formatting the old partitions. In the LiveCD, it hung around 83% for over 10 minutes and never progressed, with my HDD activity light on the entire time.
[...]
Once 9.10 comes out I'd very much like to use an encrypted /home or whole-disk encryption.

I experienced this, too. I believe it's related to encrypted home and its friend, encrypted swap. I run "top" in the terminal and figured out that behind the scenes, dd was used to overwrite ALL swap devices from /dev/null. As I had two 4 GB swap partitions (on two separate disks), the process took quite a while.

The only problem I can see is that below the progress bar the installer said "Creating user...". It should have said "Initializing encrypted swap."

---

### Post by mikko.ohtamaa on 2009-10-10
The correct bug report is here [https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/432422](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/432422)

---

