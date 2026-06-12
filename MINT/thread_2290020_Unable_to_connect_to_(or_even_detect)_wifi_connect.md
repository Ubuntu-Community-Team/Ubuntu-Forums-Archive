---
title: "Unable to connect to (or even detect) wifi connections"
date: 2015-08-08
forum: MINT
---

### Post by johnnyboy on 2015-08-08
Hello!  I'm a new Linux Mint user, I'm having issues with wifi.  More specifically, Mint seems to be having trouble with, a) keeping my wireless card turned on, b) detecting wireless connections, c) maintaining wireless connections.

Here are some specs:
Com: Recently purchased Hewlett-Packard "HP Notebook"
wireless card: Realtek RTL8723BE PCIe Wireless Network Adapter
Driver: rtl8723be
Linux Mint Version: 17.2 Mate edition

What I've tried:
1. Force the wlan0 card to stay turned on with "sudo ifconfig wlan0 up" command.
2. Update drivers with Driver Manager
3. Update broadcom drivers
4. Mess with the "airplane mode" button (f12)
5. Write a configuration file that disables power management for the card (presumably to force it to run full bore, link: [https://sites.google.com/site/easylinuxtipsproject/reserve-7#TOC-Realtek-RTL8723BE-chipset](https://sites.google.com/site/easylinuxtipsproject/reserve-7#TOC-Realtek-RTL8723BE-chipset) )

I'm hoping someone knows what the issue is and how to fix it.  I've tried a couple other forums so far and though they have had great suggestions, none of them have led to a 100% resolution.

Thanks!

---

### Post by ajgreeny on 2015-08-08
I do not know Mint well enough to know what kernel is in 17.2, but I have seen posts in places that I can't now find where some of the RTL wifi adapters did not work with kernels in the 3.13 series but did in later kernels.

If you can use a cable connection to update to the 3.19 series kernel you may be in luck, but I am not sure if that is easy in Mint so will have to leave it to you to search more.

See also the post at [http://ubuntuforums.org/showthread.php?t=370108](http://ubuntuforums.org/showthread.php?t=370108) which may help you find a lot more info for us all to help you.

---

### Post by johnnyboy on 2015-08-08
> **ajgreeny said:**
> I do not know Mint well enough to know what kernel is in 17.2, but I have seen posts in places that I can't now find where some of the RTL wifi adapters did not work with kernels in the 3.13 series but did in later kernels.

If you can use a cable connection to update to the 3.19 series kernel you may be in luck, but I am not sure if that is easy in Mint so will have to leave it to you to search more.

See also the post at [http://ubuntuforums.org/showthread.php?t=370108](http://ubuntuforums.org/showthread.php?t=370108) which may help you find a lot more info for us all to help you.

ajgreeny, thanks for the response.  I've been fighting with Mint for a few days now and I think I see the writing on the wall.  I've decided to throw in the towel with Mint and switch back to Ubuntu - I am installing 15.04 as we speak!

---

### Post by tomasrey88 on 2015-08-09
Switching to Ubuntu may not fix your problems as Mint is just a prettier version of Ubuntu with all the codecs pre-installed. You'll likely face the exact same problems. Try a differential diagnosis. Install the wireless network adaptor in the exact same network environment on a Windows computer, install the driver from the manufacturer Realtek's website, then see if you have the same problems. If so, then it is the hardware that is at fault, not the software. 

There is a "debian" edition, LMDE. If you are using that, switch to the Ubuntu edition if you were running fine with Ubuntu but not with Mint, you're probably using LDME because Ubuntu = MINT unless you're using LDME. 

If it is a software problem, try the "Cinnamon" Ubuntu edition and it should run fine if you were running Ubuntu fine. There's not much difference between the two, just LInux Mint has all the codecs installed so you don't have to hunt down all the codecs and install them, which is a PITA. Also, it is better organized and neater looking, but that is about it. The difference is just aesthetics and ease of installation, not anything major. 

Best of luck!
Shameless plug, Please answer my question, link is below. Thanks! 
[http://ubuntuforums.org/showthread.php?t=2288606](http://ubuntuforums.org/showthread.php?t=2288606)

---

