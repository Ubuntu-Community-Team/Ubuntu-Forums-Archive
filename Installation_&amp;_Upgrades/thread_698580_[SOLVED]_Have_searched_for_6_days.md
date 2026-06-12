---
title: "[SOLVED] Have searched for 6 days"
date: 2008-02-16
forum: Installation &amp; Upgrades
---

### Post by GJRick on 2008-02-16
I have been reading the Ubuntu forums (and others) for six days straight trying to get Ubuntu installed on my wife's Valentine's gift. I bought an Acer Extensa 4420 last Sunday at Best Buy and have been trying, in vain, to install any form of Linux on it because I don't want her to have to mess with Vista.

Laptop hardware:
Broadcom 802.11g 
Marvell Yukon 88e8071 PCI-E Gigabit Ethernet
Realtek Audio
ATI Radeon Xpress 1250 video

My main error is the "bcm43xx_microcode5.fw not available or load failed". The computer has NEVER booted up from a Live CD all the way into a desktop because of the error. Much of the reading says I need to get the firmware updated on the wireless card, but all the instructions are for doing that from the desktop...which I can't get to.

I have tried:

Ubuntu 7.10
Ubuntu 7.10 alternate
Ubuntu 7.04
Ubuntu 7.05 alternate
Kubuntu 7.10 
Kubuntu 7.10 alternate
PCLinuxOS

None of them will let me get up and running. I continue to get the above error. I have tried booting in recovery mode and typing:

dpkg-reconfigure -phigh xserver-xorg
shutdown -r now

No love.

I have set the video mode to 640 X 480 only in the text setups on the alternate CD's. 

