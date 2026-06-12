---
title: "Modem driver challange"
date: 2005-09-02
forum: Installation &amp; Upgrades
---

### Post by neur0 on 2005-09-02
I installed ubuntu 3 days ago, and it is my first contact with linux. The installation went smooth, and almost everything works. The main problem is my modem. It is an ancient Lucent/Agere 56k winmodem. I found a few drivers for it, but I can't install them. One of them is a .deb file and I RTFM and typed the dpkg -i ... but it says something like:
"Could not indetify your distribution's way of automatically loading modules..."

Other possible driver is in tar.gz source code format, and I followed the instructions from tuxfiles.org, but somehow, this way doesnt work. (either because of the pakage or because of the system's compatibility for this pakage) 

Can anyone help me get that modem running so I can access online help from my ubuntu and start learning more about linux? 

PS 
I am completely new to Linux, but was/am an experienced user of dos,windows...

---

### Post by menawollas on 2005-09-02
This is probably of little use, but winmodems are really a cut price way of building a modem, and are primarily software based.

You would probably be better off buying a proper modem, which should only cost about 10 dollars/pounds/rand/yuan whatever.

---

### Post by az on 2005-09-02
Actually, your modem has linux drivers for it, and they are included in the Hoary kernel:

[https://wiki.ubuntu.com/forum/hardware/lucent](https://wiki.ubuntu.com/forum/hardware/lucent)


What you will need to do:
1. make sure that you have the restricted-modules installed. This was done by default in the install of Ubuntu or Kubuntu Hoary preview. 

***type this in a terminal***

sudo apt-get install linux-restricted-modules-2.6.10-5-386

2. put lt_serial and lt_modem in /etc/modules in order to get the modules loaded on boot. The modem device will appear as /dev/ttLTM0 (that is a zero at the end). 

***type this in a terminal***

sudo gedit

(Open the /etc/modules file and add those words to the bottom of the list)
lt_serial 
lt_modem 


3. since udev rewrites /dev on each boot, and since kppp doesn't like to use /dev/ttLTM0, you need to have a symlink created on boot (from /dev/ttLTM0 to /dev/modem is easiest, I think). To do this, create the file /etc/udev/rules.d/10-local.rules, and put these lines in it: 

#ltmodem KERNEL="ttLTM0", SYMLINK="modem" 

Otherwise, just use /dev/ttLTM0. 

***You can either add that line to the udev rules file or just configure your modem dialer to use the "/dev/ttLTM0" device. (The 0 is a zero!)***


4. since the 2.6.10 kernels have some problems with these modules, put the following in the grub boot commands (at the place where it will get updated!): pci=routeirq Do not forget to update grub 

sudo update-grub
Example: 

## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specifiv kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
# kopt=root=/dev/hda1 ro pci=routeirq

***I do not need to do this to get this to work***



Good luck!

---

### Post by neur0 on 2005-09-03
It WAS strange to me (as a widows user) that the "Device manager" "sees" my modem and knows its name (Agere...) and that it can't work.
Thanks,
rebooting, logging into Ubuntu, trying this in
5..
4..
3..
2..
1..

---

### Post by neur0 on 2005-09-03
Everything works now thanks again. (posting this from ubuntu)

---

