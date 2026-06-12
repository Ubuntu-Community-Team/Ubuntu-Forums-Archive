---
title: "Nvidia drivers"
date: 2012-07-28
forum: Installation &amp; Upgrades
---

### Post by Shugs81 on 2012-07-28
Hi peeps

After a maassiiive gap I'm coming back to ubuntu studio...

I'm tring to install the nvidia drivers but can't seem to stop x-server....

i used

```
sudo /etc/init.d/gdm stop
```

but it says command not found... I also tried to go into recovery mode, picking root thinking it the most logical option but when i tried to run the Nvidia installation it said I didn't have permissions to create '/tmp/***'

I dunno if i've managed to miss something but I couldn't find any other options that were ubuntu releated...

help!! I was hoping to have this  up and running so I can carry on with building a portfolio from blender and if i can get it running max... but either way I need the gfx card running!!

Thanks!!

---

### Post by kc1di on 2012-07-28
You didn't say what version of Ubuntu you are using?  

Your signature still says 9.04 which I'm doubting. 

if it's 12.04 then you need to go to system tools > additional drivers and install Nvidia from there if it offers them for your machine.  

if not the correct command is ```
 sudo /etc/init.d/lightdm stop
```
Ubuntu 12.04 uses lightdm as desktop manager not gdm. 

Cheers.
P.s. If you want the latest in Nvidia Drivers go to the following page and install it's [ppa]("http://www.ubuntuupdates.org/ppa/ubuntu-x-swat")

---

### Post by Shugs81 on 2012-07-28
doh!!!

yes it is 12.04....
the current installed driver has sarted working now but i might as well try the latest one!!!

cheers bud!

---

### Post by kc1di on 2012-07-28
> **Shugs81 said:**
> doh!!!

yes it is 12.04....
the current installed driver has sarted working now but i might as well try the latest one!!!

cheers bud!

good luck :)

---

