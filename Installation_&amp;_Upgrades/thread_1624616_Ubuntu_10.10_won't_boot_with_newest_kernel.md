---
title: "Ubuntu 10.10 won't boot with newest kernel"
date: 2010-11-18
forum: Installation &amp; Upgrades
---

### Post by geewiz89 on 2010-11-18
I had done the upgrade from 10.04 to 10.10 online and couldn't boot to newest kernel and had to select the previous one in GRUB. From what I have read it may be because of NVIDIA drivers or some conflict. 
Anyways,I did a fresh install of 10.10 from the Live CD overriding my 10.04-to-10.10-online-updated partition so I do not have an option to boot older Linux kernels now. I was wondering if the Live CD could be used to install any previous linux kernels for the new installed Ubuntu 10.10 system.

---

### Post by Alexis.M on 2010-11-18
Same problem here after the upgrade from 10.04 to 10.10, the newest kernel won't boot without any error message, leaving a black screen with a flickering cursor. The previous kernel from 10.04 still works though.

---

### Post by geewiz89 on 2010-11-18
> **Alexis.M said:**
> Same problem here after the upgrade from 10.04 to 10.10, the newest kernel won't boot without any error message, leaving a black screen with a flickering cursor. The previous kernel from 10.04 still works though.

Yea, and since I decided to reinstall starting with 10.10, I don't have the option for the older kernel anymore. That's why I'm wondering if there is a way to make the Live CD edit my installed version of Ubuntu. Or at very least, can I install stuff running the Live CD, reinstall, and have all the stuff I installed/changed during the Live CD session take hold in the reinstall?

---

### Post by z5h on 2010-11-18
I'm in the same situation.

---

### Post by Mark Phelps on 2010-11-18
I've encountered a very similar problem and in my case, reinstalling the ubuntu-desktop package fixed it.  It's worth a shot to try that.

---

### Post by geewiz89 on 2010-11-18
> **Mark Phelps said:**
> I've encountered a very similar problem and in my case, reinstalling the ubuntu-desktop package fixed it.  It's worth a shot to try that.

I'm assuming you did this from an older kernel? My problem is I don't have any older kernel since my 10.10 is a fresh install and I'm looking for an option where I don't have to download and make a 10.04 disc and install that just to get the older kernel.

---

### Post by Frogs Hair on 2010-11-18
I had this issue once , not from an upgrade but a kernel update. I removed the Nvidia driver and booted with the new kernel , reinstalled the driver and rebooted. This was with 9.10 and only it happened once.

---

### Post by geewiz89 on 2010-11-19
> **Frogs Hair said:**
> I had this issue once , not from an upgrade but a kernel update. I removed the Nvidia driver and booted with the new kernel , reinstalled the driver and rebooted. This was with 9.10 and only it happened once.

The best I can figure out is to press "e" on the newest kernel, since again, that's all I have, delete 'quiet splash" and add "acpi=off" and it boots to terminal and that's all I get. I can't get th wifi to connect through it (tried) to download older version of linux kernel, I tried editing a config file to change nvidia driver to linux's generic "nv" driver, nothing.

---

### Post by geewiz89 on 2010-11-20
I ended up just re-downloading the 10.04 x64 disc image and burned and installed that. The funny thing is I don't get the option to upgrade to 10.10 after running Update Manager like I did before. I'm still in the process of installing and updating my repositories right now so I'm guessing the option will eventually come up. Not sure if I'm going to rush it though after that ordeal.

---

