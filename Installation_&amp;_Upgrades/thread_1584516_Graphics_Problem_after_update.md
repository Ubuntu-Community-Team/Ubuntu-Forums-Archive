---
title: "Graphics Problem after update"
date: 2010-09-29
forum: Installation &amp; Upgrades
---

### Post by Kyluke on 2010-09-29
hey guys,
I have just updated my installation of ubuntu 10.04 and now my graphics are all messed up. The only thing that works are the generic drivers and not the ati drivers. Any ideas?

Please help I am really sick of not knowing after every update whether my pc will be fine or not.

If this does not work I am switching back to windows because it does not have these stupid yet annoying errors

---

### Post by Carole S on 2010-09-29
I have the same problem.  Updated last night, then restarted and found myself in Terminal Mode.  I am unable to get into the desktop and I think the cause is someting to do with my NVIDIA driver.

I am running in 64bit mode

This is not the first time that this has happened with 10.04 and I really need reliability.

I have lost work, which I now cannot access.  Grrrrrrrhhhhhh!:confused:

---

### Post by TBABill on 2010-09-29
Ok, just a couple questions. When it was working before was it using the proprietary ATi driver or the open source ATi driver? Have you tried to uninstall/reinstall the fglrx driver (if that's what you use) via Synaptic? You'll probably have to reboot if you try that method.
 
This is a minor issue that can be fixed. No reason to jump ship quiet yet.
 
Was this a normal system update (security or package updates) or an upgrade from 9.10 to 10.04? Just making sure I understand your issue clearly and how the problem happened.

---

### Post by Kyluke on 2010-09-29
yeah sorry just pretty angry, I won't go back to windows.

Well it was a normal security update. The drivers are the ones from the ati website (so guessing the open source drivers)

After a normal update form update manager and a reboot it always says that fglrx has failed to load and I have to switch to generic drivers and restart. I have reinstalled the drivers and restarted several times now.

---

### Post by Kyluke on 2010-09-29
After the installation of the ATI drivers it tells me there was a failure in installing part of the DKMS

Here is maybe some useful info (log):

Creating symlink /var/lib/dkms/fglrx/8.771/source ->
                 /usr/src/fglrx-8.771

DKMS: add Completed.

Kernel preparation unnecessary for this kernel.  Skipping...

Building module:
cleaning build area....
cd /var/lib/dkms/fglrx/8.771/build; sh make.sh --nohints --uname_r=2.6.32-25-generic --norootcheck.....(bad exit status: 1)
0
0
[Error] Kernel Module : Failed to build fglrx-8.771 with DKMS
[Error] Kernel Module : Removing fglrx-8.771 from DKMS

------------------------------
Deleting module version: 8.771
completely from the DKMS tree.
------------------------------
Done.
[Reboot] Kernel Module : update-initramfs

---

### Post by Handssolow on 2010-09-29
Not sure if this is the best thread but I've just updated the kernel and got a graphics problem. It isn't working automatically when the kernel is updated to 2.6.32-25-generic-pae or if I chose recovery mode and low res graphics.

Eventually I got into grub at boot and chose the previous kernel 2.6.32.24-generic-pae. Fortunately a working gui appears thought I note that I am still with the NVIDIA recommended driver with this older kernel.

What next, remove the proprietary NVIDIA driver and see which kernel delivers a gui?

---

### Post by Handssolow on 2010-09-29
Booting with the older kernel 2.6.32.24.generic-pae then I removed the NVIDIA driver. A reboot brought up the new kernel 2.6.32.25-generic-pae but in low res graphics. Selected Hardware Driver which was downloaded and installed. A reboot and all is working with new kernel and NVIDIA driver.

Say after me-
I must remember to remove the proprietary graphics driver before updating the kernel.

Ah it takes me back to the old days with Dapper Drake.

---

### Post by Kyluke on 2010-09-29
for me it does not help

---

### Post by Kyluke on 2010-09-29
> **Handssolow said:**
> 
Ah it takes me back to the old days with Dapper Drake.

You see it's supposed to be better

---

### Post by crl0901 on 2010-09-29
I had an issue with 10.04 updates and ATI drivers.  This is the bug listing they gave me.  Haven't tried it yet but there might be some useful information for your problem:

[https://bugs.launchpad.net/ubuntu/+source/fglrx-installer/+bug/642518](https://bugs.launchpad.net/ubuntu/+source/fglrx-installer/+bug/642518)

They mention a hotfix that ATI issued.  Might want to check into that.  May I also suggest doing a full system backup with Remastersys before doing major updates.  Doing this, I was able to restore my system perfectly to the state it was before the update.

---

### Post by TBABill on 2010-09-29
Did you install the driver from the ATi website because the drivers in the repository would not work? Or a functionality the existing ones did not have? One of the issues encountered when installing from outside the repositories is update issues. Because they are not part of the Ubuntu system or installed via Synaptic, the system may not recognize the driver and it makes other changes to the system that can bork an outside piece of software (even though it's a driver). You probably encountered it when the kernel was updated because your changes to the previous kernel were lost in the new one.
 
Can you revert to the old kernel at startup and see if you work fine? Just click down to the prior kernel at the grub2 screen and boot from it? Or did you remove the old kernel? Just trying to think of other possibilities :)

---

### Post by efflandt on 2010-09-29
Having to recompile/reinstall video drivers after a kernel update (or possibly other updates like the X server) is one of the risks you take when you manually install drivers from sources other than other than default video drivers or drivers installed through System > Administration > Hardware Drivers or other packages for your Ubuntu version.  Ubuntu is not necessarily going to know how to update things not installed from its packages.

I have not had any trouble with nvidia proprietary drivers (195) activated from Hardware Drivers in 64-bit 10.04.  Judging from 10.10 beta, Hardware Drivers in 10.10 when it is released will use a newer nvidea version (256) assuming your card is supported by that.

My older desktop with legacy ATI X1300 is no longer supported by the ATI proprietary drivers, but it works with default drivers.  Although, in 64-bit 10.04 I had to disable kms with **nomodeset** kernel boot parameter for suspend/hibernate to work.  I didn't do much testing of 64-bit 10.10 beta on the old PC yet other than to make sure that it booted fine from USB hard drive with default video drivers.

---

### Post by Kyluke on 2010-09-29
I have installed my ATI drivers about 4 different ways and nothing has helped.
Guess I will have to wait for 10.10

---

### Post by lunix- on 2010-09-29
Same problem here,   but the bug was easy to fix, luckily.  I got some help on freenode #ati from LordHavoc  (thanks LordHavoc for saving my fglrx :p)

What I did was: 


Replace contents in **/var/lib/dkms/fglrx/8.771/source/kcl_ioctl.c** with the contents on this web page:
[http://launchpadlibrarian.net/55867668/kcl_ioctl.c](http://launchpadlibrarian.net/55867668/kcl_ioctl.c)

Then:
sudo **dpkg --configure fglrx**

And then after ' **sudo reboot** ' everything working as before :)

---------------
Im on Catalyst 10.5 and use HD4850

Bug is explained better on this site:
[https://bugs.launchpad.net/ubuntu/+source/fglrx-installer/+bug/641890](https://bugs.launchpad.net/ubuntu/+source/fglrx-installer/+bug/641890)

Good luck everybody :)


EDIT: Today I got this fix in my Update Manager,  so shouldn't be necessary to do the steps above..   Good work community! :)

---

### Post by Kyluke on 2010-09-30
Unfortunetly that didn't work for me. When I install fglrx it installs version 8.723.1. I tried nonetheless with your suggestion but nothing changed instead I got errors such as fglrx already configured.

It always tells me dkms error, I just think that dkms is broken. I tried reinstalling it but that didn't help. Any advice?

---

### Post by Russell Burrows on 2010-09-30
Three things that work for me:

Never, ever jump on updates.
If it aint broke then dont fix it.
Wait 90 days until upgradeing to a newer version package.

---

### Post by Handssolow on 2010-09-30
Well said but you assume that others will have sorted the out problems by the time you're ready to do the update.

---

### Post by jmcdougall on 2010-10-01
My computer updated today and I am having the same problem.  My computer uses Intel's integrated graphics and have not seen anything about that particular combination here.  Any help with Intel integrated graphics is appreciated.
John

---

### Post by Kyluke on 2010-10-01
I personally think the problem lies with DKMS

---

