---
title: "Problem updating grub2"
date: 2010-01-18
forum: Installation &amp; Upgrades
---

### Post by diegotox on 2010-01-18
Hey guys I'm new to Ubuntu, and I recently installed the 64-bit version of 9.10 successfully on my pc. I've been having trouble updating grub to include a background on the boot menu; I added the necessary codes into the 05_debian_theme file to show the picture when I boot. However, when I type in  the terminal "sudo update-grub2", it starts to compile the new grub.cfg but then gives me an error massage that goes "no path or device is specified/try "grub-probe --help" for more information." What is this about? Please help me solve it!

---

### Post by suseendran.rengabashyam on 2010-01-19
Hi,


       Please check the following line in your configuration file:


       for i in {/boot/grub,/usr/share/images/desktop-base}/ubuntu.{png,tga} ;
       

Make sure that you have mentioned the correct file path and the correct file name.
       

Hope that helps.
                   [URL="http://10.10.43.151:3000/issues/show/74#"]
[/URL]

---

### Post by Leppie on 2010-01-19
hi and welcome to the community.

update-grub2 really is a script for those upgrading from grub legacy so that their menu.lst entries can be processed for use with grub2. just use update-grub.

where is your grub background image located? if you installed the image pack from the repo, you will have to add the path as it does not install to one of the folders indicated by the 05_debian path for images.

---

### Post by diegotox on 2010-01-19
Hey guys, thanks for your help! I will check the file as soon as possible. As for the image's location, I put it in /usr/share/images/desktop-base and named it GRUB, and for the line of code I put "for i in {/boot/grub,/usr/share/images/desktop-base}/GRUB.{png,tga} ;." I think that the problem may be that the picture is not named "ubuntu" but that seeks kind of irrelevant; nevertheless I will try and see.

---

### Post by drs305 on 2010-01-19
I don't believe this is the cause of the error message, but did you name the image GRUB or GRUB.png/GRUB.tga 

I believe it must have the .png or .tga extension as the script is currently configured or it won't recognize it. At least that is what happens on my machine when I don't include the extension. On the other hand it doesn't generate the error message you are getting. It's just something you are going to have to fix once you get the path problem solved.

Posting your /etc/grub.d/05_debian_theme will probably answer a lot of our questions.

---

### Post by Leppie on 2010-01-19
> **diegotox said:**
> Hey guys, thanks for your help! I will check the file as soon as possible. As for the image's location, I put it in /usr/share/images/desktop-base and named it GRUB, and for the line of code I put "for i in {/boot/grub,/usr/share/images/desktop-base}/GRUB.{png,tga} ;." I think that the problem may be that the picture is not named "ubuntu" but that seeks kind of irrelevant; nevertheless I will try and see.
the fact that the image is not called ubuntu isn't a problem.
maybe the image isn't a png or tga file, but a jpg or something different?

---

### Post by diegotox on 2010-01-22
Hey guys sorry for the delay, I was out of town due to a family emergency but all is fine now. I am about to check the script and I will report soon. However, I think thtat I did put the file extension in the image, but I shall check for it right away.

---

### Post by diegotox on 2010-01-22
Ok, here is the line in the 05_debian_theme:

"for i in {/boot/grub,/usr/share/images/desktop-base}/GRUB.tga.{png,tga} ;"

I can also verify that the image is named GRUB, is a .tga image, and is located at /usr/share/images/desktop-base. Also, the image is 1280x800, which is the resolution of my screen. I still do not see what may be the problem.

---

### Post by diegotox on 2010-01-22
And here is the whole 05_debian_theme:


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
use_bg=true
if [ "$GRUB_TERMINAL_OUTPUT" = "gfxterm" ] ; then
  for i in {/boot/grub,/usr/share/images/desktop-base}/GRUB.tga.{png,tga} ; do
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
  set color_normal=white/black
  set color_highlight=black/black
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

---

