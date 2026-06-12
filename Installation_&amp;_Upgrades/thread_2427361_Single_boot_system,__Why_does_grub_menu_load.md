---
title: "Single boot system,  Why does grub menu load"
date: 2019-09-21
forum: Installation &amp; Upgrades
---

### Post by livelyc on 2019-09-21
Hello everyone,

After much teeth gnashing, hair pulling and screaming,  I was finally able to get my new Dell G5 laptop to boot in secure mode.  Only one thing wrong,  I've never had grub menu appear on a single boot system after install before.  I'm trying to suppress it,  but nothing seems to work.  Here is my grub config...
```
GRUB_DEFAULT=0
GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=0
GRUB_DISABLE_OS_PROBER=true
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""
```

I've tried reducing the GRUB_TIMEOUT from 30 to 15,  The menu countdown still starts counting down from 30.
I've also tried commenting out the GRUB_TIMEOUT=15 line,  this had no effect.
In any case, after making changes,  I've ran...[INDENT]
```
sudo grub-mkconfig 
sudo sudo grub-install /dev/nvme0n1p1
sudo update-grub
```

[/INDENT]
 None of the changes I've made have seemed to have any effect. can anyone help me solve this issue?  I don't need nor want to see the grub menu on startup.

Thanks in advance.

P.S. 

I've also tried using Grub Customizer,  and saving the configuration to the MBR of /dev/nvme0 as well.  Absolutely nothing seems to have any effect.

---

### Post by livelyc on 2019-09-21
This was solved with a complete reinstall.  lame, that it had to come to that, but it is what it is.

---

### Post by oldfred on 2019-09-21
You probably only needed a complete reinstall of grub.

And grub customizer creates copies of grub files so standard grub files then are not used. Full reinstall of grub then overwrites grub customizer files.
And if any corruption in grub entries, you get grub.cfg.new with grub-update which says you have an error, so no changes are actually written into grub.cfg.

---

