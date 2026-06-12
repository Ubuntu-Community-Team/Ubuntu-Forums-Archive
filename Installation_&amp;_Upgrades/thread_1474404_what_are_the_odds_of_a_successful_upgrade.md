---
title: "what are the odds of a successful upgrade"
date: 2010-05-06
forum: Installation &amp; Upgrades
---

### Post by noworldorder on 2010-05-06
Does anyone have a sense of what the odds are of successfully installing from 9.10 to 10.04 without something nasty happening?

---

### Post by halj32 on 2010-05-06
it's best to download the CD & do a fresh install.
doing an upgrade has never worked well for me, lots of problems so I would say very low

---

### Post by YuiDaoren on 2010-05-06
I never risk it. I back up /home and any custom configurations in /etc and do a fresh install. It seems to be the way to go if you want to avoid headaches.

(Actually, home is on a separate partition, so the backup part is more precautionary.)

---

### Post by noworldorder on 2010-05-06
I tried to upgrade and then (perhaps a stroke of luck) my internet connection failed and the upgrade was aborted. It said the files are still on my computer.


Did any of the installation steps do anything I need to reverse?



Thanks - Chris

---

### Post by fanofu on 2010-05-08
Every time I try to upgrade from 9.10(Karmic) to 10.04, 99% of files get downloaded and then comes an error message: 

[B]Could not download the upgrades

The upgrade is now aborted. Please check your Internet connection or installation media and try again. All files downloaded so far are kept.

Failed to fetch [http://archive.canonical.com/ubuntu/pool/partner/a/adobe-flashplugin/adobe-flashplugin_10.0.45.2-1lucid1_i386.deb](http://archive.canonical.com/ubuntu/pool/partner/a/adobe-flashplugin/adobe-flashplugin_10.0.45.2-1lucid1_i386.deb) Connection failed[/B]

Can anyone help me?

Thanks,
fanofu

---

### Post by frantid on 2010-05-08
> **fanofu said:**
> [B]
Failed to fetch [http://archive.canonical.com/ubuntu/pool/partner/a/adobe-flashplugin/adobe-flashplugin_10.0.45.2-1lucid1_i386.deb](http://archive.canonical.com/ubuntu/pool/partner/a/adobe-flashplugin/adobe-flashplugin_10.0.45.2-1lucid1_i386.deb) Connection failed[/B]


seems like a few are having problems with flash.  I would uninstall it first before attempting the upgrade.  Then you can always install it after everything else is done.

---

### Post by SneakyBooBoo on 2010-05-08
I get about half-way through the upgrade from a cd-image and then I just get "found linux-kernel-..." something or another over and over and over. And thats about all that happens. No disk activity, nothing, just that line of text repeating itself over and over.

I've reinstalled now and I'll never bother with another upgrade again.

---

### Post by frantid on 2010-05-08
> **SneakyBooBoo said:**
> I get about half-way through the upgrade from a cd-image and then I just get "found linux-kernel-..." something or another over and over and over. And thats about all that happens. No disk activity, nothing, just that line of text repeating itself over and over.

I've reinstalled now and I'll never bother with another upgrade again.

I think there's a note about this in the known bugs thread?  Ctrl-C kills the loop, and then it will continues.  A lot of good that does you now, but maybe it will help someone else.

---

