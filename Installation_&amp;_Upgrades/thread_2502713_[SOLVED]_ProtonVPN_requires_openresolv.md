---
title: "[SOLVED] ProtonVPN requires openresolv"
date: 2024-11-26
forum: Installation &amp; Upgrades
---

### Post by xendistar2 on 2024-11-26
I have just moved to Xubuntu and I am trying to install ProtonVPN but it is asking me to install "openresolv (an open-source implementation of [resolvconf]("https://en.wikipedia.org/wiki/Resolvconf"))"

Checked Synaptic but it is not showing as available, is it part of the different package??

Can anybody advise

ISSUED SOLVED Found another page on the Proton web site, that I could not find in my earlier search, this allowed me to download the required software, which is now installed and the VPN is working.

---

### Post by Norm24 on 2024-11-26
I'm going to make the assumption you're using 24.04 or 24.10?And are you trying to install Proton through Synaptic?

Openresolv is available in the repos for both Focal(20.04) and Jammy(22.04) but not for Noble(24.04).It can be had as a tarball on github and is available as .deb download for Debian.

I installed Proton directly from their site yesterday on the computer I'm using right now which is running Mate 24.04 and there was no issue.

---

### Post by xendistar2 on 2024-11-26
Thanks Norm, yeah new install of 24.04, when I looked all I could find was the manual install, when I looked again later I found the download and install instructions with all the commands to enter. Not sure why I could not find it  earlier but at least now it is working.

---

### Post by Norm24 on 2024-11-27
> **xendistar2 said:**
> Thanks Norm, yeah new install of 24.04, when I looked all I could find was the manual install, when I looked again later I found the download and install instructions with all the commands to enter. Not sure why I could not find it  earlier but at least now it is working.

I had to do a little looking myself before I found the install instructions.

---

