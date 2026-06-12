---
title: "Dual Boot Question"
date: 2008-11-21
forum: Installation &amp; Upgrades
---

### Post by wausaubill on 2008-11-21
I am not sure what other folks think about this, but it seems to make sense to me.

I have two internal hard drives installed in my Windows XP box.  One drive is allmusic and photos, so I can move those easily and use the whole drive for Ubuntu.

Here is my question...

Can I make up a boot CD that will boot into Ubuntu and then use that second drive to run everything from?  I am sure that you can, but if there are instructions somewhere (I have looked but not found anything exactly like that).

I figure I will be running Ubuntu most of the time and booting off the CD saves me the trouble of configuring GRUB, worrying about my MBR and such.  When I want XP, I just restart and when I want to go back to Ubuntu, I just slip the CD in and restart.

Any ideas, suggestions or links to tutorials would be most appreciated.

Thanks!

Bill

---

### Post by inobe on 2008-11-21
use the second drive to run everything ?

could you please give us more detailed information .

---

### Post by theozzlives on 2008-11-22
You can install Ubuntu in Windows

---

### Post by caljohnsmith on 2008-11-22
You can install Ubuntu to your current data HDD, and also have Grub installed to MBR of that drive; that way your Windows drive is untouched, and if you set your BIOS to boot your Ubuntu drive, you can boot either Ubuntu or Windows from your Grub menu. So really I don't see any reason you would need to create a boot CD for Ubuntu, but it's up to you of course. If you want to install Grub to the MBR of your current data drive when you install Ubuntu, just click the "advanced" button near the end of the installation process, and specify "/dev/sdb" (or whichever is the data drive) as the place to install Grub. That's all there is to it. Once you get the Ubuntu drive booting OK, I can help you add a entry for Windows in your Grub menu if you like; just let me know. Good luck and let us know how it goes. :)

---

### Post by wausaubill on 2008-11-23
Thanks Caljohn, I will look at that methdology.  The main reason I wanted to create a boot CD rather than using GRUB (other than not messing with my first (Windows) drive) is that I tried to install WUBI to use another drive and for some reason (that I was not able to figure out and no one here seemed to know off the top of their head either) GRUB did not work properly so I could not use it.

I have used the live CD and it seems to work great, even configuring my wireless pci card properly.

Anyway, I figured that by using a boot CD I could avoid a Murphy's type situation where GRUB would be one more thing that could go wrong.  Seemed to make sense to me anyway. :)

Thanks!

Bill

---

### Post by caljohnsmith on 2008-11-23
> **wausaubill said:**
> Thanks Caljohn, I will look at that methdology.  The main reason I wanted to create a boot CD rather than using GRUB (other than not messing with my first (Windows) drive) is that I tried to install WUBI to use another drive and for some reason (that I was not able to figure out and no one here seemed to know off the top of their head either) GRUB did not work properly so I could not use it.

I have used the live CD and it seems to work great, even configuring my wireless pci card properly.

Anyway, I figured that by using a boot CD I could avoid a Murphy's type situation where GRUB would be one more thing that could go wrong.  Seemed to make sense to me anyway. :)

Thanks!

Bill
Wubi actually uses "Grub4DOS", and it also modifies your Windows boot loader, so really your bad experience with Wubi should hopefully not have much relevance to using the Grub that you get with a normal Ubuntu install. I think you should be fine, but if you run into any problems, let me know and I'll try to help you sort them out. :)

---

### Post by vistadude on 2008-11-23
I don't realy get what your saying, but no, now if you wanted when in the live cd you could go to the place menu and select computer and then go to the hard drive you want and access the files on there.

---

### Post by wausaubill on 2008-11-23
Sounds good, CalJohn, I will be giving it a try soon and will let everyone know the results.

---

