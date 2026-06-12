---
title: "Black screen after upgrating to 10.04"
date: 2010-05-26
forum: Installation &amp; Upgrades
---

### Post by davoudi on 2010-05-26
**So I just upgrate my Ubunutn to 10.04 from 9.10 and it seems I have problem with graphic card. I added div file extracted from windows in the previous Ubuntu release and things were fine but now I have a black screen. This is the output of lspci**


> 
[B][URL="http://www.futureshop.ca/en-CA/product/-/b9000613.aspx?path=61ea50e77f116b6b0a379bdd8abb5335en02"]lspci | grep VGA
01:00.0 VGA compatible controller: nVidia Corporation GT218 [GeForce 310M] (rev a2)[/URL][/B]


[B]
Thanks for you time.
[/B]

---

### Post by davidmohammed on 2010-05-26
try booting with nomodeset in your grub...

press shift on boot to display grub
press e to edit

add nomodeset before quiet splash

---

### Post by davoudi on 2010-05-26
That is how my grub look like

> 
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""


So should I add nomodeset to GRUB_CMDLINE_LINUX and then move the line up?

And should I rename xorg file?

---

### Post by davidmohammed on 2010-05-26
in lucid you dont need /etc/X11/xorg.conf for most graphics cards.  Suggest rename the file, boot with nomodeset and see if your desktop appears.

Since you have nvidia graphics, there should be some drivers in administrator - hardware drivers to install.  Once installed, you will not need to boot with nomodeset.

---

### Post by davoudi on 2010-05-26
My desktop is on now. I run the hardware drivers but it couldn't find any driver! I can install one nVidia driver using SMP if I know the version.

---

### Post by WinRiddance on 2010-05-26
> **davoudi said:**
> My desktop is on now. I run the hardware drivers but it couldn't find any driver! I can install one nVidia driver using SMP if I know the version.

You might not need any additional drivers if Lucid recognized everything properly. If you right click somewhere on your desktop, click on **change desktop background** which will open the place where you can change themes and so on. There are some tabs at the very top when you first open that window. Click on the last one to the right, the one for desktop or** visual effects**. There should be at least 3, possibly 4 different options there on the left. See if you can click on the third one from the top to enable all of your 3D graphic settings. If you can, then all's well and you don't need any other drivers. Hope this helps ...

---

### Post by davoudi on 2010-05-26
> **WinRiddance said:**
> You might not need any additional drivers if Lucid recognized everything properly. If you right click somewhere on your desktop, click on **change desktop background** which will open the place where you can change themes and so on. There are some tabs at the very top when you first open that window. Click on the last one to the right, the one for desktop or** visual effects**. There should be at least 3, possibly 4 different options there on the left. See if you can click on the third one from the top to enable all of your 3D graphic settings. If you can, then all's well and you don't need any other drivers. Hope this helps ...
I have laready tried that but no luck. I get the following message: Desktop effect could no be enabled.

---

### Post by davoudi on 2010-05-27
I also tried the follwoing solution :[http://ubuntuforums.org/showthread.php?t=1467074](http://ubuntuforums.org/showthread.php?t=1467074) but no result.

---

### Post by davoudi on 2010-05-29
Has anybody tried this?: [https://launchpad.net/~xorg-edgers/+archive/ppa](https://launchpad.net/~xorg-edgers/+archive/ppa)

---

### Post by davoudi on 2010-06-01
*Solved here: [http://ubuntuforums.org/showthread.php?t=1470822](http://ubuntuforums.org/showthread.php?t=1470822) 			*

---

