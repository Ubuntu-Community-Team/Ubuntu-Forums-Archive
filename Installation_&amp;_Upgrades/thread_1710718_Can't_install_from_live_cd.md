---
title: "Can't install from live cd"
date: 2011-03-20
forum: Installation &amp; Upgrades
---

### Post by 16sinker on 2011-03-20
I'm attempting to install Ubuntu on a Gateway laptop that is a 3.06 gigahertz Intel pentium 4 with 1 gig of ram. I'm using the live cd but can't get the computer to boot to the cd. My BIOS is set to boot from cd/rom but I'm not getting the typical Ubuntu menu, which includes install, when I boot the computer. I get the Ubuntu loading screen with the graphical loading dots and when that completes I get a blank screen. I've installed Ubuntu on 4 or 5 other PCs and have never had this problem. I'm trying to completely remove XP and replace with Ubuntu 10.04 LTS. Normally on booting from the Ubuntu cd I get a menu immediately which includes complete installation, but not with this computer. What am I missing?

---

### Post by Dutch70 on 2011-03-20
At install screen press F6 and select nomodeset.

---

### Post by Tuexnovia on 2011-03-20
> **16sinker said:**
> I'm attempting to install Ubuntu on a Gateway laptop that is a 3.06 gigahertz Intel pentium 4 with 1 gig of ram. I'm using the live cd but can't get the computer to boot to the cd. My BIOS is set to boot from cd/rom but I'm not getting the typical Ubuntu menu, which includes install, when I boot the computer. I get the Ubuntu loading screen with the graphical loading dots and when that completes I get a blank screen. I've installed Ubuntu on 4 or 5 other PCs and have never had this problem. I'm trying to completely remove XP and replace with Ubuntu 10.04 LTS. Normally on booting from the Ubuntu cd I get a menu immediately which includes complete installation, but not with this computer. What am I missing?

> **Dutch70 said:**
> At install screen press F6 and select nomodeset.