I feel like a dolt not having my wife's Valentine's Day present finished for her on Thursday, but I have never run into such a juggernaut with Linux (albeit I've only been using it off and on for about a year).

Any help is GREATLY appreciated.  Thanks.

Rick in Colorado and in the doghouse for being a Valentine's Day chump

---

### Post by Pumalite on 2008-02-16
Get wired to the Internet with DHCP.

---

### Post by xlinuks on 2008-02-16
Or you could put an XP SP2 with all the bells and whistles..  IMO it's still a lot better than Vista.

---

### Post by wolfen69 on 2008-02-16
can you return the computer for your money back? then buy a linux pre-installed.(Dell, System76)
i have tried to install linux on 2 brand new computers, and it just isnt going to happen.(xp wouldnt even work) the machines are just too closely tied to vista.

---

### Post by Pumalite on 2008-02-16
I have installed 6 different distros in 5 different hardwares. Some motherboards and their chipsets are just not cooperative. I have a Gutsy 64 bit installed side by side with OSX in a MacBook Intel Core 2 Duo. Some other 'good' ones: ASUS P5K SE, Intel Desktop Board D975XBX, etc.

---

### Post by sloggerkhan on 2008-02-16
I have an acer with the same or similar wireless. I think what you need to do is boot to the recovery console and blacklist the that broadcom thing in the appropriate location. (Which I unfortunately can not recall, as the last time I did that was like 1.5 years ago.) In any case, once you blacklist the module, it shouldn't load and you'll get to your desktop IF that was really the cause of your hangup.

Also, if you just want to kill the interfering wireless driver::
sudo rmmod bcm43xx
however, that might make it harder to get working later.

edit:
found blacklist info:
```

sudo nano /etc/modprobe.d/blacklist

```
and add
```

blacklist bcm43xx

```
to it.

If it boots fine, use the restricted drivers manager to install the firmware, then unblacklist it.
If it still has problems after blacklisting, it's **probably** something other than the wireless card.

Another possibility (since I didn't see your exact card specified) is that you are using a newer broadcom card of some kind that somehow won't cooperate with the firmware given, in which case you might try ndiswrapper. (after successfully blacklisting the module.)

---

### Post by GJRick on 2008-02-16
I tried that too, Pumalite, just forgot to list that. sorry. Still no love.

---

### Post by GJRick on 2008-02-16
I, too, like XP, but like the hands-off security worries and stability of Linux better.

---

### Post by GJRick on 2008-02-16
The cheapest Linux computer sfrom Dell are $700-900 (what jip), and this Acer was $500 with 2GB, 120 GB, DVD burner, etc.

---

### Post by GJRick on 2008-02-16
Thanks for all the suggestions so far.  I'm going to give sloggerkhan's suggestion a try and report back soon. Thanks again!

---

### Post by Pumalite on 2008-02-16
I'll give you a few things to read:
[http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)
[http://www.psychocats.net/ubuntu/partitioning](http://www.psychocats.net/ubuntu/partitioning)
[http://www.howtoforge.com/dual_boot_windows_xp_vista_ubuntu_feisty_p2?](http://www.howtoforge.com/dual_boot_windows_xp_vista_ubuntu_feisty_p2?)
[http://apcmag.com/5046/how_to_dual_boot_vista_with_linux_vista_installed_first](http://apcmag.com/5046/how_to_dual_boot_vista_with_linux_vista_installed_first)
[http://users.bigpond.net.au/hermanzone/](http://users.bigpond.net.au/hermanzone/)

---

### Post by GJRick on 2008-02-16
Darn it, still didn't work Sloggerkahn. I'm almost ready to go back to Vista, and I really don't want to do that...

Thanks for you suggestions.

---

### Post by GJRick on 2008-02-16
Hi, Puma. Thanks for the links. Unfortunately, I can't use any of the suggestions on them because they all involve the Live CD installation and I can' t boot into a working desktop from any Live CD. 

The alternate CD install options have not yielded any success either. I'm completely baffled and can't find a solution anywhere yet...but I have confidence in the Ubuntu community that a solution will surface.

Thanks.

Rick

---

### Post by Pumalite on 2008-02-16
You can try some boot parameters. Here is a guide and a collection. Try them alone and/or in combinations:
[http://grumpymole.blogspot.com/2007/05/ubuntu-how-to-edit-grub-boot-parameters.html](http://grumpymole.blogspot.com/2007/05/ubuntu-how-to-edit-grub-boot-parameters.html)
[https://help.ubuntu.com/7.04/installation-guide/hppa/boot-parms.html](https://help.ubuntu.com/7.04/installation-guide/hppa/boot-parms.html)
Some suggestions:
noapic nolapic acpi=off pci=noacpi pnpbios=off vga=0x317
Also removing 'quiet' and 'splash' sometimes work.

---

### Post by GJRick on 2008-02-16
Thanks Pumalite. I will try the suggestions you gave, but I must admit that the info in the linnks made my brain hurt. I'm a practical computer user (which is why I like Ubuntu), but this install is kicking my a--.

---

### Post by GJRick on 2008-02-16
I'm trying the new suggestions from Pumalite, but some new information might help. I tried loading PCLinuxOS again today, and it failed at the end with a "Failed to start the X server" message. When looking at the problem, it stated that "no monitor" was found. I used their x.org editor (very cool) and tried different configurations of monitor, video card, and resolution all to no avail.

As I'm typing this, the suggestions for boot parameter that Pumalite game me yielded no results either. 

Thanks again.

---

### Post by sloggerkhan on 2008-02-16
I am guessing that the wireless card isn't the real issue here at this point.
However, I'm not sure what else could cause a problem. You have checked the md5sum of the CD and also done a memtest?

---

### Post by GJRick on 2008-02-16
yes, I have done both of those things.... Thanks.

---

### Post by chriszilla445 on 2008-02-16
Just got the same computer and the same problem. :mad: If I get anything to work I'll post it here

---

### Post by GJRick on 2008-02-16
Excellent. Thanks Chriszilla. I am search frantically and trying everything I'm capable of (which isn't much). I'm downloading Freespire right now to try it, but I'm thinking it will be the same problem.

I, too, will post any success that I come across. 

cheers

---

### Post by sloggerkhan on 2008-02-17
PS: If you changed the thread title to be more specific, you might get some better advice ;)
If you can't do, maybe PM a mod, they'd probably be willing to help with something small like that.

---

### Post by GJRick on 2008-02-17
How can I change the title of the thread Sloggerkhan? I  wanted to to title it so experts would know that I did do some searching prior to asking for help.

Thanks.

---

### Post by Pumalite on 2008-02-17
You could try: 'Installing Ubuntu on Acer.. blah...blah'
[http://ubuntuforums.org/showthread.php?t=595979](http://ubuntuforums.org/showthread.php?t=595979)

---

### Post by zipperback on 2008-02-17
I have an acer aspire 5050-3371

It works with Ubuntu Linux Gutsy 7.10 without any problems.

My system uses the Atheros chipset for wifi.

---

### Post by GJRick on 2008-02-17
You are a lucky fellow. I've been battling this all week and can't get anything to work (see first post). I sure hope I can find a solution so I don't have to put Vista back on this thing.

---

### Post by GJRick on 2008-02-18
Unfortunately, I wasted 7 days of my time trying to get this Acer 4420 laptop installed with Ubuntu (or any Linux). I appreciate all the help you folks threw my way, but it appears that this model of wireless and video combo are too much for Ubuntu at this time.

I will stay with Ubuntu on my other laptops and continue to learn (and help others when I can). 

Thanks again.

---

