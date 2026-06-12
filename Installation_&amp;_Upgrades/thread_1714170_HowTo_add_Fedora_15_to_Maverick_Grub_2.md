---
title: "HowTo: add Fedora 15 to Maverick Grub 2"
date: 2011-03-25
forum: Installation &amp; Upgrades
---

### Post by kansasnoob on 2011-03-25
I just installed Fedora 15 to do some gnome3 testing and it still uses an antiquated grub. Rather than spending the time to add my many operating systems to it's grub I chose to just accept the default (Fedora only) and when the installation was complete I used the chroot procedure here (METHOD 3 - CHROOT):

[https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD](https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD)

To reinstall my Maverick grub 2, but I noticed Fedora was not picked up by os-prober. No biggy, I rebooted (and after fiddling in BIOS to get past the Fedora CD rebooting rather than ejecting) I booted into Maverick and once again ran "update-grub".

Arrgh, still not found! Still not a problem, this works for detecting many operating systems:

```
sudo apt-get install --reinstall libdebian-installer4
```

```
sudo os-prober
```

```
sudo update-grub
```

It worked ............ again!

So, if you want to check out the full suckage of gnome3/gnome-shell rock on. You'll soon find that SABDFL was right in pursuing Unity :D

Credit where credit is due, I learned this a long time ago here:

[http://digitizor.com/2009/12/28/how-to-add-opensuse-11-2-to-grub2/](http://digitizor.com/2009/12/28/how-to-add-opensuse-11-2-to-grub2/)

I've found it works for adding a lot of "nux" OS's to grub 2, enjoy.

---

### Post by zvacet on 2011-03-25
Tnx!  :D

---

### Post by Quackers on 2011-03-25
I just told Fedora to install grub (legacy) to the root partition. Then booted into Ubuntu and ran sudo update-grub. Fedora now appears in my grub2 menu. I'll keep it that way. Obviously it has drawbacks, but, I suspect, not as many as grub legacy and grub2 fighting each other :-)

---

### Post by mrsomoasun on 2011-05-22
You guys helped me get Fedora set up with no problem. The update-grub routine worked just fine.

That part about the Gnome 3 suckage. Yup, absolutely right. It's interesting, but stupid. I'm sold on Unity for sure. :guitar:

---

### Post by garvinrick4 on 2011-05-22
I looked at fedora 15 and in anaconda choose not to install any grub being it was grub-legacy 
as it seems all RedHats cousins use. Upate grub in whichever install grub-pc
is being used in and all OK. The problem I have had with Fedora is that it had some
funky way of dist-upgrading through its boot partition which of course I can have nothing
to do with do not use grub-legacy and or a boot partition? Any one else look into that?
 Another is with Debian using grub-pc you install and has no os-prober is a seperate
install, which is no problem just different. Was a selection in install not to install grub in
Debian which I like in a installation package.

---

### Post by Mac-ghost-hunter on 2011-06-08
How did you pick were to put the grub legacy?  I installed it and that last warning was no changes will be writen to disk and the fedora took off deleting my grub2 entry on the MBR.  I hope to get it fixed tonight what a headache with grub .97
 
Mac-ghost-hunter

---

