---
title: "Installation on HP Dv6 (blank screen)"
date: 2011-12-18
forum: Installation &amp; Upgrades
---

### Post by celtic426 on 2011-12-18
I recently bought an HP dv6 and now I have the urge to install linux on it.  So far I've tried three different distros and they all result the same way.

I boot the live CD and and the boot menu comes up and I hit Run or Install Ubunutu.  After I hit enter the screen goes blank.  Not even a black screen - the screen just like shuts off as if the power was off.  So I'm guessing there's a problem detecting a graphics option.

The laptop has switchable graphics: a big graphics card for games, and discrete graphics for other less demanding tasks.  You can imagine how this could create problems for linux...

Now, HP released a BIOS update which I installed which supposedly lets you choose a fixed graphics option in the BIOS.  So you can choose which graphics option/card is on at all times.  But I cannot find this option anywhere in the BIOS.

So if someone could let me know what I could add to the boot menu command or any other ideas would be greatly appreciated.  

Thanks.

---

### Post by MAFoElffen on 2011-12-18
> **celtic426 said:**
> I recently bought an HP dv6 and now I have the urge to install linux on it.  So far I've tried three different distros and they all result the same way.

I boot the live CD and and the boot menu comes up and I hit Run or Install Ubunutu.  After I hit enter the screen goes blank.  Not even a black screen - the screen just like shuts off as if the power was off.  So I'm guessing there's a problem detecting a graphics option.

The laptop has switchable graphics: a big graphics card for games, and discrete graphics for other less demanding tasks.  You can imagine how this could create problems for linux...

Now, HP released a BIOS update which I installed which supposedly lets you choose a fixed graphics option in the BIOS.  So you can choose which graphics option/card is on at all times.  But I cannot find this option anywhere in the BIOS.

So if someone could let me know what I could add to the boot menu command or any other ideas would be greatly appreciated.  

Thanks.
Okay... there is over different 20 laptops of the HP DV6-xxxx.  Which is yours?  Imaterial of that, what are your 2 Video GPU's?

---

### Post by celtic426 on 2011-12-18
Thanks for trying to help.

It's a dv6-6123cl with an AMD Radeon HD 6520G.

And I'm not sure of the smaller GPU but it's an AMD A6-3400m processor quad core if that helps.

---

### Post by MAFoElffen on 2011-12-18
> **celtic426 said:**
> Thanks for trying to help.

It's a dv6-6123cl with an AMD Radeon HD 6520G.

And I'm not sure of the smaller GPU but it's an AMD A6-3400m processor quad core if that helps.
Thank goodness!  (Switched NVidia is harder) Use nomodeset or radeon.modeset=0 as a boot option to install and on the first boot up. If you need instructions on that:
[COLOR=Red][SIZE=2][COLOR=Black][SIZE=1]**[Modesetting and the LiveCD]("http://ubuntuforums.org/showpost.php?p=10740097&postcount=3")**[/SIZE][/COLOR][/SIZE][/COLOR]
[COLOR=Red][SIZE=2][COLOR=Black][SIZE=1]**[Temporarily Editing Grub Menu for Boot Options]("http://ubuntuforums.org/showpost.php?p=11491229&postcount=812")**[/SIZE][/COLOR][/SIZE][/COLOR]

Install the ATI Catalyst binary driver using these directions... The ATI Catalyst utility will see both GPU's and let you switch between....
[COLOR=Red][SIZE=2][COLOR=Black][SIZE=1]**[Installing ATI Binary Drivers]("http://ubuntuforums.org/showpost.php?p=10950714&postcount=334")**[/SIZE][/COLOR][/SIZE][/COLOR]

---

### Post by celtic426 on 2011-12-19
Thank you for your response although it didn't work for me. :(

I've tried booting about 20 times while adding one of those lines in.  But it didn't seem to help. :/

Anything else you know of I could do? :confused:

---

### Post by MAFoElffen on 2011-12-19
> **celtic426 said:**
> Thank you for your response although it didn't work for me. :(

I've tried booting about 20 times while adding one of those lines in.  But it didn't seem to help. :/

Anything else you know of I could do? :confused:
Can you get to the "recovery" menu?

---

### Post by Mark Phelps on 2011-12-19
Find it very hard to believe that the Catalyst Control Center will also allow you to manage Intel drivers ...

Perhaps something in the link below will help:

