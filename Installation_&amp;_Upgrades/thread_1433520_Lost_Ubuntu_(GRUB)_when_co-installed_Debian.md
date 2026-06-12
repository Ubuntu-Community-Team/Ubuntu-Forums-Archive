---
title: "Lost Ubuntu (GRUB) when co-installed Debian"
date: 2010-03-19
forum: Installation &amp; Upgrades
---

### Post by digitalis49 on 2010-03-19
I am **not** a linux expert so please be gentle.

I have been using the latest release of Ubuntu  ((Gnome) (hd1,0)) and thought I would also try out Debian under KDE.

I installed Debian (netinst) which went on hd1,5.

Now, only Debian and Windows XP appear on the Grub menu.

Is there any way to include Ubuntu in Grub?

Again, please, I am not an expert.

Hope there is some help out there......

Thanks, in advance.

---

### Post by tommcd on 2010-03-19
You can either add Ubuntu to Debian's grub; or you can reinstall Ubuntu's grub2 to the MBR and then update grub2 to include Debian.
Did you install Debian Lenny (aka Debian stable) or Debian Squeeze (aka Debian testing)?
If you are on Lenny, then Lenny still uses grub-legacy. To add Ubuntu to Debian's grub-legacy, follow the advice in post #4 of this thread:
[http://ubuntuforums.org/archive/index.php/t-393379.html](http://ubuntuforums.org/archive/index.php/t-393379.html)
**EDIT**: If your Ubuntu install is on an ext4 partition, I am not sure if the grub-legacy on Lenny would be able to boot that. There is no harm in trying it though.

To reinstall Ubuntu's grub2 to the MBR, follow the advice at the end of post #6 in this thread (the stuff after EDIT)
[http://ubuntuforums.org/showpost.php?p=8771566&postcount=6](http://ubuntuforums.org/showpost.php?p=8771566&postcount=6)
Also see this:
[https://wiki.ubuntu.com/Grub2#Recover%20Grub%202%20via%20LiveCD](https://wiki.ubuntu.com/Grub2#Recover%20Grub%202%20via%20LiveCD)
And here is a great guide for grub2. The stuff on reinstalling grub2 to the MBR is in item 13 "Reinstalling GRUB 2 from LiveCD":
[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)
There seems to be some slight variations on how to reinstall grub2. That is why I posted those links.
  
Then after grub2 is reinstalled to the MBR, boot up Ubuntu and run:
```
sudo update-grub
```
This should add Debian to Ubuntu's /boot/grub/grub.cfg file so you can also boot Debian.

---

### Post by MentatGhola on 2011-07-10
Thanks this was a big help.  I needed the command to update grub so I could see my new debian install.

---

