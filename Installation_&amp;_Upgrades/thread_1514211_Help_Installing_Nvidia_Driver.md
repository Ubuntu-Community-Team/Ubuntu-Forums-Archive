---
title: "Help Installing Nvidia Driver"
date: 2010-06-20
forum: Installation &amp; Upgrades
---

### Post by Arythael on 2010-06-20
For the past hour, I've been trying to install the official (non-glx) driver for my graphics card. I've only been using Ubuntu for a month or two, and have heard Nvidia's driver runs much faster/smoother than the glx driver. I tried to follow Nvidia's README for installing it, but it's far too cluttered... I understood that I need to stop the X server, then run the installer, but that's about all I could get from the README.

I disabled the glx driver in System > Administration > Hardware Drivers, opened a (Ctrl+Alt+F1) console as root (through 'sudo su'), stopped the X server, then ran the driver .run file from Nvidia's website. It installed without any errors, but when I rebooted, my computer came up with a prompt saying that Ubuntu is running in low-graphics mode, then a prompt with some Nvidia error messages, basically saying there are no drivers installed.

Also, I was having trouble stopping the X server. I tried several commands that I found online, and I don't remember which one worked, but '/etc/init.d/gdm stop', 'killall gdm', 'stop gdm', and 'service gdm stop' didn't seem to work - the Nvidia installer still said there was an X server running and it couldn't continue.

I'm really not sure what to do now... I would assume the first thing to do is uninstall the Nvidia driver and start over, but I can't find any help with how to uninstall/purge it (all searches are polluted with how to uninstall the glx driver and install the official one). I'd also like to know the correct procedure for installing the driver. Any help?

---

### Post by Silvertones on 2010-06-20
Only use Nvidia drivers available at sys/admin/hardware drivers.It's a snap.

---

### Post by Arythael on 2010-06-20
> **Silvertones said:**
> Only use Nvidia drivers available at sys/admin/hardware drivers.It's a snap.

If you can explain why it's better, you might convince me to use it instead. But ease of installation isn't a consideration, and that doesn't answer any of my questions.

Bump... anyone that can help?

---

### Post by 23dornot23d on 2010-06-20
What graphics card are you using and does glx run at all

fglrxinfo

What problems do you get when you run this with the normal driver installed .......... 

and did you check ........... here ......
Administration - Hardware Drivers

To make sure that you have the latest installed ........

  What computer do you have ....... do you have a link to the article telling you to change your driver to make it smoother ?

---

### Post by Arythael on 2010-06-21
> **23dornot23d said:**
> What graphics card are you using and does glx run at all

fglrxinfo

What problems do you get when you run this with the normal driver installed .......... 

and did you check ........... here ......
Administration - Hardware Drivers

To make sure that you have the latest installed ........

  What computer do you have ....... do you have a link to the article telling you to change your driver to make it smoother ?

I'm using a GeForce GTX 275. I don't know what you mean by "does glx run at all"... the normal driver works, I have the latest one from Admin > Hardware Drivers running fine. fglrxinfo returns "command not found."

My computer is in an Alienware case, but at this point I've replaced almost every component in it since I got it. I'm using an AMD Athlon 64 x2 6000+ processor on an ASUS M3N72-D motherboard with the latest BIOS installed.

It wasn't an article telling me to change the driver. The main reason I'm trying is because I'm having constant stuttering/artifacting problems while playing certain video files (in any media player - I've tried VLC, mplayer, movie player, etc), that I didn't have with Windows. Some forum user said something along the lines of "I just upgraded to nvidia's drivers and my graphics run so much smoother" in a post that I found in one of my countless searches trying to change my driver, I have no idea where to find it again.

---

