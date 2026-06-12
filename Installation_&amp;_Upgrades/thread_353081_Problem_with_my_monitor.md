---
title: "Problem with my monitor"
date: 2007-02-04
forum: Installation &amp; Upgrades
---

### Post by Banipal on 2007-02-04
I have problems running Ubuntu on my computer. I downloaded "ubuntu-6.10-desktop-i386.iso " this image and burned it on a cd and started to install.But when after clicking install button my monitor gives "cannot display this video mode" error. Then i downloaded "ubuntu-6.10-alternate-amd64.iso" and successfully installed Ubuntu via this cd. But this time it gives the same error while starting ubuntu. 

I googled and tried to find some solutions. My monitor is "Dell E173FP" and i saw that some people also has the same problem running ubuntu with dell monitors. I edited xorg.conf and erased the modes(resolutions) that my monitor does not support. Then i added a line indicating my monitors refresh rate, 
(This is not my conf file, i edited someone's)
[PHP]Section "Monitor"
Identifier "DELL E173FP"
Option "DPMS"
HorizSync 30-80 //I added this 
VertRefresh 60-70 //I added this too, my monitor support refresh rates in this region
EndSection

Section "Screen"
Identifier "Default Screen"
Device "Ati Radeon 9600"
Monitor "DELL E173FP"
DefaultDepth 24
SubSection "Display"
Depth 1
Modes "1280x1024" "1152x864" "1024x768" "800x600"    //I deleted other modes
EndSubSection
SubSection "Display"
Depth 4
Modes "1280x1024" "1152x864" "1024x768" "800x600"
EndSubSection
SubSection "Display"
Depth 8
Modes "1280x1024" "1152x864" "1024x768" "800x600"
EndSubSection
SubSection "Display"
Depth 15
Modes "1280x1024" "1152x864" "1024x768" "800x600"
EndSubSection
SubSection "Display"
Depth 16
Modes "1280x1024" "1152x864" "1024x768" "800x600"
SubSection "Display"
Depth 24
Modes "1280x1024" "1152x864" "1024x768" "800x600"
EndSubSection
EndSection [/PHP]

Then one of my friend advised me to add vga=795 to menu.lst 's kernel part, i tried it with 794 and 795 both. But this time my monitor does not give an error but it stays black.

I could not solve this problem. Need help :( (I am a beginner in linux :( )

[IMG]http://img214.imageshack.us/img214/7480/propnz6.jpg[/IMG]
[IMG]http://img214.imageshack.us/img214/1932/atinh6.jpg[/IMG]

---

### Post by shareMenaPeace on 2007-02-04
What happen when you remove the added lines?

```
HorizSync 30-80 //I added this 
VertRefresh 60-70 //I added this too, my monitor support refresh rates in this region 
```

---

### Post by Banipal on 2007-02-04
> **shareMenaPeace said:**
> What happen when you remove the added lines?

```
HorizSync 30-80 //I added this 
VertRefresh 60-70 //I added this too, my monitor support refresh rates in this region 
```

Nothing unfortunately :( The result was same

---

### Post by Banipal on 2007-02-04
I forgot to say, I also tried the resolutions in the boot screen when live cd is inserted by pressing F4. I really need help, I should have installed a linux distribution by now because of one of my courses :(

I tried a Turkish linux distribution "Pardus", my monitor gave the same error when i choose to install :twisted:

---

### Post by zellboy on 2007-02-04
I am very new myself to linux, however I had a similar problem when trying to install Fedora on my work tower.. AMD64 on an Asus PCI-E board with Dos already installed, with dual monitors. After several attempts the same thing continued to happen. I would get "Sync out of range" on my screens. After installing Ubuntu I continued to recieve the message during install. End result, we figured to disconnect the other monitor from the card. Booted up and installed perfectly. Now just to get the resolution up plus dual monitors again, audio and a few other thing, hope this helps some.

---

