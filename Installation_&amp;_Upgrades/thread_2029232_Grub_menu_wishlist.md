---
title: "Grub menu wishlist"
date: 2012-07-19
forum: Installation &amp; Upgrades
---

### Post by jpeg729 on 2012-07-19
I like having several installations all at once. One for work with an encrypted home. One running UbuntuStudio for music studio work. One running another installation of UbuntuStudio for trying out cutting edge software versions ... you get the picture. Add in a Kubuntu or an Xubuntu.

But the grub menu is a horrible mess. Lots of "Ubuntu 12.04 (on /dev/sda?)" How should I know which is which?

Why should Kubuntu appear as "Ubuntu"? Wouldn't it be better if it didn't have an identity crisis?

Can't we find a way of tidying things up a bit?

---

### Post by bogan on 2012-07-19
Hi!, **jpeg729,**

Install Grub Customizer and you can do all that and more.

Edit the name that appears in the grub menu and then boot to it to find out which it is.

Then give it the exact name you want it to have, and hide the ones you don't want to show.

A bit long-winded and there more sophisticated ways.

To Install Grub Customizer:```
sudo add-apt-repository ppa:danielrichter2007/grub-customizer 
sudo apt-get update 
sudo apt-get install grub-customizer
```Chao!, **bogan.**

---

### Post by jpeg729 on 2012-07-20
Thankyou. That is a start, but I don't want to install something extra. I would prefer to make things better for everyone.

Anyone else have any ideas or wishes? Am I the only one who cares?

---

### Post by bogan on 2012-07-20
Hi!,** jpeg729,**

OK, if you do not want to add a program specifically designed to do what you are asking for, and which does make everything better for all who use it:

Just keep a list of the partitions and what they are, what they do and what you use them for.

EG: 
sda1  Windows
sda2 10.04 Ubuntu Studio Testing So0ftware
sda3 Extended
sda4 12.04 Ubu8ntu Studio  Music
sda5  12.04 Kubuntu
etc
etc

Chao!,** bogan.**

---

### Post by oldfred on 2012-07-20
Before grub customizer we did it all manually. drs305 has instructions and these links:

How to: Create a Customized GRUB2 Screen that is Maintenance Free.- Cavsfan
[http://ubuntuforums.org/showthread.php?t=1542338](http://ubuntuforums.org/showthread.php?t=1542338)

The Grub 2 Guide (formerly Grub 2 Basics) manual way
[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)

[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Custom_Menu](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Custom_Menu)

OR Partial Custom menu:
I turned off os-prober so it does not look for other systems and totally customized my 40_custom.
includes  to limit display to two, also hiding of windows recovery partition
Grub 2 Title Tweaks Thread -drs305
[http://ubuntuforums.org/showthread.php?t=1287602](http://ubuntuforums.org/showthread.php?t=1287602)
In /etc/default/grub I added this:
gksudo gedit /etc/default/grub
GRUB_DISABLE_OS_PROBER=true
or
sudo chmod a-x /etc/grub.d/30_os-prober

---

### Post by jpeg729 on 2012-08-31
Manual solutions are for geeks. grub-customizer is great but it will only be used by lazy geeks. What about newbies? Wouldn't it be better if the default menu was intuitive and clean and just worked even when the kernel gets updated or another OS installed?

**One idea:** edit /etc/lsb-release
On every version of Ubuntu 12.04 it reads exactly the same.

DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=12.04
DISTRIB_CODENAME=precise
DISTRIB_DESCRIPTION="Ubuntu 12.04 LTS"

Change the description line to "Kubuntu 12.04 LTS" or "Gaming ubuntu" on each linux and your grub menu suddenly gets a lot clearer. **Why doesn't Kubuntu call itself Kubuntu for crying out loud?** The description is just a description I suppose, the important details are in the other lines.

**Second idea:** Grub2 can load up other configfiles using the "configfile" command.
It would be easy to edit /etc/grub.d/30_os-prober to make it load other linuxes configfiles instead of listing their kernels. **I've done it if it interests anyone.**

**Third idea:** self_boot.cfg
Each linux install should have a self_boot.cfg file that just indicates the current and past kernels and the recovery options (if desired). The ruling grub install should have a general configfile that pulls all those in using grub2's configfile command. **Besides, if there already is one linux installed with grub2, why insist on installing it again as the current linux installers all do?**

---

### Post by oldfred on 2012-08-31
The underlying kernel has no idea what desktop you are using if any. All the Ubuntu's are using the same kernel so you will have the same info.

fred@fred-Precise:~$ echo $DESKTOP_SESSION
gnome-fallback

Debian installs all do put a link to the most current kernel, so you can have just one entry in grub to boot the most current kernel in another install. See Cavsfan's instructions in link above.

Most new users are not booting multiple installs. But you can add your comments to the wishlist 

Does not look like this is too current:
[https://wiki.ubuntu.com/Ubuntu/Wishlist](https://wiki.ubuntu.com/Ubuntu/Wishlist)

[https://bugs.launchpad.net/ubuntu/+source/grub2](https://bugs.launchpad.net/ubuntu/+source/grub2)

---

