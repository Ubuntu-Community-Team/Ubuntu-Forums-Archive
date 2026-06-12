---
title: "Fresh install of 9.10 but still see old settings"
date: 2009-12-22
forum: Installation &amp; Upgrades
---

### Post by UDon on 2009-12-22
Hi, newbie here.

I upgraded from Ubuntu 9.4 to 9.10, but had a few minor issues. I read someone suggest that a fresh install might be better, and might resolve the minor problems. Since I had a Windows partition that I wanted to wipe, I thought I'd do a fresh install of 9.10. So I created a 9.10 boot disk, backed up all critical files on USB key, and did a fresh install. All went without problems

The Windows partition looks like it is wiped according to disk manager. However, I still see it in Grub, and more importantly it looks like all my old settings from the previous 9.10 are still active. I tried a second time, and it happened again. 9.10 installed perfectly, but I see my old files, screen-saver, etc, just as I had them from the last release. But I want a fresh virgin 9.10 installation!

How can I do a real fresh install of 9.10, so that NONE of my previous settings are kept?

---

### Post by darkod on 2009-12-22
If you do not intend to dual boot with windows, are you using the Erase and use whole disk option when installing ubuntu?
Or you are using the same / partition?

---

### Post by UDon on 2009-12-22
Hi, I don't remember seeing an "Erase" or "Use whole disk" option when doing the install, but that sounds like the kind of thing I would need to select. Thanks for the tip -- I'll look into that a little more on google, to find how to set those options, and then try to do another install. I'll post the result here.

---

### Post by darkod on 2009-12-22
It's not the selected option in this screenshot, but do you see it?

---

### Post by UDon on 2009-12-23
Hi darkod, in fact I was using the "Erase and use whole disk" option, and still all my old settings, including desktop items, tray items, etc were popping up.

But after spending two days swearing at my PC (an important part of the fix!) I finally worked out what the problem was.

Even though I'd read about potential problems with having two hard disks, I didn't really twig on how this was causing the problem until earlier today. The primary hard-drive was being erased, so I (eventually) worked out that my desktop settings had to be on the secondary one. So I erased that. That was good, my desktop settings had disappeared, but now my Grub had gone as well, and I couldn't boot in!

No problem, because Ubuntu automatically installs Grub in fresh installs. So it was just a matter of doing that... but it didn't work. I couldn't boot into my new Ubuntu partition on the primary hard-drive no matter what I did.

After much cursing and trying to install Grub using whatever methods I could find on the net -- and there are a few -- it dawned on me that maybe my BIOS was pointing to the Grub on the secondary drive. It wasn't something I thought of really, as I'd read a few warnings about checking BIOS to see the boot sequence. But it didn't strike me that Grub was being installed on the primary but that it wasn't being looked at.

So I went into my BIOS and checked it, and there it was: HD1 was in the sequence before HD0! So I just simply swapped them around, and that fixed it. It found the Grub that had been set up the primary hard-disk, and everything went fine after that! Whew! So after two days of searching everything I could, the fix just took two minutes. 

I restored everything from my backups, and had a few problems, the main one being that I installed Thunderbird 3.0 (Shredder). But it couldn't find my Thunderbird 2 files, so I uninstalled 3.0 and brought back 2.0, and it started up with no problems.

I had a hell of a lot of problems with PulseAudio in Ubuntu 9.10 after upgrading from 9.4. That's one reason why I wanted to do a clean install. So far I haven't had any problems with audio, which is great. But it's still too early to tell at this stage.

Anyway, all is good now, and I'm enjoying my Windowless PC. Thanks again for your help darkod, comforting to get feedback after all that frustration!

---

