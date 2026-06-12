---
title: "Cannot put grub background image"
date: 2011-02-20
forum: Installation &amp; Upgrades
---

### Post by jogonjr on 2011-02-20
Hi again. I am trying to put a background image in my grub but am unsuccessful. I am using Ubuntu 10.04. I was able to set the resolution to 1366x768 but the background remains black and if I do sudo update-grub, it wont even say Found Background image as it is supposed to according to some guides in the forums. I have tried for so long yet still not working so I am posting again. Here is my 05_theme file.

```
&#65279;#!/bin/bash -e

source /usr/lib/grub/grub-mkconfig_lib

# this allows desktop-base to override our settings
f=/usr/share/desktop-base/grub_background.sh
if test -e ${f} ; then
  source ${f}
else
  WALLPAPER="/usr/share/images/desktop-base/leafscreen.png"
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
  for i in {/boot/grub,/usr/share/images/grub,/home/drs/mysplash}/BonsaiTridentMaple.{png,tga,jpg,jpeg}; do
    if is_path_readable_by_grub $i ; then 
      bg=$i
      case ${bg} in
        *.png)        reader=png ;;
        *.tga)        reader=tga ;;
        *.jpg|*.jpeg)    reader=jpeg ;;
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
  set color_normal=white/black
  set color_highlight=brown/black
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

Thanks for any help.

---

### Post by dino99 on 2011-02-20
[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)

---

### Post by coffeecat on 2011-02-20
> **jogonjr said:**
> Here is my 05_theme file.

It's usually called 05_debian_theme. Is it executable? And sorry to ask such a basic question, but did you check you have your image at 
/usr/share/images/desktop-base/leafscreen.png? There isn't a /usr/share/images/desktop-base/ folder in a default installation.

---

### Post by jogonjr on 2011-02-20
Yes, the image is there. I'll include a snapshot of it. I have also tried the downloaded images in [I]/usr/share/images/grub to no avail. One thing is unusual though. 
The line [/I][I][B]
GRUB_BACKGROUND=/usr/share/images/desktop-base/xxxxx.png  
[/B][/I]does not exist in**   '/etc/default/grub**'     as it says here 
[https://help.ubuntu.com/community/Grub2#GRUB%202%20Splash%20Images](https://help.ubuntu.com/community/Grub2#GRUB%202%20Splash%20Images)
 I tried to add it replacing the xxxx.png with my leafscreen.png but it still doesnt work.


[[IMG]http://img143.imageshack.us/img143/378/screenshot1zqc.th.png[/IMG]]("http://img143.imageshack.us/i/screenshot1zqc.png/")

Uploaded with [ImageShack.us]("http://imageshack.us")

---

### Post by Quackers on 2011-02-20
That line doesn't appear in my /etc/default/grub either and I have a splash image working. I think it may depend on the actual version of grub2 installed - possibly.
If you have installed the grub2 splashimages file, I would suggest you try one of those first. 
Here is my line from /etc/grub.d/05_debian_theme
WALLPAPER="/usr/share/images/grub/B-1B_over_the_pacific_ocean.tga" 
which I believe is the file in which the grub2 splashimages file is installed to.

Edit  Just in case you are not doing, you must "save" the file before exiting, then run sudo update-grub afterwards.

---

### Post by coffeecat on 2011-02-20
> **Quackers said:**
> That line doesn't appear in my /etc/default/grub either

Nor mine in either Lucid or Maverick. I think the documentation may be in error. I'm sure it used to refer to 05_debian_theme. Like Quackers my background splash works OK so I don't know why yours isn't. For the record, this is a fragment of my /etc/grub.d/05_debian_theme in Maverick:

```
# this allows desktop-base to override our settings
f=/usr/share/desktop-base/grub_background.sh
if test -e ${f} ; then
  . ${f}
else
#  WALLPAPER="/usr/share/images/desktop-base/moreblue-orbit-grub.png"
  WALLPAPER="/usr/share/images/desktop-base/No_Escape.png"
  COLOR_NORMAL="black/black"
  COLOR_HIGHLIGHT="magenta/black"
fi
```And this from my Lucid 05_debian_theme (now disused in favour of Maverick's grub, but it was working).

```
# this allows desktop-base to override our settings
f=/usr/share/desktop-base/grub_background.sh
if test -e ${f} ; then
  source ${f}
else
#  WALLPAPER="/usr/share/images/desktop-base/moreblue-orbit-grub.png"
  WALLPAPER="/usr/share/images/grub/emperor-1920x1200.png"
  COLOR_NORMAL="black/black"
  COLOR_HIGHLIGHT="magenta/black"
fi
```There's a slight difference in the if clause, but I don't know enough to know what this means.

---

### Post by grahammechanical on 2011-02-20
I tried the method being used here and it took a lot of effort to get it working. Then I did a fresh install and just could not be bothered reading up on it all over again. So I used Grub Customizer

[http://ubuntuforums.org/showthread.php?p=10340183#post10340183](http://ubuntuforums.org/showthread.php?p=10340183#post10340183)

Now I have a splash image. Easy to do as well.

Regards.

---

### Post by jogonjr on 2011-02-21
Thank You all for your help. Unfortunately it still doesn't work. I make sure I do everything right. I don't forget to save and update the grub. I also tried the grub-customizer thinking it will end my misery but it didn't. I installed it, ran it, went to preferences, browsed for the image, copied to grub,saved,restarted. No go. :(

---

### Post by coffeecat on 2011-02-22
Have you tried with a different image file? I wonder if there might be something about your PNG that grub doesn't like.

---

### Post by Quackers on 2011-02-22
I suspect it's the version of grub2 in use. Have a look at section 8 in this guide by drs305. The version of grub has a big say in what will be needed
[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)

---

### Post by jogonjr on 2011-02-26
I reinstalled ubuntu and i finally got it to work. Thanks to you all.

---

