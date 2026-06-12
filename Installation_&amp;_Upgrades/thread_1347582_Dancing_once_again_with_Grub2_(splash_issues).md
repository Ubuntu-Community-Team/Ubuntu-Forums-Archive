---
title: "Dancing once again with Grub2 (splash issues)"
date: 2009-12-06
forum: Installation &amp; Upgrades
---

### Post by dan1973 on 2009-12-06
Hello all,

Having a problem setting the grub2 splash image. Don't know why it isn't working. Has been set before on this machine - before a complete re-installation. I'm sure it's some silly small error on my part, can anyone help?

This time i followed the ubuntu documentation and have also retraced my steps to try to find the error.

My images are indeed located /usr/share/images/grub

Below is my 05_debian_theme file.

not sure what else anyone may need to help me - just ask and i'll post.:D

Many thanks for any assistance, 

```

#!/bin/bash -e

source /usr/lib/grub/grub-mkconfig_lib

set_mono_theme()
{
  cat << EOF
set menu_color_normal=white/black
set menu_color_highlight=black/white
EOF
}

# check for usable backgrounds
use_bg=false
if [ "$GRUB_TERMINAL_OUTPUT" = "gfxterm" ] ; then
  for i in {/boot/grub,/usr/share/images/grub}/Windbuchencom.tga.{png,tga} ; do
    if is_path_readable_by_grub $i ; then 
      bg=$i
      case ${bg} in
        *.png)		reader=png ;;
        *.tga)		reader=tga ;;
        *.jpg|*.jpeg)	reader=jpeg ;;
      esac
      if test -e /boot/grub/${reader}.mod ; then
        echo "Found Debian background: `basename ${bg}`" >&2
        use_bg=true
        break
      fi
    fi
  done
fi

# set the background if possible
if ${use_bg} ; then
  prepare_grub_to_access_device `${grub_probe} --target=device ${bg}`
  cat << EOF
insmod ${reader}
if background_image `make_system_path_relative_to_its_root ${bg}` ; then
  set color_normal=black/black
  set color_highlight=magenta/black
else
EOF
fi

# otherwise, set a monochromatic theme for Ubuntu
if ${use_bg} ; then
  set_mono_theme | sed -e "s/^/  /g"
  echo "fi"
else
  set_mono_theme
fi
```

---

### Post by Shazaam on 2009-12-06
This line...
```
for i in {/boot/grub,/usr/share/images/grub}/Windbuchencom.tga.{png,tga} ; do
```
should be this...
```
for i in {/boot/grub,/usr/share/images/grub}/Windbuchencom.{png,tga} ; do
```
Remove tga after the name Windbuchencom but leave the dot.

Mine looks like this...
```
for i in {/boot/grub,/usr/share/images/desktop-base}/Windbuchencom.{png,tga} ; do
```
I have the pics in both folders so grub2 can find them. :)

---

### Post by dan1973 on 2009-12-06
hello,

copied images into the desktop-base folder and changed the 05_debian_theme as follows, but it still fails to pick up the image when i run update-grub.

```
#!/bin/bash -e

source /usr/lib/grub/grub-mkconfig_lib

set_mono_theme()
{
  cat << EOF
set menu_color_normal=white/black
set menu_color_highlight=black/white
EOF
}

# check for usable backgrounds
use_bg=false
if [ "$GRUB_TERMINAL_OUTPUT" = "gfxterm" ] ; then
  for i in {/boot/grub,/usr/share/images/desktop-base}/Windbuchencom.{png,tga} ; do
    if is_path_readable_by_grub $i ; then 
      bg=$i
      case ${bg} in
        *.png)		reader=png ;;
        *.tga)		reader=tga ;;
        *.jpg|*.jpeg)	reader=jpeg ;;
      esac
      if test -e /boot/grub/${reader}.mod ; then
        echo "Found Debian background: `basename ${bg}`" >&2
        use_bg=true
        break
      fi
    fi
  done
fi

# set the background if possible
if ${use_bg} ; then
  prepare_grub_to_access_device `${grub_probe} --target=device ${bg}`
  cat << EOF
insmod ${reader}
if background_image `make_system_path_relative_to_its_root ${bg}` ; then
  set color_normal=black/black
  set color_highlight=magenta/black
else
EOF
fi

# otherwise, set a monochromatic theme for Ubuntu
if ${use_bg} ; then
  set_mono_theme | sed -e "s/^/  /g"
  echo "fi"
else
  set_mono_theme
fi
```

---

