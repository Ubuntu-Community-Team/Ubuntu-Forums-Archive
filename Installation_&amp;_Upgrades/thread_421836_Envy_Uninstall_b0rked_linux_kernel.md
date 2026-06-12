---
title: "Envy Uninstall b0rked linux kernel"
date: 2007-04-24
forum: Installation &amp; Upgrades
---

### Post by allwin on 2007-04-24
Anyone want to try and handle this one?

In preparation for upgrade to FF, I went into ENVY to uninstall the Nvidia driver for my old card.  That went fine.  I wanted to remove that because I read out here how it messes things up...thinking if I was all OSS code, it'd be an easier update...I could deal with Beryl and all that after I got FF running.

When I rebooted (I changed xorg.conf to "NV" from "NVIDIA" cuz I thot I knew what I was doing), it complained about garbage in /lib/modules/2.6.17.11-generic/modules.alias before bringing X up (I have quiet turned off at boot).  Somehow "modules.alias" got messed up by the uninstall.  Trying to reinstall with ENVY resulted in segfault and a mess of messages about lots of modules ending in .ko not being loadable.

SO...I rebooted with the .10 kernel, reran ENVY, it installed a new copy of Nvidia, and I could get back into the GNOME desktop just fine.  I said, WTF, I'm upgrading anyhow, so I went for broke and ran update-notifier.  I wanted to pick up the last few Edgy updates before pushing the BIG BUTTON.

Synaptic comes back complaining about a syntax error near line 300 in package "glibc", something about duplicate symbol SHA256 nearby, trying to fix, NET RESULT-I cannot install anything any more!

I did have to shutdown the power on this system once, and I ran E2FSCK just in case, but it found no errors.

NOW I"M STUCK!  I can't run anything but the older .10 kernel and I can't upgrade anything.

I even copied modules.alias from .10 to .11, which cured the boot time errors, but rendered ENVY confused with the seg fault and complaint about all the .ko modules not being in 'elf' format.  Yeah, I figured .10 and .11 couldn't be that different...something had placed a binary file inside modules.alias, which is supposed to be text.

I would LIKE to uninstall the .11 kernel and re-install it (maybe that would straighten it out) and tried that even but the "duplicate SHA256" error comes up almost immediately when I try to do that.

Any ideas how I recover this mess?
Can anyone help me out here?

---

### Post by allwin on 2007-04-25
SOLVED!  I dunno how I found this but I ran:

dpkg --clear-available

which removed the faulty 'glibc' package and then enabled me to reinstall the latest kernel plus the restricted modules (the most important part).  Evidently ENVY is capable of scrogging things when you uninstall.  BTW, the update to Feisty went well and I only had to download the latest ENVY version, run it, and I got Beryl back and all systems go under FF.

---

