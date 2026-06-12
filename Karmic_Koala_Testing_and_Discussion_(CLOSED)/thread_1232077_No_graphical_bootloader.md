---
title: "No graphical bootloader"
date: 2009-08-05
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by jackhynes on 2009-08-05
Haven't had a graphical bootloader since I installed A2, is this because it is being phased out or because I installed a package under Jaunty to associate the loading bar speed with time rather than progress?

At the moment my bootsplash is what looks like an architect's technical documents.

---

### Post by phenest on 2009-08-05
I guess you're refering to usplash? Works here. Have you got the 'splash' kernel option in grub?

---

### Post by jackhynes on 2009-08-08
> **phenest said:**
> I guess you're refering to usplash? Works here. Have you got the 'splash' kernel option in grub?

Not sure, I'm using GRUB2. I haven't disabled it.

---

### Post by jackhynes on 2009-08-13
bump

---

### Post by inportb on 2009-08-13
Hm... wanna do a screenshot for us? =p

---

### Post by hikaricore on 2009-08-13
> **inportb said:**
> Hm... wanna do a screenshot for us? =p

now that's just mean..

---

### Post by wayne_cat on 2009-08-13
> **jackhynes said:**
> Not sure, I'm using GRUB2. I haven't disabled it.

find out if it is enabled/disabled

```
root@macbook:~# grep splash /etc/default/grub 
GRUB_CMDLINE_LINUX_DEFAULT="quiet [COLOR=Red]**splash**[/COLOR]"
```

---

### Post by jackhynes on 2009-08-13
> **wayne_cat said:**
> find out if it is enabled/disabled

```
root@macbook:~# grep splash /etc/default/grub 
GRUB_CMDLINE_LINUX_DEFAULT="quiet [COLOR=Red]**splash**[/COLOR]"
```

I receive the same message as above.

---

### Post by inportb on 2009-08-13
> **hikaricore said:**
> [QUOTE=inportb;7780700]Hm... wanna do a screenshot for us? =pnow that's just mean..[/QUOTE]

What do you mean *that's just mean*? I'm curious about these architect's technical documents... I might have seen that myself while trying usplash-smooth ;p

---

### Post by jackhynes on 2009-08-13
> **inportb said:**
> Hm... wanna do a screenshot for us? =p

How is this...

---

### Post by inportb on 2009-08-13
That's exactly what I was expecting... I saw this myself and was wondering what was going on. I never tried usplash-smooth again after that. Perhaps I should. (thanks for the screenshot ;p )

---

### Post by jackhynes on 2009-08-13
> **inportb said:**
> That's exactly what I was expecting... I saw this myself and was wondering what was going on. I never tried usplash-smooth again after that. Perhaps I should. (thanks for the screenshot ;p )

So... you offering a solution?

---

### Post by wayne_cat on 2009-08-13
> **jackhynes said:**
> I receive the same message as above.

usplash-smooth is not supported on Karmic. You can disable the bootsplash (if you want)

--------------------
Edit the file /etc/defaults/grub and change the line:

```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
```to

```
GRUB_CMDLINE_LINUX_DEFAULT="quiet"
```the run the command "update-grub2"
-------------------
Or you can use a supported bootsplash ...

---

### Post by inportb on 2009-08-13
> **wayne_cat said:**
> usplash-smooth is not supported on Karmic

Aww snap. Do you know why that is so?

---

### Post by hessiess on 2009-08-13
The screen shot is a monitor calibration image.

---

### Post by wayne_cat on 2009-08-13
> **inportb said:**
> Aww snap. Do you know why that is so?

The original package was for Intrepid and there is a version for Jaunty:

[https://launchpad.net/~usplash-smooth/+archive/ppa]("https://launchpad.net/%7Eusplash-smooth/+archive/ppa")


... but Karmic:

```
root@macbook:~# dpkg -l |grep bootsplash |grep -v libusplash0
rc  usplash                                        0.5.33                                     Userspace bootsplash utility
ii  xsplash                                        0.4-0ubuntu1                               X based bootsplash
root@macbook:~#  
```this is what we have ... mmmm ... xsplash :)

---

### Post by jackhynes on 2009-08-15
> **wayne_cat said:**
> The original package was for Intrepid and there is a version for Jaunty:

[https://launchpad.net/~usplash-smooth/+archive/ppa]("https://launchpad.net/%7Eusplash-smooth/+archive/ppa")


... but Karmic:

```
root@macbook:~# dpkg -l |grep bootsplash |grep -v libusplash0
rc  usplash                                        0.5.33                                     Userspace bootsplash utility
ii  xsplash                                        0.4-0ubuntu1                               X based bootsplash
root@macbook:~#  
```this is what we have ... mmmm ... xsplash :)
I appreciate the help but I still don't understand why I don't have a graphical bootloader. xsplash and usplash are both installed and usplash-smooth is not installed. Why am I seeing a calibration image instead?

---

### Post by wayne_cat on 2009-08-15
> **jackhynes said:**
> I appreciate the help but I still don't understand why I don't have a graphical bootloader. xsplash and usplash are both installed and usplash-smooth is not installed. Why am I seeing a calibration image instead?

Do you see the image just for a moment or is it visible until GDM starts?

---

### Post by jackhynes on 2009-08-15
> **wayne_cat said:**
> Do you see the image just for a moment or is it visible until GDM starts?

Yeah it is in place of the usplash and behaves in the same way (loading bar, disk check messages [if needed] etc.), just looks really ugly.

---

### Post by wayne_cat on 2009-08-15
> **jackhynes said:**
> Yeah it is in place of the usplash and behaves in the same way (loading bar, disk check messages [if needed] etc.), just looks really ugly.

I'm not sure where this image comes from ... artefact in the fame buffer?

Have you tried this:

[http://ubuntuforums.org/showpost.php?p=7781323&postcount=13](http://ubuntuforums.org/showpost.php?p=7781323&postcount=13)

This switches from "boot splash" to a plain text boot.

---

### Post by jackhynes on 2009-08-15
> **wayne_cat said:**
> I'm not sure where this image comes from ... artefact in the fame buffer?

Have you tried this:

[http://ubuntuforums.org/showpost.php?p=7781323&postcount=13](http://ubuntuforums.org/showpost.php?p=7781323&postcount=13)

This switches from "boot splash" to a plain text boot.

Yeah, but what I should have is the graphical boot...

---

### Post by cdEWoozy on 2009-08-15
> **jackhynes said:**
> Yeah, but what I should have is the graphical boot...

IIRC usplash is embedded in the initrd. You probably need to re-generate the initrd by running ```
sudo dpkg-reconfigure usplash
```

If you have more than the default usplash theme installed, you may need to run ```
sudo update-alternatives --config usplash-artwork.so
``` and select the right theme. The default theme is ```
/usr/lib/usplash/usplash-theme-ubuntu.so
```

---

### Post by jackhynes on 2009-08-16
Thanks cdEWoozy that fixed it for me. I think the new boot screen looks great! Now how do I mark this thread as solved, it's no longer under Thread Tools?

---

