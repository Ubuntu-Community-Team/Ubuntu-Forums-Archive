---
title: "Help!! Toshiba Drivers for Keyboard, Touchpad, Display and Wireless!"
date: 2013-08-10
forum: Installation &amp; Upgrades
---

### Post by VegasTamborini on 2013-08-10
I'm not too sure what is important information here so I guess I'll just say as much as I can (You can skip down to the last paragraph if you can't be ass-ed reading my saga).

I have a Toshiba Satellite Laptop that I bought this year that shipped out with Windows 7 and have been meaning to switch to Ubuntu since I got it. I chose to install Ubuntu 12.04 because I recently had stability issues with 13.04 on another computer.

So I wiped my entire hard-drive (intentionally) a couple of days ago and attempted to make the switch. I made a bootable USB and tried to install by pressing F12 to change the boot device. My attempts to connect my wireless didn't work (to me it looked like driver issues) so I connected straight into my router with a networking cable, thinking that maybe the drivers might be part of the installation. Halfway into the installation the computer froze, so I rebooted and instead chose the 'Try Ubuntu' option and attempted to install that way. This time the touch-pad didn't work, so I connected a USB mouse and continued (Probably should have realised at this point that something was up).

This time the installation completed and so I rebooted to switch from 'Live USB' mode to the actual installation only to find that now the on-board keyboard, touchpad and wireless didn't function. So again I plugged in a network cable, USB mouse and keyboard. My first port of call was to install the updates from the update manager in the hope that drivers would download somewhere in that. It made it about halfway through when the screen froze (starting to look like the display drivers were also missing).

So I Googled a bit, spoke to some friends about it and came up with the idea to try Linux Mint 'Live USB' to try and narrow down the problem (still loyal to Ubuntu, I swear!!! hehe). The wireless and display worked on Mint, but still no keyboard and touch-pad. 

I left it for a day or two to have a think about it, and continued Googling in the meantime, I found a lot of people with similar(not identical) problems but got the feeling I could replace the keyword 'Toshiba' with any other brand and get a similar, very vocal community in the same position. I did find a page deep within Ubuntu official documentation that stated "*Ubuntu works very closely with Toshiba on the following products: **No results found**.*" that made me chuckle. The last few times I have turned on the laptop it freezes at the log-on screen; the touch-pad works, however the screen itself is not fully loaded and neither the on-board keyboard or the USB keyboard do anything, therefore making it impossible to type my password and log-on.

Anyway, I suppose my question is, WTF do I do now? I have my Windows 7 installation on yet another USB, however I like Ubuntu and want to get it working on my shiny new laptop. Are there any untested, beta drivers anyone knows about that might work? Is it even a driver problem? Maybe even post an answer to a question I haven't even asked if you think it'll help, I'm really stuck here. I am trying to install 13.04 as we speak, just in case that has an updated list of drivers. And for the record I do realise that some of this is my fault, and should have been bothered to partition my hard-drive first to test Ubuntu out.




Edit:

Alright, so I installed Ubuntu 13.04 and while some of my problems still persist, it is a lot better. The keyboard and touchpad only work intermittently (maybe 50% of the time), however I have had no further problems with the wireless or display drivers. I am happy about this, especially because it means that if the keyboard and touchpad work some of the time, it seems plausible that they are able to work all the time. 

I also found out that the touchpad is a "SynPS/2 Synaptics TouchPad" and the keyboard is a " AT Translated Set 2 keyboard" according to "System Profiler and Benchmark" So now I am looking for Synaptics drivers and AT Translated drivers. If anyone knows where to get these please feel free to post.




Also I thought I should put up some of my relevant specs:

Model:           Toshiba Satellite C875D Laptop
OS:               Ubuntu Desktop 64x 13.04
Processor:     AMD A6-4400M APU with Radeon(tm) HD Graphics        : 1400.00MHz
                     AMD A6-4400M APU with Radeon(tm) HD Graphics        : 1400.00MHz
RAM:             8GB

Touchpad:      SynPS/2 Synaptics TouchPad
Keyboard:      AT Translated Set 2 keyboard
BIOS:            InsydeH2O Version 1.20

---

