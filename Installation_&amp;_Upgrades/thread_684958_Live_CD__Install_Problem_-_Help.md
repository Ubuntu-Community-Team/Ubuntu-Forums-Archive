---
title: "Live CD / Install Problem - Help"
date: 2008-02-01
forum: Installation &amp; Upgrades
---

### Post by RpJp on 2008-02-01
Hello,

I downloaded Ubuntu 7.10 and burned the iso to a CD and set my boot sequence to cd first. I get the Ubuntu boot menu and select the first option "Start or install Ubuntu" what happens next is the logo and moving status bar display for a while before the screen goes completely blank. I've tried a few times to get to the gnome desktop but with no luck - my screen simply goes blank and I have no option but to cut the power.

More info:
Laptop
256MB DDr-Ram
Intel Extreme Graphics up to 64MB
40GB HDD, 13GB free
Windows XP installed

Any help is much appreciated, thank you.

---

### Post by ayoli on 2008-02-01
> **RpJp said:**
> Hello,

I downloaded Ubuntu 7.10 and burned the iso to a CD and set my boot sequence to cd first. I get the Ubuntu boot menu and select the first option "Start or install Ubuntu" what happens next is the logo and moving status bar display for a while before the screen goes completely blank. I've tried a few times to get to the gnome desktop but with no luck - my screen simply goes blank and I have no option but to cut the power.

More info:
Laptop
256MB DDr-Ram
Intel Extreme Graphics up to 64MB
40GB HDD, 13GB free
Windows XP installed

Any help is much appreciated, thank you.

did you check your iso like explained here : [http://www.psychocats.net/ubuntu/iso](http://www.psychocats.net/ubuntu/iso)
if your iso and cd are ok, : then you may want to try boot options such as 
```
irqpoll nopapic
```

---

### Post by overdrank on 2008-02-01
> **RpJp said:**
> Hello,

I downloaded Ubuntu 7.10 and burned the iso to a CD and set my boot sequence to cd first. I get the Ubuntu boot menu and select the first option "Start or install Ubuntu" what happens next is the logo and moving status bar display for a while before the screen goes completely blank. I've tried a few times to get to the gnome desktop but with no luck - my screen simply goes blank and I have no option but to cut the power.

More info:
Laptop
256MB DDr-Ram
Intel Extreme Graphics up to 64MB
40GB HDD, 13GB free
Windows XP installed

Any help is much appreciated, thank you.

Hi and welcome, you may want to check the cd for errors 
Then you may want to do a checksum on the cd 
[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM) 
The intel graphics may be an issue so could you tell us the specific model?

---

### Post by RpJp on 2008-02-01
Hello thanks for the quick replies!

I checked the MD5 sums before I burned the iso and the disk is fine - I managed to reach gnome by booting in safe graphics mode. Any idea what the problem is that stops the normal boot from working?

If installed from safe graphics mode will Ubuntu actually boot when installed?

---

### Post by ayoli on 2008-02-01
> **RpJp said:**
> Hello thanks for the quick replies!

I checked the MD5 sums before I burned the iso and the disk is fine - I managed to reach gnome by booting in safe graphics mode. Any idea what the problem is that stops the normal boot from working?

If installed from safe graphics mode will Ubuntu actually boot when installed?

it should, but you could have a grphical issue, as asked above what is exactly your intel graphics chip ?

---

### Post by RpJp on 2008-02-01
It's an Intel 82845G/GL/GE/PE/GV/ Graphics Controller...

---

### Post by overdrank on 2008-02-01
> **RpJp said:**
> It's an Intel 82845G/GL/GE/PE/GV/ Graphics Controller...

That chipset should not be an issue but have you tried to reconfigure your xorg from the command line. Using the ctrl, alt, F1 keys at the login screen will bring you to the command line and then ```
sudo dpkg-reconfigure -phigh xserver-xorg
```

---

### Post by nparrott on 2008-02-01
Try booting is safe graphics mode...  I had this problem with my thinkpad... it worked for me!

---

### Post by RpJp on 2008-02-01
> **overdrank said:**
> That chipset should not be an issue but have you tried to reconfigure your xorg from the command line. Using the ctrl, alt, F1 keys at the login screen will bring you to the command line and then ```
sudo dpkg-reconfigure -phigh xserver-xorg
```

I reconfigured xorg but itdidn't seem to work - I can't get to the desktop in any way except safe graphics mode. Basically I want to know how to correctly install Ubuntu from safe graphics mode. I'm silghtly concerned that the install won't work because the graphics are wrong...

---

### Post by overdrank on 2008-02-01
> **RpJp said:**
> I reconfigured xorg but itdidn't seem to work - I can't get to the desktop in any way except safe graphics mode. Basically I want to know how to correctly install Ubuntu from safe graphics mode. I'm silghtly concerned that the install won't work because the graphics are wrong...

Hi and I do apologize as I thought you had it install already on my previous post with the xorg. The intel graphics should not be a issue, and have you looked in the bios to see how much memory is shared with the graphics? That could be an issue as you only have 256mb and the onboard graphics are sharing that.

---

### Post by ayoli on 2008-02-02
you should try to append one of these boot options to the boot line:
```
noacpi
```
or 
```
irqpoll noapic
```

---

