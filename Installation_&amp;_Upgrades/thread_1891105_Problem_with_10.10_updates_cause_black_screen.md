---
title: "Problem with 10.10 updates cause black screen"
date: 2011-12-04
forum: Installation &amp; Upgrades
---

### Post by captain_mills on 2011-12-04
I have been using Ubuntu 10.04 for a while now and just recently decided to update to 10.10.  I am using a dual boot system with WinXP (for Photoshop and 3DS Max) on one partition and Ubuntu on the other.  When I turn my computer on, within 10 seconds I get a DOS screen that asks me what I want to boot.  Upon choosing Ubuntu (it gives me 4 options), it now takes almost right at 5 minutes now to load the login screen for Ubuntu 10.10.  It displays a blank black screen with a cursor blinking at the top.  It never did this in 10.04... After I log in, it takes another minute or so to load... Another thing it never used to do...

Any help will be appreciated. I can give any info needed to help solve the problem too...

Thanks!!!

---

### Post by Rubi1200 on 2011-12-04
Hi and welcome to the forums :-)

We prefer that people start their own threads as no two problems are exactly alike.

Moved to own thread, thanks for understanding.

---

### Post by spindler on 2011-12-04
it appears as if you might not have installed Ubuntu GUI or the desktop.  Run the following:

sudo apt-get install ubuntu-desktop

This will provide you a windows style desktop environment. 

Hope this helps.

Spindler

---

### Post by MAFoElffen on 2011-12-04
> **captain_mills said:**
> I have been using Ubuntu 10.04 for a while now and just recently decided to update to 10.10.  I am using a dual boot system with WinXP (for Photoshop and 3DS Max) on one partition and Ubuntu on the other.  When I turn my computer on, within 10 seconds I get a DOS screen that asks me what I want to boot.  Upon choosing Ubuntu (it gives me 4 options), it now takes almost right at 5 minutes now to load the login screen for Ubuntu 10.10.  It displays a blank black screen with a cursor blinking at the top.  It never did this in 10.04... After I log in, it takes another minute or so to load... Another thing it never used to do...

Any help will be appreciated. I can give any info needed to help solve the problem too...

Thanks!!!
what happens if you select "Recovery" at the Grub Menu > select boot in safemode/lowgraphics?

If it boot into a GUI from there, then go to "Hardware Drivers" to install graphics drivers.

If not then I give you instructions to get around that.

---

### Post by captain_mills on 2011-12-06
Okay, so I decided to do some problem solving based on the comments above....

Spindler, thanks, but before I go installing something, I'd like to know what it is... so I did some research.  Turned up nothing that I didn't feel I already had.  The GUI came up eventually, though it took forever, so I thought, "No, that can't be it"... but thanks anyway

MAFoElffen, I dug deeper into your comments and thought I'd take a look at my Grub menu... I tried going into my recovery mode and noticed that I had two of them.  My grub menu had the following options (simplified because I didn't write down word for word):

> 
ubuntu 2.6.35-31
ubuntu 2.6.35-31 (recovery)
ubuntu 2.6.32-35
ubuntu 2.6.32-35 (recovery)
memtest
memtest 115200
windows xp home edition


I decided to go thru each of them and see what happened with each.  I noticed that each of the -31 options took forever to load but the -35's loaded as quickly as I should expect...

So, I went in and looked for ways to clean up my grub menu... and found a few links... I will share one below.

[http://www.howtogeek.com/howto/17787/clean-up-the-new-ubuntu-grub2-boot-menu/](http://www.howtogeek.com/howto/17787/clean-up-the-new-ubuntu-grub2-boot-menu/)

At this point, I'd like some help understanding what the grub menu options were talking about... What are the -31 options?  are they what's left of my 10.04?  Are the -35's the new 10.10?  Do I need both of the memtests?

Once I get some answers to my grub menu questions, I'll consider this one solved and can be archived for others.  I would also like a pat on the back for trying to solve my own problem... :-) (j/k)

Anyway, please help with my grub menu questions above...  Thanks again!

CM

---

### Post by 2F4U on 2011-12-06
First of all, 2.6.32-35 and 2.6.35-31 are Linux kernel versions (I am assuming that you know what a Linux kernel is). The 2.6.32 kernel is most likely from an Ubuntu 10.04 version, while the other is from a newer Ubuntu version.

---

### Post by captain_mills on 2011-12-06
Strange because the 2.6.32-35 boots faster... much faster... than the 2.6.35-31.  And that's what the problem was.  When I boot into the 2.6.32-35, it still says it's 10.10... 

Thanks for the comment... But I still need some help apparently...

:-)
CM

---

### Post by MAFoElffen on 2011-12-06
> **captain_mills said:**
> Strange because the 2.6.32-35 boots faster... much faster... than the 2.6.35-31.  And that's what the problem was.  When I boot into the 2.6.32-35, it still says it's 10.10... 

Thanks for the comment... But I still need some help apparently...

:-)
CM
I'm confused by your posts and what problem you are having.... Is it that you are not able to boot and it boots to a blank screen? That is what your title leads to... Does it boot? 

Or is it that it takes longer to boot, as your later posts describe?

If it's a graphics problem, do you know what kind of video card you have? If you can get to a tty session at hang, using <cntrl><alt><F2>. Login then 
```

lspci -vnn | grep VGA

```Either way, if you went to a Recovery grub menu item and boot. A menu will appear with a menu item to boot into safemode graphics... from there you could reinstall graphics drivers. 

From the same menu you could get to a root prompt, which would comfirm that a kernel is booting... And to be able to load your drivers from a CLI.

I never noticed and difference in boot time between 10.04 and 10.10.  If your graphics aren't configure right... there are some additional graphics checks that would cause later drivers to crash slower than the older ones.  Using "text" as a kernel boot option while booting to a TTY text console boot turns all the graphics off, then they boot in the same times. All those kernels use KMS.

So still curious what you "have" as a problem that you need help with.

---

### Post by captain_mills on 2011-12-06
I added my original question to a pre-existing thread so as to not have to start a new thread, but I was unaware that they encourage new threads for each problem here...  I thought to lump my issue in with a similar one, then it was moderated and separated...

When I originally posted my problem, I was unaware that ubuntu would *eventually* load.  After choosing the "ubuntu, with linux 2.6.35-31" option from the grub menu, it goes straight to a black screen with a blinking cursor.  It stays there for 5 minutes now, but I didn't know that originally.  Upon posting, I was shutting down and restarting in safe mode in order to get in.  Now I just wait the 5 minutes plus...

After doing some of my own reading and troubleshooting, I just discovered last night that the "ubuntu, with linux 2.6.32-35" (which is apparently an earlier version of kernel) boots up immediately with no wait time.

What I am now in need of is (1) an explanation of why the earlier kernel boot is immediate whereas the new kernel boot still takes 5 minutes of black screen before loading, *as well as* (2) a solution to the 5-minute boot time on the newer kernel, (3) help understanding the difference in kernel versions and if it will affect my machine if I remove the 2.6.35-31 from the grub menu.

Sorry if I've not been clear enough.  I love working with Ubuntu, compared to anything windows or mac, but I am still noob after a year or so of smooth sailing before this upgrade...

---

### Post by captain_mills on 2011-12-10
Dunno if a BUMP is legal here but...

I still have problems loading my 2.6.35-31 kernel... still takes for ever to load, whereas my 2.6.32-35 kernel loads just fine.  Dunno what will happen if I clean up my grub menu by eliminating the 2.6.35-31 kernel...

help?

---

