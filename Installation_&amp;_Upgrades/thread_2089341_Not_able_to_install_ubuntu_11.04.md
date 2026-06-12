---
title: "Not able to install ubuntu 11.04"
date: 2012-11-29
forum: Installation &amp; Upgrades
---

### Post by farjibaba on 2012-11-29
I am using a computer which was having win 7 pro. make SIS model- Q77-MD2 configuration intel core i5, 3043.86 MHZ, 500 HDD, 4 GB Ram and intel Q77 Chip set. I can install all versions of windows and RHEl 5.3 but I am not able to install Ubuntu 11.0, when i start installation system goes shut down without any error. Neither It is installing in live mode nor in text mode. and I have tried to format the all partition of windows and made my HDD raw even also I was not able to install ubunt
my Image is aslo very good md5 matched and not corruptd

Please help me or PM me any suggession..

---

### Post by mr.suchy on 2012-11-29
You don't describe everything so I quess that you can input a name, password in installation but suddenly system is out. Try this. Run Ubuntu with live cd and enter this command in terminal:

```
sudo apt-get remove ubiquity-slideshow-ubuntu
``` 

Then run installation from desktop.

---

### Post by mörgæs on 2012-11-29
Besides, 11.04 is obsolete, so it's only good that it does not install :-)

Go for 12.04 or 12.10. You could try the idea posted above or use the alternate installer (which unfortunately is only available for Lubuntu):
[http://cdimage.ubuntu.com/lubuntu/releases/12.10/release/](http://cdimage.ubuntu.com/lubuntu/releases/12.10/release/)

---

### Post by sudodus on 2012-11-29
Welcome to the Ubuntu Forums farjibaba,

Ubuntu 11.04 is old and the detection of new hardware is much better on the current versions of Ubuntu. Actually, 11.04 has passed end of life, and there are no security updates.

Instead I suggest that you download the iso file of Ubuntu 12.04 LTS (long time support until april 2017) and make a boot CD/DVD/USB drive.

See this link
[[COLOR="Red"]http://www.ubuntu.com/download/help/try-ubuntu-before-you-install[/COLOR]]("http://www.ubuntu.com/download/help/try-ubuntu-before-you-install")

---

### Post by farjibaba on 2012-11-29
> **mr.suchy said:**
> You don't describe everything so I quess that you can input a name, password in installation but suddenly system is out. Try this. Run Ubuntu with live cd and enter this command in terminal:

```
sudo apt-get remove ubiquity-slideshow-ubuntu
``` 

Then run installation from desktop.

Please tell me what else you want, when I press Enter on install in hard drive nothing happen and my system goes sleep automatically. System does not ask any password and there is no command shell and I am bound to install this version only. It is also not runnig in live mode. and my another 5 machines have install without any problem but only this machine which is newly procured and I am not able to install.....

please help me

---

### Post by sudodus on 2012-11-30
> **farjibaba said:**
> Please tell me what else you want, when I press Enter on install in hard drive nothing happen and my system goes sleep automatically. System does not ask any password and there is no command shell and I am bound to install this version only. It is also not runnig in live mode. and my another 5 machines have install without any problem but only this machine which is newly procured and I am not able to install.....

please help me
Particularly on new computers, it is better to use up-to-date versions of Ubuntu, because it is better at recognizing the hardware. So again I suggest that you download the newest long time support version Ubuntu 12.04 LTS or some other flavour (Kubuntu, Lubuntu or Xubuntu) and try it.

Test it live! If it works live, it will also work when installed. Tweak with boot options if necessary!

---

