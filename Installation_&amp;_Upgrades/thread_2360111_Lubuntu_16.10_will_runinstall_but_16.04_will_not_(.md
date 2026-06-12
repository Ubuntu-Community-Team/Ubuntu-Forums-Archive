---
title: "Lubuntu 16.10 will run/install but 16.04 will not (Dell B110)"
date: 2017-05-01
forum: Installation &amp; Upgrades
---

### Post by pete5 on 2017-05-01
Dell Dimension B110 
Celeron D 325 2.53 GHz, 768MB DDR-400, Intel 865 chipset

Originally installed Lubuntu 16.10 32 bit. (Dual boot with XP) User had some problems. I decided to start from scratch and stick with LTS this time but found I could not either boot live or install 16.04, but 16.10 works.. 

To check the 16.04 DVD and the drive I copied the entire contents of the disk to a folder using XP, and I booted another (newer) computer live using the same disk.

Last message I can catch is something like   

*ERROR* Child device config size 27 is too small

then it ends up unresponsive with a blinking cursor on a black screen.

I tried another computer with a P4, 512M, Intel D865GV board and it did the same thing. Can boot to 16.10 but not 16.04.
 
I really want to use 16.04 LTS because I want it as simple as possible for a non-technical user (stable configuration for longest possible time, minimal updates, etc.) 

Further reading of tech posts led me to try F6 options nomodeset and this allowed me to boot . I understand this is a graphics driver related problem but I'm not sure what it means as far as installing vs. running live. Can I install 16.04 once I get live running with nomodeset option or do I have to do some special config to get 16.04 to boot once installed?

---

### Post by DuckHook on 2017-05-02
Hello pete5,

Please do not use unusual formatting in your posts except for emphasis, etc.

Have you hash-checked your image and the resulting DVD? Your issue may be as simple as a corrupted download. I've found it best to torrent for installation images since torrenting error-checks continuously.

---

### Post by pete5 on 2017-05-02
I cut and pasted the error message in to the post and the bbs software decided to change formatting then I just tried to change it all back to uniform.

---

### Post by DuckHook on 2017-05-02
> **pete5 said:**
> I cut and pasted the error message in to the post and the bbs software decidet to change formatting then I just tried to change it all back to uniform.No problem and nothing personal was meant. It's just that a plethora of differing formats on the forums would make everything very difficult to read.

---

