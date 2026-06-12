---
title: "How to clone the newly installed O/S to use for re-install or 2nd computer"
date: 2014-01-04
forum: Installation &amp; Upgrades
---

### Post by Odyssey1942 on 2014-01-04
Hi all,

When you install or upgrade Ubuntu, there is a "running in" period when you add familiar software, tweak software, and generally (re-)configure your computer the way you like it.

Once you have it back the way you like it, and it is still "fresh", is there a way to create a self-installing "copy" that will not only restore the tweaked system to the computer from which the copy was made, but can self-install on another computer? And what is the name for this, if any?

---

### Post by ibjsb4 on 2014-01-05
I use Clonezilla for cloning an HDD to HDD or just clone partitions.  Its not meant to be used as an installer, but it will also do that.  I have cloned a system to another machine(s) and Ubuntu has auto adjusted to new equipment specifications.

[http://clonezilla.org/](http://clonezilla.org/)

Usless things have changed, multi disk cloning is not supported.  Gots to fit one one disk.

---

### Post by varunendra on 2014-01-05
I usually prefer Remastersys because it creates a Live DVD iso (can be used to create Live USB) which I can use as a Live disk with all my programs. However, installing from it carries only the programs, not any customizations, and the installation process is same as a fresh installation (you choose a partition, select size, etc...).

For a fully automated 'Self-Installer', Clonezilla is a very good alternative, if not the best. Here's how you create a self installing copy from it -

[indent]**1)** Boot clonezilla > choose a destination partition to save the 'Image' of your Ubuntu partition > choose the source partition (Ubuntu) to image > save the image.

**2)** After the image is saved, choose to re-run clonezilla > choose the same destination partition again > this time it will give you 3 additional options - 1. Create Restore ISO, 2. Create Restore .zip for USB, 3. Create both ISO and .zip

**3)** If the image size is less than 4.7 GB (so that it can fit on a single DVD), choose the 3rd option (create both ISO and .zip). If it is larger, choose to create just the .zip archive.

**4)** Carefully choose the options for restoring the image (these settings will be applied when restoring the image). Make sure to select the -k (or -p, I don't remember correctly) option that is meant to **'Keep' the current partition table** while restoring the image. [COLOR="#FF0000"]Choosing the default option (or any other option) at this stage **will remove the existing partitions and all the data on them** while restoring (thus simulating a 'Factory Defaults')[/COLOR].

**5)** After the Restore Image creation is finished, reboot to Ubuntu (or windows) > burn the ISO to a DVD and keep it as a self installer DVD. Keep the .zip file handy on an external drive or immediately create a restore USB with it. Creating a Live USB with the .zip requires just extracting its contents to the USB drive, then run a booinstall.sh (or something similar, can't remember right now) script on it to install the boot-loader on the USB.[/indent]

Later, you can boot from this 'Restore' DVD/USB and it will autostart clonezilla in restore mode (you'll be given 10 seconds to choose to run it in normal mode from its boot menu). The only question it will ask is whether to start the restoration or cancel it (you'll have to answer "**Y**" to proceed). Once started, it can't be aborted without risking loss, just like any other 'Auto-Restore' program.

Hope it is what you wanted.

---

### Post by Odyssey1942 on 2014-01-06
Thanks to both, and especially to varunendra for the step by step. 

Looks perfect.

---

### Post by varunendra on 2014-01-06
No problem, and sorry for those "I don't remember correctly" parts in-between.. I hope they would be obvious choices when you'd actually be doing it. :)

---

