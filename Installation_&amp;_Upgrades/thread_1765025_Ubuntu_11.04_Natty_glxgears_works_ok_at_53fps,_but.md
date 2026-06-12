---
title: "Ubuntu 11.04 Natty: glxgears works ok at 53fps, but not Unity 3D, and ideas please??"
date: 2011-05-22
forum: Installation &amp; Upgrades
---

### Post by Sun.Dial on 2011-05-22
Setup: Toshiba M300 laptop, Ubuntu 11.04, Intel 855GM graphics

Hi,
I've persevered with this for 2 days searching for answers and trying many, but still no success.
On a previous installation of Ubuntu 9.10 I had similar problems with Compiz, but managed to get all the 3D effects working in the end, so I am assuming I will eventually succeed with 11.04 on the same laptop.

I have found recommendations referring to 'glasen' drivers for the 855 graphics, and following the instructions thought I would end up with an 'additional driver' for the Intel chips, but did not.

Other posts referred to 'glxgears' which works at about 53fps.

I have Ubuntu-Tweak installed and the option for Unity  in Compiz manager is checked.
None of the Compiz effects work.

When rebooted, the logon menu available after I click on my username does not mention Unity by name, but the word Ubuntu is in italics, and also Ubuntu Classic but in normal typeface.

When I first installed 11.04, the system informed me that I did not have the correct hardware to run Unity at that point, and defaulted to the desktop I am used to from 10.10, Gnome.

I would like to try Unity and so any help or advice would be greatly appreciated.

Thanks,
Sun

---

### Post by dronkot on 2012-02-11
I have same chipset and same problem :-(:-(. Seems like problem here is in enabling 3D for this chipset in Ubuntu 11.04.   Have you fix this problem?

---

### Post by Cookieh on 2012-02-11
Does your driver support 3D mode?
If no, get a new driver.
If yes then, check that your driver is the current newest version, if not then update it, but I think there is a new one :
[http://www.technomagz.com/ubuntu-11-04-intel-855gm.html](http://www.technomagz.com/ubuntu-11-04-intel-855gm.html)

---

### Post by Cookieh on 2012-02-11
One more thing, have a look at this, as this has helped my friend:

[https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver)

---

### Post by Sun.Dial on 2012-02-16
Thanks for your replies, I must admit I'd all but given up, and they pushed me to try again. I have downloaded the latest driver from Glasen (and many thanks to him for his efforts), and it seems I now have a driver by the name of i95. This does not mean anything to me at present, but now GLXgears works at 61fps and it looks like 3D shadow effects are present (as they were before though). However, all of this has not resulted in any difference to the interface I see, which is 2D. It could be that there is some 'tick box' which needs to be checked, but having tried all the Compiz settings, I haven't found one yet. Thank you very much for trying to help. Sun

---

### Post by Sun.Dial on 2012-02-16
...forgot to include that I am using Ubuntu version 11.10 now.

---