### Post by Ginsu543 on 2009-12-06
Check to see if (hd0) is set to the right device (e.g., /dev/sda) in the file /boot/grub/device.map. I also had the same problem with grub 2 picking up splash images. I was trying to solve another issue (when I ran update-grub, it would give me an error message), looked around here and elsewhere, and discovered that (hd0) was not set to my primary Karmic partition in device.map. When I corrected that, I found that not only did it fix my update-grub error message, it also fixed my splash problem.

---

### Post by dan1973 on 2009-12-06
This is my update-grub report:

Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.31-16-generic
Found initrd image: /boot/initrd.img-2.6.31-16-generic
Found Microsoft Windows XP Professional on /dev/sda1
Found Microsoft Windows XP Professional on /dev/sdb1
grub-probe: error: Cannot find a GRUB drive for /dev/sdb1.  Check your device.map.


My sdb1 is an external unbootable NTFS hard drive, I also want to get rid of it from the boot menu.

How do I check my device.map?

---

### Post by dan1973 on 2009-12-06
My device.map reads 

(hd0)	/dev/sda

This seems correct to me?

---

### Post by Ginsu543 on 2009-12-06
Try editing you device.map to read:

(hd0) /dev/sdb

Then update-grub, reboot, and see if your splash screen comes up.

---

### Post by Shazaam on 2009-12-06
OOPS I missed one and I am very sorry.
This...
```
use_bg=false
```
should be changed to true (use background is what it stands for).

---

### Post by dan1973 on 2009-12-07
Hi, if I change use_bg=false to true and try to update grub, it wont let me. The message i get is:

Generating grub.cfg ...
No path or device is specified.
Try ``grub-probe --help'' for more information.
No path or device is specified.
Try ``grub-probe --help'' for more information.


When I change it back to false, grub updates and detects my systems fine but doesn't find the splash image.

---

### Post by dan1973 on 2009-12-07
Should i try and re-install grub2 over the version i have at present or will that just cause more problems?

---

### Post by mick222 on 2009-12-07
> **Shazaam said:**
> OOPS I missed one and I am very sorry.
This...
```
use_bg=false
```
should be changed to true (use background is what it stands for).

This should be "false"
 
I was having the same trouble and gave up a while back but the suggestion of changing the device map settings seems to have worked.I have two hard drives and Karmic is on the second .

---

### Post by Ginsu543 on 2009-12-08
> **mick222 said:**
> This should be "false"
 
I was having the same trouble and gave up a while back but the suggestion of changing the device map settings seems to have worked.I have two hard drives and Karmic is on the second .
Yes, that setting should be "false" because "use_bg=false" is the default setting. The background is used only if the proper background image is found. If you read a little further down the script, you will see "use_bg=true" under the next if...fi subroutine.

---

### Post by Shazaam on 2009-12-08
Hmm. Here is my debian_theme and it works (both "use bg=" set to true)...
```
#!/bin/bash -e

source /usr/lib/grub/grub-mkconfig_lib

set_mono_theme()
{
  cat << EOF
set menu_color_normal=blue/cyan
set menu_color_highlight=black/white
EOF
}

# check for usable backgrounds
use_bg=true
if [ "$GRUB_TERMINAL_OUTPUT" = "gfxterm" ] ; then
  for i in {/boot/grub,/usr/share/images/desktop-base}/Windbuchencom.{png,tga} ; do
    if is_path_readable_by_grub $i ; then 
      bg=$i
      case ${bg} in
        *.png)		reader=png ;;
        *.tga)		reader=tga ;;
        *.jpg|*.jpeg)	reader=jpeg ;;
      esac
      if test -e /boot/grub/${reader}.mod ; then
        echo "Found Debian background: `basename ${bg}`" >&2
        use_bg=true
        break
      fi
    fi
  done
fi

# set the background if possible
if ${use_bg} ; then
  prepare_grub_to_access_device `${grub_probe} --target=device ${bg}`
  cat << EOF
insmod ${reader}
if background_image `make_system_path_relative_to_its_root ${bg}` ; then
  set color_normal=black/black
  set color_highlight=magenta/black
else
EOF
fi

# otherwise, set a monochromatic theme for Ubuntu
if ${use_bg} ; then
  set_mono_theme | sed -e "s/^/  /g"
  echo "fi"
else
  set_mono_theme
fi
```

---

### Post by Ubun2usr on 2010-01-03
Dan1973, Did you get your splash images to work?

I've just updated to Mint 8 & Grub2.  Grub had a nice graphical display on the LiveCD boot but I cannot get graphics up on the full install.  Mint & Unbuntu Grub files are almost identical except for a few names - including the theme setup & grub.cfg.  I've tried making a few changes to the theme file, image locations & have installed grub-splashimages. All seems okay when using either update-grub or grub-makeconfig to produce grub.cfg - but no graphical display when Grub loads!!

Appreciate anyone's recent experience.


If you have a solution, it may work for me.

---

