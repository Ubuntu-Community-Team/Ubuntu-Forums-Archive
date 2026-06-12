---
title: "Is it ok to upgrade precision 7750 to 22.04 jammy jellyfish?"
date: 2022-06-23
forum: Installation &amp; Upgrades
---

### Post by Ranbunta_Bantubunt on 2022-06-23
I have a dell precision 7750 with the Dell-supplied ubuntu 20.04 installed. I am wondering about trying to get on Jellyfish (motivated most proximally by the desire to upgrade Evolution, as Jellyfish supports .44 and there are some bugs that keep glitching me in evolution on 20.04). Dell only officially supports 18.04 and 20.04 on the precision 7750.

Also I am getting this warning when I try "sudo do-release-upgrade -d":

```
$ sudo do-release-upgrade -d
Checking for a new Ubuntu release
In /etc/update-manager/release-upgrades Prompt 
is set to never so upgrading is not possible.

```

So it seems Dell would prefer that we not do this. The ubuntu version I have installed is the pre-installed Dell version of 20.04 which includes some tweaks for their hardware, drivers, etc. 

I'm guessing it's best if I sit and wait for official support, does anyone happen to have tried this or otherwise tried upgrading in place the official Dell distributions?

I guess if I were to try to do d-release-upgrade, really the better thing to do would be a clean install of 22, but I'd rather not do that as apparently there are some issues with hardware not working properly if you're not on the official dell build (ymmv but I have little ability to troubleshoot anything that doesnt work out of the box). 

Thanks
Rabu

---

### Post by Impavidus on 2022-06-23
It says, prompt is set to never. You could change that. Will it work? I don't know. You could first try a live disk of 22.04.

Note that the release upgrade path from 20.04 to 22.04 hasn't been released yet. Although 22.04 has been released, the upgrade from 20.04 is still in development.

---

### Post by kurt18947 on 2022-06-23
> **Impavidus said:**
> It says, prompt is set to never. You could change that. Will it work? I don't know. You could first try a live disk of 22.04.

Note that the release upgrade path from 20.04 to 22.04 hasn't been released yet. Although 22.04 has been released, the upgrade from 20.04 is still in development.

Trying a live disk should tell you about hardware incompatibilities. As Impavidus says, there is no official path from 20.04 to 22.04 AFAIK. I understand that there will be once 22.04.1 is released, Canonical wants the dust to settle from 22.04 before recommending an inplace upgrade. Dell may want to test 22.04.1 before recommending 22.04.1.

---

### Post by grahammechanical on 2022-06-23
I purchased a laptop with Ubuntu 20.04 pre-installed. It came with an OEM kernel that over time was naturally upgraded to the generic kernel. The hardware kept working. You might benefit from reading about OEM kernels. It will put your mind at rest.

[https://wiki.ubuntu.com/Kernel/OEMKernel](https://wiki.ubuntu.com/Kernel/OEMKernel)

> The OEM kernel was used to be called OEM staging kernel, because the  delta in OEM kernel should all be merged to the generic kernel in the  next Ubuntu release, so it is essentially a staging code base.

> Before the kernel reaches end-of-life, all of the changes made to the  OEM kernel will be reviewed to make sure that the kernel in the next  Ubuntu release already has the changes it needs. For instance, a driver  we integrate in the OEM kernel should also exist in the next kernel.  This ensures users a smooth upgrade path &#8212; systems that upgrade to the  next Ubuntu release will not lose any functionalities or features, nor  have any new regression.

You may also find that a repository pointing to the supplier's internet address has been added to your /apt/sources.list file. That happened in my case. I am dual booting with 22.04 to test it out. As suggested above you can try the 22.04 live session or dual boot to see if all the hardware still works.

Regards

---

### Post by Ranbunta_Bantubunt on 2022-06-23
Thanks all. Great ideas. I didnt realize that there was no direct path from 20.04 to 22.04 yet. 

I think I will try a live image of 22.04 out of curiosity to see how it goes. It's a big proposition to do a clean install for me so probably will wait until there is an upgrade path from 20.04->22.04 provided by canonical before making the plunge but will be interesting to try the live disk to see if any issues crop up.

---

### Post by mIk3_08 on 2022-06-24
> **Ranbunta_Bantubunt said:**
> Thanks all. Great ideas. I didnt realize that there was no direct path from 20.04 to 22.04 yet.
I think I will try a live image of 22.04 out of curiosity to see how it goes. It's a big proposition to do a clean install for me so probably will wait until there is an upgrade path from 20.04->22.04 provided by canonical before making the plunge but will be interesting to try the live disk to see if any issues crop up.
If you can't wait to try it yourself can you do download it [here]("https://releases.ubuntu.com/22.04/") and have a install to your machine. Regards and Cheers.
[Click here]("https://releases.ubuntu.com/22.04/")
or here
```
https://releases.ubuntu.com/22.04/
```

---

