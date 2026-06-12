---
title: "Setting up a Dell Inspiron-11 3000 Series with Ubuntu 16.04."
date: 2016-10-25
forum: Installation &amp; Upgrades
---

### Post by irv on 2016-10-25
[SIZE=5][CENTER][COLOR="#0000CD"]Setting up a Dell Inspiron-11 3000 Series with Ubuntu 16.04[/COLOR][/CENTER][/SIZE]

[IMG]http://wabasha-server.net/photos/01.jpg[/IMG]

First, I picked up this used laptop with Windows 10 on it and a 500gb hard drive. The first, thing I did was to remove the hard drive and replace it with a 64gb SSD that I had picked up some time ago. At first, I thought it to be too small but I was wrong. I found a good way to set it up. The laptop has a slot for an SD card, and it just so happened that I had a 32gb card laying around. I have a bigger laptop I use for everyday work but needed a small light weight one with long battery life. I copied all my data files over to the SD and plugged it into the slot on the dell. I use it for all the data and installed Ubuntu 16.04 on the SSD. Here is what my setup looks like:

[IMG]http://wabasha-server.net/photos/02.png[/IMG]

[IMG]http://wabasha-server.net/photos/03.png[/IMG]
This is the Main Partition

[IMG]http://wabasha-server.net/photos/04.png[/IMG]
This is the Data Partition. 

As you can see I have more than enough room on the 64gb SSD and I already have many of my programs installed.

The next thing I did was to remove the 4gb of RAM and replace it with a 8gb memory module. I replace the wifi card with a (Intel 7260NGW NGFF / M.2). This will run 3 times faster than WiFi-N that is installed right now. It was only a $21 card.
If you want to know how to do all the hardware changes just watch this youtube video at: [https://ubuntuforums.org/showthread.php?t=2316240]("https://ubuntuforums.org/showthread.php?t=2316240")

This turned out to be a nice little laptop for Ubuntu to run on, but this is not to say there were some issues like hotkeys not working. Let me tell you about a problem I had and how I fixed it. When I type on any laptop my palms rub on the touchpad and my mouse jumps all around doing crazy things I don’t want to do. So I have to turn off the touchpad while I type. The problem was I couldn’t turn it off. After doing some searching on the Internet I found a way to do it. Here is what had to be done.
I had to open and edit this file:

```
 /usr/share/X11/xorg.conf.d/51-synaptics-quirks.conf.
```

At the bottom of the file I added these lines:

> # Disable generic Synaptics device, as we're using
# "DLL0704:01 06CB:76AE Touchpad"
# Having multiple touchpad devices running confuses syndaemon
Section "InputClass"
        Identifier "SynPS/2 Synaptics TouchPad"
        MatchProduct "SynPS/2 Synaptics TouchPad"
        MatchIsTouchpad "on"
        MatchOS "Linux"
        MatchDevicePath "/dev/input/event*"
        Option "Ignore" "on"
EndSection


Then I had to do a: ```
sudo systemctl restart lightdm

```

I found all this out at this link: [https://ubuntuforums.org/showthread.php?t=2316240]("https://ubuntuforums.org/showthread.php?t=2316240")

I am not a big fan of touch screens but this little laptop can be used as a tablet by flipping the screen around to the back. This is nice but the keyboard and touchpad needed to be turned off and the touch screen needed to be left on. Seeing I never used the touch screen when using as a laptop I turned it off in the startup: 

[IMG]http://wabasha-server.net/photos/05.png[/IMG]

The command I used was: ```
xinput set-prop 12 'Device Enabled' 0
```
To turn it back on just change the "0" to "1"

My touchscreen ip was 12. I found this out by typing xinput at the command prompt:
```
xinput
```
> &#9121; Virtual core pointer                    	id=2	[master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer              	id=4	[slave  pointer  (2)]
&#9116;   &#8627; Logitech USB Receiver                   	id=10	[slave  pointer  (2)]
&#9116;   &#8627; Logitech USB Receiver                   	id=11	[slave  pointer  (2)]
&#9116;   &#8627; DLL06CA:00 06CB:2985                    	id=14	[slave  pointer  (2)]
&#9116;  [COLOR="#FF0000"] &#8627; ELAN Touchscreen                        	id=12	[slave  pointer  (2)][/COLOR]
&#9123; Virtual core keyboard                   	id=3	[master keyboard (2)]
    &#8627; Virtual core XTEST keyboard             	id=5	[slave  keyboard (3)]
    &#8627; Power Button                            	id=6	[slave  keyboard (3)]
    &#8627; Video Bus                               	id=7	[slave  keyboard (3)]
    &#8627; Power Button                            	id=8	[slave  keyboard (3)]
    &#8627; Sleep Button                            	id=9	[slave  keyboard (3)]
    &#8627; Integrated_Webcam_HD                    	id=13	[slave  keyboard (3)]
    &#8627; Intel Virtual Button driver             	id=15	[slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard            	id=16	[slave  keyboard (3)]
    &#8627; DELL Wireless hotkeys                   	id=17	[slave  keyboard (3)]
    &#8627; Dell WMI hotkeys  


When all's said and done, this turned out to be one nice little laptop. The first time I used it on the battery, it lasted me all day and when I got home I still had an hour and a half left before it would have run out of power. (I didn’t even take the charger with me.) With all the hardware upgrades and running Ubuntu it is a fast little laptop and I didn’t spend an arm and a leg for it.
I picked the laptop up for $270 and with all the add ons I have a totall oof $384 tied up in this nice little laptop. And besides all this I have some extra memory and a 500 gb hard drive I can sell on ebay.

---

