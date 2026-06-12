---
title: "Ubuntu 10.04 Brightness setting on Acer Aspire 4741"
date: 2010-08-05
forum: Installation &amp; Upgrades
---

### Post by arimogi on 2010-08-05
Hi all,

I am a new user of Ubuntu, I use Ubuntu 10.04 Lucid Lynx on my laptop Acer Aspire 4741G and the specification are:
1. Intel(r) Core(tm) i5-430M Processor
2. Intel(r) HD Graphics
3. 2GB Memory
4. HD LED LCD

I have a problem in adjusting brightness, before this laptop, I used Ubuntu on my Acer Extensa, all shortcut buttons are working properly, include Fn button. To adjusting brightness, I only have to push Fn button + arrow left or arrow right. And now, I try in Aspire 4741G, it does not work. I also try to type command via terminal:

echo "some value" > /proc/acpi/video/VGA/LCD/brightness

but still doesn't work.

Anyone can help me? :(
Thanks for the attention.


best regards,

Ari Mogi

---

### Post by Revolutionary101 on 2010-08-05
In Ubuntu the Fn buttons for laptops can be a bit finicky. I also have problems with this on my laptop, but I changed my shortcuts to Ctrl+"whatever key" to make it do the exact same commands as the Fn key did.

---

### Post by arimogi on 2010-08-09
Well, thanks for the attention, but I've tried to use another function and program to dim or decreased brightness of my laptop, and it still doesn't work. From power management also doesn't work. It doesn't matter if Fn-keys doesn't work, but I need is just to dim the light. Is it any other solution.
Thank for your attention.


Best regards,

Ari Mogi

---

### Post by garvinrick4 on 2010-08-09
You want a GUI way, right click panel and add to panel go to brightness applet and add.

---

### Post by madarve on 2010-08-14
I have the same problem with that laptop, and no, It's not about looking for an easy or pretty-GUI to adjust brightness, it just about doing it. There is currently no way of adjusting brightness in the laptop (maybe a driver issue?).

Any help would be appreciated.

Thanks

---

### Post by pjferra on 2010-08-25
I have an other model of Acer, but have the same problem.
I solved this by adding a couple of boot options.
On a console do the following:

1) sudo gedit /etc/default/grub
2) change the line that says
             GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
   to
             GRUB_CMDLINE_LINUX_DEFAULT="quiet splash nomodeset acpi_backlight=vendor"
3) save
4) sudo update-grub
5) restart ubuntu

Good luck!

---

### Post by Darkhorse85 on 2010-09-22
Hi 
I also have a aspire 4741 and the above solution rendered my laptop unbootable. If anybody is having similar problems with this solution try the following post as it fixed the problem for me.

[http://ubuntuforums.org/showpost.php?p=9291657&postcount=1](http://ubuntuforums.org/showpost.php?p=9291657&postcount=1)
:)

---

### Post by ca1ig0la on 2010-10-11
@arimogi

Please can you paste in your xorg.conf? I have your same laptop with a geforce gt415M but can't get nvidia drivers to work. Actually I can't get any driver to work. I'm running in low graphic mode (800x600) and can't figure out what's wrong nor how to fix it.

I tried everything: from the additional driver utility to the binary drivers from the nvidia website. Tried to install nv and nouveau... nothing. I can't.

Did you upgrade from 10.04 or did you do a plain install? 

Thanks

---

### Post by arimogi on 2011-03-15
Finally, it is solved, I change my OS to Ubuntu 10.10. I have try all solution you provided here, but I still don't know why the brightness can't reduce. Anyway thanks for your help.

---

### Post by sumith_p on 2011-08-23
> **Darkhorse85 said:**
> Hi 
I also have a aspire 4741 and the above solution rendered my laptop unbootable. If anybody is having similar problems with this solution try the following post as it fixed the problem for me.

[http://ubuntuforums.org/showpost.php?p=9291657&postcount=1](http://ubuntuforums.org/showpost.php?p=9291657&postcount=1)
:)
Thanks...i am using ubuntu 11.04 n acer aspire 5750....that worked for me...i mean the brightness issue...

---