### Post by Leppie on 2010-01-22
> **diegotox said:**
> 
  for i in {/boot/grub,/usr/share/images/desktop-base}/GRUB.tga.{png,tga} ; do
a small and subtle error. this line should be like this:
```
for i in {/boot/grub,/usr/share/images/desktop-base}/GRUB.{png,tga} ; do
```

the {png,tga} part takes care of the "extension", so you cannot put it with the filename as well (because then it because part of the filename).

---

### Post by diegotox on 2010-01-23
Great! I just corrected the mistake and the new grub.cfg was compiled successfully! I will reboot now and see if it works.

---

### Post by Leppie on 2010-01-23
cool, keep us posted :)

---

### Post by diegotox on 2010-01-23
Ok, when I boot, my selected image is displayed but with the wrong resolution; it seems like it has been stretched in all directions. Even more strange, the menu is actually displayed with the correct resolution. I have double checked the 05_debian_theme and grub.cfg files to make sure that the resolution is written correctly, and it is. I also revised the image and can confirm that it is 1280x800, which is the same as my native resolution. What could the problem be now?

---

### Post by Leppie on 2010-01-23
could you post your grub.cfg?

---

### Post by diegotox on 2010-01-24
Ok, here it is. Please note that I edited the names of the entries, but I don't think that should affect the screen resolution, right?

#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by /usr/sbin/grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s /boot/grub/grubenv ]; then
  have_grubenv=true
  load_env
fi
set default="0"
if [ ${prev_saved_entry} ]; then
  saved_entry=${prev_saved_entry}
  save_env saved_entry
  prev_saved_entry=
  save_env prev_saved_entry
fi
insmod ext2
set root=(hd0,3)
search --no-floppy --fs-uuid --set c978577c-156e-4cc8-b107-c814b461e4ac
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=1280x800
  set gfxpayload=keep
  insmod gfxterm
  insmod vbe
  if terminal_output gfxterm ; then true ; else
    # For backward compatibility with versions of terminal.mod that don't
    # understand terminal_output
    terminal gfxterm
  fi
fi
if [ ${recordfail} = 1 ]; then
  set timeout=-1
else
  set timeout=5
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
insmod ext2
set root=(hd0,3)
search --no-floppy --fs-uuid --set c978577c-156e-4cc8-b107-c814b461e4ac
insmod tga
if background_image /usr/share/images/desktop-base/GRUB.tga ; then
  set color_normal=white/black
  set color_highlight=blue/black
else
  set menu_color_normal=white/black
  set menu_color_highlight=black/white
fi
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry "Ubuntu 9.10" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set quiet=1
    insmod ext2
    set root=(hd0,3)
    search --no-floppy --fs-uuid --set c978577c-156e-4cc8-b107-c814b461e4ac
    linux    /boot/vmlinuz-2.6.31-17-generic root=UUID=c978577c-156e-4cc8-b107-c814b461e4ac ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-17-generic
}
menuentry "Ubuntu 9.10 (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    insmod ext2
    set root=(hd0,3)
    search --no-floppy --fs-uuid --set c978577c-156e-4cc8-b107-c814b461e4ac
    linux    /boot/vmlinuz-2.6.31-17-generic root=UUID=c978577c-156e-4cc8-b107-c814b461e4ac ro single 
    initrd    /boot/initrd.img-2.6.31-17-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

---

### Post by Leppie on 2010-01-24
it seems that bioses do not wide screen formats.

are you sure the text is in this resolution?

---

### Post by diegotox on 2010-01-31
Sorry about the phase out guys I was out on a business trip to Atlanta. Yep I'm pretty sure that is what the text says. It seems to me that the best option now is to tweak the image a bit and make it a little more stretch so that it does not look messed up. Thanks for all your help, guys!

---

### Post by dino99 on 2010-02-09
The latest grub2 is 1.98 now but package is only for Karmic & Lucid; Jaunty still have 1.96.

Is it possible to use 1.98 with Jaunty ?

---

