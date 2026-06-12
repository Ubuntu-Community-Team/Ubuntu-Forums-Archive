---
title: "Adobe Flash Player 10.0.12.36 Final was released. Will it be in Ibex?"
date: 2008-10-15
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by victorche on 2008-10-15
[http://www.adobe.com/shockwave/download/download.cgi?P1_Prod_Version=ShockwaveFlash&P2_Platform=Linux](http://www.adobe.com/shockwave/download/download.cgi?P1_Prod_Version=ShockwaveFlash&P2_Platform=Linux)

Enjoy :)

It is marked as final. There is a .deb for Ubuntu 8.04+ also ;)

---

### Post by philinux on 2008-10-15
I would think so but Thursday, October 16, is the archive freeze day.

Thanks for the heads up though it's now installed on my hardy drive.

---

### Post by plun on 2008-10-15
Works just fine...

Heavy ads :)

[http://www.adobe.com/products/flashplayer/](http://www.adobe.com/products/flashplayer/)


Manual for installing

[http://www.adobe.com/products/flashplayer/productinfo/instructions/](http://www.adobe.com/products/flashplayer/productinfo/instructions/)

Both deb and apt is supported.


(I have no hope that this one is included after the OO3 debacle :()

---

### Post by SunnyRabbiera on 2008-10-15
well with adobe finally providing a native ubuntu package we may not have to worry about repositories no more.

---

### Post by taavikko on 2008-10-15
> **plun said:**
> Works just fine...

Heavy ads :)

[http://www.adobe.com/se/products/flashplayer/](http://www.adobe.com/se/products/flashplayer/)


:()

Thanks for the Swedish link ;) Even though I'm one third Swedish, hard time to understand it, what might people from other countries like it :)

---

### Post by plun on 2008-10-15
> **taavikko said:**
> Thanks for the Swedish link ;) Even though I'm one third Swedish, hard time to understand it, what might people from other countries like it :)

No, I changed it to english.... those "dam--d" language redirects" :)

Turn down volume maybe....

---

### Post by philinux on 2008-10-15
LOL yes turn the volume down and backports come to mind.

However it's so easy to install.

---

### Post by plun on 2008-10-15
> **philinux said:**
> LOL yes turn the volume down and backports come to mind.


Well... turn up again and enjoy:)

[http://www.youtube.com/watch?v=xjvfUEOr0N4&feature=related](http://www.youtube.com/watch?v=xjvfUEOr0N4&feature=related)

---

### Post by philinux on 2008-10-15
> **plun said:**
> Well... turn up again and enjoy:)

[http://www.youtube.com/watch?v=xjvfUEOr0N4&feature=related](http://www.youtube.com/watch?v=xjvfUEOr0N4&feature=related)

Well thats better. :)

---

### Post by bash on 2008-10-15
Wow ... they finally provide a .deb package. I am surprised. Now we just need a 64-bit, a lot less crashes and fullscreen hardware support working with compiz and we have a good flashplugin. ;)

---

### Post by plun on 2008-10-15
> **philinux said:**
> Well thats better. :)

Intrepid is up and running with all systems....:)

CPU values

~30% Firefox

~8%  Xorg

Total ~45% CPU....  much better then earlier Flash versions.

---

### Post by philinux on 2008-10-15
Yep and full screen is much better.

---

### Post by The Grum on 2008-10-15
Has the APT download worked for anyone? I tried it on intrepid and got "could not find package adobe-flashplugin".

The .deb installs great. Fails miserably when playing flash video (BBC News website)

---

### Post by bash on 2008-10-15
> **The Grum said:**
> Has the APT download worked for anyone? I tried it on intrepid and got "could not find package adobe-flashplugin".

The .deb installs great. Fails miserably when playing flash video (BBC News website)

Hmm ... videos work fine for me.

---

### Post by cl333r on 2008-10-15
> **victorche said:**
> [http://www.adobe.com/shockwave/download/download.cgi?P1_Prod_Version=ShockwaveFlash&P2_Platform=Linux](http://www.adobe.com/shockwave/download/download.cgi?P1_Prod_Version=ShockwaveFlash&P2_Platform=Linux)

Enjoy :)

It is marked as final. There is a .deb for Ubuntu 8.04+ also ;)

The Linux guys always know the latest minute news.. unbelievable :)

---

### Post by mindhaq on 2008-10-15
> **philinux said:**
> LOL yes turn the volume down and backports come to mind.

However it's so easy to install.

