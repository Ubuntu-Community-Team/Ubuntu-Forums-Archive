---
title: "Installation"
date: 2007-11-06
forum: Installation &amp; Upgrades
---

### Post by thakayos21 on 2007-11-06
After downloading and making the iso cd for Gutsy Gibbon, I restarted my computer to boot from disc. It doesn't load I just recieve a blank black screen. My harddrive runs and my fans show activity but I don't recieve anything on the screen. What is the fix for this issue?

---

### Post by rsambuca on 2007-11-06
In order to help you we require more information:

Did you check the md5sum of the iso prior to burning it?
Did you burn it at a low rate to help prevent single bit errors?
Did you run the CD integrity check?
Did you use quality CD media?
What are your system specs: cpu, graphics card...

---

### Post by gfxguy on 2007-11-06
I'm having some problems with 7.10 on my laptop...

How long did you give it before giving up?  When Ubuntu (both the live CD to install and the system after it's been installed) show me a blank screen for a REALLY long time.

Eventually the installed system finally shows me the login screen.... BUT, the text and icon sizes are REALLY HUGE.  Then I login, and everything is HUGE until it's completely logged in, then everything is normal afterwards (including the login screen).

Ok, back to installation; the CD takes so long to start up that, I'm guessing, the screensaver has already kicked in (although the screen is completely blank during booting, after I've selected the install option).  I have to hit the alt or control key and then the screen turns on to the usual desktop.

---

### Post by Cynikiss on 2007-11-06
I'm having the same problem as the original poster. I've actually tried burning two separate ISOs (Kubuntu and Ubuntu, both v6).

When I restart my system to boot from the discs, I've run the disc check from the loading menu and everything seems fine there, and the system goes through all the check...ok processes as it attempts to load the OS, and then I get the black screen and nothing else. I did not, however, burn the discs at a slower speed (I always have it set to max burn speed, out of habit), and will try that.

I'm unfamiliar with the concept of md5sum... whatever that is. I've seen it mentioned elsewhere, but have no idea what that is or what it's supposed to accomplish. (If someone could explain it to me, briefly, I would appreicate it.)

To burn both ISOs, I used InfraRecorder, as instructed.

System Specs (don't laugh, it's an old system :P):
Intel Pentium 4 2.8HGz, 2GB RAM
nVidia GeForce 6200
nVidia GeForce4 MX 4000

If I've forgotten to include any other helpful information, let me know.

---

### Post by rsambuca on 2007-11-06
> **Cynikiss said:**
> I'm having the same problem as the original poster. I've actually tried burning two separate ISOs (Kubuntu and Ubuntu, both v6).

When I restart my system to boot from the discs, I've run the disc check from the loading menu and everything seems fine there, and the system goes through all the check...ok processes as it attempts to load the OS, and then I get the black screen and nothing else. I did not, however, burn the discs at a slower speed (I always have it set to max burn speed, out of habit), and will try that.

I'm unfamiliar with the concept of md5sum... whatever that is. I've seen it mentioned elsewhere, but have no idea what that is or what it's supposed to accomplish. (If someone could explain it to me, briefly, I would appreicate it.)

To burn both ISOs, I used InfraRecorder, as instructed.

System Specs (don't laugh, it's an old system :P):
Intel Pentium 4 2.8HGz, 2GB RAM
nVidia GeForce 6200
nVidia GeForce4 MX 4000

If I've forgotten to include any other helpful information, let me know.

I am actually surprised this isn't working with that setup.  Maybe pop out one video card prior to installing and insert it later.  

For the md5sum info, [check out this link]("https://help.ubuntu.com/community/HowToMD5SUM").  However, if you CD verifies OK,  I assume your iso was OK.

---

### Post by Cynikiss on 2007-11-06
Ah... maybe it is the video card thing that's causing the problem. I've actually had to remove one of the cards when reinstalling Windows before, but to be honest, I didn't think I'd have the same problem. (Kinda the assumption that Windows is dumb, Linux usually isn't, lol)

Thanks for the link to the md2sum info, I've bookmarked it. :) Thanks for the quick reply as well! I've attempted to burn the ISO at a slower speed (16x) this time, and am going to try again. If it doesn't work this time, I'll remove one of the video cards and make another attempt. If neither of those changes work... who knows? Lol.

---

### Post by Cynikiss on 2007-11-06
Okay, so it did end up being the dual-video card issue. :p

Now I have a different problem, lol. (Of course!) I've got Ubuntu loaded from the CD, but I can't get connected to the internet. I'm using a Linksys WUSB54G (ver 4) usb wireless card to connect, and I've gone in to make sure that the device is activated, but when I attempt to specify the correct network for it to connect to, it will freeze up. Here's exactly what I'm doing:

System > Administration > Networking > Wireless Connection
By default, it shows as not activated for whatever reason, and so I click on 'Properties' and check off 'Enable this connection'. Then under Wireless Settings, I specify the correct network name, and configure it to DHCP since I don't use a static IP address, and then click 'OK'. Once that's done, I click to 'Activate' that connection, and a window comes up saying 'Activating interface rausb0' with a loading bar, and that's when it freezes and I have to restart the system.

Maybe I'm just being thick-headed here, but I'm not quite sure what I'm doing wrong. I looked around on Google for drivers for this device, and all I really found was this: [http://web.ralinktech.com/ralink/Home/Support/Linux.html]("http://web.ralinktech.com/ralink/Home/Support/Linux.html"), which frankly confused the heck out of me.

Any assistance would be much appreciated! Thanks for your time. :)

---

### Post by thakayos21 on 2007-11-06
I really didn't give it that long of time to wait. I waited for about 5 minutes and gave up. I have a nVidia FX5200 series graphics card.

---

