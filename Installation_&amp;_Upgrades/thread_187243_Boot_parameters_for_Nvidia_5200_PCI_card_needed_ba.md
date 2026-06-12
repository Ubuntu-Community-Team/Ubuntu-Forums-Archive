---
title: "Boot parameters for Nvidia 5200 PCI card needed badly"
date: 2006-06-02
forum: Installation &amp; Upgrades
---

### Post by Sgood1971 on 2006-06-02
Hi all, 

Trying to install 6.06 on a PC that has an Nvidia 5200 PCI graphics card. I am using the live/install cd. It starts out nicely and continues well until x tries to start. Then the screen gets garbled and you can see a partial message that says "Failed to start X server...unreadable stuff...Would you like to see the output of...more unreadable stuff.." I am dropped to a prompt that is halfway across the screen. I know that I can add boot parameters to it and get around some problems. For instance on my laptop I had to do...
```
live vga=771
```
I just need a way to tell it that I have a PCI card and not an AGP.

Any Help appreciated greatly, thanks in advance.

---

### Post by Beck on 2006-06-03
[QUOTE=Sgood1971]Hi all, 

Trying to install 6.06 on a PC that has an Nvidia 5200 PCI graphics card. I am using the live/install cd. It starts out nicely and continues well until x tries to start. Then the screen gets garbled and you can see a partial message that says "Failed to start X server...unreadable stuff...Would you like to see the output of...more unreadable stuff.." I am dropped to a prompt that is halfway across the screen. I know that I can add boot parameters to it and get around some problems. For instance on my laptop I had to do...
```
live vga=771
```
I just need a way to tell it that I have a PCI card and not an AGP.

Any Help appreciated greatly, thanks in advance.[/QUOTE]
I have a 9100 PCI, and I have the same problem :(.  I've yet to see one version of Ubuntu(I've tried since 4.10) that works with my graphics card.  I've had to disable it in the bios everytime to get it to work.

Someone please help with a workaround.

ATI Radeon 9100 PC 128mb = Will not boot.

---

### Post by tseliot on 2006-06-03
setting the driver to vesa might solve the problem.

I need to see if I find the right cheat code for Dapper's livecd

---

### Post by Sgood1971 on 2006-06-03
[QUOTE=Beck]I've had to disable it in the bios everytime to get it to work.[/QUOTE]

I had to do that when I put Mepis on this machine. I was hoping to avoid it, but that's what I ended up doing. I disabled it in the BIOS, Installed using the integrated card, and now I'm in the process of installing the Nvidia drivers. 

[QUOTE=tseliot]setting the driver to vesa might solve the problem.

I need to see if I find the right cheat code for Dapper's livecd[/QUOTE]

I had already thrown in the towel by the time I saw your reply and installed on the integrated card. I will definately try it next time. I checked out the sites in your sig and found your envy script. That is very cool. Will it work with my 5200 PCI card?

---

### Post by skelooth on 2006-06-03
this prolly doesn't help much, but...

I have a NVidia 5200 fx PCI and it's always worked right out of the box. I had some issues upgrading though, and I had to run dpkg-reconfigure xserver-xorg then I had to manually change the driver back to nv

---

### Post by Beck on 2006-06-27
Still have yet to get my PCI Radeon 9100 to work :(.

---

### Post by tseliot on 2006-06-28
[QUOTE=Beck]Still have yet to get my PCI Radeon 9100 to work :(.[/QUOTE]
Use the Safe Mode from the livecd menu as soon as it boots

---

