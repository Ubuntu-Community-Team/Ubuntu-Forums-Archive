---
title: "Netbook will only boot into grub rescue prompt after installing Kubuntu Netbook"
date: 2010-03-28
forum: Installation &amp; Upgrades
---

### Post by razed1 on 2010-03-28
_NOTE: I've posted this exact thread over at the Kubuntu forums [here]("http://kubuntuforums.net/forums/index.php?topic=3110753.0"). I don't know how connected this forum is with that one (if at all), so I apologize profusely in advance if this is viewed as redundant._

I have an Asus Eeepc 1000he that dual boots Windows XP and Ubuntu Netbook Remix. I wanted to try out Kubuntu Netbook, so I installed it to an 8 gig SD-card. After installation, it reboots to this screen:

GRUB loading.
error: no such disk
grub rescue> 

Most of the solutions I've found via google and forum searching have suggested that the live-cd installed grub2 over the mbr (or something to that effect). I've read that a few grub-rescue commands can work the problem out, but most of the suggested commands don't seem to work for me. The only two that do work are ls and set.

ls reveals this: "(hd0) (hd0,4) (hd0,3) (hd0,2) (hd0, 1)"
set reveals: 
"prefix=(UUID=95fea94d-bf5e-49b0-ad92-af178a8c2a89)/boot/grub
root=UUID=95fea94d-bf5e-49b0-ad92-af178a8c2a89"

Typing "ls (hd0)" or "ls (hd0,4)" and so on just says "error: no such disk." Typing "ls UUID=95fea94d-bf5e-49b0-ad92-af178a8c2a89" or "ls (UUID=95fea94d-bf5e-49b0-ad92-af178a8c2a89)/boot/grub" says the same.

It also seems that I have a "insmod" command, although I have no idea what it does. Can you tell I have no idea what I'm doing? [IMG]http://kubuntuforums.net/forums/Smileys/classic/smiley.gif[/IMG]

The strange thing (to me, anyway) is that I can't get into my bios settings or boot from the live-cd (or any other media). The computer seemingly forgoes the normal loading order and skips the bios entirely. Holding down or pressing F2, F8, F12, or Shift doesn't affect the boot in any way. I can't find a way to get help or list commands in the grub rescue prompt, either.

Please help! As it stands now, my netbook is completely useless! I can't even reinstall Windows at this rate  [IMG]http://kubuntuforums.net/forums/Smileys/classic/cry.gif[/IMG]

---

### Post by stlsaint on 2010-03-28
Im pretty sure that unless specified otherwise...the installer will install grub to the master hdd set by bios..which would be the one inside the computer. So you would need to specify the in the last step before installing where to install grub to. I also suggest using the ubuntu EEEpc version for netbooks. Or perhapds [UNR]("http://www.ubuntu.com/getubuntu/download-netbook").

---

### Post by razed1 on 2010-03-28
Well, I'm already using Ubuntu Netbook Remix. I just wanted to try out the Kubuntu Netbook edition. In any case, I'm not able to install any operating systems at all, because as I stated, I can't boot from disk, USB, or another SD card. It loads up into the grub rescue prompt no matter what I do. Any suggestions as to how to get through this prompt?

---

### Post by razed1 on 2010-03-28
I realize now that my problem was not going into the advanced options and telling grub to make a complete install on the SD card instead of trying to install over the MBR (or whatever it did). Sucks, but I still haven't found a way to fix it. None of the partitions listed by ls are known filesystems that I can browse. :(

---

### Post by razed1 on 2010-03-30
Ok, I realize I'm making a triple post, but I've solved the issue and wanted to possibly help anyone with similar troubles who stumbles upon this thread.

I have no idea why, but upon booting the netbook, holding down F2, F8, F10, AND F12 (yes, all four), let me get into my BIOS settings, where I could set it to boot from disk. I then used Super Grub Disk to fix my MBR.

It wouldn't work with any of those keys individually; It wouldn't work with any combination of those keys; It wouldn't work just pressing them simultaneously and letting them go. I don't know why it had to be all four, held down, but I tried it multiple times just to make sure, and each time only holding down all four until the BIOS settings popped up worked. Maybe it's a feature unique to the Eeepc? I'm not sure, as I bought it used without a manual.

Anyways, that's how I fixed it: hold F2 + F8 + F10 + F12 to get into the BIOS, then fixing the MBR via Super Grub Disk.

---

### Post by vtC on 2011-02-22
Now I only registered myself here, to say I LOVE YOU!

you really helped me out of my **** "grub rescue" Problem. I had no bios entry and no boot option to choose. 
but this F2 + F8 + F10 + F12 was the solution.....really, THANKS!!!!!

---

