---
title: "Low resolution on login screen"
date: 2014-04-16
forum: Installation &amp; Upgrades
---

### Post by pkdev on 2014-04-16
hello, i have problem with screen resolution on login screen(1024x768). After login resolution is back to 1920x1080.
When i type xrandr on terminal i get this:

[IMG]http://i.imgur.com/X6ToQpD.png[/IMG]

I dont know why there is 1024x768 on the top with plus. Plus should be next to resolution 1920x1080. How to fix it?
When i take another monitor everything is working great.
Can you help me?
(Ubuntu 14.04, on previous versions is the same situation)

---

### Post by jmbell on 2014-04-16
Do you mean grub boot screen? Or the ubuntu login screen? If the former, could you show the contents of /etc/default/grub? Specifically what's written in the line (commented out by default): ```
 #GRUB_GFXMODE=640x480 
``` If it's the latter, I'm not so sure.

---

### Post by pkdev on 2014-04-17
grub boot screen and login screen
this is my grub config
```
# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.
# For full documentation of the options in this file, see:
#   info -f grub -n 'Simple configuration'

GRUB_DEFAULT="0"
GRUB_HIDDEN_TIMEOUT="0"
GRUB_HIDDEN_TIMEOUT_QUIET="true"
GRUB_TIMEOUT="10"
GRUB_DISTRIBUTOR="`lsb_release -i -s 2> /dev/null || echo Debian`"
GRUB_CMDLINE_LINUX_DEFAULT="splash xvga=1920x1080x24"
GRUB_CMDLINE_LINUX=""

# Uncomment to enable BadRAM filtering, modify to suit your needs
# This works with Linux (no patch required) and with any kernel that obtains
# the memory map information from GRUB (GNU Mach, kernel of FreeBSD ...)
#GRUB_BADRAM="0x01234567,0xfefefefe,0x89abcdef,0xefefefef"

# Uncomment to disable graphical terminal (grub-pc only)
#GRUB_TERMINAL="console"

# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
#GRUB_GFXMODE=1920x1080
GRUB_GFXPAYLOAD_LINUX=1600x1200x32

# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID="true"

# Uncomment to disable generation of recovery mode menu entries
#GRUB_DISABLE_RECOVERY="true"

# Uncomment to get a beep at grub start
#GRUB_INIT_TUNE="480 440 1"


```

---

### Post by grahammechanical on 2014-04-17
May I refer you this this page?

[http://pkg-xorg.alioth.debian.org/howto/use-xrandr.html](http://pkg-xorg.alioth.debian.org/howto/use-xrandr.html)

Note this comment:
> 

[LIST]
[*][COLOR=black]The mode marked with a star (*) is the current mode.[/COLOR]
[*][COLOR=black]The one marked with a plus (+) is the preferred one. Most monitors report a preferred mode to the driver. And the server/driver will generally choose it by default.[/COLOR]
[/LIST]


We should also keep in mind that Linux sets the screen resolution from information placed by the manufacturer in a memory chip in the monitor and not from a configuration file. This information is called Extended Display Identification Data (EDID). This is why we are able to switch monitors without editing a configuration file or running a set up utility.

If you are using a proprietary video driver you can use the configuration/setting utility that came with the driver to detect displays. If we are using the open source video driver we can use the Displays utility in System Settings to detect displays. That might rectify things.

It occurs to me that Linux (and the login screen) will use the manufacturer preferred video display setting but it is only when we load into Ubuntu that any user defined setting will take effect. Your machine is not using the manufacturer preferred video display setting and that might possibly be due to you choosing another setting. The one that is actually in use.

This is what I see when I run xrandr

> Screen 0: minimum 320 x 200, current 1680 x 1050, maximum 8192 x 8192
DVI-I-1 connected primary 1680x1050+0+0 (normal left inverted right x axis y axis) 433mm x 271mm
   1680x1050      60.0*+
   1280x1024      75.0     60.0  
   1280x960       60.0  
   1152x864       75.0  
   1024x768       75.1     70.1     60.0  
   832x624        74.6  
   800x600        72.2     75.0     60.3     56.2  
   640x480        75.0     72.8     66.7     60.0  
   720x400        70.1  
VGA-1 disconnected (normal left inverted right x axis y axis)
HDMI-1 disconnected (normal left inverted right x axis y axis)

Notice, my actual setting is also the manufacturer preferred setting because I have not made any adjustments.


Regards.

---

