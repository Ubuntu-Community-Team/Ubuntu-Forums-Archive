---
title: "Where's menu.lst  IN UNR??"
date: 2009-07-05
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by Done_Fishin on 2009-07-05
I have a non apci compatable laptop that I was trying to install UNR on. I say "was" because after learning how to boot the damn thing without crashing (overheating CPU) I then came to the point that i needed to add acpi=off to the start-up config and I couldn't find the well publicised file menu.lst that one should modify for these changes. I reverted to Super OS 9.04 where I had the problem of adding "options psmouse proto=imps" which was required for my touchpad. It was working in 8.10 yet not in 9.04 and I then learnt that it was functional in 9.10.
I am setting this up for someone who is totally PC ignorant because the old HDD failed taking with it the restore partition for XP Home .. and XP Home now re-installed sits there beeping at me!!

I want to install this to my external 20GB USB connected laptop hard drive so that I have the option of showing him how it functions before installing in place of Windows. UNR for this purpose would be great if I could only modify the start up to incorporate acpi=off.

so please anyone .. can you point me at the right place to find the file?? I did find grub.cfg but it says NOT to modify the file ..

---

### Post by ronacc on 2009-07-05
if you are trying to boot 9.10 alpha2  see the grub2 threads in this forum .

---

### Post by Done_Fishin on 2009-07-05
Does 9.10 come with default grub2 .. thought it was to go that way with the official release.
I'll browse around. Thanks

---

### Post by Done_Fishin on 2009-07-05
Problem solved 

menu.lst has been replaced by grub.cfg .. something I suspected but couldn't prove easily.

> **Done_Fishin said:**
> [QUOTE=jerrylamos;7539508]If you do a 
ls -l /boot/grub/grub.cfg
you'll see it is marked as
-r--r--r--
which is read only.  Every time Grub2 updates the file it changes its permissions into read only.

What you do is
sudo chmod 644 /boot/grub/grub.cfg
which changes the permissions to
-rw-r--r--r--
so you can do a 
sudo gedit /boot/grub/grub.cfg.

Good luck.  I've had some limited success in changing grub.cfg without fouling myself up altogether.

I find Grub2 A WHOLE LOT MORE UNFRIENDLY AND MORE COMPLICATED than Grub which is no gem itself.  I assume there's a reason for Grub2?  I haven't looked into what advantages it may have.

Jerry


I have no idea as to whether I am using grub2 but I did manage to modify my grub.cfg using the information above to add acpi=off, from within the UNR Live CD installation.
Carefully using the "CD" command to get to my installation on the hard drive and then down to /boot/grub/grub.cfg I made it rw, modified it saved it and then rebooted into the USB install. I found that I didn't need to change it again since the properties remained set as per the previous edit. Because it was done via the Live CD ?? Don't know!!

but it was a great help having the info above to guide me through that hassle of making the file writable .. I had been tearing at my hair trying to find out why I couldn't do it! Mustt have re-installed UNR 5 or 6 times over the last 24 hours looking for various workarounds ):P):P
[/QUOTE]

---

