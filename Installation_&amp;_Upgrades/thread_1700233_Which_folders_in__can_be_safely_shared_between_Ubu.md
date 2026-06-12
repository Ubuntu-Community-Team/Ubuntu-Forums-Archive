---
title: "Which folders in / can be safely shared between Ubuntu, Kubuntu &amp; Mint?"
date: 2011-03-04
forum: Installation &amp; Upgrades
---

### Post by Peppr on 2011-03-04
Here's the tl;dr version: I'd like to be able to set up partitions on my hard drive so that if I boot into Ubuntu,  install a LAMP stack or something, then reboot into Kubuntu, the LAMP  stack (or whatever) is available.



BACKGROUND: I recently  found out that you can set up a partition on your hard drive for /home,  which would be unaffected by future installs and would preserve user  files. Additionally, you could install two separate OS' that each mount  the partition as /home so users' files would even be preserved across  different distros.

I'd like to set up a system where I have  multiple OS options when I boot. I'd like to be able to boot Ubuntu,  Kubuntu and Mint, and down the road maybe venture beyond Debian.

I  figure that there is a lot of overlap in code between Ubuntu, Kubuntu  and Mint. In order to preserve space, I'm wondering if there are any  other folders that can be put into partitions and shared across these  OS'. Here's what I'm 100% sure would work:

/home
/dev
/tmp

I'm  less sure about /bin, /sbin, /etc and /usr. I don't wan't /var to be in  its own partition because I'm concerned important log files could be  overwritten.


Anyone ever done anything like this?

---

