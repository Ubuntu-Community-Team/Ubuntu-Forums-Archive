---
title: "nVidia and fresh install of Ubuntu 7.04"
date: 2007-08-28
forum: Installation &amp; Upgrades
---

### Post by Ardoramor on 2007-08-28
Hello people, noob is here. I have spent quite a few hours looking for solution here and through google but couldn't find anything so I decided I'd post here. Here is my problem:

I have bought a Sony laptop. It comes with Vista pre-installed. Its nice but I also need to have Linux environment. I decided to double boot with Ubuntu. I downloaded and burned text-based installer of Ubuntu 7.04, and installed it in one go. After my laptop was restarted, Ubuntu started to boot but failed to load xServer. Next, I was loaded into text mode w/o any GUI. It would probably help to mention that I have nVidia GeForce 8400 GT.

I looked around the web for possible fixes. The ones I've found suggested that I edit xorg.conf and change "nv" to "nvidia". Well, the problem is that I dont have nvidia driver installed. I went to drivers folder and the only thing that I have for nvidia is nv driver. I dont know how to get nvidia driver that I need. I dont think I can try getting it from the internet because I dont know how to connect to the internet through console and not sure if mirrors are enabled. Could anyone help me please?

Thank you very much!

---

### Post by merlinus on 2007-08-28
Try this at the command prompt:

```

sudo dpkg-reconfigure xserver-xorg

```
You can probably go with the default for most screens, but select "vesa" for your video driver.

Then:
```

startx

```
or reboot.

This should at least get you to a GUI, then you can search how to install the correct video drivers for your card.

-merlin

---

### Post by Marat Galiev on 2007-08-28
Only 27 steps:)
1)Install packages xserver-xorg-dev,pkg-config,libc6-dev.
You an find them at packages.ubuntu.com.
2)Press ctrl+alt+F2.
3)sudo nano /etc/init.d gdm stop
4)cd /there/your/driver/location
5)sudo sh NVIDIA-100.14...-xxx.run --ui=none
(without GUI menu).
To the question with nvidia-xconfig answer "Yes".
6)sudo nano /etc/default/linux-restricted-modules-common
Edit line
DISABLED_MODULES="nv nvidia_new"
7)sudo cp /lib/modules/2.6.20-15-generic/kernel/drivers/video/nvidia.ko /lib/modules/2.6.20-15-generic/volatile/
8)sudo modprobe nvidia
9)/sbin/ldconfig
10)/sbin/depmod -aq
11)reboot
12)step 7
13)cd /lib/modules/2.6.20-15-generic/volatile/
13)sudo insmod ./nvidia,ko
14)sudo modprobe nvidia
15)step 9
16)step 10
17)sudo /etc/init.d/gdm start
18)reboot
19)cd /lib/modules/2.6.20-15-generic/kernel/drivers/video/
20)sudo cp nvidia.ko nvidia_new.ko
21)sudo insmod ./nvidia.ko
22)step 9
23)step 10
24)ctrl+alt+F7
25)sudo nvidia-xconfig
26)reboot

---

### Post by Ardoramor on 2007-08-28
Thanks! That helped :D

Now all I need is to configure wireless card and get nvidia drivers :)

Thanks again!

---

### Post by Ardoramor on 2007-08-28
I have one more question which relates to installation. After I installed Ubuntu, grub started to handle the dual boot. However, I see a small problem with it. I have password protected partitions which I dont want people to access. The problem is that grub allows you to edit each individual entry. So someone might come in and edit an entry by removing the password or which partition it accesses. Is there any way of preventing it?

Thanks, you've helped me out so much!

---

### Post by Marat Galiev on 2007-08-28
that filesystem in you partitions?
and that partitions-linux or windows?

---

### Post by mariaclara on 2007-08-28
hi,

well, here's how i installed nvidia drivers on my ubuntu7.04,.
try the onboard nvidia driver.

click on Sytem->Admnistration->Restricted Drivers Manager enter your password.
click nvidia box. ok.

it should install automatically.

have fun

clare marie
philippines

---

### Post by Ardoramor on 2007-08-28
> **Marat Galiev said:**
> that filesystem in you partitions?
and that partitions-linux or windows?

Well, I feel silly but let me try answering that... I'm not really sure. Windows Disk Manager only recognizes its own filesystem as NTFS. There are three others. One partition is Sony's recovery partition. The other two are Ubuntu and swap partition. I would think that they use the regular filesystem (which I dont know ><... I'd guess ext3). Is that info any good?

---

### Post by Marat Galiev on 2007-08-28
Ok,that drive password protected?with windows?

---

### Post by Ardoramor on 2007-08-28
Yep, Windows and Ubuntu are protected. Recovery are not. But I've figured it out now. What I was doing was putting password for every grub menu entry (except for menu entries which have Vista and Ubuntu installed). However, editing option was available where another person could come in and edit the file itself and remove the password prompts. The way I fixed it was to edit the menu file by putting another password prompt after the timeout variable. Now, the user either gets loaded to Ubuntu by default or has to select which partition to load (and thus passwords are secure and always work) :)

Thanks for your help everyone!

---

