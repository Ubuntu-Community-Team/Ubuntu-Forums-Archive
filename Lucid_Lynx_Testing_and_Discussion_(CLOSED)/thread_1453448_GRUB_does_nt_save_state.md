---
title: "GRUB does nt save state"
date: 2010-04-13
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by juanJosepablos on 2010-04-13
Hi,
a few weeks back I was able to:
modify /etc/default/grub
GRUB_DEFAULT=saved

and then update-grub and the last state was saved on the grub menu.
I am not longer able to do so... Can anyone seeing this?

Cheers,

---

### Post by ubername on 2010-04-13
> **juanJosepablos said:**
> Hi,
a few weeks basck I was able to:
modify /etc/default/grub
GRUB_DEFAULT=saved

and then update-grub and the last state was saved on the grub menu.
I am not longer able to do so... Can anyone seening this?

Cheers,

You need 

GRUB_DEFAULT=saved
[COLOR="Red"]GRUB_SAVEDEFAULT=true[/COLOR]

added to /etc/default/grub, or at least that worked for me.

---

### Post by ronparent on 2010-04-13
Thank you both so much. The machine I am currently installed on (not the one below - that will be the hard nut) will not run without the noapic nolapic added to the boot command line and splash removed. I don't clearly understand the GRUB_DEFAULT issue but I added it anyway. I also added my changes above to the command line and it now boots correctly! I am now ready (I think) to move the drive to my problem machne below and to tinker with getting it to run. 

I might add that I have been reading the grub2 documentation and got no clue on what I had to do to configure it to enable 10.04 to boot on my machine. At least I now have one additional tool with which to tinker with it.

---

### Post by juanJosepablos on 2010-04-13
Strange looking  on the /etc/grub.d/00_header seems like saved is the rigth parameter. I have try both and still fails. Is your system up-to-date?

---

### Post by juanJosepablos on 2010-04-13
I was right. Looking onthe documentation:
[https://wiki.ubuntu.com/Grub2](https://wiki.ubuntu.com/Grub2) Either a number or saved

---

### Post by juanJosepablos on 2010-04-13
ubername,
could you post your /boot/grub/grub.cfg? I am not able to see the saved parameter on the menu entries.

---

### Post by ubername on 2010-04-13
You need both entries.

This is my /etc/default/grub:

```

# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.

GRUB_DEFAULT=saved
GRUB_SAVEDEFAULT=true
#GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT="6"
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT=""
GRUB_CMDLINE_LINUX="ipv6.disable=1 splash"

# Uncomment to disable graphical terminal (grub-pc only)
#GRUB_TERMINAL=console

# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
GRUB_GFXMODE=1280x1024

# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID=true

# Uncomment to disable generation of recovery mode menu entries
#GRUB_DISABLE_LINUX_RECOVERY="true"

# Uncomment to get a beep at grub start
#GRUB_INIT_TUNE="480 440 1"
```

---

### Post by juanJosepablos on 2010-04-13
yes,
That works!, I think that GRUB_SAVEDEFAULT should be added as hint on the /etc/default/grub entry. Do you think that this is a bug?

---

### Post by ubername on 2010-04-13
[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275) 

Was where I started from so credit to DRS305. It's not really a bug IMO. I guess this is where these forums come into their own.

---

### Post by juanJosepablos on 2010-04-13
But I am sure that I was able to config grub with lucid before, so I guess that removing the GRUB_SAVEDEFAULT entry from the grub file is a bug. On 8.04 you have to edit on /boot/grub/menu.lst

---

