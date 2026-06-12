---
title: "HUGE font after Install: how to fix this?"
date: 2008-07-26
forum: Installation &amp; Upgrades
---

### Post by within on 2008-07-26
Hello ubuntu fellows,


During and after install of Xubuntu using Wibi windows installer, I get font size really HUGE [SIZE="7"] (3 times like this)[/SIZE] everywhere (login/desktop/...) makig the GUI completely not usable.

---update ---
in fact the all windows of the GUI are HUGE, seems it is more related to a screen size trouble.

It is insatlled on my gf's laptop: a Toshiba Satellite pro (pentium M).
I don't know the reason why and what to do to fix this.

Of course, I've searched the board first before posting but I didn't find any suitable answer to help.

Thanks for your help,
within

---

### Post by pytheas22 on 2008-07-26
I did some quick searching and it sounds like this may be some issue related to wubi and the way it install Xubuntu, although I'm not sure.  Could you try booting to a live CD just to see if the problem still occurs there--that way we'd know whether it's an issue with your hardware or not.

You might also try installing a different desktop environment to see if it works alright.  You could install Gnome with:
```

sudo apt-get install ubuntu-desktop
```

(provided you have enough free space on your hard disk).  Do things work alright in Gnome?

---

### Post by within on 2008-07-26
Hi Pytheas22,

thanks for taking care of this issue.

With Ubuntu (Gnome) there is no problem.

