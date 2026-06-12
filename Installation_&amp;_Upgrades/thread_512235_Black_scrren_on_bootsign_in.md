---
title: "Black scrren on boot/sign in"
date: 2007-07-28
forum: Installation &amp; Upgrades
---

### Post by ratbagradio on 2007-07-28
I have just upgraded from Edgy to Feisty -- 7.04 -- yesterday.
The boot took fine and I was trying to engineer better device management before breaking for lunch (sardines on toast).
 I came back and the screen was black and nothing I could do would bring it back to graphical presentation.
So I rebooted.
Booted up fine -- got to the "UBUNTU" logo screen and then there was no sign in screen (for username or password)-- just black wall to wall  after Ubunrtu tried twice to proceed(there was some static imagery strip on the bottom of the screen briefly )

I'd appreciate any suggestions...

I'm running Ubuntu alone on my pc. And it had functioned fine until this glitch kicked in ....and the Edgy envionemnt was Ok except for issues with mounting portable media and this is why I decided to upgrade.

Is this my big mistake?

---

### Post by rillip on 2007-07-29
I'm guessing that xorg is configured wrong.  Try adding something like vga=791 to the end of your grub menu by editing it when the menu comes up (think you hit e).  This will put it in 1024 x 768.  794 puts it in 1280 x 1024 (forget what the next size up is, think that's it)

That should get you far enough to be able to reconfigure xorg  I think.  To do so

```
sudo dpkg-reconfigure xserver-xorg
```

---

### Post by ratbagradio on 2007-07-29
Thanks. I installed feisty from the CD in a comeplete and new  install and the issue seems to be passe now.

---

