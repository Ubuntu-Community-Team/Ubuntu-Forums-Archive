---
title: "Ubuntu and Lilo"
date: 2005-09-14
forum: Installation &amp; Upgrades
---

### Post by 8FootSativa on 2005-09-14
I recently decided on setting up a Windows 2000/Ubuntu dual boot, as my girlfriend is now living with me and she prefers a Windows enviroment. I decided to use the XFS filesystem this time around and all went well until it came time to install grub. Apparently grub and xfs don't get along, so I went ahead with Lilo. I didn't think this would be a big deal, as the Ubuntu grub is setup brilliantly compared to other distros, and I assumed lilo would use a similar configuration. Plus I've seen many distros offer a very polished lilo.

Everything went as planned until the intial boot. No options screen. Just right into Ubuntu. After the initial setup I stumbed into the lilo.conf and did what I *thought* would give me the option of choosing either Windows or Ubuntu.

This just sent me into Windows with no option screen.  :grin: 

I'm not familar with lilo, can someone give me an example lilo.conf to give me at least a menu choice?

---

### Post by bsussman on 2005-09-14
[http://www.linux-boot.net/Loaders/Lilo/]("http://www.linux-boot.net/Loaders/Lilo/") might help.

includes examples.

Remember that lilo requires an execution after the conf is altered, unlike grub

 ```
> vi /etc/lilo.conf
``` 

yaddayaddayadda alter config

 ```
> lilo

``` 
(lilo runs and installs config as altered)

Took me a long time to convert to grub (no regrets now).  Too bad it doesnt work for you.:?

---

### Post by 8FootSativa on 2005-09-14
[QUOTE=bsussman][http://www.linux-boot.net/Loaders/Lilo/]("http://www.linux-boot.net/Loaders/Lilo/") might help.

includes examples.

Remember that lilo requires an execution after the conf is altered, unlike grub

 ```
> vi /etc/lilo.conf
``` 

yaddayaddayadda alter config

 ```
> lilo

``` 
(lilo runs and installs config as altered)

Took me a long time to convert to grub (no regrets now).  Too bad it doesnt work for you.:?[/QUOTE]


Thanks! I think I've got it all figured out.

I hear ya on grub....I prefer it over lilo by far. I also seem to get the best performance out of XFS on my systems, so I have to comprimise.

---

