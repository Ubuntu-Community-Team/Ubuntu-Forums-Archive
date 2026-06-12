---
title: "Ubuntu using wrong graphic card"
date: 2018-09-07
forum: Installation &amp; Upgrades
---

### Post by ueby on 2018-09-07
Hi,

I have installd ubuntu 18.04.1 LTS on my laptop and it has two graphic cards, one is internal Intel and the otherone is external Nvidia. And i want to use my external graphic card when i plug my laptop to my monitor with hdmi cable. My laptop is Lenovo y50-70, [url]("https://www.cnet.com/products/lenovo-y50-70-laptop-59438436-black-doorbuster-4th-generation-intel-core-i7-4710hq-2-50ghz-1600mhz-6mb/specs/") to laptop hardware specs. I know for sure that my laptop has Nvidia graphics card. But when i run the folowing command:```
 lspci -k | grep -A 2 -i "VGA"
```  it show's me only one graphic card:
> 
00:02.0 VGA compatible controller: Intel Corporation 4th Gen Core Processor Integrated Graphics Controller (rev 06)
    Subsystem: Lenovo 4th Gen Core Processor Integrated Graphics Controller
    Kernel driver in use: i915


i have installd nvidia drivers with command line [HTML]sudo ubuntu-drivers autoinstall[/HTML] nvidia version nvidia-driver-390 is installd on my laptop. The output of ubuntu-drivers devices gives me the folowing:
> == /sys/devices/pci0000:00/0000:00:01.0/0000:01:00.0 ==
modalias : pci:v000010DEd00001392sv000017AAsd00003978bc03sc02i00
vendor   : NVIDIA Corporation
model    : GM107M [GeForce GTX 860M]
driver   : nvidia-driver-390 - distro non-free recommended
driver   : nvidia-340 - distro non-free
driver   : xserver-xorg-video-nouveau - distro free builtin



but when i try to start nvidia-settings, i dont see all settings of nvidia graphic drivers and the terminal it outputs the folowing error:

> ERROR: NVIDIA driver is not loaded


ERROR: Error querying enabled displays on GPU 0 (Missing Extension).


ERROR: Error querying connected displays on GPU 0 (Missing Extension).

** Message: 22:20:33.855: PRIME: No offloading required. Abort
** Message: 22:20:33.855: PRIME: is it supported? no

ERROR: nvidia-settings could not find the registry key file. This file should have been installed along with this
       driver at /usr/share/nvidia/nvidia-application-profiles-key-documentation. The application profiles will
       continue to work, but values cannot be prepopulated or validated, and will not be listed in the help text.
       Please see the README for possible values and descriptions.


(nvidia-settings:1825): Gtk-CRITICAL **: 22:20:33.900: gtk_widget_get_preferred_width_for_height: assertion 'height >= 0' failed

(nvidia-settings:1825): Gtk-WARNING **: 22:20:33.900: gtk_widget_size_allocate(): attempt to allocate widget with width 12 and height -12

(nvidia-settings:1825): Gtk-CRITICAL **: 22:20:33.900: gtk_box_gadget_distribute: assertion 'size >= 0' failed in GtkScrollbar

(nvidia-settings:1825): Gtk-CRITICAL **: 22:20:33.900: gtk_widget_get_preferred_width_for_height: assertion 'height >= 0' failed

(nvidia-settings:1825): Gtk-WARNING **: 22:20:33.900: gtk_widget_size_allocate(): attempt to allocate widget with width 12 and height -12

(nvidia-settings:1825): Gtk-CRITICAL **: 22:20:33.900: gtk_box_gadget_distribute: assertion 'size >= 0' failed in GtkScrollbar

so i asume with above errors that nvidia drivers are not installed properly. Can anyone help me to install nvidia drivers the right way?

kind regards,

ubey

---

### Post by Bashing-om on 2018-09-07
ueby; Hey -

We can sure try :)

What desktop are you using ?
```

echo $XDG_SESSION_TYPE

```
as nvidia has dismal support for Wayland presently.

let's get on the same page and go from there.

[INDENT][INDENT]we can do that
[/INDENT][/INDENT]

---

### Post by ueby on 2018-09-08
Hi Bashing,

the output is x11. Wich type of ubuntu desktop do i have to use?

---

### Post by ueby on 2018-09-08
I have solved the problem, i installd nvidia drivers with this comands:

> 
[COLOR=#242729][FONT=Arial]sudo apt update[/FONT][/COLOR][COLOR=#242729][FONT=Arial]
sudo apt upgrade[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]sudo ubuntu-drivers autoinstall[/FONT][/COLOR]

and reboot after reboot i choose mok, enterd password  and rebooted again. The problem was that on my laptop UEFI was enabeld.

---

### Post by Bashing-om on 2018-09-08
ueby; Great !

Please mark this thread solved;
aides others seeking the solution,
helps keep the forum clean and
precludes others miss-directing efforts to aid.
[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

[INDENT][INDENT]up up and away
[/INDENT][/INDENT]

---

