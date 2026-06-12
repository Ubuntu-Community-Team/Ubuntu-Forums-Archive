---
title: "Grub2"
date: 2011-04-11
forum: Installation &amp; Upgrades
---

### Post by exsencon on 2011-04-11
I wish somebody could explain to me the advantages of Grub2 over Grub1 or legacy as it is called today.
I have two systems.
Dell Dimension 520 2*250GBHDD, 4GBRAM,P4,Nvidia Graphics
Multiboot system with winXP and 10 Linuxes (Ubuntu,Kubuntu,Slackware,Sabayon,Fedora,Mepis,Mint,PClinux,Suse,Debian) and Opensolaris and PCBSD all booting from Ubuntu's Grub1 installed in the MBR. Everything working fine.

Dell Inspiron 1501 Laptop 120GB HDD, 2GBRAM, ATI Graphics with WinXP, Ubuntu,Suse,Dreamlinux and Slax.Again everything booting from Ubuntu's Grub1
Here I decided to upgrade my Ubuntu 9.04 to 10.10. Couldn't do it over the internet (he made a complete mess out of it) so I wiped out the old Ubuntu root partition and installed from live CD (keeping my home partition) It went quite well but with the brand new Grub2 bootloader he couldn't find my other OS except for WinXP (of course).
Since I have a Grub1 boot CD I thought it would be quite easy to fix,but not so. Grub1 boot CD couldn't do anything about Grub2.
So after a lot of retrials and rebooting and frankly ---- I went into the
/boot/grub/grub.cfg file configured everything like it should be in an old menu.lst file and everything worked again as it should.
Now I know that you shouldn't edit that grub.cfg file(why not) but that was the only way I got my multiboot system working again.

Frankly, I don't understand why Grub2 makes things that complicated while Grub1 had it all that simple.Makes me look back to Lilo again.

---

### Post by idoitprone on 2011-04-11
You dont configure grub.cfg directly, since it always rewritten when you update grub ex kernel update. What you want to to configure is /etc/grub.d/40_custom. You have to make minor revision to, since drive numbering scheme changed a little.

[https://help.ubuntu.com/community/Grub2#GRUB%20vs%20GRUB%202]("https://help.ubuntu.com/community/Grub2#GRUB%20vs%20GRUB%202")

There are technical reasons why grub 1 is going to be phased out. I only understand some of it such as gpt partition table support and programming is easier with grub2.


[http://mailman.archlinux.org/pipermail/arch-releng/2011-March/001610.html](http://mailman.archlinux.org/pipermail/arch-releng/2011-March/001610.html)

---

### Post by oldfred on 2011-04-11
You must move your custom entries to 40_custom as idoitprone commented.

More info on customization. I used to chainboot to my other installs, but once I learned grub2, it just finds all the other installs. But I still copy most of the entries and some customized into 40_custom and turn off the os-prober.

Total Custom menu:
[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Custom_Menu](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Custom_Menu)
[http://ubuntuforums.org/showthread.php?t=1483827](http://ubuntuforums.org/showthread.php?t=1483827)

Link with several of links below:
How to edit bootloader? Feb 2011
[http://ubuntuforums.org/showthread.php?t=1694681](http://ubuntuforums.org/showthread.php?t=1694681)

HOWTO: Grub Customizer 
[http://ubuntuforums.org/showthread.php?t=1664134](http://ubuntuforums.org/showthread.php?t=1664134)
A easy way to remove the amount of kernels is to install Ubuntu tweak:
[http://ubuntu-tweak.com/](http://ubuntu-tweak.com/)

How to: Create a Customized GRUB2 Screen that is Maintenance Free.
[http://ubuntuforums.org/showthread.php?t=1542338](http://ubuntuforums.org/showthread.php?t=1542338)

OR Partial Custom menu:
I used drs305's command to limit ubuntu entries to two, turned off os-prober so it does not look for other systems and totally customized my 40_custom.
includes line to limit display to two, also hiding of windows recovery partition
Grub 2 Title Tweaks Thread -drs305
[http://ubuntuforums.org/showthread.php?t=1287602](http://ubuntuforums.org/showthread.php?t=1287602)
In /etc/default/grub I added this:
gksudo gedit /etc/default/grub
GRUB_DISABLE_OS_PROBER=true
or
sudo chmod a-x /etc/grub.d/30_os-prober

One way to fix the descriptions is to move the windows entries to 40_custom and edit at will.

Copy the other boot entries from this:
gedit /boot/grub/grub.cfg
Copy them to and edit only titles:
gksudo gedit /etc/grub.d/40_custom
Then do:
sudo update-grub

---

### Post by exsencon on 2011-04-11
Yes, Oldfred I read all that but still,admit Grub1 is a lot easier to handle and that even if you're used to Grub2. I just don't understand why they made a beautiful simple system so complicated. Instead of just one file we now have at least three. So much for simplicity.Even gpt partitioning goes well under 2TB. Now who goes beyond 2TB?
I really think this is not the right way to go for Linux. It's not because we Linux people can live with it,I just think about non linux people maybe wanting to try a Linux distro. If they see Grub2 they'll run away.

---

### Post by idoitprone on 2011-04-12
> **exsencon said:**
> Yes, Oldfred I read all that but still,admit Grub1 is a lot easier to handle and that even if you're used to Grub2. I just don't understand why they made a beautiful simple system so complicated. Instead of just one file we now have at least three. So much for simplicity.Even gpt partitioning goes well under 2TB. Now who goes beyond 2TB?
I really think this is not the right way to go for Linux. It's not because we Linux people can live with it,I just think about non linux people maybe wanting to try a Linux distro. If they see Grub2 they'll run away.

ummm, did ever consider a server? Maybe a server wants to boot on more than 2tb hdd or want more than 4 primary partitions? Linux distro cater to the server market and serve their need, since it pays the bills. Just learn how to deal with grub2 and it actually nice, since everything practically automated and no more searching the internet just to write each entry

---

### Post by oldfred on 2011-04-12
When I first started posting here, it was almost always a boot stanza for windows or fixing the boot stanza for windows. Or trying to train users that the boot stanza did not go into the auto area. Or that they could edit parameters in the first part of menu.lst. Yes each is now a separate area, but it prevents wrong entries and the os-prober alone is worth it for grub2 if you have more than one system for most new dual booters.

---

### Post by exsencon on 2011-04-12
> **idoitprone said:**
> ummm, did ever consider a server? Maybe a server wants to boot on more than 2tb hdd or want more than 4 primary partitions? Linux distro cater to the server market and serve their need, since it pays the bills. Just learn how to deal with grub2 and it actually nice, since everything practically automated and no more searching the internet just to write each entry

I fully understand Linux caters to the server market and rightly so.But I still maintain Grub2 makes it a lot more complicated than it was with Grub1 for the average user.Having said that,I think I can manage my multiboots with any Grub or Lilo,it just takes a little more tweaking and I am a lazy person!Thanks for your comments.

---

