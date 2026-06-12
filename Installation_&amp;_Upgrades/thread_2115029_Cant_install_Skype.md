---
title: "Cant install Skype"
date: 2013-02-11
forum: Installation &amp; Upgrades
---

### Post by Dan M on 2013-02-11
Hi, I have a laptop with windows 7 installed and ubuntu (64 bit). Skype is installed on windows and I would like to install on to Ubuntu but get the following message.

Package dependencies cannot be resolved

This error could be caused by required additional software packages which are missing or not installable. Furthermore there could be a conflict between software packages which are not allowed to be installed at the same time.

Can you help?

---

### Post by ahallubuntu on 2013-02-11
~

---

### Post by Dan M on 2013-02-11
12.04 64 bit, i have been trying to install via the Ubuntu Software Center, but will try the link you suggested.

Many Thanks

---

### Post by Dan M on 2013-02-11
still no joy, i get the following message

i386, wrong architecture

---

### Post by ahallubuntu on 2013-02-11
~

---

### Post by Dan M on 2013-02-11
> **ahallubuntu said:**
> You downloaded "Ubuntu 12.04 (multiarch)" from that page?  That's what worked for me on Ubuntu 12.04 64 bit - at least, to install it without error.
Yes I downloaded that version, then opened in the software center and got that message, does your machine have a windows version installed on the same machine.

---

### Post by xc3RnbFO8P on 2013-02-11
Try to install Skype with Gdebi (in software center)

---

### Post by ahallubuntu on 2013-02-11
~

---

### Post by Dan M on 2013-02-11
> **ahallubuntu said:**
> I do have Windows 7 on the same machine as a dual boot.  Not sure I have Skype installed in Windows, though.  

All I can say is: I installed Skype twice using the link above without doing anything special.  Of course, that was more than a month ago; perhaps Microsoft has updated the download since then and if I tried it now it would no longer work.
More than likely, no probs I will keep plugging away, thanks anyway for your help.

---

### Post by Dan M on 2013-02-14
> **Ringi said:**
> Try to install Skype with Gdebi (in software center)
have tried Gdebi and get the following error message ''i386, wrong architecture''

---

### Post by xc3RnbFO8P on 2013-02-14
Try:
> sudo apt-get install -f
and
> sudo apt-get update

---

### Post by Dan M on 2013-02-14
> **Ringi said:**
> Try:

and

This is what happened

Fetched 1,045 kB in 4s (223 kB/s)
W: Failed to fetch http://archive.canonical.com/dists/$(lsb_release/-sc)/source/Sources  404  Not Found [IP:4444444444444]

W: Failed to fetch http://archive.canonical.com/dists/$(lsb_release/partner/source/Sources  404  Not Found [IP:44444444444]

W: Failed to fetch http://archive.canonical.com/dists/$(lsb_release/-sc)/binary-amd64/Packages  404  Not Found [IP:]

W: Failed to fetch http://archive.canonical.com/dists/$(lsb_release/partner/binary-amd64/Packages  404  Not Found [I]

E: Some index files failed to download. They have been ignored, or old ones used instead.

---

### Post by xc3RnbFO8P on 2013-02-14
Try to change download server in Software Source (update manager)

---

