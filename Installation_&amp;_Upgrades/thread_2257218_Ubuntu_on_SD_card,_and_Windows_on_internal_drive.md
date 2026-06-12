---
title: "Ubuntu on SD card, and Windows on internal drive"
date: 2014-12-17
forum: Installation &amp; Upgrades
---

### Post by RichieB07 on 2014-12-17
I'm looking into buying a HP Stream 13 as a more travel friendly computer, but since it only has 32GB of flash storage, I don't want to use all that up with two systems.

I would need the Windows system for some stuff at work, but prefer the Ubuntu side for everything else.  Since the laptop has a microSD card slot, is it possible to install Ubuntu on a microSD card, and then have the boot option for which one I want?

I know it has UEFI, but that can be disabled decently easy.


My other wonder is how stable the microSD install will be.  I've read that they can be less stable than installing on an actual hard drive (whether mechanical or SSD).

---

### Post by sudodus on 2014-12-18
MicroSD (flash cards in general) and USB pendrives contain cheap and mass produced memory chips plus a controller unit. The memory wears from writing, and the lifetime is shorter than in HDDs and high quality SSDs. The controller contains a system to spread the wear, and new flash cards and USB pendrives are better than old ones. Still, it can be a good idea to use the mount option **noatime** and to avoid swap (or keep swap in another drive).

See these links for more details

[https://help.ubuntu.com/community/Installation/FromUSBStick#Prerequisites](https://help.ubuntu.com/community/Installation/FromUSBStick#Prerequisites)

[This link to a post by DuckHook in the Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=2178075&p=12805426#post12805426") describes how a flash drive works, and how it can fail, first getting read-only, then totally 'bricked'.

-o-

Another issue is that of the UEFI system. According to the general specifications it should allow other distros (than Windows), but some computers have special systems that make it hard. I don't know about HP Stream 13. See these links

There is a good wiki page about [booting with UEFI]("https://help.ubuntu.com/community/UEFI"), and a good tutorial thread, [UEFI Installing - Tips]("http://ubuntuforums.org/showthread.php?t=2147295"). 

Finally, [try Ubuntu (Kubuntu, Lubuntu, Xubuntu, ...) before installing it]("http://ubuntuforums.org/showthread.php?t=2230389")

---

### Post by RichieB07 on 2014-12-18
Thanks for all the awesome information!

---

### Post by ajgreeny on 2014-12-18
You may also find, as Windows is already installed, that you can't disable UEFI without making it impossible to boot to Windows, unless you reinstall it.

I suspect it will possibly be easier to run Ubuntu with UEFI, but be warned, HP has a tendency to make it more difficult to boot to anything but Windows in its UEFI setup; there are ways around this but it just adds to our Linux problems.
HP and some others will not let you set anything other than Windows as default in UEFI menu. But there are work arounds which I show below.
Thanks to forum member oldfred for this info.

UEFI still lets you boot devices and the /efi/Boot folder has bootx64.efi which is the hard drive boot entry. If you rename that and make it be grubx64.efi then booting hard drive boots grub menu.

Other work arounds.
[http://ubuntuforums.org/showthread.php?t=2234019](http://ubuntuforums.org/showthread.php?t=2234019)

Script that automates the rename. Not tested but looks like it should work.

script to auto create bootx64.efi as grub
[http://askubuntu.com/questions/549647/uefi-machine-doesnt-boot-ubuntu-through-nvram-bootcatalog-how-to-fix](http://askubuntu.com/questions/549647/uefi-machine-doesnt-boot-ubuntu-through-nvram-bootcatalog-how-to-fix)

---