If I am right, this link will help you TOO. 
They speak about NOMODESET.
[http://ubuntu4beginners.blogspot.com/2011/01/ubuntumaverick-blank-screen-problem.html](http://ubuntu4beginners.blogspot.com/2011/01/ubuntumaverick-blank-screen-problem.html)

---

### Post by Dutch70 on 2011-03-20
Well, what a coincidence. One guy from Kentucky & one from London. 
 I'm in London, KY. Couldn't resist pointing that out. 

Where are you in KY 16sinker?

---

### Post by 16sinker on 2011-03-20
> **Dutch70 said:**
> At install screen press F6 and select nomodeset.

I pressed f6 and selected nomodeset and pressed enter, but nothing happens. Is there another key to press rather than enter?

---

### Post by Quackers on 2011-03-20
What graphics card is used on the laptop? A different boot option may be required - like one of the i915.modeset options.

---

### Post by Dutch70 on 2011-03-20
> **16sinker said:**
> I pressed f6 and selected nomodeset and pressed enter, but nothing happens. Is there another key to press rather than enter?

Did you try the following, from the link given above? 

> Once you see this page, press F6 and you'll see some options pop up. Navigate to nomodeset and hit Enter. You'll see a mark in the beginning. **Press Esc and now choose Try Ubuntu Without Installing or Install Ubuntu, whichever you want to**

---

### Post by 16sinker on 2011-03-20
> **Dutch70 said:**
> Did you try the following, from the link given above?

Don't know what graphics card is in the computer, but I selected nomodeset, pressed enter and esc. Chose install ubuntu and even selected english language then pressed enter. The boot screen appears with the loading dots and when it appears the loading is done, I get a blank screen and nothing follows.

---

### Post by Dutch70 on 2011-03-20
Please run this command in terminal and post the output between code tags by using the "#" in the toolbar. 
That will tell you your graphics card.

```
lspci | grep VGA
```

---

### Post by Quackers on 2011-03-20
Try other boot options, but don't press Esc after selecting the option and pressing enter.

---

### Post by 16sinker on 2011-03-20
> **Dutch70 said:**
> Please run this command in terminal and post the output between code tags by using the "#" in the toolbar. 
That will tell you your graphics card.

```
lspci
```

I can't get to terminal on the computer in question.

---

### Post by 16sinker on 2011-03-20
> **Dutch70 said:**
> Please run this command in terminal and post the output between code tags by using the "#" in the toolbar. 
That will tell you your graphics card.

```
lspci
```

> **Dutch70 said:**
> Well, what a coincidence. One guy from Kentucky & one from London. Although my location says Corbin KY.
 I'm technically in London, KY. Couldn't resist pointing that out. 

Where are you in KY 16sinker?

Hopkinsville

---

### Post by 16sinker on 2011-03-20
I seem to be having problems with this computer aside from my problem installing Ubuntu. The computer is automatically shutting down now as if it were over heating. I'll pursue the installation of Ubuntu later. Thanks for the tips this morning.

---

### Post by 16sinker on 2011-04-08
> **16sinker said:**
> I seem to be having problems with this computer aside from my problem installing Ubuntu. The computer is automatically shutting down now as if it were over heating. I'll pursue the installation of Ubuntu later. Thanks for the tips this morning.

Good news. I found out that my pc has an IntelR Graphics Controller and that being the case i added i915.modeset=1 to the end of the line after "quiet splash", hit enter and I am now installing Ubuntu 10.04 LTS. Hooray!!:D

---

### Post by Quackers on 2011-04-08
That's good :-)
If it installs and runs ok keep an eye on the temperature.

---

### Post by 16sinker on 2011-04-08
> **Quackers said:**
> That's good :-)
If it installs and runs ok keep an eye on the temperature.

The good news is, Ubuntu installed. The bad news is, after restarting, the computer shows the graphical boot screen and then I get a page with some errors that indicates I need to go to linux.com. The page disappears so quickly that I can't read the complete text. I then get a blank screen. As to the temperature, the machine seems to be running hot and shuts off automatically after a few minutes of the blank screen. Any suggestions?

---

### Post by Quackers on 2011-04-08
Did you use the nomodeset option to get the live cd to boot?
If so, you will need to select that option the first time you boot Ubuntu.
Hold down the shift key during boot up. You will see a grub menu (hopefully) with the top item highlighted. Press the "e" key then on the next screen navigate to the end of the line which ends "quiet splash" and then enter a space and the word "nomodeset"  (without the quotes) then press ctrl + X to boot.
If it's getting hot without even really booting there may be a more serious problem though.

---

### Post by 16sinker on 2011-04-08
> **Quackers said:**
> Did you use the nomodeset option to get the live cd to boot?
If so, you will need to select that option the first time you boot Ubuntu.
Hold down the shift key during boot up. You will see a grub menu (hopefully) with the top item highlighted. Press the "e" key then on the next screen navigate to the end of the line which ends "quiet splash" and then enter a space and the word "nomodeset"  (without the quotes) then press ctrl + X to boot.
If it's getting hot without even really booting there may be a more serious problem though.

No, I didn't use nomodeset. This link [http://ubuntu4beginners.blogspot.com...n-problem.html](http://ubuntu4beginners.blogspot.com...n-problem.html) indicates that since I have an Intel Graphics Controller, I should skip nomodeset by clicking escape and add the i915.modeset=1 boot parameter to the end of the line after "quiet splash". I did that and the installation proceded. Hope that answers your question.

---

### Post by 16sinker on 2011-04-08
> **16sinker said:**
> No, I didn't use nomodeset. This link [http://ubuntu4beginners.blogspot.com...n-problem.html](http://ubuntu4beginners.blogspot.com...n-problem.html) indicates that since I have an Intel Graphics Controller, I should skip nomodeset by clicking escape and add the i915.modeset=1 boot parameter to the end of the line after "quiet splash". I did that and the installation proceded. Hope that answers your question.

So, I used your instructions relative nomodeset, but instead added the i915.modeset=1 parameter to the end of the line after "quiet splash". hit ctrl X and it booted! I am now looking at my ubuntu desktop. So, thanks for your help Quackers. For now this thread is solved.

---

### Post by 16sinker on 2011-04-08
Ok, I now have the boot process in place on this computer and have made the changes in the boot parameter permanent. My problem now is that I can't connect to my wireless network. This computer connected fine running windows XP, but now I can't connect with Ubuntu. I do have my desktop and access to terminal. Can someone help?

---

### Post by Quackers on 2011-04-08
I'm glad thinks are going better :-)
Can you connect to your router with an ethernet cable? You should then be able to get any wireless card drivers and graphics drivers. (If graphics drivers are installed you may not need the i915.modeset=1 boot option - in fact you probably won't).

---

### Post by 16sinker on 2011-04-08
> **Quackers said:**
> I'm glad thinks are going better :-)
Can you connect to your router with an ethernet cable? You should then be able to get any wireless card drivers and graphics drivers. (If graphics drivers are installed you may not need the i915.modeset=1 boot option - in fact you probably won't).

No, but I can disconnect router from ethernet cable and hook up directly, get my updates and drivers and go from there. Hadn't thought of that. Thanks. I'll let you know.

---

### Post by 16sinker on 2011-04-09
Well, I'm back to let you know, that I can't get this computer on line, wireless or by ethernet cable. I've got a good install of Ubuntu apparently, cause I've been able to customise the desktop to suit me. I don't know if I have any options or not as far as installing drivers and such and especially getting the updates for the last year for 10.04 unless I get online. As I mentioned earlier, I can access terminal, if anyone has some command line diagnostics. I'll have to enter commands manually from another computer, but I'm willing to try  if anyone has suggestions. Thanks.

---

### Post by 16sinker on 2011-04-09
Never mind about the manual command line input, I could maybe do that, but I would have no way to copy and past output. I have tried a netgear wireless adapter with no luck. Just need to get online somehow.

---

