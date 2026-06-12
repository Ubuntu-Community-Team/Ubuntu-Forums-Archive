---
title: "INstallining dapper screen resolution."
date: 2006-07-06
forum: Installation &amp; Upgrades
---

### Post by Compucore on 2006-07-06
When I had received my dapper drake CD's last friday. I was trying to install Dapper drake 6.06 onto my Aptiva 2158-281 computer. The problem that I am having is this. When I go into boot and install for it. I eventually get to the point where I have my splash screen and desktop that comes up. Problem is that my old monitor that I am using for it. only accepts maximum of 800X600 resolution at 24 or 32 bit. Now what I had tried to do even at the menu setup for Dapper drake where you have f1 for this option. F2 for language, F3 for screen resolutions, Etcs. I tried telling it that I have a 800X600 that way and went with the install and I had tried manually trying to insert the resolution so I could see the splash and desktop when it finally boots up so I could install it in. Both times it has failed to bring the resolution down. ANd I am at a loss of where to go in order to make the changes. Since it is extremely difficult to view the desktop when the screen is mashed up and not really viewable. Is there a way around this that I could pass the valuts for it so I could see the screen properly on thedesktop. There is now way of going back into text mode to even do the installation of this version?

Compucore

---

### Post by cacharreo on 2006-07-06
sudo dpkg-reconfigure xserver-xorg

---

### Post by nab on 2006-07-06
If I understand you right, your setup for the console is ok.

So switch to a console with e.g. Crtl + Alt + F1

login and start following script to manually configure your XServer:

>  sudo dpkg-reconfigure xserver-xorg

At e.g. [http://www.mepislovers-wiki.org/index.php?title=Dpkg-reconfigure_xserver-xorg]("http://www.mepislovers-wiki.org/index.php?title=Dpkg-reconfigure_xserver-xorg") you find more information on this scripts.

Hope this points you in the right direction.

---

### Post by Compucore on 2006-07-06
Okay I think we are getting confused here. So before we go any further we'll try this over and make sure that we are on all on the same page here. And I'll retry and explain it here. Thank god for second pc here and here is what I want to do. I canview the other screen and rewrite the menu onto this one to show you.OKay What I did is this and I will explain as best as possible here. 

What I did is this, I powered up the old aptiva, and inserted Dapper into the cdrom drive and closed it. Dapper starts to load and comes up with this menu system. 

Start or install Ubuntu
Start ubuntu in safe Graphical mode 
Check CD for defects
Memory test
Boot from first hard disk

**F1** Help **F2** Language **F3** Keymaps** F4** VGA **F5** Accessibility **F6** Other options

I get this screen on boot up from the cdrom itself to choose from. What I need to do is to have it boot in the screen Mode of 800 X 600 24. I had highlighted F4 to bring the resolution to that so I could see the GUI of GNome once I was in ubuntu. I keep the highlighted text of start or install ubuntu. And hit the enter or return to procced. THe computer then goes into grub to boot into linux and starts loading. When I get to GNome instead of seeing Gnome in the 800 X600 resolution it had stay in 1024 X768 and I cannot see that resolution. And it is extremely hard to view anything at that resolution since my monitor cannot handle it. ANd becomes all garbled to view.

Just from this menu alone I cannot view gnome properly to make a proper install dapper on my Aptiva. I could make any adjustsments here to try and get it to a lower resolution but it is a no go. This is where I am stuck at with dapper on my older computer. On my Dell GX150 I have no problems since the monitor can handle up to 1600X1200. So it was not a big deal.

Compucore

---

