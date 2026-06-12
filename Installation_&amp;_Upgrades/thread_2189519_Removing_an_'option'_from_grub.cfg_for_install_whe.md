---
title: "Removing an 'option' from grub.cfg for install where grub is configured"
date: 2013-11-22
forum: Installation &amp; Upgrades
---

### Post by mc4man on 2013-11-22
There is an obscure (at this point), video display issue that only occurs on an install where grub is configured.
So in other words, in a multiboot  - 
install A - grub is configured on, issue exists
install B - booted from os-prober entry, issue does not occur
(if grub is reconfigured to install B then it shows issue, install A then is fine.

The difference seems to be the install where grub is configured has this section, the problem is in red.
```
if loadfont $font ; then
 [COLOR="#FF0000"] set gfxmode=auto[/COLOR]
  load_video
  insmod gfxterm
  set locale_dir=$prefix/locale
  set lang=en_US
  insmod gettext
fi
```

If I remove the red line & reboot then that install no longer shows the video issue. 
So the question is - how to remove that line/option permanently so update-grub does not put back

---

### Post by oldfred on 2013-11-22
I would think it is more likely to be boot options or how each install is configured.
The gfxmode is for grub to show its menu, it used to be just 640x480 or whatever BIOS gave. It now tries to use settings from system for video.

That setting can be overridden in grub with this

         gksudo gedit /etc/default/grub

You can change to the resolution that works.

> # The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
#GRUB_GFXMODE=640x480


What video card/chip do you have? And have you install drivers or set boot parameters in the Linux line?

 #To see video:
sudo lshw -c display
sudo lshw | grep -A 11 display
lspci | grep VGA
#Resolution:
xwininfo -root

---

### Post by mc4man on 2013-11-22
For some unknown reason when grub uses "set gfxmode=auto" then **after login** video playback can be affected in a limited scenario
(I can't fathom why this occurs but can be demonstrated here quite clearly in at least one instance - 

There is a new video player called mpv which is a fork of mplayer2. It can use something call osc (on screen controller) which is a control panel that appears over the video window when a mouse cursor is placed over the window. Generally it works fine without issue.

However on a machine with Intel video (intel 4000) if one uses 'libvdpau-va-gl1' to provide vdpau support for intel then when 'osc' is exposed video playback becomes very late, almost to halt. When the osc disappears then the video catches up.
This only occurs on the install where grub is configured & I've traced it to that line/option. Without it all is fine with mpv & osc.

When booting to an install that grub isn't configured on then it doesn't seem to use  set gfxmode at all so there video playback/osc is not affected.

So what I can't figure is how to persistently  disable 'set gfxmode=..'  on the install grub is configured on.

The 'ability' of grub parameters _to affect video after login_ is also seen in this unrelated RH bug (which was closed as it stopped at some point
[https://bugzilla.redhat.com/show_bug.cgi?id=838723](https://bugzilla.redhat.com/show_bug.cgi?id=838723)

Edit: figured a hackish method by editing 2 templates, 00_header & 10_linux, (turned out I needed 2 lines removed
mpv will be in 14.04, if osc is enabled then will just file a bug on libvdpau-va-gl1 & or grub

---

### Post by oldfred on 2013-11-22
With Intel I really do not know what works. All these have been posted as working boot options. It may just depend on model.

  Older Intel video card: i915.modeset=1 or i915.modeset=0 newer:  i915.i915_enable_rc6=1

   Some other Intel boot options
acpi_osi=Linux  acpi_backlight=vendor
 i915.i915_enable_rc6=1

   Force Intel Video mode as boot parameter in grub menu - change to your screen size
video=1280x1024-24@60
and if that doesn't work you can try
video=VGA-1:1280x1024-24@60

   Asus i3 with Intel graphics, 
acpi_osi=Linux
video=1280x1024-24@75 or whatever native resolution is

   For Intel graphics running slow:
sudo apt-get install mesa-utils
glxinfo | grep OpenGL | head -n3

---

### Post by mc4man on 2013-11-24
This was really just an issue with a certain type of osd having issues when grub sets a gfxmode (which it either doesn't do for an os-prober boot or does differently on a grub configured boot.
In any event I don't have any use for gfxmode during boot, in the 9 - 10 sec it takes don't care how it looks or at what res.

(I guess one way to see the diff I'm referring to would be to have 2 recent ubuntu installs, then on both remove quiet splash. The grub configured boot will have higher res text than the os-prober boot

So to prevent update-grub from adding gfxmode to my affected boot (grub configured/first listed) just adjusted 2 templates as such & all is fine with osc.
(maybe a better way but this will suffice for the moment

```
--- /etc/grub.d/00_header	2013-11-22 21:44:24.334026219 -0500
+++ /etc/grub.d/00_header	2013-11-22 21:44:24.334026219 -0500
@@ -202,7 +202,6 @@
 	fi
 
     cat << EOF
-  set gfxmode=${GRUB_GFXMODE}
   load_video
   insmod gfxterm
 EOF

--- /etc/grub.d/10_linux	2013-11-22 21:55:29.006117251 -0500
+++ /etc/grub.d/10_linux	2013-11-22 21:55:29.006117251 -0500
@@ -150,10 +150,6 @@
 	  echo "	load_video" | sed "s/^/$submenu_indentation/"
       fi
   fi
-  if ([ "$ubuntu_recovery" = 0 ] || [ x$type != xrecovery ]) && \
-     ([ "x$GRUB_GFXPAYLOAD_LINUX" != x ] || [ "$gfxpayload_dynamic" = 1 ]); then
-      echo "	gfxmode \$linux_gfx_mode" | sed "s/^/$submenu_indentation/"
-  fi
 
   echo "	insmod gzio" | sed "s/^/$submenu_indentation/"
```

---

