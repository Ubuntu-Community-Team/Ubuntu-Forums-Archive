---
title: "Screen Resolution"
date: 2005-03-22
forum: Installation &amp; Upgrades
---

### Post by wjmay on 2005-03-22
Hi,
I am new to Linux and need some help.  Somehow, during installation, I chose the wrong screen res.  Now, when Ubuntu starts it gives me a lot of garbage, rather than the logon screen.  I knoe that I can change run levels, so that i can change it in the command shell.  I just can't remember how to do that.  And then, do i just run setup to change it, or is there another command for gnome ?

Thanx for the help

---

### Post by alastair on 2005-03-22
There's the "edit the /etc/X11/xorg.conf" way, which might be over-complex initially for someone not used to this, or other ways that might work :

1) Back up (make a copy of) your X config file i.e.

cd /etc/X11
sudo cp -p xorg.conf xorg.conf.bak

(although since it is broken, perhaps not that improtant!)

2) Try a "reconfigure" i.e.

sudo dpkg-reconfigure xserver-xorg

---

### Post by JRHolmes on 2005-03-25
I have a similar problem.  After upgrading from Warty to Hoary, my screen resolution has shifted to a plain VGA display.  It appears that the server has properly found the Intel Integrated graphics controller, but there are no options above 640 x 480 for the resolution.

I found elsewhere and prior to going to these forums, I ran:

sudo dpkg-reconfigure xserver-xorg

I either failed to properly respond to that setup info or it failed.  Either way, I had no success in getting the resolution reset to anything other than VGA.

---

### Post by mpries on 2005-03-25
On my IBM ThinkPad T23 I resolved the problem by changing the Monitor section in the /etc/X11/xorg.conf file in

Section "Monitor"
         Identifier         "BuiltinLCD"
         VendorName   "IBM"
         ModelName     "Laptop 1024x768"
         HorizSync        31.5 - 90.0
         VertRefresh     59.0 - 70.0
         # Option         "dpms"
EndSection

After this change I can choose other resulutions than 640x480 at the GNOME screen resulution dialog.

---

### Post by 8oluf7 on 2005-03-29
[QUOTE=mpries]On my IBM ThinkPad T23 I resolved the problem by changing the Monitor section in the /etc/X11/xorg.conf file in

Section "Monitor"
         Identifier         "BuiltinLCD"
         VendorName   "IBM"
         ModelName     "Laptop 1024x768"
         HorizSync        31.5 - 90.0
         VertRefresh     59.0 - 70.0
         # Option         "dpms"
EndSection

After this change I can choose other resulutions than 640x480 at the GNOME screen resulution dialog.[/QUOTE]

Yeah-but: I found I also had to change the monitor identifier in another section "Default Monitor", before this worked. I also took the opportunity to add the 1280x1024 resolution missing from the various depth/resolution combinations in the subsequent sections. Once this had been done Gnome opened up in 1280x1024.

But it's stuck at 60Hz refresh rate. Sigh. When I've got my internet connection back (another thing broken by upgrading from Warty to Hoary), I'll try gtf (suggested by another poster).

---

### Post by bistrototal on 2005-03-30
Hi,
i had the same problem with the resolution until i added the following to my xorg.conf:
```

        HorizSync    30 - 70
        VertRefresh  50.0 - 75.0

```

Now it works perfectly well!

---

