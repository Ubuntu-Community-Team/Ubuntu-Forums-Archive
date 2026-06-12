---
title: "Using previous kernels in grub boot options at startup"
date: 2011-12-09
forum: Installation &amp; Upgrades
---

### Post by unckybob on 2011-12-09
How can I download previous kernels and incorporate them into the grub boot options that you get at boot time?

---

### Post by josephmills on 2011-12-09
go get the kerenel that you like after installing run 
```
sudo update-grub
```
reboot select kerenel

---

### Post by josephmills on 2011-12-09
I guess that I did not say enough 
one figure out kerenel that you like 
then either open synaptic and look for it or go to ubuntu mainline 
[http://kernel.ubuntu.com/~kernel-ppa/mainline/](http://kernel.ubuntu.com/~kernel-ppa/mainline/)
Pick the kerenel that you like.
lets say 2.6.35.12[http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.35.12-maverick/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.35.12-maverick/)
download the three files that pertain to you. 
ex. say I am 32 bit I would download these three files 

	linux-headers-2.6.35-02063512-generic_2.6.35-02063512.201111232104_i386.deb


linux-headers-2.6.35-02063512_2.6.35-02063512.201111232104_all.deb

	linux-image-2.6.35-02063512-generic_2.6.35-02063512.201111232104_i386.deb


**Then make a folder in your home dir called linux and place all three files in there **

open terminal 
```
cd ~/linux/
```
```
sudo dpkg -i lin* 
```
then 
```
sudo update-grub
```
and reboot 
hope this helps

---

### Post by bogan on 2011-12-09
Hi!, [B]josephmills
[/B] 
If I use the method you suggested to unckylob in "Re: Using previous kernels in grub boot options at startup", will:```
sudo dpkg -i lin*
```  install the new version to a new partition?
 Or alongside the current version in the same partition? 
If the later, it would allow me to force an installation without making a new partition, which a Live Cd insists on doing, and which I do not want; I have not been able to find a way to do so, up to now.
 {*I assume it will not overwrite anything.*}
Also will it work for newer versions, as well as for previous ones?
Thanks in advance.

CHAO![B] , bogan.
[/B]

---

### Post by unckybob on 2011-12-09
Thanks Joseph, 

I don't see the kernel I like.

2.6.38-13-generic with natty. 

Can you help?

---

### Post by unckybob on 2011-12-10
I searched around the net for the proper packages and found them. It went just fine. It seems that you don't have to use the "update-grub" command. They are somehow added to the grub boot list anyway. Thanks so much.

---

### Post by josephmills on 2011-12-13
> **unckybob said:**
> I searched around the net for the proper packages and found them. It went just fine. It seems that you don't have to use the "update-grub" command. They are somehow added to the grub boot list anyway. Thanks so much.

Yes that is correct dpkg handles all of that for you(SOMETIMES)I just like to put it down just in case the debian package manager does not have that built into its install script. At any rate glad to see that you got it worked out
Joseph

---

