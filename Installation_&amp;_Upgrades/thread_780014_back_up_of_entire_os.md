---
title: "back up of entire os"
date: 2008-05-03
forum: Installation &amp; Upgrades
---

### Post by eskay_karthik on 2008-05-03
I have a HP laptop with dual boot, Vista and Ubuntu.
My vista is creating problems and I need to format it. Since I have only a recovery disk, I dont know whether my Ubuntu drive will get formatted too. So I need to create a back-up of ubuntu. When I installed ubuntu, I spent loads of time configuring it, the visuals and sound cards and apache and stuff. I cant afford to reinstall ubuntu again and configure it from the beginning.

Is there a way to create a back up the entire ubuntu ??

eskay

---

### Post by scragar on 2008-05-03
[http://ubuntuforums.org/showthread.php?t=35087](http://ubuntuforums.org/showthread.php?t=35087)

for the lazy: ```
tar cvpzf backup.tgz --exclude=/proc --exclude=/lost+found --exclude=/backup.tgz --exclude=/mnt --exclude=/media --exclude=/dev --exclude=/sys /
```

your really want to exclude /media and /dev, since these are not so much parts of your OS, as other devices.

:P

---

### Post by eskay_karthik on 2008-05-03
thanks loads .... could you also tell me how to reinstall the grub ???

---

### Post by scragar on 2008-05-03
it's easiest from a live CD, you just double check that the boot flag is on the linux partition, then run```
sudo grub
```
and from inside grub find the HD number and partition for ubuntu:
```
find /boot/grub/stage1
```result = something like ```
(hd0,1)
```
root to it:```
root (**hd0,1**)
```
then run setup:
```
setup (**hd0**)
```
editing things as required(note that setup can take either just the hd reference, or the hd+partition ref, don't use the partition ref unless required though)

---

### Post by eskay_karthik on 2008-05-03
Copying the contents of my grub folder present now and using it as a reference to edit later on .... will this be easier ??? because at present my grub gives 5 options ... Ubuntu, Ubuntu recovery, Ubuntu memtest, Vista, Vista recovery....

---

### Post by scragar on 2008-05-03
I don't think your grub settings would change, all you would have to do is restore it to the hd after it get's removed(when you install vista it will be removed).

---

### Post by eskay_karthik on 2008-05-03
Thanks.
Now , i hav one more small doubt..
Can I upgrade to 8.04 without changing the configuration settings ??? 
The most important things I spent days together are getting the sound to work, then the sound recorder, the webcam, installing php, apache server and mysql, compiz visuals ... Will the upgrade affect these in any way ???

---

### Post by scragar on 2008-05-03
no, you're backing up these settings with the rest of your OS.

---

### Post by eskay_karthik on 2008-05-03
backing up is cool . I understood ... but while upgrading ?? Nothing will happen to the above mentioned settings rite ?? I will upgrade directly from internet and not from any cd ..

---

### Post by scragar on 2008-05-03
reagardless of how your upgrading be sure to store the generated .tar file somwhere safe, where it's not going to be damaged by anything(I'd say burn to DVD, but if you have a big home folder it might not fit...)

---

