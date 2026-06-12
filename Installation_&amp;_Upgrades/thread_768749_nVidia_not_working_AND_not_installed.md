---
title: "nVidia not working AND not installed"
date: 2008-04-26
forum: Installation &amp; Upgrades
---

### Post by Flying Mandarine on 2008-04-26
Hi everyone,

I have made a fresh install of Ubuntu 8.04, and very much like other persons wrote, the nVidia drivers are not recognized (I have a GeForce 9600 GT). I've created a new thread because some symptoms appear to be different:

- I can choose resolutions from 1280 x 800 down to 512 x 384 (I have an old 19' screen). I think it is vesa.
- If I go in Hardware drivers, it says that I don't use any proprietary drivers, even when I install nvidia-glx or nvidia-glx-new, which don't seem to be of much use.
- If I use EnvyNG, I need to install manually the nVidia drivers, and when it works* and I restart my computer, it's only then that it switches to low graphics mode, and I am not able to put more than 640 x 480. Worse, it sometimes makes the screen go crazy and the system freezes and I need to do a hard reboot.
- On a side note, my screen sometimes (especially when I reinstall 8.04 again, which I did three times last night) turns black and it seems I need to do a reboot. I'd say it's linked to the nVidia drivers problem, but how?

*It seems not to work according to which source I'm downloading from. Also, I wasn't able to use the Update Manager although it always says that it is downloading around 40 files; it's written my computer is up to date.

Lots of people seem to have the proprietary driver installed but not enabled, but I've just got absolutely nothing in my restricted drivers list.

Thanks in advance for your help!

Edit: Woops, I wonder if Installation & Upgrades is the most fitting board for that kind of problem?

---

### Post by chek2fire on 2008-04-26
Your card is supported only with the latest driver. Try to download them from nvidia and to install them.

---

### Post by Pumalite on 2008-04-26
Check this:
[http://ubuntuforums.org/showthread.php?t=733923](http://ubuntuforums.org/showthread.php?t=733923)

---

### Post by Flying Mandarine on 2008-04-27
Hey again,

I've installed the latest nVidia drivers (173.08, available at [http://www.nvidia.com/object/linux_display_ia32_173.08.html](http://www.nvidia.com/object/linux_display_ia32_173.08.html)) as you both suggested, and it seemed to work actually fine!

However, there are still two problems:

-I still cannot put my screen resolution higher than 1280 x 800 I believe. When I do (I can select it thanks to nvidia-settings), the screen just doesn't work anymore and turns back to the previous resolution after 15 seconds.

-More problematic: after some time, the screen shuts down (same symptom as above), but when I reboot the computer, it boots in low graphics mode and I am forced to reinstall the drivers once more. The worst is that it seems to be doing that more and more often: at first it worked fine for three or four hours, then for one, now only for half an hour. I've checked the temperature of the GPU, 41 degrees, I guess it's alright? But anyway, I don't say why it would mess up with the drivers that much? Also, it seems it's more prone to do this whenever I do something such as having multiple softwares opened, or starting a game.

Any ideas?

Thanks in advance again!

---

### Post by Pumalite on 2008-04-27
Start checking hardware. Do memtest first (at least 12 HRS)

---

### Post by Flying Mandarine on 2008-04-28
Hi,

Just a quick update as I was eventually able to change my resolution. I had to go in **Screens and Graphics** (which you can add to the Applications tab thanks to System => Preferences => Main Menu) for then changing from a generic screen to my specific screen.

Also, I don't know if that has a link with my screen-turning-off problem, but when I play TrackMania Nations Forever in WINE (I haven't tried doing anything else which uses as many resources), the keyboard and the mouse don't respond anymore, although my screen still displays what is happening and is not frozen. The only solution seems to be a hard reboot.

I will be launching memtest for 12 hours and I'll keep you up to date!

---

### Post by Pumalite on 2008-04-28
Another frequent cause of weird problems is the Power Supply and heating in general,

---

### Post by brigadoon on 2008-04-28
Another NVIDIA card another display problem. I had some issues with the upgrade as well. I posted my solution at...

[http://ubuntuforums.org/showthread.php?p=4828515#post4828515](http://ubuntuforums.org/showthread.php?p=4828515#post4828515)

It may or may not help you. It may give you some ideas.

---

### Post by foska on 2008-04-28
Thanks for that bit of info there FM.  You saved me from re-installing this OS because just before I read your post I was at my wits end!

> **Flying Mandarine said:**
> Hi,

Just a quick update as I was eventually able to change my resolution. I had to go in **Screens and Graphics** (which you can add to the Applications tab thanks to System => Preferences => Main Menu) for then changing from a generic screen to my specific screen.

Also, I don't know if that has a link with my screen-turning-off problem, but when I play TrackMania Nations Forever in WINE (I haven't tried doing anything else which uses as many resources), the keyboard and the mouse doesn't respond anymore, although my screen still displays what is happening and is not frozen. The only solution seems to be a hard reboot.

I will be launching memtest for 12 hours and I'll keep you up to date!

---

### Post by Flying Mandarine on 2008-04-29
Pumalite: Alright, here are the results of my Memtest86 test:

WallTime: 12:29:00
Cached: 2047M
RsvdMem: 84M
MemMap: e820-Std
Cache: on
ECC: off
Test: Std
Pass: 32
Errors: 0
Ecc Errs:

It looks like my problem doesn't come from here, does it?

Also, if I can believe what's written in the BIOS and in nvidia-settings, my CPU is at 25°C, my main board at 40°C and my graphics card at 39°C. It's all normal, isn't it? However, as my computer always crashes when I do something relatively resource-consuming, I have trouble thinking it could be something else than temperature. Or maybe it is still a problem with my screen since it just turns off?

brigadoon: Thanks for the link, I'm not sure this is linked since except for crashing, my graphics card works perfectly well now. I'll look more into it though.


Thanks in advance for everyone's help!

---

### Post by Flying Mandarine on 2008-04-29
Pumalite: How could I check if the problem comes from my power supply? And can it, given the CPU, main board and graphic card temperatures seem OK?

I let my computer running more than 24 hours and nothing happens if I do basic things (Pidgin, Firefox...), but as soon as I launch a game, it freezes the way I described above (keyboard and mouse don't work anymore), or if I do something a bit "bigger" in Firefox such as playing a Flash game or going on websites like stickam.com, the screen turns off.

However, the screen turning off is really abrupt (it can crash as soon as I do something), whereas the keyboard/mouse thing happen after several minutes or even hours, depending on if the computer has been on for a long time, I guess.

---

### Post by Pumalite on 2008-04-29
I don't remember if you upgraded or clean installed. But I recommend a clean install over an upgrade any day. I have 4 Hardies in clean installs working with Nvidia cards without a problem. As the Power Supplies go; it's like being an Emergency Room physician: if you think of doing a tracheotomy, then do it. In other words; if you suspect your power supply, then change it

---

### Post by Flying Mandarine on 2008-04-29
My computer is new, and so is my hard drive, so it's a clean install. I built it myself, that's the first time I did but I don't think I did anything wrong which would cause that kind of problem.


In case it can help, here's my config:


GeForce 9600 GT 512 mb (Twintech)
Power supply Advance EA4G-750, 750W
Dual Channel DDR2, XMS2, 2 x 1 Go, PC2-6400, Corsair
Hard drive DiamondMax 22, 500 Go, 7200 tpm, buffer 32 Mo, SATA II, Maxtor
Main board GA-P35C-DS3R ver. 2.1, socket 775, Gigabyte
Processeur Core 2 Quad Q9300 (2.50 GHz)


My power supply is new, so I don't think I need to change it (at least I hope!). But I have just been thinking about something: there weren't enough SATA things to plug from my power supply to my hard drive AND my DVD drive AND my DVD burner, so I had to buy some more wires to transform male plugs into females plugs (or the other way around).
Could this change be enough to make the power supply crash? It's a 175W after all.

Thanks,

---

### Post by russ18uk on 2008-04-29
> **Flying Mandarine said:**
> Pumalite: Alright, here are the results of my Memtest86 test:

WallTime: 12:29:00
Cached: 2047M
RsvdMem: 84M
MemMap: e820-Std
Cache: on
ECC: off
Test: Std
Pass: 32
Errors: 0
Ecc Errs:

It looks like my problem doesn't come from here, does it?

Also, if I can believe what's written in the BIOS and in nvidia-settings, my CPU is at 25°C, my main board at 40°C and my graphics card at 39°C. It's all normal, isn't it? However, as my computer always crashes when I do something relatively resource-consuming, I have trouble thinking it could be something else than temperature. Or maybe it is still a problem with my screen since it just turns off?

brigadoon: Thanks for the link, I'm not sure this is linked since except for crashing, my graphics card works perfectly well now. I'll look more into it though.


Thanks in advance for everyone's help!Your mainboard and CPU temperatures are the wrong way round. But don't worry they're fine. You should see your CPU go up a fair amount as you stress it and cool as you leave it idling. Didn't want to leave you slightly misguided :)

Do you have lm-sensors/ls-sensors installed and can take a look at your 12v line? Most decent power supplies will have seperate 12v rails sometimes 4 of them so you may be overloading 1 by daisychaining converters.

---

### Post by Pumalite on 2008-04-29
> **Flying Mandarine said:**
> My computer is new, and so is my hard drive, so it's a clean install. I built it myself, that's the first time I did but I don't think I did anything wrong which would cause that kind of problem.


In case it can help, here's my config:


GeForce 9600 GT 512 mb (Twintech)
Power supply Advance EA4G-750, 750W
Dual Channel DDR2, XMS2, 2 x 1 Go, PC2-6400, Corsair
Hard drive DiamondMax 22, 500 Go, 7200 tpm, buffer 32 Mo, SATA II, Maxtor
Main board GA-P35C-DS3R ver. 2.1, socket 775, Gigabyte
Processeur Core 2 Quad Q9300 (2.50 GHz)


My power supply is new, so I don't think I need to change it (at least I hope!). But I have just been thinking about something: there weren't enough SATA things to plug from my power supply to my hard drive AND my DVD drive AND my DVD burner, so I had to buy some more wires to transform male plugs into females plugs (or the other way around).
Could this change be enough to make the power supply crash? It's a 175W after all.

Thanks,

Your hardware is great, but it could cause problems because it's pretty new. You temperatures are fine. I've heard of people changing the order of the ports and solving their problem that way, but I don't know why.

---

### Post by Flying Mandarine on 2008-04-29
russ18uk: The other way around? You mean the CPU should be at 40 and the main board at 25? Well, I just check it out in the BIOS because I don't know how to check it under Ubuntu...

It crashed once again while surfing on Dailymotion. The screen turned off, but I believe the sound was also cut off, so I don't think it's actually linked to the screen if even the sounds turns off.

russ18uk: I just saw your edit, I've no idea what are lm-sensors/ls-sensors, 12v rails and daisychaining converters. I'll check out on the Internet and I'll try to look into that right now.

---

### Post by Flying Mandarine on 2008-04-29
Alright, I installed lm-sensors using [this post]("http://ubuntuforums.org/showthread.php?t=2780") (most of the steps from 3 to 5 can be ignored now, though). Here are the results of the test when my computer isn't too busy (some results, especially the lowest ones, can vary if I launch the test while doing other things at the same time):

> 
it8718-isa-0290
Adapter: ISA adapter
in0:         +1.12 V  (min =  +0.00 V, max =  +4.08 V)
in1:         +1.90 V  (min =  +0.00 V, max =  +4.08 V)
in2:         +3.38 V  (min =  +0.00 V, max =  +4.08 V)
in3:         +2.99 V  (min =  +0.00 V, max =  +4.08 V)
in4:         +0.13 V  (min =  +0.00 V, max =  +4.08 V)
in5:         +0.00 V  (min =  +0.00 V, max =  +4.08 V)
in6:         +0.10 V  (min =  +0.00 V, max =  +4.08 V)
in7:         +3.07 V  (min =  +0.00 V, max =  +4.08 V)
in8:         +3.09 V
fan1:       1115 RPM  (min =    0 RPM)
fan2:          0 RPM  (min =    0 RPM)
fan3:       1293 RPM  (min =    0 RPM)
fan4:        971 RPM  (min =    0 RPM)
temp1:       +41.0°C  (low  = +127.0°C, high = +127.0°C)  sensor = transistor
temp2:       +19.0°C  (low  = +127.0°C, high = +127.0°C)  sensor = thermal diode
temp3:        -2.0°C  (low  = +127.0°C, high = +127.0°C)  sensor = transistor
cpu0_vid:   +2.800 V


I've disconnected my DVD drive and my DVD burner before doing the test because I tried to see if removing some stuff linked to the power supply would prevent the computer from crashing, but opening Dailymotion and Youtube at the same time made the computer crash (no screen turning off, only keyboard and mouse not responding but sound and screen still working). 

That's a bit curious since russ18uk's explanation seemed plausible to me but I might be mistaken.

(Should I begin a new post (and where?) since the problem seems not to be linked with nVidia drivers anymore?)

---

### Post by Azraelthe7th on 2008-04-29
> **Flying Mandarine said:**
> Hi,

Just a quick update as I was eventually able to change my resolution. I had to go in **Screens and Graphics** (which you can add to the Applications tab thanks to System => Preferences => Main Menu) for then changing from a generic screen to my specific screen.

Also, I don't know if that has a link with my screen-turning-off problem, but when I play TrackMania Nations Forever in WINE (I haven't tried doing anything else which uses as many resources), the keyboard and the mouse don't respond anymore, although my screen still displays what is happening and is not frozen. The only solution seems to be a hard reboot.

