---
title: "How do you make a master grub2 menu"
date: 2010-04-29
forum: Installation &amp; Upgrades
---

### Post by jis on 2010-04-29
I want to install more than on linux distribution on one computer (and the computer has Windows XP, too). How do you make a master grub2 installation that is in its own partition and that has entries that chainload different linux distributions that may have grub2 or grub?

---

### Post by phillw on 2010-04-29
> **jis said:**
> I want to install more than on linux distribution on one computer (and the computer has Windows XP, too). How do you make a master grub2 installation that is in its own partition and that has entries that chainload different linux distributions that may have grub2 or grub?

As a general rule, the LAST installation of ubuntu (or any other that uses Grub2) will ask to install grub2 and then do a scan for all other operating systems whether they be Win, Suse, Knoppix etc.
It will even check out all different hard-drives for operating systems (Hey, those devs are good :-) )

Grub2 can handle linuxes that use grub-legacy and all windows operating systems (I've not seen it with the new Apple O/S), but not the other way round (unless you want to spend a lot of time editing stuff).

Once they are all on, you can alter the order in which they appear in the list if you want.

Regards,

Phill.

---

### Post by jis on 2010-04-29
When I get new kernel via updates to a distribution, a new item is added to its grub menu. How is that handled for the previous distributions? Are their grub menus chainloaded from the grub2 menu of the last installed distribution?

---

### Post by louieb on 2010-04-29
Check out Herman's GRUB2 page - there is a how to create a dedicated GRUB partition there.

[IDBS GRUB 1.97]("http://members.iinet.net/%7Eherman546/p20.html")  

I'm still using GRUB legacy in my dedicated GRUB partition. Let us know how it goes. I may switch it to GRUB2 in the future.

---

### Post by rolnics on 2010-04-30
> **louieb said:**
> Check out Herman's GRUB2 page - there is a how to create a dedicated GRUB partition there.

[IDBS GRUB 1.97]("http://members.iinet.net/%7Eherman546/p20.html")  

I'm still using GRUB legacy in my dedicated GRUB partition. Let us know how it goes. I may switch it to GRUB2 in the future.

I'd be interested as well. Although I'm tempted to try myself as well.

I've been searching today and that link seem to be the best / most comprehensive I've found so far. Although its raised some questions which I think putting it into practice will solved!

---

### Post by jis on 2010-04-30
Install Ubuntu so that Grub is installed at the same partition as / (or /boot if you use separate /boot). Create also a  partition for the master grub2 menu; in this example it is /dev/sda1 and Stage 1 of the master grub2 will be installed in MBR of /dev/sda.

Then in Ubuntu 9.10 or 10.4 do the following. Using a Live CD or equivalent is fine, I think.
```

sudo mount /dev/sda1 /mnt
sudo grub-install --root-directory=/mnt /dev/sda
sudo grub-mkconfig --output=/mnt/boot/grub/grub.cfg

```

Then edit /mnt/boot/grub/grub.cfg (even if editing is prohibited in the file) to include entry for the OS(s):

```

# If Grub was installed at /dev/sda2 in Ubuntu installation,
# the menu entry should be like this:
menuentry "Ubuntu at /dev/sda2" {
        set root=(hd0,2)
        chainloader +1
}

```

Extra entries can be removed in the file.

Finally unmount the dedicated partition
```
sudo umount /mnt
```

But how do you get grub remember the last used entry so that, if you reboot, the same entry will be used without user interaction?

---

### Post by rolnics on 2010-05-01
> **jis said:**
> 
Then edit /mnt/boot/grub/grub.cfg (even if editing is prohibited in the file) to include entry for the OS(s):

```

# If Grub was installed at /dev/sda2 in Ubuntu installation,
# the menu entry should be like this:
menuentry "Ubuntu at /dev/sda2" {
        set root=(hd0,2)
        chainloader +1
}

```


You've answered my question for me thanks.

So does this mean you're up and running with this then?

---

### Post by jis on 2010-05-01
Yes, but I still have not succeeded setting grub to remember last selection.

---

### Post by efflandt on 2010-05-01
> **jis said:**
> Yes, but I still have not succeeded setting grub to remember last selection.

In /etc/default/grub:

#GRUB_DEFAULT=0
GRUB_DEFAULT=saved

---

### Post by jis on 2010-05-02
> **efflandt said:**
> In /etc/default/grub:

#GRUB_DEFAULT=0
GRUB_DEFAULT=saved

It didn't work for me. Did someone get it work?

---

### Post by frantid on 2010-05-02
you also have to have

GRUB_SAVEDEFAULT=true

set in /etc/dault/grub

---

### Post by jis on 2010-05-02
> **frantid said:**
> you also have to have

GRUB_SAVEDEFAULT=true

set in /etc/dault/grub

I think I tried that, too, but maybe I did something wrong. Did anyone get this work?

---

### Post by frantid on 2010-05-02
> **jis said:**
> I think I tried that, too, but maybe I did something wrong. Did anyone get this work?


It didn't work for me until I added the second line.  You can add "savedefault"  manually to the entries in grub.cfg you want to be able to set it on.  It sets a line in the file grubenv in /boot/grub/

---

### Post by jis on 2010-05-03
> **frantid said:**
> It didn't work for me until I added the second line.  You can add "savedefault"  manually to the entries in grub.cfg you want to be able to set it on.  It sets a line in the file grubenv in /boot/grub/

Thanks, I needed to add "savedefault" to the entries in grub.cfg.

---

