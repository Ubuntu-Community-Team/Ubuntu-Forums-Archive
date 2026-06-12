---
title: "ati/amd proprietary fglrx graphics driver"
date: 2011-03-21
forum: Installation &amp; Upgrades
---

### Post by h9uest on 2011-03-21
Hi people:

I'm using ubuntu 10.04, and I have the fglrx graphics driver suggested by the system. I installed it, but will never be able to restart my ubuntu. While it's loading ubuntu, it gets stuck forever. That forced me to reinstall ubuntu for a couple of times, and now I don't dare to install the graphics driver again.

As a result, I don't have 3-D acceleration, which is really sub-optimum.

Can anyone share some inputs on this issue? Is there a possible work-around?

Thanks in advance.

---

### Post by Mark Phelps on 2011-03-21
Without knowing the make and model video card/chip, it's hard to provide specific advice ...

If you don't know what that it, open a terminal and do "lspci".  Look for the line that has "VGA" in it.

---

### Post by h9uest on 2011-04-09
> **Mark Phelps said:**
> Without knowing the make and model video card/chip, it's hard to provide specific advice ...

If you don't know what that it, open a terminal and do "lspci".  Look for the line that has "VGA" in it.

Hi Mark:

Sorry for the delay:

VGA compatible controller: ATI Technologies Inc Mobility Radeon HD 3400 Series


That's the graphics card, I think.

---

### Post by coffeecat on 2011-04-09
It's disappointing that you are not getting 3d with the default open source driver in Lucid and your Mobility HD3400 card. With both my laptop Mobility HD4200 and desktop HD4350 I get good 3d with the open source driver.

The default open source ATI driver in Maverick is better than the one in Lucid. Try downloading the ISO for Maverick/10.10 and running that live to see if you can get 3d. I know this is not an optimum solution but 10.10 may work better for you.

---

### Post by GopalaDasa on 2011-04-14
Same problem here! Stuck! Now going to re-install the Ubuntun and wont dare to install any suggestion unless I know what it may cause the trouble! :(

As I am doing all these practical in my brand new laptop so no data is there.

But I am wondering what if I have data in my laptop and if it ever cause such trouble then that may put me to format my system and I may loose the data.

ANy solution for such situation? Thank you!

---

### Post by coffeecat on 2011-04-14
> **GopalaDasa said:**
> But I am wondering what if I have data in my laptop and if it ever cause such trouble then that may put me to format my system and I may loose the data.

If you ever find yourself in the situation of having a system that you cannot boot into the GUI with because of a bad video driver and you have data to rescue, this is easily done with the live CD. Something you cannot do with Windows.

---

