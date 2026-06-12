---
title: "Cant get grub loader options need nomodeset nvidia"
date: 2011-04-15
forum: Installation &amp; Upgrades
---

### Post by toalorama on 2011-04-15
I have installed ubuntu by pressing F6 and setting nomodeset.
Need to install nvidia closed drivers.
On bootup dont know how to get grub options.
Have tried pressing shift.
Have tried pressing e.
Boots straight into nouveau drivers.
Any help appreciated.

---

### Post by drs305 on 2011-04-15
> **toalorama said:**
> I have installed ubuntu by pressing F6 and setting nomodeset.
Need to install nvidia closed drivers.
On bootup dont know how to get grub options.
Have tried pressing shift.
Have tried pressing e.
Boots straight into nouveau drivers.
Any help appreciated.

Did you **hold** down the SHIFT key during boot to display the Grub2 menu (different from pressing and releasing, if that is what you did)? If this didn't work you could try multiple presses of the ESC key but your timing would have to be fairly good.

If you get to the menu, press 'e' to edit the first menuentry, then remove "quiet splash" and add "nomodeset" at the end of the line starting with "linux". Press CTRL-x to boot once you have added **nomodeset**, then install the drivers after it boots.

---

### Post by toalorama on 2011-04-16
ESC eventually did the trick.
Thanks.

---

### Post by coffeecat on 2011-04-16
> **toalorama said:**
> ESC eventually did the trick.
Thanks.

If pressing esc did the trick, you have legacy grub, not grub 2 which requires shift. The wording of your OP suggests that you have only recently installed Ubuntu, but you would only get legacy grub as default by installing a now-unsupported end-of-life version of Ubuntu. Which version of Ubuntu do you have?

---

### Post by drs305 on 2011-04-16
Actually although we don't mention it often, the ESC key function is still available in Grub 2. It's a fallback option which can still be used although holding down the SHIFT key is more reliable IMO. 

There are times the keystatus check is not incorporated into the grub.cfg file so having the ESC key option is still nice to have.

---

### Post by coffeecat on 2011-04-16
> **drs305 said:**
> Actually although we don't mention it often, the ESC key function is still available in Grub 2. It's a fallback option which can still be used although holding down the SHIFT key is more reliable IMO. 

There are times the keystatus check is not incorporated into the grub.cfg file so having the ESC key option is still nice to have.

Thanks for that. Useful to know.

---

### Post by drkages on 2011-10-03
> **toalorama said:**
> I have installed ubuntu by pressing F6 and setting nomodeset.
Need to install nvidia closed drivers.
On bootup dont know how to get grub options.
Have tried pressing shift.
Have tried pressing e.
Boots straight into nouveau drivers.
Any help appreciated.

I assume that you using 11.04, can you provide more details about how you got the installation to work. 

I am having a similar problem (nvidia gt240) but the nomodeset not working for me.

A better place for this discussion will be:

[http://ubuntuforums.org/showthread.php?t=1600807]("http://ubuntuforums.org/showthread.php?t=1600807")

---

