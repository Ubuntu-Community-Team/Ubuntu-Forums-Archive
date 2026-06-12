---
title: "Notebook WiFi recently became intermittent - turns off after a few minutes"
date: 2017-02-17
forum: MINT
---

### Post by afz12 on 2017-02-17
Hi

I use Ubuntu 16.10 and Mint 8.1 dual boot on a hp Envy notebook and recently the internal WiFi modem has developed an odd turning off fault. It recovers temporarily when I use

sudo echo -e "nnameserver8.8.4.4" | sudo tee -a /etc/resolv.conf
sudo service network-manager restart

This lasts a few minutes, or more, quite random, then it turns off again.

When I use an Ethernet cable, no problem. Also, when I get a nano USB WiFi dongle to go (TL-WN725N), also no problems - no turning off.

Both OS exhibit the same behavior and were OK a few weeks ago. Why the sudden change? Have I done something silly? If so, can I reverse the damage?

Also both OS are up to date using their update manager and also

sudo apt-get update
sudo apt-get dist-upgrade

I suspect something has gone amiss in grub but I don't know enough to fix this. Anyway, all suggestions are welcome.

---

### Post by wildmanne39 on 2017-02-17
Click on the wireless script in my signature and follow the directions for running it and posting the file it creates here using code tags.

---

### Post by afz12 on 2017-02-18
Hi wildemanne39

Thanks for the instructions. I ran it OK and got a txt and tar file but I don't know what a code tag is. I see add/edit tags and view tag cloud but I don't know how to upload the tar file - this is my guess, it seemed to attach under "file upload"

---

### Post by wildmanne39 on 2017-02-18
There are several things we can do to help your connection issues, please do:
```
sudo sed -i 's/wifi.powersave = 3/wifi.powersave = 2/' /etc/NetworkManager/conf.d/default-wifi-powersave-on.conf
```
Please uninstall wicd completely it conflicts with network manager.
We need to set your country code for your router:
```
sudo iw reg set NZ
sudo sed -i 's/^REG.*=$/&NZ/' /etc/default/crda
```

Go into your routers configuration and set the encryption to WPA2-AES (CCMP) not mixed mode and not TKIP.

Then set the channel to 1, 6 or 11 not auto then save settings.

Go into network manager and set your settings to match the screenshots.
Let's set a driver parameter that helps the driver maintain a connection.
```
echo "options rt2800pci nohwcrypt=y" | sudo tee /etc/modprobe.d/rt2800pci.conf
sudo modprobe -rfv rt2800pci
sudo modprobe -v rt2800pci
```
Reboot

---

### Post by afz12 on 2017-02-18
Hi wildemanne39

Thanks for the instructions. I entered these but accessing the modem was an issue. I used its number and it displayed OK but didn't accept any username or password (e.g. last 6 characters of MAC address). Now the modem won't start at all - but using an external USB nano WiFi goes OK. What do you suggest I do next?

---

### Post by wildmanne39 on 2017-02-18
Do you mean the internal wifi will not connect? if not click on the wireless script in my signature and post the results of it here.

It is late here I am about to tired to do much more wireless issues tonight.

---

### Post by afz12 on 2017-02-18
Hi wildemanne39

I think I've attached the new tar file

The modem says "service not available"

I am not in any hurry to fix this as I have other notebooks and other ways to connect but I would like to understand what went awry. 

Would wiping the notebook completely and reinstalling a new OS solve this modem issue?

---

### Post by howefield on 2017-02-18
Thread moved to the "*MINT*" forum.

---

### Post by afz12 on 2017-02-18
Hi howefield

I don't mind shifting to "Mint" but I did state that this Wifi issue occurs on both Mint and Ubuntu on a dual boot notebook - it is not therefore a specific Mint issue, it seems to me as a generic WiFi issue.

---

### Post by howefield on 2017-02-18
Sure, but given that you clearly want to use Mint to diagnose the solution this is the correct forum to post in.

Good luck in resolving, you have one of the best helping you.

---

### Post by afz12 on 2017-02-18
Thanks howefield - I had also made an Ubuntu tar file but was just a bit too late to send this. No worries. However perhaps you can answer; if I remove all OS on this notebook and install a fresh OS from scrarch, is this likely to make the WiFi modem work again? I don't mind doing this and have just made a USB boot drive to see if it springs into life before installing

---

### Post by wildmanne39 on 2017-02-19
I know what happened some how a setting was changed in your router but not one that I asked you to change, it is possible resetting the router will help, 

I also noticed that you did not set IPV6 to ignore as I asked you to from the screenshots in my previous post please do so now then reboot, then go into the router and change this 802.11n to this 802.11bgn, your device is having trouble connecting at just N speeds.

---

