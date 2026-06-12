---
title: "Does grub need a widescreen vga option."
date: 2008-11-12
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by philinux on 2008-11-12
Since there are a lot of widescreen displays in use does it not make sense to have some widescreen resolution options available via vga=XXX. If this is possible.

The default usplash is squished for me.

---

### Post by MacUntu on 2008-11-12
A neverending story. See [https://bugs.launchpad.net/ubuntu/+source/usplash/+bug/64147](https://bugs.launchpad.net/ubuntu/+source/usplash/+bug/64147)

> For my 1280*768 screen I created a 1280*768 image, compressed it to 1024*768 (4:3) and overwrote the 4:3 image usplash was using for my screen.

That's how I did it. A bit laborious with all the indexing stuff (all images have to use the same color palette) but it works fine.

---

### Post by dudude on 2008-11-12
Maybe in ten years when GRUB 2 is released, this will be fixed. :)

---

### Post by BwackNinja on 2008-11-12
Not a problem with grub, but a limitation of the system. Plymouth, if adopted, works around this I think.

---

### Post by PatrickVogeli on 2008-11-15
I agree... until then I use the [wideubuntu]("http://www.gnome-look.org/content/show.php/Wideubuntu+Usplash?content=84632") usplash theme, which looks awesome

Maybe ubuntu should include that one and a small script to set it up automatically

---

### Post by andrewabc on 2008-11-15
> **PatrickVogeli said:**
> I agree... until then I use the [wideubuntu]("http://www.gnome-look.org/content/show.php/Wideubuntu+Usplash?content=84632") usplash theme, which looks awesome

Maybe ubuntu should include that one and a small script to set it up automatically

I don't know anything about laptops, but you should be able to edit 

/etc/usplash.conf

Mine has 
> # Usplash configuration file
# These parameters will only apply after running update-initramfs.

xres=1680
yres=1050
Sometimes I have to edit it (doesn't recognize desktop resolution), switch monitors etc.

---

### Post by philinux on 2008-11-15
I tried that and got no splash screen at all on my desktop monitor.

I'll try the widebuntu when I get home.

---

### Post by andrewabc on 2008-11-15
Of course try different resolutions (that just happens to be my native monitor resolution).

Searching google and the forums for such stuff should have a similar how to with the usplash.conf file.

---

### Post by Josh04 on 2008-11-15
Depending on your graphics card BIOS, widescreen resolutions may be avilalable as numbers in the 8xx range. If not, there's a 915resolution module for GRUB2 which will let you set widescreen resolutions with the vga=xxx tag - you need to apply a patch to grub though.

---

### Post by MacUntu on 2008-11-15
Usplash cannot handle video modes other than 4:3 so there is no way other than using a widescreen pixmap compressed to 4:3 to get a nice boot splash.

---

### Post by Hairy_Palms on 2008-11-16
Usplash Does Support Widescreen video modes, only if your graphics card framebuffer supports them, which u can check with
>  sudo hwinfo --framebuffer
and see what resolutions come out.

---

### Post by MacUntu on 2008-11-16
> **Hairy_Palms said:**
> Usplash Does Support Widescreen video modes

Well, I guess they include this just for fun:

[QUOTE=README]Themes have a ratio field where you can specify either USPLASH_4_3 if the image is a true 4:3 image or 16:9 if the image is a 16:9 image, scaled to 4:3. The image MUST be a 4:3 image, because usplash can only handle 4:3 video modes currently.[/QUOTE]

;)

---

### Post by philinux on 2008-11-16
Tried wideubuntu and go nosplash just text at startup and no text at shutdown. Ah well.

---

### Post by Hairy_Palms on 2008-11-17
> Well, I guess they include this just for fun
maybe, either that or it just hasnt been updated, its supported widescreen since at least hardy, it doesnt work automatically as 4:3 does, but it still works if your card supports it.

> sudo apt-get install hwinfo
sudo hwinfo --framebuffer

copy the vga code to /boot/grub/menu.lst

sudo gedit /boot/grub/menu.lst

add vga=0x0259 or w/ever vga code you got given for the resolution above
(0x0259 is for 24-bit 1440x900 in my Geforce)

Save, and run the following command:
sudo update-grub

Edit the following file:
sudo gedit /etc/usplash.conf

Change to your resolution, save, and run the following command:
sudo dpkg-reconfigure usplash


---

