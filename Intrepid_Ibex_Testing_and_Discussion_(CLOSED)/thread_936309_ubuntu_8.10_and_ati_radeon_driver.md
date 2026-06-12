---
title: "ubuntu 8.10 and ati radeon driver"
date: 2008-10-02
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by patrick102 on 2008-10-02
Hi all, 

New to linux but I am very very impressed. The customisation features, the menu interface and the sheer performance and layout of this OS is a true beauty. Awesome....

anyway,

I installed ubuntu 8.10 and had an unexpected problem. The auto installer in the hardware installation package ('hardware drivers' in the system menu) bundled with ubuntu will not download ati radeon drivers when i am running 8.10. I have re-installed ubuntu 8.04 and installed the drivers without a problem. Just an observation. I have a radeon 9800 pro. Just a warning to anyone planning to install ati drivers on 8.10. I understand you can install them manually but there we go. In the installer, when it goes to download the driver, it stays on 0% downloaded and then wont close or do anything. Other things will still run normally in the background though. 

I love ubuntu :popcorn:

---

### Post by Sef on 2008-10-02
Moved to Ibex forum.

---

### Post by ktp on 2008-10-02
> **patrick102 said:**
> Hi all, 

New to linux but I am very very impressed. The customisation features, the menu interface and the sheer performance and layout of this OS is a true beauty. Awesome....

anyway,

I installed ubuntu 8.10 and had an unexpected problem. The auto installer in the hardware installation package ('hardware drivers' in the system menu) bundled with ubuntu will not download ati radeon drivers when i am running 8.10. I have re-installed ubuntu 8.04 and installed the drivers without a problem. Just an observation. I have a radeon 9800 pro. Just a warning to anyone planning to install ati drivers on 8.10. I understand you can install them manually but there we go. In the installer, when it goes to download the driver, it stays on 0% downloaded and then wont close or do anything. Other things will still run normally in the background though. 

I love ubuntu :popcorn:

Is this the open source or the nonfree drivers?  I know there is an issue with nonfree drivers (from AMD/ATI) not working with new XOrg/Xserver.

---

### Post by MilesRdz on 2008-10-02
I don't think the restricted driver manager installs the latest working ATi driver. :(

---

### Post by sdowney717 on 2008-10-02
Unfortunately, ATI proprietary non free driver does not support xorg 7.4 and xserver 1.5 which are in Ibex. So you must use the free radeon driver.
ATI is behind on this and will eventually catch up.

---

### Post by patrick102 on 2008-10-03
incidently, i am running free version

thx

i dont know when is best time to upgrade though.... maybe i dont need to ever as everything is fine at the moment.

---

### Post by sdowney717 on 2008-10-04
the hardware drivers install system-admini-hardware drivers installs the non free drivers.

---

### Post by Lorenz on 2008-10-04
I'm having the same "problem" but it's ok, I can exist without Compiz for some time :)

---

### Post by inportb on 2008-10-04
Hm? The opensource radeon driver supports compositing very well.

---

### Post by patrick102 on 2008-10-05
lol i assumed that as i installed from the bundled software the app had installed the free driver. that explains it.

---

### Post by shellster on 2008-10-06
I use the ATI Radeon 9800 Pro on my Ubuntu box as well.  I also had to do some minor tweaking to get things running on intrepid.  My experience, has been that this particular card is always badly, or not ever supported in beta releases of Ubuntu.  I don't know why that is, but other ATI cards seems to work out of the box, but the  9800 Pro will 99% of the time, break.

Don't get my wrong, I don't mind taking the time to tweak things, but I am just saying...

---