### Post by afz12 on 2017-02-19
Hi wildmanne39

I did follow your instructions as best I could but there are problems with your suggestions. These are

1. I did try to adjust the router settings but it did not accept my username / password despite that I had written these down previously

2. The notebook WiFi modem also plays up when I use the notebook at a public place. For example, yesterday I was at the library and the modem exhibited the same behavior there. I am sure you agree that I cannot be expected to change the settings of routers owned by our public library

3. I have other computers that connect to my router perfectly well. These are a hp dv6 notebook (running Ubuntu 16.04 and Mint 18.1), an Acer 5920 (running Mint 18.1 and XP) and a Pendo tablet (some version of Linux). If the router settings were at fault then wouldn't these also have problems?

 4. If I did manage to change the router settings then perhaps this would interfere with the operation of my other devices. Bear in mind there is quite a high probability that I would stuff the procedure up and find myself in a worse situation

I am not trying to disobey your advice wildmanne39 but these concerns are in my mind quite reasonable.

I would prefer to find a solution that allows this notebook (Mint 18.1 and Ubuntu 17.04) to work with my router as it is and also with WiFi in public places that have routers I certainly cannot interfere with

---

### Post by wildmanne39 on 2017-02-19
As I said the errors that showed up is because only N speed is enabled in the router at the moment, I am not sure how that happened and I understand you can not get into it at this time but I can not change that fact that is the issue at this time.

I can not tell you why you can not connect at other locations without seeing a info file from the script ran at one of those locations but I would suspect since we included a driver parameter that you should be able to connect at any location that is not N speed only, see even devices that connect at N speed will not do it every time it depends how close to the router they are and many other variables so other devices at times will start to have trouble if only N speed is set.

I am sorry I have no further suggestions I have done all I can do it is up to you to do the rest.

---

### Post by afz12 on 2017-02-19
Hi wildmanne39

