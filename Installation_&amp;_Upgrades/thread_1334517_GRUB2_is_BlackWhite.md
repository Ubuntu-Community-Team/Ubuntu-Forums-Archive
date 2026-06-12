---
title: "GRUB2 is Black/White"
date: 2009-11-22
forum: Installation &amp; Upgrades
---

### Post by Soorena on 2009-11-22
Hi,

So I followed many guides and I installed the 'grub2-splashimages' and edited the file '/etc/grub.d/05_debian_theme' replacing the default image with the one I selected but when I restart its till black and white with no image.

I have no idea what I need to change here is my 05_debian_theme file:

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
  for i in {/boot/grub,/usr/share/images/desktop-base}/TulipStair_QueensHouse_Greenwich.{png,tga} ; do
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

And here is the /etc/default/grub file:

```
# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.

GRUB_DEFAULT=0
GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT="10"
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="splash"
GRUB_CMDLINE_LINUX=""

# Uncomment to disable graphical terminal (grub-pc only)
#GRUB_TERMINAL=console

# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
#GRUB_GFXMODE=640x480

# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID=true

# Uncomment to disable generation of recovery mode menu entrys
#GRUB_DISABLE_LINUX_RECOVERY="true"
```

So any ideas why it's doing this to me? I'm using Ubuntu 9.10.

Thanks ahead of time,
Soorena

---

### Post by guitarhero183 on 2009-11-22
```
# check for usable backgrounds
use_bg=false
```Try changing "use_bg=false" to "use_bg=true"

---

