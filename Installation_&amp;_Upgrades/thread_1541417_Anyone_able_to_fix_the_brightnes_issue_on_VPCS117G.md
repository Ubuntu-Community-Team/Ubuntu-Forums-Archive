---
title: "Anyone able to fix the brightnes issue on VPCS117GG Sony Vaio?"
date: 2010-07-29
forum: Installation &amp; Upgrades
---

### Post by disappearedng on 2010-07-29
Dear everyone, 
The brightness Fn key on my new Sony VAIO VPCS117GG laptop doesn't work. I did an update and installed the Nvidia driver correctly and even configured my xorg.conf to work thanks to atreides8081. 

Has anyone been successful?

---

### Post by roger_1960 on 2010-07-29
Hi

Cant help specifically (I have a Toshiba with the same problem) but there is a LCD brightness applet which you can install in the panel.

---

### Post by disappearedng on 2010-07-29
yeah I added that applet and it doesn't work. When I try moving the scale in any direction, the applet window closes immediately (looks like it's crashing). Adjusting brightness reports changes on libnotify but then it actually doesn't change the brightness at all.

---

### Post by lechien73 on 2010-07-29
People are reporting various issues with the Fn key brightness control on Sony Vaios. There's a bug filed about it, but it's currently "unassigned".

Some things that have worked for other people are:

Open a terminal window and type:

```
gksu gedit /etc/default/grub
```

In the line that says GRUB_CMDLINE_LINUX and add or change it to read:

```
GRUB_CMDLINE_LINUX="acpi_backlight=vendor"
```

Save it and then, in your terminal window, run

```
sudo update-grub
```

And reboot!

A further solution is shown below:

1. Find out the vendor string used by hal:

 $ lshal | grep system.hardware.vendor

 (E.g.: system.hardware.vendor = 'Sony Corporation )

2. Find out the product string:

 $ lshal | grep system.hardware.product

 (E.g.: system.hardware.product = 'VPC-S117GG' )

3. Type:
```
gksu gedit /usr/share/hal/fdi/information/10freedesktop/10-laptop-panel-hardware.fdi

```
4. Add this line

```
<match key="/org/freedesktop/Hal/devices/computer:system.hardware.vendor" string="Sony Corporation">
 <match key="/org/freedesktop/Hal/devices/computer:system.hardware.product" contains_outof="VPC-S117GG">
   <!-- needed since the acpi video module reports it handle the events, but it don't work on this machines-->
          <merge key="laptop_panel.brightness_in_hardware" type="bool">false</merge>
        </match>
</match>

```
5. Reboot!

More details here: [http://uri.tl/n](http://uri.tl/n)

Have a look at post #35 onwards, I took the above information from there and modified it according to what I think your system would return :)

---

### Post by unbuntu85 on 2010-07-29
look the only advice i can give you is:


if you had unbuntu 10.04 on acer aspireone you could you the FN button hold it and click the > arron button that goes this way >
thats the only advice i can give you 
sorry if that wasnt advice that was easy but it works atleast!!:p

---

### Post by disappearedng on 2010-07-30
Tried both. Doesn't really work either. I noticed that your modelno 
had an extra hypen in it. ( I tried grepping lshal and it didn't have '-' in it)

> **lechien73 said:**
> People are reporting various issues with the Fn key brightness control on Sony Vaios. There's a bug filed about it, but it's currently "unassigned".

Some things that have worked for other people are:

Open a terminal window and type:

```
gksu gedit /etc/default/grub
```

In the line that says GRUB_CMDLINE_LINUX and add or change it to read:

```
GRUB_CMDLINE_LINUX="acpi_backlight=vendor"
```

Save it and then, in your terminal window, run

```
sudo update-grub
```

And reboot!

A further solution is shown below:

1. Find out the vendor string used by hal:

 $ lshal | grep system.hardware.vendor

 (E.g.: system.hardware.vendor = 'Sony Corporation )

2. Find out the product string:

 $ lshal | grep system.hardware.product

 (E.g.: system.hardware.product = 'VPC-S117GG' )

3. Type:
```
gksu gedit /usr/share/hal/fdi/information/10freedesktop/10-laptop-panel-hardware.fdi

```
4. Add this line

```
<match key="/org/freedesktop/Hal/devices/computer:system.hardware.vendor" string="Sony Corporation">
 <match key="/org/freedesktop/Hal/devices/computer:system.hardware.product" contains_outof="VPC-S117GG">
   <!-- needed since the acpi video module reports it handle the events, but it don't work on this machines-->
          <merge key="laptop_panel.brightness_in_hardware" type="bool">false</merge>
        </match>
</match>

```
5. Reboot!

More details here: [http://uri.tl/n](http://uri.tl/n)

Have a look at post #35 onwards, I took the above information from there and modified it according to what I think your system would return :)

---

### Post by disappearedng on 2010-07-31
> **disappearedng said:**
> Tried both. Doesn't really work either. I noticed that your modelno 
had an extra hypen in it. ( I tried grepping lshal and it didn't have '-' in it)

It appears that there's a solution with ATI cards towards the end of that url. I was wondering if there is a new update for nvidia cards...

---

### Post by disappearedng on 2010-08-07
> **disappearedng said:**
> It appears that there's a solution with ATI cards towards the end of that url. I was wondering if there is a new update for nvidia cards...

No it doesn't....

I can use nvidia's program to adjust my screen brightness.

My mouse sort of sucks. I don't know whether that's a problem with sony or the drivers.

In addition, typing on this laptop is kind of difficult because keys are not really responsive. I almost can't type double charcters without going back to fixing them.

For further reference, do not get Sony VPCS 117GG if you intend to use linux on top of it.

---

### Post by jneyra on 2010-08-20
Hi all. I get full working laptop, a Sony Vaio F11 series.

0. Previously you should configure nvidia driver, in /etc/X11/xorg.conf
```

   Option         "RegistryDwords" "EnableBrightnessControl=1"

```

1. Find out the vendor string used by hal:
```

$ lshal | grep system.hardware.vendor

```
(E.g.: system.hardware.vendor = 'Sony Corporation )

2. Find out the product string:
```

$ lshal | grep system.hardware.product

```

(E.g.: system.hardware.product = 'VPCF113FX' )

3. Type:
```

sudo vim /usr/share/hal/fdi/information/10freedesktop/10-laptop-panel-hardware.fdi

```

4. Add this line
```

<match key="/org/freedesktop/Hal/devices/computer:system.hardware.vendor" string="Sony Corporation">
 <match key="/org/freedesktop/Hal/devices/computer:system.hardware.product" contains_outof="VPCF113FX">
   <!-- needed since the acpi video module reports it handle the events, but it don't work on this machines-->
          <merge key="laptop_panel.brightness_in_hardware" type="bool">false</merge>
        </match>
</match>

```

5. Reboot!

It works on Gnome and KDE 4.

P.S: If you have changed /etc/default/grub
```

GRUB_CMDLINE_LINUX="acpi_backlight=vendor"

```

Restore to default value

```

GRUB_CMDLINE_LINUX=""

```

Reboot

---

