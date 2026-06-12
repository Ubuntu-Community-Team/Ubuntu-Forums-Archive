---
title: "Problem upon Upgrade - FGLRX Pkg Not Configured"
date: 2015-07-31
forum: Installation &amp; Upgrades
---

### Post by Rick St. George on 2015-07-31
Running v14.04 Trusty. Receive the following Error (not knowing what to do next) ...

```

stephen@linus2me:~$ sudo apt-get dist-upgrade
[sudo] password for stephen: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
2 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
Do you want to continue? [Y/n] y
Setting up fglrx-updates (2:15.200-0ubuntu0.3) ...
update-alternatives: warning: forcing reinstallation of alternative /usr/lib/fglrx/ld.so.conf because link group i386-linux-gnu_gl_conf is broken
update-alternatives: error: unable to remove '/etc/ati': Is a directory
dpkg: error processing package fglrx-updates (--configure):
 subprocess installed post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of fglrx-amdcccle-updates:
 fglrx-amdcccle-updates depends on fglrx-updates; however:
  Package fglrx-updates is not configured yet.

dpkg: error processing package fglrx-amdcccle-updates (--configure):
 dependency problems - leaving unconfigured
No apport report written because the error message indicates its a followup error from a previous failure.
                          Errors were encountered while processing:
 fglrx-updates
 fglrx-amdcccle-updates
E: Sub-process /usr/bin/dpkg returned an error code (1)
stephen@linus2me:~$ 

```

Any suggestions?
Thanks
Rick

---

### Post by QIII on 2015-07-31
Hello!

What happens if you do

```
sudo amdconfig --initial 
```

---

### Post by Rick St. George on 2015-07-31
I get this;

```

sudo amdconfig --initial
[sudo] password for stephen: 
Uninitialised file found, configuring.
Using /etc/X11/xorg.conf
Saving back-up to /etc/X11/xorg.conf.original-0


```

Does this help? Now should I run Dist-Upgrade ???

---

### Post by QIII on 2015-07-31
That's exactly what we need to see.

Don't do dist-upgrade just yet.  The driver initialization requires a reboot.

Do that first and then try update and dist-upgrade.

---

### Post by Bashing-om on 2015-07-31
Rick St. George; Hi !


FGLRX relates to a proprietary graphics driver for the ATI chip sets.
It will behoove us to know what hardware and driver is presently installed.
```

dpkg -l | grep -i fglrx
lspci -vnn | grep VGA -A 12
sudo lshw -C display

```
Then we can consider purging/(RE-)installing the graphics driver .

[INDENT][INDENT]just what I think
[/INDENT][/INDENT]

---

### Post by QIII on 2015-07-31
If it weren't installed properly, using amdconfig would have returned an "unknown command" message.

The original output also indicated the file was present, but unconfigured.

;)

---

### Post by Rick St. George on 2015-07-31
> **QIII said:**
> That's exactly what we need to see.

Don't do dist-upgrade just yet.  The driver initialization requires a reboot.

Do that first and then try update and dist-upgrade.

Rebooted ... Ran update ... Screen went BLACK ... Montor shows "No Signal". 
HDD shows busy, but afraid I'm going to have to do a cold restart.

I thought the screen may blackout briefly, and restore. But it hasn't after 5 minutes.
Any thoughts or ideas before I do a Cold Restart? Note, I'm on another machine now.

Thanks!

---

### Post by QIII on 2015-07-31
Do a cold reboot first so we can see.

What GPU model are you using?

---

### Post by Rick St. George on 2015-07-31
Uh Oh ! ! !
Don't know what happened ... but, cold reboot brought up nohting and monitor read "No Signal". HDD shows busy, but don't know what is going on. 

GPU - you mean power supply? Took off cover to see - Diablotek 400W ATX.
System has MOBO: PC chips 3000+; CPU AMD Sempron 3000; 1 GB Ram

---

### Post by QIII on 2015-07-31
No.  The graphics card.

---

### Post by Rick St. George on 2015-07-31
GPU: XFX One, 1GB DDR3, HDMI DVI PCI-Express 2.1

---

### Post by QIII on 2015-07-31
So, an HD 5450?

---

