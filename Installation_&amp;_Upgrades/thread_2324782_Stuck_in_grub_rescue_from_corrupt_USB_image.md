---
title: "Stuck in grub rescue from corrupt USB image"
date: 2016-05-16
forum: Installation &amp; Upgrades
---

### Post by Lanin on 2016-05-16
Hi, I was going to give Ubuntu a go so I made a USB boot disk booted it up selected live and it preceded to tell me "XZ-compressed data is corrupt" .  Now when I boot up I go straight to grub recovery. I have tried several commands such as 
set root=(hd0,6) 
Set prefix=(hd0,6)/boot/grub 

and so on. 
Using ls command ive looked at the partitions and tried booting from every option including the USB.  I can't get into grub 2 by holding shift on boot either.  I don't have any recovery media I upgraded to Windows 10 and was 7 oem before that.  I don't have access to any other computers currently either.  I apologise for not giving a more comprehensive list of what I have tried I have spent the last 3 hours trying things and I'm on my phone so it's not easy to retrace exactly what commands I've used. And command involving a hd comes back not found. I'm new to Ubuntu so its a pain sorry

---

### Post by yancek on 2016-05-16
After creating a bootable usb (how exactly did you do this) you tried booting it and got the error message "XZ-compressed data is corrupt".  You got this when you simply booted the usb, is that correct?   Now when you boot you go to Grub recovery, when you boot what?  The usb drive?  From your hard drive?  What's installed on your hard drive?

Did you verify the download with an md5 checksum?  Do you have another computer on which you can try to boot the usb to verify that creating the bootable usb was successful?

---

