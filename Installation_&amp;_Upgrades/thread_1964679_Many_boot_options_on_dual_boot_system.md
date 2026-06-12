---
title: "Many boot options on dual boot system"
date: 2012-04-24
forum: Installation &amp; Upgrades
---

### Post by algrossi on 2012-04-24
I have a Dell Inspiron with Windows XP and Ubuntu 10.04, dual boot. Every time Ubuntu upgrades, a new boot option appears on the boot menu. I now have about 10 different kernels to choose from and I want to remove all but the last few. I deleted them from the /boot directory but they still appear when I boot the system. There must be another place where these boot options are kept and I cannot find it. Does anyone know where...?
Thank you;
Al;

---

### Post by Mark Phelps on 2012-04-24
Removing them from the directory doesn't change the menu because it is static.  To change the menu, open a terminal and enter "sudo update-grub".  This will generate a new menu.  When you reboot the removed kernels should be gone.

If they are not, then install synpatic package manager and use that to remove them.

---

### Post by Dngrsone on 2012-04-24
I use Synaptic to completely remove the older kernel packages (I usually leave the last version, just in case).

Once Synaptic is done, a reboot usually shows a cleaner Grub page, without even having to run update-grub.

---

### Post by algrossi on 2012-04-24
Thanks a million my friend.
That makes perfect sense. I will try it at the first opportunity to reboot.
This Ubuntu forum is a great place to be - especially for noobs like me.
I am slowly learning and appreciate everyone's help.
Have a great day;
Al;

---

### Post by Rex Bouwense on 2012-04-24
> **Dngrsone said:**
> I use Synaptic to completely remove the older kernel packages (I usually leave the last version, just in case).

Once Synaptic is done, a reboot usually shows a cleaner Grub page, without even having to run update-grub.
+1  There is another option and that is Ubuntu Tweak, but it must be downloaded and installed.  Plus you can tweak other things in the OS.

---

### Post by Dngrsone on 2012-04-24
> **Rex Bouwense said:**
> +1  There is another option and that is Ubuntu Tweak, but it must be downloaded and installed.  Plus you can tweak other things in the OS.

Will Ubuntu Tweak work in 10.04?  I thought that it was a Unity thing.

---

### Post by Rex Bouwense on 2012-04-24
> Will Ubuntu Tweak work in 10.04? I thought that it was a Unity thing. 
You betcha.  I used it in Ubuntu 10.04 and now I am using it in Lubuntu 11.10.  It is a great tool.
[http://ubuntu-tweak.com/](http://ubuntu-tweak.com/)

---

### Post by Dngrsone on 2012-04-24
I'm using it in 12.04; just didn't realize it would work in 10.04 as well...

---

