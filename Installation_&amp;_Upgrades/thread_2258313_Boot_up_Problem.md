---
title: "Boot up Problem"
date: 2014-12-26
forum: Installation &amp; Upgrades
---

### Post by user987 on 2014-12-26
I have just cloned Ubuntu 14.04 from my HD to a usb flash drive via DD.

It was a sucessful clone because when i ran fdisk both the clone and HD had identical files.

When i boot up via the flash drive i had no problem either.

The problem comes in when i use the flash drive on my other computers.

I get the messages :

gave up waiting for root device
Alert! /dev/disk/by-uuid/fff6b3e7-d5e8-4489-9f49-b54c49616e5a does not exist
dropping to a shell
busy box v1.21.1(ubuntu 1:1.31.0-1ubuntu 1) built in shell (ash)

Any idea what happen?

I had also cloned Zorin OS HD  from another computer to a flash drive and the flash drive  could boot any computer it was plug in to. 

So what happen in Ubuntu?

Thanks for any help in advance.

---

### Post by egeezer on 2014-12-26
You will probably have to add to the boot code something like "waitusb=10" so that it will give those computers time to acknowledge the presence of your USB.

---

### Post by schragge on 2014-12-26
Another useful kernel option is [rootdelay]("http://www.linuxtopia.org/online_books/linux_kernel/kernel_configuration/re58.html"). Try something like *rootdelay=90*. Add it to kernel command line parameters in */etc/default/grub*:
```

sudo sed -i 's/^GRUB_CMDLINE_LINUX="/&rootdelay=90 /' /etc/default/grub
sudo update-grub

```
If that works you can then play with delay value to see if a shorter delay would be enough.

---

### Post by user987 on 2014-12-27
To egeezer,
                 Where do i add the code you showed?
Can you give a example?


To schragge,
                   I'll try your command and get back to you later.

Thanks to both for quick response.

---

### Post by user987 on 2014-12-30
To schragge,
                  I check and my uuid for the flash drive is the same as the one it can't find.
I will try your delay command and see what happens.

---

### Post by user987 on 2014-12-31
I used the commands on the flash drive and it came back with :
Setting Grub_Timeout to a Non-Zero value when Grub_Hidden_Timeout is set is no longer supported.

Any way i then  plug it in to my other computers and they all came back with same messages in my original post above.

Any new ideas or suggestion on why the flash drive won't boot up other then on the original computer it was created on?

Also should i try another cloning program?

---

### Post by user987 on 2015-01-02
I want to mention that the flash drive that could not boot was a san disk 3.0 32g , while the one that work was a san disk 16g 3.0 model.

I tried again cloning another computer that has a 16g SSD HD with mint on it via DD to a 16g and 32g flash drives.

Both clone sucessfully but again the 32g flash drive would not boot up while the 16g can boot up any computer.

This is telling me that it is not a OS or DD problem but something with the flash drives structure.

Does anyone have any idea what is going on?

I will also list the code i got from the 32g boot failure and hope someone can help.

common problems
-bad args (cat/proc/cmdline)
-check rootdelay=(did the system wait too long enough?)
-checkroot=(did the system wait for the right device?)
-missing  modules (cat/proc/modules; ls/dev)
alert! /dev/disk/by-uuid/7cf51a43-98a6-45c6-9af2-d9a23fe38cf does not exist
Dropping to a shell!
BusyBox v1.21.1(ubuntu1:1.21.0-ubuntu1) buit-in shell (ash)
initramfs

---

### Post by yancek on 2015-01-02
Each partition has a specific uuid.  When you clone a system from one hard drive to another, the second hard drive will not have the same UUID as the first which is what your error is.  

> alert! /dev/disk/by-uuid/7cf51a43-98a6-45c6-9af2-d9a23fe38cf does not exist

You need to run blkid or sudo blkid to find out what the actual uuid is.

---

### Post by user987 on 2015-01-03
I will run the command and get back the results to you.

But how do you explain the fact that both the 16g flash drives with zorin and Mint don't have this problem and i assume is seeing the uuid.

Also when boot both the 32g flash drives with Ubuntu or Mint , in both cases i see the Ubuntu  purple scrren or Mint green logo stating to boot but then get the codes mention earlier.

---

### Post by schragge on 2015-01-03
Well, identifying partition by its UUID is not the only option, /etc/fstab also accepts device file names and labels. I don't know how it's done in Mint or Zorin, but Ubuntu uses UUIDs. TBH, I don't expect this to be the issue at hand. I assume all active Debian-based distributions including Mint and Zorin use UUIDs by now.

---

### Post by user987 on 2015-01-05
i ran the blkid and the uuid is the same as the alert one.
So i really don't understand why the 32g flash drives are having this problem.

If i get the chance i will use a 2.0 32g flash drive  give it a go, maybe it is a 3.0 problem of the 32g flash drives.

---

