---
title: "Install - going out of my brain!"
date: 2010-04-28
forum: Installation &amp; Upgrades
---

### Post by malcmail on 2010-04-28
My windows 2k machine which acted as a print server recently died. So i thought I woudl give ubuntu a go on it.

After a couple of attempts got it installed and was liking it. Then after some more reading thought perhaps the server version was a better plan. However I couldnt get it to recognise my wireless card after 2 days of hell! So now I'm trying to reinstall the desktop version.

Now all it seems to do is give up along the way. Normally at the partition stage but often before it. Just freezing so it won't take any input etc. I know my machine can run it as it already has. And I cant use the alternate version as I end up with the same problem with my wireless card (although would it be easier to fix in desktop once its on?).

Any magical help gratefully received.

---

### Post by snowpine on 2010-04-28
Welcome to the forums!

1. Make sure your computer meets the minimum hardware specs for Ubuntu (1ghz processor with 512mb ram is recommended for the Desktop version):
[https://help.ubuntu.com/community/Installation/SystemRequirements](https://help.ubuntu.com/community/Installation/SystemRequirements)

2. Post which wireless card you have (use the 'lpsci' command if you're not sure)... we aren't mind readers and can't help if we don't know which card you have. :)

---

### Post by malcmail on 2010-04-28
Thanks for the reply. Given that it ran it ok 2 days ago and di also from the disk (albeit slowly) that its all good. Memory etc wise even though the box is hardly new.

As for the card - its a Belkin PCI F5D7000 E. If I could get that to work ok on server I wouldnt bother killing myself trying to get desktop back on lol. I tried ndiswrapper and it went smoothlyish. After installing a gcc to it. But there was no dhcpcd and trying to install it fell flat too. SO thats why I'm back at the desktop version now.

---

### Post by Bright_View on 2010-04-28
> **malcmail said:**
> Thanks for the reply. Given that it ran it ok 2 days ago and di also from the disk (albeit slowly) that its all good. Memory etc wise even though the box is hardly new.

As for the card - its a Belkin PCI F5D7000 E. If I could get that to work ok on server I wouldnt bother killing myself trying to get desktop back on lol. I tried ndiswrapper and it went smoothlyish. After installing a gcc to it. But there was no dhcpcd and trying to install it fell flat too. SO thats why I'm back at the desktop version now.

Just in case, you may wish to try running memtest to make sure the memory is alright.  I had a heck of a time installing ubuntu with a 'new' (new to me) system I got, and it ended up being a memory problem.  It would hang at various stages during installation - usually close to the same point during installation, but not exactly the same point.  

In my case, the memory actually passed memtest, and I only figured out that the memory was the problem after removing modules and trying with different individual sticks of ram in the computer.  You may wish to remove everything that is not necessary for the computer to operate and try to isolate the problem that way if you think it may be hardware related.

Good luck, I feel your pain.

---

### Post by snowpine on 2010-04-28
> **malcmail said:**
> Thanks for the reply. Given that it ran it ok 2 days ago and di also from the disk (albeit slowly) that its all good. Memory etc wise even though the box is hardly new.

As for the card - its a Belkin PCI F5D7000 E. If I could get that to work ok on server I wouldnt bother killing myself trying to get desktop back on lol. I tried ndiswrapper and it went smoothlyish. After installing a gcc to it. But there was no dhcpcd and trying to install it fell flat too. SO thats why I'm back at the desktop version now.

I see no reason why networking capabilities would be better with the desktop than the server edition (servers are all about networking after all).

According to kernel.org your card uses b43 firmware: [http://wireless.kernel.org/en/users/Devices/PCI](http://wireless.kernel.org/en/users/Devices/PCI)

This driver is very easy to install in Ubuntu:
[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx#Installing%20BCM43xx%20drivers](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx#Installing%20BCM43xx%20drivers)

There's no reason to spend 2 days frustrated by a minor problem like this; "Ubuntu networking" is an extremely well-documented topic, and these forums are always here if you have questions. :)

---

### Post by malcmail on 2010-04-28
I'd no idea why it didnt work straight away with the server version either. Just seemed weird. I'll give that link a go and let you know how I get on - thx for the help guys.

---

### Post by malcmail on 2010-04-28
I tried the link and at step 1 got a little confuzzled. I did lspci and no mention of belkin or broadcom but of Atheros Communications Inc AR2413.  Should I be worried?  

I'ce installed the bmcwl kernel although it said it completed with errors! Managed to get the cutter installed.  On the presumption eveything to now is actually ok what is the final command line with the cutter? Is it the windows driver copied down (unlikely I presume) or a driver I can't see? Thx again for all the help. Maybe I can sleep tonight! :)

---

### Post by snowpine on 2010-04-28
> **malcmail said:**
> I tried the link and at step 1 got a little confuzzled. I did lspci and no mention of belkin or broadcom but of Atheros Communications Inc AR2413.  Should I be worried?  

I'ce installed the bmcwl kernel although it said it completed with errors! Managed to get the cutter installed.  On the presumption eveything to now is actually ok what is the final command line with the cutter? Is it the windows driver copied down (unlikely I presume) or a driver I can't see? Thx again for all the help. Maybe I can sleep tonight! :)

Sorry I gave you bad advice about your chipset. :( The best thing to do is to stop the Broadcom tutorial I linked to if you do not have a Broadcom chipset. :) Unfortunately I am not as familiar with the Atheros cards as with the Broadcom.

Let's take a breath and go back to square one. Which Ubuntu release are you using? (9.10, 10.04, etc.) Did your wifi work with the desktop edition, but not with the server? What steps have you taken to connect on the server version?

---

### Post by malcmail on 2010-04-28
Square one is apt as I just reinstalled the Server version 91.0 32 bit version.

The driver disk that came with the pci card was broadcom. The sticker on the card says belkin, the lspci says Atheros. Take your pick!! :)

