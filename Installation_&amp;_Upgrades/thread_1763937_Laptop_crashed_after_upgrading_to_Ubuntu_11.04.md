---
title: "Laptop crashed after upgrading to Ubuntu 11.04"
date: 2011-05-21
forum: Installation &amp; Upgrades
---

### Post by maxmiaggi on 2011-05-21
Hello

I used ubuntu 10.10 till yesterday when I found out regarding the release of ubuntu 11.04. So, I upgraded to it. All the required files were downloaded and were being installed. During the installation process, I went somewhere (since it was to take some time in finishing that). After I returned, I found my laptop off (seems like somebody switched off the power supply unknowingly and my battery discharged).

Now when I switch on my laptop, the boot screen doesn't come up (from where I choose whether ubuntu or windows).. all that it shows is:

```
error: symbol not found: 'grub_env_export'.
grub rescue>
```Now what to do? I am not able to access anything, not even windows. Do I need to format my whole hard disk and reinstall both windows and ubuntu? :cry:

---

### Post by Hedgehog1 on 2011-05-21
You are going to need an Ubuntu 11.04 LiveCD/LiveUSB before this is over.


If you boot from the 11.04 LiveCD/LiveUSB, you may have an upgrade path offered in the 'install 11.04'.

[IMG]http://img848.imageshack.us/img848/874/upgradetonatty.png[/IMG]

**If this is not offered**, if you have your data in a separate '/home' partition you can reinstall 11.04 over your 10.10 '/' partition and be sure to not format the '/home' partition:

First, define your '/' (root) partition:

[IMG]http://img31.imageshack.us/img31/7520/04allocdrivespace2.png[/IMG]

[IMG]http://img130.imageshack.us/img130/9673/05allocdrivespace3.png[/IMG]

Then define your '/home' partition:

**[SIZE="4"]IF YOU ARE DOING AN UPGRADE/REINSTALL, DO NOT FORMAT THIS PARTITION![/SIZE]**

[IMG]http://img202.imageshack.us/img202/6828/07allocdrivespace5.png[/IMG]

This separates your documents and 'stuff' from the system files and 'stuff' in the '/' partition.

***The Hedge***

:KS

p.s. To learn how to move your '/home' into it's own partition: **_[SeparateHomePartition]("http://www.psychocats.net/ubuntu/separatehome")_**

---

### Post by sidzen on 2011-05-21
go back to 10.04LTS and stay there till the bugs are worked out!
and d1sable update notification or ignore it

---

### Post by maxmiaggi on 2011-05-21
Thanks for the reply guys...

@Hedgehog1:

well, i did upgrade to 11.04, and it seems like it has installed. But the problem is that the grub bootloader screen isnt coming up during bootup. Due to this Im not able to open any OS in my system.

I guess 11.04 has already been installed. So, should I reinstall it over the same once again using LiveUSB?

Regards
maxmiaggi

---

### Post by Hedgehog1 on 2011-05-21
> **maxmiaggi said:**
> 
well, i did upgrade to 11.04, and it seems like it has installed. But the problem is that the **grub bootloader screen isnt coming up **during bootup. Due to this Im not able to open any OS in my system.

maxmiaggi,

My advice was based on your first description of an incomplete load of Natty/11.04, and that you were seeing this error:
```
error: symbol not found: 'grub_env_export'.
grub rescue>
```

This is grub coming up, but aborting due to missing pieces.

Assuming that this is still your situation, then a clean reinstall from the Natty LiveCD/LiveUSB is your best option.

If you are not currently setup with a seperate '/home' poartition, please boot of the liveCD/LiveUSB and backup your data to a USB stick or external drive before reinstalling.

***The Hedge***

:KS

---

### Post by maxmiaggi on 2011-05-22
Thanks! A clean reinstall did the job! :)

---

