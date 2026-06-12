---
title: "Nvidia video corruption... please tell me it's not Intrepid!"
date: 2008-10-07
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by enigma_0Z on 2008-10-07
I recently updated to Intrepid Ibex Beta... Looked nice, nvidia-glx-173 (or whatever's newest) installed well, manually installing the driver didn't, but I figured "oh well" because this way it's integrated with DKMS and all the nifty intrepid stuff anyway...

The symptom is this: The screen freezes mostly, the system becomes unresponsive, and the rest of the screen (in a checkerboard pattern) flashes with dots, strange colors, and different portions of what's normally elsewhere on the screen.

Well, as I was running the upgraded system, during the screensaver (which I admit is graphically intense), I got some video corruption and the system froze. Basically, some squares on the screen weren't updating and were filled with staticky dots while others were still moving. I figured it was a fluke and rebooted.

The next day, same thing happened, only it looked even worse. Rebooted and everything was fine (again).

This morning, I booted up the system and now I'm getting video corruption, in GDM, even before compiz starts. The screen kind of flashes boxes and colors near the top, or random characters if I'm in the console (ctrl-alt-f1, etc), and then GDM restarts because X received signal 11. Checking the Xorg logs, there's a backtrace in the log indicating a crash, but it is not very useful, only states what modules were loaded/unloaded when it crashed. Checked dmesg and syslog too, and there's nothing of value in there other than something that mentions nvidia (or NVRM) and an "xid", but I'm not sure what it means either. I'm not even sure if the crashes generated these.

So, I just rebooted it again, and it appeared fine. Logged in and began using the system. About 15 minutes in, the screen freaks out entirely, same symptom as described above, but with additional full-screen magenta color flashes, on both the built-in LCD and the external LCD connected. So I reboot again, and I get corruption in both the BIOS loading screen and in GRUB, like the corruption on the ctrl-alt-f1 screen. It appears that my laptop (at least the graphics card) is hosed. My question, is this related to the upgrade to 8.10 (Intrepid Ibex), or is this actually [this]("http://direct2dell.com/one2one/archive/2008/08/18/nvidia-gpu-update-dell-to-offer-warranty-enhancement-to-all-affected-customers-worldwide.aspx").

Thanks!

-edit-

Update! I called Dell Support, and they're sending me a box. Yay! /sarcasm. Anyways, after the laptop sat idle for several hours, it booted up fine now, so I'm thinking it has to do with the temp. of the graphics card...

---

### Post by Supersaiyan.IV on 2008-10-10
Try starting Compiz through the fusion-icon.

> sudo apt-get install fusion-icon

Solved my corruptions.

---

### Post by enigma_0Z on 2008-10-13
> **Supersaiyan.IV said:**
> Try starting Compiz through the fusion-icon.



Solved my corruptions.

Not that kind of an issue. I have video corruption in the BIOS screen and in Windows as well... But it happened just after I installed intrepid.

---

### Post by Sef on 2008-10-13
> Not that kind of an issue. I have video corruption in the BIOS screen and in Windows as well... But it happened just after I installed intrepid.

Sounds like a hardware issue.  Just coincidence with installing Intrepid.

---

### Post by txHarleyMan on 2008-10-13
> **Sef said:**
> Sounds like a hardware issue.  Just coincidence with installing Intrepid.
I don't buy that.  When I installed Intrepid Beta over Debian Lenny, I get verticle bars ( red, white, Aqua ) intermittently when I restart.  It does not prevent it booting into Intrepid, but this issue only started when I installed Intrepid.  

Nvidia 8600GT video card here.

---

### Post by enigma_0Z on 2008-10-13
NV card here too... AFAIK the NV cards have some self-destruct issues on certain systems (espeically laptops). What kind of computer do you have?

I'd also try and boot a livecd or (gasp) windows and see if you have the same issues... If the problem persists past Linux, then it's definitely hardware... of course that doesn't mean that Linux didn't cause the hardware issue, which is my dilemma.

---

### Post by dabl on 2008-10-13
Yeah, I get a "screen show" sometimes before the Nvidia driver is loaded and KDM starts, or sometimes if I Ctrl-Alt-F1 from X, there's a little half-screen of video gibberish before the tty console comes up.

Also, my 9600GT is not correctly detected by the Kubuntu Live CD.  I have to choose F4 "Safe Graphics" mode to get it booted.  Then, on the first reboot after installing, I have to boot "Recovery Console" and choose "Fix X", which sets up a nice VESA display that actually looks pretty good -- I can set it to 1600x1200 and work with it.

But, the 177.80 downloaded Nvidia driver installs just fine, and except for the occasional blip as described above, is running well, handling Compiz just fine, and looking fine on my Samsung SyncMaster CRT.  :)

