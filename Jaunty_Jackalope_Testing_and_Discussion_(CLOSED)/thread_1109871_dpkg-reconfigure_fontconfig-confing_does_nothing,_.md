---
title: "dpkg-reconfigure fontconfig-confing does nothing,  Bug or featrure?"
date: 2009-03-29
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by negativ on 2009-03-29
As of today, 

```
$ sudo dpkg-reconfigure fontconfig-config
```

simply returns me to a command prompt. No error message or other feedback of any kind.  Is this a bug, or has something changed?  I tried searching around but couldn't find anything to indicate that this is intended behavior.

I certainly hope this is merely a bug which will be resolved (and soon), because I *need* to be able to use bitmap fonts, and I don't know of any other way to enable them.  Any workaround or advice would be appreciated.

---

### Post by Zorael on 2009-03-29
Huh, weird, works on my jaunty installation. I guess you could try to reinstall the fontconfig-config package, just in case something broke?

And if you need bitmapped fonts in X sessions, you should be able to enable them in ~/.fonts.conf.

```
<?xml version='1.0'?>
<!DOCTYPE fontconfig SYSTEM 'fonts.dtd'>
<fontconfig>

<!-- other content -->

 <match target="font" >
  <edit mode="assign" name="embeddedbitmap" >
   <bool>true</bool>
  </edit>
 </match>

<!-- likewise -->

</fontconfig>
```

Attaching mine, just for kicks.

---

### Post by coffeecat on 2009-03-29
> **Zorael said:**
> Huh, weird, works on my jaunty installation.


Even weirder, I do have fontconfig-config installed on my Jaunty and, like negativ, nothing happens when I run sudo dpkg-reconfigure fontconfig-config. While not quite nothing. There's a brief flurry of disc activity and I'm returned to a prompt with no output at all.

> **negativ said:**
> I *need* to be able to use bitmap fonts

