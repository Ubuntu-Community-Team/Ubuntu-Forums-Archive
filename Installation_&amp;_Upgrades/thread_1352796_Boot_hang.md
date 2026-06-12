---
title: "Boot hang"
date: 2009-12-12
forum: Installation &amp; Upgrades
---

### Post by vanv101 on 2009-12-12
My ubuntu laptop is having some issues.  System: Dell e1505 with ubuntu 9.10. 
Last night I installed the newest kernel and when I rebooted it won't go past the bios.  Right at the time when grub normally shows up I get a blank screen with a blinking "_" at the top left of the screen and it just sits there.  I've browsed the forum with no luck. 

 I tried the fix on the [http://ubuntuforums.org/showthread.php?t=1352731](http://ubuntuforums.org/showthread.php?t=1352731) post and it didn't work. 
 I've also tried deleting the new kernel, and then rebuilding grub, but it doesn't work still.

When I rebooted I noticed my dell has an option to press F12 to pick a boot device.  I pressed it and selected my internal hd.  Grub then proceeded to load like normal and I could select the kernel and boot up ubuntu. (I'm writing this post on the problem pc)  

I'm confused on what my problem actually is and how to fix it.  Any help would be greatly appreciated!

This happened after installing the 2.6.31-16 kernel...

---

### Post by Tmi on 2009-12-12
Not that I have a solution, but just wanted to confirm this problem. 
My computer also freezes with a blank screen with a blinking _. After a reboot grub loads again and I get into Ubuntu.

At the next boot this happened again and once more rebooting worked. I guess this might be some general problem so hopefully they'll fix it soon. I can manage by rebooting once until they do :P

Edit: I think a "sudo update-grub2" solved it for me.

---

