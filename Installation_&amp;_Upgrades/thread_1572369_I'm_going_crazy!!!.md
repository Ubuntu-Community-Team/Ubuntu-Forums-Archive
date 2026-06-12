---
title: "I'm going crazy!!!"
date: 2010-09-11
forum: Installation &amp; Upgrades
---

### Post by Odin888 on 2010-09-11
Hello everyone.

I recently tried to install a new hard drive (main boot) into my computer. I had a heck of a time trying to install 10.04 onto the drive. After many failed attempts, I pulled the hard drive and thought maybe I could install 10.04 onto the drive by putting the drive into an external usb case. Ta da it worked. I then thought I could reinstall the drive back into the computer and of course changing the bios, which recognized the hard drive and changed the boot order as well. The computer starts to boot see's everything on start up then a error message pops up NTLDR missing, boot from disk...now what do I do? I do not want to lose everything that is on this drive.

HELP and Thank You
;)

---

### Post by mörgæs on 2010-09-11
I don't have a solution to your problem, just suggesting that giving your thread a meaningful title might help. 

[http://ubuntuforums.org/showthread.php?t=1422475](http://ubuntuforums.org/showthread.php?t=1422475)

---

### Post by coffeecat on 2010-09-11
> **Odin888 said:**
> The computer starts to boot see's everything on start up then a error message pops up NTLDR missing

NTLDR is a Windows bootloader. It sounds as though you still have the Windows mbr in the mbr, but part of grub has been installed to a Windows partition. You didn't say that you originally had Windows on that drive, but clearly you did.

So that we can see exactly what is going on, boot up with the live Desktop CD with the new hard drive still in the computer. Then have a look at this link:

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

Download the boot info script while still in the live session and post the contents of the RESULTS.txt file. **Please**, enclose the file in code tags, otherwise your post will be near unreadable. You can do this most easily by highlighting the pasted text in the forum message field and then clicking on the # icon just above the message field.

By the way. Were you intending to keep Windows in a dual-boot or were you trying to replace Windows with Ubuntu?

---

### Post by Odin888 on 2010-09-13
yup your right! sorry about that. Thank you.

I don't know if you have seen the post I had later...

Thanks again.

---

### Post by Odin888 on 2010-09-13
> **mörgæs said:**
> I don't have a solution to your problem, just suggesting that giving your thread a meaningful title might help. 

[http://ubuntuforums.org/showthread.php?t=1422475](http://ubuntuforums.org/showthread.php?t=1422475)
Hi. Thanks for being so quick. A couple of points. That link has nothing to do with my problem. If I could post the screen image from the initial boot I would. But since I can only boot in the live cd, and run back and forth from my friends house to check forum, I'm out of luck.

I think it may have to do with the file /dev/sda and /dev/sdb. It was originally a external HDD and was used to operate my system, which it did. When I removed it as a usb and tried to install  it as a Master ide, things went amok. My bios does not see it at all as a ide or back as a usb...

Again thanks for being so quick

---

### Post by coffeecat on 2010-09-13
> **Odin888 said:**
> yup your right! sorry about that. Thank you.

I don't know if you have seen the post I had later...

Thanks again.

What are you talking about?

> **Odin888 said:**
> If I could post the screen image from the initial boot I would. But since I can only boot in the live cd, and run back and forth from my friends house to check forum, I'm out of luck.

@Odin, did you even see my earlier post. If you want this problem fixed, post the output from the link I posted.

---

