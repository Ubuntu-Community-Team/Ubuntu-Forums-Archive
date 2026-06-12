---
title: "Installing ubuntu on computer with RAID configuration?"
date: 2012-01-18
forum: Installation &amp; Upgrades
---

### Post by jaredbuck on 2012-01-18
Hi all.

I tried installing ubuntu on my new computer that has two hard drives set up in a RAID configuration.  I ran across some error messages (don't remember them now) and it basically failed to work. Are there any special steps i need to take to install ubuntu to dual boot it with windows 7 on a RAID setup like mine?

Help would be appreciated.

Jared

---

### Post by ronparent on 2012-01-19
A RAID on Windows 7 is what the Linux community likes to refer to as a 'fakeRAID'. The latest releases of Ubuntu generally handle these RAIDs fine with some stipulations. In many of the Win7 laptop environments three partitions on the RAID are already used! To install Ubuntu you need be able to create two new partitions. The installer cannot handle this because the typical bios based RAID drive allows only four primary partitions! The answer is simple - create an extended partition within a live cd session with which you can created as many secondary partition as you are likely to need. 

Although the matter is really simple, it necessitates learning enough about Ubuntu and using RAID drives to flumux the new user. Do you really want to go on?

---

