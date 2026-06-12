---
title: "Why does the grub screen come up now?"
date: 2011-05-08
forum: Installation &amp; Upgrades
---

### Post by GEOvanne on 2011-05-08
Yesterday I installed ubuntu on my slave drive. Windows, on the primary, had a virus I and couldn't get into it.

This morning I went into ubuntu and started copying files from the windows drive, then I shut down and left.
When I came back and tried to go into ubuntu the grub thing came up and showed that windows was now available (:confused:). It also showed ubuntu kernel 2.6.20-25 generic and when I go into that its all command line. Also, it said some thing about enabling nx capabilities.

When I select the windows option it booted up windows.

Is there a way to get back into ubuntu or do I have to reinstall it?

---

### Post by zvacet on 2011-05-08
You may try to reinstall grub following [these]("http://ubuntuforums.org/showthread.php?t=224351") instructions and see if it helps.Did you thinking about upgrading to 10.04,because I think that support for Hardy ends.

---

### Post by 73ckn797 on 2011-05-08
Boot from the live CD and choose to try Ubuntu. I believe that you can then run in a terminal: ```
sudo update-grub
``` That may easily correct things.

---

### Post by GEOvanne on 2011-05-08
Ok, so before I try what you said here is what happened when I tried again:

I can still access windows.

I get to choose Linux 2.6.35-28-generic or 2.6.35-22-generic
When I select either one of them, the ubuntu loading screen comes up and it stops there.


What i really want to happen is for windows to boot up normally when the computer is turned on, and if I want to use ubuntu I press F8 and select it from the boot up menu.



Edit.
Ok so I tried what you said and it wont work.

When I try sudo update-grub I get : error:cannot find a device for / (is /dev mounted?)

And when I try sudo grub (from the link) I get : command not found



Before I installed yesterday I plugged out the windows drive, do I have to install with both drives plugged in?

---

### Post by 73ckn797 on 2011-05-08
> **GEOvanne said:**
> Ok, so before I try what you said here is what happened when I tried again:

I can still access windows.

I get to choose Linux 2.6.35-28-generic or 2.6.35-22-generic
When I select either one of them, the ubuntu loading screen comes up and it stops there.


What i really want to happen is for windows to boot up normally when the computer is turned on, and if I want to use ubuntu I press F8 and select it from the boot up menu.



Edit.
Ok so I tried what you said and it wont work.

When I try sudo update-grub I get : error:cannot find a device for / (is /dev mounted?)

And when I try sudo grub (from the link) I get : command not found



Before I installed yesterday I plugged out the windows drive, do I have to install with both drives plugged in?

Is the problem happening when you select the Ubuntu drive to boot from? Is the Ubuntu choice on the windows boot screen?

You can fix the Windows boot MBR and also reinstall Grub to the Ubuntu drive. It sounds like you have tried the Grub reinstall.

---

### Post by GEOvanne on 2011-05-08
> **73ckn797 said:**
> Is the problem happening when you select the Ubuntu drive to boot from? Is the Ubuntu choice on the windows boot screen?

You can fix the Windows boot MBR and also reinstall Grub to the Ubuntu drive. It sounds like you have tried the Grub reinstall.


Windows had a boot problem so I couldn't normally access it. Grub allows me to get to it, but now I cant go into ubuntu.

At start I pressed F8 to get boot options and selected ubuntu drive, then grub comes up.

---

### Post by 73ckn797 on 2011-05-09
What version of Ubuntu are you using?

---