[https://help.ubuntu.com/community/HybridGraphics]("https://help.ubuntu.com/community/HybridGraphics")

---

### Post by celtic426 on 2011-12-19
MAFoElffen, I don't think I can get to the recovery menu, unless there's a way of getting there from the main boot screen menu.  

Would something like the "Script for use during bootup" in the Hybrid Graphics link Mark Phelps listed help me?

Another note - Upon trying to boot Fedora 16, it makes some progress booting but then I come across an error which a google search shows is a problem in the Xorg config.  But when I went to look at the Xorg log it was permission denied even tho I logged in as root.  Is there a way I can edit or see what's going in the Xorg config (on both Ubuntu or Fedora) ?

I appreciate your guys' help, this is frustrating.

---

### Post by MAFoElffen on 2011-12-19
> **Mark Phelps said:**
> Find it very hard to believe that the Catalyst Control Center will also allow you to manage Intel drivers ...

Perhaps something in the link below will help:

[https://help.ubuntu.com/community/HybridGraphics](https://help.ubuntu.com/community/HybridGraphics)
Experience with this through users in my Graphics sticky.  That link is for good for nVidia hybrid graphics.  Not sure if it works with Intel/ATI... because those users I helped went with the ATI binaries and didn't need to use that route. I'm supposing it make work, but for ATI...

ATI, even though they have a boiler plate disclaimer on hybrid graphicss, their Catalyst Control Panel supports it:
[COLOR=Red][SIZE=2][COLOR=Black][SIZE=1]**[Installing ATI Binary Drivers]("http://ubuntuforums.org/showpost.php?p=10950714&postcount=334")**[/SIZE][/COLOR][/SIZE][/COLOR]

It doesn't control the intel chipset, it deals with the ATI chipset.  Even with optimus (nvidia) under Windows7, the intel chipset stays on all the time.

---

### Post by MAFoElffen on 2011-12-19
> **celtic426 said:**
> MAFoElffen, I don't think I can get to the recovery menu, unless there's a way of getting there from the main boot screen menu.  

Would something like the "Script for use during bootup" in the Hybrid Graphics link Mark Phelps listed help me?

Another note - Upon trying to boot Fedora 16, it makes some progress booting but then I come across an error which a google search shows is a problem in the Xorg config.  But when I went to look at the Xorg log it was permission denied even tho I logged in as root.  Is there a way I can edit or see what's going in the Xorg config (on both Ubuntu or Fedora) ?

I appreciate your guys' help, this is frustrating.
Please post those /etc/X11/xorg.conf and /var/log/Xorg.0.log files...

Which driver did you install? Was it a binary or packaged file? The reason I ask is that the fglrx packaged driver does not contain the Catalyst Control Panel, does it? My understanding was that it didn't. (But understand things change) That utility is sothing that your can't do without, with your hardware.

The recovery menu is accessed from the Grub Menu, under "Recovery"... the second menu item.

---

### Post by celtic426 on 2011-12-19
> **MAFoElffen said:**
> Please post those /etc/X11/xorg.conf and /var/log/Xorg.0.log files...

Which driver did you install? Was it a binary or packaged file? The reason I ask is that the fglrx packaged driver does not contain the Catalyst Control Panel, does it? My understanding was that it didn't. (But understand things change) That utility is sothing that your can't do without, with your hardware.

The recovery menu is accessed from the Grub Menu, under "Recovery"... the second menu item.

Thanks again for your response although we may be misunderstanding each other as I have not installed any drivers yet because I haven't even installed the ubuntu system yet.  I only have Windows and now I'm just trying to install ubuntu but can't get the livecd to boot.

Can I get the contents of those two files just on the livecd without a system installed?

I don't know I'm kind of confused now, I'm just trying to get the livecd to boot so I can install it.

---

### Post by MAFoElffen on 2011-12-20
> **celtic426 said:**
> Thanks again for your response although we may be misunderstanding each other as I have not installed any drivers yet because I haven't even installed the ubuntu system yet.  I only have Windows and now I'm just trying to install ubuntu but can't get the livecd to boot.

Can I get the contents of those two files just on the livecd without a system installed?

I don't know I'm kind of confused now, I'm just trying to get the livecd to boot so I can install it.
I was confused.

Okay then.  On the LiveCD, the first panel is a black screen with a person/keyboard icon. Press <Esc> > It will go to a low res (vga) screen with a box for language > after that is the Advanced Install Menu. > From there press <F6> then <Esc>. Look at the boot line that appeared. It will have a blnking cursor.... That is where you can add the kernel boot options. Then use "try" to boot and test.

It those don't work. Then get back to the Advanced Boot Menu and at that menu screen, press <Esc>... A message will appear saying Exiting Graphical Install process and entering text install process.  It will try to probe the graphics to find a mode.  It will either find one, error to a message then present a text menu to pick vga mode or drop to a prompt.

If you can't install from the 2 methods above, then there is a text-based install from either the Alternate Install CD or the Minimal Install CD.

---

### Post by celtic426 on 2011-12-21
Ok, i tried those two methods but they didn't work.  Once I install it with the text based installer would I have the same problem with the blank screen?

---

### Post by lefthand on 2012-01-01
I've been playing around with this same model from Costco and am seeing the same thing. I was able to get to the graphic installer when I marked nomodeset and acpi=off. After the install was done it still just went to black screen sadly.

I flashed the bios with the latest but still no option to disable either graphics mode.

I was just about to return it (and still might) but I decided to try 12.04 even though it's still in Alpha. To my surprise it all came up as expected. I just finished the install and it seems to be working ok so far. I'm hoping I can use catalyst to manage the graphics now but I haven't started on that.

---

### Post by punkybouy on 2012-01-16
Have you tried using the alternate installation CD ?  64 bit? That would be nothing but a text based install.  Nice thing about the alternate CD is that it gives you the option to encrypt the drive.  You also said you are using Windows.  Does that mean you are trying to setup up a dual boot machine?

---

### Post by lefthand on 2012-01-16
> **punkybouy said:**
> Have you tried using the alternate installation CD ?  64 bit? That would be nothing but a text based install.  Nice thing about the alternate CD is that it gives you the option to encrypt the drive.  You also said you are using Windows.  Does that mean you are trying to setup up a dual boot machine?

Even with the alt installer once you finish the install, the graphics don't work. The problem does appear to be fixed in 12.04. I ended up returning mine since I don't think the discrete graphics were going to work any time soon. There were a few other issues so it just wasn't worth it to me. Ended up getting Lenovo which works almost perfectly.

---

