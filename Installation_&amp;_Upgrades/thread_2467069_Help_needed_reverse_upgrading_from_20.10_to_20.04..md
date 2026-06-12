---
title: "Help needed reverse upgrading from 20.10 to 20.04.3LTS"
date: 2021-09-15
forum: Installation &amp; Upgrades
---

### Post by whateverhahaha on 2021-09-15
Hi, Ubuntu Forum:

I need help "Reverse upgrade" from 21.04 to 20.04.3LTS.  I know it sounds strange, but I needed the 5.11 kernel from 20.10 so I initially installed it on my laptop when Ubuntu 20.04 was stuck on 5.4 kernel.  Now that the Ubuntu 20.04.3LTS had been released and the HWE kernel is also 5.11, I would prefer the 20.04.3LTS HWE 5.11 kernel now.

sudo do-release-upgrade doesn't allow me to do the 21.04 -> 20.04.3LTS upgrade without a clean install.  Any ideas or instructions?

Thanks in advance.

---

### Post by guiverc on 2021-09-15
Ubuntu 20.10 used the 5.8 kernel, it was Ubuntu 21.04 that used the 5.11 kernel.  You might want to clarify as your release & kernels don't match.

Upgrade tools are designed to upgrade forwards (to later software) and won't go backwards. 

You can *upgrade via re-install* (it's great especially for desktops) which allows you to go backwards, forwards or to the same release; and I use it upgrade systems from *groovy*/20.10 (*after it was released*) to switch to 20.04.2, then to *hirsute/*21.04, then as 20.04.3 got close to a release; switching to 20.04.3, then forward to *impish* (what will 21.10 on release).  I don't lose my *manually installed apps*, data files etc.   Alas you didn't say if it's desktop or server you're asking about.

---

### Post by Impavidus on 2021-09-15
The 5.11 kernel has been available on 20.04 since the release of 21.04 via the linux-generic-hwe-20.04-edge package. It was not available in the live session though.

---

### Post by whateverhahaha on 2021-09-15
Yeah, my bad, it is 21.04.  Sorry.  The story didn't change though, I was on 21.04's 5.11 kernel because of the AMD platform, and I need to "upgrade" to the 20.04.3LTS distro for some PPA compatibility(specifically the jonathonf zfs 2.1.0 ppa) since 20.04.3LTS finally has 5.11HWE.

The do-release-upgrade script does not take into account when the "LTS" branch release catch up to the "normal" releases in terms of kernels, and for people wishing to get "stability" once the LTS's delay in kernels got caught up, might want to upgrade to the previous LTS branch from a normal branch.

Any help?  I could wipe clean, and reinstall, but I would rather not do that on this system.

---

### Post by TheFu on 2021-09-15
You know that backup that you made before doing any major system changes - like moving releases?  I'm 100% positive you made that backup, right?
Just restore it.  Then you'll be back where you want.

If you didn't make a backup AND retain that backup, there isn't any magic. Sorry.  Programmers create upgrade tools. They don't make downgrade tools - especially without charging lots of money.

---

### Post by grahammechanical on 2021-09-15
The question I am asking is "Why?" 

One reason for staying on an LTS release is the direct upgrade path to the next LTS release. Which would be 22.04. You have upgraded but to what? Was it to 20.10 and then to 21.04? You have broken the LTS to LTS upgrade path. In a few months time you could, if you choose to, upgrade to 21.10 and then in May 2022 upgrade to Ubuntu 22.04.

It may not seem like it but there are now big differences between Ubuntu 20.04 and 20.10 and 21.04. It is not just the kernel that has been changed. There is also going to be a big difference between Ubuntu 20.04 LTS and Ubuntu 22.04 LTS. Some of us would recommend a fresh install as preferable to a online upgrade.

Re-installs wipe the OS clean. I would not believe anyone one who said that they had a script/app that would cleanly reverse upgrade Ubuntu.

Regards

---

### Post by whateverhahaha on 2021-09-18
The "Why" is pretty obvious.

For someone who first choose to install the latest non-LTS branch then want to "reverse upgrade" to the last LTS branch with HWE kernel obviously need the kernel for mostly hardware support.  I bought AMD renoir laptop in May 2020, and kernel 5.4 branch in the 20.04 LTS kernel does not support Renoir GPU.  So I needed 5.11 kernel based distro to fully take advantage of Renior.  When the time comes(usually after 6 months or so when the .3 release of 20.04.3LTS comes with HWE 5.11 kernel which pretty much optimizes Renoir's GPU drivers well enough, I would want to switch to the 20.04.3LTS HWE distro to get jonathonf/zfs 2.1.0 PPA support for example.  Most PPAs only support LTS branches, and the LTS kernels are way more stable than non-LTS branches.

So do you now see the need for a reverse non-LTS to lastLTS upgrade path?  It is mostly for people who stayed too cutting edge in terms of non-Nvidia GPUs mostly(Nvidia's binary drivers keeps up with kernel compiles very quickly, but the same can't be said for AMD or Intel.  

For example, when Intel's DG2 comes to market in Q1, 2022 which requires 5.15 kernel+, you would need a distro with 5.15 kernel+ to be able to get into the X window.  Considering the nonLTS is usually 3-6 months behind mainline, and LTS another 6 months behind non-LTS, you would have to wait a year or so for Ubuntu LTS branch to be able to use Intel DG2 for example.  So people who buy hardware 0day would probably want to go on the non-LTS branch first, and then "upgrade" to the LTS HWE 6 months later.  

It is a pretty valid upgrade path for the "do-release-upgrade" script in my mind.  First you need a distro that can at least run the newest GPUs, and once LTS HWE comes out, you need the stability and PPA support.

---

### Post by MAFoElffen on 2021-09-18
Simple. Do it just like a Server migration from one release to another.

- Backup your data.
- List out any progam packages you have installed. back up your configuration files for the network, installed apps, etc.
- Install clean 20.04.3 with HWE.
- Reinstall you app and config files.
- Restore your data.

There is always a backwards path, and you do have a sound reason for it. It just takes a bit of planning and work.

---

### Post by guiverc on 2021-09-18
> **whateverhahaha said:**
> 
The do-release-upgrade script does not take into account when the "LTS" branch release catch up to the "normal" releases in terms of kernels, and for people wishing to get "stability" once the LTS's delay in kernels got caught up, might want to upgrade to the previous LTS branch from a normal branch.


The `do-release-upgrade` handles 
(1) upgrading from one release to the next (ie. it'll upgrade a 21.04 system to 21.10 after 21.10 has been released and deemed *stable* for upgrades). 
(2) upgrades from one LTS (ie. 20.04) to the next LTS **after** the release of the .1 upgrade, ie. 20.04 can *release-upgrade* to 22.04.1.

Those are the intended upgrade paths for `do-release-upgrade`.  To the **next release OR** from one LTS** to the next LTS**

I mentioned the method via re-install (*I've performed it multiple times in the last day & a half with upgrades from lubuntu to ubuntu, back to lubuntu etc., and used it when I needed to QA-test focal.3 (ie. [20.04.3]("https://fridge.ubuntu.com/2021/08/27/ubuntu-20-04-3-lts-released/")) so impish boxes went back to focal; but given focal has been released the testing is currently all impish; with a couple of days of testing bionic ([18.04.6]("https://fridge.ubuntu.com/2021/09/17/ubuntu-18-04-6-lts-released/")) which has now been released so it's returned to impish; as stated I find it great with desktop system; use existing partitions but do **not ****format** to ensure this type of install is triggered*)

---

### Post by ActionParsnip on 2021-09-18
> **MAFoElffen said:**
> Simple. Do it just like a Server migration from one release to another.

- Backup your data.
- List out any progam packages you have installed. back up your configuration files for the network, installed apps, etc.
- Install clean 20.04.3 with HWE.
- Reinstall you app and config files.
- Restore your data.

There is always a backwards path, and you do have a sound reason for it. It just takes a bit of planning and work.

2nd step...verify the backup can be restored from ;)

---

