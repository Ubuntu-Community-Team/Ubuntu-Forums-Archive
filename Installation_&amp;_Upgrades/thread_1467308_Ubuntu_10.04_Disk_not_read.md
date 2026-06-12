---
title: "Ubuntu 10.04 Disk not read"
date: 2010-04-30
forum: Installation &amp; Upgrades
---

### Post by oomar on 2010-04-30
This is really confusing me. 

So i downloaded the Ubuntu 10.04 Desktop Edition and burned it to a disk. Shut off my computer and restarted it, booting from the CD Drive. It couldn't find it. So I thought maybe there was an unrecorded write error so I burned it to a second disc. Well after burning it I noticed I can't even see the disc anymore. It doesn't seem to be recognized at all. That explains why it didn't boot from CD. But what I want to know is why on earth is it basically going invisible and not working?

hmmm? I've never had a problem with burning discs, especially Ubuntu stuff... So why...?

EDIT: Well I just booted up the CD on a different computer and it seems to be working fine...

So it appears that my computer simply has ceased to see bootable discs or maybe its just non-empty discs... Idk. 

If someone wants to bump this to a more appropriate section, please feel free.

I would still like anyone that has an idea to help me.

---

### Post by cariboo on 2010-04-30
What does dmesg say when you insert the cd ?

---

### Post by oomar on 2010-04-30
You're gunna have to be more specific. I ran dmesg and a lot of stuff came up. A ton. What are you thinking?

---

### Post by johanbove on 2010-05-04
I have similar issues with disc iso: the disc is unusable.

Downloaded the iso through Torrent from the official source and did a md5 checksum which came out ok.

Tried burning it with different tools: K3B, command line wodim. 

After three tries the disc finally burned normally, although K3B had troubles closing the verification of the disc properly.

Left the newly burned disc in the drive and rebooted the comp, hoping to see a nice "Live CD boot up" screen. *By the way, with 9.10 disc I have no issues whats over.*

But alas, the boot process got halted with the loading screen stuck on the ubuntu logo with the 5 dots, not animating and the scroll and num lock of my keyboard flashing. Tried this twice with the same result. Apparently the flashing means linux got stuck in a kernel panic. Not sure what's going on deeper down. Haven't been able to dig deeper there. Is there a way to check what goes on behind the "screens" at this boot time?

Tried to load the disc in a windows XP home computer, but it simply crashed the whole thing. WUBI didn't start. Had to close of the thing to be able to do anything after that.

Haven't been able start from the 10.04 CD since.

---

### Post by johanbove on 2010-05-08
The disc works fine now after burning it with Xfburn on the lowest speed, with speedburn off and in TAO mode.

---

