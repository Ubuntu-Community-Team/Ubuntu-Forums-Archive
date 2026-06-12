---
title: "How do I uninstall 12.10"
date: 2013-04-01
forum: Installation &amp; Upgrades
---

### Post by userqq on 2013-04-01
Hi, I dont like version 12.10 and want to go back to ver 11.04. I have 12.10 installed with the *windows installer* taking 12 gb of my 40 gb drive.
I know how to install 11.04 but I am not sure how to properly (and completely) uninstall 12.10.
there is the **wubi** that I installed it with, It has an uninstall option, maybe that's it? I dunno.
Thanks in advance!):P

---

### Post by darkod on 2013-04-01
Version 11.04 is not supported any more. What is it that you don't like in 12.10? The new Unity interface?

You can install something like gnome-panel that will give you Gnome Classic interface similar to the older Gnome2.

The use of 12.04 LTS is recommended because it is supported for 5 years until 2017. 11.04 is no longer supported.

Also, if I understand correctly, you have a wubi 12.04 installation inside windows and 12.10 installation on its own linux partition, right? You can simply boot the computer with the ubuntu cd and install over 12.10, using the same existing partitions as root and swap. To reuse existing partition you have to use the manual method.
To use the auto method to install you will have to boot into live mode and delete the existing partitions, and then you can use the unallocated space with the auto install method. But be careful when deleting the 12.10 partition, if you don't install another ubuntu right away, the computer will not boot after you delete the partition because grub2 will be missing its config files.
If you want to remove 12.10 without installing another ubuntu right away, first boot windows and restore the windows bootloader to the MBR, and only after you are sure windows is booting fine with windows bootloader, use the ubuntu live mode and Gparted to delete the ubuntu partitions.

---

### Post by userqq on 2013-04-01
Got it. Thanks Yeah, Im still having problems with the wireless (bcm4306) randomly disconnecting. Also 12.10 seems to be using up too much computer power and the machine is old.
Dont get me wrong . 12.10 just looks and feels really good.
Im pretty sure the same wireless problem will be there with 12.04, Heck, could be with 11.04c as well.  My kid is running 11.10 and swears by it.

Oh, can't I just use the wubi installer to uninstall in windows?, it has that option.

EDIT: Honestly I would like to be able to see and actually turn off some of the unused startup applications  like I could in 11.04. It doesnt even say 'startup applications' in the upper right hand star (start) icon.
My router also says that the computer has 4 libtorrents running and I did not put them there.I dont like that and Im thinking that maybe these hidden startup applications and libtorrents and connical connections may be why I keep getting disconnected. 
Do you know how I can show these hidden startup applications and connections?
Thanks again you always answer and it is appreciated.:)

---

### Post by xianbei on 2013-04-01
You can find the program by opening the dash and typing 

startup applications

---

### Post by darkod on 2013-04-02
You can uninstall in windows if that is how you installed. I understood that the 12.10 is stand alone, on its own partition, not wubi in windows.

If it's wubi in windows, the only way to uninstall is in Control Panel - Programs. There is no ubuntu partition to delete.

If it's stand alone ubuntu with linux partition, you can't uninstall it from inside windows.

---

