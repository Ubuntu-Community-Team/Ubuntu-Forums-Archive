---
title: "Installing 500Gb sata drive to IDE notebook with 137Gb limit bios"
date: 2011-08-17
forum: Installation &amp; Upgrades
---

### Post by tuanle1998 on 2011-08-17
I purchased a sata to ide adapter so I can use my new 500Gb HD in my old notebook that uses 2.5" IDE connector with 137Gb limit.

[http://www.amazon.com/gp/product/B0049D7PCU](http://www.amazon.com/gp/product/B0049D7PCU)

I've tried to partition the drive to 100Gb partitions and install Ubuntu 11.04 onto the main partition, then hook the drive into my notebook. So far, it fails to boot up.

The bios recognizes the drive as 137Gb when I plugged in the brand new drive before formatting using the adapter.

Any suggestions on how I should partition the drive so that it would boot up with Ubuntu?

Is there a way to force the drive to format less than it's capacity?

---

### Post by valantis on 2011-08-17
> **tuanle1998 said:**
> I purchased a sata to ide adapter so I can use my new 500Gb HD in my old notebook that uses 2.5" IDE connector with 137Gb limit.

[http://www.amazon.com/gp/product/B0049D7PCU](http://www.amazon.com/gp/product/B0049D7PCU)

I've tried to partition the drive to 100Gb partitions and install Ubuntu 11.04 onto the main partition, then hook the drive into my notebook. So far, it fails to boot up.

The bios recognizes the drive as 137Gb when I plugged in the brand new drive before formatting using the adapter.

Any suggestions on how I should partition the drive so that it would boot up with Ubuntu?

Is there a way to force the drive to format less than it's capacity?
Hi the only way is to install your hdd on other pc and make a partition of 120gb , and then put it on your laptop. also you must find on you ventor site if has release a bios update to recognise bigger hdd(becarefull the instractions of your ventor )

---

### Post by YesWeCan on 2011-08-17
I think the 137GB only applies during the boot up. So I think you can create a 500MB boot partition at the start of the disk, then your other Ubuntu partitions any size you like after that. When you install Ubuntu, use "manual" or "special" or whatever to format the 500MB partition ext4 and mount it as /boot.

BTW, this is not necessary but I like to make all Ubuntu or linux partitions logical for greater flexibility. The boot partition can also be logical, as long as it is contained within the first 137GB.

---

### Post by tuanle1998 on 2011-08-17
It seems like it's too much work for the work-arounds.  I have decided to use the 500Gb drive in another computer and sell the notebook for parts.

Thank you for your responses.

---

### Post by infamous-online on 2011-08-17
> **tuanle1998 said:**
> I purchased a sata to ide adapter so I can use my new 500Gb HD in my old notebook that uses 2.5" IDE connector with 137Gb limit.

[http://www.amazon.com/gp/product/B0049D7PCU](http://www.amazon.com/gp/product/B0049D7PCU)

I've tried to partition the drive to 100Gb partitions and install Ubuntu 11.04 onto the main partition, then hook the drive into my notebook. So far, it fails to boot up.

The bios recognizes the drive as 137Gb when I plugged in the brand new drive before formatting using the adapter.

Any suggestions on how I should partition the drive so that it would boot up with Ubuntu?

Is there a way to force the drive to format less than it's capacity?

First off, how old is your notebook?

---

### Post by ottosykora on 2011-08-18
probably wise to not use it for current ubuntu. I tried also on such desktop computers, but could not run anything after 8.10 ubuntu on it, graphics support was not given etc.

---

### Post by coffeecat on 2011-08-18
@tunale1998, I know this is too late, but...

> **YesWeCan said:**
> I think the 137GB only applies during the boot up. So I think you can create a 500MB boot partition at the start of the disk, then your other Ubuntu partitions any size you like after that.

+1 to this. I agree. The 137GB limit is a BIOS limitation and only applies at the first part of the booting process. Once the OS has loaded it will be able to see the whole 500GB.

> **tuanle1998 said:**
> It seems like it's too much work for the work-arounds.

A pity. Creating a separate boot partition at the beginning of the drive would have been a straightforward exercise.

---

### Post by tuanle1998 on 2011-08-18
My notebook is probably closed to 10 years old.  It's a fujitsu lifebook that came with a 40gb HD, 512k ram.

I do have another old desktop computer that I can load Ubuntu there to see if I like using it.

I appreciate your help.

---

### Post by coffeecat on 2011-08-18
> **tuanle1998 said:**
> My notebook is probably closed to 10 years old.  It's a fujitsu lifebook that came with a 40gb HD, 512k ram.

If it's 10 years old, then I'd agree with ottosykora that it probably won't run recent versions of Ubuntu anyway, particularly with 512KB of RAM. :-s Are you sure you mean 512k? 512k takes me back nearer 20 years rather than 10! :)

Good luck!

---

### Post by YesWeCan on 2011-08-18
> **coffeecat said:**
> If it's 10 years old, then I'd agree with ottosykora that it probably won't run recent versions of Ubuntu anyway, particularly with 512KB of RAM. :-s Are you sure you mean 512k? 512k takes me back nearer 20 years rather than 10! :)

Good luck!
Ah the good old days...when you could literally navigate a spaceship to the Moon and land a man on it with less than 100k of RAM. :P
[http://www.universetoday.com/34815/build-your-own-apollo-11-landing-computer/](http://www.universetoday.com/34815/build-your-own-apollo-11-landing-computer/)

---

### Post by ottosykora on 2011-08-19
actually I had less problems in running it but big problems to install it.

On my computer from that age, I was not able to run gui installers anything above 8.04.
For 8.10, I had to run the alternate CD installer.
Next problem was when I needed Kubuntu other time. They have this fancy boot menu with about 5 icons showing what is just loading. When it reached the last colorful icon the whole computer crashed as this icon was slightly bigger then the other one and used some more colors...

However it is right, I inserted a 320gb drive, installed w2k and some data partitions in the first 120gb, bootmagic from partition magic package as boot manager to one of the fat32 data partitions and the separate partition ext3 in the 'higher' region for ubuntu then, this way , yes it did work that time, but it was pain...

---

