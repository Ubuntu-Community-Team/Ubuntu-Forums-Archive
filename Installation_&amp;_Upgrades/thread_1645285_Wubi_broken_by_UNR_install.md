---
title: "Wubi broken by UNR install"
date: 2010-12-14
forum: Installation &amp; Upgrades
---

### Post by Eno88 on 2010-12-14
2 problems in a day, go me!
 
Long story short, wanted to install UNR 10.04 proper, dropping WUBI. I figured I'd move my home folder and installed apps from wubi to the regular partition **from inside** the wubi install, **after** installing UNR and it's bootloader on a partition.
 
The Wubi install no longer works, trying to boot it hangs at mounting a no longer existant logical partition. That partition used to be ntfs storage, now becoming the proper UNR partition.
Wubi's Grub actually says it's not a NTFS partition anymore and hangs there.
 
Questions:
Would reinstalling Wubi from Windows (keeping the \disks\ folder) solve anything?
Is there anything I can do from Wubi Grub's command line?
 
Updating with the full error message a bit later.
 
Edit: Will try this first: [http://art.ubuntuforums.org/showthread.php?t=1037874](http://art.ubuntuforums.org/showthread.php?t=1037874)
That worked but still leaves me without the apps I had installed, any solutions for that please?

---

### Post by bcbc on 2010-12-14
> **Eno88 said:**
> 2 problems in a day, go me!
 
Long story short, wanted to install UNR 10.04 proper, dropping WUBI. I figured I'd move my home folder and installed apps from wubi to the regular partition **from inside** the wubi install, **after** installing UNR and it's bootloader on a partition.
 
The Wubi install no longer works, trying to boot it hangs at mounting a no longer existant logical partition. That partition used to be ntfs storage, now becoming the proper UNR partition.
Wubi's Grub actually says it's not a NTFS partition anymore and hangs there.
 
Questions:
Would reinstalling Wubi from Windows (keeping the \disks\ folder) solve anything?
Is there anything I can do from Wubi Grub's command line?
 
Updating with the full error message a bit later.
 
Edit: Will try this first: [http://art.ubuntuforums.org/showthread.php?t=1037874](http://art.ubuntuforums.org/showthread.php?t=1037874)

It sounds like you had Wubi on partition X, and overwrote this partition when you installed UNR. So it's probably gone. But run the [bootinfoscript]("http://bootinfoscript.sourceforge.net/") and post the results. That will indicate whether the root.disk is somewhere - maybe just the partition number changed when you installed UNR and that's a simple fix.

---

### Post by Eno88 on 2010-12-14
I had wubi on Win7's partition (bad, I know), I gave UNR it's own partition so I still have Windows and wubi files.
 
Now, I've managed to get my /home/user files out of wubi's virtual disk but I keep getting denied copying all other folders from it's / to UNR's /
Any way to get my apps list out of the virtual disk?
Also, if I could recover the theme I had on would be nice :popcorn:

---

### Post by bcbc on 2010-12-14
> **Eno88 said:**
> I had wubi on Win7's partition (bad, I know), I gave UNR it's own partition so I still have Windows and wubi files.
 
Now, I've managed to get my /home/user files out of wubi's virtual disk but I keep getting denied copying all other folders from it's / to UNR's /
Any way to get my apps list out of the virtual disk?
Also, if I could recover the theme I had on would be nice :popcorn:

I wouldn't just copy from / to /. There are a lot of things that will not work. If you wanted to, you could have migrated the wubi install instead.
PS if the problem is that you're mounting the old ntfs partition that's now the Netbook edition install... just loop mount the root.disk and edit /etc/fstab and take out the line mounting that partition.

---

### Post by Eno88 on 2010-12-14
That did it!
Thanks a lot, now I've got both installs running.

Could you recommend a good tutorial to migrate apps,settings, themes and such? LVPM site says 10.04 isn't supported.

---

### Post by bcbc on 2010-12-14
[http://ubuntuforums.org/showthread.php?t=1519354](http://ubuntuforums.org/showthread.php?t=1519354)

---

### Post by Eno88 on 2010-12-15
Must've screwed that up somewhere.. rsync went well, but I think it went the wrong way around. None of the apps were moved to the new Ubuntu install and now both grub and wubigrub point to the new ubuntu partition.
 
Will fix grub to point to the virtual disk and go at it again :/
 
Edit:
Could I do this with cp instead of rsync?

---

### Post by bcbc on 2010-12-15
That link is to migrate a wubi install, not merge apps and settings from one install to another.

---

