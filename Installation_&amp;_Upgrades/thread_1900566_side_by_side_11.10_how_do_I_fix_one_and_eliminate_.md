---
title: "side by side 11.10 how do I fix one and eliminate the other?"
date: 2011-12-26
forum: Installation &amp; Upgrades
---

### Post by smcrossman on 2011-12-26
I need a little input.  My main pc (desktop running 64 bit 11.10 with many Kubuntu features and NVIDIA) started giving me the "out of range" message when I would boot up. No biggie....needed to reset the resolution but I didn't have time to get around to it. Then I started getting errors about inability to mount CD/DVD drive.  Well I have been trying to add NFS to my system so had been into fstab and automount, etc....again...I figured I would get to it soon, but....

Well yesterday BEFORE I addressed the above issues I uninstalled PLASMA features. The desktop keeps crashing and without it I can make the layout more similar between my different machines.  It would boot but never load a desktop....or if I could get a desktop it was unresponsive.  Then it started refusing to boot because of the fatal error with the CD/DVD drive.  So like a dunce I went in and took my old fstab orig, cp'd it to fstab....error....thought okay...file exists I'm in recovery lets try removing the fstab file then copying.....WRONG!  I can delete but not write.

[COLOR=Green]NOW will not boot because there is no fstab file/directory......DUH....obvious enough to me....[/COLOR]

I promptly downloaded and made a live usb to repair the issue. Only when I went to do it I couldn't figure out which option I was supposed to use so I installed 11.10 beside 11.10.  I really just want to FIX the first version by replacing the fstab, and then I can use the second install and try out server or some of the other versions.  But when I open the partition in File Manager all I get is the lost & found file.

[COLOR=SeaGreen]I now have a large hard drive half taken by an install of 11.10 that will not run, 1/4 taken by extension. The remaining 1/4 is 2/3 new install & 1/3 SWAP. [/COLOR] None of my customizations, software which required compiling, alterations to accommodate my network storage system, etc, etc.  I do have my files and my emails and such which is GREAT, but....

[B][COLOR=Red]What do I do to access the root drive of the first install so I can repair it and then how do I get IT to boot up not the new one? 
[/COLOR]
 [/B]I probably can work the second one out....I know I've done a lot of altering and such to the startup menu because of the NVIDIA....I'm just running on 8 hours sleep in 4 days so I've hit my wall.

Just when I start making progress I crash the whole system....UGH!

---

### Post by darkod on 2011-12-26
So, if I understand correctly, you can't see any files on the root partition of the main 11.10?

---

### Post by smcrossman on 2011-12-26
> **darkod said:**
> So, if I understand correctly, you can't see any files on the root partition of the main 11.10?


Correct.  Seems odd but that''s what I've got.

---

