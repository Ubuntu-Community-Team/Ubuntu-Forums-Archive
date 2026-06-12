---
title: "Upgrade fails"
date: 2020-03-11
forum: Installation &amp; Upgrades
---

### Post by py-ohayo on 2020-03-11
Hello,

While executing an upgrade I get the following message:

[IMG]https://i.postimg.cc/631SPLC8/Screenshot-from-2020-03-11-16-34-37.png[/IMG]

How to resolve the problem ?

Thanks

---

### Post by mörgæs on 2020-03-12
Your screenshot shows two suggestions. I don't have better ideas than what's already posted.

---

### Post by py-ohayo on 2020-03-12
Does 1st suggestion mean that I have to uncheck "brown-color" cases here:

[IMG]https://i.postimg.cc/Twz0YPKq/Screenshot-from-2020-03-12-11-20-46.png[/IMG]

Also, I did not understand what is the second suggestion

---

### Post by ajgreeny on 2020-03-12
Are you trying to upgrade from one version of Ubuntu to the next, eg from 19.04 to 19.10, or is this just upgrading the packages on your system?

If you are trying the first you **must disable all PPA repositories**, including any graphics driver PPAs, which I believe is what you have; I've never used an Nvidia card so I'm not completely sure if that's so, but it looks that way to me.

Disable those three items shown and try the upgrade again. After that you can investigate those PPAs again.

---

### Post by py-ohayo on 2020-03-12
I want to just upgrade  package, not Ubuntu version (BTW I have 18.04).
To do this I click on the new icon that regularly appears since yesterday on the top of screen (please see screenshot below): red circle with white line.

[IMG]https://i.postimg.cc/DyShNvsf/Screenshot-from-2020-03-12-12-02-17.png[/IMG]

I've tried to uncheck these 3 items, but I couldn't !
I click on them, but nothing happens.

---

### Post by dino99 on 2020-03-12
Why having two cuda entries enabled ? This might reveal some conflict against the used nvidia driver.

Purge them and reinstall nvidia only; If your problem is gone, also do the second step: apply the compatible cuda version.

---

### Post by py-ohayo on 2020-03-12
First I've installed 418 version of the driver by following some manual.
Then I realized that 418 is not compatible with my CUDA version.
That's why I've installed 440 version, which is Ok with my CUDA 10.2.
Can you suggest how do deinstall just 418 ?
Thanks

---

### Post by ajgreeny on 2020-03-12
> Can you suggest how do deinstall just 418 ?
Thanks 
That will depend on how you installed it by "following some manual".

What manual was that and what did you actually do when following the manual; we really can't help as you've not told us enough so far.

---

### Post by py-ohayo on 2020-03-13
Here it is:

[https://www.pyimagesearch.com/2019/12/09/how-to-install-tensorflow-2-0-on-ubuntu/](https://www.pyimagesearch.com/2019/12/09/how-to-install-tensorflow-2-0-on-ubuntu/)

The relevant part of this long manual is titled "Step # 2 (GPU only): Install NVIDIA drivers, CUDA, and cuDNN"
But this tutorial is based on **CUDA 10.1**, and it suggests to install version **418** of NVIDIA drivers.
At that time I already had **CUDA 10.2** installed.
As I learned later on the NVIDIA site, CUDA 10.2 is compatible with version **440** of NVIDIA drivers.
So I installed **440**.

---

