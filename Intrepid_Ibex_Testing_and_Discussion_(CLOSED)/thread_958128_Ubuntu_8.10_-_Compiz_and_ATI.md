---
title: "Ubuntu 8.10 - Compiz and ATI"
date: 2008-10-25
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by Radeky on 2008-10-25
So,

I just installed Ubuntu 8.10, and on this particular PC, I could not get 8.04 to run properly with my ati graphics card.

After a bit of searching on Compiz issues, it appears that my issue is slightly different from the rest and I thought I'd post it.

I can't get desktop effects enabled.
> 
When I run compiz --replace, I get this:
Checking for Xgl: not present. 
Detected PCI ID for VGA: 
Checking for texture_from_pixmap: not present. 
Trying again with indirect rendering:
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Comparing resolution (2560x1024) to maximum 3D texture size (2048): Failed.
aborting and using fallback: /usr/bin/metacity 


And it just hangs there and does nothing.
Hitting Ctrl+c forces me to log out and back in for me to be able to do anything.

I have not tried switching video drivers, because I'm not seeing any show up in the normal list of restricted video drivers and the last time(s) I did this with 8.04... I always ran into a black screen when trying to log in.  So, thoughts?  I'll do the video drivers, as long as someone also posts the process to go back to defaults.

---

### Post by Radeky on 2008-10-25
bump.

---

### Post by senseijose on 2008-10-25
):P try to install drivers using safe mode login and them reboot.

---

### Post by Radeky on 2008-10-25
Which drivers?  The propietary ATI ones?  That is a nasty hassle.

---

### Post by sdowney717 on 2008-10-25
try this first 
remove all entries from xorg.conf
(run an empty xorg.conf)

see if it boots.
if it boots, then it is using the standard ati (not fglrx) driver. 
So, if you make changes that give you that black screen, you know it is easy to get back to the free driver.

---

### Post by Kevbert on 2008-10-25
Have you tried using [[COLOR="Red"]compiz-check[/COLOR]]("http://forlong.blogage.de/entries/pages/Compiz-Check") ? It may give you additional information/help.

---

### Post by Radeky on 2008-10-25
I bet its using the standard ATI driver.  Dammit, I dont want to have to install the fglrx drivers.  They were a pain in the *** on 8.04.

I'll give it a shot, but my 'blank' xorg.conf is going to keep the info I have for my mouse, since it was having weird issues.

---

### Post by Radeky on 2008-10-25
> **Kevbert said:**
> Have you tried using [[COLOR="Red"]compiz-check[/COLOR]]("http://forlong.blogage.de/entries/pages/Compiz-Check") ? It may give you additional information/help.
Compiz-check wouldn't run.

---

### Post by sdowney717 on 2008-10-25
if there are no entries in xorg.conf, then xorg auto configures everything on every boot.

---

### Post by Radeky on 2008-10-25
> radek@khaos-ubuntu:~$ ./compiz-check

Gathering information about your system...

 Distribution:          Ubuntu 8.10
 Desktop environment:   GNOME
 Graphics chip:         ATI Technologies Inc R430 [Radeon X800 XL] (PCIe)
 Driver in use:         radeon
 Rendering method:      AIGLX

Checking if it's possible to run Compiz on your system...

 Checking for texture_from_pixmap...               [ OK ]
 Checking for non power of two support...          [ OK ]
 Checking for composite extension...               [ OK ]
 Checking for FBConfig...                          [ OK ]
 Checking for hardware/setup problems...           [FAIL]

There has been (at least) one error detected with your setup:
 Error: Your current resolution is too high to run Compiz. 

Would you like to know more? (Y/n) y

 Your resolution is 2560x1024 but the maximum 3D texture size that your
 graphics card is capable of is 2048x2048. Thus Compiz will not be able to run
 on this setup. You have to decrease the resolution first (in case you are
 using a dual-head setup, try disabling one monitor and run the script again).

So, the dual-head issue.  So, the idea is to set the computer to mirror, enable compiz and then switch back to dual?

Edit: Just noticed... it thinks my graphics card is PCIe.  Its most definitely AGP unless someone swapped the internals of my computer when I wasnt looking.

---

### Post by Kevbert on 2008-10-26
> **Radeky said:**
> I bet its using the standard ATI driver.  Dammit, I dont want to have to install the fglrx drivers.  They were a pain in the *** on 8.04.

I'll give it a shot, but my 'blank' xorg.conf is going to keep the info I have for my mouse, since it was having weird issues.

