---
title: "Can't boot 14.04 after motherboard replaced"
date: 2016-04-08
forum: Installation &amp; Upgrades
---

### Post by eltreno on 2016-04-08
Hi,

I have a dell XSP 13 ultrabook which has ubuntu 14.04 installed (as the "only operating system" on the machine - windows was wiped when I did the USB install) and I had the install use the "encrypted drive" option.

I have not done anything special in regards to the boot system, everything is still default.

Motherboard was replaced today, and now on boot it says "The operating system cannot be detected."

SSD is still detected in BIOS, I have also tried booting with "legacy" as well as "UEFI", and UEFI with secure boot mode "enabled" and "disabled", but each time "The operating system cannot be detected."

I also went through the recommended boot-repair option (this was done running from a LIVE-USB), I tried the reboot but nothing.

So here is the recommended paste to show ubuntu forum heros, to see if anyone can point me in the right direction from here.

[http://paste.ubuntu.com/15682559/](http://paste.ubuntu.com/15682559/)

I am also OK to follow a commend line tutorial if there is anything that can be recommended.

Thanks.

---

### Post by eltreno on 2016-04-08
So, after few hrs of hair pulling, I ended up running boot-repair a second time. This time it gave me a bunch commands to run.

Now I am in a position where my Ubuntu colored boot screen gives me 4 options to boot from (when I sect Advanced boot options because the default "Ubuntu" option *Drops into **shell* after about 30 seconds of the Ubuntu loading screen

linux-image-3.13.0-85-generic
linux-image-3.13.0-85-generic   safe mode
linux-image-3.13.0-83-generic
linux-image-3.13.0-83-generic   safe mode


I now have to select the earlier version 83-generic   (because 85-generic will not work - it skips the passphrase screen)

83-generic takes me to my passphrase screen and then loads perfectly.

So....anything I should do to get 85-generic working?

Should I be worried on the next dist upgrade 86-generic that it may not boot again, or should the next update fix grub to use the encrypted passphase boot procedure as well?

---

### Post by gordintoronto on 2016-04-08
First things first: it's working, so make sure you have a backup of everything you care about on an external drive. And another backup on Dropbox.

---

### Post by kansasnoob on 2016-04-08
Was the graphics chip changed also? I'm thinking it sounds like a graphics issue.

---

### Post by eltreno on 2016-04-09
Yes I have everything backed-up twice - so all good there :)

It has [COLOR=#000000][FONT=Trebuchet MS]Intel(R) HD Graphics 520 which I think is on the motherboard so I expect it was changed.

I am still able to boot into the [/FONT][/COLOR]linux-image-3.13.0-83-generic, so i am just doing that for now and keeping backups etc - and waiting for the [COLOR=#000000][FONT=Trebuchet MS] [/FONT][/COLOR]linux-image-3.13.0-86-generic upgrade.

I'll post back the results of what happened when I get it.

---

### Post by kansasnoob on 2016-04-09
> **eltreno said:**
> Yes I have everything backed-up twice - so all good there :)

It has [COLOR=#000000][FONT=Trebuchet MS]Intel(R) HD Graphics 520 which I think is on the motherboard so I expect it was changed.

I am still able to boot into the [/FONT][/COLOR]linux-image-3.13.0-83-generic, so i am just doing that for now and keeping backups etc - and waiting for the [COLOR=#000000][FONT=Trebuchet MS] [/FONT][/COLOR]linux-image-3.13.0-86-generic upgrade.

I'll post back the results of what happened when I get it.

Was the old graphics chip considerably different? I wonder if you'd installed a proprietary driver that no longer works properly with the new chip?

---

