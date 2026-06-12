---
title: "Ubuntu 10.04 on Acer Aspire 8943G?"
date: 2010-08-11
forum: Installation &amp; Upgrades
---

### Post by twgray on 2010-08-11
Has anyone successfully installed Ubuntu 10.04 on the Acer Aspire 8943G laptop?  Particularly the Wifi?  I have only run the live CD so far but am unable to get it to even recognize the Wifi...

---

### Post by samquixote on 2010-08-29
Sounds like I have the same problem - getting the network connections to work!.  In my case ifconfig showed only the loopback connection and lshw indicates that both the Atheros wired and Broadcom wireless are "UNCLAIMED".
lsmod showed no e1000 driver.  (Need e1000 to get wired connection working - once that is working, use the wired connection to get the Broadcom STA hardware driver to get wireless up.)
modinfo showed that the e1000 driver was there.
iwconfig and iwlist complained that nothing was there!
Tried installing the e1000 driver using modprobe - no luck (may have done that wrong - am investigating further).
lspci finds the respective devices.

Ubuntu was installed using wubi, dual booting with Win 7.

The installation (from the same .iso) under VirtualBox works just fine!

...sam

[Update]
Your other posting - [http://ubuntuforums.org/showthread.php?t=1558553](http://ubuntuforums.org/showthread.php?t=1558553) - referenced another posting - [http://georgia.ubuntuforums.org/show....php?p=9453261](http://georgia.ubuntuforums.org/show....php?p=9453261) - which had useful info that solved the problem for me!
Since in Ubuntu I had no inet access, the apt-get steps were not relevant, therefore I used the Win 7 boot to download the compat-wireless-2.6.tar.bz2 file from [http://linuxwireless.org/download/compat-wireless-2.6](http://linuxwireless.org/download/compat-wireless-2.6)
then rebooted back into Ubuntu.
Copy the file from /host/<Windows download location> to ~/Desktop (or wherever you like).
Open a terminal window.
cd ~/Desktop
tar -xvjf compat-wireless-2.6.tar.bz2
cd compat-wireless*
sudo scripts/driver-select atl1c
sudo make
sudo make install
(Since you may need to do the last three lines whenever there is a kernel update, I created a script with those lines - sans sudo, then chmod +x <scriptfile>, then just sudo <scriptfile>)
Reboot and voila! wired connection is working.  (If not, do modprobe atl1c and reboot - that should then work.)
First thing is run Administration->Update Manager and get your system up-to-date!
Reboot.
Now run Administration->Hardware Drivers and activate the Broadcom driver.
Do NOT activate the ATI driver - it will cause your system hang at next boot.  I am researching that issue!
You now will have the wireless connection also functioning.

Hope this works for you!
...sam

If I find a solution to the ATI driver hang, I'll post here.

---

### Post by dreKion on 2010-09-01
Yes, I have installed Kubuntu 10.04 and works fine.

Wifi - OK
Ethernet - OK (must compile and install driver)
bluetooth - OK
Sound - OK (you must install alsa driver 1.0.23).


TV - FAIL (Not driver in linux)

---

