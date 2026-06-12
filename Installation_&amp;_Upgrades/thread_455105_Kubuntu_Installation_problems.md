---
title: "Kubuntu Installation problems"
date: 2007-05-26
forum: Installation &amp; Upgrades
---

### Post by twidget on 2007-05-26
Hi
for some reason i'm haveing trouble getting a Kubuntu install to work right
System stats:
sy-k7vme motherboard with onboard video
athlon xp 2500
512Mb  RAM
nVidia mx 440
Viewsonic 27" lcd
Airlink wireless card (atheros chipset)
I tried installing feisty but \the install hung without a network connection so i moved the pc to a place with ethernet. because of this i had to use an older 15" monitor and a dvi->vga converter during install..everything went fine except that once i moved the computer back to my 27" i didnt get the nVidia splash anymore and kaffeine played some AVI's on only half the screen.also the wireless was flaky. I got frustrated so i took it to work with me and installed edgy instead. install went fine except now i have no sound.installed nvidia drivers using adept and followed the procedure here: [http://doc.gwos.org/index.php/Latest_Nvidia_Edgy](http://doc.gwos.org/index.php/Latest_Nvidia_Edgy)
this completely killed my xserver. i went into grub and booted the next lower version of kernel. got a corrupted but viewable nvidia splash and everything worked except sound.
i then commented out the lines that i changed in the how-to and removed the nvidia drivers and then ran dpkg-reconfigure xserver-xorg. this got my xserver back but now wireless lan assistant and network settings both tell me i have no wireless card. lspci on the other hand says i have an atheros card.
while going through the dpkg-reconfigure i noticed that the graphics adapter section says something like PCI:1:0:0 or something of that sort. so my current theory is that linux is still trying to use the onboard video instead of my AGP card. lspci says my agp card is at 01:00.0 so i tried entering AGP:01:00.0 but dpkg wont let me do that.
so the question is can aybody give me advice on how to fix any of this or should i try and re-install yet again? Is there a way that i can install Kubuntu and have everything work without needing a wired connection to the internet?
thanks for your time.

---

### Post by meshellwm on 2007-11-11
Hi,

I also had a problem upgrading to kubuntu 7.10.

First, I tried to upgrade from within kubunto 7.04 but I had some glitch. Then I tried 7.10 and it would not connect to my wireless network. I reinstalled 7.04, which hangs until you click on the network icon and select a wireless network -- I nearly missed it the first time! I got 7.04 to install then followed the upgrade instructions. I successfully upgraded to 7.10, but I still had no network. I'll probably use another distro for now.

I've documented a few things here:

[http://home.earthlink.net/~meshellwg/w/www/html/linux.html](http://home.earthlink.net/~meshellwg/w/www/html/linux.html)

I would still like to install kubuntu if anyone can resolve the networking issues...

---

