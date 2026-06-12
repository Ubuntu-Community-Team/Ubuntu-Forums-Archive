---
title: "Upgrade to 10.04 hanging"
date: 2012-06-27
forum: Installation &amp; Upgrades
---

### Post by mgbridges on 2012-06-27
The upgrade of my PC from 8.04 to 10.04 has hung mid-way through installation. Last message was "processing triggers for python-central". Mouse & keyboard are not responsive.

What can I do from here? If I hit the reset button on the PC am I going to be left with a dead box?

Cheers,

Martin

---

### Post by darkod on 2012-06-27
Yeah, if you reset it will probably be unbootable (not always though).

In case that happens, see if you can boot the recovery mode. If the recovery menu sohws, select Network first to activate the network (for internet) and then select Drop to root shell.

Once in the root shell, try to finish off the upgrade with:
```
dpkg --configure -a
apt-get install -f
```

If there is no way to boot even the recovery mode, you will have to boot in live mode with the cd and enter the installation with chroot to execute the above commands.

---

### Post by mgbridges on 2012-06-27
Thanks. I hit the reset button and as expected the PC failed to boot. I'm sat at an (initramfs) prompt. 

Should I create an 8.04 Live CD (the version I was upgrading *from*) or a 10.04 CD (the version I was upgrading *to*)?

Will the Live CD spot the failed upgrade?

Cheers,

Martin

---

### Post by mgbridges on 2012-06-27
Hmmm. I dug out my old 8.04 CD and tried booting from that. I selected "Try Ubuntu without installing" but I still don't manage to boot - I still get an (initramfs) prompt.

Any ideas? I'm a bit out of my depth here, as you might be able to tell.

---

### Post by darkod on 2012-06-27
I would actually try with 10.04 since the upgrade already started.

But before that, did you check whether recovery mode is available? If you have only ubuntu the grub boot menu might not show by default, so you need to press a button as soon as the board POST finishes.

Now, with 8.04 you probably had grub1 while 10.04 comes with grub2. Since we are not sure if the grub package got upgraded, you can try to show the menu with hitting Esc, or if that fails, with hitting Shift.

Shift is for grub2 and I think Esc was for grub1. Immediately after the POST start hitting the button few times. For grub2 sometimes even holding Shift works.

If you manage to get the grub menu to show, select the recovery mode entry and try the suggestion from the previous post.

---

### Post by mgbridges on 2012-06-27
Thanks. I managed to get into the GRUB menu by pressing ESC, so I guess I'm still on GRUB1. I tried selecting the recovery option but it failed in the same way as the normal boot.

I've just created a 10.04 LiveCD now so I'll try that.

---

### Post by mgbridges on 2012-06-27
10.04 LiveCD got me in, so now I've managed to restart the upgrade. Fingers crossed and thanks for the help.

---

### Post by darkod on 2012-06-27
No problem. Let us know how it goes.

---

### Post by mgbridges on 2012-06-27
I mounted my boot disk, chroot'd to it and ran the commands you suggested. It churned away for a long time, all seemed to be going well, but it terminated with "Processing was halted because there were too many errors"

Do you think I'm safe to try and boot directly now?

---

### Post by darkod on 2012-06-27
Honestly, I have no idea what it wants to tell you.

But you can always try to boot it, you can't do any damage with it.

Usually those commands can finish an interrupted upgrade process but it's not a 100% guarantee.

If it keeps giving you errors, you will have to focus on the exact error and whether it mentions for which package it refers, what does it have a problem with.

---

### Post by mgbridges on 2012-06-27
Getting steadily closer! I rebooted it and it came up fairly OK, but with a couple of errors:
[LIST]
[*]failed to mount my fileshare
[*]didn't start gde
[/LIST]
I'm now re-running the dpkg command and seem to be getting closer to having gde!

---

### Post by mgbridges on 2012-06-27
I'm marking this thread as solved. Thanks to Darko's advice I have managed to get the system to a point at which it will successfully boot into 10.04 with a desktop environment. I still have a couple of significant problems (no networking, failing to mount my RAID array) but I'll raise these in a separate thread.

Thanks Darko.

---

### Post by darkod on 2012-06-27
No problem.

If that is software raid I would like to take a look at that thread too since I am interested in mdadm and any problems with it.

---

