---
title: "Grub2 boot splash not working need advice"
date: 2010-03-21
forum: Installation &amp; Upgrades
---

### Post by speed32219 on 2010-03-21
I have been trying to get a boot image to display on a minimal install of Ubuntu. I have followed the steps in the grub2 wiki but I can&#8217;t get it to work. attached are the steps I have taken with no change in boot. (No Image)

~$ grub-install -v
grub-install (GNU GRUB 1.97~beta4)

sudo apt-get install grub2-splashimages

sudo cp /usr/share/images/grub/*.tga /boot/grub/

sudo nano /etc/grub.d/05_debian_theme

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
**use_bg=true**
if [ "$GRUB_TERMINAL_OUTPUT" = "gfxterm" ] ; then
   for i in {/boot/grub,/usr/share/images/desktop-base,**/usr/share/images/grub**}/B-1B_over_the_pacific_ocean.{png,tga} ; do
#   WALLPAPER="/usr/share/images/grub/B_1B_over_the_pacific_ocean.tga"	 
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
```

I have also tried to change this.
sudo nano /etc/default/grub
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash",  without any change.
(Tried splash and left blank).

And the update command. Could it be my file permissions?

```
:~$ sudo update-grub2
Generating grub.cfg ...
**Found Debian background: B-1B_over_the_pacific_ocean.tga**
Found linux image: /boot/vmlinuz-2.6.31-20-generic
Found initrd image: /boot/initrd.img-2.6.31-20-generic
Found memtest86+ image: /boot/memtest86+.bin
done

```

And the File in multiple locations. 
 ls -al /boot/grub/B-*
-rwxr-xr-x 1 root root 816018 2010-03-20 02:42 /boot/grub/B-1B_over_the_pacific_ocean.tga

ls -al /usr/share/images/grub/B-*
-rw-r--r-- 1 root root 816018 2008-05-10 13:58 /usr/share/images/grub/B-1B_over_the_pacific_ocean.tga

---

### Post by speed32219 on 2010-03-22
I just installed Karmic 2.6.31-24-server on a CF card.  Of course no splash as default, bit I followed the same steps as above and still no splash, just the normal black and white boot messages.

I do not know why it is not working, Maybe I need to move back to Jaunty.  I also added the temp fix  for the SMB2 boot error in GRUB, now I get an additional 1.5 screens of driver load information. I do not see how Xsplash would have anything to do with the boot image.  Just grabbing for straws, but maybe I should try that next.

---

### Post by Elfy on 2010-03-23
Hi - I was involved in a broken one of these the other day on IRC. They also had what appeared to be an odd /etc/grub.d/05_debian_theme file - yours looks truncated as well.

This is mine 

```
#!/bin/bash -e

source /usr/lib/grub/grub-mkconfig_lib

# this allows desktop-base to override our settings
f=/usr/share/desktop-base/grub_background.sh
if test -e ${f} ; then
  source ${f}
else
  WALLPAPER=[COLOR="Blue"]"/boot/grub/Wood.png"[/COLOR]
  COLOR_NORMAL="black/black"
  COLOR_HIGHLIGHT="magenta/black"
fi

set_mono_theme()
{
  cat << EOF
set menu_color_normal=white/black
set menu_color_highlight=black/light-gray
EOF
}

# check for usable backgrounds
use_bg=false
if [ "$GRUB_TERMINAL_OUTPUT" = "gfxterm" ] ; then
  for i in /boot/grub/`basename ${WALLPAPER}` ${WALLPAPER} ; do
    if is_path_readable_by_grub $i ; then 
      bg=$i
      case ${bg} in
        *.png)		reader=png ;;
        *.tga)		reader=tga ;;
        *.jpg|*.jpeg)	reader=jpeg ;;
      esac
      if test -e /boot/grub/${reader}.mod ; then
        echo "Found background image: `basename ${bg}`" >&2
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
  set color_normal=${COLOR_NORMAL}
  set color_highlight=${COLOR_HIGHLIGHT}
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

I only needed to put the patch to the wallpaper as highlighted above - there were some changes in grub2 I think that led to that. 

I will add though that I have lucid and my grub is grub-install (GNU GRUB 1.98-1ubuntu2) - so possibly your's does in fact need to be as it is.

Actually - I will post my karmic grub debian theme file as well

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
  for i in {/boot/grub,/usr/share/images/grub/}Windbuchencom.{png,tga} ; do
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
  set color_highlight=green/black
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

Hope that is of some help

---

### Post by bcollignon on 2010-10-21
Splash not working in Ubuntu 10.10 even though image is found when running sudo update-grub.  05_debian_theme module is as follows:

#!/bin/sh -e

. /usr/lib/grub/grub-mkconfig_lib

# this allows desktop-base to override our settings
f=/usr/share/desktop-base/grub_background.sh
if test -e ${f} ; then
  . ${f}
else
  WALLPAPER="/usr/share/images/grub/e3grub.tga"
  COLOR_NORMAL="black/black"
  COLOR_HIGHLIGHT="magenta/black"
fi

set_mono_theme()
{
  cat << EOF
set menu_color_normal=light-gray/black
set menu_color_highlight=black/light-gray
EOF
}

# check for usable backgrounds
use_bg=false
for output in ${GRUB_TERMINAL_OUTPUT}; do
  if [ "$output" = "gfxterm" ] ; then
    for i in /boot/grub/`basename ${WALLPAPER}` ${WALLPAPER} ; do
      if is_path_readable_by_grub $i ; then 
        bg=$i
        case ${bg} in
          *.png)		reader=png ;;
          *.tga)		reader=tga ;;
          *.jpg|*.jpeg)	        reader=jpeg ;;
        esac
        if test -e /boot/grub/${reader}.mod ; then
          echo "Found background image: `basename ${bg}`" >&2
          use_bg=true
          break
        fi
      fi
    done
    break
  fi
done

# set the background if possible
if ${use_bg} ; then
  prepare_grub_to_access_device `${grub_probe} --target=device ${bg}`
  cat << EOF
insmod ${reader}
if background_image `make_system_path_relative_to_its_root ${bg}` ; then
  set color_normal=${COLOR_NORMAL}
  set color_highlight=${COLOR_HIGHLIGHT}
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

Any help appreciated.

---

### Post by drs305 on 2010-10-21
bcollignon,

You get the "Found background image..." message in the terminal when you update grub?

Some things to check:
The image is the proper size for the resolution you are using.
The image is in fact the proper format (I know it has a tga extension)
You don't have 'console' enabled in /etc/default/grub

If you want to troubleshoot further, install the 'approved' splash images:
```
sudo apt-get install grub2-splashimages
```
Set your wallpaper setting in 05_... to /usr/share/images/grub/... and pick one of the default wallpapers.
Update grub, reboot, and see if the wallpaper appears.

---

### Post by anthr6x on 2010-12-15
I had the same problem with 10.10. it finds the image I have pointed to on update-grub, but shows nothing on startup. but when pointed to an image at /usr/share/images/grub/ installed by grub2-splashimages, it worked fine. so I copy the image i want to use to /usr/share/images/grub/ and update the /etc/grub.d/05_debian_theme and there it was, working like a charm. hope that helps.

---

