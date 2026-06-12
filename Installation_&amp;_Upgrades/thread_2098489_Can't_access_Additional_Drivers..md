---
title: "Can't access Additional Drivers."
date: 2012-12-26
forum: Installation &amp; Upgrades
---

### Post by Thepinkgamer on 2012-12-26
Hello. Sorry in advance for my bad grammer. I am dyslectic. 


Today I wanted to install Steam on my Ubuntu computer after reading that the beta was out. I installed it and everything worked I wast just going to upgrade the drivers for my computer cus I was following the steps listed on the Ubuntu website 


"AMD/ATI Graphics

1 Enable the pre-released updates. You can enable this repository by opening Ubuntu Software Center, selecting Edit | Software sources... and then enabling the Pre-released updates option on the Updates tab.

2 Update your repository to the latest version in the Update Manager.

3 Remove the currently installed drivers.

4 In 12.04, launch the Additional Hardware Drivers dialog from System Settings. In 12.10, launch Software Properties, then click on the Additional Drivers tab in the Software Sources menu.

5 Install the newest fglrx-experimental-X driver."


Now the only thing I know that I did wrong was hat I removed the currently installed drivers before updating my repository. Anyways after updating my repository I was going to install the drivers like step 4 tells me. I open my system settings and click on Additional drivers. It checks for drivers and then nothing. The program doesn't even start up. I tried restarting my computer but it still doesn't want to start.

I tried removing it via the Software center and then installing it again. But that didn't help ether :( 

It really sucks cus I have no additional drivers not and my system is running slower because of it. 

Anyone here who knows a way to fix it? maybe installing the drivers via the terminal or something.

I use a emachines E730G the stickers on it says intel CORE i3 and ATI mobility Radeon HD 5470 Graphics 512 MB. I don't really know a lot about hardware so don't ask anymore about it :P

---

### Post by koreymc on 2013-01-03
I'm having the exact same problem.  I just upgraded from 10.10 to 12.04 last night.  After updating the repository I installed Steam, then when following the steps mentioned above, the Additional Drivers program wouldn't open anymore, though it would open and show a couple of drivers at some point earlier.

Any help would be greatly appreciated.  I was thinking of reinstalling 12.04 since I haven't done anything yet.  Is it enabling the "pre-released updates" that's messing things up?  Thanks.

---

### Post by bpb101 on 2013-01-03
graphics cards , whats the graphics ?

---

### Post by Frogs Hair on 2013-01-03
I'm not positive if this is what you are looking for and I don't know why additional drivers would not open. There appears to be a number of web pages in regards this topic. I would do some more research prior to installing the package at the link.  

[http://www.ubuntuupdates.org/package/core/precise/restricted/proposed/fglrx-experimental-9](http://www.ubuntuupdates.org/package/core/precise/restricted/proposed/fglrx-experimental-9)

---

### Post by bpb101 on 2013-01-03
> **Frogs Hair said:**
> I'm not positive if this is what you are looking for and I don't know why additional drivers would not open. There appears to be a number of web pages in regards this topic. I would do some more research prior to installing the package at the link.  

[http://www.ubuntuupdates.org/package/core/precise/restricted/proposed/fglrx-experimental-9](http://www.ubuntuupdates.org/package/core/precise/restricted/proposed/fglrx-experimental-9)

i was proable going to link them their , worked wonders for my amd radon hd 6670 
just left a watermark - it is removed by 

                                  Remove watermark amd 12.11  beta
 

 

 

 sudo gedit /etc/ati/signature
 Replace UNSIGNED with
 

> 9777c589791007f4aeef06c922ad54a2:ae59f5b9572136d99fdd36f0109d358fa643f2bd4a2644d9efbb4fe91a9f6590a145:f612f0b01f2565cd9bd834f8119b309bae11a1ed4a2661c49fdf3fad11986cc4f641f1ba1f2265909a8e34ff1699309bf211a7eb4d7662cd9f8e3faf14986d92f646f1bc
 

  

---

### Post by koreymc on 2013-01-03
My video card's an ati radeon hd 4650.  I think from some other threads it looked like the newest driver may not work with mine since it's a little older?  Searching for my card on AMD's site, they list Catalyst 12.6 for mine, which I believe is a slightly older version of the driver.

I'll try to look some more about this issue, but I haven't been able to find much yet specifically about the additional drivers program no longer opening.  I've seen plenty of other Steam and AMD driver problems, though.

---

### Post by Mark Phelps on 2013-01-04
> **koreymc said:**
> My video card's an ati radeon hd 4650.  I think from some other threads it looked like the newest driver may not work with mine since it's a little older?  


Correct ... AMD dropped restricted Linux driver support for your card this summer.  The current working drivers will not run in Ubuntu 12.10 because they need an older version of the X-server than is installed with 12.10.

You are limited now to using the open-source Radeon drivers -- which are installed by default.

If you try to force the installation of an AMD driver, you will trash your display and have a LOT of work ahead of you removing those drivers, and replacing them with the default drivers.

---

