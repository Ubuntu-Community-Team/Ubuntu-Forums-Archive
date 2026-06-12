---
title: "Restricted drivers Nvidia problem"
date: 2009-10-13
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by whitethorn on 2009-10-13
Hi,

Whenever I install the nvidia drivers using the restriced drivers installation, X no longer appears.  I also don't make it to the consoles.  To get things running again I booted up karmic live ran the following command in chroot.

sudo dpkg-reconfigure xserver-xorg

I then emptied my /etc/X11/xorg.conf.  I was then able to get X and gnome back.

---

### Post by steev182 on 2009-10-13
What I did to get through this problem was I booted with the restricted drivers, and it didnt work, went into the Live CD, put the xorg.conf, /var/log/Xorg* and /var/log/kern.log onto a USB disk, deleted the xorg.conf and wemt back into my system.

Then posted my logs and Xorg.conf on here, and ended up finding that the problem was the onboard graphics trying to load a module, which caused the nVidia graphics card to be unable to load up too. I ended up having to blacklist the onboard radeon, and then it worked perfectly.

---

### Post by lovinglinux on 2009-10-13
Try version 173. It works for me, while version 185 renders the same issue you are experiencing.

---

### Post by Nossie on 2009-10-13
hmmm I've tried both versions and with the restricted drivers installed I just end up in a loop switching :(

---

### Post by donniezazen on 2009-10-13
> **whitethorn said:**
> hi,

whenever i install the nvidia drivers using the restriced drivers installation, x no longer appears.  I also don't make it to the consoles.  To get things running again i booted up karmic live ran the following command in chroot.

Sudo dpkg-reconfigure xserver-xorg

i then emptied my /etc/x11/xorg.conf.  I was then able to get x and gnome back.

+1

---

### Post by Nossie on 2009-10-13
I fixed mine by just downloading the official beta nvidia 190 drivers...


everything works now :D

[http://www.nvidia.com/object/linux_display_amd64_190.32.html](http://www.nvidia.com/object/linux_display_amd64_190.32.html)

for amd64 .. depends on your gfx card though I guess

---

### Post by jpcrow on 2009-10-13
I am on a kubuntu machine and have the same described problems after upgrading from jaunty to karmic.

I have my jaunty live cd and am wondering what exactly you typed in terminal once you booted into your live cd?

ie chroot then what?

as I understand what you are saying, you changed your root directory in the live cd to the root on your hard drive and then ran the following command in the terminal:

Sudo dpkg-reconfigure xserver-xorg

and then you erased the contents of your xorg.conf? or you deleted the file entirely?

I'm thinking lots of people are experiencing this issue, any help would be appreciated in clearing it up! Thanks

---

### Post by lovinglinux on 2009-10-14
This bug has been fixed with the latest updates! =D>

---

### Post by whitethorn on 2009-10-14
> **jpcrow said:**
> I am on a kubuntu machine and have the same described problems after upgrading from jaunty to karmic.

I have my jaunty live cd and am wondering what exactly you typed in terminal once you booted into your live cd?

ie chroot then what?

as I understand what you are saying, you changed your root directory in the live cd to the root on your hard drive and then ran the following command in the terminal:

Sudo dpkg-reconfigure xserver-xorg

and then you erased the contents of your xorg.conf? or you deleted the file entirely?

I'm thinking lots of people are experiencing this issue, any help would be appreciated in clearing it up! Thanks

Since the bugs been solved.  I'm putting this in here because you asked :)  

I followed the first couple steps here on this page.

[http://www.ubuntu-inside.me/2009/06/howto-recover-grub2-after-windows.html](http://www.ubuntu-inside.me/2009/06/howto-recover-grub2-after-windows.html)

Pretty much the following commands. The first command is to find out on which partition your / partition is on. I didn't mount my partition to mnt.  I created a folder in /media/ and mounted it to there. 

```

sudo fdisk -l
sudo mount /dev/sda1 /mnt
sudo mount --bind /dev /mnt/dev
sudo mount --bind /proc /mnt/proc
sudo chroot /mnt

```

Now your logged in as root on your partition on your computer. When I said cleared my xorg.conf.  I pretty much just emptied the file.  The newer xorg does a pretty good job at guessing your settings. Hope this helps.

---

### Post by Nossie on 2009-10-15
> **lovinglinux said:**
> This bug has been fixed with the latest updates! =D>

Strange....  I came home after being away.... installed the updates...

and my problem came back :( and now I cant resolve it just by downloading the beta driver...

back to the drawing board I guess :-|


*pout*

---

### Post by lovinglinux on 2009-10-15
> **Nossie said:**
> Strange....  I came home after being away.... installed the updates...

and my problem came back :( and now I cant resolve it just by downloading the beta driver...

back to the drawing board I guess :-|


*pout*

There was some nvidia updates yesterday and I was able to install and run it without issues, so I assumed it has been fixed. But I guess is not. Nevertheless, it is still working for me.

---

### Post by trulan on 2009-10-15
Yeah the updates fixed it for me too - it even works properly out of the box on the rt kernel, which is a first for Karmic.

---

### Post by lovinglinux on 2009-10-15
BTW, I had issues during the driver activation on another box. When activating the driver, the progress bar went all the way and it looked like it was installed, but the driver activation wasn't displayed in the jockey interface and it didn't ask for a reboot. So I went to Synaptic and manually installed nvidia-185-kernel-source, nvidia-185-modaliases, nvidia-glx-185 and nvidia-kernel-common. It worked.

---

### Post by Nossie on 2009-10-16
> **lovinglinux said:**
> BTW, I had issues during the driver activation on another box. When activating the driver, the progress bar went all the way and it looked like it was installed, but the driver activation wasn't displayed in the jockey interface and it didn't ask for a reboot. So I went to Synaptic and manually installed nvidia-185-kernel-source, nvidia-185-modaliases, nvidia-glx-185 and nvidia-kernel-common. It worked.


Thanks,

I had a think about what you said, first I checked to see if nvidia had released an updated 190 driver (which they hadn't) then checked hardware drivers... there was also no prompt to restart for me either this time.

I then went into synaptic but the packages had already been installed.... so I went back into restricted and REMOVED the 185 drivers (having got back into x through removing the config file in /etc/x11) and then dropped back to a prompt and installed the 190 drivers...

it came back up screens found and workable :)

strange... thanks for giving me the thought tho!

---