I will be launching memtest for 12 hours and I'll keep you up to date!
Screens & Graphics?  I haven't seen that option since I upgraded to Hardy!

---

### Post by Flying Mandarine on 2008-04-30
Azraelthe7th: Well, believe me, that's one really useful tool. It allowed me to stop thinking about throwing my screen out the window!


I've searched on the Internet and it seems the brand for my power supply, Advance, is quite bad. I know it is a 750W and it should be more than enough, but get a look at this:

(Voltage, then Max. load)
**MAX 180 W:** +3.3V/28A; +5V/28A
**MAX 20W:** -12V/0.8A; +5Vsb/2.5A
**MAX 650 W:** +12V1/20A; +12V2/20A; +12V3/20A; +12V4/20A


Given my components and the voltage I provided above, would one of you have any idea of something which could be wrong?

Once again, thank you,

---

### Post by Azraelthe7th on 2008-04-30
> **Flying Mandarine said:**
> Azraelthe7th: Well, believe me, that's one really useful tool. It allowed me to stop thinking about throwing my screen out the window!


I know it is, it's just that it's not installed.  I did a synaptic search, and looked just about everywhere I could think of and it's simply not there. :confused:

---

### Post by Flying Mandarine on 2008-04-30
Azraelthe7th: Go to **System => Preferences => Main Menu**. Then click on **Other**, and enable **Screens and Graphics**.
Then go in **Applications => Other** and it should be good!

