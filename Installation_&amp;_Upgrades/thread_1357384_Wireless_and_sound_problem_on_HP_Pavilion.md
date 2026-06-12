---
title: "Wireless and sound problem on HP Pavilion"
date: 2009-12-17
forum: Installation &amp; Upgrades
---

### Post by freestyleren on 2009-12-17
I just dual booted my Vista-running HP Pavilion dv9000 with Ubuntu 9.10. I'm experiencing some problems though.

It seems that I cannot connect to any wireless networks (It doesn't detect any), and I suspect it has to do with the little wireless switch on the side of my PC. Even when 'activated' it still glows red, as opposed to blue when working in Windows.

The other problem is that when booting in Ubuntu the sound seems to make little 'pops', regardless if the sound is turned on or not.

I'm a fairly new Ubuntu user, and have never dual booted before so any help is most appreciated.

---

### Post by freestyleren on 2009-12-17
Oh, this was supposed to be in Laptops, is there any way to move this?

---

### Post by GuitarJim1987 on 2009-12-17
Hi freestyleren

I too have just installed 32bit 9.10 ubuntu on a HP laptop (G5000, much older). I too had a problem with wireless connections.

First of all double check in 'users and groups' (via system>administration) that your login account has the permission to access wireless networks. This was the last thing I tried after spending hours fiddling with drivers. For some reason 9.10 defaults as off.

Next if the wireless card does not work 'out of the box' you may need to find some drivers. Connecting via a cable to your home connection is the easiest way to do this. First check in the hardware drivers under administration to see if there are any proprietary drivers for the wireless card you have. If not your best bet is probably ndiswrapper for which there are plenty of guides elsewhere.

With regard to the sound issue, it is a power saving feature in ubuntu 9.10 which turns your soundcard off at hardware level if inactive for so many seconds. There is a work around [here]("http://ubuntuforums.org/showthread.php?t=1314834").

I hope that helps.

---

### Post by freestyleren on 2009-12-17
Thanks I'll try that.

---

### Post by freestyleren on 2009-12-17
The sound the worked, but although wireless was actually disabled in user groups it still doesn't work.

---

### Post by GuitarJim1987 on 2009-12-17
Okay so the next step regarding the wireless card is to connect your laptop via a wired connection to the Internet. Then you need to check for proprietary drivers, go System > Administration > Hardware Drivers. Hopefully Ubuntu will find a driver for your wireless card and all need to do is highlight the driver and hit hit activate underneath.

If Ubuntu does not find a driver then you may get some results using ndiswrapper to install the windows driver. Install ndiswrapper via synaptic package manager and you should have a new entry in system > administration called 'windows wireless driver' or something to that affect which is the GUI for ndiswrapper. A detailed guide on how to use [here]("http://www.linuxquestions.org/linux/answers/Networking/NdisWrapper_The_Ultimate_Guide/").

---

### Post by freestyleren on 2009-12-17
Trying to make the suspend function work, I must have changed something that now keeps my Ubuntu from loading the desktop. How can I edit the files back in the command line?
This was what I was trying to do: [http://myy.helia.fi/~karte/acer_travelmate_3004wtmi_with_linux.html#suspend-to-ram_s3](http://myy.helia.fi/~karte/acer_travelmate_3004wtmi_with_linux.html#suspend-to-ram_s3)

---

### Post by GuitarJim1987 on 2009-12-17
Lol, I think you can just go:

```
sudo gedit /etc/default/acpi-support
```and change

```
DOUBLE_CONSOLE_SWITCH=true
```to

```
DOUBLE_CONSOLE_SWITCH=false
```then

```
sudo gedit /etc/X11/xorg.conf
```delete the extra lines the guide said to add, save and close.

You will probably need to reboot now too.

EDIT - note that you followed instruction for completely the wrong laptop which is probably why it messed up. Did you get the wireless working?

---

### Post by freestyleren on 2009-12-17
I tried that but it says Gtk-warning **: cannot open display.

---

### Post by GuitarJim1987 on 2009-12-17
I really can't help you any further really, I'm quite new to ubuntu aswell. I would advise changing the title of this topic to encourage others to help out.

---

### Post by freestyleren on 2009-12-17
I appreciate the time, and I realize this has turned into an Q&A's thread. :(

---

### Post by freestyleren on 2009-12-17
Ok, i fixed that little problem using the nano command.

---

