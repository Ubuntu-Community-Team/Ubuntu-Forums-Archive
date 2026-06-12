---
title: "Serious issue?"
date: 2010-02-10
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by gjoellee on 2010-02-10
This happened with the latest updates (5min ago) Take a look here:

```
udo dpkg --configure -a
Setting up initramfs-tools (0.92bubuntu64) ...
update-initramfs: deferring update (trigger activated)

Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-2.6.32-12-generic
cpio: ./lib/udev/firmware.sh: Cannot stat: No such file or directory
update-initramfs: failed for /boot/initrd.img-2.6.32-12-generic
dpkg: subprocess installed post-installation script returned error exit status 1

```Is this serious, or can I just ignore it? Anyway, unless this error get fixed, I won't be able to run dpkg.

---

### Post by philinux on 2010-02-10
> **gjoellee said:**
> This happened with the latest updates (5min ago) Take a look here:

```
udo dpkg --configure -a
Setting up initramfs-tools (0.92bubuntu64) ...
update-initramfs: deferring update (trigger activated)

Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-2.6.32-12-generic
cpio: **./lib/udev/firmware.sh: Cannot stat: No such file or directory**
update-initramfs: failed for /boot/initrd.img-2.6.32-12-generic
dpkg: subprocess installed post-installation script returned error exit status 1

```Is this serious, or can I just ignore it? Anyway, unless this error get fixed, I won't be able to run dpkg.

Same here with last update. There must be a fix to a script else no one can update after this.

---

### Post by jppr on 2010-02-10
> **gjoellee said:**
> This happened with the latest updates (5min ago) Take a look here:

```
udo dpkg --configure -a
Setting up initramfs-tools (0.92bubuntu64) ...
update-initramfs: deferring update (trigger activated)

Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-2.6.32-12-generic
cpio: ./lib/udev/firmware.sh: Cannot stat: No such file or directory
update-initramfs: failed for /boot/initrd.img-2.6.32-12-generic
dpkg: subprocess installed post-installation script returned error exit status 1

```Is this serious, or can I just ignore it? Anyway, unless this error get fixed, I won't be able to run dpkg.

This is serious, i have same. synaptic and update-manager don´t work anymore and everytime when try update system in consol comes that error.

---

### Post by gjoellee on 2010-02-10
> **jppr said:**
> This is serious, i have same. synaptic and update-manager don´t work anymore and everytime when try update system in consol comes that error.

I made a duplicate post, check here: [http://ubuntuforums.org/showthread.php?p=8804672#post8804672](http://ubuntuforums.org/showthread.php?p=8804672#post8804672)

---

### Post by philinux on 2010-02-10
Looks like the full stop in front of the file name as locate finds the file.

```
locate firmware.sh
/lib/udev/firmware.sh



```

---

### Post by tito_torrisi on 2010-02-10
> sudo dpkg --configure -a
Setting up initramfs-tools (0.92bubuntu64) ...
update-initramfs: deferring update (trigger activated)

Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-2.6.32-12-generic
cpio: ./lib/udev/firmware.sh: Cannot stat: No such file or directory
update-initramfs: failed for /boot/initrd.img-2.6.32-12-generic
dpkg: subprocess installed post-installation script returned error exit status 1

Well well...

---

### Post by zika on 2010-02-10
> **philinux said:**
> Looks like the full stop in front of the file name as locate finds the file.

```
locate firmware.sh
/lib/udev/firmware.sh



```You have to do **sudo updatedb**. That is state before Your upgrade... You **had** that file, as we all did...

---

### Post by gjoellee on 2010-02-10
> **zika said:**
> You have to do **sudo updatedb**. That is state before Your upgrade... You **had** that file, as we all did...


I ran:
```
sudo updatedb 
locate firmware.sh 
```and

```
locate firmware.sh 
```does not give any output

Confirmed!

---

### Post by kklimonda on 2010-02-10
recent update to udev has replaced /lib/udev/firmware.sh with /lib/udev/firmware binary - to get it to work you have to apply patch from [http://launchpadlibrarian.net/39011493/udev-firmware.patch](http://launchpadlibrarian.net/39011493/udev-firmware.patch) and regenerate initramfs (dpkg --configure -a should be enough as it was interrupted).

---

### Post by zika on 2010-02-10
> **kklimonda said:**
> recent update to udev has replaced /lib/udev/firmware.sh with /lib/udev/firmware binary - to get it to work you have to apply patch from [http://launchpadlibrarian.net/39011493/udev-firmware.patch](http://launchpadlibrarian.net/39011493/udev-firmware.patch) and regenerate initramfs (dpkg --configure -a should be enough as it was interrupted).Great hint! Thank You!

---

### Post by gjoellee on 2010-02-10
> **zika said:**
> Great hint! Thank You!

I never run patches, how do I patch this?

---

### Post by zika on 2010-02-10
[http://ubuntuforums.org/showpost.php?p=8804856&postcount=25](http://ubuntuforums.org/showpost.php?p=8804856&postcount=25)> **gjoellee said:**
> I never run patches, how do I patch this?

---

### Post by michaelmartin007 on 2010-02-10
Hi,

I upgrade the system and I had the same problem. I was following
all thread. I have been following every one of you because I was in same situation. 
This is only to give thanks to all of you for the help. Finally I 
followed the steps for applying the path and it work.

Thanks for help.

---

### Post by itsjustarumour on 2010-02-10
> **zika said:**
> [http://ubuntuforums.org/showpost.php?p=8804856&postcount=25](http://ubuntuforums.org/showpost.php?p=8804856&postcount=25)

Fixed it for me - thanks Zika!  :KS

---

### Post by itsjustarumour on 2010-02-10
> **michaelmartin007 said:**
> Hi,

I upgrade the system and I had the same problem. I was following
all thread. I have been following every one of you because I was in same situation. 
This is only to give thanks to all of you for the help. Finally I 
followed the steps for applying the path and it work.

Thanks for help.

Did you make sure you ran

> sudo dpkg --configure -a

in the terminal again after amending the file?

---

### Post by zika on 2010-02-10
> **itsjustarumour said:**
> Fixed it for me - thanks Zika!  :KSCredit is not mine, I just linked to "my" thread" where answer was given by some other member. But, I'm glad I was able to help...

---

