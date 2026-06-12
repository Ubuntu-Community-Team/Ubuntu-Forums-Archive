---
title: "How do you: Install proprietary nvidia drivers on 11.04?"
date: 2011-05-05
forum: Installation &amp; Upgrades
---

### Post by Newuser901 on 2011-05-05
Can't find anything directly telling you how to get the newest drivers for 11.04. can anyone help? I need something blunt. Not managing to find much at all actually. I'm running eve in wine and I was hoping that would help deal with some graphics problems that just started happening. I"m not sure why they got there. I have been playing on it since 11.04 came out and no problems. I did remove and reinstall wine or some parts of it(not sure which they were I barely got it working since I don't understand what it what in the ubuntu install directory thing) and reinstall and there were some updates about the time this happened. I now get anomalies graphics wise oh high settings, or more specifically several of the graphics settings when you put them medium to high or on. It partly makes it look like you have the ubuntu desktop pulled back showing your default 4 desktops but with the games background transfused over the whole screen with all of the parts adjusted to unusual positions. There are other anomalies but that is one of the distinctive ones. I was planning on using the newest drivers anyway. I was hoping they would run better, but I never did it. I was trying to avoid reinstalling EVE since I don't want to use the bandwidth since I'm on AT&T and the jackasses have now nubbed my 6mbit connection down to 250gbytes a month and I don't live alone and can't change the damned thing even though it was in my name originally.... 8(

---

### Post by mikewhatever on 2011-05-05
The latest Nvidia driver for 11.04, 270.41.06, is available through the repositories. If you haven't been prompted to install it yet, search for and install the 'nvidia-current' package from the Software Center.

---

### Post by Lubelaczek on 2011-05-05
> **mikewhatever said:**
> The latest Nvidia driver for 11.04, 270.41.06, is available through the repositories. If you haven't been prompted to install it yet, search for and install the 'nvidia-current' package from the Software Center.
 
Many of us do that and it says: drivers installed but not currently in use (or something like that). Why? I have no idea... Any working solution yet, guys?

---

### Post by mikewhatever on 2011-05-05
Not sure really. Some of those have dual cards (Intel/Nvidia), which is the setup that I hear Linux doesn't cope well with.

---

### Post by VanR on 2011-05-05
> **Lubelaczek said:**
> Many of us do that and it says: drivers installed but not currently in use (or something like that). Why? I have no idea... Any working solution yet, guys?

I would just ignore what it says about the driver is not in use. In my case it most certainly was in use. Go to System>Administration>Nvidia X Server Settings and see if the latest driver is in use. 270.14.06. I'm even using it on Zorin OS 4 (10.10 Maverick)

---

### Post by Newuser901 on 2011-05-06
Is the driver on 11.04 now the latest nvidia driver? On 10.10 it was not the latest and you had to add them to the repository somehow with the terminal.

---

