---
title: "How do I &quot;auto&quot; boot virtual XP"
date: 2008-02-25
forum: Installation &amp; Upgrades
---

### Post by keratos on 2008-02-25
Hi

I have successfully installed VMware server on my Linux box and installed a XP guest O/S. 

I can run XP from a terminal with "vmrun start /var/lib/vmware/virtual machines/XP" and all is okay, full screen, and VMware tools installed so the SVGA is fine.

It is absolutely brilliant. I would even say running XP through linux and vmware is FASTER than XP native....cannot believe it, dont know how, but it just seems much more responsive. ????

Anyway, is there anyway I can setup grub and linux to boot my VMware guest O/S from the GRUB boot menu. Like, I want the capability to boot a GRUB menu option called "XP" that actually boots linux, auto logs in, and runs my VMware guest XP O/S. Then, when I power down the XP guest O/S, the linux box shuts down.

Like I said above, I can accomplish this from the command line in linux, but I want this ability for my 6yr old daughter so that she is blisfully unaware linux is the primary O/S.

Thanks in advance.

This will take a REAL guru to resolve me thinks :-)

---

### Post by OoooMatron on 2008-02-25
You can use gnome to autologin and then run your command in the startup sessions. Hopefully that will sort it. Or at least a starting point.

I don't know how you can make it work for that installation of linux though, you'd maybe have to install it on another partition and boot to that. I presume you hope that some kind of config in grub will tell it to run vmware on startup?

---

### Post by keratos on 2008-02-25
> **OoooMatron said:**
> You can use gnome to autologin and then run your command in the startup sessions. Hopefully that will sort it. Or at least a starting point.

I don't know how you can make it work for that installation of linux though, you'd maybe have to install it on another partition and boot to that. I presume you hope that some kind of config in grub will tell it to run vmware on startup?


Thanks.

You are right, what I wanted to know is how GRUB can be setup to boot Ubuntu then autorun GDM which autologs in, which autoruns vmware. 

I already have the gnome/auto login and vmware autostart setup.

It is jut eh Grub bit.

Not sure how to do this and how to tell the kernel/rc to run a special version of GDM autologin.

...or even if that is the best way to do this, there could be another ?!

---

### Post by OoooMatron on 2008-02-26
Hmm, i don't know very much about this at all but what about this suggestion.

1. Build (or install) a  kernel with a different version name

2. Write some kind of perl or python script to detect which kernel is running (run the UNAME -R command). Depending on that, update the GDM autostart to parse your vmware startup code. Of course, this script needs to be placed in the linux startup folders, not gnome.

That's the best I can think of. Unfortuantely, I don't have time to try and code it for you but maybe someone can. It shouldn't be that hard.

---

### Post by keratos on 2008-02-27
> **OoooMatron said:**
> Hmm, i don't know very much about this at all but what about this suggestion.

1. Build (or install) a  kernel with a different version name

2. Write some kind of perl or python script to detect which kernel is running (run the UNAME -R command). Depending on that, update the GDM autostart to parse your vmware startup code. Of course, this script needs to be placed in the linux startup folders, not gnome.

That's the best I can think of. Unfortuantely, I don't have time to try and code it for you but maybe someone can. It shouldn't be that hard.

Good idea. I've accomplished this and have a script that identifies the kernel name (including my "dummy" vmware kernel that is booted at Grub).

However, it is not clear how gnome/GDM starts and where the autologin features are defined. 

What files do I need to modify in order to tell GDM to autologin and gnome to autostart an application (vmware). I do have the vmware command arguments though !

---

### Post by keratos on 2008-03-01
Help !!

---

### Post by zekica on 2008-03-01
I haven't tried this, but it should work:

You can tell to GRUB to boot the same kernel, but appending another keyword to it.

If you have for example something like this:
```
title           Ubuntu 7.10, kernel 2.6.22-14-generic
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.22-14-generic root=UUID=xxxxxx ro quiet splash
initrd          /boot/initrd.img-2.6.22-14-generic
quiet
```

You can add another entry to your /etc/grub/menu.lst that will look like this:
```
title           Ubuntu 7.10, kernel 2.6.22-14-generic
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.22-14-generic root=UUID=xxxxxx ro quiet splash **startwindows**
initrd          /boot/initrd.img-2.6.22-14-generic
quiet
```

Then you can create a startup script that will be run before GDM, for example create a file:
**/etc/init.d/startwindows**
```
#!/bin/bash

grep startwindows /proc/cmdline >/dev/null
if [ $? == 0 ]; then
cp -f /etc/gdm/gdm.conf-custom-windows /etc/gdm/gdm.conf-custom
else
cp -f /etc/gdm/gdm.conf-custom-nowindows /etc/gdm/gdm.conf-custom
fi
```

create two copies of **/etc/gdm/gdm.conf-custom** into files:
**/etc/gdm/gdm.conf-custom-windows** and
**/etc/gdm/gdm.conf-custom-nowindows**.

Into **/etc/gdm/gdm.conf-custom-windows** find a section **[daemon]**
And add following lines:
```
AutomaticLoginEnable=true
AutomaticLogin=<username>
```

then set vmware to start windows automaticly for this user.
However, i don't know very elegant way to automatically shutdown it when vmware exits, but you can try the following:
type **sudo visudo** in terminal and add (so that sudo doesn't ask for password when executing poweroff command):
```
%admin ALL= NOPASSWD: /sbin/poweroff
```

and creating a script that will call vmware and on it's exit call:
```
sudo poweroff
```

I hope you understand what I've suggested.

---

### Post by keratos on 2008-03-01
thank you VERY much,

I tried the suggestion and it works. However...

I also purchased Linux Format magazine today and read an article on VirtualBox (didnt know about this app before).

Anyway, installed virtualbox and setup an XP vm. Here is the great bit..

in the user's gnome startup I placed a small script and set this to run using the gnome panel System->Preferences->Sessions
```

VBoxSDL -vm XP -fullscreen
gnome-session-save --kill --silent

```

Now, when the user logs in, the XP vm starts in fullscreen and when "windows" is shutdown, the system returns the user to the ubuntu login screen.

Brilliant.

THANKS FOR THE HELP.

---

