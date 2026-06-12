---
title: "compile new kernel vs upgrading - EOL versions"
date: 2013-07-16
forum: Installation &amp; Upgrades
---

### Post by Claus7 on 2013-07-16
Hello,

I'm really happy with my EOL version of ubuntu that I'm using (perfect 10 that is), yet I was thinking of updating. Why? Because, in some rare occasions, I want to use some programs that are using the latest version of some libraries.

Now, solution no 1: Upgrade from version to version till the last one, without losing my configuration.
Solution no 2: why not compiling the latest kernel and see what is going to happen then? Still keeping the old configuration intact.

My questions are:

1) if I do compile a new kernel, will that affect my already existing (original) configuration?
My thought was that the new kernel will be placed as a new one in grub menu, and if faulty, to be removed from my system.
2) Will this uninstall the proprietary graphics driver that I'm using?
I think that I will reinstall it, yet I do not think that I will have to install everything anew.
3) what it will be the main difference between updating gradually and compiling my own kernel?
I think that it will be possible to configure the repositories so as to get the latest updates from ubuntu. No?
4) If I install a new program, unsupported previously, in my new kernel configuration, will this, by any means, affect the original configuration?
For example: switching back I hope that e.g. the original pulseaudio will be there intact.

Thank you in advance,
Regards!

---

### Post by monkeybrain2012 on 2013-07-16
You could have kept your configurations if you have a separate /home so just reinstall over / or if not just save your home folder. do a clean install and copy the /home back and remove some outdated configuration files. It is a bad idea to run a EOL release because you won't get any security updates. It is also a bad idea to do an "upgrade" when you don't have a very pristine installation and are many releases behind.

---

### Post by snowpine on 2013-07-16
I recommend to keep your "perfect 10" install for a while, and install a currently-supported distribution (such as later versions of Ubuntu, for example) as a "dual boot" configuration. This will allow you to boot to the older system if necessary, while you are working out the kinks with the new version. :)

ps If your hardware is functioning flawlessly, then there is really no reason to upgrade your kernel. ;)

---

### Post by Claus7 on 2013-07-17
Hello,

1st: thank you for your responses. Now:

> **monkeybrain2012 said:**
> You could have kept your configurations if you have a separate /home so just reinstall over / or if not just save your home folder. do a clean install and copy the /home back and remove some outdated configuration files. It is a bad idea to run a EOL release because you won't get any security updates. It is also a bad idea to do an "upgrade" when you don't have a very pristine installation and are many releases behind.

I do have a separate /home, yet that way I have to install ALL the programs I'm using along with the new version of ubu... With security updates I agree, yet I think that ubu boxes are very reliable even if are pristine. I do also agree that many upgrades will destroy the system in the end. 

And:

> **snowpine said:**
> I recommend to keep your "perfect 10" install for a while, and install a currently-supported distribution (such as later versions of Ubuntu, for example) as a "dual boot" configuration. This will allow you to boot to the older system if necessary, while you are working out the kinks with the new version. :)

ps If your hardware is functioning flawlessly, then there is really no reason to upgrade your kernel. ;)

I think that your proposal is to stick with what I have, and this was my intention from the beginning. I just wanted to see what were the experiences from compiling a new kernel for similar situations like the one I'm now.

Happy ubuntu-ing,
Regards!

---

### Post by snowpine on 2013-07-17
> **Claus7 said:**
> I think that your proposal is to stick with what I have...

No! What you have now is end-of-life, potentially insecure, and totally unsupported in any case.

---

### Post by monkeybrain2012 on 2013-07-17
> **Claus7 said:**
> 

I do have a separate /home, yet that way I have to install ALL the programs I'm using along with the new version of ubu... With security updates I agree, yet I think that ubu boxes are very reliable even if are pristine. I do also agree that many upgrades will destroy the system in the end. 



