---
title: "Don't boot if USB HD connected"
date: 2007-12-23
forum: Installation &amp; Upgrades
---

### Post by xeo_pt on 2007-12-23
I have a Dell T105 with Ubuntu 7.10, it works fine!
Now a attached a USB HD external drive (/dev/sdb1)
I mount the drive as usual and change fstab to mount it at boot.
The problem is that at boot the main/internal drive is detected by Ubuntu as sdb1and try to  boot with the main disk as sdb1, but after mount the fstab it gives an error and stops.
I have to type rebbot. and it works almost normaly except that the main disk is a sdb1 and the external is sda1.
If I unplug the external disk it boots fine.
My scripts are made to work with the USB drive as /dev/sdb1, so I have a lot of probles.
I use this technique in a system (debian) and works fine, but now Ubunt is give me this problem.
Any ideas for a workaround?

Thanks in advance.

---

### Post by Pumalite on 2007-12-23
It's a bad idea to include USB in fstab. Better to have it mount on plug in.

---

### Post by xeo_pt on 2007-12-23
> **Pumalite said:**
> It's a bad idea to include USB in fstab. Better to have it mount on plug in.

Thanks for you answer!
How can I do it.
How can I prevent the USB been detected at boot and how can it be mounted further?

---

### Post by nzadLithium on 2007-12-23
Just wait for it to finish booting then login. Then plug your disk in. As long as you have automount enabled (system>>preferences>>removable drives and media check the top 3 in the storage tab)  it should show up on the desktop.

---

### Post by xeo_pt on 2007-12-23
> **nzadLithium said:**
> Just wait for it to finish booting then login. Then plug your disk in. As long as you have automount enabled (system>>preferences>>removable drives and media check the top 3 in the storage tab)  it should show up on the desktop.
The problem is the device is already pluged, so it as to detect as a normal USB device,
but I think that the problem is with the BIOS because it send to Ubuntu the drive info as been of higher prioraty than the internal ones.

---

### Post by meierfra on 2007-12-23
Can you change the boot order in the bios  so that the internal drive is first?

---

### Post by xeo_pt on 2007-12-24
> **meierfra said:**
> Can you change the boot order in the bios  so that the internal drive is first?

Yes, but it as already set, but this board only as usb no PS/2 plug, so I have to connect a USB keyboard and when the BIOS boot it will detect all USB devices prior to SATA devices and I think that here is the problem.

---

### Post by nzadLithium on 2007-12-24
Im confused :S cant u just unplug the usb disk wait for it to startup then plug it back in??

---

### Post by xeo_pt on 2007-12-25
> **nzadLithium said:**
> Im confused :S cant u just unplug the usb disk wait for it to startup then plug it back in??
Thats my problem!
If the power goes down ant it cames the system as to be able to recovery without human intervention!

---

### Post by meierfra on 2007-12-25
I'm not quite sure I understand all the details of your problem, so let me ask a few question.

 Are your external drive always going to be plugged?

If this is the case you should be able the edit menu.lst and fstab to make things work.

> at  boot the main/internal drive is detected by Ubuntu as sdb1and try to boot with the main disk as sdb

What  does that mean? Who detects  Ubuntu as sdb1? Grub? the kernel?

Plug in all your hard drives and  post the output of 

```
sudo fdisk -l
```

```
 cat /boot/grub/menu.lst
```

```
cat  /etc/fstab  
```

```
sudo blkid
```

---

### Post by xeo_pt on 2007-12-25
> **meierfra said:**
> I'm not quite sure I understand all the details of your problem, so let me ask a few question.

>  Are your external drive always going to be plugged?
Yes and no! if there is a problem the drive can't be off, or I can change the drive.
> 
If this is the case you should be able the edit menu.lst and fstab to make things work.
Yes, but if the external drive fails the system will boot the wrong way.

> 
What  does that mean? Who detects  Ubuntu as sdb1? Grub? the kernel?
The kernel!

I will post the output as soon as I can.

Thanks.

---

### Post by meierfra on 2007-12-25
> The kernel!

If you use UUID's you should not have a problem.

---

### Post by meierfra on 2007-12-25
> Yes, but if the external drive fails the system will boot the wrong way.

Why would the external drive fail? Is that what this is all about, figure out a system which even works when the external drive fails?

---

### Post by nzadLithium on 2007-12-26
yeah im a bit lost about what your trying to acheive as well. Maybe you could explain it more clearly. Every sentence you say seems to have a starting half then a half that contradicts it  :D *confused*

---

