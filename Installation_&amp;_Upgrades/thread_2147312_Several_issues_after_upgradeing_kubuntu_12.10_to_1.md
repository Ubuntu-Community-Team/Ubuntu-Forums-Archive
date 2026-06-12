---
title: "Several issues after upgradeing kubuntu 12.10 to 13.04"
date: 2013-05-21
forum: Installation &amp; Upgrades
---

### Post by morlix on 2013-05-21
Hello all,

today i decided to upgrade my kubuntu 12.10 to 13.04 to get the latest software.

Unfortunately this wasn't such a good idea, because now i have severall issues.
First of all i want to say that no error messages occur during the upgrade process.

But after the reboot X and KDE won't start automatically and i don't know why.

Ok so i logged in and after typing "startx" kde starts without problems.

The next problem is that KWallet won't work properly anymore, but even if i enter the correct password it keeps asking me for the password again and again and again.

The last problem for which i already found a reason is that the efibootmgr won't work currently under kernel 3.8. Also i have a workaround for this, so this isn't a real problem at all.

I have the following HW:

HP 8760w
Intel(R) Core(TM) i7-2670QM CPU @ 2.20GHz
8 GB RAM
256GB SSD for the system
500 GB HDD for the data
Radeon HD 6730M/6770M/7690M XT with open source drivers

Does anybody have some hints for me on how to solve the first two issues?

Kind regards,

morlix

---

### Post by oldos2er on 2013-05-21
Can you post the output from the following command? ```
cat /etc/default/grub
```

---

### Post by morlix on 2013-05-21
```
~$ cat /etc/default/grub | grep -v ^$ | grep -v ^#
GRUB_DEFAULT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="text"
GRUB_CMDLINE_LINUX=""
GRUB_GFXMODE=1920x1080x24
GRUB_GFXPAYLOAD_LINUX=keep
```

Could you please explain me, what the bootloader has to do with my problems?

---

### Post by morlix on 2013-05-21
Ok i think i know what you want to see :-)

I have "text" mode enabled and thats the reason why lightdm won't start.

---

### Post by morlix on 2013-05-21
Thanks: **[COLOR=#C61919][oldos2er]("http://ubuntuforums.org/member.php?u=338320") [/COLOR]**for this hint! Now KDE and lightdm starts automatically.

Now the next weird problem is with my KWalletd not accepting the correct password.

I already tried to purge kwalletmanager and kwalletcli, restored a kwallet.kwl from a recent backup before the upgrade, but it doesn't change anything.
Anybody you have a hint on how to solve or debug this issue?

---

