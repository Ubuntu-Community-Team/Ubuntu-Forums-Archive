---
title: "Dual boot XP Pro &amp; Ubuntu 7.04"
date: 2007-04-16
forum: Installation &amp; Upgrades
---

### Post by dan7723 on 2007-04-16
**Goal:**

My goal is to dual boot Windows XP Professional and Ubuntu 7.04 on my machine on one hard drive.

**Problem:**

(FAILURE) - to even boot Ubuntu 6.10 Live CD
(FAILURE) - to even boot Ubuntu 7.04 BETA Live CD
(SUCCESS) - booting Ubuntu 6.06 LTS Live CD 

**Ubuntu 6.06 LTS**

This is the only version that I've been able to boot from Live CD and install successfully to dual boot.

**Specs of my machine:**

Dell Dimension 9150
Intel Pentium D @ 2.8GHz
1 GB RAM
250 GB Western Digital HD
CD-RW
DVD-RW
Nividia GeForce 7300 LE
SB Audigy 2 ZS

**Questions:**

Am I missing something here and did I leave something out?
Is this just a bad system configuration?
Anyone here with a Dell Dimension 9150 similar to mine that can help?

---

### Post by loserboy on 2007-04-16
might be your video card, where does the edgy livecd hang at

---

### Post by dan7723 on 2007-04-16
> **loserboy said:**
> might be your video card, where does the edgy livecd hang at

6.10 will show the Ubuntu splash screen and it will act like it's loading up, then the screen blanks with just the curser at the top of the screen. It hangs there.

7.04 hangs right after the boot menu!

---

### Post by loserboy on 2007-04-16
[https://wiki.ubuntu.com/EdgyKnownIssues](https://wiki.ubuntu.com/EdgyKnownIssues)

#59618 under installation.

thats what I had to do for my nvidia 7800, could be the same issue i dunno,but for some reason i was able to get into dapper by just starting in safe mode, but in edgy I had to use this workaround.

something to do with safe mode not using vesa, it's worth a shot.

---

### Post by loserboy on 2007-04-16
oh also did you try the alternate livecd, I hear that has a pretty high success rate

---

