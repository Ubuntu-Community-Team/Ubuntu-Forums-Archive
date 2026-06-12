---
title: "Unable to install ubuntu 12 using a USB"
date: 2012-07-04
forum: Installation &amp; Upgrades
---

### Post by gotchanisa on 2012-07-04
I checked existing threads and there's nothing that helped. I'm trying to install ubuntu 12 on a PC. The PC is a P4 with 1 Gb ram. I created a live usb installer and then tried it on my regular PC. it worked fine. But when inserted in the P4, it just comes up to a blank screen with a blinking cursor. 

My CD drive is bust and that is the reason I have to install with a USB.

I then removed the hard disk from the P4 and inserted it in my regular pc. I disconnected the hard drive that I'm using so the only connected hard drive is from the P4. I then go ahead with the install and it successfully installs the Ubuntu OS with the same USB stick.

However on switching back the hard drives, I am stuck on the UBUNTU splash screen that has those 5 dots that perpetually move and nothing happens after that.

I'm a noob when it comes to Ubuntu... so please be gentle:p

P.S. I tried changing the hard drive and also made an XP USB installer just to check if it will load XP. But the same result there too. Black screen with a blinking hyphen. Help!!

---

### Post by dino99 on 2012-07-04
thats let me thinking about an acpi issue; what happen if you boot with noacpi on the boot line (edit the boot line into grub menu, and insert noacpi & remove splash, that way you will see the boot comments)

by the way, you should find usefull warnings/errors logged into .xsession-errors

---

### Post by gotchanisa on 2012-07-04
> **dino99 said:**
> thats let me thinking about an acpi issue; what happen if you boot with noacpi on the boot line (edit the boot line into grub menu, and insert noacpi & remove splash, that way you will see the boot comments)

by the way, you should find usefull warnings/errors logged into .xsession-errors

Thanks Dino... but can you give me detailed instructions or point me to a link. I don't understand anything of what you just said :(

---

### Post by Quackers on 2012-07-04
This thread may help with that
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)

---

### Post by gotchanisa on 2012-07-06
I was able to get to the installed version by defaulting the BIOS.

Now have to figure out why the updates are failing. Even when we try updating through the terminal command.

---

### Post by gotchanisa on 2012-07-15
I'm still facing issues with the computer. I was able to make all the updates necessary but it often comes back with an internal error message. I'm thinking it could be a hardware issue because I faced a similar issue when I tried working with windows. The screen used to just turn off and no amount of moving the mouse would turn the screen back on. Is there a command I could run to find out if all the hardware is running alright? How can I fix this issue?

Thanks in advance!

---

