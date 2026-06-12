---
title: "Serious Help Needed"
date: 2011-05-15
forum: Installation &amp; Upgrades
---

### Post by Joomla12 on 2011-05-15
I just finished upgrading to 11.04 from 10.10. After rebooting my laptop, it brings me to the GRUB menu. After I select what to boot from, it boots in verbose mode with lines saying execution of program '/sbin/modprobe' failed. It then brings me to the BusyBox command line. I really need some help fixing this.

Also, for some reason GRUB 2 was not installed during the upgrade. Would updating it fix this?

---

### Post by Hedgehog1 on 2011-05-15
Greetings!

You are going to need a Natty/11.04 LiveCD/LiveUSB before this is over.  Do you have access to another PC where you can do that?  It is also possible to do from an older LiveCD (download to hard drive, then burn ISO to a CD or make a LiveUSB)

Once you are booted from a **NATTY** LiveCD/LiveUSB, you can start by reinstalling grub2:


Determine what partition holds your Ubuntu root.  In the examples below, they assume that /dev/sd**a5** is your Ubuntu partition.  Yours may be /dev/sd**b5** or /dev/sd**a3** or /dev/sd**b3** or whatever...  Use that.  Also note that your drive MAY be /dev/sd**b**.

In the Terminal (Menu to: Applications >> Accessories >> Terminal):

```
sudo mount /dev/sd**a5** /mnt
```
```
sudo grub-install --root-directory=/mnt /dev/sd**a**
```

***The Hedge***

:KS

---

### Post by ex_isp on 2011-05-15
> **Joomla12 said:**
> I just finished upgrading to 11.04 from 10.10. After rebooting my laptop, it brings me to the GRUB menu. After I select what to boot from, it boots in verbose mode with lines saying execution of program '/sbin/modprobe' failed. It then brings me to the BusyBox command line. I really need some help fixing this.

Also, for some reason GRUB 2 was not installed during the upgrade. Would updating it fix this?

No help but I also, am failing at modprobe.  I have stripped the box of everything un-necessary and still have same error

my thread for reference:[http://ubuntuforums.org/showthread.php?t=1758665](http://ubuntuforums.org/showthread.php?t=1758665)

Seems to be kernal prob with some hardware

---

### Post by Hedgehog1 on 2011-05-15
If the above does not solve the issue entirely, then please do this from you LiveCD/LiveUSB:


[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Follow the instruction on the website and post the results here.

Please press the '#' button when posting and place the the script results between the [noparse]```
 & 
```[/noparse] tags.

***The Hedge***

:KS

---

### Post by Hedgehog1 on 2011-05-15
> **ex_isp said:**
> my thread for reference:[http://ubuntuforums.org/showthread.php?t=1758665](http://ubuntuforums.org/showthread.php?t=1758665)

I don't want to hijack this thread - lets jump back to yours and see if I can help.

See you back there in a sec.

***The Hedge***

:KS

---

### Post by Joomla12 on 2011-05-15
I do have access to another laptop that I can use. I can use fdisk -l to find my partition too. Thanks for the reply. I'll post back with the results.

On a side note, this error came up when booting with an older kernel. [http://www.imgur.com/E8HvJ.jpg](http://www.imgur.com/E8HvJ.jpg)

---

### Post by Hedgehog1 on 2011-05-15
> **Joomla12 said:**
> On a side note, this error came up when booting with an older kernel.

Booting a kernel from a previous release level can yield very unpredictable results.  Sometimes it works ok-enough to get you to where you can fix things.  Sometimes it has errors that the correct kernels don't exhibit.

It is hard to say which one of the categories this error falls into.

***The Hedge***

:KS

---

