---
title: "Can't Boot From CD"
date: 2011-11-14
forum: Installation &amp; Upgrades
---

### Post by Jafador on 2011-11-14
So I downloaded Ubuntu, and burned it to my CD, and restarted my computer. Nothing happened and Windows came up again. I went into the bios and set CD drive to the number one priority, removed the priority to boot from the harddrive, and selected boot from disk. I got the error message Boot Failure: System Halted..

I am pretty sure I burned the CD right, I and only have 1 CD drive. I don't know why it won't boot.

Almost forgot, I am trying to install this on a dell 4400, but it has also failed on my dell 8400

---

### Post by Rubi1200 on 2011-11-15
Hi and welcome to the forums :)

Checklist:

1. check the md5sum:
[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

2. try burning another CD at the lowest speed:
[https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)

3. post the specifications for the computer

---

### Post by Miykel on 2011-11-15
G'Day, if you have Windows installed why not download Wubi, create an ubuntu partition and run Wubi, select the Ubuntu partition when the installer asks you where to install
 Regards Miykel

---

### Post by Rubi1200 on 2011-11-15
> **Miykel said:**
> G'Day, if you have Windows installed why not download Wubi, create an ubuntu partition and run Wubi, select the Ubuntu partition when the installer asks you where to install
 Regards Miykel

If you install with Wubi you do NOT create a separate Ubuntu partition.

Wubi installs within Windows and does not require the creation of a separate partition.

Read here for more:
[https://wiki.ubuntu.com/WubiGuide](https://wiki.ubuntu.com/WubiGuide)

---

### Post by Miykel on 2011-11-15
When you run the installer you have the option of installing it within Windows or selecting another partition, I multiple drives and have W7 partition on one drive and Ubuntu partition on second drive.
Miykel

---

### Post by nothingspecial on 2011-11-15
Rubi1200 is correct, you do not need to partition your hard drive to install Ubuntu using wubi.

> What is Wubi?

Wubi is an officially supported installer for Windows users that allows Ubuntu to be installed and uninstalled in a safe, easy way as with any other Windows application.

However, this thread is not about wubi so let us return to the question in hand.

---

### Post by Jafador on 2011-11-15
> **Rubi1200 said:**
> Hi and welcome to the forums :)

Checklist:

1. check the md5sum:
[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

2. try burning another CD at the lowest speed:
[https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)

3. post the specifications for the computer

1. Its fine
2. I don't really have another CD readily available right now, so it would be best if we could get this one to work.
3. Dell 4400, 1gig ram, 1.6Ghz processor, 20gig total memory. Not the best, but it meets requirements

---

### Post by Jafador on 2011-11-16
I tried booting on my dell 8400, which has like 3 Ghz processor, 250gig memory on the first hard drive, and 2 gig RAM. I just got the error "selected boot device not available - strike F1 to retry boot, F2 for setup utility. " I don't know why it won't boot.

---

### Post by Rubi1200 on 2011-11-16
I'm also not sure what is going on; let me ask some other users to add their comments and possible workarounds.

---

### Post by coffeecat on 2011-11-17
> **Jafador said:**
> I just got the error "selected boot device not available - strike F1 to retry boot, F2 for setup utility. "

That sounds like a BIOS error message. If the BIOS is set to boot from the CD drive, then that would indicate either a problem with the optical drive itself or a problem with the actual CD. 

Are you able to read data and audio CDs from within Windows from that drive? In your OP you said that it also failed in another Dell. What happened exactly? Did you get the same error? If you did, that might indicate a problem with the CD itself.

Other than that I can't think of anything else to suggest at the moment.

---

### Post by Jafador on 2011-11-18
> **coffeecat said:**
> That sounds like a BIOS error message. If the BIOS is set to boot from the CD drive, then that would indicate either a problem with the optical drive itself or a problem with the actual CD. 

Are you able to read data and audio CDs from within Windows from that drive? In your OP you said that it also failed in another Dell. What happened exactly? Did you get the same error? If you did, that might indicate a problem with the CD itself.

Other than that I can't think of anything else to suggest at the moment.

The first dell (the one I am trying to install on) gave the error message Boot Failure: System Halted, the second dell (just a test to see if it was a computer problem or something), gave the message Selected Boot Device not available. From within windows I can view the CD and it appears to be fine. It has the name Ubuntu... and has several files/directories. I have tried installing 3 different versions of ubuntu with the same result.

 I believe it could be the CD, because it is old, but that seems unusual. I was going to try a USB, but I don't think the computer can boot from a USB. I guess I will have to get another CD to see if it is a CD error of some sort.

---

### Post by dandnsmith on 2011-11-19
I commend to your attention a tool called IsoBuster (Win app) which can, amongst other things look at what's on a CD and decide whether it has the correct setup for booting. It won't quickly help with CD errors.

---

### Post by Jafador on 2011-11-19
> **dandnsmith said:**
> I commend to your attention a tool called IsoBuster (Win app) which can, amongst other things look at what's on a CD and decide whether it has the correct setup for booting. It won't quickly help with CD errors.

I used IsoBuster, and my CD appears to have the required Bootable disk section, so I ran a surface scan on the CD, and it passed. Then I ran a readable files scan. Many many files were found to be unreadable. I have tried burning the disk several times with different versions of ubuntu. Is it my disk, burning software (ISO Recorder), computer, or something else that makes them unreadable?

---

### Post by coffeecat on 2011-11-19
First check that the ISO is good by checking the md5sum with the link Rubi1200 posted in post #2. If that passes, then are you using just the one CD? If so, it sounds as though it is past its best and you need a replacement.

---

### Post by Jafador on 2011-11-19
> **coffeecat said:**
> First check that the ISO is good by checking the md5sum with the link Rubi1200 posted in post #2. If that passes, then are you using just the one CD? If so, it sounds as though it is past its best and you need a replacement.

As I said, the ISO md5 checks out. I agree it is likely the CD. I will get a new CD soon and see if that makes any difference. Thanks for the help.

---

### Post by Jafador on 2011-12-25
For all those who may encounter this problem in the future, it was the CD, and it took a while, but the CD I got a while ago works just fine now. Thanks for all your help everyone!

---

