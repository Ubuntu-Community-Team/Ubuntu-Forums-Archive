---
title: "Thinking about downgrading but need some advice"
date: 2013-10-26
forum: Installation &amp; Upgrades
---

### Post by bachtobach on 2013-10-26
I've got 32 bit xubuntu 13.10 installed on my Inspiron 1545 Dell laptop and I'm experiencing some annoying bugs. I know that they are bugs and it's not just me not understanding how to do something or how it works (computer always suspending when closing the lid no matter what is set in the power options, volume icon broken). 

I think it might be best if I went to 64 bit 12.04 as this is certified with my particular laptop and I know these bugs I'm experiencing didn't exist in 13.0* (4?). The only thing is that I'm not sure how to go about doing this. I would prefer not to wipe the whole drive and start again so I was thinking maybe creating a partition, installing it and then deleting/wiping the old OS when I have transferred all my data/program settings over, if this is even possible. The only things I want to save are my files in Home and ideally the torrents I am seeding in Deluge (don't want to have to add them all again if possible. 

So does this sound like a good way to do it and is it even recommended to do this? I don't know what the differences are between 12 and 13 versions but I would prefer to have a rock solid OS rather than the slightly buggy one I have right now.

---

### Post by Dennis N on 2013-10-26
> **bachtobach said:**
> 
I think it might be best if I went to 64 bit 12.04 as this is certified with my particular laptop and I know these bugs I'm experiencing didn't exist in 13.0* (4?). The only thing is that I'm not sure how to go about doing this. I would prefer not to wipe the whole drive and start again so I was thinking maybe creating a partition, installing it and then deleting/wiping the old OS when I have transferred all my data/program settings over, if this is even possible. The only things I want to save are my files in Home and ideally the torrents I am seeding in Deluge (don't want to have to add them all again if possible. 

So does this sound like a good way to do it and is it even recommended to do this? I don't know what the differences are between 12 and 13 versions but I would prefer to have a rock solid OS rather than the slightly buggy one I have right now.

I think it is an excellent solution. 

You can dual boot with the older (but still supported version) installed on a new partition. I suggest using the same user name and password as the first installation. After the installation, you can easily access the other OS files with the Thunar file manager - in fact, the other OS partition will show up in the Places section and on the desktop as a device icon. Double click to mount and open it and browse to the old home folder. You can copy files over to the new partition without any problem, or the reverse direction.

I do this (install to a separate partition) when I try a new release. In case I don't like it, my previous version is still in place. Your new install will be an older version, but that doesn't matter.

As to versions, I have been using mostly 12.04 and 12.10 on various machines, but have used 13.04 and it is fine too. 12.10 came with the newer xfce 4.10 desktop. For 12.04 there is a PPA to upgrade.  Also 13.04 and 12.10(?) have the newer Thunar. Again, there is a PPA to get that too if necessary.

---

### Post by Toz on 2013-10-26
I find 13.10 to be pretty solid (apart from the bugs). Would finding a workaround to the bugs make any difference?

> computer always suspending when closing the lid no matter what is set in the power options
In 13.10, the logind component of systemd seems to be having more of an effect on the system. Xfce is not currently patched to play well with logind/systemd. To workaround this particular issue:
1. Open /etc/systemd/logind.conf for editing:
```
sudo -i mousepad /etc/systemd/logind.conf
```
...enter your password when prompted

2. Change the line that reads:
> #HandleLidSwitch=suspend
...to read:
```
HandleLidSwitch=ignore
```
3. Save the file.
4. Setup the settings in Xfce Power Manager as you would like them.
5. Reboot.

>  volume icon broken
1. Open the /usr/share/dbus-1/services/indicator-sound.service file for editing:
```
sudo -i mousepad /usr/share/dbus-1/services/indicator-sound.service
```
...enter your password when prompted.

2. Change the line that reads:
> Exec=/usr/lib/x86_64-linux-gnu/indicator-sound/indicator-sound-service
...to read:
```
Exec=/bin/sh -c 'if [ -n "$(ps -U $USER | grep xfce4-panel)" ]; then /usr/lib/indicator-sound-gtk2/indicator-sound-service;else /usr/lib/$(arch)-linux-gnu/indicator-sound/indicator-sound-service;fi'
```

3. Save the file.
4. Log out and back in again.

---

### Post by bachtobach on 2013-10-26
Toz, I just did both of those steps (by copying and pasting rather than typing), rebooted and now I just get a black screen with a blinking horizontal cursor at the top left. Before this I get the xubuntu logo. I can´t type anything in this black screen so it´s not command line.

---

### Post by Toz on 2013-10-26
That's really odd. Neither of those commands should have affected the boot process. Did you install something else at the same time (maybe run some updates)?

If you haven't already, try rebooting one more time. Otherwise, [here]("https://wiki.ubuntu.com/RecoveryMode") is a link to doing a recovery boot. Boot in and undo the changes that you made to those two files and see if that returns the system.

---

### Post by bachtobach on 2013-10-26
I did install lxde so I think perhaps that is causing an issue. I tried to uninstall it by going control alt F1 but it hasn´t helped. 
I just followed the steps in the link and mounted but what do I do then? I rebooted but it does the same, it gives a long list of stuff which all seem to have OK next to them but then the cursor screen comes back.

---

### Post by Toz on 2013-10-26
What video card do you have? Sounds like the video isn't properly initializing.

You might want to temporarily boot with the nomodeset parameter to see if you get video. Follow the "Temporarily Add a Kernel Boot Parameter for Testing" instructions for [here]("https://wiki.ubuntu.com/Kernel/KernelBootParameters") and add **nomodeset** right after the word splash so it looks like this:
```
......ro quiet splash nomodeset
```

See if that gets the video back.

---

### Post by bachtobach on 2013-10-26
Ok, tried the nomodset trick but still does the same thing. I did notice that on the list that comes up before this blank screen it the last entry says LXDE Display so I wonder if this is what is stalling it. I had a similar problem when I tried to install another DE, I think KDE, but with a slightly different blank screen - that time I had a mouse pointer. I managed to solve it by doing something in the command line which took me to the log in screen (not the command line log in). I can´t remember what it was though and I can´t find the link, I think it involved killall or something. 

I think my video card is ATI Radeon HD 4300

---

### Post by Toz on 2013-10-26
When the system displays the flashing cursor, can you Ctrl+Alt+F1 to get to a text console? If so, try logging into the text console and if possible, uninstall lxde or reset lightdm via:
```
sudo dpkg-reconfigure lightdm
```

---

### Post by bachtobach on 2013-10-27
That one didn't work either so I just installed 12.04 and started again. Everything seems to be good so far after upgrading Thunar through the PPA. One thing I have noticed is that the fan in the laptop isn't going at full speed like it was in 13.10. 

Thanks for the help, it's very much appreciated.

---

