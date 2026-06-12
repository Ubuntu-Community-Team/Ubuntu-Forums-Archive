---
title: "Weird Problem"
date: 2010-12-31
forum: Installation &amp; Upgrades
---

### Post by Metasyn on 2010-12-31
While trying to re-install win xp 64 bit over 32 bit. Windows took over the Grub boot loader and was only booting into windows not Ubuntu. While trying to use [http://apcmag.com/how_to_dual_boot_linux_and_windows_xp_linux_installed_first.htm?page=5](http://apcmag.com/how_to_dual_boot_linux_and_windows_xp_linux_installed_first.htm?page=5)

I got an error on the second step "setup (hd0,0)" that said "error 17: can't mount selected partition"

After looking into my Menu.lst file I found that ubuntu was (hd0,6) after trying again this time with setup (hd0,6) I got the exact same error. What should i do to fix this?

---

### Post by presence1960 on 2010-12-31
Let's get a better look at your setup & boot process. Boot the Ubuntu Live CD/USB. Choose "try ubuntu without any changes", when the desktop loads come back here and do the following:

1. Download the boot info script. There is a link in my signature.
2. Once downloaded move the boot info script to the desktop.
3. Open a terminal and run the command ```
sudo bash ~/Desktop/boot_info_script*.sh
```

  This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text. 

See [here]("http://bootinfoscript.sourceforge.net/") for more info on the boot info script.

---

### Post by coffeecat on 2010-12-31
> **Metasyn said:**
> While trying to use [http://apcmag.com/how_to_dual_boot_linux_and_windows_xp_linux_installed_first.htm?page=5](http://apcmag.com/how_to_dual_boot_linux_and_windows_xp_linux_installed_first.htm?page=5)

That's a poor guide. It has Ubuntu on partition 1 and Windows on partition 2 which is an unusual way of doing things and nowhere (that I can see) does it tell you how to adjust the commands for your particular partition layout.

> **Metasyn said:**
>  I got an error on the second step "setup (hd0,0)" that said "error 17: can't mount selected partition"

Look at the guide again. This is one bit it gets right. It's...

```
setup (hd0)
```...not...

```
setup (hd0,0)
```> **Metasyn said:**
>  After looking into my Menu.lst file I found that ubuntu was (hd0,6) after trying again this time with setup (hd0,6) I got the exact same error. What should i do to fix this?

If you are absolutely, 101% sure that your Ubuntu root partition is on (hd0,6) (=sda7) and that you are running a version of Ubuntu prior to 9.10, then the sequence of commands from a live CD terminal is:

```
sudo grub
root (hd0,6)
setup (hd0)
quit
exit
```Just to be clear - (hd0), **not** (hd0,0) in the setup line.

If you are not sure or that doesn't work, from the live CD go to:

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

Download and run the boot info script and post the RESULTS.txt file in cide tags as described in that link for clarity.

---

### Post by presence1960 on 2010-12-31
> **coffeecat said:**
> That's a poor guide. _***It has Ubuntu on partition 1 and Windows on partition 2 which is an unusual way of doing things***_ and nowhere (that I can see) does it tell you how to adjust the commands for your particular partition layout.


That's because the guide is for installing windows after ubuntu.

---

### Post by coffeecat on 2010-12-31
> **presence1960 said:**
> That's because the guide is for installing windows after ubuntu.

Very true. Perhaps 'poor' was harsh, but with a bit of forethought the authors could have included the OP's re-installation scenario. It's a shame because the illustrations are good and very clear.

---

### Post by presence1960 on 2010-12-31
> **coffeecat said:**
> Very true. But with a bit of forethought the authors could have included the OP's re-installation scenario. It's a shame because the illustrations are good and very clear.

I hear you. That is why for the most part I stick with ubuntu community derived documentation.

---

