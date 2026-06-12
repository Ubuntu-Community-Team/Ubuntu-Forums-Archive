---
title: "Cannot get linux-headers-2.6.32-20"
date: 2010-04-12
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by Cavsfan on 2010-04-12
I got a bunch of updates this morning and when I tried "sudo apt-get dist-upgrade", it said there was a new kernel available. 
When I gave it the "y" to install it I received this error:

Err [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid/main linux-image-2.6.32-20-generic 2.6.32-20.29
  404  Not Found [IP: 91.189.88.40 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/l/linux/linux-image-2.6.32-20-generic_2.6.32-20.29_amd64.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/l/linux/linux-image-2.6.32-20-generic_2.6.32-20.29_amd64.deb)  404  Not Found [IP: 91.189.88.40 80]
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?

Just wondering if anyone else is having the same issue and if I should just be patient or what?

Thanks

---

### Post by grandtoubab on 2010-04-12
> **Cavsfan said:**
> I got a bunch of updates this morning and when I tried "sudo apt-get dist-upgrade", it said there was a new kernel available. 
When I gave it the "y" to install it I received this error:

Err [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid/main linux-image-2.6.32-20-generic 2.6.32-20.29
  404  Not Found [IP: 91.189.88.40 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/l/linux/linux-image-2.6.32-20-generic_2.6.32-20.29_amd64.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/l/linux/linux-image-2.6.32-20-generic_2.6.32-20.29_amd64.deb)  404  Not Found [IP: 91.189.88.40 80]
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?

Just wondering if anyone else is having the same issue and if I should just be patient or what?

Thanks
same but we are lucky because that kernel is bad. read this forum too many problems with 2.6.32-20 :lolflag:

---

### Post by Nightstrike2009 on 2010-04-12
I think i have that kernel i got it via update manager as a regular update, any idea how to get rid of it if its bad? 

My installed kernels are:

2.6.32-20 Generic
2.6.32-19 Generic

Both seem to run OK on mine (I am using 32bit version)

---

### Post by dino99 on 2010-04-12
> **Nightstrike2009 said:**
> I think i have that kernel i got it via update manager as a regular update, any idea how to get rid of it if its bad? 

PS: Sorry for lack of technical info I am a dual booter and using the M$ partition at the moment i have two kernels one ending in 19 the other in 20.

use the latest as it fixed a bunch of bugs but introduce at least one more: we dont see grub menu automaticaly (have to press shift key after bios process to see it and select the kernel we want to boot with)

If you wait a little, there are several important new releases waiting to come into repo: kernel, update-manager, mountall, jockey

---

### Post by aviramof on 2010-04-12
i think there was a problem with this kernel and they pulled it a few hours ago it was possible to find it in synaptic but the link was broken now he's not there anymore and further more this kernel crashed for me very fast and i was forced to remove it lucky me i still had 2.6.33 kernel ha ha ha.:)

---

### Post by philinux on 2010-04-12
I get this in my chroot.

The following packages have been kept back:
  linux-generic linux-headers-generic linux-image-generic

So I guess I'll wait for a fix before rebooting.

Glad I saW this thread.

---

### Post by aviramof on 2010-04-12
> **Nightstrike2009 said:**
> I think i have that kernel i got it via update manager as a regular update, any idea how to get rid of it if its bad? 

My installed kernels are:

2.6.32-20 Generic
2.6.32-19 Generic

Both seem to run OK on mine (I am using 32bit version)

you can get rid of it like this

```
sudo apt-get remove --purge linux-image-2.6.32-20-generic
```

---

### Post by Cavsfan on 2010-04-12
I do like[COLOR=Blue] **_Ranch Hand's_**[/COLOR] way of doing things!
After entering this command in terminal "sudo apt-get update" it displayed all of this:

The following packages have been kept back:
  linux-generic linux-headers-generic linux-image-generic
The following packages will be upgraded:
  libtag1-vanilla libtag1c2a python-papyon telepathy-butterfly update-manager update-manager-core update-manager-kde xserver-common xserver-xorg-core
9 upgraded, 0 newly installed, 0 to remove and 3 not upgraded.

Then after entering this command - "sudo apt-get dist-upgrade" the new header came up:
The following NEW packages will be installed:
  linux-headers-2.6.32-20 linux-headers-2.6.32-20-generic
The following packages have been kept back:
  linux-generic linux-image-generic
The following packages will be upgraded:
  linux-headers-generic
1 upgraded, 2 newly installed, 0 to remove and 2 not upgraded.

I use Update Manager to see if there are updates to be gotten and now after the updates, 
Update Manager shows only 2 grayed out items (linux-generic and linux-image-generic)

I am going to reboot now and see what happens.

---

### Post by alexsimps on 2010-04-12
same thing "Calculating upgrade... Done
The following packages have been kept back:
  linux-generic linux-image-generic
0 upgraded, 0 newly installed, 0 to remove and 2 not upgraded." I will also restart and see...

---

### Post by Cavsfan on 2010-04-12
I am still running kernel 19, although I thought 20 installed. :confused:

Everything looks good, but I am confused.

---

### Post by Cavsfan on 2010-04-12
> **philinux said:**
> I get this in my chroot.

The following packages have been kept back:
  linux-generic linux-headers-generic linux-image-generic

So I guess I'll wait for a fix before rebooting.

Glad I saW this thread.

I am glad I helped! I believe this is a first for me - helping someone else or at least contributing! :D

---

### Post by alexsimps on 2010-04-12
Everything also seems fine and also running 2.6.32-19

---

### Post by ronparent on 2010-04-12
2.6.32-20 apparently is back on. I inadvertently downloaded and booted to it less than 30 min ago. Seem to be running fine!

---

### Post by linusr on 2010-04-12
> **ronparent said:**
> 2.6.32-20 apparently is back on. I inadvertently downloaded and booted to it less than 30 min ago. Seem to be running fine!

2.6.32-20 is back on, installing...

---

### Post by tokyobadger on 2010-04-13
I was wondering why I got the same kernel version again - thought the repos were wrong until I saw this thread. I think I ran for about 24 hours no probs (amd64) on the first iteration of 2.6.32-20. Updated now.

---

### Post by Cavsfan on 2010-04-13
Yes, I am good too now. I got some updates this morning and installed the rest of the kernel and a bunch of other stuff.

Life is good! :guitar:

---

