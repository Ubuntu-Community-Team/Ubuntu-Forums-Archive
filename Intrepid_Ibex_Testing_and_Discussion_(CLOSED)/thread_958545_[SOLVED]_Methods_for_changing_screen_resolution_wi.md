---
title: "[SOLVED] Methods for changing screen resolution without GUI?"
date: 2008-10-25
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by scandido on 2008-10-25
I've upgraded my computer to 8.10 and, stupidly, chosen a resolution in the screen resolution settings which my monitor does not support. The computer does not seem to understand this and keeps trying to use this resolution after I pass through the login screen. In short, I cannot see anything to change the setting back through the GUI.

In the past, I would have hit CTRL+ALT+F5, logged in at the prompt, edited my xorg.conf file to put back the appropriate resolution, restarted X and the problem would have been fixed. However, when I try this now, all the settings are "Configured Video Device", "Configured Monitor", etc. I've done some reading ([https://help.ubuntu.com/community/XORGHardy](https://help.ubuntu.com/community/XORGHardy)) and it seems that a lot of these settings are being configured internally. 

I've tried moving xorg.conf and regenerating it but there are no changes. What steps do I need to take in order to drop back to a resolution I can use, without use of the GUI? 

Thanks for your help!

---

### Post by swisscow on 2008-10-25
Not sure if you need the dektop up and running but a cli code that works (I sometimes use it in the terminal) is xrandr - can't remember the exact command but if you type in xrandr 'i think it brings up the help and it's fairly straightforward to use.

---

### Post by scandido on 2008-10-25
When I tried xrandr, it gives me the message

Can't open display

Any ideas? Thanks for your help.

---

### Post by blakamin on 2008-10-25
Tried "sudo dpkg-reconfigure -phigh xserver-xorg" ?

---

### Post by wgrant on 2008-10-25
GNOME gets the resolution settings from ~/.config/monitors.xml. If you remove that, it should revert to the default.

---

### Post by scandido on 2008-10-25
Yes, I tried and it generated essentially the same xorg.conf that I had before. Unfortunately, there weren't many settings as all the entries were something like "Configured Monitor", "Configured Video Device", etc.

I was able to edit the xorg.conf file manually to use the vesa driver and a resolution of 800x600. However, once I was in I couldn't modify the resolution settings for when I was not using the vesa driver. 

In short, the method you proposed used to be how to "reset" your display settings when you made a mistake (at least so far as I know). However, it seems like it no longer works this way.

Thanks.

---

### Post by scandido on 2008-10-25
What was proposed by wgrant was the solution. Thank you very much.

---

### Post by mdurham on 2008-10-25
> **wgrant said:**
> GNOME gets the resolution settings from ~/.config/monitors.xml. If you remove that, it should revert to the default.

I don't have a  "~/.config/monitors.xml" file, why would that be?
Cheers, Mike

---

### Post by wgrant on 2008-10-25
> **mdurham said:**
> I don't have a  "~/.config/monitors.xml" file, why would that be?
Cheers, Mike

It probably won't be there if you haven't changed settings in System->Preferences->Screen Resolution.

---

### Post by mdurham on 2008-10-25
> **wgrant said:**
> It probably won't be there if you haven't changed settings in System->Preferences->Screen Resolution.

Thanks wgrant, but where does the resolution come from then? I'm not saying that my resolution is wrong, it's perfectly ok, but when all there is in xorg.conf is "Configured Video Device", where is it configured?
Cheers, Mike

---

### Post by wgrant on 2008-10-25
> **mdurham said:**
> Thanks wgrant, but where does the resolution come from then? I'm not saying that my resolution is wrong, it's perfectly ok, but when all there is in xorg.conf is "Configured Video Device", where is it configured?
Cheers, Mike

It is detected from the monitor's EDID.

---

### Post by mdurham on 2008-10-25
> **wgrant said:**
> It is detected from the monitor's EDID.

Great, thanks a lot.
Cheers, Mike

---

### Post by gcoats23 on 2008-10-25
Hi guys im having the same problem, except I am not as good at the cli- 
so what i did was type nano ~/.config/monitors.xml
 but that just opend a new file- ill keep trying things - 
thanks  It is detected from the monitor's EDID- well its not being detected right- i cant boot at all- my screen goes blank and my monitor says "cannot display resolution"
garrett
this might help too-i set up this computer with my monitor and everything went great(installing for a friend who liked ubuntu) then he took his pc home and called me and said "all i get is a blank screen telling me my screen resolution is wrong" hope that helps-
wow im sorry this is not in the 8.04 section. my bad - sorry guys

---

### Post by scandido on 2008-10-26
The fix is actually to remove the file. Nano is a text editor so it will allow you edit the file. Obviously, there is probably a way to remove the "bad" lines but I'm not sure how to do it. 

First, try moving it to make sure it helps.

mv ~/.config/monitors.xml ~/.config/old_monitors.xml

If that works, then just get rid of the file

rm ~/.config/old_monitors.xml

Good luck.

---

### Post by mike310z on 2008-10-26
I started out with this exact problem this morning. I eventually worked out that xorg.conf is no longer used after doing the package reconfigures etc. I then found the monitors.xml which I deleted and found that it is re created if you change the settings via System->Screen Resolution.

However my Dell 1703fpt, is capable of only 1280 x1024 @ 75hz and the Screen Resolution API give me the option of 1400x1050 and 1600 x1024, both of which cause the monitor to go mental :-)

If the available resolutions are auto detected I need to report a bug, but I am not sure that there is not some setting I am supposed to have used some place.

Can anyone offer any help, is this a bug ?

---

