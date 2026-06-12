---
title: "Error msg on boot after activating driver"
date: 2013-01-31
forum: Installation &amp; Upgrades
---

### Post by oxf on 2013-01-31
Lubuntu 12.04, LTS
Acer Aspire One, D270

I installed Lubuntu on the above laptop, successfully
I then ran software update, again successfully, all runs nicely in fact.

I then checked the additional hardware drivers and activated the CedarTrail graphics driver. Driver installed except right at the end something causes it to go to a black screen.
However, this has happened before and always a reboot results in it loaded and ready to go.

This time however, it won't fully boot and stalls at the following error message:
```

Could not write bytes, broken pipe

phy0: brcms_ops_bss_info_changed: qos enabled: false (implement)
phy0: brcmsmac: brcms_ops_bss_info_changed: associated
phy0: changing basic rates: failed: -22
phy0: brcms_ops_bss_info_changed: arp filtering: enabled true, count 0 (implement)
phy0:  brcms_ops_bss_info_changed: arp filtering: enabled true, count 1 (implement)
```What does this mean? Should I try and boot to recovery mode or shell. And if so what to do when I get there?

Thanks
Caitlin

---

### Post by dino99 on 2013-01-31
i think you should download & install the latest 3.8-rc5 kernel to get the newest hardware drivers

[http://kernel.ubuntu.com/~kernel-ppa/mainline/daily/current/](http://kernel.ubuntu.com/~kernel-ppa/mainline/daily/current/)

into an empty folder, download the 2 required headers (...all.deb, i386/amd.deb) & the 2 images (image & image-extra)
then goto that folder, to run:  

sudo dpkg -i *

---

### Post by oxf on 2013-01-31
> **dino99 said:**
> i think you should download & install the latest 3.8-rc5 kernel to get the newest hardware drivers

[http://kernel.ubuntu.com/~kernel-ppa/mainline/daily/current/](http://kernel.ubuntu.com/~kernel-ppa/mainline/daily/current/)

into an empty folder, download the 2 required headers (...all.deb, i386/amd.deb) & the 2 images (image & image-extra)
then goto that folder, to run:  

sudo dpkg -i *

Thanks..
I'll be honest I don't fully understand what I'm doing here but will try.

I can boot into recover mode and run dpkg from there? 

I know this driver does work on the pc because I've installed in on Ubuntu on the other partition which is what I'm using right now. 

I'm thinking of just reinstalling Lubuntu and not activating the graphics driver. Is there a way I can download it/activate it from terminal instead?

Thanks
Caitlin

---

### Post by oxf on 2013-02-06
Well an update;

After trying to boot it drops me to a tty terminal. Someone suggested I try running
"startx" from the tty terminal. I tried this and I get an error message which tells me it failing to connect to xserver.

I've searched around and it does appear this is a known bug associated with this driver/chip and my solution might be to try a different graphics driver. 

This is where I get lost. Is there a way I can remove the above driver and install a different one from tty?

And the final question: If Ubuntu will run on this machine why not Lubuntu??????

Thanks

---

