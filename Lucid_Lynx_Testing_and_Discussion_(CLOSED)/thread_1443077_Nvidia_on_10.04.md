---
title: "Nvidia on 10.04"
date: 2010-03-30
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by jeggen on 2010-03-30
I am enjoying 10.04 and have to admit I have a hard time when I need to boot to Windows.  One thing I have struggled with is controlling screen brightness on my laptop.  I have an Nvidia 
Quadro FX 570M.  I know that the Nvidia has a different kind of brightness control.  From what I can tell, I need to use the smartdimmer program, which I have installed and works.  Is there any way to bridge this with the Gnome system (e.g. power control options, keyboard dim/bright shortcuts, panel brightness control)?  It seems like this shouldn't be too much of a stretch... Nvidia cards are pretty prevalent these days.  Is this one of the things that is supposed to be fixed with switching to the Nouveau driver?  Currently I am using the current NVidia driver (although it displays as active but not currently in use - see [https://bugs.launchpad.net/ubuntu/+source/jockey/+bug/539997](https://bugs.launchpad.net/ubuntu/+source/jockey/+bug/539997))

I have tried to use the nouveau driver but when I switch the driver in xorg.conf (as below) but on boot it says it doesn't work and that I have to use a basic mode.  I would appreciate any help in figuring out what is a "papercut" to me.

```
Section "Device"
	Identifier	"Default Device"
	Driver	"nouveau"
	Option	"NoLogo"	"True"
EndSection
```

---

### Post by Mark Phelps on 2010-04-01
10.04 is still in beta testing, so posts regarding 10.04 need to be put in the proper forum: Development & Programming, Lucid Lynx Testing.

I will be asking the Mods to move this thread there.  Look there for any future responses.

---

### Post by jeggen on 2010-04-01
Thanks for the clarification.  I will post future questions in the testing forum.

---