Thank you for your assistance, I appreciate that you volunteer your time to help others and adopting a sub optimal solution would be fine. The other devices have no problem with range and also work OK in external places. Only this notebook has issues but works fine with an external WiFi dongle, provided the internal modem is off (it sometimes runs for a while, sometimes not). When I boot Mint (I'll check also for Ubuntu 17.04 alpha 2) I get  a modem error message - this is definitely a modem at fault. It goes something like "failed to enter state -4 -5". Anyway this is a high class problem and perhaps if I can permanently deactivate the internal modem either using a script or physical removal and use the external dongle then this would be quite acceptable - I don't want to squander your time further wildmanne39 as I am sure there are plenty of other members with more pressing issues than mine for you to address.

---

### Post by jeremy31 on 2017-02-19
I notice you have a very new 4.4 kernel, perhaps rebooting and using grub to boot to an older kernel in Linux Mint will fix the issue.  I know that by default Linux Mint doesn't install kernels on it's own but it can be enabled in the Update Manager

---

### Post by afz12 on 2017-02-19
Hi jeremy31

This notebook currently runs dual boot Mint 18.1 and Ubuntu 17.04 alpha 2. The modem plays up on both OS. The Ubuntu beta should be ready next month so I am happy to wipe all and reinstall this beta and then Mint in any case (I always have files backed up so this isn't a drama). However I am thinking now that the internal modem has a hardware fault. I remember that when at the library I use the battery not the plug pack for power and then the internal modem works. At home I use power and it plays up. I suspect a hyper sensitivity to voltage is going on here. I tried the same just before - the modem starts on batteries, then is OK on power but then eventually plays up, but does respond to a reset

sudo echo -e "nnameserver 8.8.4.4" | sudo tee -a /etc/resolv.conf
nnameserver 8.8.4.4

sudo service network-manager restart

worked this time but not always.

Most notebooks will exhibit a slightly dimmer display when external power is removed - internal voltage regulators (always switch-mode IC types in notebooks) never provide exact voltage regulation so I suspect the internal modem has or is developing a hardware fault that makes it sensitive to slight over-voltage. I expect that this notebook, as will others, start with a 19 V to battery "buck regulator" first, usually 4 lithium cells will need +12 V. From this, there will be another switch-mode from say 12 V to an internal +5 V general purpose supply, switched then to +3.3 V and say 1.2 V for the CPU core(s) and also +22V or so for lighting the notebook display screen. The screen voltage definitely must reduce on battery power as slight dimming is always visible. This explanation, anyway, is consistent with what I have observed to date. Definitely, attacking the router is not a solution, demonizing this won't allow public access and it was provided by my current service provider with the settings they use. It hasn't changed and works fine with 3 other devices.

 Anyway I suspect this is a modem fault and a hardware one at that! My other older hp dv6 notebook had its internal WiFi modem eventually give up the ghost so I don't think it is too incredible to assume that this notebook has also developed an internal modem hardware fault - this explanation is consistent with all observations as to its behavior so far.

If so there are two sub optimal but perfectly adequate solutions. I would like to permanently deactivate the internal WiFi modem preferably using a Linux command, updating grub I guess. I could physically remove the PCB but I don't know what I might find under the notebook' hood. This notebook works fine using an external WiFi dongle (TP LInk TL-WN725N) but competes with the internal modem if it turns on when really not wanted. I am sure there must be a command(s) to permanently deactivate the internal modem as this would be a perfectly fine solution. Can you suggest some Linux commands jeremy31?

---

### Post by jeremy31 on 2017-02-19
If you still have the media you installed Linux Mint from, does booting it up allow the wifi to work correctly?

If you don't want to use the internal you could blacklist the kernel module with ```
echo "blacklist rt2800pci" | sudo tee -a /etc/modprobe.d/blacklist.conf
```
Removing the card from the machine would be preferred if it is easy to do, or to disable the internal WLAN in BIOS might work.  There may be instructions online on how to replace the wifi card on your HP model and it might be easy to replace what you have with an Intel 7265

---

### Post by afz12 on 2017-02-19
Hi jeremy

Thanks for your reply. The USB stick usually gets the modem to work but this could be a high current drain procedure and again points to a modem voltage sensitivity issue. The internal modem is working fine now for quite some time on batteries - I'll recharge later and retest a few times.

I could remove the complete notebook' bottom cover to access the modem but I'm unsure what I might find! I think I'd prefer to let sleeping dogs lay on that one.

Thanks for the Linux command - I'll use this later. If for experimental purposes I want to reactivate it, is there a command to un-blacklist it?

I could replace the modem but these are extremely expensive here. Using an external dongle is a lot less expensive and the small nano ones are as small as those used for a wireless mouse (good range also!) - this seems the most pragmatic solution. Interestingly I have looked in BIOS but didn't see a command to deactivate the modem, but I may have missed this. I'll take another peek.

---

### Post by jeremy31 on 2017-02-20
You could use this command to unblacklist
```
sudo sed -i 's/blacklist rt2800pci/#blacklist rt2800pci/' /etc/modprobe.d/blacklist.conf
```

---

### Post by afz12 on 2017-02-20
Hi jeremy31

Thanks for the code - this is excellent. I tried both instructions in a terminal and both were accepted OK.

I have been investigating voltage sensitivity issues with this WiFi modem - his is definitely a fault local to this notebook that by one way or another affects its WiFi modem. I let its battery drain down and rebooted - most times the WiFi enabled. However once the charge, as reported by the OS got to about 95% the WiFi modem would not enable.

I removed the notebook's modem cover and pulled the modem PCB out and put it back in its socket a few times. It had what looked like 2 MCX RF connectors presumably going off to antennas so I did the same with these. If the modem was loose this should have fixed it. However the notebook's behavior was the same afterwards.

I left the notebook running overnight on power with a USB dongle inserted, on power and with the internal modem still off. This morning, the dongle WiFi still works and the internal modem is still off.

I have an older hp dv6 notebook that also had a physical fail for its internal modem and it also uses an external TP-Link TL-WN725N USB dongle modem now. This works fine in its Linux Mint 18.1 and Ubuntu 16.10. This model also works fine in this notebook running Ubuntu 17.04 alpha 2 and Mint 18.1. I suspect its internal modem is on its last legs as this interpretation is consistent with all observations to date as well as previous history with a somewhat similar notebook of the same hp brand - possibly a precursor of sorts to this hp Envy version and therefore probably entertained by the same modem manufacturer. It is not unrealistic to consider that a similar modem reliability deficit could exist between the two, given this. In all cases though this interpretation is consistent with all findings to date and in stark contrast, the router fault hypothesis has no boxes ticked, nor if even so, issues with public WiFi could never be solved by attacking a local router as a solution.

Anyway my interpretation so far is that this notebook's modem or something that drives it is at fault, and certainly, also, this is definitely not an issue that relates to any particular operating system at all. Most likely the physical hardware, in this case the modem PCB, is on its last legs. Given this, there is no software solution to this other than to deactivate it as per your code jeremy31 and pull the PCB out much he same way as extracting a bad tooth;). I apologize for seeking a software solution for what appears to be a hardware fault, but given the forum's inability to find a software solution when one most probably doesn't exist, this exercise has served to have removed this adventure as a possibility. I guess according to Sherlock Holmes' wise quote, going something like, "Once you remove every explanation that is impossible, then what remains, however implausible, must be the truth!"

Thanks jeremy31. The external USB dongle modem is a perfectly satisfactory solution and seems to be going quite well.:p):P

---

