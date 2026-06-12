---
title: "After upgrading to Dapper and using update tool Nvidia support disappears"
date: 2006-06-19
forum: Installation &amp; Upgrades
---

### Post by gusjones on 2006-06-19
OK here goes,

Every so often Ubuntu pops up with a nice lightbulb icon saying its time to install the latest updates.

Well post upgrade install to Dapper, I did a kernel update, and now my nvidia driver is not recognised. I've tried reinstalling unistalling, removing and reinstalling it. editting the xorg.conf, putting it back to 'nv' then back to 'nvidia' again.

When it fails I basically get a boot up error which goeas something like 'failed to load 'Nvidia' driver or 'nvidia' driver not found.

Now if on boot up I hit escape go into Grub and boot up with an earlier kernel then 'nvidia' driver is picked up fine.

If I boot with the most recent kernel then I can only get a graphical display if I use the 'nv' version of the nvidia driver specified in my xorg.conf file. Of course 'nvidia' version is far better as it allows one to use the full 3D capabilities of the card.

Has anyone come across this problem, any solutions, ideas? ](*,)

---

### Post by zxee on 2006-06-19
Basically the answer is this: Whever you do a kernel upgrade you will need to do all the steps again that you 1st did to get the nvidia propritary driver installed. Rather than outline that here-since I don't know if you used apt-get or another method just take a look at the dapper installation upgrade forum.

---

### Post by cacharreo on 2006-06-19
I have had the same problem and i have fixed it installing the nvidia drivers using the automatix package:mrgreen: 
[http://www.ubuntuforums.org/showthread.php?t=138405](http://www.ubuntuforums.org/showthread.php?t=138405)

---

### Post by tseliot on 2006-06-20
Try this:
[http://doc.gwos.org/index.php/Latest_Nvidia_Dapper#WHAT_HAPPENS_IF_YOU_CHANGE_YOUR_KERNEL_OR_IF_YOUR_KERNEL_IS_UPDATED]("http://doc.gwos.org/index.php/Latest_Nvidia_Dapper#WHAT_HAPPENS_IF_YOU_CHANGE_YOUR_KERNEL_OR_IF_YOUR_KERNEL_IS_UPDATED")

---

### Post by gusjones on 2006-06-21
Thanks Cacharreo,

I tried your approach because when checking out the 'automatix' package I liked the look of some of the packages it installed which I had not yet installed. So I went with it and problem solved.

Thanks all, :mrgreen: 

Rob.

---

