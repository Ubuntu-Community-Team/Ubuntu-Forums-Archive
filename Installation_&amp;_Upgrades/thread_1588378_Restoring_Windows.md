---
title: "Restoring Windows"
date: 2010-10-04
forum: Installation &amp; Upgrades
---

### Post by Sompom on 2010-10-04
Awhile back I was planning to re-install my Windows, so I booted Ubuntu from a USB stick and copied all of the one hard disk to my second hard disk. I then formatted the first disk. When I went to re-install, the dumb windows couldn't seem to detect my hard disks. I tried looking for drivers, nothing. So I said, fine, I'll use Ubuntu then.:KS
Since I am a gamer, I first installed Wine and my favourite games. I then went to try and play multiplayer. For those of you who know Wine, you'll know that Punkbuster doesn't work and that many server are Punkbuster-enabled.
Just now I used the Windows Vista install disk and tried to repair the old install, which I have copied back on to the disk it was originally on. The repairer seems to think all is well, and it does detect that there is a Vista install, which it didn't before. How do I point GRUB to the boot files (if they're still there:confused:, I'm clueless about this) and which files do I point it to? Thank you for any help!
Note: I have two hard drives, 300GBs with one ntfs partition in slot one (the original Vista disk) and another in slot two with two partitons, one with Ubuntu, ext4 (I believe, whatever the default is) (100GB) and one sotrage, ntfs (about 350GBs)

---

### Post by andrewthomas on 2010-10-04
If your windows install is good, then a simple 

```
sudo update-grub
```

Should pick up your vista install.

---

### Post by Sompom on 2010-10-04
Alright! That was a good thought. It didn't pick up Vista though, it picked up where the restore disk left its mark (it the boot loader it's called Windows Vista (Restored) or something like that.) I selected that option and tried to boot. The backlight flickered and came back to the BIOS. Next I tried "Last known Configuration that worked" It didn't work. I then tried Safe Mode, and the loading stopped at Loaded driver \SystemRoot\system32\drivers\crcdisk.sys, whereupon it upped and went back to the BIOS. I tried then the driver logging, and it worked for whatever reason:)! I then waited for it to load, and rebooted to try again. It didn't work:(. I chose the logging option again, and this time saved the log. (Attached). It that driver possibly corrupted? I have another Windows machine I can pull it off of, but I haven't time just now. I will get back if that works.\
Note: I have to take just the first bit of the log, because it wont accept all 50kbs of it. I the rest is desired, I can attach it in chunks.

---

### Post by andrewthomas on 2010-10-04
Can you mount the windows partition in ubuntu?

You could then copy the files you need off the windows partition and then reinstall windows using the installer disk.

---

### Post by Mark Phelps on 2010-10-05
Unfortunately, MS doesn't seem to be able to produce a repair utility that works all of the time!

You have to run Startup Repair from the Vista disk three times before it actually repairs everything.  IF you only ran it once, it didn't do all the repairs needed -- which is why it probably didn't launch OK.

You could try running Startup Repair again -- three times -- to see if that fixes it.

You can also boot into command mode using the Vista disk and run the new repair app (bootrec.exe) twice, once using the parameter /fixmbr and a second time using the parameter /fixboot

Good Luck

---

### Post by Sompom on 2010-10-05
Great! It worked (twice, at least... That's better than so far!) Thanks Mark!
As an added bonus it seems to have choosen the install that I wanted it to choose! I had two set up, I was just going for one of the to work. More is better, right :P.
Anyway, thanks a bunch Mark and Andrew.

---

