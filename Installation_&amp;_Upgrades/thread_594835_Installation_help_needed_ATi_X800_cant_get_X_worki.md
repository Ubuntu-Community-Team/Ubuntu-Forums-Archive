---
title: "Installation help needed: ATi X800 cant get X working at all, even with vesa driver"
date: 2007-10-28
forum: Installation &amp; Upgrades
---

### Post by Triptoph on 2007-10-28
Hi there, 

I want to get a linux distro working on my computer as it is a superior programming environment to windows I believe, but I have been working on it for a couple days and haven't had much luck, I hope someone out there can help!

When using the normal ("Live CD"?) installation ISO (64-bit), the splash screen with menu options appears.  If I choose to install normally or in safe mode the same thing happens: screen goes blank, then the monitor shuts off and there is no HDD activity at all.

Using the alternate 64-bit ISO, I can install it alright, and it detects my network connection with DHCP automatically.  Once installed, I can't boot normally (same symptoms as when the normal install CD tries to start X), but recovery mode does work.  

I have searched these forums and others, and found a few articles that led me to reconfigure xorg.conf and try using the vesa driver, however this has no effect on the problem.  Most articles about getting Ati cards to work assume you already can get the GUI up and running in some way or another.  

Another aggrivating issue to add to this mess is that in recovery mode I can't use apt-get because it reports that it can't resolve gb.ubuntu.com, thus i can't download files this way.

**Hardware:**
ATi X800 XL Video Card PCIe (I noticed while reconfiguring xorg.conf that it refers to PCI:1:0:0 or something like that, I assume that's alright and it doesn't need PCIE:1 or something like that...)
Intel quad-core 6600 CPU
4GB RAM
large CRT monitor that supports many resolutions, I doubt the monitor type is related here.
Creative X-Fi Sound Card 

I usually use a dual-head setup with a second monitor but i have unplugged it for now to make things slightly simplier

Although I would really like to use ubuntu as the philosophy and community appeal to me, I tried to install MEPIS to see if that would get around my problems, but shortly after booting with the install CD it got into an infinite loop repeating the same line over and over!  Since this isn't the MEPIS forums i wont go into detail there, but I was pretty surprised at that one.

If you have any idea what might help here, please let me know, I would greatly appreciate any help!  If not, thanks at least for reading this far :)

---

### Post by Triptoph on 2007-10-28
The motherboard is an Asus P5K Deluxe board with the newer P35 chipset, perhaps that is causing some issues too...

---

### Post by Triptoph on 2007-10-29
Got ethernet up and running by reinstalling with alternate CD, unplugging the network cable so that DHCP failed, then plugging it back in and manually configuring it. 

Next tried ATi's driver, fglrx, but that didn't change the blank screen problem.  Maybe this isn't a video driver issue exactly.  What else could cause X to turn off monitors at startup?  

After fglrx was installed, fglrxconfig reported that it couldn't find screen 0... hmm.

Could it be trying to talk to the wrong device?  Or the unused TV Out port on my video card?  That might cause no output to be sent to the main monitors, causing them to turn off.... ?

Anyone have any thoughts? :confused:

---

### Post by bigpetey44 on 2007-10-29
Triptoph, I'm not sure what exactly is causing that to happen, but I can share my experience real quick. I have a Asus mobo with athlon 64 3000+ and had 3 gigs of ram in the board (maxed out, only 3 slots). My pc is a little older but still pretty quick in my opinion.

My motherboard cant handle 3 gigs at ddr 400 (the max for my board). I have ati graphic driver problems installing, install problems like black screen, screen imperfections etc. I couldnt figure out for the hell of me what is was, but them i realized i can only have 2 slots used as ddr400, so i went and pulled one out, and bang everything fell into place. I have a X1650 and it picks up fine and install was smooth. Desktop effects the whole nine work fine.

I had windows and the 3 gigs shows up fine but that doesnt mean a thing because its windows. I still dont know if this information helps or not but after me doing that im just baffled lol. If your willing to try anything see if you just have 2 gigs of ram in there just for testing purposes. I dont know if any of this helps you like i said but if your willing to see whats up give it a shot ... also have you tried setting default bios settings?

---

### Post by big dizzle on 2008-01-14
> **bigpetey44 said:**
> Triptoph, I'm not sure what exactly is causing that to happen, but I can share my experience real quick. I have a Asus mobo with athlon 64 3000+ and had 3 gigs of ram in the board (maxed out, only 3 slots). My pc is a little older but still pretty quick in my opinion.

My motherboard cant handle 3 gigs at ddr 400 (the max for my board). I have ati graphic driver problems installing, install problems like black screen, screen imperfections etc. I couldnt figure out for the hell of me what is was, but them i realized i can only have 2 slots used as ddr400, so i went and pulled one out, and bang everything fell into place. I have a X1650 and it picks up fine and install was smooth. Desktop effects the whole nine work fine.

I had windows and the 3 gigs shows up fine but that doesnt mean a thing because its windows. I still dont know if this information helps or not but after me doing that im just baffled lol. If your willing to try anything see if you just have 2 gigs of ram in there just for testing purposes. I dont know if any of this helps you like i said but if your willing to see whats up give it a shot ... also have you tried setting default bios settings?

you can tell from my hardware list on my signature that you and i have close to the same setup and i have been getting a lot of the same problems that you are reporting (black screen while booting when trying to use default ATI driver, etc...).  I will give this a try and report my results.  hope this works :)

---

### Post by big dizzle on 2008-01-14
> **big dizzle said:**
> you can tell from my hardware list on my signature that you and i have close to the same setup and i have been getting a lot of the same problems that you are reporting (black screen while booting when trying to use default ATI driver, etc...).  I will give this a try and report my results.  hope this works :)

didn't work :(

plz let me know if you have any more suggestions, post on the other thread i started if you don't mind...

[http://ubuntuforums.org/showthread.php?t=662401](http://ubuntuforums.org/showthread.php?t=662401)

thnx

---

### Post by squalho on 2008-01-14
Hello,
I was experiencing your same problem, then I found a tool (thanks Chiappo!) that solved everything.
It is called Envy, and this is the URL: [http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

If you can access the console by CTRL+ALT+F1 you can easily get the deb file with wget.
After you install it with the normal sudo dpkg -i.

Run the program with Envy -t and just choose your graphic adapter.

It works!!!!

Vittorio

---

### Post by Triptoph on 2008-01-14
I tried envy a number of times with no success unfortunately, hope it works better for the others with this problem!  I worked on this for a few days straight and although I did once reach a working configuration, it involved having two desktops which is not what I wanted as I like to be able to move windows between the two monitors.

In the end I decided my time was more valuable and bought a nVidia card that worked fine from the get-go!  The Ati X800XL is now collecting dust.

---

### Post by big dizzle on 2008-01-15
I also tried envy multiple times to no avail.  I think I am going to sell my graphics card on eBay to some poor windows user and buy an nVidia card.

---