You seem to be running it on Hardy 64. How did you install it? I just get a wrong architecture error :(

---

### Post by philinux on 2008-10-15
Hardy 64, Intrepid 32.

I reckon for my needs 32 bit is easier and a tad quicker. Will be going 32 bit on disk 1 with Intrepid and disk 2 will get the Jackalope. LOL

---

### Post by nanog on 2008-10-15
I hope ubuntu makes 64 bit default. Its time.

---

### Post by NoFearDJB on 2008-10-15
+1 fast track into 8.10, Flash 10 is leaps and bounds better than version 9!

---

### Post by psyke83 on 2008-10-15
Guys, **don't** install the deb from Adobe's site. It doesn't integrate properly with nspluginwrapper and "update-alternatives" (which will cause problems for 64 bit users).

This is the bug report: [https://bugs.launchpad.net/ubuntu/+source/flashplugin-nonfree/+bug/283669](https://bugs.launchpad.net/ubuntu/+source/flashplugin-nonfree/+bug/283669)

Fabien Tassin has packaged flash 10 and nspluginwrapper 1.2.0 in his [PPA]("https://launchpad.net/~fta/+archive"), which are pending for approval in the official repositories.

---

### Post by ubulette on 2008-10-15
I just pushed flashplugin-nonfree 10.0.12.36 and nspluginwrapper 1.1.2 to Intrepid.
Just in time.

---

### Post by psyke83 on 2008-10-15
> **ubulette said:**
> I just pushed flashplugin-nonfree 10.0.12.36 and nspluginwrapper 1.1.2 to Intrepid.
Just in time.

Awesome :). Many thanks, man.

---

### Post by Kalinda on 2008-10-15
> **philinux said:**
> Yep and full screen is much better.

Really? Because when I try to run Flash 10 at full screen, Firefox just crashes. :( It did the same with the betas and RCs. And I'm not even running Compiz. It's really annoying because I wanted to know if it would be all sluggish and crappy at full screen like Flash 9 was.

Can anyone help me?

---

### Post by philinux on 2008-10-15
> **Kalinda said:**
> Really? Because when I try to run Flash 10 at full screen, Firefox just crashes. :( It did the same with the betas and RCs. And I'm not even running Compiz. It's really annoying because I wanted to know if it would be all sluggish and crappy at full screen like Flash 9 was.

Can anyone help me?

Sounds like a graphics driver problem What are you're full specs?

---

### Post by Kow on 2008-10-15
> **ubulette said:**
> I just pushed flashplugin-nonfree 10.0.12.36 and nspluginwrapper 1.1.2 to Intrepid.
Just in time.

And you sir/mam are awesome.

---

### Post by jblackhall on 2008-10-15
Hasn't flashplugin-nonfree been the Flash 10 RCs for quite some time in Intrepid?  I just assumed this would be included since they've been prepping for it.

---

### Post by Kalinda on 2008-10-15
> **philinux said:**
> Sounds like a graphics driver problem What are you're full specs?
I've got an nVidia 6600 and I'm using version 169 of the driver, the same one that came with Hardy... trying to upgrade it or use the one off the nvidia website doesn't work.

Also, here's my xorg.conf:

```
# nvidia-settings: X configuration file generated by nvidia-settings
# nvidia-settings:  version 1.0  (buildd@vernadsky)  Thu Jun  5 09:26:53 UTC 2008

# nvidia-xconfig: X configuration file generated by nvidia-xconfig
# nvidia-xconfig:  version 1.0  (buildmeister@builder3)  Thu Feb 14 18:20:37 PST 2008

Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0" 0 0
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
EndSection

Section "Files"
    RgbPath         "/usr/lib/X11/rgb"
EndSection

Section "Module"
    Load           "dbe"
    Load           "extmod"
    Load           "type1"
    Load           "freetype"
    Load           "glx"
EndSection

Section "ServerFlags"
    Option         "Xinerama" "0"
EndSection

Section "InputDevice"

	# generated from default
    Identifier     "Mouse0"
    Driver         "mouse"
    Option         "Protocol" "auto"
    Option         "Device" "/dev/psaux"
    Option         "Emulate3Buttons" "no"
    Option         "ZAxisMapping" "4 5"
EndSection

Section "InputDevice"

	# generated from default
    Identifier     "Keyboard0"
    Driver         "kbd"
EndSection

Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "LG W2242"
    HorizSync       30.0 - 83.0
    VertRefresh     56.0 - 75.0
 # 1680x1050 @ 54.00 Hz (GTF) hsync: 58.48 kHz; pclk: 131.00 MHz
    Modeline "1680x1050_54.00"  131.00  1680 1784 1960 2240  1050 1051 1054 1083  -HSync +Vsync
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    Option         "NoLogo" "True"
EndSection

Section "Device"
    Identifier     "Videocard0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 6600"
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Videocard0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView" "0"
    Option         "TwinViewXineramaInfoOrder" "CRT-0"
    Option         "metamodes" "1680x1050 +0+0; nvidia-auto-select +0+0"
    Option         "AllowNon60HzDFPModes"
    Option         "UseEdidFreqs" "false"
    SubSection     "Display"
        Depth       24
	Modes	   "1680x1050_54"
    EndSubSection
EndSection
```

The reason it's set to 54Hz is because it's the only way to fix the video tearing I get when I turn on the nvidia driver.

I'm not using Compiz.

---

### Post by crjackson on 2008-10-15
> **psyke83 said:**
> Guys, **don't** install the deb from Adobe's site. It doesn't integrate properly with nspluginwrapper and "update-alternatives" (which will cause problems for 64 bit users).

This is the bug report: [https://bugs.launchpad.net/ubuntu/+source/flashplugin-nonfree/+bug/283669](https://bugs.launchpad.net/ubuntu/+source/flashplugin-nonfree/+bug/283669)

Fabien Tassin has packaged flash 10 and nspluginwrapper 1.2.0 in his [PPA]("https://launchpad.net/~fta/+archive"), which are pending for approval in the official repositories.

So would there be any problems using the adobe package from their website if I'm using Hardy 32-bit?

---

### Post by exploder on 2008-10-15
crjackson, I have Flash 10 final running in LinuxMint 5 which is based on Hardy. Flash 10 works great here, better image quality and much better audio quality as well.Flash 10 final is a keeper!

---

### Post by crjackson on 2008-10-15
> **exploder said:**
> crjackson, I have Flash 10 final running in LinuxMint 5 which is based on Hardy. Flash 10 works great here, better image quality and much better audio quality as well.Flash 10 final is a keeper!

Cool - I'll give it a spin. Did you install over top of your current flash install, or did you remove flashplugin-nonfree prior to the install of the deb?

---

### Post by Kalinda on 2008-10-15
> **Kalinda said:**
> I've got an nVidia 6600 and I'm using version 169 of the driver, the same one that came with Hardy... trying to upgrade it or use the one off the nvidia website doesn't work.
Okay, I managed to upgrade to the latest nvidia driver, with or without it being 54Hz. It still doesn't work.

I turned off the drivers, it doesn't work... 

:confused:

---

### Post by sharp65 on 2008-10-15
I just updated to the latest flash when installing the latest updates for intrepid and now flash doesn't seem to be working.

---

### Post by exploder on 2008-10-15
> Cool - I'll give it a spin. Did you install over top of your current flash install, or did you remove flashplugin-nonfree prior to the install of the deb?

crjackson, I just installed over the old version, afterwards I found the old version in Synaptic under "residual config" and removed it.

---

### Post by talkingwires on 2008-10-15
> **plun said:**
> (I have no hope that this one is included after the OO3 debacle :()Debacle? The Ubuntu developers *wanted* OO3 in Intrepid, but that was before it's release date started slipping. Here, [check it out]("http://ubuntuforums.org/showpost.php?p=5965539&postcount=28").

---

### Post by exploder on 2008-10-15
plun, I would not worry about OO 3. The new version will either show up as an update or be in the backports repo. I would exercise patience on this.

---

### Post by crjackson on 2008-10-15
> **exploder said:**
> crjackson, I just installed over the old version, afterwards I found the old version in Synaptic under "residual config" and removed it.

Thanks - It's on my todo list for when I get home from work tonight. If you don't hear from me, that means it went perfect and I'm pleased :)

---

### Post by plun on 2008-10-16
@talkingwires and exploder

I am just dissipointed and for my personal needs I can compile it from source if necessary. (crazy nerd....)

Its about these usergroups which just installs and dont change anything:

[http://www.librarian.net/stax/2042/do-you-ubuntu/](http://www.librarian.net/stax/2042/do-you-ubuntu/)


What is a backport for them ?


(Adobe Flash was important for these)

---

### Post by | MM | on 2008-10-16
Hi,

My way of having an up to date flash on x86_64 is:

1) Install [FONT="Courier New"]flashplugin-nonfree[/FONT] from the repositories so you get the needed 32bit support files.

2) then when a new version of [FONT="Courier New"]libflashplayer.so[/FONT] is released, i just replace the old version in [FONT="Courier New"]/usr/lib/flashplugin-nonfree/[/FONT].


Works every time.  But that may be irralavent now... because i think they've started releasing DEB files.

---

### Post by infinito on 2008-10-16
This is what I get with "about:plugins" in Firefox:

```
Shockwave Flash

    Filename: libflashplayer.so
    Shockwave Flash 10.0 r12
```

Did they forgot to update the version string?

---

### Post by ubulette on 2008-10-16
> **infinito said:**
> This is what I get with "about:plugins" in Firefox:

```
Shockwave Flash

    Filename: libflashplayer.so
    Shockwave Flash 10.0 r12
```

Did they forgot to update the version string?

technically no, 10.0.12.36 is still 10.0 r12 but don't worry, it's the right one:

```
$ strings /usr/lib/flashplugin-nonfree/libflashplayer.so | grep 10.0
Shockwave Flash 10.0 r12
LNX 10,0,12,36

```

---

### Post by talkingwires on 2008-10-16
> **plun said:**
> What is a backport for them ?From the [developer's post]("http://ubuntuforums.org/showpost.php?p=5965539&postcount=28") I originally linked to: > 
That said I will be uploading openoffice.org 1:3.0.0-2ubuntu1 to the openoffice-pkgs PPA in a few hours after the test build completes. And it will probably go into intrepid-backports in about a month.

---

### Post by crjackson on 2008-10-16
Installed it last night. Working great so far.

---

