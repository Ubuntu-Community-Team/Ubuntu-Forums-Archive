---
title: "[SOLVED] EeePC, wireless and Intrepid"
date: 2008-10-17
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by AlanR8 on 2008-10-17
Have Intrepid KUBUNTU with 4.1.2 on my play machine, and EeePC 700. It runs well.

However, I'm struggling to get the wireless working. In Hardy I just followed this tutorial to install the Madwifi drivers:

> sudo apt-get install build-essential
wget 'http://snapshots.madwifi.org/special/madwifi-ng-r2756+ar5007.tar.gz'
tar zxvf madwifi-ng-r2756+ar5007.tar.gz
cd madwifi-ng-r2756+ar5007
make clean
make
sudo make install
sudo reboot


Is there something similar for Intrepid? Bear in mind KUBUNTU and KDE 4.1.2

Thanks in advance and yes I've looked around......

---

### Post by olskar on 2008-10-17
> **AlanR8 said:**
> Have Intrepid KUBUNTU with 4.1.2 on my play machine, and EeePC 700. It runs well.

However, I'm struggling to get the wireless working. In Hardy I just followed this tutorial to install the Madwifi drivers:



Is there something similar for Intrepid? Bear in mind KUBUNTU and KDE 4.1.2

Thanks in advance and yes I've looked around......

Check out comments in 
[https://bugs.launchpad.net/ubuntu/intrepid/+source/linux-restricted-modules-2.6.24/+bug/182489](https://bugs.launchpad.net/ubuntu/intrepid/+source/linux-restricted-modules-2.6.24/+bug/182489)

---

### Post by aysiu on 2008-10-17
I have a 701 and have never (in Gutsy, Hardy, or Intrepid) been able to get Madwifi to work. I always used *ndiswrapper* for previous versions. In Intrepid, I installed the appropriate Eee PC-related packages in Synaptic and then rebooted and wireless worked fine.

---

### Post by Johnsie on 2008-10-17
with intrepid it should work almost out of the box. You just:

-install intrepid
-then go to system->hardware drivers
-disable the atheros driver in that list
-reboot your computer

and wireless should work on the eeepc.

---

### Post by Johnsie on 2008-10-17
double post

---

### Post by jfernyhough on 2008-10-17
I have Intrepid running on my 701 and wireless works fine with the 27-7 kernel (was also fine with 27-4).

All I had to do was add

blacklist ath_pci

to /etc/modprobe.d/blacklist and everything worked.

---

### Post by tact on 2008-10-17
What about the other bits of eeepc that needed special tweaks to get working prior to intrepid?  OSD, internal microphone, built-in cam, etc..  do these all work for you "out of the box" in intrepid?

---

### Post by LavianoTS386 on 2008-10-18
Add the eeepc specific kernel following the instructions at [www.array.org]("http://www.array.org")

---

### Post by Kobalt on 2008-10-18
I'm also using the array custom kernel, on a eeepc 901, and wifi works finally.

---

### Post by AlanR8 on 2008-10-18
So here's the deal....

Looking at my THEN current installation of Kubuntu with KDE 4.1.*, If I went "Start, System, Hardware Drivers Manager, there was NOTHING!

Quick re-install and all the updates and this time the driver appears in the list!

What gets me is why did I have to blacklist the installed driver to get wireless to work?

This is beyond my ken.........

Please give me a clue.

---

### Post by AlanR8 on 2008-10-18
Bump

---

### Post by Sycron on 2008-10-26
Today I've updated my intrepid on eeepc 701. After restart wireless doesn't work anymore. I'm using 2.6.27-7-generic.
> sycron@Book:~$ sudo iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

pan0      Interface doesn't support scanning.

sycron@Book:~$ 


---

### Post by AlanR8 on 2008-10-26
Try this. Make sure after the update your black list has both:

> blacklist ath_pci
blacklist ath_hal


After my update the second line had disappeared.

I also tried this, taken from somewhere else on these hallowed forums....

> in terminal:

sudo apt-get install linux-backports-modules-intrepid

shutdown and back on

gets everything up again


Worked for me.

That said, I find the wireless connectivity on the Eee VERY poor. Sitting right beside my Sony the signal strength is way less. Playing a film on the Sony from my "server" wirelessly is a breeze. On the Eee, VLC stutters and freezes. 

The Eee has 2 gigs of RAM and with a full Intrepid install, 500 Megs of free space on it's 4Gig HD. If I move the avi file to the 2Gig SD card in the Eee it plays fine.

Can only be the network.

Any comments or fixes?

---

### Post by IanW on 2008-10-27
It seems the wifi module needed for the EeePC701 was moved to linux-backports-modules-intrepid.
Installing this worked for me too.

---

### Post by Sycron on 2008-10-27
Thank you guys. Now another question. Yesterday I've installed Ubuntu BETA on my mother's comp (Compaq 6720s) and after updates wireless doesn't work anymore. Installing backports will fix this ? I hope yes :| .

---

### Post by Sycron on 2008-10-27
After I've restarted my eee, my wireless works again. THANK YOU!

---