### Post by Rick St. George on 2015-07-31
Yes, I suppose - here is the Link to what I have in this older computer.
[http://www.newegg.com/Product/Product.aspx?Item=N82E16814150655](http://www.newegg.com/Product/Product.aspx?Item=N82E16814150655)

But now the machine doesn't come up, at least ... I can't see anything and have to power it off.

Suggestions???  Perhaps a Repair with the install DVD? Have to download one (no problem) as this was just upgraded to 14.04.

---

### Post by QIII on 2015-07-31
Don't reinstall just yet.  That's what I call the "Blast off and nuke 'em from orbit" option.  A last resort.

The most likely issue and the one most easily corrected did not pan out.

So now we get back to what Bashing-om was suggesting.

Reboot your machine and when the motherboard splash disappears, immediately hold down the shift key.  (If you have your BIOS set to not display the splash, just hold the shift key down immediately after you hear the POST beep.)

That should bring you to the GRUB menu.

Select "Advanced options" (or similar) and arrow down to "Root with networking" and select that.

After a boatload of text scrolls by, you should be at a command line as root.  However, your system will be mounted read-only and you won't be able to make changes.  You need to mount read/write as follows:

```
mount -o remount,rw /
```

Careful.  remount,rw has no spaces.  Now you will be able to make changes.

We'll need to purge the driver and start fresh.

```
apt-get purge fglrx fglrx-updates fglrx-amdcccle fglrx-amdcccle-updates
```

You need to purge both pairs because if you don't it may try to install the other.

We'll also need to remove the xorg.conf created when you initialized the driver.  We'll rename it rather than deleting it for now. By default, Ubuntu does not need an xorg.conf.  Leaving it there without the fglrx driver will cause problems.

```
mv /etc/X11/xorg.conf /etc/X11/xorg.conf.old
```

Reboot.

Let us know if you get back to the GUI.

---

### Post by Rick St. George on 2015-07-31
Thanks "QII", I didn't run all that YET.  I rebooted, holding down Shift Key, and wah-lah ... it came up!

Ran "lshw" - got this;

```

$ sudo lshw -C display
[sudo] password for stephen: 
  *-display               
       description: VGA compatible controller
       product: Cedar [Radeon HD 5000/6000/7350/8350 Series]
       vendor: Advanced Micro Devices, Inc. [AMD/ATI]
       physical id: 0
       bus info: pci@0000:01:00.0
       version: 00
       width: 64 bits
       clock: 33MHz
       capabilities: pm pciexpress msi vga_controller bus_master cap_list rom
       configuration: driver=fglrx_pci latency=0
       resources: irq:41 memory:d0000000-dfffffff memory:febe0000-febfffff ioport:e000(size=256) memory:febc0000-febdffff


```

What do you think?  Should I still need to follow your Recommends?

Thanks!

---

### Post by Bashing-om on 2015-07-31
Rick St. George; Hummm ....

That do show that the proprietary driver is installed .

QIII, Is it time to look at the log file ?
```

cat /var/log/Xorg.0.log 

```

see what 
[INDENT][INDENT]tale is told 
[/INDENT][/INDENT]

---

### Post by QIII on 2015-07-31
Here's what I'm thinking:  upgrading to a newer release of Ubuntu without first uninstalling proprietary drivers is almost a sure recipe for a significant emotional event.

In case that is what caused this, that can be rectified by uninstalling the driver, cleaning up any configuration and then rebooting.  That will take you back to the original default olen source driver.

From there, normal installation of the driver should work fine.

So yes, I think you should purge the driver.  It is clearly "installed" but it may be borked.

---

### Post by Rick St. George on 2015-07-31
Thanks Guys .. . I will consider this Done!  Be glad when I am as smart as you, re: linux.
Know basic commands and it feels good being in control of my own computer. 
Thanks for making Open Source OS Ubuntu work for all of us. You Rock ! ! !

CASE CLOSED.
:guitar:

---

### Post by QIII on 2015-07-31
It ain't done 'til it's done!  We may not be as smart as you think -- I don't think I am.

Let us know how you make out.

---

### Post by Bashing-om on 2015-07-31
> **QIII said:**
> It ain't done 'til it's done!  We may not be as smart as you think -- I don't think I am.

Let us know how you make out.

+1 ( I have not broke my system as much as QIII has, I have a long way to go).

Given time, you will learn.

It is not over 'til it is fixed - purge and (RE-)install, then see where we are.

One of these days, when I am as smart as QIII is, and he is as mart as you think he is
[INDENT][INDENT]watch out, formidable things are happening
[/INDENT][/INDENT]

---

