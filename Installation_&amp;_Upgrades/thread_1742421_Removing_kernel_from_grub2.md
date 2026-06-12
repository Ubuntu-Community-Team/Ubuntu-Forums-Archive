---
title: "Removing kernel from grub2"
date: 2011-04-28
forum: Installation &amp; Upgrades
---

### Post by And6ate9 on 2011-04-28
How do you go about removing old kernel from other distros from the grub menu. 

For example I have lucid and ubuntu studio installed. Lucid controls the grub2. So how would I remove the old kernel out of the ubuntu studio?

---

### Post by slooksterpsv on 2011-04-28
Easiest way is to uninstall the kernel you don't need anymore. Difficult way is to modify the /boot/grub/grub.cfg file and remove the kernel from the options there, issue with that is if it does an update-grub, it'll add that kernel back in.

So if it was kernel 2.6.35-22 you wanted to remove you could do:

sudo apt-get remove linux-image-2.6.35-22-generic

---

### Post by garvinrick4 on 2011-04-28
> **And6ate9 said:**
> How do you go about removing old kernel from other distros from the grub menu. 

For example I have lucid and ubuntu studio installed. Lucid controls the grub2. So how would I remove the old kernel out of the ubuntu studio? boot into ubuntu studio and run
```
grep menuentry /boot/grub/grub.cfg
```open Synaptics and type in the offending kernel starting with 2.6. in upper right box.
Mark for it to be removed and apply it.

---

### Post by wilee-nilee on 2011-04-28
> **And6ate9 said:**
> How do you go about removing old kernel from other distros from the grub menu. 

For example I have lucid and ubuntu studio installed. Lucid controls the grub2. So how would I remove the old kernel out of the ubuntu studio?

Difficult at least for me to understand your intentions. 

Do you have ubuntu tweak installed in either OS if not install it in both it will remove Kernels easily. then run 
sudo update-grub 
after to reset the grub menu.
[http://ubuntu-tweak.com/downloads/](http://ubuntu-tweak.com/downloads/)

The above post #3 works quite well also.

---

### Post by And6ate9 on 2011-04-28
so I am guessing I would have to boot into the 2nd os and then do the uninstall. Then boot into the first os and update grub?

---

### Post by williejones on 2011-04-28
> **And6ate9 said:**
> so I am guessing I would have to boot into the 2nd os and then do the uninstall. Then boot into the first os and update grub?

Yes that is what what you need to do.

---

### Post by And6ate9 on 2011-04-28
Damn player how'd I get all dem beans!!!!!!

Sweetness!!!!!!!!!

---

### Post by drs305 on 2011-04-28
The way Grub2 constructs its menu is a bit convoluted. It looks first for other grub.cfg and menu.lst files.

If you want to try it without leaving your current system, you can try this and see if it removes the kernel from your current grub.cfg file. While in your controlling OS:

Open up your ubuntu studio's grub.cfg file by mounting the studio's partition and running "gksu gedit /mountpoint/boot/grub/grub.cfg".

Manually delete the entry you don't want to see. It should be in the 10_linux section of the ubuntu studio's grub.cfg file (It should also be in the 30_os... section of your controlling grub.cfg - but leave your lucid one intact for now). 

Caution: Of course, leave yourself at least one bootable menuentry in your ubuntu studio, and you should also make sure it isn't the default entry in either your lucid or studio grub.cfg file. (It's more important in your lucid grub.cfg, since that is the one controlling your boot, but keep your studio grub.cfg entry somewhat viable anyway.)

Save the file, then run update grub in your current lucid installation. 

I think you should find the deleted kernel entry is not displayed in your lucid grub.cfg.

The next time you boot your ubuntu studio, remove the kernel and update grub (This will update the non-default grub.cfg file, but this is the file your lucid grub will look to when it updates its own grub.cfg).

---

### Post by And6ate9 on 2011-04-28
OH SNAP@!!!!! 

YOU GOT COFFEE CUPS YO!!!!!

Yo gotta give me some of them cup!!!!!!!

I need to hold all my beans player!!!!!!!!!!!!!!!!

How do I marked this thread solved?

---

### Post by slooksterpsv on 2011-04-28
At the top it says Thread Tools click it then click Mark Thread as Solved

---

### Post by And6ate9 on 2011-04-29
OH DOUBLE  SNAP!1 you got the coffee  too cuz!!!

I gott get me some java up in here!!!!!

Just wait till I bust out with the cream and sugar!!!

---

