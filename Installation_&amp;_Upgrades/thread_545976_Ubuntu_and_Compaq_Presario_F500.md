---
title: "Ubuntu and Compaq Presario F500"
date: 2007-09-08
forum: Installation &amp; Upgrades
---

### Post by zutronius on 2007-09-08
I've been having issues getting Ubuntu to work on my Compaq F500.

I found a walkthrough here that tells how to get the Os running on the F50. 

[http://cro.alienpants.com/index.php/2007/05/05/getting-ubuntu-running-on-my-compaq-f500/#comment-100408](http://cro.alienpants.com/index.php/2007/05/05/getting-ubuntu-running-on-my-compaq-f500/#comment-100408)

However, I'm confused by this part: 

The first sticking point. To make this work, you need to add the directive

vga=792

to the end of the boot command. When you first boot the live CD, press F6 and add that command at the end of the line. This will let you boot into the graphical shell.

You will need to do this later to the grub bootloader menu in /boot/grub/menu.lst - simply add the directive to the end of the kernel boot command. That’s it, it all worked from there. Some minor issues with the NVIDIA drivers, desktop effects and Beryl, so I’m using none of those. I’m going to try the newly released NVIDIA drivers over the weekend.

How do I add that command later to the grub bootloader menu??

---

### Post by logos34 on 2007-09-10
like this:

**gksudo gedit /boot/grub/menu.lst**

Example: 
> ## ## End Default Options ##

title		Ubuntu, kernel 2.6.20-16-generic
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.20-16-generic root=/dev/hda2 ro quiet splash [COLOR="Red"]vga=792[/COLOR]
initrd		/boot/initrd.img-2.6.20-16-generic
quiet
savedefault

---

### Post by zutronius on 2007-09-10
I get a message sayinf

GTK warning **: Cannot open display

---

### Post by logos34 on 2007-09-10
> **zutronius said:**
> I get a message sayinf

GTK warning **: Cannot open display

huh?

normally you see this in a terminal:
> 
$ gksudo gedit /boot/grub/menu.lst
(gedit:19459): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.


ok, then try
[B]
sudo nano -w /boot/grub/menu.lst[/B]

---

### Post by zutronius on 2007-09-10
that brought me into a new window titled GNU Nano 2.0.2

now what should i do?

---

### Post by logos34 on 2007-09-10
use the arrow keys to scroll down to the kernel line and add the option.  Ctrl+X to exit, yes to save changes to file

---

### Post by zutronius on 2007-09-10
I get another error message when I add vga=792 to the command

I get a message saying error writing=w/boot/grub/menu.lst No such file or directory

---

### Post by logos34 on 2007-09-10
> You will need to do this later to the grub bootloader menu in /boot/grub/menu.lst - simply add the directive to the end of the kernel boot command. [B]That&#8217;s it, it all worked from there. Some minor issues with the NVIDIA drivers, desktop effects and Beryl, so I&#8217;m using none of those. I&#8217;m going to try the newly released NVIDIA drivers over the weekend.

How do I add that command later to the grub bootloader menu[/B]??

What's going on--are you doing this on the live cd or from the installed ubuntu (which is how I interpreted the above remarks)?  I thought you were able to boot into but just want to edit menu.lst so you don't have to add it every time a t boot...

---

### Post by zutronius on 2007-09-10
I guess I don't know. I already had Ubuntu installed. It worked once, I installed updates, then I went to reboot it, and it now freezes past the first load up screen. I am attempting to reinstall again. I originally had Ubuntu Studio installed now trying 7.0.4

---

### Post by logos34 on 2007-09-10
I think I see now.  The only thing I can think of is the updates screwed up the graphics driver, but on reboot you would normally get an X server failure screen after the Ubuntu logo loading bar (in which case you can run dpkg-reconfigure xserver-xorg to try and fix it).  Then it dumps you at the command prompt.  

Here's some links containing other boot options you might try:

[https://help.ubuntu.com/community/BootOptions?highlight=%28boot%29](https://help.ubuntu.com/community/BootOptions?highlight=%28boot%29)
[http://grumpymole.blogspot.com/2007/05/ubuntu-how-to-edit-grub-boot-parameters.html](http://grumpymole.blogspot.com/2007/05/ubuntu-how-to-edit-grub-boot-parameters.html)
[https://help.ubuntu.com/7.04/installation-guide/i386/boot-parms.html](https://help.ubuntu.com/7.04/installation-guide/i386/boot-parms.html)

---

### Post by zutronius on 2007-09-10
Thanks for the advice.

I got one step further. I got past the load up bar screen, it did a hard drive check, then it froze after that screen. I'm out of options. I tried to install PcLinuxOS and now that wont even work. I'm getting very fruistrated.

I also get a message error saying BIOS BUG FOUND.

---

### Post by zutronius on 2007-09-11
I give up with Ubuntu. I can't even get PCLINUXOS to properly boot now. Sigh :(

---

### Post by cro on 2007-10-17
Zutronius: I've had the issues you mention with Ubuntu on the Presario F500. To get around them the latest Gutsy works a treat, but you can also grab the xorg.conf file I've posted to my blog (or type it in). It's a working xorg.conf for GNOME on the Presario F500 with the GeForce Go 6100 and the latest NVIDIA linux drivers (100.14.19 from [http://www.nvidia.com/object/linux_display_ia32_100.14.19.html](http://www.nvidia.com/object/linux_display_ia32_100.14.19.html))

To use the NVIDIA drivers, do this:
Download the package somewhere, preferably to your Presario.
Boot into RECOVERY mode for the GENERIC kernel. The 386 kernel will not work.
Go to the directory where you put the NVIDIA downloaded file.
Run the file ('sudo sh NVIDIA{rest of tile name}')
Accept everything, including the download (which will fail, so let it compile a kernel), then let it update the xorg.conf file. If you used my one from above, all will be fine.
Reboot, and everything will work. (caveat: this is the process I use on my Presario F500, and it works fine)

---

