---
title: "ubuntu 12.04 not booting -&gt; with ubuntu 13.04 the same problem"
date: 2013-05-03
forum: Installation &amp; Upgrades
---

### Post by marchenamarlene on 2013-05-03
I was using ubuntu 12.04 when suddenly my laptop did not boot anymore. I tried to solve the problem but nothing worked so I  installed ubuntu 13.04 instead of ubuntu 12.04 (preserving the same  partition). But with the new installation the problem was the same. I realized that the problem  was the booting rather than the installation, so I tried the boot  repair.
 

When I clicked to the Bootinfo summary bottom I had

[IMG]https://mail.google.com/mail/u/0/images/cleardot.gif[/IMG]
[http://paste.ubuntu.com/5624270/](http://paste.ubuntu.com/5624270/)


and when I clicked to  the Recommended repair bottom I had

[http://paste.ubuntu.com/]("http://paste.ubuntu.com/5624270/")5624292/


I  am still not able to boot my computer and now when I use the liveUSB I  have the following message: "The installer encountered an unrecoverable  error. A desktop session will now be run so that you may investigate the  problem or try to install again"


Now I do not know what to do. Any help will be much appreciated.

Regards,

Marlene.
[IMG]https://mail.google.com/mail/u/0/images/cleardot.gif[/IMG]

---

### Post by Bashing-om on 2013-05-03
marchenamarlene; Hi ! Welcome to the forum .

Let's pre suppose that an update to the 12.04 broke your graphics driver and that a compatible driver in 13.04 has not been loaded.

Try this and advise results:
Boot ubuntu and as soon as the bios screen clears, depress and hold the shift key -> grub boot menu.
Arrow down to a recover mode kernel and press the enter key -> recovery console menu -> resume normal boot;

Can you now boot ubuntu under low graphics mode ?
[INDENT=2]
try'n to help

[/INDENT]

---

### Post by marchenamarlene on 2013-05-12
Hi,

When I ran -> grub boot menu

I get: "Could not find kernel image: grub" and the boot menu does not work. 

Now what I need to do?

Thanks!

---

### Post by Bashing-om on 2013-05-12
marchenamarlene; Hey .

You are taking an incorrect approach to get into the recovery mode.
1. Boot ubuntu
2. As soon as the startup bios screen clears, depress and hold the shift key
3. this institutes the grub selection booting screen, here arrow down to the entry "recovery kernel" - or some such
4. Press the enter key
5. this institutes the recovery console screen, here choose "resume normal boot"

Do you now boot to a GUI login screen ? if so then login here and do you now get to the desk top -- graphics may be degraded - that is fixable in the next steps.

can you get this far in booting up ubuntu ?
[INDENT=2]
my best regards

[/INDENT]

---

