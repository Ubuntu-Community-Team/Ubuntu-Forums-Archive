---
title: "[SOLVED] Someone please put me out of my misery"
date: 2008-09-29
forum: Installation &amp; Upgrades
---

### Post by thomasboleyn on 2008-09-29
Is it possible in any way shape or form to install Hardy Ubuntu on this laptop - [http://www.laptopsdirect.co.uk/Sony-Vaio-K215Z-PCG-K215Z/version.asp](http://www.laptopsdirect.co.uk/Sony-Vaio-K215Z-PCG-K215Z/version.asp) ?

Or am I stuck with Feisty forever? (I can't even use Gutsy..black screen of death after boot)

Is this an impossible quest?

Please help!x

---

### Post by Victormd on 2008-09-29
I don't have a sony laptop so it's hard to say wether it will or will not work on this specific model. However, Hardy has much better hardware compatibility when compared to Gutsy (personal experience with HP and Dell laptops). My suggestion would be to dual boot between feisty and hardy, and if hardy works (which I believe it will), get rid of feisty... :)

---

### Post by thomasboleyn on 2008-09-29
I'm downloading the alternative text based installer for Hardy at the moment, as the normal one I have on cd won't get past the boot screen and I noobishly don't know how to use the 'quiet-splash' option. We'll see what happens...

---

### Post by Victormd on 2008-09-29
You might want to check out the noapic and noapci switches in Grub when booting from the LiveCD... Most of the times, adding noapic to the end of the kernel line in Grub will fix problems similar to yours. Let me know if you need help doing this, it's a quick and simple check...

Check my post (#3) here:
[http://ubuntuforums.org/showthread.php?p=5278082#post5278082](http://ubuntuforums.org/showthread.php?p=5278082#post5278082)

---

### Post by thomasboleyn on 2008-09-29
Yes I do need help doing this please. How do I enable these different boot options from the menu that comes up when I boot from the cd? I gave up on the text based installer..far too complicated for me :s

Thanks for your help!

---

### Post by thomasboleyn on 2008-09-29
bump!

---

### Post by Victormd on 2008-09-29
Sorry, just got back to my comp. Did you take a look at the link in my previous post?

---

### Post by Sef on 2008-09-29
>  		bump! 	

Please don't bump unless 24 hours have gone by.  Thank you.

---

### Post by thomasboleyn on 2008-09-29
Sorry about the bump, just thought I'd let you know I'm typing this from the comfort of the hardy live session! I selected the first option that 'e' brings up at the initial menu, 'acpi off' I think it was, or something similar, and bang I'm in, advanced desktop effects and all! My built in wireless doesn't seem to be supported so I'm using a wired connection at the moment, but I couldn't be more grateful for your help! How should I go about enabling this option permanently from now on for the boot?

Thanks sooooooo much again!

---

### Post by thomasboleyn on 2008-09-29
I'm really sorry I am being an idiot, I've realised you mentioned it in the post you linked too aswell. Just finishing the install now, everything seems to be going well. Thanks soooo much again.

---

### Post by Victormd on 2008-09-29
Glad to hear it worked! :)
> **thomasboleyn said:**
> My built in wireless doesn't seem to be supported so I'm using a wired connection at the moment
Once you install the updates, your wireless should be listed under SYSTEM>ADMINISTRATION>HARDWARE DRIVERS 

> How should I go about enabling this option permanently from now on for the boot?
To permanently enable this, you'll need to edit your grub and add this option to it. The previous link shows how to do that as well, let me know if you have any trouble. However, once you've installed all the updates, you might not need this option anymore so you may want to play around with it now that you know what works... :)

---