Oh! You mean, like, it can't even be enabled in the Main Menu? If not, maybe it's because you used Ubuntu 8.04 Beta and it wasn't implemented at the time?
I'm unsure.

---

### Post by Azraelthe7th on 2008-04-30
Acutally, I upgraded from Gutsy.

Anywho, I can run it using the terminal command "sudo displayconfig-gtk", and everything appears to be normal, but the nvidia drivers aren't detected for some reason, and for that reason I can't use it.

I guess I'll just wait until NVIDIA releases the full Linux drivers so that EnvyNG could go fetch them or something.

---

### Post by Flying Mandarine on 2008-04-30
Hey, I guess you tried downloading the latest drivers on [http://www.nvidia.com/object/linux_display_ia32_173.08.html](http://www.nvidia.com/object/linux_display_ia32_173.08.html) ?


I've unplugged everything I can unplug from my power supply (DVD drives, useless fans, etc.), but still it's crashing... I'm getting desperate!

---

### Post by Azraelthe7th on 2008-04-30
Do like me (and most of the high-end NVIDIA-Linux users) and wait until NVIDIA releases the full driver.  At least it'll be functional and stable.

---

### Post by shellback84 on 2008-05-01
After much trial and error I have learned that my new 8800 GT will not work in 7.10. I was hoping that 8.04 would change that and address my 8800 GT but from what I have read so far nothing has changed. I love Ubuntu and will not change my main operating system for a 3D video card. I duo boot using Grub loader, from Ubuntu to XP and use XP for gaming only. Everything else I do in Ubuntu. To get sound I had to pull my sound blaster XFI extrema gaming card and install my older 24 bit sound card to get sound. I am also waiting for that driver update as well. The drivers will come for both of these cards and I will play the waiting game for this killer operating system that is free. Life is good.

---

