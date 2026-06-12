---
title: "LiveCD Installation not working"
date: 2006-08-27
forum: Installation &amp; Upgrades
---

### Post by ToGo123 on 2006-08-27
Hello there.

I just got the LiveCD (v 6.06) a few days ago.  I decide to install it on my desktop (Dell Dimension), but when I restart my computer, my CD drive would detect the CD, but would load Windows XP.  I tried on my notebook (Dell Inspiration), but it would do the same thing.  

Is there something I'm doing wrong?

---

### Post by confused57 on 2006-08-27
On my Dell, I have to press "F12" at bootup when the Dell logo appears...this will enable you to select to boot from the CD drive.  If F12 doesn't work, maybe it's F9.

---

### Post by jdr00ejr on 2006-08-28
On my Dell desktop I had to change the Boot Order in the BIOS to Boot from the CD.  (When booting up - at the Dell Logo...I just pressed each F# key quickly...cause I don't remember which one it is).  

The problem I am having is I can get the Install Program to start, but I get to step 2 of 6 where it wants to update the time, and it never finishes loading that step so that I can proceed.  I have 256mb of Ram...any ideas why it won't continue?

Thanks.

---

### Post by kshymkiw on 2006-08-28
Are you burning the CD or is this a CD that was shipped to you?

---

### Post by jdr00ejr on 2006-08-28
This is an Original Ubuntu 6.06LTS LiveCD.

---

### Post by confused57 on 2006-08-28
> **jdr00ejr said:**
> On my Dell desktop I had to change the Boot Order in the BIOS to Boot from the CD.  (When booting up - at the Dell Logo...I just pressed each F# key quickly...cause I don't remember which one it is).  

The problem I am having is I can get the Install Program to start, but I get to step 2 of 6 where it wants to update the time, and it never finishes loading that step so that I can proceed.  I have 256mb of Ram...any ideas why it won't continue?

Thanks.

You can try pressing Ctrl+C when it reaches the update time, this should skip the step.

---

### Post by CoMRaDe_X on 2006-08-28
I also have this problem. I go throught the F12 booting menu.  I choose Boot From CD-ROM Device.  I wait a couple of seconds it will say "strike F1 to retry or F2 to go to setup"

I did burn mine but at a very slow speed (8x) because i had heard of people's cds not working because they burned too fast.

help appreciated

-Comrade

---

### Post by cleentrax on 2006-08-28
A couple of things to check. First, if you burned the CD yourself (as opposed to ordering it from Ubuntu), make sure that you created the disk from the iso file (as opposed to merely copying it as a data file to the disk).

Second, make sure that you have enabled booting from CD-ROM in your BIOS. On my Dell, I can enter the BIOS by hitting Delete at startup.

---

### Post by confused57 on 2006-08-28
> **CoMRaDe_X said:**
> I also have this problem. I go throught the F12 booting menu.  I choose Boot From CD-ROM Device.  I wait a couple of seconds it will say "strike F1 to retry or F2 to go to setup"

I did burn mine but at a very slow speed (8x) because i had heard of people's cds not working because they burned too fast.

help appreciated

-Comrade

Did you burn the iso "as an image" as described here?:
[http://www.psychocats.net/ubuntu/iso.html](http://www.psychocats.net/ubuntu/iso.html)

---

### Post by jdr00ejr on 2006-08-28
> **confused57 said:**
> You can try pressing Ctrl+C when it reaches the update time, this should skip the step.

I'll give this a shot and see what happens...thanks for the info.

---

