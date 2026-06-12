---
title: "X broke while trying to switch from manual installed NVidia driver to normal"
date: 2009-10-27
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by Rackstar on 2009-10-27
Hi,

Today I updated to Karmic, and it hasn't been great so far. Mainly because of nvidia-drivers.

1) In 9.04 I was using the 185 driver, installed manually from the NVidia website.
2) I updated to 9.10 while having that driver installed
3) I uninstalled through NVidia[...].run --uninstall
4) Tried to install through GUI, like this:
[http://www.psychocats.net/ubuntu/nvidia](http://www.psychocats.net/ubuntu/nvidia)
5) It said "downloading and installing", but when the dialog box disappeared, the driver wasn't marked "active"

EDIT: this is my xorg.conf at this stage:
```

Section "Screen"
	Identifier	"Default Screen"
	DefaultDepth	24
EndSection

Section "Module"
	Load	"glx"
EndSection

Section "Device"
	Identifier	"Default Device"
	Driver	"nvidia"
	Option	"NoLogo"	"True"
EndSection


```

6) When X is started, CLI shows up, and flashes, also I'm only able to type when CLI is visible.

I'm able to get back to gdm, when I remove xorg.conf. But where do I go from here? I tried several things, but I was never able to fix it.

Thanks in advance!

Ruben

---

### Post by NRDNick on 2009-10-27
> **Rackstar said:**
> Hi,

I'm able to get back to gdm, when I remove xorg.conf. But where do I go from here? 

Ruben

If you logged in to gdm fine then where else would you like to go?
Karmic does not need an xorg.conf file unless you need to do some tweaking to your setup, everything is done automatically. Sorry if I sound naive but I don't understand what the problem is. You could try typing ```
Sudo nvidia-xsetup
```to see if that gives you a working xorg.conf.

---

### Post by Rackstar on 2009-10-27
Thanks for your reply!

Unfortunally, I mean that I am logged in into gdm, but without the nvidia driver. When I remove the xorg-file, it disables/removes (?) the driver.

---

### Post by NRDNick on 2009-10-27
It shouldn't remove or disable the driver as far as I know. you can try this in a terminal to see which driver is in use. Sorry it took me a few mins to google this code but if you run ```
lspci -v | perl -ne '/VGA/../^$/  and /VGA|Kern/ and print'
``` In a terminal it should show you which kernel driver is installed for your display. You could also check in System/Administration/Hardwar Drivers to see if it's listed there, however without the modaliases for the particular driver you have it wont display anything. Another thing you could try is enabling special effects(compiz) in the appearance menu in System/Preferences/Appearance last tab on the right. If you aren't running the proprietary driver the effects will not be enabled, but if it allows you to enable them then I would say all is good.

Edit:Sorry I just reread your OP over again, can you enable the driver from the Hardware drivers menu now that you've deleted your xorg.conf? Need some sleep here, but I'm sure there will be some other people here that can help ya. Good luck!

---

### Post by Rackstar on 2009-10-27
Hey,

Thanks for the reply!

Well I when I try to install a driver by going to "hardware drivers" the dialog shows up "downloading and installing" disappears, but nothing changed (not marked active). And when I reboot, it's the same CLI blinking again, then I need to delete xorg.conf again.

This is the output for the code you gave me:
```

01:00.0 VGA compatible controller: nVidia Corporation G72M [Quadro NVS 110M/GeForce Go 7300] (rev a1)
	Kernel modules: nvidiafb


```

---

### Post by Rackstar on 2009-10-27
As I had other problems as well with this upgrade (trackpad not working, no sound device, previous kernels in grub, ...) I decided to do a fresh install.

Wasn't that easy, had to reburn 4 times, also tried usb-boot, but didn't work also. I don't know why it was this hard this time. Hope it'll be a smooth ride from now on.

Thanks for your help.

---

### Post by information_entropy on 2009-10-27
> **Rackstar said:**
> 

6) When X is started, CLI shows up, and flashes, also I'm only able to type when CLI is visible. 


Same thing happened to me when I activated 185.
I tried 173. Same result. :(

If I delete the nvidia driver in xorg.conf the machine boots ok
But still no luck trying to get any nvidia driver to work

If the clean install solves the problem, please let us know.

---

### Post by trulan on 2009-10-27
Just an FYI - the current NVidia drivers (from NVidia) will not work with the RT kernel.  The version of the drivers from Ubuntu has been patched.  Chances are you aren't using the RT kernel (Ubuntu Studio), but if you are, you need the patched version of the drivers from the Ubuntu repos.  (Just updated today).

---

