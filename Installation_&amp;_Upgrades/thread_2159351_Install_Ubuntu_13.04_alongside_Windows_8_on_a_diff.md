---
title: "Install Ubuntu 13.04 alongside Windows 8 on a different drive"
date: 2013-07-02
forum: Installation &amp; Upgrades
---

### Post by GeneralShep on 2013-07-02
Hey guys, I have tried installing Ubuntu 13.04 x64 on my computer, however the option to boot into Ubuntu never appears on startup. This is my current setup

Drive 1: 120GB SSD; Windows 8
Drive 2: 3TB HDD; File Storage
Drive 3: 320GB HDD; <Empty>

I am trying to install Ubuntu onto Drive 3, with Drive 1 holding Windows 8, and Drive 2 storing my files. I am able to install it, however when I boot up I am never given the option to boot into Ubuntu. I am guessing that either NT Loader doesn't register Ubuntu as an OS to boot into, or it ignores it. Do I need to do something in particular to solve this issue?

Thanks.

---

### Post by fantab on 2013-07-03
Boot with Ubuntu Live DVD/USB, then 'Try Ubuntu without installing' and let the desktop load. Open Terminal [Ctrl+Alt+T] run the following command and post its output here:

```
sudo parted -l
```

Also tell us if Windows8 is pre-installed? What laptop/desktop (name, model and manufacturer) do you have?

Most likely, your Windows 8 boots in EFI mode using UEFI. If this is true then Ubuntu must also be installed in EFI mode. To install in EFI mode we need to have GUID Partition Table (GPT) on our HDD. I suspect that you don't have GPT on your third. The out put from the above command will clarify this for us.

---

### Post by GeneralShep on 2013-07-03
Okay, I'll boot with the Live USB when I have the chance.

Yes, Windows 8 is pre-installed, however I wouldn't mind re-installing it to get Ubuntu working. My computer is custom built.

Thank you for the help.

---

### Post by Mark Phelps on 2013-07-03
You said > Windows 8 is pre-installed which generally means that Win8 came WITH the PC, and no installation media is available, only a Recovery partition.

If that is true, how do you plan to reinstall Win8?

---

