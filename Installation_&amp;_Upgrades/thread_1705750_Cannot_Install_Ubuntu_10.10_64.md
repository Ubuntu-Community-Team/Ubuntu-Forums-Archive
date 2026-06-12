---
title: "Cannot Install Ubuntu 10.10 64"
date: 2011-03-12
forum: Installation &amp; Upgrades
---

### Post by freekb0y on 2011-03-12
So to whoever is out there,
             I am trying to install Ubuntu 10.10 on a Intel i5 quad core with 4 gigs of Ram.  The Motherboard is an Asus P7P55D-E with an Asus Engt-240 Graphics card there is no on board Video Display.  The issue that I am encountering is that the live CD begins to boot and then returns with a blinking cursor.  I tried running the alternate Boot Cd with the same issue.  I can get to the option screen on the live cd by holding down shift but anything that I select after that I am once again presented by a blinking cursor.  If anyone has any knowledge on this issue it would be greatly appreciated

Thanks

---

### Post by Hippytaff on 2011-03-12
Hi and welcome to the forums :-)

What graphics card do you have?

---

### Post by freekb0y on 2011-03-12
Asus Engt-240 

here is more info

[http://www.google.com/products/catalog?q=asus+engt240&oe=utf-8&rls=org.mozilla:en-US:official&client=firefox-a&um=1&ie=UTF-8&cid=13034960472181106938&sa=X&ei=6AJ8TfzDEK6L0QHW_8DAAw&ved=0CDQQ8wIwAg#](http://www.google.com/products/catalog?q=asus+engt240&oe=utf-8&rls=org.mozilla:en-US:official&client=firefox-a&um=1&ie=UTF-8&cid=13034960472181106938&sa=X&ei=6AJ8TfzDEK6L0QHW_8DAAw&ved=0CDQQ8wIwAg#)

---

### Post by Hakunka-Matata on 2011-03-12
[

---

### Post by freekb0y on 2011-03-12
So during installation I turned off the quiet flag and I see the system going through the hardware.  It ends with edd information not available and before that link I see BIOS EDD facility v0.16 2004-jun-25, 0 devices found anyone have any idea????

---

### Post by Hakunka-Matata on 2011-03-12
> The issue that I am encountering is that the live CD begins to boot and then returns with a blinking cursor.

Where in the process of loading the LiveCD does the screen go to blinking cursor?

---

### Post by freekb0y on 2011-03-12
Out of curiosity could this have something to do with USB 3.0

---

### Post by Hakunka-Matata on 2011-03-12
> **freekb0y said:**
> So during installation I turned off the **quiet flag** and I see the system going through the hardware.  It ends with edd information not available and before that link I see BIOS EDD facility v0.16 2004-jun-25, 0 devices found anyone have any idea????

Then change 'quiet splash' to 'nomodeset,

---

### Post by Hakunka-Matata on 2011-03-12
Re: Newer versions of ubuntu don't work.
What hardware are you using?

I would suspect a video card problem that may be solved by using one of several possible kernel boot options that you may need to set, at least to start with, and then when you have the right driver for the card all may work OK.

Try the live CD, and when you get to the screen where you just see the purple screen with two icons at the bottom (a keyboard and a figure of a man) or when you get the option to Try ubuntu, Install ubuntu, etc etc, press F6 and try the [COLOR="Magenta"]nomodeset[/COLOR] option.

---

### Post by freekb0y on 2011-03-12
> Where in the process of loading the LiveCD does the screen go to blinking cursor? 	


The boot up off the disc starts then the screen flickers and there is the human being at the bottom of the screen and then it flickers again and I am presented with the cursor.  But I downloaded the alternate disc and have turned off the quiet flag and when it goes through the system config it hangs up in different areas I posted one of the errors and now it is stuck at usb 2-1.3: new low speed USB device using ehci_hcd and address 3

---

### Post by Hakunka-Matata on 2011-03-12
> The boot up off the disc starts then the screen flickers and there is the human being at the bottom of the screen 

At that point, you intervene, exactly how I don't know, by hitting TAB, or pressing F6, however it is done, you want to select the "nomodeset" option, or you replace quiet splash with nomodeset, or you add nomodeset behind quiet splash, I've seen numerous different posts on it,  I see this fix all over the forums but have never done it myself, because I've never had the problem and haven't been able to simulate it.

If you search on "nomodeset" here in the forum, you'll get loads of hits ...

---

### Post by freekb0y on 2011-03-12
> Then change 'quiet splash' to 'nomodeset,

Did this with same result sadly the system bombs out at different times in the scan

---

### Post by Hakunka-Matata on 2011-03-12
search this very forum for 'nomodeset' (maybe you already have, only guessing?) and you'll see lots of posts on the problem,

---

