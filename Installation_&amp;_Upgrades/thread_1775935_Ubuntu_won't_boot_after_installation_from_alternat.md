---
title: "Ubuntu won't boot after installation from alternate CD"
date: 2011-06-05
forum: Installation &amp; Upgrades
---

### Post by b0wter on 2011-06-05
I've tried to install Ubuntu 11.04 for the whole afternoon and I'm stuck.
Reason why I use the alternate cd is that I want to use an encrypted logical volume (full system, not just home folder). I did not create the partitions myself, I simply used the installer option for "guided LVM with encryption".
But now I have the problem that I finished the installation without error, but when I boot my laptop nothing happens. I do only get a blinking cursor, but no GRUB, which I installed too (because there is a nother hdd with win 7).

---

### Post by Quackers on 2011-06-05
You may need a boot option like nomodeset.
What graphics card do you have?

---

### Post by b0wter on 2011-06-05
Should be an Intel GMA x4500MHD.

---

### Post by Quackers on 2011-06-05
In that case you may need one of the i915.modeset=0 or i915.modeset=1 boot options, or something else.
For details on how to apply these boot options look at the 
"How to temporarily set kernel boot options on an installed OS (not wubi)"
section of the thread below 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)

---

### Post by cSquall on 2011-06-05
I have what may be a similar problem.  I upgraded to Natty and I can get to the grub menu selector and boot to the Windows partition fine, but if I choose the Ubuntu option, all I get is a pink screen...

Do I need to reinstall Grub, or does the fact that I see the Grub menu and that Windows boots indicate that my grub and Master boot records are fine?

---

### Post by Quackers on 2011-06-05
It could be a graphics problem. If your graphics card is a ATI or Nvidia one you could try the nomodeset boot option. If it's Intel GMA try one of the options previously mentioned.
It would also be better to start your own thread, as similar problems do not necessarily mean a similar fix.

---

### Post by Wray on 2011-06-05
> **Quackers said:**
> It could be a graphics problem. If your graphics card is a ATI or Nvidia one you could try the nomodeset boot option. If it's Intel GMA try one of the options previously mentioned.
[COLOR=Purple][SIZE=4]It would also be better to start your own thread, as similar problems do not necessarily mean a similar fix.[/SIZE]

[COLOR=Black]That is a good idea. Complete noob here.

How do i start a new thread?... told you!
[/COLOR][/COLOR]

---

### Post by Quackers on 2011-06-05
Near the top left of the page there is a brown coloured box with "New Thread" in it. Click on that :-)

And welcome to UF :-)

---

### Post by b0wter on 2011-06-05
I've been playing around a little more and what is strange is that, booting from the Live CD, I can unlock the encrypted volume in the Disk Utility but I can't active the volumes or access them in Nautilus.
Maybe something is wrong with them so that my laptop won't start (but then again I am wondering why GRUB won't show up). And since I cant access the config files I cannot change GRUB's settings (holding shift doesnt bring up the menu).

---