---

### Post by enigma_0Z on 2008-10-13
> **dabl said:**
> Yeah, I get a "screen show" sometimes before the Nvidia driver is loaded and KDM starts, or sometimes if I Ctrl-Alt-F1 from X, there's a little half-screen of video gibberish before the tty console comes up.

Also, my 9600GT is not correctly detected by the Kubuntu Live CD.  I have to choose F4 "Safe Graphics" mode to get it booted.  Then, on the first reboot after installing, I have to boot "Recovery Console" and choose "Fix X", which sets up a nice VESA display that actually looks pretty good -- I can set it to 1600x1200 and work with it.

But, the 177.80 downloaded Nvidia driver installs just fine, and except for the occasional blip as described above, is running well, handling Compiz just fine, and looking fine on my Samsung SyncMaster CRT.  :)

The "blip" you're describing... does it look like a memory dump from your video card? That happens with me too, it's like the display is running and it shows the old memory contents before the screen gets refreshed.

I'm talking about something else... the whole screen became corrupted and was totally unusable.

---

### Post by Supersaiyan.IV on 2008-10-13
I suppose it's a GFX card overheating problem. The new A12 (some laptops have A13) uploads a new BIOS to the graphics card to solve power/fan management. The corruption could simply be an overheating issue.

Since the video issues are there upon BIOS load I suppose your card has been permanently damaged.

Also, we still don't know which laptop model/gfx card we're talking about.

---

### Post by enigma_0Z on 2008-10-13
> **Supersaiyan.IV said:**
> I suppose it's a GFX card overheating problem. The new A12 (some laptops have A13) uploads a new BIOS to the graphics card to solve power/fan management. The corruption could simply be an overheating issue.

Since the video issues are there upon BIOS load I suppose your card has been permanently damaged.

Also, we still don't know which laptop model/gfx card we're talking about.

According to what I've heard with the bios update, if it's affected already, no, an update won't fix it. 

My card is the 8400GS in a Dell Vostro 1400, so i think my bios #'s are a bit different. However, even if you install the BIOS update, the cards are still made with sub-par materials, and the BIOS update comes at the expense of battery life because it runs the fan more.

I'm trying to determine if my card actually melted, or if I screwed something up.

---

### Post by plun on 2008-10-13
Please read this message from Dell

