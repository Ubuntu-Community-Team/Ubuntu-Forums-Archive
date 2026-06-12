---
title: "how to remove drivers in ubuntu hardy 8.10"
date: 2008-10-24
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by Arthur Millar on 2008-10-24
why is this so complicated 
i have tried removing anything that resembles the driver im trying to remove and still it comes up and causes conflicts on my machine 
when i reboot ubuntu blacklists the driver that works and replaces the nonworking crap driver 
arrrgggggg

---

### Post by melojo on 2008-10-24
edit this file below and blacklist the driver and see if the one that works is blacklisted 
/etc/modprobe.d/blacklist

---

### Post by Arthur Millar on 2008-10-24
> **melojo said:**
> edit this file below and blacklist the driver and see if the one that works is blacklisted 
/etc/modprobe.d/blacklist

already been done 
i removed the driver with rmmod 
then edited /etc/modprobe.d/blacklist
# (whatever)
blacklist (whatever)
install the driver i wanted with insmod 
run lsmod | grep (whatever)
its there and the device works 
reboot 
and im back to square one 
i also tried editing udev 
and replacing the driver names 
I also removed the .ko file and any other file with the drivers name

---

### Post by melojo on 2008-10-24
can you put those commands in a script and add it to /etc/rc.local and let it do this automatically when you boot.

I don't know if this will work just curious.  This is similar to how I get my wireless card to work.

---

### Post by Arthur Millar on 2008-10-24
I will need help with that 
i have rc.local open with gedit 
do i just type out what i would in terminal
 eg
$ rmmod r8169
cd 8101-1.009.00
make clean modules 
make install
depmod -a
insmod ./src/r8101.ko
ifconfig eth0

this is what i do to get my net up

---

### Post by melojo on 2008-10-24
rmmod r8169
cd 8101-1.009.00
make clean modules
make install
depmod -a
insmod ./src/r8101.ko
ifconfig eth0


Add the full path to the directory >  cd 8101-1.009.00and try running it in a terminal before adding it to rc.local.

make sure its executable

---

