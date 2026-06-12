---
title: "Inssues booting to 6.06 / and post 5.10 install"
date: 2006-06-16
forum: Installation &amp; Upgrades
---

### Post by thatchmaster on 2006-06-16
PIII 1ghz / 256MB / Dell Optiplex GX110 beater box / 25GB partition for Ubuntu

It was an XP SP1 box.  I burned the ISO for 6.06, booted to it, it loaded almost everything, but when it was about to switch to another screen, it went to a black screen with a solid cursor (frozen).  Let it go 10 minutes just to make sure it was frozen.

Booted back to XP, burned the ISO for 5.10, installed it.  Went thru the full config (I've installed 5.10 on two PPC based systems before), gets to GRUB, loads that fine.  Loads modules and everything else OK, fails on syncing with ntp server, gets to hardware abstraction layer, goes to switch screens, but switches to a black screen with a frozen cursor.  Just like when I tried to originall install 6.06.  

So--with the little infomation provided (sorry I can't get much), anyone have any ideas, or anything I could try?

Thanks in advance,

Erik


edit --- I *can* boot to recovery mode.  Any info that might be useful? I'm wondering now if maybe it just can't display the resolution or something.  On the PPC version, it asked what res's I wanted to allow, but this one did not.  Seems to display anything non-GUI here just fine.  

edit2 -- Not able to startx.  Screen goes blank.

---

### Post by thatchmaster on 2006-06-18
Up.

Anyone?  I'll have more time to troubleshoot tomorrow when I get back to the machine.

Thanks,

Erik

---

### Post by thatchmaster on 2006-06-19
Ran apt-get update and upgrade -- tried startx again, goes to load up, the screen goes blank again.  Rebooted, tried to boot normally, loads everything up, goes to blank screen w/ cursor, after a few seconds, cursor freezes.  

Hopefully, the more info I give here, someone can give me a direction to go.

Thanks,

Erik

---

### Post by thatchmaster on 2006-06-19
Tried to test out glines in /usr/games

```

(glines:6271): Gtk-WARNING **: cannot open display:

```

I'm still relatively new to linux, but I'd assume maybe what's going on here is I don't have all the drivers I need.  Also realized I can't ping anything.  

-Erik

edit-- I **do** have network connectivity.

---

### Post by thatchmaster on 2006-06-19
Well, after creative searching, I figured out the answer.  

(for anyone searching, or that cares) 

Looks like it was because of the onbaord video card.  Basically, switched my card to be seen at pci 1:7:0 instead of the default 0:1:0 , in /etc/X11/xorg.conf (bus locations found by entering "lspci -X", and noting where your card is located) , then running 

sudo dpkg-reconfigure xserver-xorg

Hope that helps anyone else with this problem.

-Erik

---

### Post by Efrain Valles on 2006-09-18
I had the exact problem. I can't boot ubutu. xubuntu or any other flavor in 6.06... I'll try 5.10... I'll try to install 5.10 and see...

---

### Post by Efrain Valles on 2006-09-19
Well I played around it and it still got me. I installed Hoary... I ugraded to Breezy and when all the changes kicked in... I tried to reboot and it got stuck exiting... I went ahead and rebooted manually and it apears as if I lost the changes that were being processed.

 I got the X failing to load error. I am on bash and I have tried configuring...

I am going to do 
apt-get update
apt-get upgrade and see what happens...

---

