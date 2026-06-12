---
title: "Problem logging into Aspire 5000"
date: 2020-01-20
forum: Installation &amp; Upgrades
---

### Post by cadtoon on 2020-01-20
Hi,
Laptop = Acer
Model = Aspire 5002
Series = 5000
Originally Win XP

This laptop only has CD. The only ISO I could find to fit is ubuntu 14.04.6 - server off [http://releases.ubuntu.com/14.04/](http://releases.ubuntu.com/14.04/)
Installed using entire partition eliminating XP.
Upgrade to 16.? LTS
Upgrade to 18.04.3 LTS
Installed Lubuntu-desktop

From there I cannot login. Screen change to black, changes back to login GUI.
CTR+ALT+F1
I can login and I have tried many of the suggestion in the Forum but still not there. 
I am not totally new to command line but not use to it and I fumble through it.
Please help if you know how to solve my issue.

Thx,
Bob

---

### Post by mörgæs on 2020-01-20
Hi, welcome to the fora.

It's safer to install a new Buntu than upgrading. The [minimal 19.10]("http://cdimage.ubuntu.com/netboot/19.10/") (also known as netboot) fits to a CD and I suggest that you try this one. 

Remember to use wired internet access while installing. 

At the end on the install process you are offered a GUI. I recommend a light one like X/Lubuntu over Ubuntu.

---

### Post by cadtoon on 2020-01-21
I went a different route.
First I found a program that boots from the CD, from there you can select various boot drives including USB. [https://www.plop.at/en/ploplinux/index.html](https://www.plop.at/en/ploplinux/index.html)
Next I found another program, PowerISO that can be used to make a bootable USB Stick. [https://www.poweriso.com/](https://www.poweriso.com/)
With this I installed MINT-Cinnamon. Got the same login problem but after a reboot it detected a video problem, reverted to 640x480 and the login worked.
I further researched I have SIS 661/741/760 PCI/AGP or 662/761Gx PCIE Video card. There are no Linux drivers that I can find. 

I don't think it matters which Linux flavour I install, none of them will work. 

Thanks for the recommendation.

---

### Post by guiverc on 2020-01-21
I see @[COLOR=#DD4814]mörgæs[/COLOR] has mentioned [COLOR=#000000]SIS 661/741/760 PCI/AGP[/COLOR] before, ie. 

[https://ubuntuforums.org/showthread.php?t=2371684](https://ubuntuforums.org/showthread.php?t=2371684)

Lubuntu 16.04 LTS, like all flavors of 16.04 LTS (excluding Kylin) had only 3 years of support, and is thus EOL.  Ubuntu 16.04 LTS server (no desktop) or desktop (Unity 7 desktop) still have support so maybe an option.

---

### Post by cadtoon on 2020-01-22
Thx,
I followed the link you provided, it looked to me that the problem was not solved.
I found on another forum that MINT 18.1 would work, it didn't and again only resolution offered is 640x480.
What I find strange is with all the different installs I have attempted, the resolution during install is better, perhaps 1024. I would be happy with that, even 800. 640 just doesn't cut it.

Bob

---

### Post by guiverc on 2020-01-22
If you were using a 'live' installer, boot it and work out what is running in that environment to achieve the 'perhaps 1024' resolution.  ie. what modules are present (`lsmod`), what driver is in use (`sudo lshw -C video` etc) and then compare with what gets installed.

 From any differences, I'd hope ideas on how to work towards would fix would become apparent (or at least to the 'install' resolution/screen-settings).

---

### Post by mörgæs on 2020-01-22
I'm delighted to see that my old SIS threads are still remembered. 

For a new Buntu release VESA drivers might be worth trying. Cadtoon, if you click the Old Hardware link in my signature and search for VESA there should be some instructions.

---

### Post by cadtoon on 2020-01-23
> **mörgæs said:**
> I'm delighted to see that my old SIS threads are still remembered. 

For a new Buntu release VESA drivers might be worth trying. Cadtoon, if you click the Old Hardware link in my signature and search for VESA there should be some instructions.

Hi mörgæs,
I have been fighting this for what seems like forever.
I actually went back to an old 16.04 to get what I thought was old Xrandx. I'm not sure what my Google search was but I stumbled onto this site:
[https://forum.peppermintos.com/index.php?topic=4776.0](https://forum.peppermintos.com/index.php?topic=4776.0)

I took the recommended text and created the xorg.conf file to the x11 folder and it worked! but only up to 1024x768
Is there new vesa driver available and if yes can you guide me on how to install?

Otherwise I can mark this as solved.

Bob

---

### Post by mörgæs on 2020-01-24
I don't think Vesa drivers are being further developed. They are available as-is but it's old technology.

If the solution is only possible in 16.04 I would not consider the problem solved but still thanks for considering to mark the thread.

---

### Post by cadtoon on 2020-01-25
I did a bare-metal backup of Mint 19, I will restore it this afternoon and see if following the same recommendations work. I will keep you posted.

The restore I did turns out to be Mint 10. What's strange is it resolution is even better 1280x800. I found a file in x11 named default-display-manager with one line /usr/sbin/gdm

Next I tried Mint 19.03, it had issues with the install screen so I didn't get it installed. Mint 18.3 did install but got graphics warning. copied xorg.conf 
Now it boots 1024x768 but still get warning.

Looked up gdm = **GNOME Display Manager**
I will try it use it.

Well that didn't work. I got a black screen, not a terminal, displaying gdm start commands with green [OK] but does nothing. I can alt-F3 to get terminal, and that screen flashes, making it almost impossible to type.

Going back to Mint 10 and do upgrades from there. See if I can get to 18

Well, I tried 19-64bit, wouldn't install, tried 18-64bit, wouldn't install. tried 19-32bit and it installed. I have tried everything I can find to do but the best I can get is 1024 with video acceleration error. I installed gdm3 to get 1024. I installed ssdm but can only get 640, I installed lightdm and again only 640.

Going to the Mint Forum to see if I can get help there.

I will keep you posted.

---

### Post by cadtoon on 2020-01-28
Hi,
I continued on the Mint forum. There are no video drivers for this Acer Laptop. They were dropped for some security reason.
I'm not sure I'll be back here, so thank you for all your assistance! 

You can check out my Mint forum post [https://forums.linuxmint.com/viewtopic.php?p=1751604#p1751604](https://forums.linuxmint.com/viewtopic.php?p=1751604#p1751604)

Regards,
Bob

---

### Post by mörgæs on 2020-01-29
It would surprise me if Mint offered other graphics drivers than Buntu but you are of course free to try.

I still expect that your best chance is a recent install combined with further VESA experiments.

---

### Post by cadtoon on 2020-01-29
Well that's it. I can get up to releases of both Lubuntu and Mint to version 18.3. As soon as I go to 19 I have all kinds of install problems. There was one release of Mint 3 that has Mint on a Debian kernel that runs fairly smooth but no one supports the SIS video chipset.

My advice to anyone with an SIS video, don't waste anymore time. My Aspire 5000 will be going to recycle.

---

### Post by mörgæs on 2020-01-30
Sorry to hear that. 

Lubuntu 18 is still supported.

A last purpose before recycling could be to use it for web surfing only while running an old OS. Listening to podcasts and other activity as long as no passwords are entered.

---

### Post by cadtoon on 2020-02-04
I got nowhere at Mint. Same problems, it all falls back on Linux. Somewhere back when there was a major change on the code they dropped the SiS support. Saying a security issue. More then likely a legal issue.

I went so far as to put the laptop in a pile of other electronics I have in the garage for recycle. I started going through a bunch of old external drives only to discover the backup software used does not work properly on my Win 8.1 system. I brought the Aspire back in the house and restored what I could of XP. Once I got the backup software working I dug deeper into reviving the XP OS. I currently have it all up-to-date with AVG antivirus installed. I know the system will always have security issues so no banking or anything else that requires a password to enter, including mapped drives to my NAS.

Conclusion: Don't bother wasting your time trying to get any Linux flavour running on an Aspire 5000.

---

