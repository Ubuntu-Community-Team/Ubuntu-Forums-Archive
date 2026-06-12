---
title: "Bootable CD to chainload ISO from USB?"
date: 2017-02-03
forum: Installation &amp; Upgrades
---

### Post by private_lock on 2017-02-03
Hello!

My parents have this aged PC, which is not enabled to boot from USB (there simply is no option in the BIOS). So I had it boot an old live CD of Kubuntu 08.04 64-bit (working OK) ... but I'd rather prefer to install a longterm-support lubuntu 16.04.1 LTS Now the image is bigger than the 700MB empty disk I have, so I was thinking to just make a minimal CD, to chainload the actual ISO from USB...

Is this possible? How to do it? Is there some howto-guide or an ISO ready to burn to my CD?

I could also install the Lubuntu Iso to the USB-Pendrive via usb-disk-creator, if this is of any help, I just need the CD to tell the computer to go on booting from USB.

Thanks
private_lock

---

### Post by oldfred on 2017-02-03
Server install may be better than minimal.
You can still then add desktop of choice.

You can use plop on older systems.
       [http://www.plop.at/en/bootmanagers.html](http://www.plop.at/en/bootmanagers.html)

---

### Post by C.S.Cameron on 2017-02-03
Plop +1

Or if the computer has a hard drive you might consider installing grub on it.

---

### Post by private_lock on 2017-02-05
Thank you! I got it working ...

Just to document the steps in a little more detail, should I come back to this later :-)
- prepare a bootable empty USB-pendrive (don't mount it, everything will be deleted anyway)
- [http://cdimage.ubuntu.com/lubuntu/releases/16.04/release/lubuntu-16.04.1-desktop-amd64.iso](http://cdimage.ubuntu.com/lubuntu/releases/16.04/release/lubuntu-16.04.1-desktop-amd64.iso)
- beware, usb-creator-kde is a little spooky, as the progress-window is always there, even right after the start
- and the progress-window might creep under other windows, so just minimize everything else, if you suspect it might have crashed
- luckily the LED of the USB-pendrive was still blinking, keeping me from withdrawing it

- download [https://download.plop.at/files/bootmngr/plpbt-5.0.15.zip](https://download.plop.at/files/bootmngr/plpbt-5.0.15.zip) or newer (*not* PlopKexec or the other new bootmanager project)
- extract plpbt.iso from the main directory (*not* any of the other iso in deeper directories)
- you can test the iso in a VirtualBox, to start some chooser menu on a starfield screensaver (though, I could not get VirtualBox to chainload my USB-pendrive ...)
- burn the plpbt.iso to CD anyway (yes, it is a tiny file of only 544 KiB from February 2015)
- high-end hardware like my notebook will only boot the CD when put in legacy mode deactivating UEFI support in BIOS (again no luck chainloading my USB-pendrive here)
- now boot the old computer (pre-UEFI-aera) from CD (to get the starfield-menu again)
- only now stick the prepared USB-pendrive in
- select USB with cursor-buttons and press Enter
- Jippie: Lubuntu is finally starting a life session, ready to install

Finally a note on the failed experiments: the doc says, USB-hubs are not supported. So besides UEFI, this might also be an issue to explain, why the other two setups did not succeed.

Thanks again
private_lock

---

