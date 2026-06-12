---
title: "Mac OSX: Convering ISO to DMG Help!!!"
date: 2015-05-05
forum: Installation &amp; Upgrades
---

### Post by andy134 on 2015-05-05
Hello,

I want to install Ubuntu on my old Mac Pro. I have no ability to burn an install DVD/CD so I need to use a USB stick. I did already follow the instructions from Ubuntu but when I get to the stage when I need to convert the file to DMG, the terminal prompt comes back as file not found or some other weird error. Assuming the ISO file is downloaded to my download folder what is the correct command to type in terminal to convert the ISO file into a Mac disk image IMG? Or is there an easier way to install Ubuntu on Mac? I am using an old OS (10.5 Leopard). I followed 3 different web tutorials for 3 hours and have still failed!

Any help is appreciated.  Thanks!!!

---

### Post by bapoumba on 2015-05-06
have you tried this ? [http://www.ubuntu.com/download/desktop/create-a-usb-stick-on-mac-osx](http://www.ubuntu.com/download/desktop/create-a-usb-stick-on-mac-osx)

---

### Post by andy134 on 2015-05-06
Yes that is EXACTLY what I tried but I get an error message when I copy and paste the command. :(

---

### Post by Vladlenin5000 on 2015-05-06
> **andy134 said:**
> Yes that is EXACTLY what I tried but I get an error message when I copy and paste the command. :(

Most commands aren't to be pasted "as is"... 
Example:
```
hdiutil convert -format UDRW -o [COLOR=#ff0000]~/path/to/target.img[/COLOR] [COLOR=#ff0000]~/path/to/ubuntu.iso[/COLOR]
```

In [COLOR=#ff0000]red [/COLOR][COLOR=#ff0000][/COLOR]the parts that vary. The first should be the full path and full name of the converted file (your choice) and the last should be the full path and full name of the ISO you downloaded. The next is _another example_ where I used a Bento Linux ISO as origin, in the SOFTWARE folder and saved a converted IMG in SOFTWARE2:
```
hdiutil convert -format UDRW -o [COLOR=#008000][COLOR=#008000]/mnt/5abe7285-e644-4423-b6e5-5adde621d645/SOFTWARE2/bento-x86_64.img[/COLOR] /mnt/5abe7285-e644-4423-b6e5-5adde621d645/SOFTWARE/bento-x86_64.iso[/COLOR]
```

---

### Post by andy134 on 2015-05-07
> **Vladlenin5000 said:**
> Most commands aren't to be pasted "as is"... 
Example:
```
hdiutil convert -format UDRW -o [COLOR=#ff0000]~/path/to/target.img[/COLOR] [COLOR=#ff0000]~/path/to/ubuntu.iso[/COLOR]
```

In [COLOR=#ff0000]red [/COLOR]the parts that vary. The first should be the full path and full name of the converted file (your choice) and the last should be the full path and full name of the ISO you downloaded. The next is _another example_ where I used a Bento Linux ISO as origin, in the SOFTWARE folder and saved a converted IMG in SOFTWARE2:
```
hdiutil convert -format UDRW -o [COLOR=#008000][COLOR=#008000]/mnt/5abe7285-e644-4423-b6e5-5adde621d645/SOFTWARE2/bento-x86_64.img[/COLOR] /mnt/5abe7285-e644-4423-b6e5-5adde621d645/SOFTWARE/bento-x86_64.iso[/COLOR]
```

I am not a Linux user I guess, it fails. But thank you all the same for your help Sir! I will stick with my Mac OSX.

Thanks!
Andy

---

### Post by Karl_Hungus on 2015-05-07
DUDE! check this out... just [WATCH]("https://www.youtube.com/watch?v=dCdfUarlerA") the whole thing its pretty simple and this will all make sense now...

---