I thought a fresh install may be a better way to go as I'd faffed around so much already - clean had to be a better place to start.

When I did get desktop working it connected straight to the net no issues at all. I just had to add the SSID and we were off and running.

Still want to know what I tried before?? Miserably probably - learning fast though!

---

### Post by snowpine on 2010-04-28
Fresh install, good. :) What does the output of 'iwconfig' (without the quotes) look like? (I recognize you may not be able to cut & paste without a GUI or internet connection.) Do you see a device named 'wlan0' or similar? Does it list your wireless network?

---

### Post by malcmail on 2010-04-28
It at least has wlan0. In the setup it said no network devices found btw.

IEEE 802.11.bg ESSID:""
Mode: Managed Frequency:2.412GHZ Accesspoint: Not-associated

Plenty of other stuff - if you need it I'll type it up (say you dont!!)

PS No light on the card at the back

---

### Post by snowpine on 2010-04-28
So I *think* your card is being detected (no restricted drivers necessary), but you just need a little help how to connect using the terminal only. Is that accurate?

Here's a helpful thread that should get you started: [http://ubuntuforums.org/showthread.php?t=1185936](http://ubuntuforums.org/showthread.php?t=1185936)

---

### Post by malcmail on 2010-04-28
Looks like I'm getting somewhere - cheers fella.

I also started following this thread [http://ubuntuforums.org/showthread.php?t=571188](http://ubuntuforums.org/showthread.php?t=571188)

I tried the command to add the default gateway though but all i get is "SIOCADDRT: no such process". Think this might be all that is holding me back. I hope. ANy more ideas?

I tried route add default gw GW xxx.xxx.xxx.xxx and got GW: unknown host. I'm a trier lol

Further - if I do iwconfig th end of the report shows Signal level 0 - that cant be good can it? My router works on channel 11 if that makes a blind bit of difference.

---

### Post by malcmail on 2010-04-28
SCORE!!! Well its pinging google anyway so thats a start. Now to set a static IP address and make it stick.  Thanks for all your help. I think I may not wuv oo - hehe. Cheers!

---

