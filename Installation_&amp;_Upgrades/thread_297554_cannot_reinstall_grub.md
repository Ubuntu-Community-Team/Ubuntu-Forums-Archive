---
title: "cannot reinstall grub"
date: 2006-11-11
forum: Installation &amp; Upgrades
---

### Post by coldrick on 2006-11-11
I have a dual-boot Edgy/winXP laptop. After having a play with [mojopac]("http://www.mojopac.com") from the windoze boot, I rebooted, only to have grub fail with an Error 17. Grrr. Not impressed with mojopac.

Rebooted with alternate CD, chose "Rescue a broken system", and got to Enter rescue mode. Chose my Edgy boot partition (/dev/sda6), then chose Reinstall GRUB boot loader, entered /dev/sda. I get 'grub-reinstall' failed with exit code 20.

Hm. Try "execute a shell in /dev/sda6". Get a window that shows "Installing GRUB boot loader" at 50%. Can't get any response from this. ](*,) Reboot with alternate CD again.

 Get back to "execute a shell in /dev/sda6": get prompt, try sudo grub. Now I get "Probing devices to guess BIOS drives. This may take a long time.", followed by "Error opening terminal: bterm"

Try sudo grub-install (hd0) and get a syntax error. Try sudo grub-install /dev/sda and get "/dev/sda: not found or not a block device." Same for /dev/hda

Where to now? (BTW, /dev/sda6 is indeed my Ubuntu boot: ls shows the right stuff.)

Help!

Regards,
David

---

### Post by DaveBorealis on 2006-11-11
> **coldrick said:**
> I get 'grub-reinstall' failed with exit code 20.

Hello David,

I've never used the alternate CD to rescue a broken system, but from your description the problem might be one of having to mount the hard drive.

```
mount -a
```

Something to try...
Dave

---

### Post by Herman on 2006-11-11
coldrick, 
I'm very interested since I'm the author of a website about how to use the 'Alternate' CD, and also about Grub and other bootloaders and managers.
Thanks to your post, I am testing out the same thing right now, and received the same errors for the first two methods you described. I could not install Grub with the 'Edgy' RC Alternate CD either, or open a Grub shell for installing Grub.

However, I was able to use the grub-install command successfully. I do not prefer using the grub-install command, I think it's better to install grub from a grub shell. Anyway, it worked. I used 'grub-install /dev/hda' for mine. (No 'sudo', because it's already a # prompt, and replace (hd0) with /dev/hda for this.

I tried a few other things in the 'Rescue mode' of my 'Edgy Eft' release candidate alternate CD, and there seems to be quite a few bugs in this part of it. I'm still using the release candidate because the officially released Edgy Alternate CD I had was defective. It passed its md5sum integrity test for the downloaded .iso file, but failed it's own 'check CD for defects' test, and failed to successfully complete an install.

The Dapper Alternate CD was much better. Everything worked properly. It doesn't seem as if much care went into the making of the Alternate CD for 'Edgy', unfortunately. The 'Desktop' live/install CDs seem to be okay. Maybe they don't care about the Alternate CDs anymore.

Regards, Herman :(

-----------
EDIT: Well, I guess in all fairness, most ordinary mortals should be sticking with Dapper Drake anyway, it's the stable release with Long Term Support (LTS). 
Edgy Eft is more for the enthusiast who is expert enough to put up with a few hiccups and minor glitches and who actually enjoy a few challenges.
Similarly, the 'Alternate' CD is also more for those of us who know what we are doing, whereas the 'Desktop' CD is for general use.
It seemed as if we had to wait forever for Dapper to be released, because they took so much care with it, but 'Edgy' was out on time.  I guess we should not be expecting to be able to have things fast and perfect too. I must say that I have had no other real problems with Edgy Eft. Edgy Eft is great. :D

David, have you tried out adrian15's Super Grub Disk? [http://adrian15.raulete.net/grub/tiki-index.php](http://adrian15.raulete.net/grub/tiki-index.php)
That's the software most people are using for working with bootloaders nowadays.

---

### Post by coldrick on 2006-11-12
Gave it away and reinstalled. Sheesh! :-? 

Regards,
David

---

