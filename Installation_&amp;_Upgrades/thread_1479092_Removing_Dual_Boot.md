---
title: "Removing Dual Boot"
date: 2010-05-10
forum: Installation &amp; Upgrades
---

### Post by jcdlinux on 2010-05-10
Hi,

I installed Ubuntu (9.10) through wubi a few weeks ago, but was experiencing problems so I uninstalled it. When booting though, I could still get the the GRUB screen to select my OS; I ignored this and later installed Ubuntu to dual boot with XP with the live CD by resizing the XP partition. Then when I tried to select XP It would take a long time to boot, and would later only display my desktop background and the cursor. This happens every time I select XP. Ubuntu works fine, I even upgraded to 10.04 no problems, but my XP install is not working. I have to force it to shut down, and holding Ctrl+Alt+Del gives me Task Manager without anything running, and If I click shut down or restart, it just hangs there like if it were on strike!

Now, how do I completely remove Ubuntu with GRUB and fix the XP without loosing what is stored on my Windows partition. Then I would try to install Ubuntu 10.04.

Thanks in advanced

---

### Post by darkod on 2010-05-10
Unfortunately this doesn't sound like dual booting issue. It looks like the XP was corrupted during the resizing. Windows and especially XP is very sensitive to resizing the system partition and likes to do its disk checks after.

That's why it is better practice to shrink the partition first, boot windows few times to do the disk checks, and only then start the ubuntu installer and install in the unallocated space. Letting the installer shrink it is an easy way, but can create these issues.

You might try the XP repair function. When you boot with the XP install cd in the first screen (I think it was first), select Enter to continue installation (NOT Recovery Console), then on the next screen you would have option to try repair with R.

Once XP is running fine, even if it destroys grub2 on the MBR, DO NOT install ubuntu again, it's still there (should be). You can just reinstall grub2 to the MBR, otherwise windows can't boot ubuntu, not straight forward at least.

But lets get to that step first, it's very easy to reinstall grub2.

---

### Post by jcdlinux on 2010-05-10
Hi darkod,

Thanks for the info. I'll try to follow the steps you gave me and will post back the results.

Thanks!

---

### Post by jcdlinux on 2010-05-12
Hi,

I was not able to do what was suggested because the windows xp CD does not give me the option to repair windows, only the option to install over it. I tried deleting the ubuntu partition and now get an error from Grub. I also tried using ms-sys to repair the MBR from Ubuntu live CD, but even though it said it was repaired I still get error from GRUB. Anymore ideas?

---

### Post by darkod on 2010-05-12
If you are sure there wasn't an option to repair the installation, it might be that it's messed up so badly that even windows cd can't detect it.

In that case I guess reinstalling is the only option.

I would still try once more to repair. Look at the attached images. The XP1 is the first and you should press Enter as if you want to install, not repair. Then accept the license agreement and when XP2 screen comes up, press R for repair.

But if it doesn't show a detected installation like in the picture, it seems there is no help.

In that case quit the installer and you can try to get your data out by booting the ubuntu live mode (Try Ubuntu).

That should still be able to read the XP partition and copy files. Copy everything you need, then install XP into the partition where you want it, NOT the whole hdd. That way you don't have to shrink later.

---

### Post by Doug11 on 2010-05-12
If he boots from the live cd,,will he still be able to see his XP partition and recover some of his files wanted to backup?

---

### Post by jcdlinux on 2010-05-13
Hi,

No there is still no option. It detects a version of Windows but does not give the option. I did a search and found that this could happen, but couldn't find a workaround.

And yes, I am able to see the files from windows, so I can back them up, but this will take a lot since there are a lot of GB of data, that's why I wanted to repair it (I am also doing to have to install a lot of applications again :confused:)

---

### Post by darkod on 2010-05-13
> **jcdlinux said:**
> Hi,

No there is still no option. It detects a version of Windows but does not give the option. I did a search and found that this could happen, but couldn't find a workaround.

And yes, I am able to see the files from windows, so I can back them up, but this will take a lot since there are a lot of GB of data, that's why I wanted to repair it (I am also doing to have to install a lot of applications again :confused:)
I guess that's the only option right now. At least you can get the data out. :)

---