Backup and reinstall all your programs in new install, transferring sources.list etc (of course have to make sure that ppa exists for the new Ubuntu release and change name accordingly)

[http://askubuntu.com/questions/9135/best-way-to-backup-all-settings-list-of-installed-packages-tweaks-etc](http://askubuntu.com/questions/9135/best-way-to-backup-all-settings-list-of-installed-packages-tweaks-etc)

BTW, I don't think it makes any sense to stick to an EOL OS just because you don't want to spend an hour or less reinstalling your software (it will take less time and be done automatically with the method linked above), what if your PC dies on you? Would you have to reinstall then?

---

### Post by Claus7 on 2013-07-19
Hello,

> **monkeybrain2012 said:**
> Backup and reinstall all your programs in new install, transferring sources.list etc (of course have to make sure that ppa exists for the new Ubuntu release and change name accordingly)

[http://askubuntu.com/questions/9135/best-way-to-backup-all-settings-list-of-installed-packages-tweaks-etc](http://askubuntu.com/questions/9135/best-way-to-backup-all-settings-list-of-installed-packages-tweaks-etc)

BTW, I don't think it makes any sense to stick to an EOL OS just because you don't want to spend an hour or less reinstalling your software (it will take less time and be done automatically with the method linked above), what if your PC dies on you? Would you have to reinstall then?

ehm... Let me put it this way:

I have changed the icon on applications, the flags when I change keyboard language, the way ubuntu is greeting me, the background in nautilus, the sound settings, the configurations in compiz, the transparency of the terminal, of the menus, the size of fonts, configuration of wine, icon short-cuts, firefox fonts - settings - menus, grub menu with a separate hdd that now lies at rest, ubuntu tweak short-cuts on desktop screen, ipv6 configuation, internet configuration ....

3 years and more of configurations, even from alpha version of maverick. Cannot throw it away so easily you know, especially if this is working like a charm?! 

I wanted to see if there was a way to experiment with a new kernel  with my existing configuration, since some libraries for some new programs are outdated. I think, that in the future, I might experiment a little bit, before switching to a new version. 

And a quote that I remember mentioned some years ago: Ubuntu is more stable than windows and better looking than a mac...
not sure who stated though...

Thanks for the responses,
Regards!

---

### Post by Frogs Hair on 2013-07-19
If you want to preserve  these configurations and tweaks I don't think using them in what would essentially be a test machine is a good way to go about. If you want to experiment with newer kernels in 10.10 or other unsupported releases try it on another partition. There is always risk using a kernel other than the one designated for the release even on supported  versions. If this is your daily user backup before proceeding.

---

### Post by Claus7 on 2013-07-19
Hello,

> **Frogs Hair said:**
> If you want to preserve  these configurations and tweaks I don't think using them in what would essentially be a test machine is a good way to go about. If you want to experiment with newer kernels in 10.10 or other unsupported releases try it on another partition. There is always risk using a kernel other than the one designated for the release even supported on versions. If this is your daily user backup before proceeding.

thank you for your response. It was really comprehensible. I guess that you are referring to copying my existing configuration on a new partition and experiment there. My only last question is: will it be possible to use the new repositories of ubuntu (the latest ones) if the installation of the new kernel in a new partition is successful? E.g. using the repositories of oneiric ocelot.

Regards!

---

### Post by Frogs Hair on 2013-07-19
You won't be able to use newer repositories on old releases. To enable newer repositories unless for the purpose of upgrading to a newer Ubuntu version would cause major breakage. EOL Upgrades: [https://help.ubuntu.com/community/EOLUpgrades](https://help.ubuntu.com/community/EOLUpgrades)

11.10 was the first Gnome 3 release and brings the Unity Desktop , new versions of Gnome, Compiz and libraries to support them. Many applications were updated and others simply became obsolete because there was no interest in continuing development for Gnome 3 due to major changes.

---

### Post by Claus7 on 2013-07-20
Hello,

thank you for all the info!

Regards!

---

