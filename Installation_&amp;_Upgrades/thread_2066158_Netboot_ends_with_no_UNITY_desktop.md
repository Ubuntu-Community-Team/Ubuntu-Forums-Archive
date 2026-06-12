---
title: "Netboot ends with no UNITY desktop"
date: 2012-10-03
forum: Installation &amp; Upgrades
---

### Post by BanderSnoot on 2012-10-03
Hi folks,

I have some experience with Ubuntu and 12.04, so far mostly successful.

Installed using the mini.iso netboot and everything seemed to go well.. except that I have no Unity GUI.   Just command line.

I am hoping there is an app get or such that will get me out of this hole.  It feels like 1987.

Thanks for any and all assistance.

---

### Post by jerrrys on 2012-10-03
Yes, lets do this :)  Where do you want to go from here?  Full blown desktop?  Or maybe less?

Edit: how much ram do you have?  What kind of processor?

---

### Post by Wim Sturkenboom on 2012-10-04
You're title refers to lubuntu; I however did not see a mini.iso on the lubuntu website?

Am I blind or can you clarify?

---

### Post by jerrrys on 2012-10-04
> **Wim Sturkenboom said:**
> You're title refers to lubuntu; I however did not see a mini.iso on the lubuntu website?

Am I blind or can you clarify?

Here's the [website]("https://help.ubuntu.com/community/Installation/MinimalCD")

Lubuntu; Unity; whatever the OP wants to build  :)

---

### Post by raja.genupula on 2012-10-04
> **BanderSnoot said:**
> Hi folks,

I have some experience with Ubuntu and 12.04, so far mostly successful.

Installed using the mini.iso netboot and everything seemed to go well.. except that I have no Unity GUI.   Just command line.

I am hoping there is an app get or such that will get me out of this hole.  It feels like 1987.

Thanks for any and all assistance.

Hi Jerry

@OP you should have to explain what you have done after mini.iso installation . 

if you want to get GUI that too Unity then you have to install it .

open your terminal and type this 

```
sudo apt-get install ubuntu-desktop
```

Then it will give the GUI . 

if still no GUI then there is something to do with your VGA drivers .

so let us know what you got .

---

### Post by jerrrys on 2012-10-04
Or maybe less:

sudo apt-get install --no-install-recommends ubuntu-desktop

That command will install all the necessary packages (red) for a working Unity desktop, but none (green) of the recommend packages.  The full install being 600+MB and the no-recommend being 160MB download.

[http://packages.ubuntu.com/precise/ubuntu-desktop](http://packages.ubuntu.com/precise/ubuntu-desktop)

Hay raja, how ya doing  :)

---

### Post by raja.genupula on 2012-10-04
> **jerrrys said:**
> Or maybe less:

sudo apt-get install --no-install-recommends ubuntu-desktop

That command will install all the necessary packages (red) for a working Unity desktop, but none (green) of the recommend packages.  The full install being 600+MB and the no-recommend being 160MB download.

[http://packages.ubuntu.com/precise/ubuntu-desktop](http://packages.ubuntu.com/precise/ubuntu-desktop)

Hay raja, how ya doing  :)

Hi Jerry , great man .

yes I'd have to suggest this also . because my post will gives all Ubuntu-desktop packages like  all stuff . but Jerry post just give GUI of ubuntu-desktop i.e unity .

---

