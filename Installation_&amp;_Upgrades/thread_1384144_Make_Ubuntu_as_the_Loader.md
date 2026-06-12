---
title: "Make Ubuntu as the Loader"
date: 2010-01-18
forum: Installation &amp; Upgrades
---

### Post by brother.zahar on 2010-01-18
Hi There...
 
My laptop contains Ubuntu 9.04 and Windows Vista. I am not able to log into Ubuntu from grub unless I restart the system after going into Vista. Currently I want to uninstall Vista and I should be able to log into Ubuntu each time I start. At the time when grub starts it shows Vista as loader. Would this be the reason?
I want to make Ubuntu as the loader.Kindly help.
 
 
 
 
Thanks,
Sahar Hassan

---

### Post by tachuela on 2010-01-18
Did you install with wubi?

---

### Post by brother.zahar on 2010-01-23
no brother, I did not even know what wubi means..
 
I installed it with Ubuntu CD which came for free...

---

### Post by qyot27 on 2010-01-23
Do you mean the OS that Grub will log into by default?  That's easily changed in the config files (which vary based on whether you're using Grub legacy or Grub2), and has nothing to do with installation or uninstallation of the OSes on the computer.

After you remove Vista, you may need to reset Grub using a LiveCD, though - it can get finicky if not all the systems are there (or maybe it just works the other way around and only screams at you if the Linux partitions are gone - I've had that happen to me before, but it was nothing resetting the MBR wouldn't fix).

---

### Post by brother.zahar on 2010-01-23
Hey,
 
Its not that I want to uninstall Vista anyway, it is just  that I want to have my hardware loaded and I should be able to key in once I got into Ubuntu without having to get into Vista and restart from there. That is, once the system has booted up and once I chose Ubuntu from list I should be able to key in which is something not happening it right now..I am not able to use my keyboard and touchpad if I am getting into Ubuntu straight..I need to get into Vista and restart the computer and then chose Ubuntu once it is restarted..I dont want  this burden anymore..Please help...

---

### Post by tachuela on 2010-01-23
Start for allocating space for Ubuntu FROM WITHIN Windows first. Then install Ubuntu and let Grub2 install itself in the MBR. Later 'update-grub' will do it.

---

