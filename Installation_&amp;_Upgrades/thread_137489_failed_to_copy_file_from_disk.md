---
title: "failed to copy file from disk"
date: 2006-02-28
forum: Installation &amp; Upgrades
---

### Post by altern on 2006-02-28
hi

I tried few different installation cds (Kubuntu, ubuntu and even a debian). I get the same error in all of them after the cdrom detection. 
"failed to copy file from disk. retry?"
I believe this can be because i am running it from a DVD-R i installed recently when my cdrom died. It is a Benq DW 1620 Pro.

I have searched for help but everyone says I should check the integrity of the cd, however this cannot be the case as i used few different distros and cds. A couple of them were the original ubuntu cds sent by cannonical.

any ideas?

thanks

---

### Post by swamytk on 2006-02-28
Hi,

I too faced this issue for long time. Recently I came to understand that DMA is disabled for IDE devices by default in Ubuntu distributions (Any one??? Pl. correct me if I am wrong). My Samsung DVD-R device was not able to read Ubuntu CDs (sent by canonical also). You have to enable DMA to solve this issue. 

Here is how to enable DMA while installing Ubuntu:
1. Choose "expert" install at boot prompt of boot cd
2. Select default values for prompts if you don't want to fiddle with them.
3. In "tune drive parameters" screen type '-d 1 /dev/hdc'. This is to enable DMA on CD-Drive (hdc - sec.master in this example. You select your conf.)
4. Then proceed as usual with installation.

The above setting is for installation time setup only. For day to day operation with DMA support, follow the link below which gives exact picture.
[https://wiki.ubuntu.com/DMA](https://wiki.ubuntu.com/DMA)

All the best!

---

### Post by altern on 2006-02-28
great. it works
but it is not nice to do the expert install. Loads of questions, I just keep choosing the defaults but it always feels like something is going to go wrong.
As a comment i think it would be much nicer if something like this could be passed to the installer as a parameter not having to go through the whole expert install.
many thanks!

---

