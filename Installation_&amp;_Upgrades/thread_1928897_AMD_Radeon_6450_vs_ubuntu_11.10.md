---
title: "AMD Radeon 6450 vs ubuntu 11.10"
date: 2012-02-20
forum: Installation &amp; Upgrades
---

### Post by uRock on 2012-02-20
Just bought a new PC which came with an AMD Radeon HD 6450 card. The e11.10 LiveCD booted and ran fine for the installer. Restarted. After selecting ubuntu from the grub menu it goes directly to a blinking purple screen. What should I try in order to get this thing working?

Thanks:D

---

### Post by uRock on 2012-02-21
I was folling the advice here [http://askubuntu.com/questions/54437/hd-6450-radeon-problems-with-installation](http://askubuntu.com/questions/54437/hd-6450-radeon-problems-with-installation) and when I got to the folling command it errored out as follows,
```
sudo ./ati-driver-installer-117-x86.x86_64.run
./ati-driver-installer-117-x86.x86_64.run: 1 Syntax error: redirection unexpected
```Also tried this without any luck,```
sudo sh ./ati-driver-installer-117-x86.x86_64.run
```Any thoughts?

---

### Post by uRock on 2012-02-21
I am thinking this driver needs me to be in GUI to install it, if so, how do I install it without being in the GUI?

Inspecting the bin shows that it is trying to run html, is there another way to install this or am I out of luck?

---

### Post by mastablasta on 2012-02-21
what do you mean "without any luck"? same error?: Syntax error: redirection unexpected
 
it should work in terminal. you did chmod and you are at the right place and typed in the right file name?
 
is there any other GPU in the PC?
 
have you tried nomodeset, xforcevesa, recovery mode ?

---

### Post by uRock on 2012-02-21
I did chmod +777 the .run file. I even renamed it to remove the first "." from the file name. When examining the file I see that it is a html, which I think needs to be in the GUI to run. 

I am gonna shut the machine down(currently running Windows), then remove the ATI card and see if the onboard card will run. If it does run, then I will install the driver, then reinstall the hardware. A lot more work than I wanted to go through.:(

---

### Post by uRock on 2012-02-21
After removing the hardware and booting from the mobo graphics I was able to go to the site to download the driver and I found where the problem is. In the cli for wget, chmod and sudo the filename should have started with amd instead of ati. I now have the proper driver installed and saved for future use, because I have read that it will have to be reinstalled with every kernel upgrade. 

The commands I should have run,```
wget http://www2.ati.com/drivers/linux/amd-driver-installer-12-1-x86.x86_64.run
chmod +x amd-driver-installer-12-1-x86.x86_64.run
sudo ./amd-driver-installer-12-1-x86.x86_64.run

```

---

### Post by cromat on 2012-02-22
Interesting I didn't realize that anyway, I have had no serious issues with the latest 12.1 driver from ATI.

---

### Post by uRock on 2012-02-22
> **cromat said:**
> Interesting I didn't realize that anyway, I have had no serious issues with the latest 12.1 driver from ATI.

It is the 12.1 driver from ATI. I had no problems with it, either. The command to fetch it that I found was not written correctly.

---

### Post by angryfirelord on 2012-02-22
I've always ran it this way:
```
sudo sh ati-driver-installer-117-x86.x86_64.run
```
Seeing as how I'm about to order a 6450 (in order to replace the onboard graphics), I'll let you know if I run into the same problem.

---

### Post by uRock on 2012-02-22
> **angryfirelord said:**
> I've always ran it this way:
```
sudo sh ati-driver-installer-117-x86.x86_64.run
```
Seeing as how I'm about to order a 6450 (in order to replace the onboard graphics), I'll let you know if I run into the same problem.

When I ran the wget command from the recovery console for the ati driver listed in the link, it was downloading an html file.

---

### Post by angryfirelord on 2012-03-04
Just as a follow up, this card didn't didn't work for me. I tried it under both Scientific Linux 6 and Fedora 16, but the card simply gave me a black screen upon trying to load X. The catalyst drivers didn't work either, so I ended up having to return it. Phoronix managed to use it for their testing, so I'm not sure why I wasn't able to get it to work.

---

### Post by steve. on 2012-04-27
For others with the same issue this is how I got AMD Radeon 6450 to work on 12.04 32bit. 
It worked perfect when booted live.
After installation video failed to be useful so rebooted
Selected recovery and video was fine.
Tried updating drivers using "Additional Drivers" from Dash Home.
ATI/AMD proprietary FGLRX graphics driver (post-release updates) - failed :(
Rebooted into recovery again and selected
ATI/AMD proprietary FGLRX graphics driver - worked :)

---

