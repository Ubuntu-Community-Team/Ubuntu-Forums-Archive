---
title: "BIG problems with ATIx1950 drivers+Beryl"
date: 2007-02-25
forum: Installation &amp; Upgrades
---

### Post by fresch1 on 2007-02-25
Okay..
I Still have BIG problems with this..
This is what i have already tried:

This guide:
[https://help.ubuntu.com/community/BinaryDriverHowto/ATI]("https://help.ubuntu.com/community/BinaryDriverHowto/ATI")

I tred it but after reboot, the Splash screen freezes, and gives me a thin green, blue and red line across the screen.

I had to use ```
sudo dpkg-reconfigure xserver-xorg
```
and select "vesa" driver afterwards (If i select ATI i get the same Freeze at splash screen)


Then i tried this guide:
[http://technowizah.com/2006/10/debian-how-to-ati-drivers.html]("http://technowizah.com/2006/10/debian-how-to-ati-drivers.html")

I followed the guide, until i had to configure my xorg.conf file. When i pressed CTRL+ALT+F1 to reset X, i got at very "Colourful" screen that froze.
After reboot, i could start ubuntu, but when i wrote ```
fglxrinfo
```, i got the error, that my card wasnt installed, also ```
glxgears 
```didnt work.


Then i tried the Envy script:
[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

This script can automatic install Nvidia and ATI drivers for Ubuntu.
I rebooted Ubuntu, and startet Ubuntu in recovery mode, resulting in the terminal before the system starts.
From there i wrote ```
sudo envy
``` and a menu appeared.
i pressed "5" for ATI install, and selected the 33. Ati driver ( envy didnt have the newest driver).
After that the entire thing installed by it self, Ubuntu rebooted, and afterwards i tried the ```
fglxrinfo
``` command, and suddently my ATI x1950 card was identified.

```
glxgears
``` also worked like a Charm with a GREAT FPS, and ```
glxinfo | grep rendering

``` Shows ```
direct rendering: Yes
```

So, all working so far, although with the 33. driver.

But then i couldnt get Beryl to work, or XGL.
I installed Beryl xgl (i followed this guide [http://lhansen.blogspot.com/2006/10/...untu-edgy.html](http://lhansen.blogspot.com/2006/10/...untu-edgy.html))
Than rebooted, and selected the session "Xgl".

The background became black and white full of small dots and a white cross instead of the cursor, for 1 second, and then the normal desktop appears, and i cant see any xgl or beryl stuff, plus its suddently extremelyt slow (Resizeing windows ect. is extremely slow)...

I tried enableling Composite, but then the ```
glxgears
``` run VERY slow, and every guide says that i have to disable it.

 
Later i read some quotes that i didnt really understand (im still a HUGE linux noob)
> AIGLX doesn't work AFAIK with fglrx as fglrx doesn't support composite. If you want 3D Desktop with fglrx then use Xgl. the radeon driver works with AIGLX if you want to sacrifice that bit of performance.

and another quote 

> I don't know if anyone said it but: you won't get direct rendering when running XGL. NEVER. It's impossible. To run beryl with direct rendering, you must run intel graphics, nvidia, or ati open-source drivers though AIGLX (included in xorg 7.1).

Cheers! 

Im still stuck..


Then a guy told me to try this :

[QUOTE=antidrugue]I am not sure what is wrong exactly with your setup, but I can tell that I got **Compiz + AIGLX** to work in Fedora Core 6 on an ATI card (ATI Radeon 9600).

Both the free "radeon" driver and the proprietary "fglrx" (using freshrpms packages) worked right away and gave me a working "3D desktop", with dual-monitors may I had.



That is only necessary if you want to use Compiz/Beryl directly, without AIGLX or XGL backend. It is by no mean a requirement in order to get a full 3D desktop working.

Just check the **AIGLX** part of [_this tutorial_](http://technowizah.com/2006/10/debian-how-to-aiglx-compiz.html) for more info on how to properly configure your **/etc/X11/xorg.conf** file for Compiz/Beryl support.[/QUOTE]


But i dont know what to do..


Please. Dont  someone have a simple guide that works?

I have had problems with this for 2 days and nights now.
Im really tired.. :/

---

### Post by pay on 2007-02-26
Your card is not supported by the open source radeon driver and I'm not even sure that it is supported by the fglrx driver. What version of the driver are you trying?

---

