---
title: "help install from IPOD or any usb device"
date: 2005-07-11
forum: Installation &amp; Upgrades
---

### Post by burnhamd on 2005-07-11
Hey guys I ran out of cdrs and was thinking of creative ways to install ubuntu.  I was wondering if I could put the contents of the ubuntu iso on my ipod and use that as a replacement to installation from my CD.(I want to install it to my harddrive not on my Ipod).  I thought maybe I could reformat my ipod then put the boot stuff on there but I dont know if this will work any help will be appreciated.

---

### Post by ravagilli on 2005-07-12
technically you could do this, but you'd have to change the formatting on your ipod, from say e.g fat 32 or ntfs, whatever it is. Thus loosing everthing on your ipod (so back it up). Then you'd have to make it bootable, and your motherboard would have to be able to boot from usb device, to be able to install ubuntu from your ipod. Don't really know much about this sort of thing but i have been reading about installing linux on a usb pen drive, and it seems quite complicated! any way hope this helps you a tiny bit, until someone with more knowledge can help you.

---

### Post by mp3guy on 2005-07-12
and you'd have to then repair the Ipod filesystem for use again, its not like a standard flash disk.

---

### Post by burnhamd on 2005-07-12
First of all before I even tried to put linux on there I would leave the plugged in on accident after I shut down my computer.  When I was booting with the Ipod plugged in it would say boot sequence has been changed and I pressed the continue just for fun and it would have a bunch or characters fly down the screen and it would just stay that way.  So I figured it was the I pod boot thingy trying to boot up on my pc.  Thats where the thought of booting from the Ipod came from.
So I tried deleting all of the partions on my Ipod (one for firmware and one for music) then I formatted one fat16 partion.  And I unplugged my Ipod just to see what I had done and the Ipod boot manager(I guess) came up and gave me a warning sign. So I plugged the Ipod back in my pc and restarted the computer.  hen the pc came to the booting point it gave me the same flying text.  Im was wondering if it had something with the mbr of the Ipod.  I looked at the ipod linux project and they have their own boot loader that you(from my understanding) put together with the Ipod loader and it boots either linux or Ipod firmware.  But im new at this boot stuff and dont know how to mess with the mbr.  If I could somehow get a bootable floppy image formatted on my Ipod I might be able to do it but I dont know how to do that.  I asked the guys at the Ipodlinux project but no repy yet.

Any ideas guys.

---

