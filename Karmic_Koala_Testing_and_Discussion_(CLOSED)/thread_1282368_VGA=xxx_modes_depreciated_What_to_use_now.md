---
title: "VGA=xxx modes depreciated? What to use now?"
date: 2009-10-04
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by emarkay on 2009-10-04
In trying to debug my AMD problem:
[http://ubuntuforums.org/showthread.php?p=8046744#post8046744](http://ubuntuforums.org/showthread.php?p=8046744#post8046744)

I saw a fraction of a second a message that"vga=771 has been depreciated........" 
There is a post on this, but it's long and not really to the point:
[http://ubuntuforums.org/showthread.php?t=1264194&highlight=vga%3D771](http://ubuntuforums.org/showthread.php?t=1264194&highlight=vga%3D771)

Thus, for all to reference, WHAT has replaced these boot modes?

---

### Post by MadMan2k on 2009-10-04
kernel modesetting

---

### Post by RockDoctor on 2009-10-04
> **MadMan2k said:**
> kernel modesetting
Not being an expert in the use of KMS, how do I utilize KMS to set a particular VGA mode (in my case, I want 795)?

---

### Post by FuturePilot on 2009-10-04
Did you see this post? [http://ubuntuforums.org/showpost.php?p=8024427&postcount=17]("http://ubuntuforums.org/showpost.php?p=8024427&postcount=17")

---

### Post by lvlo on 2009-10-04
> **FuturePilot said:**
> Did you see this post? [http://ubuntuforums.org/showpost.php?p=8024427&postcount=17]("http://ubuntuforums.org/showpost.php?p=8024427&postcount=17")Good tip, but with this solution I have no TTY consoles...

---

### Post by dino99 on 2009-10-04
> **lvlo said:**
> Good tip, but with this solution I have no TTY consoles...

vga=xxx is deprecated, so need to remove it from boot line:

when you see the grub menu: highlight the boot line, press "e" to edit it, then wipe "vga=xxx" from your boot line  & press ctrl+x to boot

when boot is done, go to:

 /etc/default/grub

and add this if you dont have it

GRUB_CMDLINE_LINUX="gfxpayload=true"

remove vga=xxx

save & exit

---

### Post by lvlo on 2009-10-04
Thanks for this solution, **dino99**. Half of problem is gone now: I have Grub in 1024x768, but TTY consoles are still in 640x480 resolution... I did "sudo update-grub" after changes.

Here is my /etc/default/grub:

```
# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.

GRUB_DEFAULT=0
#GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=5
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX="gfxpayload=true"

# Uncomment to disable graphical terminal (grub-pc only)
#GRUB_TERMINAL=console

# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
GRUB_GFXMODE=1024x768

# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID=true

# Uncomment to disable generation of recovery mode menu entrys
#GRUB_DISABLE_LINUX_RECOVERY="true"
```

---

### Post by emarkay on 2009-10-04
> **RockDoctor said:**
> Not being an expert in the use of KMS, how do I utilize KMS to set a particular VGA mode (in my case, I want 795)?

Yes, FP, I saw that post - I even mentioned and referenced it!  But I think the above quote sums up my initial question!!

Is KMS the ONLY way, the RECOMMENDED way?  

If so, then have a link so I ca nlearn about it to "play" with VGA settings to see if I can finally boot Karmic?

Dino, 
GRUB_CMDLINE_LINUX="gfxpayload=true"
Is this for GRUB or GRUB2, and why doe we need to add it?  (and why is it not already there for something as basic as boot display modes)?

---

### Post by dino99 on 2009-10-04
> **emarkay said:**
> Yes, FP, I saw that post - I even mentioned and referenced it!  But I think the above quote sums up my initial question!!

Is KMS the ONLY way, the RECOMMENDED way?  

If so, then have a link so I ca nlearn about it to "play" with VGA settings to see if I can finally boot Karmic?

Dino, 
GRUB_CMDLINE_LINUX="gfxpayload=true"
Is this for GRUB or GRUB2, and why doe we need to add it?  (and why is it not already there for something as basic as boot display modes)?

grub2 is the default for karmic, on a fresh install grub (legacy) is gone, 
the gfxpayload is a workaround & we'll having a cleaner boot system when released in few weeks. :)

---

### Post by FuturePilot on 2009-10-04
> **emarkay said:**
> 
GRUB_CMDLINE_LINUX="gfxpayload=true"
Is this for GRUB or GRUB2, and why doe we need to add it?  (and why is it not already there for something as basic as boot display modes)?

gfxpayload is the replacement for vga=xxx. Have you tried to follow those instructions? I'm not sure if KMS is going to do what you want, but even if it is, it will only work if you have an Intel or ATI (I think ATI has KMS support in the OSS driver) graphics card.

---

