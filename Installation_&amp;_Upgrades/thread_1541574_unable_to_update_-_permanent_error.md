---
title: "unable to update - permanent error"
date: 2010-07-29
forum: Installation &amp; Upgrades
---

### Post by abelito8 on 2010-07-29
Good evening, 

I am using Xubuntu 10.4 on a AAO 11.6 (160 GB) and it's been a month that I cannot update my system
if I type in 
sudo apt-get update 

the system will download the packages but then display the message

GPG error: [http://deb.torproject.org](http://deb.torproject.org) karmic Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 74A941BA219EC810

any help?

thank you

---

### Post by moonport on 2010-07-29
Try to update your sources list:
system>sdministration>software sources app.

In some cases, works after that.

---

### Post by abelito8 on 2010-07-29
Thank you, I have tried and even updating software sources gives the same message...

---

### Post by arpanaut on 2010-07-29
> **abelito8 said:**
> 

GPG error: [http://deb.torproject.org](http://deb.torproject.org) karmic Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 74A941BA219EC810



You are going to need to edit your sources to show 'lucid Release" instead of karmic, then go to the torproject site and acquire the public key, I am sure there are instructions on their site for doing this.

HTH

---

### Post by abelito8 on 2010-07-31
Ah, now I understand, I tried to install TOR and since ever I have an error...but now I cannot remember how to open the sources through the terminal...

---

### Post by abelito8 on 2010-07-31
sorry I just found the link again, now everything works, thanks

---