[http://direct2dell.com/one2one/archive/2008/09/12/nvidia-gpu-update-limited-warranty-enhancement-details.aspx](http://direct2dell.com/one2one/archive/2008/09/12/nvidia-gpu-update-limited-warranty-enhancement-details.aspx)

It might also be more models now, just to do what Dell proposes.

It can also be warranty cases and this is a expensive fiasco for nVidia.

---

### Post by nystire on 2008-10-13
If you have shared memory for your video card, check your RAM. It could be that you have a blow chip in the main memory, and not in the video RAM.

---

### Post by plun on 2008-10-13
Please read this message from Dell

[http://direct2dell.com/one2one/archive/2008/09/12/nvidia-gpu-update-limited-warranty-enhancement-details.aspx](http://direct2dell.com/one2one/archive/2008/09/12/nvidia-gpu-update-limited-warranty-enhancement-details.aspx)

It might also be more models now, just to do what Dell proposes.

It can also be warranty cases and this is a expensive fiasco for nVidia.

---

### Post by plun on 2008-10-13
Massive database error

---

### Post by enigma_0Z on 2008-10-13
> **plun said:**
> Please read this message from Dell

[http://direct2dell.com/one2one/archive/2008/09/12/nvidia-gpu-update-limited-warranty-enhancement-details.aspx](http://direct2dell.com/one2one/archive/2008/09/12/nvidia-gpu-update-limited-warranty-enhancement-details.aspx)

It might also be more models now, just to do what Dell proposes.

It can also be warranty cases and this is a expensive fiasco for nVidia.

Seen that too. I think that *that* is what's going on... but  I guess my question is is there any to tell whether the chip fried or it was intrepid?

---

### Post by sokopok on 2008-10-13
Well I've been working with the VESA driver for 2 days now, because, hey I've got the same problem. Updated saturday, got the new DKMS, rebooted and here we are.
When I use nv driver I just get a black screen when X starts, when I use nvidia driver I get funky black and white stripes with some multicolor pixels sprinkeled on top.
Windows gives me a black screen.
Called Dell support today, they want me to remove Linux and reinstall from the original CD, didn't want to help me with BIOS upgrade for the videocard. I couldn't find the info about the exact chipset so opened up my laptop today to figure that out, to no avail (anonymous :/).
Definitely  DKMS that screwed up my videocard.
I'm using a Dell Vostro 1400, with NVidia 8400M GS.

---

### Post by enigma_0Z on 2008-10-13
> **sokopok said:**
> Well I've been working with the VESA driver for 2 days now, because, hey I've got the same problem. Updated saturday, got the new DKMS, rebooted and here we are.
When I use nv driver I just get a black screen when X starts, when I use nvidia driver I get funky black and white stripes with some multicolor pixels sprinkeled on top.
Windows gives me a black screen.
Called Dell support today, they want me to remove Linux and reinstall from the original CD, didn't want to help me with BIOS upgrade for the videocard. I couldn't find the info about the exact chipset so opened up my laptop today to figure that out, to no avail (anonymous :/).
Definitely  DKMS that screwed up my videocard.
I'm using a Dell Vostro 1400, with NVidia 8400M GS.

Sounds like you're chip's been fried... I had some similar issues with an older nVidia 7200. Dell allowed me to simply remove the HDD, and I sent the laptop to them to test it. You may want to avoid mentioning that Linux is on the lappy... If you do, the script readers, erm, support techs will (in most cases) automatically skip to the last resort steps which are reboot, reinstall, repair (eg. send it in).

Does the VESA driver work for you? In my experience, the video became unusable even before Linux booted fully, even in the BIOS and GRUB screens.

---

### Post by sokopok on 2008-10-13
VESA works perfectly + I ran all the Dell diagnostics without a single error.
I've been very open with this Dell guy, that's me. I told him I run linux, I told him my card got fried immediately after installing the new DKMS driver, I told him I installed Vista x64, ...
He didn't say anything about the article plun mentioned ([http://direct2dell.com/one2one/archive/2008/09/12/nvidia-gpu-update-limited-warranty-enhancement-details.aspx](http://direct2dell.com/one2one/archive/2008/09/12/nvidia-gpu-update-limited-warranty-enhancement-details.aspx)).
Before I hung up the phone (whe he insisted I reinstall the original OS, whicjh I can't btw cause I don't have the CD anymore) I asked him about the warranty, he said it would still be valid for any hardware issues. But now I opened up the laptop myself, so I'm afraid that's going to void it. If I'd only heard about this before.... (bit too impulsive sometimes :( )

---

### Post by Supersaiyan.IV on 2008-10-13
The only time the GFX card gave me weird multicolor pixels was when the usplash (ubuntu logo during boot) was wrongly resized to an unknown vga code.
This resulted in loud system beeps & messed up graphics (and a minor heart attack). Hard reset was the only cure.
The thing is that on wide-screens usplash(and grub?) needs to load the vesa module, and if its wrongly configured it _will_ go nuts.

Fixed it by doing:
```
sudo gedit /etc/usplash.conf
```
In there add my desired resolution:
```
xres=1280
yres=800
```
Then reload everything:
```
sudo update-initramfs -u
```

---

### Post by sokopok on 2008-10-13
Since Intrepid I've got the same beeping/heart attack syndrome every once in a while. But frankly that's the least of my worries right now ;/
I'll grill the guys at Dell tomorrow and see where that gets us. Why the smeg are the too lame to warn/inform me of the fact my system is slowly cooking itself like this. Checked temperature with sensors earlier. Idle system temp. dropped by 35C since my NVidia quit.

---

### Post by Gleber on 2008-10-29
sokopok, were you able to fix you issue with blank screen and line of multicolor pixels on the top of the screen? 

I'm struggling with it right now. I've had to revert to 'nv' driver, which works like a charm.

Interesting fact is the only resolution which does not work for me is 1280x1024, other (like 800x600, 1164x864(?), 1280x960) works without any problem. Maybe your video card isn't fried yet? Have you tried CTRL+ALT+'+' and CTRL+ALT+'-' on numpad? It switches me to other resolutions, which works...

I've tried adding different ModeLines, I've tried different versions (177 and 173), I've tried reinstalling xserver, libgl1-*, nvidia-*, xdm and nothing helps.

---

### Post by dabl on 2008-10-29
I inadvertently proved last night, beyond all doubt, that the "funny video" that I sometimes see is a quick flash of cached video display, either from main memory or from the graphic card's memory.

I was running my sidux system which has a very distinctive reddish-patterned wallpaper, doing updates and various things, and when I finished, I did a shutdown/restart and booted Kubuntu Intrepid Ibex.  Immediately after I logged in to Kubuntu/KDE, instead of the blue swirly default wallpaper, up popped a somewhat-fragmented display of the brick-red sidux patterned wallpaper, for only a fraction of a second, and then came the blue Kubuntu desktop.

So, there's two cents' worth.  :)

---

### Post by saffagirl on 2008-10-30
I've had the vostro 1400 with the same card, wasn't running ubuntu then, but had my motherboard fried by the gpu...clearly an issue. Had multiple issues eventually got replacement 1310 with the same graphics card!(after a lot of incompetent techies going it's not in my job log, i ain't doing antything.) now running dual boot w. vista and hardy. Not so sure about intrepid yet, tried beta and didn't like the way it handled wl and nvidia drivers.

So bottom line, I'm like you, scared that my machine is a ticking time bomb and am not so happy. Definitely being downplayed, I had random looking freeze ups and funky screens, then would just completely cut out...so watch out. Dell, nvidia et al are being taken to court in the states and hopefully something more will be done about it. the bios makes your fan work a lot...still fairly warm though.

So what I'm saying is get onto dell pronto=sounds like graphics card.

---

### Post by sokopok on 2008-10-30
I ran all the diagnostics I could get my hands on, which all said: Everything OK! But still no video. Not with the 'nv' or 'nvidia' driver anyway. 

I'm still using the "vesa" driver, which started working properly when I got the monitor refresh rates set up in xorg.conf.
[INDENT]Option          "UseEDIDFreqs"  "false"
        HorizSync       28.0 - 51.0
        VertRefresh     43.0 - 61.0
[/INDENT] Apparently the new, fancy Xorg isn't yet very good at figuring out all the options automatically, so you need to give it some hints and hope it accepts them (see [http://ubuntuforums.org/showthread.php?p=5951159#post5951159](http://ubuntuforums.org/showthread.php?p=5951159#post5951159) ).

I stopped wasting my time with this, since I had other urgent business to take care of, but anyway... [Gleber]("http://ubuntuforums.org/member.php?u=540408"), Could you post you xorg.conf settings, I'd like to give them a try.

---

