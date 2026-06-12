---
title: "Grub2 custom splashes aren't working."
date: 2009-11-06
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by Starks on 2009-11-06
The OMGUBUNTU guide ([http://www.omgubuntu.co.uk/2009/11/install-grub2-backgrounds.html](http://www.omgubuntu.co.uk/2009/11/install-grub2-backgrounds.html)) isn't working and one flips the use_bg argument to true, updating grub no longer works and fails to probe devices.

Has there been a change to grub2 since karmic's release?

---

### Post by ranch hand on 2009-11-06
I have not looked at that guide, I do not have to as changing thatsetting has never been a good idea.

The main reaso nit is not a good idea, as you have discovered. is that it does not work.

Now, have you installed "grub2-splashimages".  This is not really needed but it does give you another folder in /usr/share/images.

Your 05_debian-themes file calls for /usr/share/images/desktop-base.  That needs to be changed if you want to use the files from /usr/share/images/grub that is installed and populated when grub2-splashimages is installed.

If you look at the link in my sig the top 2 links in my post are the best.  I use the directions from the first on (mostly).

I have found, though, that just using the desktop-base file is fine if you want to use your own or some found file.  You do need to change (maybe) the font colors in the lines below where you put your image.

Make sure that the / is before your image name and the . after it.  Png files work fine.
```

# check for usable backgrounds
use_bg=false
if [ "$GRUB_TERMINAL" = "gfxterm" ] ; then
  for i in {/boot/grub,/usr/share/images/desktop-base}/widget.{png,tga} ; do
    if is_path_readable_by_grub $i ; then 
      bg=$i
      case ${bg} in
        *.png)        reader=png ;;
        *.tga)        reader=tga ;;
        *.jpg|*.jpeg)    reader=jpeg ;;
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
  set color_highlight=white/black

```

---

### Post by Starks on 2009-11-06
Thanks. I forgot about the file path.

---

