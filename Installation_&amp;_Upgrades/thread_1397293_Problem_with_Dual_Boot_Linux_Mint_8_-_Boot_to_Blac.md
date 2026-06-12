---
title: "Problem with Dual Boot Linux Mint 8 - Boot to Black Screen"
date: 2010-02-03
forum: Installation &amp; Upgrades
---

### Post by KingFeckless on 2010-02-03
Hi,

I hope I can find some help here, also keep in mind that I am a linux noob. After installing linux mint 8 (main, 32bit) and starting it via grub I end up having a black screen (no error message). Every support post I found seem to point in the direction of corrupted data so I checked the checksum of the download and used a live CD (burned with slowest speed) and also live USB, both with the same results. Is there something else I should check?

(hda -> XP / hdb -> Linux Mint 8)

Greets
Stefan

---

### Post by ajgreeny on 2010-02-03
Does the black screen have a flashing command line text or is it just totally black?

If you get to the command line it may be a graphics card driver problem or something similar, but to help further it will help to have more information on the hardware, particularly the graphics card, but as much as you know about.

If the live CD works and gives you a desktop (you don't say if it does or not) it should be possible to get the system up and running, but as I say, more info is needed, so from the desktop of the live CD run in terminal ```
sudo lshw > hardware.txt
``` and send the resulting hardware.txt file to us here as an attachment.  To do that use the paperclip icon on the reply text box, navigate to the file and upload it, just like an email atachment.

---

### Post by KingFeckless on 2010-02-03
Ah I forgot that, the live CD as well as live USB work fine. After I start LM8 I get a "_" in the top left corner for about a second and then it is just a pitch black screen.

Before I installed LM8 I was using LM7 without a problem.

I will post the hardware.txt here once I get home.

---

### Post by KingFeckless on 2010-02-03
As promised attached the hardware.txt.

While I read through that file I noticed it does not mention the grafic card (ATI Radeon 9600)....this might be a hint.

---

### Post by ajgreeny on 2010-02-03
Yes it does mention the graphic card right down the bottom of the file, as expected.

I think you may be right about that being the problem, however, and suspect that you may be able to get things going if you stop compiz running, ie desktop effects, or use a screen res of no more than 1024x768, or a colour depth of 16bit instead of the usual default of 24bit.

It seems, however that you can not even get to the same situation as I did with my ATI 9200 SE card, where I had a black screen background, but the panels still showed, and non maximised windows still appeared correctly.  From that I could use Alt+F2 to get the run dialog and stop compiz with **metacity --replace** but it appears that you do not get a screen at all from which to try that.

Can you login to the command line after Ctrl+Alt+F1?  If so, do it and then you can try to stop compiz by using the command I just gave.  The problem may be that with no gui, that command will not work.  So perhaps as a final resort you could try ```
sudo apt-get remove compiz
```If that does not help after a restart of x or reboot, you can always add it back

A manual edit of xorg.conf may get you somewhere as well, here's mine just to show what I needed to get things running with compiz. 
```
Section "Device"
    Identifier     "Configured Video Device"
    Driver         "ati"
EndSection 

Section "Monitor"
    Identifier    "Configured Monitor"
            HorizSync    30-80
            VertRefresh    50-75
EndSection

Section "Screen"
    Identifier    "Default Screen"
    Monitor        "Configured Monitor"
    Device        "Configured Video Device"
    DefaultDepth    16
    SubSection "Display"
        Modes        "1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
EndSection
```
 Put your own figures in, of course.  Still not as good as 9.04, however, which I use as my main OS.  Perhaps we both need new graphics cards!

But first let's get you a desktop!

---

### Post by KingFeckless on 2010-02-04
Yeah I pretty much have no screen at all, but will try what you said later at home.

Yesterday, I tried reinstalling the previous version of Mint (7 - Gloria) reading some of the stuff about Radeon problems here and couldn´t get any system running. Re-re-installing Mint 8 put me in a limbo between grub 1 and 2 I guess. I tried to get rid of grub and start fresh with using "fixmbr" but still get a grub error. I will have to do some installing later today.....*sigh* 

(still want to change, I hate my XP with a passion, not to mention how it hates me)

---

### Post by KingFeckless on 2010-02-04
Hmm.....

when I use ctrl+alt+f1 I get back to the blinking "_" so no chance to enter something. I then used the recovery version which pretty much works. "StartX" and I have my desktop. Strangely though I do not have a xorg.conf. Could that be one of the differences between ubuntu and mint.....

---

### Post by ajgreeny on 2010-02-04
Neither ubuntu nor mint have an xorg.conf as default.  If you have one it will only be after installing a proprietary driver, or as in my case, because I made the file to accommodate my display problems, and reduce the colour bitrate to 16.

Have you tried your own version of my xorg.conf file, ie with your own figures unstead of mine?  If not, try it and you may have a bit more luck.

---

### Post by KingFeckless on 2010-02-04
I just did, but it did not work that well. I somehow was able to create that list and it listed nvidea as the default which kept me from booting and almost made me reinstall. Makes me wonder if there is a general driver problem on my system. Is there a way I can force an error message?

---

### Post by KingFeckless on 2010-02-04
Okay, this is strange. I was playing with the boot obtions in Grub and deleted "quiet" and "splash" and what can I say....it boots. Not sure why though.

Is there something one can do in the appropriate driver section to at least have some Radeon 3d power?

---

