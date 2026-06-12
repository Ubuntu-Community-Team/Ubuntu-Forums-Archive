---
title: "Installed 11.10 over 10.10 and even got my Broadcom 43xx going."
date: 2011-10-13
forum: Installation &amp; Upgrades
---

### Post by irv on 2011-10-13
I got up at 2am this morning downloaded 11.10, burned a CD and installed over 10.10. Normally I do a clean install, and have two hard driver to swap, but this time I just upgraded a 10.10 version and things went well.
I knew I was going to have a problem with my wifi card because I did in 11.04.
If you are using a Broadcom 43XX Wireless card you need to follow these steps. Make sure you are online by plugging in a network cable.

First if you have STA driver loaded you need to uninstall it.

```
sudo apt-get remove bcm-kernel-source
```

2. I installed “firmware-b43-installer” package

```
sudo apt-get install firmware-b43-installer
```

3. I installed “b43-fwcutter” packager

```
sudo apt-get install b43-fwcutter
```

4. I typed into the terminal:

 ```
cat /etc/modprobe.d/* | egrep '8180|acx|at76|ath|b43|bcm|CX|eth|ipw|irmware|isl| lbtf|orinoco|ndiswrapper|NPE|p54|prism|rtl|rt2|rt3 |rt6|rt7|witch|wl'

```
This was the output:

> # which ath5k cannot recover. To prevent this condition, stop
blacklist ath_pci
blacklist eth1394
# replaced by p54pci
blacklist prism54
# replaced by b43 and ssb.
blacklist bcm43xx
blacklist uart6850
blacklist twl4030_wdt
Now after reboot it found the wifi card and connected to the Internet.

---

### Post by 23dornot23d on 2011-10-13
I too found a vast improvement in the way the wireless identifies and sets up ......

All went well ........ :D

Glad you got sorted .... interesting going from 10.10 to 11.10 ..... 

I thought people were supposed to do the intermediate step to 11.04 first ......

Safe way is usually a clean install in a fresh 20 Gig partition to make sure everything is working ok

Then at least its just a option in the grub-menu to go back to the previous version

But if its all working ok great ....... ;)

---

### Post by irv on 2011-10-13
One thing I found interesting, and I liked. When setting the options before the install my cam was activated and let me take a snapshot for the photo when login screen comes on if you change users or do a suspend. Nice touch. By the way it took less then an hour to do the upgrade from 10.10. This included online updates to all my installed apps.

I was reading where 11.10 did not include synaptic but seeing I had it installed on 10.10, it keep it after upgrading to 11.10 along with all the other apps I had installed already.

Seeing the install went so well I believe there is some great improvements in the install process.

---

### Post by wingman015 on 2011-11-22
irv,
Glad I found your post.  I have been running 11.10 from a flash drive on my Lenovo S10 with a Broadcom BCM4312 wireless card.
I am very new to all of this and I just simply typed in your commands into a terminal window.  I got errors on the first 3 commands but it ran on the 4th command.
I checked the wireless connections and noticed that I had 2 choices available.  I disconnected my ethernet and made a connection to one of the routers after entering the password.  I fired up the internet browser and successfully surfed thru a few sights.
Happy with my new discovery, I rebooted to see if it would hold and it did not.  Upon my reboot, my wireless choices are no longer listed.
 
Do you have any ideas that might help me?  I'm hesitant to load Ubuntu onto my netbook until I can get it to run successfully from my flash drive.
 
Thanks,
Brent

---

### Post by irv on 2011-11-23
> **wingman015 said:**
> irv,
Glad I found your post.  I have been running 11.10 from a flash drive on my Lenovo S10 with a Broadcom BCM4312 wireless card.
I am very new to all of this and I just simply typed in your commands into a terminal window.  I got errors on the first 3 commands but it ran on the 4th command.
I checked the wireless connections and noticed that I had 2 choices available.  I disconnected my ethernet and made a connection to one of the routers after entering the password.  I fired up the internet browser and successfully surfed thru a few sights.
Happy with my new discovery, I rebooted to see if it would hold and it did not.  Upon my reboot, my wireless choices are no longer listed.
 
Do you have any ideas that might help me?  I'm hesitant to load Ubuntu onto my netbook until I can get it to run successfully from my flash drive.
 
Thanks,
Brent
I am sorry, I had a typeo here are the commands to type in:
```
sudo apt-get remove bcmwl-kernel-source
```
```
sudo apt-get install firmware-b43-installer
```
```
sudo apt-get install b43-fwcutter
```
```
cat /etc/modprobe.d/* | egrep '8180|acx|at76|ath|b43|bcm|CX|eth|ipw|irmware|isl| lbtf|orinoco|ndiswrapper|NPE|p54|prism|rtl|rt2|rt3 |rt6|rt7|witch|wl'
```
Make sure you have a wire connection when doing this,
Then do a restart and unplug your cable and you should have wireless connection available.

---

### Post by wingman015 on 2011-12-03
Thanks irv.
I now have Ubuntu loaded as a dual boot with Windows XP and I've got my wireless working.  So far I love it and it is meeting all of my needs (using it for one week now).  The libre office suite works well for me.  I may never boot up in xp again.

Thanks for your help with the wireless.

Brent

---

