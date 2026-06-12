---
title: "dd command on an active USB key ?"
date: 2010-07-11
forum: Installation &amp; Upgrades
---

### Post by oxag on 2010-07-11
Hi,

To avoid having both Vista and Ubuntu sharing my internal hard drive I installed lucid on a 16 Go USB key. Now, I would like to take an iso image of the key as a backup to reinstall on a new key in case I lose the first one.

I believe the appropriate command to do this is dd (or dcfldd) but I am not sure about one thing : do I have to boot from a CD and then insert the key to copy or can I do it while the key is 'active' (ie. I boot from the key and I dd that same key) ?

Thanks for any response

---

### Post by C.S.Cameron on 2010-07-12
When cloning using dd I always boot from a third device, (Live CD, Live USB).

---

### Post by C.S.Cameron on 2010-07-12
Oops!

---

### Post by rogerdg on 2010-07-12
The reason for booting from another device is simple... You don't want the computer updating the data on the USB key while it is copying data.  There is no way to guarantee that the data copied will be in a usable state after the copy is complete.

Perform a normal shutdown of Linux from the USB key, restart the computer using a boot device other than the USB key, then insert the key and transfer it's data to another device.  You could use dd to copy directly to a new key if you have both in the system at the same time, just be sure you know which key is which.  (Insert one and look to see where it is connected in the device tables, then insert the other and see where it is connected.  (One should be /dev/sda and the next /dev/sdb or something similar to this.)  Next use dd /dev/sd? /dev/sd? to transfer the data replacing the ? with the correct device letter.

---

### Post by oxag on 2010-07-18
Thanks rodgerdg

I did what you suggested (boot from a live CD and dd the content of my key to a *mykey.iso* file on my hard drive) and everything went smoothly.

It took more than an hour to dd 16 GB though.

Thanks again

---

