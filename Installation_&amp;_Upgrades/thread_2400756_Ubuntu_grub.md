---
title: "Ubuntu grub"
date: 2018-09-10
forum: Installation &amp; Upgrades
---

### Post by mandeepkotti on 2018-09-10
I installed Ubuntu 18.04.1 LTS on my system along with Windows 10 as dual boot. The Ubuntu worked fine for few days, but last there there were some updates in UBUNTU which I allowed the download and install. During that, my Ubuntu freeze with no mouse and keyboard working, so ultimately I had to force shutdown the system holding power key.
During next boot to the system, the system automatically got booted to Windows 10 with no GNU GRUB Boot loader missing. I tried few solutions from web, but nothing worked for me. I'll post details of solutions I already tried.
I tried boot repair using temporary booting of Ubuntu using flash drive with but it also got failed and resulted in **dpkg** error.

```
sudo add-apt-repository ppa:yannubuntu/boot-repair
sudo apt-get update
sudo apt-get install -y boot-repair && boot-repair
```

Is there any possible solution to restore Ubuntu without loosing data.

I tried to remove Ubuntu from my machine with fixing Windows boot loader from CMD, but it's also showing _*Access Denied*_ using** bootrec /fixboot **command.

Currently Windows is working fine on system but  it's taking time to load up as I messed with boot settings by installing Ubuntu.

Any possible method to restore Ubuntu?
If not, how to fix my Windows System, so that I can install Ubuntu again.

---

### Post by westie457 on 2018-09-10
What was the dpkg error?
Try again with the Live USB run the commans from your post and if you get a dpkg error try running ```
sudo dpkg --configure -a
```when that has finished without error then try ```
boot-repair
```Go for the 'create Report'button and post the generated link here. Do **NOT **attempt any repairs yet.

The **bootrec **commands are usually run in a CMD in Windows Recovery only.
The correct commands for Win 10 are```
bootrec /fixboot
bootrec /scanos
bootrec /rebuildbcd
```for a UEFI installation.
Please let us see the report for further advice.

---

