---
title: "Live CD freezes"
date: 2006-04-29
forum: Installation &amp; Upgrades
---

### Post by markkerr on 2006-04-29
I am trying to use the Live CD on an older system.

MB= Asus me-99vm
Celeron 400
128 Megs memory
Built-in SiS® Super 2D/3D AGP VGA 
Crystal® PCI Audio with AC' 97 CODEC 
1.6 Gig HD with win95
4.3 Gig HD empty

When The desktop appears I nothing works. The mouse locks up
intermittently. When I click on the system or applications tab nothing
happens. I know this system is slow, I will upgrade to 256 megs of memory 
on Monday if you think it would help.

I ran the disk in my other computer:

Pentium 4 (2.4 gHz) with 512 memory and it ran great. I would install Ubuntu
on the newer system but I am paranoid of losing data. If I did install on the newer system could I dual boot from a 2nd HDD set to slave on the primary?

---

### Post by deadgobby on 2006-04-30
[QUOTE=markkerr]I am trying to use the Live CD on an older system.

MB= Asus me-99vm
Celeron 400
128 Megs memory
Built-in SiS® Super 2D/3D AGP VGA 
Crystal® PCI Audio with AC' 97 CODEC 
1.6 Gig HD with win95
4.3 Gig HD empty

When The desktop appears I nothing works. The mouse locks up
intermittently. When I click on the system or applications tab nothing
happens. I know this system is slow, I will upgrade to 256 megs of memory 
on Monday if you think it would help.

I ran the disk in my other computer:

Pentium 4 (2.4 gHz) with 512 memory and it ran great. I would install Ubuntu
on the newer system but I am paranoid of losing data. If I did install on the newer system could I dual boot from a 2nd HDD set to slave on the primary?[/QUOTE]

Yes you can do a dual partition or dual boot. 
[http://ubuntuguide.org](http://ubuntuguide.org)

---

### Post by rhomp2002 on 2006-04-30
I got the live CD's from Canonical.  When I tried to run the Live CD on a 32 bit addressing version, the initial boot worked fine but when it came to the install it checked for the CD Rom, found it and then when it went to start the install it said it could not find the CD Rom.  It had just found it.  Makes no sense.  I thought maybe it was just a bad CD so I tried 4 more of the 10 CD's Canonical sent and the same thing happened with all of them.

I then tried the 64 bit addressing version and it went farther but when it came time to install the printer it screwed up.  It found my HP Officejet Pro K550 just fine but when it came time to load the driver it loaded and then said it found a HP 1150 and wouldn't recognize the printer.  The driver is the same for both the printers but won't work for mine.  

BTW I installed the MEPIS Linux version which called for the same driver and it worked great.  I am looking to the Ubuntu because I want to move to the 64 bit addressing capability of my computer and MEPIS does not currently support that addressing.  

Both problems happened with the Live CD's furnished by Canonical.  I have no idea where to go with this next.  It recognizes everything up to a point and then stops recognizing what it just recognized.  Very strange.

---

### Post by deadgobby on 2006-04-30
[http://ubuntuforums.org/showthread.php?t=150806&highlight=installing+x64](http://ubuntuforums.org/showthread.php?t=150806&highlight=installing+x64)

---

### Post by markkerr on 2006-04-30
Thanks for the replies, but can you tell me why my Celeron 400 freezes when I get to the desktop? do I have enough ram? Is Ubuntu posibbly having a problem with my MB's built in video? Is there a work around for the problem?

thanks

---

### Post by Mustard on 2006-04-30
[QUOTE=markkerr]Thanks for the replies, but can you tell me why my Celeron 400 freezes when I get to the desktop? do I have enough ram? Is Ubuntu posibbly having a problem with my MB's built in video? Is there a work around for the problem?

thanks[/QUOTE]

I assume this is a fairly old machine?  Celeron 400 sounds like a pretty old CPU.

---

### Post by markkerr on 2006-04-30
Yes, the machine is six years old. My friend had it in his closet for the last
three years. He gave it to me and I revived it. I would love to load Ubuntu
on the machine if I can.

Thanks!

---

### Post by Mustard on 2006-04-30
It might be worth configuring it to use 'vesa' generic drivers to see how it goes.  I can't imagine that gnome will run too well with that particular CPU and RAM, but I don't think that problem should cause it to lock up.  I would think it would just run very slowly.  Ideally you would want to run a more lightweight desktop environment, like XFCE on an older system like that.  Its possible to install XFCE from the install disk.  Instructions for doing so exist on this forum (somewhere).

Can you get to a terminal at the login prompt, by using ctrl + alt + f1 ?

Try this command if you can..

```
sudo dpkg-reconfigure xserver-xorg
```

Pick the 'vesa' drivers and give it a go..

To restart the X server try this..

```
startx
```

or

```
sudo /etc/init.d/gdm restart
```

---

