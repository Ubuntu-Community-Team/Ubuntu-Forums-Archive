---
title: "[SOLVED] acer 4520 8.10 upgrade"
date: 2008-10-31
forum: Installation &amp; Upgrades
---

### Post by xchronox on 2008-10-31
So... I'm at the end of my rope guys. I updated today... 
Basically it's killed my wireless, an atheros card that was working with the madwifi driver in 8.04. I've tried uninstalling, reinstalling, different versions of madwifi, blacklisting... nothing has worked, it hasn't even gotten as far as detecting the card.
That's the first problem...
The second is I have firefox set up as a single menubar... it resets to default every time I close it. The browser version is the same on my desktop 8.04, so that leads me to believe it has something to do with the update.

I've already fixed the virtualbox and the nvidia drivers, i had to reset a few programs like evolution and pidgin... i'm just about to tears people. Please help.

---

### Post by xchronox on 2008-10-31
Bump, I'm going insane

---

### Post by Partyboi2 on 2008-10-31
Does this apply to you:
> **Atheros ath5k wireless driver not enabled by default**

  The version of the ath5k driver for Atheros wireless devices included in Linux 2.6.27 interferes with the use of the madwifi driver for some wireless devices and as a result has been disabled by default. Many Atheros chipsets will work correctly with the madwifi driver, but some newer chipsets may not, and the madwifi driver may not work with WPA authentication. If you have an Atheros device that does not work with madwifi, you will want to install the linux-backports-modules-intrepid-generic package, which includes an updated version of the ath5k driver. While not installed by default, this linux-backports-modules-intrepid-generic package is included on the Ubuntu 8.10 CD and DVD images for ease of installation. 


---

### Post by xchronox on 2008-10-31
thanks for the reply, but it doesn't seem to apply here... i installed said package and nothing has changed.

---

### Post by blakamin on 2008-10-31
As another 4520 owner, I recommend pressing your wireless button, rebooting and then trying this... [http://ubuntu-utah.ubuntuforums.org/showpost.php?p=5711824&postcount=6](http://ubuntu-utah.ubuntuforums.org/showpost.php?p=5711824&postcount=6)
If that doesn't work, hit the wireless button and try it one more time. 
Dunno about you, but my wireless button LED doesn't work so I couldn't tell if it was on or off.

Worked for me.

Funny thing is that wireless worked fine in the alphas..:(

---

### Post by xchronox on 2008-10-31
You're my hero!! you may have just saved a life tonight 

any ideas about my firefox issue? i still cant seem to make the UI customization stick.

---

### Post by girishadat on 2009-02-08
Hi friends, I recently installed Ubutnu 8.10 on my Acer 4520. Everything working fine. The only problem I am facing is the Acer 4520's original problem, that the nVidia GPU shoots up to 70 degrees temperature. I tried installing latest nVidia driver(v177), nVidia settings and enabled the coolbits. Now I can see a Clock Frequencies tab in NVidia X Server Settings GUI. The problem is any change made there, as root, is not getting set, when I click apply. On more, but most importantly, the PowerMizer is always set to the maximum frequency, i.e. 350MHz. Will it change automatically to lower frequencies to reduce temperature of GPU? Or is there any way to reduce GPU clock?

See the option changes I made in /etc/x11/xorg.conf
[INDENT]> 
Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    Option "RegistryDwords" "PowerMizerLevel=0×1"
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    SubSection     "Display"
        Depth       24
    EndSubSection
    Option "Coolbits" "1"
EndSection[/INDENT]

Anyone solved this problem? Any 4520 owner could reduce the GPU temperature so they can make it a real "lap"top?

---

### Post by xchronox on 2009-02-08
Well, I've checked my own system, and it does seem to climb a bit. It hasn't hit 70 yet, but I wonder, maybe there's an option in the bios.

---

### Post by xchronox on 2009-02-08
this forum might help out [http://ubuntuforums.org/showpost.php?p=5711084&postcount=6](http://ubuntuforums.org/showpost.php?p=5711084&postcount=6)

---

### Post by girishadat on 2009-02-11
> **xchronox said:**
> this forum might help out [http://ubuntuforums.org/showpost.php?p=5711084&postcount=6](http://ubuntuforums.org/showpost.php?p=5711084&postcount=6)

Hi friend, thanks for the quick reply. I did what is given in the post. Now the gpu clock changed to 100MHz. I did resetting my BIOS to defaults. But the temperature is still @ 70-71C. Any idea? My CPU is working in 52-55C range and it is an AMD...!


See my screenshot below.

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=102975&stc=1&d=1234378455[/IMG]

:(

---

### Post by xchronox on 2009-02-11
Well... sorry man, I can't seem to find a way to lower the temp... you may want to start a new thread as this one is mark [solved] hopefully someone with more knowledge will pick it up and give you a hand.

---

### Post by girishadat on 2009-03-13
Hmm... I decided to get used to with my lappy's heating problem...

Any one got another problem when you give shutdown for Ubuntu 8.10 on an Acer 4520 lappy? For mine, it is not getting "switched-off"...! It first gives a unloading some fs... etc commands in a black screen, and then gives a scrolling screen as we get on boot, with a beautiful Ubuntu label...  When the scrolling orange bar reaches the end, it gets stuck there, it is not powering off by itself. To get rid of the screen I have to tap Ctrl key twice, after which it powers off the LCD screen and the LEDs...!

Another problem is with hibernation. It is taking more time to load after hibernation than a clean booting... :D

I have been using a Linux, for last 4-5 years, with dual boot with Windows with my lappy or PC. Features of XP, like quick loading when hibernated makes me sticking to Windows again, leaving my high performing 64 bit Ubuntu behind... :(, leaving my wish to move completely to Linux... Anyway U8.10 is improved a lot than it's earlier versions... It has reached somewhere near Windows XP... But I feel Windows is again a little ahead in usability... :(

---

### Post by xchronox on 2009-03-13
Hey, so I haven't encountered the slow hybernation problem you're having, but a while ago I did find a fix for the shut down problem, it's in  [this post]("http://ubuntuforums.org/showpost.php?p=6266400&postcount=21"). Hope that helps out a bit. Maybe Ubuntu 9.04 will be a better fit for the 4520, I hear new nvidia drivers are being developed.

---

### Post by girishadat on 2009-03-14
Thanks xchronox, I could solve that problem also, following your steps. But when I checked my BIOS has two SCSI operating modes - IDE and AHCI, not the ACPI mode as you said in the post; and I found it is working in both the configurations.

Again, Thanks a lot...! :)

---

