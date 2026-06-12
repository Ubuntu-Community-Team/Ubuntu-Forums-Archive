---
title: "Installed Ubuntu but can't run Windows"
date: 2014-04-22
forum: Installation &amp; Upgrades
---

### Post by trevsmith1994 on 2014-04-22
Hello there,

I recently heard about Ubuntu and was excited to try it out. However, I seem to have made a bad decision. I installed it successfully the first time, but then the grub/boot menu wouldn't come up. It would just go straight to Windows, like Ubuntu wasn't even there (even though I am sure it was installed). Anyways, I decided I would go back in to the Ubuntu installation using my flash drive (the "try Ubuntu" version) and I selected the option where you can uninstall Ubuntu and then re-install. After I did this, the boot menu still didn't work--BUT the terrible thing is instead of going to Windows, it goes straight to Ubuntu without giving me an option! And on my computer's boot menu (I press F12 to get to it) there are two options: Ubuntu and Ubuntu! I am so confused and mortified. Did I somehow erase Windows 8? Please help! Thanks in advance. :)

---

### Post by fantab on 2014-04-23
Boot with Ubuntu DVD/USB, Try Ubunu and open Terminal [ctrl+alt+t], run the following commands and post its output here:

```
sudo fdisk -l
sudo parted -l
```

---

### Post by Stephen_Wade on 2014-04-24
Trevsmith---I am in a similar position, I am concerned that if I install Ubuntu alongside Windows, will I be able to access Windows. Are you making any progress?

---

### Post by lisati on 2014-04-24
@trevsmith1994: Please post the output from the commands given in [fantab's post]("http://ubuntuforums.org/showthread.php?t=2219100&p=12998714&viewfull=1#post12998714"). This will provide us with information that will help us start troubleshooting.

@steven_wade: Installation of Ubuntu side-by-side with Windows, sometimes called **dual boot**, *is* possible. Please be patient with us if we focus on Trev's question in this discussion/thread, otherwise it could get confusing. 

More information on dual boot can be found here: [https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)

---

