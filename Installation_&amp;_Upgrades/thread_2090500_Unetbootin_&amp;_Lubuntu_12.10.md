---
title: "Unetbootin &amp; Lubuntu 12.10"
date: 2012-12-02
forum: Installation &amp; Upgrades
---

### Post by lkz6998 on 2012-12-02
Hello,
I have a question I hope someone can help me with.  I would like to install Lubuntu 12.10 on my computer (not Live CD, I want to install it on my HD as the only operating system).

I downloaded the Lubuntu 12.10 ISO file, and I downloaded the latest version on Unetbootin so I could install from USB Flash drive instead of CD ROM.  

But Unetbootin doesn't list Lubuntu 12.10 on its "version" drop down menu.  It has 12.04 but not 12.10.  So does that mean I can't use Unetbootin?

Is there a work-around, or can somebody recommend another program to write an ISO to a USB Flash drive?

Thanks for any help.

---

### Post by Androzani1 on 2012-12-02
> Installing Other Distributions Using UNetbootin
Download and run UNetbootin, then select the "disk image" option and supply it with an ISO (CD image).

UNetbootin doesn't use distribution-specific rules for making your live USB drive, so most Linux ISO files should load correctly using this option. However, not all distributions support booting from USB, and some others require extra boot options or other modifications before they can boot from USB drives, so these ISO files will not work as-is. Also, ISO files for non-Linux operating systems have a different boot mechanism, so don't expect them to work either.

That is from the UNebootin website. See here: [http://unetbootin.sourceforge.net/#other](http://unetbootin.sourceforge.net/#other)

---

### Post by Abhinav Kumar on 2012-12-02
> **lkz6998 said:**
> Hello,
I have a question I hope someone can help me with.  I would like to install Lubuntu 12.10 on my computer (not Live CD, I want to install it on my HD as the only operating system).

I downloaded the Lubuntu 12.10 ISO file, and I downloaded the latest version on Unetbootin so I could install from USB Flash drive instead of CD ROM.  

But Unetbootin doesn't list Lubuntu 12.10 on its "version" drop down menu.  It has 12.04 but not 12.10.  So does that mean I can't use Unetbootin?

Is there a work-around, or can somebody recommend another program to write an ISO to a USB Flash drive?

Thanks for any help.
Hi lkz6998,
There is another option 'Diskimage' which you have to select and then you have to show the path of the 12.10 iso file using ... button located on the right. Once you are done , you can click OK.

Regards,
Abhinav

---

