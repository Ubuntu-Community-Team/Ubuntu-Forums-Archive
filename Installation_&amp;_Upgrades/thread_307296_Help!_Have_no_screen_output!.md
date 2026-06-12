---
title: "Help! Have no screen output!"
date: 2006-11-26
forum: Installation &amp; Upgrades
---

### Post by AD-RS1600i on 2006-11-26
Hi all,

I've just brought a pci Radeon 9250 to go into my old pc I am using for Ubuntu, so impressed i've been with this operating system :) 

Unfortunately this machine is running an internal graphics card, which is confusing the Ubuntu installation program so it simply displays nothing on either the onboard AGP or the PCI graphics card ](*,)  I can disable the PCI card in the bios and everything will install ok, but once installed it won't display anything now even if I've got the PCI card disable in the bios, no screen will display on Ubuntu as soon as it boots up to the log on screen effectively...

I tried to change the card Gnome uses by using this utility at the command prompt in recovery mode

dpkg-reconfigure xserver-xorg

problem being I can specify the card type, i.e. ATI but I have no idea what the BusID is or how to find it....

Has anyone got any ideas? I'm sure others with a system with on board graphics must have come across something similar when they upgraded.....

Thanks in advanced

Adrian

---

### Post by taurus on 2006-11-26
If you don't know what the answer is when running "dpkg-reconfigure xserver-xorg", just hit enter or use the default value...  Otherwise, run it with "-phigh" option.

```
dpkg-reconfigure -phigh xserver-xorg
```

---

### Post by AD-RS1600i on 2006-11-27
I'm really confused... I thought this would be tricky but not this tricky, unfornately the defaults in the dpkg-reconfigure -app point to the original Intel onboard GFX card. I can point it towards my PCI ATi card but I don't know what the PCI BusID is for it... 

Now the thing won't boot either way, with the ATI PCI card in or without....

Thanks for your input have you any other ideas?:KS

---

### Post by taurus on 2006-11-27
Can you boot your machine with the LiveCD with working Gnome at all?  Also, make sure you go into the BIOS and disable the onboard video card!!!

---

### Post by AD-RS1600i on 2006-11-27
I'm not a total novice, I know my stuff with the exception of anything to do with Linux.....

That's the thing, in all honesty I can probably find a way of getting it to boot again into Unbuntu, I just need a way of working out what the busID is for the PCI GFX card then a way of specifying to Unbuntu to use the PCI one not the onboard one but a the command prompt as there isn't a windows like 'safe mode' with limited GFXs...

Struggling at the moment.

---

### Post by taurus on 2006-11-27
What's why I was asking to see if you can boot your machine with the LiveCD!  Then, you can look it up with it...

---

### Post by AD-RS1600i on 2006-11-27
Oh right! I used to be able too but it's got it's knickers in a twist and won't do it now when I disable the ATi card. Urm. I will have a quick play now, assuming I can get it to work, how do i find this info within Ubuntu?

Thanks for your help

---

### Post by taurus on 2006-11-27
Either look in /etc/X11/xorg.conf or lspci!

Applications -> Accessories -> Terminal
```
lspci
cat /etc/X11/xorg.conf
```

---

### Post by AD-RS1600i on 2006-12-03
I had left this a while because I was getting frustrated with it.](*,) 

From what I've gleaned so far, I used the dpkg-reconfigure -phigh xserver-xorg utility to specify what graphics card to use as a default. My problem now is understanding how to tell Linux what Bus the card is using

For example according to xorg.conf my current graphics card (the on board I no longer want to use) is

Identifier "Intel corp...."
Driver "i810"
BusID "PCI:0:1:0"

Now to me it seems fairly logical to change it to the ati, simply tell the system via dpkg-reconfigure -phigh xserver-xorg to use the ATI on BusID.... The problem is I dont know how to find the bus ID. If I use LSPCI it displays everything but in a format which is not compatible with the way the XORG.Conf file is laid out eg. (i'm assuming this is why it doesn't work....)

The same onboard intel GFX card according to LSPCI (-b) 00:01.0 which isn't the same format as PCI:0:1:0

So my ATI card according to LSPCI is 01:0f.0 so how would you put this in the dpkg-reconfigure -phigh xserver-xorg format?

Thanks in advanced......blimey! how difficult!!

---

### Post by taurus on 2006-12-03
Boot from the LiveCD, mount the partition where / is, then copy /etc/X11/xorg.conf from the LiveCD to /etc/X11/xorg.conf on the harddrive!!!

---

