---
title: "How to install old kernel from command line"
date: 2022-06-02
forum: Installation &amp; Upgrades
---

### Post by mikeklein on 2022-06-02
Somehow last 2 kernels make my laptop login with no mouse afterwards or even a desktop showing icons...all is frozen.

Bad kernels are linux-image-5.4.0.113 and 109...how do I go about loading and installing say 5.4.0.91 entirely from cmd line?

Any ideas on how to fix problems with problematic kernels would be appreciated even more.

Thanks,
Mike

---

### Post by deadflowr on 2022-06-02
If you know the version then just try
```
sudo apt install linux-image-5.4.0-91-generic
```
you might also want the headers too, just run the same command but replace image with headers like
```
sudo apt install linux-headers-5.4.0-91-generic
```
Reboot is required.
Note that since you have a newer kernel already installed the boot will default to that.
So remember to select the new (older) kernel at boot.

That said, you might want to look into or post back basic hardware info, as it is might not good to run an old kernel for too long.
Here is a fun tool for that: [https://github.com/UbuntuForums/system-info]("https://github.com/UbuntuForums/system-info")

---

### Post by mikeklein on 2022-07-09
Sorry for delay in giving thanks...this worked. After ~2mos I finally got a usable kernel via update/upgrade. Looks like some tests are missing.

---

