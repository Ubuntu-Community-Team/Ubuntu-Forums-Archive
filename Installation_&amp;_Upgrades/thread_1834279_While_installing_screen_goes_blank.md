---
title: "While installing screen goes blank"
date: 2011-08-27
forum: Installation &amp; Upgrades
---

### Post by aliyanage on 2011-08-27
hi all,

I've got a sony vaio vgn-nr38m laptop and am currently trying to install the ubuntu 10.04 version.
I am able to start up with the cd and fill in the user name details, password, timezone etc. but as soon as I agree to erase and install and click the install button it goes up to about 5% and then gives me a black screen. The only thing visible is the mouse cursor, but thats about it and nothing happens.

Does anyone know why this is or what I need to do to avoid this from happening?


regards,
andrew

---

### Post by dino99 on 2011-08-27
see sticky on top of this subforum

---

### Post by Mark Phelps on 2011-08-27
You should NEVER just force an install on an untried machine.  Instead, use the Try Ubuntu option first -- to see what works and what doesn't.  That allows you to then use the forums to hunt down fixes for the problems -- so you will know what to do once you get it installed.

---

### Post by MAFoElffen on 2011-08-27
> **dino99 said:**
> see sticky on top of this subforum
Yes... See my sticky. 
**[B]Sticky:**[/B] 			                         [COLOR=#008C00]**[all variants]**[/COLOR] 			 			[Graphics Resolution- Upgrade /Blank Screen after reboot]("http://ubuntuforums.org/showthread.php?t=1743535")  

And what Mark said also > meaning, if you boot on the LiveCD and Try, without configuring anything else, with your model Laptop... >> You could confirm that graphics are going to work with youur Intel GMA X3100 GPU.  

It should with that chipset, but for some reason, because of other combinations, it may need a little help with a kernel boot switch.  You can try and test those it the LiveCD "Try" mode, until you can confirn that it works.

Anther thing that I have to add a disclaimer to (along with Mark), during the LiveCD Boot (instructions in my sticky / Post 3)... when it gets to the blank screen with the person/keyboard icon at the bottom... If you press the <esc> key... It will get to a keyboard dialog > press <esc> key.... >>>> It toggles the install into a "text mode" instead of "graphics mode"

The install might go through... possibly ending up with the same graphics issues or not after the install/reboot... >> Like i said, there usually isn't "many" reported problems recently with your chipset and the driver is "commonly" supported.  If you did that and it didn't work, you would be a little further along, but get to a text console session to diagnose and fix the problem.  

If you "aren't" familiar with CLI or commdline Linux, this might be intimidating...  My recommendation?  Play with the "try" mode of the LiveCD.  Look at post 3 of my sticky to learn how to get to and change the kernel boot switches.

---

