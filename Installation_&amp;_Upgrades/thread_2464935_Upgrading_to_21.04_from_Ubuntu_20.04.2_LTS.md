---
title: "Upgrading to 21.04 from Ubuntu 20.04.2 LTS"
date: 2021-07-16
forum: Installation &amp; Upgrades
---

### Post by makem2 on 2021-07-16
The reason I am upgrading is because my new build uses Intel UHD graphics 750 integrated  in the processor while the GFX cards are so expensive. I am unable to run No Man's Sky game. The symptoms are very very slow mouse movement making the game unplayable.

Extract from GitHub help:

The Intel UHD graphics 750 might be new enough that you will need to install the kernel for 20.04.3, which from [https://ubuntu.com/about/release-cycle](https://ubuntu.com/about/release-cycle) looks like it will be the same kernel which is shipping with Ubuntu 21.04 (which is a 5.11 kernel)

That is the only reason for upgrading and if someone has the knowledge to say that upgrading would not help I would be grateful.

If it is thought worthwhile trying this then is there a guide to prevent me messing up what has been a stable OS?

---

### Post by monkeybrain20122 on 2021-07-16
You can easily install a new kernel on Ubuntu 20.04 without upgrading your stable OS. I am running 5.11 on Ubuntu 20.04

You can either get it from [https://launchpad.net/~system76-dev/+archive/ubuntu/stable/+packages](https://launchpad.net/~system76-dev/+archive/ubuntu/stable/+packages), you don't need to have a system76 computer, just upgrade the kernel and then disable the ppa if you don't want to upgrade other stuffs like firmware

Or you can do it manually in a one off way, go to
[https://kernel.ubuntu.com/~kernel-ppa/mainline/v5.11/](https://kernel.ubuntu.com/~kernel-ppa/mainline/v5.11/)

create a folder and give it a name say Linux somewhere

Download the linux image, linux headers and linux modules debs for your architecture (I assume amd64) from link above and save them to your Linux folder

then
```

cd Linux #or /path/to/Linux if you created it somewhere else

sudo dpkg -i *.deb
```

then reboot

Of course you can finally compile from source, though not recommended.

**Edited:** If new kernel gives you problems then reboot into an older kernel, to boot into old kernel, tab ESC when boot and choose advanced option, choose older kernel say 5.8(?) Depending on your hardware it may not be ESC, better check with google. Once booted delete the new kernel stuffs. Easy way is to do it with synaptic, should install it if you haven't. 

```
sudo apt install synaptic
```

---

### Post by makem2 on 2021-07-16
Many thanks but when I looked at those it scared the stuffing out of me lol.

I thought it was just a matter of re-installing the file for 21.04 as I have a separate /home.

Maybe I better plod on as I am until next year.

Btw I do have synaptic as I rely on it.

---

### Post by monkeybrain20122 on 2021-07-16
> **makem2 said:**
> Many thanks but when I looked at those it scared the sxxit out of me lol.

I thought it was just a matter of re-installing the file for 21.04 as I have a separate /home.

Maybe I better plod on as I am until next year.

Btw I do have synaptic as I rely on it.

It is actually very easy and reversible. Try the second way if you don't want to add any ppa. I wouldn't trade in a stable OS for a beta with only a lifespan of 9 months.

---

### Post by CatKiller on 2021-07-16
If you want the 21.04 kernel, just install the hwe-edge metapackage. That's the 5.11 branch. hwe is the 5.8 branch, the 20.10 version. hwe will get the hwe-edge version later. Ubuntu's LTS releases get the same kernel as the interim releases through the Hardware Enablement Stack mechanism. 

If you want even newer than that, you don't need to get them from System76; Ubuntu [provides its own means](https://wiki.ubuntu.com/Kernel/MainlineBuilds) to get new upstream kernel versions.

---

### Post by grahammechanical on 2021-07-16
If you want to take the upgrade path then you must first upgrade 20.04 to 20.10 and then upgrade 20.10 to 21.04. Ubuntu 20.10 reaches end of life at the end of July 2021. After that the process get more complicated.

First run Software Updater to make sure 20.04 is up to date, Then, open Software & Updates>Updates tab and where it says Notify me of a new Ubuntu version click the down arrow and select For any new version. Now run Software Updater again and see if you get an offer to upgrade to 20.10. After you have reached 20.10 you should get an offer to upgrade to 21.04.

Regards

---

### Post by Impavidus on 2021-07-17
> **CatKiller said:**
> If you want the 21.04 kernel, just install the hwe-edge metapackage. That's the 5.11 branch. hwe is the 5.8 branch, the 20.10 version. hwe will get the hwe-edge version later. Ubuntu's LTS releases get the same kernel as the interim releases through the Hardware Enablement Stack mechanism. 
Which is as simple as running```
sudo apt install linux-generic-hwe-20.04-edge
```and reboot.

> **grahammechanical said:**
> If you want to take the upgrade path then you must first upgrade 20.04 to 20.10 and then upgrade 20.10 to 21.04. Ubuntu 20.10 reaches end of life at the end of July 2021. After that the process get more complicated.

If it works the same way as last time, a direct upgrade from 20.04 to 21.04 should be offered when 20.10 is dead. These upgrades appear somewhat less reliable though.

---

### Post by makem2 on 2021-07-17
> **monkeybrain20122 said:**
> It is actually very easy and reversible. Try the second way if you don't want to add any ppa. I wouldn't trade in a stable OS for a beta with only a lifespan of 9 months.

I would be happy with adding and later removing a ppa if I really needed to.

I think by your comment you suggest I could give it a go but better to wait so I will. That is the feeling in my water lol.

Thank you for your input.

---

### Post by makem2 on 2021-07-17
> **Impavidus said:**
> Which is as simple as running```
sudo apt install linux-generic-hwe-20.04-edge
```and reboot.



If it works the same way as last time, a direct upgrade from 20.04 to 21.04 should be offered when 20.10 is dead. These upgrades appear somewhat less reliable though.

Sorry, I missed that and the previous post. I will give it a try.

---

### Post by makem2 on 2021-07-17
> **grahammechanical said:**
> If you want to take the upgrade path then you must first upgrade 20.04 to 20.10 and then upgrade 20.10 to 21.04. Ubuntu 20.10 reaches end of life at the end of July 2021. After that the process get more complicated.

First run Software Updater to make sure 20.04 is up to date, Then, open Software & Updates>Updates tab and where it says Notify me of a new Ubuntu version click the down arrow and select For any new version. Now run Software Updater again and see if you get an offer to upgrade to 20.10. After you have reached 20.10 you should get an offer to upgrade to 21.04.

Regards

I used the process of upgrading method you suggest.

20.10 installed and upgrading to 21.04. all going fine ty.

---