Oo-er! :(

Seriously, I'm not sure whether this will work but I think it might, in /etc/fonts/conf.avail are two files, 70-no-bitmaps.conf and 70-yes-bitmaps.conf. I guess you'll need 'yes'. :wink: Just set up a symlink in /etc/fonts/conf.d thusly:

```
sudo ln -s /etc/fonts/conf.avail/70-yes-bitmaps.conf /etc/fonts/conf.d/70-yes-bitmaps.conf
```

---

### Post by nugencs on 2009-03-30
weird indeed! just did a clean install of kubuntu jaunty beta. typing "sudo dpkg-reconfigure fontconfig-config" does nothing...only returns me to the prompt. but "sudo dpkg-reconfigure fontconfig" works.

hmm... it was working before i did the clean install. i upgraded from intrepid to jaunty i386 back then and it was ok. just this morning, i did a clean install to be able to use ext4 and move to amd64. :(

---

### Post by coffeecat on 2009-03-30
> **nugencs said:**
> weird indeed! just did a clean install of kubuntu jaunty beta. typing "sudo dpkg-reconfigure fontconfig-config" does nothing...only returns me to the prompt. but "sudo dpkg-reconfigure fontconfig" works.

That's interesting. It used to be "sudo dpkg-reconfigure fontconfig" around about the Breezy or Dapper days, but then changed to "sudo dpkg-reconfigure fontconfig-config" somewhere around Edgy or Feisty iirc. That change threw me for a time because I always used this to enable Autohinting. But font rendering is so good in Jaunty, I don't have to anymore - which is nice. :)

Anyway, I tried "sudo dpkg-reconfigure fontconfig" in my Jaunty and got this output:

```
Cleaning up font configuration of fontconfig...
Cleaning up category cid..
Cleaning up category truetype..
Cleaning up category type1..
Updating fontconfig cache for /usr/share/fonts/truetype/ttf-indic-fonts-core /usr/share/fonts/truetype/thai /usr/share/fonts/truetype/sazanami /usr/share/fonts/truetype/ttf-bitstream-vera /usr/share/fonts/truetype/ttf-lao /usr/share/fonts/truetype/unfonts /usr/share/fonts/truetype/ttf-arabeyes /usr/share/fonts/truetype/ttf-liberation /usr/share/fonts/truetype/ttf-dejavu /usr/share/fonts/truetype/freefont /usr/share/fonts/truetype/arphic /usr/share/fonts/truetype/ttf-malayalam-fonts /usr/share/fonts/type1/gsfonts
Updating fontconfig cache for /usr/share/fonts/truetype/ttf-indic-fonts-core /usr/share/fonts/truetype/thai /usr/share/fonts/truetype/sazanami /usr/share/fonts/truetype/ttf-bitstream-vera /usr/share/fonts/truetype/ttf-lao /usr/share/fonts/truetype/unfonts /usr/share/fonts/truetype/ttf-arabeyes /usr/share/fonts/truetype/ttf-liberation /usr/share/fonts/truetype/ttf-dejavu /usr/share/fonts/truetype/freefont /usr/share/fonts/truetype/arphic /usr/share/fonts/truetype/ttf-malayalam-fonts /usr/share/fonts/type1/gsfonts
Updating font configuration of fontconfig...
Cleaning up category cid..
Cleaning up category truetype..
Cleaning up category type1..
Updating category type1..
Updating category truetype..
Updating category cid..
Updating fontconfig cache for /usr/share/fonts/truetype/ttf-indic-fonts-core /usr/share/fonts/truetype/thai /usr/share/fonts/truetype/sazanami /usr/share/fonts/truetype/ttf-bitstream-vera /usr/share/fonts/truetype/ttf-lao /usr/share/fonts/truetype/unfonts /usr/share/fonts/truetype/ttf-arabeyes /usr/share/fonts/truetype/ttf-liberation /usr/share/fonts/truetype/ttf-dejavu /usr/share/fonts/truetype/freefont /usr/share/fonts/truetype/arphic /usr/share/fonts/truetype/ttf-malayalam-fonts /usr/share/fonts/type1/gsfonts
Updating fontconfig cache for /usr/share/fonts/truetype/ttf-indic-fonts-core /usr/share/fonts/truetype/thai /usr/share/fonts/truetype/sazanami /usr/share/fonts/truetype/ttf-bitstream-vera /usr/share/fonts/truetype/ttf-lao /usr/share/fonts/truetype/unfonts /usr/share/fonts/truetype/ttf-arabeyes /usr/share/fonts/truetype/ttf-liberation /usr/share/fonts/truetype/ttf-dejavu /usr/share/fonts/truetype/freefont /usr/share/fonts/truetype/arphic /usr/share/fonts/truetype/ttf-malayalam-fonts /usr/share/fonts/type1/gsfonts
Regenerating fonts cache... done.
```But no ncurses-type interface to set autohinting, bitmapped fonts, etc, so this will be no use to the OP unfortunately.

All very curious.

---

### Post by nugencs on 2009-03-30
i tried reinstalling the fontconfig-config package, but it still doesn't work. it's really a bummer :(

anybody know another way of tuning subpixel font rendering other than using fontconfig-config?

---

### Post by pferraro on 2009-03-30
> **nugencs said:**
> i tried reinstalling the fontconfig-config package, but it still doesn't work. it's really a bummer :(

anybody know another way of tuning subpixel font rendering other than using fontconfig-config?

The fontconfig-config package was responsible for creating the sym links in your /etc/fonts/conf.d/ directory from the available options in /etc/fonts/conf.available/.  Performing these steps manually is easy enough.

For example, unlike firefox-3.0, firefox-3.5 takes its font hinting orders from fontconfig, instead of gnome's font settings.  My desktop uses medium, subpixel hinting in gnome, but my firefox fonts were using slight, greyscale hinting (the fontconfig default).  To fix this, I did this:
sudo rm /etc/fonts/conf.d/10-hinting-slight.conf
sudo rm /etc/fonts/conf.d/10-no-sub-pixel.conf
sudo ln -s /etc/fonts/conf.available/10-hinting-medium.conf /etc/fonts/conf.d/.
sudo ln -s /etc/fonts/conf.available/10-sub-pixel-rgb.conf /etc/fonts/conf.d/.
sudo dpkg-reconfigure fontconfig

---

### Post by coffeecat on 2009-03-31
> **nugencs said:**
> anybody know another way of tuning subpixel font rendering other than using fontconfig-config?

Have a look at my earlier post re creating symlinks between /etc/fonts/conf.avail and /etc/fonts.conf.d. Poster pfeffaro is saying the same thing.

---

### Post by niek_nijmegen on 2009-04-03
Any update on this? I always used this to change the hinting algorithm from 'native' to 'auto-hinter' or vice-versa.

Even though the default hinting in 9.04 is way better than before, i would still like to be able to change it.

---

### Post by coffeecat on 2009-04-03
> **niek_nijmegen said:**
> Any update on this? I always used this to change the hinting algorithm from 'native' to 'auto-hinter' or vice-versa.

Even though the default hinting in 9.04 is way better than before, i would still like to be able to change it.

I've always preferred autohinting myself. There's a file "10-autohint.conf" in /etc/fonts/conf.avail. Just make a symlink to it in /etc/fonts/conf.d also called "10-autohint.conf" and that should do it. That's what I've always done in other distros that don't have the fontconfig-config utility. The improvement varies from distro to distro, presumably because of variations in code in the various *.conf files in conf.avail.

Having said all that, I find the font rendering is so good in Jaunty (my setting is Subpixel smoothing > Slight) that, for the first time since I discovered autohinting, I haven't enabled it. But I have installed the msttcorefonts and I use the Apple font Lucida Grande for my desktop. That helps a lot too.

---

### Post by niek_nijmegen on 2009-04-06
ah! wonderful. that worked like a charm! I feel at home again :-)

---

### Post by Cam_B on 2009-04-11
bump

I also *need* (want to really badly) use bitmap fonts. and fontconfig-config hangs for a split second, and then just spits me back to the prompt. I have enabled bitmap fonts successfully tonnes of times before on 8.10 and 8.04, but 9.04 is being difficult.

I also tried the simlink thing, which doesn't seem to work.

Any help appreciated.

---

