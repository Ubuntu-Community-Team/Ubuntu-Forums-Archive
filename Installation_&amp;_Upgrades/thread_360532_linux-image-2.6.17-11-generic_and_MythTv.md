---
title: "linux-image-2.6.17-11-generic and MythTv"
date: 2007-02-13
forum: Installation &amp; Upgrades
---

### Post by mjezell on 2007-02-13
Hi MythTv users on edgy Ubuntu,

I have been running MythTv on Edgy for several months now with great results.  Yesterday I did a auto upgrade and Myth livetv and lirc quit working.  Went through several trouble shooting routines to no avail.  Finally uninstalled linux-image-2.6.17.11-generic to linux-image-2.6.17.10-generic and everything is working again.  For all you folks that are having trouble installing MythTv or are experiencing problems with your installation, you may want to check out the kernel version you are using.  Hope this helps..someone.

---

### Post by FryerFox on 2007-02-13
My installation stopped working after I upgraded too. Then I remembered that I had to reinstall the drivers for my TV-card (from pvrusb2 source). 

It's running fine now. Could your problem have been something similar?

---

### Post by rsambuca on 2007-02-13
I am not sure about the lirc, but most of the tv tuner drivers will need to be reinstalled after a kernel change.  Total pain in the a**!!

---

### Post by Titus A Duxass on 2007-02-13
Remember the old saying "if it ain't broke don't fix it"

My Myth box in the living room has not been updated for at least 10 months, it works therefore I leave it alone.

Out of interest when did the new kernel come into play (date wise)?

---

### Post by rsambuca on 2007-02-13
Yeah, but mine isn't a dedicated HTPC.  It is mostly used for desktop use.

This last kernel came out about a week ago (or less).  Lots of problems with this one borking video cards etc.

---

### Post by Titus A Duxass on 2007-02-13
It sounds like this could have been the cause of Patrick's problems.

Useful information for all would be mythers.

---

### Post by jeeves on 2007-02-14
I can collaborate the same story. Had a perfectly working MythTV install on 2.6.17-10, but then I foolishly allowed the kernal to upgraded to 2.6.17-11, and it completely killed off lirc. I tried reinstalling lirc on 2.6.17-11 about 8 times, but I could never get it to work. 

**[SIZE="4"]Has anyone managed to to get lirc working on 2.6.17-11? [/SIZE]**

---

### Post by caletron on 2007-02-27
Yes, I've managed to get it working. Take what follows with a grain of salt; I'm trying to show the highlights and delete the dead-ends. I may have missed some crucial step. OTOH, I may be including some red-herrings.

```
apt-get install linux-headers-generic lirc lirc-x lirc-modules-source module-assistant
```
```
dpkg-reconfigure lirc-modules-source
vim /etc/lirc/lirc-modules-source.conf
```
Do one or the other (or both?) of the last two steps. Getting this right was trés importante. The actual compilation step below was failing because of missing bttv files. I don't have a bttv card so I don't care; I'm using a home-brew sensor on ttyS0. YMMV. 
```
cd /usr/src/
ln -s linux-headers-2.6.17-11-generic linux
m-a update,prepare
m-a a-i lirc -t
dpkg -i /usr/src/lirc-modules-2.6.17-11-generic_0.8.0-5ubuntu1+2.6.17.1-11.35_i386.deb
modprobe lirc_serial
```
For me, the modprobe failed because the serial port was already grabbed by the serial module so I did:
```
setserial /dev/ttyS0 uart none
modprobe lirc_serial
lsmod | grep lirc

```
You should see lirc_serial and lirc_dev. Now, to make sure it lasts through a reboot:
 ```
cat > /etc/serial.conf
/dev/ttyS0 uart none
(press Control-D)

```
The following is a huge subject on it's own and definitely out of the scope of this thread.
```
vim /etc/lirc/lircrc
/etc/init.d/lirc start

```
Hope this helps.

---

