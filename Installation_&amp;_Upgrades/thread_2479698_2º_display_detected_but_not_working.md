---
title: "2º display detected but not working"
date: 2022-10-03
forum: Installation &amp; Upgrades
---

### Post by indiobrsp on 2022-10-03
[FONT=Arial]Hello, I recently migrated from windows and started using Linux/Ubuntu.

[/FONT]
[FONT=Arial]Everything was going fine until I connected my notebook to a monitor/display.[/FONT]
[FONT=Arial]Here is the config I am running:

[/FONT]
[FONT=Arial]Hardware model: SAMSUNG ELECTRONICS CO., LTD. 550XDA
Memory: 8 GB
Processor: 11th Gen Intel® Core™ i7-1165G7 @ 2.80GHz × 8
Graphics: Mesa Intel® Xe Graphics (TGL GT2)
OS: Ubuntu 22.04.1 LTS
OS Type: 64-bit
GNOME Version: 42.4
Windowing System: Wayland

[/FONT]
[FONT=Arial]As you can see the display was detected by the system:

[IMG]https://itsfoss.community/uploads/default/optimized/2X/e/ed4d6f9bc09d866d1f4f0f28c4c604a6d4d0941d_2_406x500.png[/IMG]

[/FONT]
[FONT=Arial]Despite this my second screen is all black. I already tried it on another computer and it works just fine. The problem is something with this config. Maybe the graphics card? Mesa Intel® Xe Graphics (TGL GT2).

[/FONT]
[FONT=Arial]Can someone please help? I really need this setup working for my studies.

[/FONT]
[FONT=Arial]Thank you very much.[/FONT]

---

### Post by MAFoElffen on 2022-10-03
The easiest way is to switch the Graphics Engine from Wayland to Xorg. Wayland is a bit finicky about dual displays.

To see if this works for you, at the Graphical Login screen (GDM), after selecting the user, at the next panel, before entering in your password, select the gear icon in the lower right corner, and select "Ubuntu Xorg"...

---

### Post by indiobrsp on 2022-10-03
> **MAFoElffen said:**
> The easiest way is to switch the Graphics Engine from Wayland to Xorg. Wayland is a bit finicky about dual displays.

To see if this works for you, at the Graphical Login screen (GDM), after selecting the user, at the next panel, before entering in your password, select the gear icon in the lower right corner, and select "Ubuntu Xorg"...

Thanks for the reply, I changed it to Xorg (X11) but it didn't work. Is there anything else I can do?

---

### Post by MAFoElffen on 2022-10-03
Open a terminal session, with everything connected and run the [UbuntuForums 'system-info']("https://github.com/UbuntuForums/system-info") script... The first time running it answer no to everything... Run it a second time like this...
```

./system-info -d

```
That will run that script in a expanded, detail mode... When asked if you want to upload it, answer <Y><Enter> for yes. After it uploads, copy down the URL to add that link to a post.

It has a section in it for detailed Graphics Information on your hardware and settings, as Linux see's it... That will give us a better idea of what is going on.

---

### Post by indiobrsp on 2022-10-03
I ran the script as you requested.

Here is the link for the report.  [URL="http://termbin.com/ezlqs"]

http://termbin.com/ezlqs[/URL]

Thank you very much for the support.

This is the link for the second script run with the -d

[https://termbin.com/0jxy](https://termbin.com/0jxy)

---

### Post by indiobrsp on 2022-10-03
[COLOR=#000000]This is the link for the second script run with the -d[/COLOR]

[https://termbin.com/0jxy](https://termbin.com/0jxy)

---

### Post by MAFoElffen on 2022-10-03
```

   --- Graphics Environment Continued from 'various graphics ENVs' ----
The Current Configured Destop is: ubuntu:GNOME 
The Current Desktop Session is: ubuntu-xorg 
The Current X Desktop Information Details from 'xrandr' are: 
Screen 0: minimum 320 x 200, current 1920 x 1080, maximum 16384 x 16384
[COLOR=#ff0000]eDP-1 **connected** 1920x1080+0+0 (normal left inverted right x axis y axis) 344mm x 194mm[/COLOR]
DP-1 disconnected (normal left inverted right x axis y axis)
HDMI-1 disconnected (normal left inverted right x axis y axis)
[COLOR=#ff0000]HDMI-2 **connected** primary 1920x1080+0+0 (normal left inverted right x axis y axis) 597mm x 336mm[/COLOR]
The Current Session Type is: x11 
The Current Display Manager is: gdm3
The Current Desktop Theme: 'Yaru'

```
I can see that the GPU see's the Display and is answering it as the resolution it is set to... That doesn't make sense that it is displaying as blank, and not showing any output.

Let me think about this one...

---

### Post by indiobrsp on 2022-10-03
I understand. OK Thank you for your help. It must be some kind of hardware problem that I was not able to troubleshoot.

---

### Post by MAFoElffen on 2022-10-04
Yes it seems like there might be something physicall wrong there. But, I can help you to diagnose that also...

No. You say you had connected another computer to that display, and the display works, right?  Using the same HDMI cable?

I don't see where you had said what make and model of display(?) Could you please ID the display? 

Have you tried that Sony Notebook to another display or TV through that port?

-- Because logically, Linux and software diagnostics reports it is working. It says it "is connected" at 1920x1080. That is why this does not make sense at the moment. Unless maybe it was a back-light problem on the display, or something like that... (cable)

For checking that, you would shine a flashlight at a sharp angle across the display and see if if shows anything faintly on the display screen...

Or try a different cable...

---

### Post by #&amp;thj^% on 2022-10-04
Just a stab in the dark but info script states sucure-boot  is enabled on OP's machine
worth a shot to disable it in bios and try again just to be sure.
Like MAFoElffen, it should work, providing cables and connectors are all in good form.

---

### Post by pacufillet on 2022-10-09
I share the same 11th gen Intel CPU and Xe Graphics family as OP. Disabling enforcement of secure boot fixed it for me. 

In my case, second display was not recognized in Settings/Display at all, and second display did not work. Now it works.

---

### Post by indiobrsp on 2023-07-18
You where right! the problema was indeed the cable! thanks!!

---

