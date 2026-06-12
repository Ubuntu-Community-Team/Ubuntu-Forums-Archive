---
title: "Update to 14.04  3.13.0-92 - Nvidia driver unsigned problem"
date: 2016-07-16
forum: Installation &amp; Upgrades
---

### Post by Tom McD on 2016-07-16
Yesterday's update to 14.04 ( 3.13.0-92 ) requires that the kernel video driver be signed.
I cannot turn off secure boot as this is a dual-boot machine, Win 10 won't boot if secure boot is off.
The GUI logon screen boots to low-resolution, it loops on valid password entry.

After about a day of googling, am unable to determine which Nvidia drivers are signed,
which are not signed, and have not been able to find a signed driver.

Graphics card is GTX-660, the drivers tried are:  340.96   and  352.63.  Rebooted to 3.13.0-91
and everything works fine (both 340.96 and 352.63).   352.63 is listed as 'recommended driver'
by the GUI.

Is there a place to find a signed nvidia driver?  If not, what alternatives are available?  If I ever
update to 16.04 apparently will have this same issue.

One search showed how to use nvidia-install which seems to be a script to install nvidia drivers,
and optionally allow signing from a MOK key.  But that script is not present on this machine.
No such options for signing appear when using the 'Software & Updates' Additional Drivers GUI to
 update drivers.

-- Tom McDermott

---

### Post by grahammechanical on 2016-07-16
My advice would be to continue loading the 3.13.0-91 kernel as that gets you to a working desktop. Previous kernels are not removed exactly for situations like this. In a few days there may be another kernel upgrade that replaces kernel 3.13.0-92 and fixes this problem.

Ubuntu 16.04 is on the 4.4 series of Linux kernels. It is not necessarily so that you will have this problem when you upgrade to 16.04. You could always install 16.04 into another partition and test it out first before upgrading.

Regards

---

### Post by wildmanne39 on 2016-07-17
I have ubuntu 16.04 and windows 10 both working with secure boot off, but I also have signed a driver for the new kernel and got it to work, here is the directions just include the drivers name where <modinfo -n driver> it is the name of your driver.
[https://ubuntuforums.org/showthread.php?t=2304607&page=9&p=13505749#post13505749](https://ubuntuforums.org/showthread.php?t=2304607&page=9&p=13505749#post13505749)
Post 81 is the directions you need.

---

### Post by Tom McD on 2016-07-17
Thanks.   Now the question - which is(are) the file(s) to be signed for the Nvidia video driver?
Can just the file(s) be signed, or something deeper involved?
I removed 3.13.0-92 (using Synaptic), so -91 is the latest (because it boots).

Related question:  is the Noveau driver signed?  If so could it be used instead?    

$ sudo find / -name nvidia*.ko
/var/lib/dkms/nvidia-352/352.63/3.13.0-91-generic/x86_64/module/nvidia_352.ko
/var/lib/dkms/nvidia-352/352.63/3.13.0-91-generic/x86_64/module/nvidia_352_uvm.ko
/lib/modules/3.13.0-88-generic/kernel/drivers/video/nvidia/nvidiafb.ko
/lib/modules/3.13.0-87-generic/kernel/drivers/video/nvidia/nvidiafb.ko
/lib/modules/3.13.0-91-generic/updates/dkms/nvidia_352.ko
/lib/modules/3.13.0-91-generic/updates/dkms/nvidia_352_uvm.ko
/lib/modules/3.13.0-91-generic/kernel/drivers/video/nvidia/nvidiafb.ko
/lib/modules/3.13.0-83-generic/kernel/drivers/video/nvidia/nvidiafb.ko
/lib/modules/3.13.0-86-generic/kernel/drivers/video/nvidia/nvidiafb.ko
/lib/modules/3.13.0-85-generic/kernel/drivers/video/nvidia/nvidiafb.ko

-- Tom

---

### Post by wildmanne39 on 2016-07-17
It is the exact driver name that is loaded for your device that has to be signed, I think it is just called nvidia driver but I could be wrong if someone that has the driver loaded please check it with:
```
lsmod
```
and let us know.

---

### Post by wildmanne39 on 2016-07-17
Yes the  Noveau driver is signed and you can probably use it, just have to see how you like it, it has been about three years since I tried it and it had come a long way.

---

### Post by Tom McD on 2016-07-18
Thnaks for all the help !

lsmod lists:
...
nvidia               8642880  44 
...

I stopped using Noveau several years ago because it lacked support for OpenCL, which several apps need.
Last I heard it still doesn't support, but maybe that has changed.

---

### Post by wildmanne39 on 2016-07-18
All you need to do is follow the directions and insert nvidia where it says modinfo -n nvidia.

---

### Post by Tom McD on 2016-07-19
Successfully created the MOK key and enrolled it in the UEFI.

But the command to sign the nvidia driver fails with :
modinfo: ERROR: Module nvidia not found.


-- Tom

---

### Post by wildmanne39 on 2016-07-19
Please post the exact command here that you used.
Thanks

---

### Post by Tom McD on 2016-07-19
sudo /usr/src/linux-headers-$(uname -r)/scripts/sign-file sha256 ./MOK.priv ./MOK.der $(modinfo -n nvidia)

---

### Post by wildmanne39 on 2016-07-19
Did you run the next command and create a password then reboot and see the blue screen?

---

### Post by Tom McD on 2016-07-19
1. I ran the MOK key generation and enrollment sucessfully. That's the one where I created the password and went through the bluescreen.
Then it rebooted when done. Then came back up in Ubuntu and verified the key is installed with mokutil.

2. Then tried to sign the nvidia driver.  That's where the error occurred.   If i just run the modinfo command, it doesn't
find anything called nvidia either.

-- Tom

---

### Post by wildmanne39 on 2016-07-19
When it rebooted the key should have been signed but you may have to run:
```
sudo modprobe nvidia
```
If that does not work you can also turn secure boot off and it will not check for security but it is not preferred.

---

### Post by Tom McD on 2016-07-19
Thanks for the help.   Turns out that it wanted modinfo -n nvidia_352
lsmod  just called it nvidia, but trying "modprobe nvidia" gave the error message  could not insert 'nvidia_352'
which is how I guessed it is called nvidia_352 but not displayed that way.  The sign command completed.
Now to re-install 3.13.0-92 and see if it works.

-- Tom



-- Tom

---

### Post by wildmanne39 on 2016-07-19
Reinstall ubuntu? or the driver? If you reinstall ubuntu you will have to redo the signing module again.

---

### Post by Tom McD on 2016-07-19
Well, not so good.  3.13.0-92 doesn't think the nvidia driver is signed.

-- Tom

---

### Post by Tom McD on 2016-07-19
Thanks again for all your help tonight, Wild Man.

It was not a re-install of ubuntu, just re-installation of the 14.04 3.13.0-92 packages.
Brought up -92, since the GUI can't start or login, brought up tty1, logged in and re-signed nvidia_352, then rebooted,
but that did not work either.

Apparently I must be signing the wrong file for the driver.

-- Tom

---

