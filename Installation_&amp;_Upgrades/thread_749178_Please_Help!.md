---
title: "Please Help!"
date: 2008-04-08
forum: Installation &amp; Upgrades
---

### Post by CpuPopper on 2008-04-08
Hi,

I would like to try Ubuntu 7.10.
I have recieved both x86 and x64 cd's in the mail, for free, which I think is nothing less than excellent.
Both CD's boot just fine... grub menu comes up, I choose to load Ubuntu, I see some text scolling up the screen, but at the point where the progress bar should appear, I just get a blank screen... it never gets to the desktop of the Live CD or Install Screen. (Thats for both the x86 & x64 CD's)

My PC has an AMD Athlon 64 X2 5200+ cpu, ASUS M2N-SLI Deluxe mobo, 4GB ram, Nvidia 8600GTS 256mb PCI-E video card, 320GB hdd, HP w1907 19" Wide LCD monitor, DVD Burner and thats about it.

About 6 months ago I got openSuse 10.3 x86 & x64 working, but I had to change some video settings once i got the OS installed. I vaguely remember the screnn was unreadable with lines and different colors before I got the video settings right. (Don't for the life of me remember how I fixed it though.

But with Ubuntu I don't get that far with Ubuntu 7.10 :confused:

I have done a bit of googling and reading on these forums for a solution but I havnt found anything yet.

Any help would be great. And thank you all in advance.

Dan.

---

### Post by Partyboi2 on 2008-04-08
When you get to the main menu press F6 and change splash to nosplash then press enter to boot. Hopefully this will give you some more info on where it is stopping.

---

### Post by CpuPopper on 2008-04-09
Hi PartBoi2,

I really appreciate your reply, thank you.

After booting with the nosplash option it got to;

* Running local boot scripts (/etc/rc.local)        [OK]

And thats where it stops. The cd stops spinning after a while and the hdd led blinks twice every second. PC is not frozen. And I get a blinking curser at the bottom of the screen. I just reset it after about 5-10 minutes.

I should have mentioned in my original post, that the drives are SATA, and the monitor is connected by DVI

I also did the break=bottom option and got to a console where i had a look at the xorg.conf file. My video card is recognised properly and is set to use the 'nv' driver. The monitor however doesn't seem to be conpletely configured... it's just recognised as a 'generic monitor' and under the 'screen' section there is no resolution, just color depth set to 24.

Thanks again for your help,

Dan.

---

### Post by Partyboi2 on 2008-04-09
try reconfiguring the xserver
```
sudo dpkg-reconfigure xserver-xorg
``` choosing the correct resolution for your monitor.
After you have finished that type
```
startx
```

---