RyanVanDiemen reported this 5 days ago the same trouble:
[http://ubuntuforums.org/showthread.php?t=864865&highlight=huge+font](http://ubuntuforums.org/showthread.php?t=864865&highlight=huge+font)

According to what he said, it seems not to depend on the way it is installed. Problems occurs with XFCE and - for him - with KDE too. He does not mention this problem with Gnome.

Personaly, I didn't have troubles with Gnome/Ubuntu. BUT, I highly recommended XFCE/Xubuntu to a friend because his puter is quite old now (Intel PIII  600 MHz + 320 Mb of Ram + 20 Gb of HD). Because he never tied linux, I don't want him to start with problems, that's why I also try to find a way solving this without reinstalling Gnome or anything else that could lead to more problems for him.

I'm convinced it's Hardware issue, but i'm sure this can be fixed in editing X.org conf file, even if I don't know how to do it and what to do after editing...

so, if you don't mind, I will not try to reinstall Ubuntu. I will get CD of Xubuntu and start with it in LiveCD mode. We'll see.

Cheers,
within

---

### Post by within on 2008-07-26
I've managed (it took me some time) to read under root (console mode, not GUI) the content of xorg.conf

the screen part is like this:
Section "Screen"
        Identifier      "Default Screen"
        Device          "xxxxxxxx"
        Monitor         "Generic Monitor"
EndSection

but I believe it should be like that :
Section "Screen"
        Identifier      "Default Screen"
        Device          "xxxxxx"
        Monitor         "Generic Monitor"
 [COLOR="Green"]       Defaultdepth    24
        SubSection "Display"
                Modes           "1280x800"[/COLOR]
        EndSubSection
EndSection


xxxxxx means I can't remember what was written :(

Anyway, if I was able to read under root with command: 

vi /etc/X11/xog.conf

I was not able to add lines and then modify the conf file. Maybe it is not the solution,  but I'd like to find out.

if anyone cnan help...

Cheers,
within

---

### Post by within on 2008-07-27
---update ---
in fact the all windows of the GUI are HUGE, seems it is more related to a screen size trouble.


I've tried to use the GUI in order to go to pref and try to fix this, but now ay. Impossible because all desktop is HUGE. In fact Font size is adapted to the window size, means my monitor screen is like 25% of the complete desktop size.

I'm still looking for some advices to fix this. Also tried XFCE site without success.

Your help is really welcome,
within

---

### Post by pytheas22 on 2008-07-27
Sorry for a somewhat delayed response.

First, if you press control-alt-f2, is the text normal on that screen?

Second, do you know what kind of video card is in this machine?  This command may provide a clue:
```

cat /etc/X11/xorg.conf | grep -i -e driver -e device
```

or it may return nothing.

Does changing screen resolution make any difference?  If you can't use the GUI to do it, add into xorg.conf:
```

Section "Screen"
Identifier "Default Screen"
Device "xxxxxx"
Monitor "Generic Monitor"
Defaultdepth 24
SubSection "Display"
Modes "1280x800"
EndSubSection
EndSection
```

and change the Modes line to different resolutions (1024x768, 800x600...).  It's not a problem for that information to be missing from xorg.conf--the X11 used by Hardy attempts to auto-detect such settings on-the-fly--but if you explicitly specify them, it will use the settings you give it (as long as it doesn't think that they'll damage your hardware).  Remember that you need to restart X (control-alt-backspace is the quick and dirty way) for updates to xorg.conf to take effect.

Also, are you able to move the mouse off the screen?  Can you scroll around--in other words, if you move your mouse to the right side of your screen, does the viewing area change?

Finally, this command might help:
```

sudo dpkg-reconfigure -phigh xserver-xorg
```

It will reconfigure X, which probably won't solve anything, but it's worth a shot.

If we think that things would work normally in Gnome, then this must be a configuration issue, not hardware, so hopefully we'll get pointed in the right direction and solve the problem soon.

---

### Post by within on 2008-07-28
Thanks pytheas22,
I'll try to answer you step by step to make it as clea as possible.

> **pytheas22 said:**
> 
First, if you press control-alt-f2, is the text normal on that screen?

YES, text size is normal size in non GUI mode.

> **pytheas22 said:**
> 
Second, do you know what kind of video card is in this machine?  This command may provide a clue:
```

cat /etc/X11/xorg.conf | grep -i -e driver -e device
```

VideoCard belongs  Intel 910GML Express Chipset Family.

This is what is returned for video:
```
Device "Configured Video Device"
```
and no driver info returned.

> **pytheas22 said:**
> 
Does changing screen resolution make any difference?  If you can't use the GUI to do it, add into xorg.conf:
```

Section "Screen"
Identifier "Default Screen"
Device "xxxxxx"
Monitor "Generic Monitor"
Defaultdepth 24
SubSection "Display"
Modes "1280x800"
EndSubSection
EndSection
```

I did changed xorg.conf (using vim) in adding just this in screen section:
```
SubSection "Display"
Modes "1280x800"
EndSubSection
```

> **pytheas22 said:**
> 
Also, are you able to move the mouse off the screen?  Can you scroll around--in other words, if you move your mouse to the right side of your screen, does the viewing area change?

NO, I can't move the mouse off the screen, and NO the viewing area does not change.

> **pytheas22 said:**
> 
Finally, this command might help:
```

sudo dpkg-reconfigure -phigh xserver-xorg
```

It will reconfigure X, which probably won't solve anything, but it's worth a shot.

I did this before, without any changes.

> **pytheas22 said:**
> 
If we think that things would work normally in Gnome, then this must be a configuration issue, not hardware, so hopefully we'll get pointed in the right direction and solve the problem soon.
Maybe Hardware problem indeed, due to non complete detection of video device and driver, so some unproper configuration.

I'm still looking for a solution, but I will try to boot with Ubuntu this afternoon...

Thanx,
within

---

### Post by within on 2008-07-28
Ubuntu ins LiveCD mode: NO problem at all, everything is fine.

So, this issue seems to be related to Xubuntu, thus Xfce + my hardware... :(

---

### Post by pytheas22 on 2008-07-28
> Ubuntu ins LiveCD mode: NO problem at all, everything is fine.

Just to confirm: that is, no problem in Gnome, right (you didn't try a live CD running xfce)?
> 
VideoCard belongs Intel 910GML Express Chipset Family

Intel video has two kinds of drivers for X.  One is called "i810" and is older; the other is called "intel."  By default you should be using "intel."  Try switching to i810 by following these steps:

First, make sure the i810 driver is installed (I think it is by default, but I'm not positive):
```

sudo apt-get install xserver-xorg-video-i810
```

Then change xorg.conf to force it to use i810.  Under the "Device" section add the line 'Driver	"i810"' so that the whole section looks like:
```

Section "Device"
        Driver  	"i810"
	Identifier	"Configured Video Device"
EndSection
```

Then restart X and see if it makes a difference.  If that doesn't help, try changing the driver to intel (just in case it's using i810 by default, which shouldn't be the case) by adding the line 'driver "intel"' to the device section.

Please let me know how it goes.

---

### Post by within on 2008-07-28
Thanks very much for you kind help.

I have no LiveCD of Xubuntu. I guess I will download and burn it to be sure.

The laptop is not connected (wifi is used normally), so apt-get won't work. I'll try my best to use ethernet connection...

I'll let you know, maybe tomorrow, coz' my gf is using her laptop now, and I haven't told her the Xubuntu tests on her computer iyet :)

---

### Post by within on 2008-07-28
pytheas22,

[SIZE="5"]THANK YOU[/SIZE]

yes, thanks, because you find the solution and solved my problem!

I first did that:
```

sudo apt-get install xserver-xorg-video-i810
```
and answer was I had the latest version

Then I changed xorg.conf to force it to use i810 like you wrote:
```

Section "Device"
        Driver  	"i810"
	Identifier	"Configured Video Device"
EndSection
```

After reboot, it works.

I am posting now from Xubuntu :)

I will try to go further now, such as mount NTFS drives of the laptop.

Thanx,
within

---

### Post by pytheas22 on 2008-07-28
> The laptop is not connected (wifi is used normally), so apt-get won't work. I'll try my best to use ethernet connection...

As I said, I think that in 8.04, both the i810 and intel drivers are installed by default, but X uses intel and ignores i810 (in Gutsy only intel was installed by default, I think).  So you may not need to download anything.  You can try just adding the "driver i810" line to xorg.conf; if i810 is not installed, X will just fail to start and you can use vi to change the value back to intel.

Also, if there's an open or WEP network in range, it's easy enough to connect from the command line with a command like:
```

sudo iwconfig wlan0 mode managed channel [network channel] key [WEP key] essid [network name, in quotes]
sudo dhclient wlan0
```

Connecting by hand with WPA is quite a bit trickier; it's probably not worth the effort.  For details, see this [thread]("http://ubuntuforums.org/showthread.php?t=571188").

Anyway, when you get a chance to try the i810 thing, let me know if it helps.

---

