---
title: "I'm desperate, and badly need help."
date: 2011-07-13
forum: Installation &amp; Upgrades
---

### Post by Jamsers on 2011-07-13
Please bear with me, I'm an absolute (emphasis on absolute) noob, but Windows just isn't a choice for me.

I've installed Ubuntu 11.04 from a USB while connected to the internet through LAN wire. I checked the boxes that asked if I wanted to download updates and third party stuff for the installation, and made the installer wipe out the whole hard disk. Everything goes absolutely fine, no trouble at all.

So I reboot immediately when it finishes and all goes fine. I log in for the first time into my Ubuntu desktop. Everything is shiny, working out of the box, wi-fi, graphics drivers, all that. I play an mp3 file to make sure the proprietary codecs were properly installed, and the mp3 plays. Good. I shut my netbook down, and walk home.

When I get home and turn on my netbook, the screen freezes on the log-on screen. As in, freezes. Cursor and all. I hard restart it, still the same thing. About the time when I'm typing my password it just freezes.

I panic, reach for the USB with the installer and attempt to reinstall. No dice. It won't even go in the installer. The installer freezes too.

Now I'm completely hopeless, and I know absolutely nothing. I don't know what to do. Somebody please help me.

I own an Acer Aspire One 522. Before I installed Ubuntu, I updated the BIOS from 1.4 to 1.9 from within Windows. Hope that helps, but the flash finished without a hitch. Still, it might be connected or something. I don't know.

Sorry for the long, ranting post. Like I said, I'm an absolute noob, so please, PLEASE, bear with me. Thank you in advance for anyone with the time and patience to try and help me. I'm really desperate and clueless as of this moment.

---

### Post by dino99 on 2011-07-13
googling a little around and found lot of users having troubles with wifi:

[https://encrypted.google.com/search?client=ubuntu&channel=fs&q=natty%2Baspire%2B522&ie=utf-8&oe=utf-8](https://encrypted.google.com/search?client=ubuntu&channel=fs&q=natty%2Baspire%2B522&ie=utf-8&oe=utf-8)

and a possible solution:
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/775034](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/775034)

look post "3 to blacklist the module :
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/775034/comments/3](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/775034/comments/3)

sudo gedit /etc/modprobe.d/blacklist.conf


but first you need to be able to boot:
- at bios end process, hold "shift" key down to get the grub menu
- choose "recovery" mode (second line choice)
- choose "network" to get a command line prompt
then run the command line above to blacklist the module, save and reboot to see if it makes a difference, otherwise you should continue in recovery mode and you should install the latest kernel:

[http://kernel.ubuntu.com/~kernel-ppa/mainline/daily/current/](http://kernel.ubuntu.com/~kernel-ppa/mainline/daily/current/)
in that order:
- install linux-headers...all.deb
- install linux-headers...i386.deb (as your install might be a 32 bits one, otherwise choose the amd64 one)
- then install the related linux-image package

---

### Post by Jamsers on 2011-07-13
Oh so it's the WiFi! Thanks! That explains a LOT.

Thank you very much... I did notice that the system froze whenever the WiFi indicator would light up. Makes perfect sense now.

Do you have any idea how to disable WiFi from turning on automatically? It kinda did that even in Windows... it would be on by default. And there's no option in the BIOS to turn it off. Darn.

---

### Post by dino99 on 2011-07-13
not sure:

[http://compnetworking.about.com/od/wirelessfaqs/f/router-wifi-off.htm](http://compnetworking.about.com/od/wirelessfaqs/f/router-wifi-off.htm)

but if you dont want/need wifi, then blacklist it: blacklist acer_wmi

[http://sachinb.blogspot.com/2011/05/wifi-on-natty.html](http://sachinb.blogspot.com/2011/05/wifi-on-natty.html)

---

### Post by Jamsers on 2011-07-14
I've found a much better solution (through that link you posted) that doesn't involve mucking around Ubuntu.

You know that feature in computers where you boot from the network? PXE? Something like that?

Whatever. Anyways, all you have to do is go to the BIOS, and in the boot sequence, put the "network boot" or something like that on top of the hard drive (meaning, make the BIOS try to boot from the network first, before it tries to boot from the hard drive). Then make sure "boot from network" is enabled in the BIOS. I'll post back with a more accurate description later.

And whala! Everything works absolutely dandy now. You can turn off the wifi, turn it on, use a wired connection, ANYTHING, and everything will be fine. No hanging or freezing at all. I'm posting this right now using my AO522 connected to the Internet through the university wifi.

Thanks for the help! Been using Ubuntu 11.04 now for a few hours now and it is absolutely delightful. And I'm glad the community responded to my early problem so quickly. It's all fixed now, and everything is working beautifully. Thanks.

---

