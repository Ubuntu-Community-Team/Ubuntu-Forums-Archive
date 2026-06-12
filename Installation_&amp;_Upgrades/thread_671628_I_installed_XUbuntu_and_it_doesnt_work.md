---
title: "I installed XUbuntu and it doesnt work"
date: 2008-01-18
forum: Installation &amp; Upgrades
---

### Post by dr3n on 2008-01-18
I just installed XUbuntu with the alternate CD after the normal one didn't work now i've got it installed and after the boot screen it goes blank and doesnt do anything ive had this problem with linux before on other versions and I don't know what causes it some people have talked about nvidea video cards messing with it i have onboard nvidea graphics so i dont know what the problem is please help :\

---

### Post by zvacet on 2008-01-19
Ctrl+Alt+F2

```
sudo dpkg-reconfigure xserver-xorg
```

When it comes to drivers select **vesa** and proceed with reconfiguring.When it is finish restart and you will have basic graphic.Then you go for your video driver.

---

### Post by dr3n on 2008-01-20
Does it have to boot to do that? because when I press Ctrl+Alt+F2 text flashes by really fast with [OK] at the end and I can't type anything in that...

---

### Post by zvacet on 2008-01-20
When you start select recovery mode from grub menu and 

```
dpkg-reconfigure xserver-xorg
```

---

### Post by dr3n on 2008-01-20
OK, I'll try that and post back the results

---

### Post by sochbat on 2008-01-20
> **dr3n said:**
> OK, I'll try that and post back the results

So i'm in the same boat as dr3n.

I freshly installed Xubuntu via NetBoot, and it completed itself and all.

But when i restart it, there isn't any GUI.

I logging in, and typed the command 'sudo ....xorg" and i get this prompt.

Package 'xserver-xorg' is not installed and no info is availible.

Do you know the command to install X?

---

### Post by sochbat on 2008-01-20
So i just tried the command "sudo apt-get install xserver-xorg' but it gives me this prompt.

"Unable to fetch some archives, maybe run apt-get update or try with --fix-missing"

Any help?

---

### Post by dr3n on 2008-01-21
Ok, I done what you said and I got nothing out of selecting my drivers I done all of what it asked restarted and still the same problem

---

### Post by zvacet on 2008-01-21
Synaptic>preferences>repositories>chek all boxes under Ubuntu software and under updates tab.Reload.

```
sudo apt-get install xserver-xorg
```

---

### Post by dr3n on 2008-01-21
Ok, it works now I overlooked the 'startx' bit

---