Looking in the compiz forums, it looks like that may be your best bet.

---

### Post by Radeky on 2008-10-27
So... got it to run!  whoo!

Then I got ATI Control Center to switch back to dual-head display...

and now compiz won't run again.

So, in Dual-head mode, it sets my resolution to 2560x1024, but it seems to think that my computer can only support a maximum of 2048x2048...

so my question is this: Can my ATI X850 XT handle 2560x1024 and Compiz?  Or is it really maxed at 2048x2048?  And if so, why does it allow me to run 2560x1024?

Because I REALLY want the desktop cube.  However, I'm not willing to sacrifice my 2nd monitor for it.

---

### Post by Longinus00 on 2008-10-27
2048x2048 is the maximum texture size for your card. Because you're desktop is larger than this, 2560x1024, you can't really use compiz. The newer video cards support 4096x4096 texture sizes if I'm not mistaken.

---

### Post by Radeky on 2008-10-27
Then why is it running "2560"x1024 just fine?

If it can support 2560 normally, whats the difference between now and compiz?

---

### Post by Radeky on 2008-10-27
XORG.CONF
> Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	DefaultDepth	24
EndSection

Section "Module"
	Load	"glx"
EndSection

Section "Device"
	Identifier	"Configured Video Device"
	Driver	"fglrx"
EndSection
fglrxinfo:
> ubuntu:~$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI RADEON X800 XL
OpenGL version string: 2.1.8087 Release

> -ubuntu:~$ ./compiz-check

Gathering information about your system...

 Distribution:          Ubuntu 8.10
 Desktop environment:   GNOME
 Graphics chip:         ATI Technologies Inc R430 [Radeon X800 XL] (PCIe)
 Driver in use:         fglrx
 Rendering method:      AIGLX

Checking if it's possible to run Compiz on your system...

 Checking for texture_from_pixmap...               [ OK ]
 Checking for non power of two support...          [ OK ]
 Checking for composite extension...               [ OK ]
 Checking for FBConfig...                          [ OK ]
 Checking for hardware/setup problems...           [FAIL]

There has been (at least) one error detected with your setup:
 Error: Your current resolution is too high to run Compiz. 

Would you like to know more? (Y/n) y

 Your resolution is 2560x1024 but the maximum 3D texture size that your
 graphics card is capable of is 2048x2048. Thus Compiz will not be able to run
 on this setup. You have to decrease the resolution first (in case you are
 using a dual-head setup, try disabling one monitor and run the script again). 


---

### Post by Vishal Agarwal on 2008-10-27
> **Radeky said:**
> So... got it to run!  whoo!

Then I got ATI Control Center to switch back to dual-head display...



What is this and where did u find it ? Pls mention the URL or some more details

---

### Post by Radeky on 2008-10-27
> **Vishal Agarwal said:**
> What is this and where did u find it ? Pls mention the URL or some more details
System > Admnistration > Synaptic Package Manager
Search: fglrx
select: xorg-driver-fglrx
Accept all
Install
Reboot

then:
Applications > Accessories > ATI Catalyst Control Center

---

### Post by Longinus00 on 2008-10-27
> **Radeky said:**
> Then why is it running "2560"x1024 just fine?

If it can support 2560 normally, whats the difference between now and compiz?

Because normally you aren't doing anything in 3d. Imagine compiz rendering your desktop as one big side of a cube. To have anthing appear on that cube you need to be able to texture it. If your desktop requires a higher resolution texture than your card can handle, it's not going to work. When you're not using compiz, there is no 3d data path so this limitation does not apply.

---

### Post by RAOF on 2008-10-27
> **Radeky said:**
> Then why is it running "2560"x1024 just fine?

If it can support 2560 normally, whats the difference between now and compiz?

In particular, you're not *normally* trying to render a 2560x1024 texture.  The desktop is a single window, and Compiz makes that a single texture, which your card/driver combination doesn't handle.

It's technically possible for compiz to render this as two textures, which would get around this problem.  I'm not sure where work is on that patchset, which required some core changes.

---

### Post by Radeky on 2008-10-27
Thanks guys.

RAOF,  who do I talk to, to see the progress on that?  Because, that would be awesome.

So, I guess my only option is to reduce the resolution to 1024x768 on both, and then enable Compiz?

---

### Post by Brickedin21 on 2008-10-28
ROAF, is there any progress as to why with my ATI card on my laptop is not giving any display at all? the prompt  using control alt f1 works, but i have nothing other than that, it boots fine and everything.

---

