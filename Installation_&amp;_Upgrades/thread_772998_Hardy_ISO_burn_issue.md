---
title: "Hardy ISO burn issue"
date: 2008-04-28
forum: Installation &amp; Upgrades
---

### Post by attercop on 2008-04-28
I've downloaded the 8.04 iso and can't get it to burn to CD at all. I have checked the md5sum and it's just as it should be. I first burned it using my Ubuntu 7.10 and simply right clicking the iso etc. That CD was not recognised as any type of bootable media and startup went straight to GRUB. 

I've checked in the BIOS and CD is #1 bootup, with HDD #2. I installed k3b and tried burning the same iso again. It again burned but k3b stopped responding at 50% when it was about to check the burn for errors. On reboot it did the same as the previous CD.

I booted into WinXP and using Nero tried to burn it again, but was not able, receiving a 'Write Error' each time.

What's going on?

---

### Post by Pumalite on 2008-04-28
Follow this guide:
[https://help.ubuntu.com/community/BurningIsoHowto?highlight=%28burn%29%7C%28](https://help.ubuntu.com/community/BurningIsoHowto?highlight=%28burn%29%7C%28)
Burn as 'image' not as 'data', at 4x or less. You cannot do it with Nero. Download ImgBurn: [http://www.imgburn.com/index.php?act=download](http://www.imgburn.com/index.php?act=download)
Install. Go to Mode>ISO>Burn. Set speed at 1x or 4x

---

### Post by attercop on 2008-04-28
I have already followed the burn ISO image how-to and md5sum verify how-to guides. I installed ImgBurn and followed your instructions and that burn failed also (at 1x speed). I now have 3 identical coasters from three different burning programs.

I should add that i've burned many Linux CDs from ISO in the past, so it's not like i'm new to this. Is it possible that the ISO file is corrupt despite displaying the correct md5sum?

---

### Post by Pumalite on 2008-04-28
Maybe the culprit is your burner. clean the lens. Check CD integrity before install. Try your CD's in a different computer.

---

### Post by attercop on 2008-04-29
I burned the ISO image file onto a DVD-RW so i could chuck it onto another PC to burn it onto CD. It burned the DVD-RW without a problem, and it's been burning music CDs without issue recently. However when using the other CD burner on another PC to burn the 8.04 ISO it burned fine first time without defects. So it is indeed my burner having an issue.

Strange that it burns DVDs and music CDs fine but is struggling to burn an ISO image though. How does one clean the lens?

---

### Post by Pumalite on 2008-04-29
There are disks that you can buy in a Computer Supply Store that clean the lens. I you are more techie inclined you can just take it apart  and use compressed air.

---

### Post by juje on 2008-04-30
ok, i have a question about the live cd...im using happily using gusty and try to load the liveCD but fail to do it...i check the cd inegrity with md5 checksum and it's ok...i also try to load the gparted live cd and that one load quite good....any clue why only the hardy live cd not working? tahnks!

---

### Post by Pumalite on 2008-04-30
Post your specs.

---

### Post by juje on 2008-05-02
ok, thanks everyone..i gave another shot to brasero and burn one new livecd (from other source) and it seems to work fine...

---

