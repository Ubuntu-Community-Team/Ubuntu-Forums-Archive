---
title: "Ubuntu Mini doesnt automatically boot to tty1 on boot"
date: 2016-10-14
forum: Installation &amp; Upgrades
---

### Post by Peter_Darbyshire on 2016-10-14
Hi,

I have just installed Ubuntu mini 16.04 onto my laptop and it doesnt boot to tty1 when i boot up.

It is stalling on a message saying /etc/sda2 Clean (I think not infront of the laptop atm)
When i press Ctrl Alt F2 it goes to tty2 then Ctrl Alt F1 it goes to tty1 but the writing is in yellow if that helps

Thanks

---

### Post by sudodus on 2016-10-14
Yes, I have noticed this behaviour.

- Is it the 32-bit or the 64-bit version?

- How do you intend to use the computer?

- Have you tried to create the corresponding system from the Ubuntu Server iso file? It can create a mini system that is very similar, but maybe without this peculiar behaviour.

---

### Post by Peter_Darbyshire on 2016-10-14
Hi, Thanks for the reply

- My machine is 64-bit
- I intend to build a openbox machine from ground up so atm a few more keys wont be to bad. I was just wondering if there was a fix.
- I havent tried a server iso yet. Would this affect anything i am doing regarding using the computer as a normal desktop?

Thanks

---

### Post by sudodus on 2016-10-14
I have used both the mini.iso and the server.iso for the same purpose, and the difference is hard to detect (of course you should not install server packages if you want a pure desktop system). But I do think that the mini system made by ubuntu server is not affected by your problem.

On the other hand, if you want a graphical system based on openbox, the problem you have now will disappear, because I suppose that you will log in to a graphical session manager, for example lightdm.

You can also use the shortcut described at the following link: [Installation/UEFI-and-BIOS](https://help.ubuntu.com/community/Installation/UEFI-and-BIOS), where you get an installed system directly from a compressed image file. That system will be portable between PC computers with 64-bit hardware.

---

### Post by Peter_Darbyshire on 2016-10-15
Update:
Used ubuntu server 16.04.
Issue has gone and built a very well working system :).

Now to figure out how to auto start startx when i log into tty1 so i dont need a login manager

---

### Post by sudodus on 2016-10-15
Have you tried putting startx at the end of your .bashrc file?

---

