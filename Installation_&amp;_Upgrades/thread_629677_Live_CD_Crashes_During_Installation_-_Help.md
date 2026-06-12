---
title: "Live CD Crashes During Installation - Help"
date: 2007-12-02
forum: Installation &amp; Upgrades
---

### Post by andrew.pope on 2007-12-02
I downloaded the Ubuntu 7.10 Desktop ISO Image and burned it to a blank DVD-RW with DVD-Decrypter. I then booted the disk and selected the start ubuntu in safe graphics mode as i keep getting "Input Not Supported" if i use the normal option, no matter which resolution i select.

After about 2-3 mins the dekstop loads. and then i double click on the Install icon. It takes about 2-3 mins to load again. I guess the slowness is because i only have 256MB of RAM for the Ubuntu Live CD to play with. 

I slowly but surely work my way through steps 1-7.

>I:
   > Select English as Language
   > Select London As Timezone
   > Select United Kingdom as Keyboard Layout
   > Choose to use my entire 7.85GB volume to install ubuntu on and leave my 20GB xp harddrive alone.
   > Choose not to Not Migrate the account from XP
   > Create A User account with a password
   > Check my Settings

After checking everythings ok i start the install. It stopped at 15% which was something like "Setting Up Partitions" i gathered it was probably starting to be slow again so i went to bed and left the PC on (it was 2 AM at this point). When i woke up i eagerly went to the PC and found it was still stuck on the 15% screen and the mouse wouldn't move and the CAPS LOCK button wouldn't work (my tests for a crashed computer).

I booted into windows to post a message on here and noticed that my second hard drive was no longer in my computer. So i started up computer management and found that my drive that i chose to put ubuntu on had a 7.49GB healthy FAT32 partition and there was a 384MB unknown healthy partition. So the installer must have only done 384MB before it crashed.

I tried installing ubuntu again and the same thing happened, it crashed at 15%. After this, I decided to seek help from all of you ubuntu experts out there!

Can anyone tell me a possible reason for the installer crashing - it happened twice so it wasn't a one off thing. And what I can do to fix it? Any information would be greatly appreciated!

thanks in advance,

andy

---

### Post by merlinus on 2007-12-02
IIRC, 256MB RAM is not enough to both run the live cd and then install from it.

Try the text-based alternate cd, which is all I ever use.

---

