---
title: "Can't get grub splash screen to show"
date: 2011-12-07
forum: Installation &amp; Upgrades
---

### Post by Goldpin on 2011-12-07
I've just upgraded to Ubuntu 11.10.  While I was using Lucid, I had a customized grub screen.  However, I can't get the same thing in 11.10.  I've installed the grub customizer, and it will show a grub splash in the "appearance" tab, but not when the computer boots.
Does anyone have any idea what the problem might be?

---

### Post by fantab on 2011-12-07
> **Goldpin said:**
> I've just upgraded to Ubuntu 11.10.  While I was using Lucid, I had a customized grub screen.  However, I can't get the same thing in 11.10.  I've installed the grub customizer, and it will show a grub splash in the "appearance" tab, but not when the computer boots.
Does anyone have any idea what the problem might be?

From Terminal run 

```
sudo gedit /etc/default/grub
```

and find this line: 
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"

if the "quiet splash" is missing then add to the line and save the file, it its already there then just ignore this step and do following in either case.

```
sudo update-grub
```

---

### Post by Goldpin on 2011-12-07
> **fantab said:**
> From Terminal run 

```
sudo gedit /etc/default/grub
```

and find this line: 
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"

if the "quiet splash" is missing then add to the line and save the file, it its already there then just ignore this step and do following in either case.

```
sudo update-grub
```

The command line shows "quiet splash".  I also ran update-grub and it shows a second kernel in the options, but the grub screen that comes up at boot doesn't.  Also, the second kernel has -pae at the end.  Does anyone know what this is????

---

### Post by Goldpin on 2011-12-08
Changed the type of splash screen and it appeared.  Found that the previous kernels can be accessed by pressing 'enter' on the 'previous operating systems'option

---

