---
title: "dualboot vista &amp; ubuntu problem"
date: 2007-05-28
forum: Installation &amp; Upgrades
---

### Post by Grogger on 2007-05-28
I installed ubuntu dapper on my new vaio laptop with Vista preinstalled. I installed ubuntu dapper in the free space and found that vista wasn't listed in the grub boot menu when I rebooted. I attempted to add the first listing to my /boot/grub/menu.lst file with gedit that says: 
"title Windows Vista
root (hd0,1)
makeactive
chainloader +1"

However when I try to boot grub to the new listing I receive an error message:
"Filesystem type unknown, partition type 0x7
makeactive
chainloader +1

Error 13: Invalid or unsupported executable format"

I hope to be able to dual boot vista and ubuntu. 

I have only one 80gb hard drive that is sata. 

I did find out that there is a restore partition that came preinstalled with my vista laptop too. I think this is located at root (hd0,0) in my grub file. I think the regular vista install is in root (hd0,1) but doesn't load properly from grub and then the ubuntu install is located at root (hd0,2).  

Any ideas?  

Thanks!

---

### Post by confused57 on 2007-05-29
You could try rootnoverify (hd0,1)....hope you're not using the quotation marks in your menu.lst Vista entry.

---

### Post by Grogger on 2007-05-29
LoL, no I didn't use the quotation marks.  I did try rootnoverify (hd0,1)  but I still receive the error 13 message.  

I did have a problem when I had first tried to install.  The installation hung up while it was trying to create a partition from the vista partition's free space.  I ended up logging out of ubuntu and then back in (or restarting, I forget) before doing the installation.  I noticed on the second round I couldn't partition manually because ubuntu thought the windows installation was taking up almost all the HD space which wasn't true.  Anyway, I'm still not sure.  ??

---

### Post by Grogger on 2007-06-01
I will try installing Fiesty on the laptop once I get to a place with a broadband connection to download it soon.  I hear Fiesty Fawn has some updated drivers and better support for newer computers.  I might just drop vista from the machine.  I don't like vista at all anyway.  As long as I can eventually get all my hardware working and the codecs I need for music and movies installed I'm happy with ubuntu.  

Thanks for your help.

---

### Post by damufunman on 2007-06-08
I ran into this site last night while trying to figure out if Vista and Ubuntu will run together: [http://techxworld.com/community/blogs/interop/archive/2006/11/05/Dual-booting-Vista-and-Ubuntu.aspx](http://techxworld.com/community/blogs/interop/archive/2006/11/05/Dual-booting-Vista-and-Ubuntu.aspx)
Let us know if this helps.

---

