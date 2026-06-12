---
title: "Cannot install"
date: 2011-05-14
forum: Installation &amp; Upgrades
---

### Post by trevtoo on 2011-05-14
Hi, maybe someone can help me here.
I've tried to install both Ubuntu 10.10 netbook and 11.04 desktop (at separate times) on my Acer Aspire One D255E netbook computer as a guest OS using Virtual PC running on Windows XP SP3.
In both cases, after a long wait I get the scrolling message, 'Login timed out after 60 seconds' at the top left of the screen.
I have 1GB RAM on the computer.
Anyone else had this problem? Maybe I'm not allocating enough memory or something, or maybe this netbook isn't compatible.
Thanks,
Trev

---

### Post by Dutch70 on 2011-05-14
Hi and welcome to UF

I take it you actually "did" install Ubuntu & you're having trouble logging in? 
Not sure if it's the problem, but I think you do need to allocate at least 512MB of RAM.

I'm not familiar with "Virtual PC" although I do use "Virtualbox"
To find out how it will run on your pc, you may want to create a live cd or usb stick. The usb is usually much simpler & faster if you have one. You can create it with Unetbootin. The download & directions are on this page. 
[[COLOR="Red"]http://www.pendrivelinux.com/using-unetbootin-to-create-a-live-usb-linux/[/COLOR]]("http://www.pendrivelinux.com/using-unetbootin-to-create-a-live-usb-linux/")

If you've got XP, I think you'll probably be wanting to put Ubuntu on your hard drive soon, but I strongly recommend Ubuntu version 10.04 Lucid Lynx.

Edit: also, to save yourself some trouble, it is a good idea to check the md5sum of the .iso that you download.
[[COLOR="RoyalBlue"]HowToMD5SUM[/COLOR]]("https://help.ubuntu.com/community/HowToMD5SUM")
and check the cd/usb for defects.
[URL="https://help.ubuntu.com/community/Installation/CDIntegrityCheck?action=show&redirect=CDIntegrityCheck"][COLOR="RoyalBlue"]InstallationCDIntegrityCheck
[/COLOR][/URL]

---

### Post by trevtoo on 2011-05-14
Hi. Thanks for the reply. I think my problem is that Virtual PC doesn't accept Linux guest OS's. I burnt a disc and was able to get that working OK. Just don't want to install to my hard drive yet until I've had a play around. Also, Ubuntu isn't very compatible with the Acer Aspire One it seems. I'll wait for a stable English version of One4Linux to come out and try again.
Thanks again.
Trev

---

### Post by saegeoff on 2011-05-14
Trevtoo, why have you not tried Oracle(Sun) Virtual Box?  It is probably the best free alternative out there.  Virtual PC is junk in my opinion.  I don't even use it to host Windows Virtual Machines.

---

### Post by saegeoff on 2011-05-14
Also, I use to own an Aspire One laptop.  I ran Ubuntu on it with no problems.

---

### Post by trevtoo on 2011-05-15
Hi, as regards Virtual Box, I may try  that again. The reason I'm using VirtualPC is because it's much friendlier with DOS OS's. When I tried Virtual Box with DOS, you couldn't have shared folders, and full screen mode was just a blank screen with the DOS screen centered. VirtualPC does it much better.
I have booted to Ubuntu from a CD that I burnt with no problems, but you can't leave that up, need to boot every time.
I've read that there are a few hardware incompatibilities with the Acer Aspire One, hence an Italian group have created Linux4One (Aspire One), but no English version yet as I know.
Anyway, I'm a Linux noob, I've tried it two or three times over the last 15 years or so, time to try again.
I'll work it out in the end, just want to try it on a VM before I commit to a full install alongside Windows.
Thanks for all the replies.
Trev

---

### Post by Dutch70 on 2011-05-15
Sounds like a Wubi install may be perfect for you right now. That is to install Ubuntu into windows programs just like any other windows program. You can then uninstall it the same simple way, or migrate it to it's own partition. 

Notice the "warning" in this guide, which more than likely pertains to 11.04 also. *(the guide probably hasn't been updated)* 
That being said, I still recommend 10.04 Lucid Lynx. 
[[COLOR="RoyalBlue"]WubiGuide[/COLOR]]("https://wiki.ubuntu.com/WubiGuide")

Check this link for how Lucid Lynx 10.04 works with your hardware. Keep in mind that it may work better now than when this was written.
[[COLOR="RoyalBlue"]https://wiki.ubuntu.com/HardwareSupport/Machines/Netbooks[/COLOR]]("https://wiki.ubuntu.com/HardwareSupport/Machines/Netbooks")
This one may be better...
[[COLOR="Blue"]https://help.ubuntu.com/community/AspireOne[/COLOR]]("https://help.ubuntu.com/community/AspireOne")

Are you sure linux4one doesn't come in English?
[[COLOR="RoyalBlue"]http://eeepc.itrunsonlinux.com/the-news/1-latest-news/242-linux4one-ubuntu-for-the-acer-aspire-one-[/COLOR]]("http://eeepc.itrunsonlinux.com/the-news/1-latest-news/242-linux4one-ubuntu-for-the-acer-aspire-one-")

Also, if you google for "ubuntu acer aspire one" You'll get lots of good links. Be sure to check the ones from the Ubuntu Forums.

---

### Post by trevtoo on 2011-05-16
Hi Dutch. I'll have a look at all that stuff. For the moment, I'm just taking things easy, bit by bit. I'm on a very slow connection and takes hours to d/l a distro, so I'll try a couple of things. The Linux4One I mentioned is built from an Ubuntu distro, and specially tailored for the Aspire One, so I'll see how that goes.
Thanks everyone for your suggestions.
Trev

---

