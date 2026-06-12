---
title: "Dell Latitude D800 freezes randomly during install and live cd"
date: 2013-05-15
forum: Installation &amp; Upgrades
---

### Post by rveach on 2013-05-15
I am trying to install Ubuntu on a Dell Latitude D800 laptop.
It has a 60 gig HD, 512 megs of RAM, 1.6 ghz intel pentium m (32 bit), and requires a non-pae linux distro.
It  currently has Windows XP SP3 on it and works with no issues, but I  wanted to install linux on it (erase windows) to see if I could get  better stability and to try various programs it has.
Everytime I try  to install linux or run a live cd/dvd, the OS 'freezes' seconds/minutes  in to doing anything and at random spots. The mouse still works, but  clicking and the keyboard does nothing. I have tried waiting and nothing  changed. Windows does not have this issue. It may get random blue  screens occasionally, but I can leave it on for weeks with no issues.

I have tried Ubuntu 11.1 DVD, some netboot ubuntu install, and xubuntu 12.04. They all have displayed the same issue.

What can I do to get ubuntu or any linux to work on it? Is there another distro better suited for this laptop?
Thanks in advance.

---

### Post by mörgæs on 2013-05-16
If you don't get an explicit message about PAE this is not the problem. 

Can you run memtest from the boot menu?

Have you tried an [alternate install]("http://cdimages.ubuntu.com/xubuntu/releases/precise/release/"), preferably from a USB stick?

---

### Post by rveach on 2013-05-16
> **mörgæs said:**
> If you don't get an explicit message about PAE this is not the problem. 

I get an explicit message about PAE. I didn't even know what it was till I saw the error message when trying to run ubuntu 12.04.

> **mörgæs said:**
>  Can you run memtest from the boot menu?

Have you tried an [alternate install]("http://cdimages.ubuntu.com/xubuntu/releases/precise/release/"), preferably from a USB stick?

It is 46 minutes in, says Pass 100% on the top right, but the bottom says pass 1, errors 144.
Test 5 is listed the most on the bottom, then it lists 1 test 6. Do you need more information?
I couldn't get it to scroll to see what else was there. The scroll lock didn't do anything.

Does this mean my memory is bad and is preventing linux from working correctly? How come this doesn't stop Windows?

I have not tried the USB stick, but I don't see how it is any different from a cd unless my cd reader is dying too, which I kind of doubt.
If you think I should still try the USB stick, then I'll give it a go later tonight.

---

### Post by mörgæs on 2013-05-16
I would swap the memory before continuing. As fas as I know the D800 uses ordinary DDR memory which should be easy to find. 

Buntu and XP could be using different areas of memory, which might explain why you don't see the same kind of errors.

In general a USB install is the safe way, but with bad memory blocks I don't think it matters.

---

### Post by rveach on 2013-05-30
I finally got new memory (1 gig) and installed it and removed the old memory.
The memtest said it was clean, but I am still experiencing freezes during live and installation. I did get the netboot to fully install and had a working Ubuntu for a bit. It was a console only version, so I decided to install the "ubuntu-desktop" and on reboot I saw the mouse cursor and then it froze on me.
So maybe my bug is related to the graphics, which might explain why anything graphic related looks "corrupted" (mouse cursor has an echo, random pixel coloring, etc). I tried playing with the "vga=" option but didn't have any success. All the ones I tried seem to just give me the exact same display.

---

### Post by mörgæs on 2013-05-31
How does it work in a lighter desktop, say Xubuntu? Ubuntu (that is, Unity) is too heavy for an almost ten years old computer.

If you want to experiment with different [PAE]("https://help.ubuntu.com/community/PAE") workarounds here's a guide I wrote.

---

### Post by rveach on 2013-05-31
> **mörgæs said:**
> How does it work in a lighter desktop, say Xubuntu?

i retried the Xubuntu 12.04 live CD, and I got the same problems (corrupted looking screen and eventually freezing).

> **mörgæs said:**
>  If you want to experiment with different [PAE]("https://help.ubuntu.com/community/PAE") workarounds here's a guide I wrote.

Since Xubuntu didn't work either, do you still want me to try your guide? Since console mode looked and worked nice (for an hour while I installed  the gui) until I switched to the gui, doesn't this point to the issue  being an incorrect graphic setting or something related?

How can I install a desktop gui but not have it automatically load every reboot? Unless I can keep going back to console mode which is usable, it will always go to the gui and stall, preventing me from uninstalling it or trying other methods.

---

### Post by mörgæs on 2013-06-01
Have you tried 

```
sudo apt-get install lubuntu-desktop
```

? It will give you the choice between Ubuntu (Unity) and Lubuntu (LXDE) at boot time. If that does not work I'm out of ideas, sorry.

---

### Post by sudodus on 2013-06-01
> **rveach said:**
> i retried the Xubuntu 12.04 live CD, and I got the same problems (corrupted looking screen and eventually freezing).

Since Xubuntu didn't work either, do you still want me to try your guide? Since console mode looked and worked nice (for an hour while I installed  the gui) until I switched to the gui, doesn't this point to the issue  being an[COLOR=#ff0000] incorrect graphic setting or something related[/COLOR]?

How can I install a desktop gui but not have it automatically load every reboot? Unless I can keep going back to console mode which is usable, it will always go to the gui and stall, preventing me from uninstalling it or trying other methods.

Yes, it is likely a problem related to graphics, now that you have good size and good quality RAM.

- What is the graphics chip?

- Try some or several boot options, See [this link]("https://help.ubuntu.com/community/BootOptions") (and link from it at the end of the web page)

- After discussing the graphics chip and graphics drivers, maybe you should try a proprietary driver

I suggest that you stay with the Xubuntu 12.04 live CD until these things are resolved.

-o-

*Edit*: Later on you can try [PAE by mörgæs]("https://help.ubuntu.com/community/PAE") or [Lubuntu-fake-PAE]("https://help.ubuntu.com/community/Lubuntu-fake-PAE") and try a new version of an Ubuntu flavour, Xubuntu or Lubuntu.

---

### Post by rveach on 2013-06-02
> **sudodus said:**
> Yes, it is likely a problem related to graphics, now that you have good size and good quality RAM.

- What is the graphics chip?

- Try some or several boot options, See [this link]("https://help.ubuntu.com/community/BootOptions") (and link from it at the end of the web page)

- After discussing the graphics chip and graphics drivers, maybe you should try a proprietary driver

I suggest that you stay with the Xubuntu 12.04 live CD until these things are resolved.

-o-

*Edit*: Later on you can try [PAE by mörgæs]("https://help.ubuntu.com/community/PAE") or [Lubuntu-fake-PAE]("https://help.ubuntu.com/community/Lubuntu-fake-PAE") and try a new version of an Ubuntu flavour, Xubuntu or Lubuntu.

Yes this was the problem. My graphics card is "nvidia geforce4 4200". Once I googled this with ubuntu, I found this is a common issue and I also found ways to get it to work. I never thought a graphics issue could cause the whole OS to die. Now I know.

[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-nouveau/+bug/653714](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-nouveau/+bug/653714)


I have to start the live dvd with the "nomodeset" option, which allowed me to finally get a working live version to fully install the OS. I later got the nvidia 96 drivers.

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/558950](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/558950)

 I did have some problems with the broadcom wireless but I fixed it with b43legacy. Even though it prints out errors every now and then in dmesg, it seems to work fine and doesn't disconnect me that I have seen. A way to fix these errors might be possible, but it seems like alot of work for something that seems working and isn't causing me issues.

So this solves all my current issues with the laptop. Thank you all for your help.

---

