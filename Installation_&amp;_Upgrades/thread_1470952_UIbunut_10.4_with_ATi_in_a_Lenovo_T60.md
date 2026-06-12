---
title: "UIbunut 10.4 with ATi in a Lenovo T60"
date: 2010-05-03
forum: Installation &amp; Upgrades
---

### Post by johnswb on 2010-05-03
Hello,  I've looked for this problem all over the forum and google.  I have yet to find a solution or anyone else with this problem.  

I was running 9.10 and my dual monitors worked find.  After upgrading (fresh install) my second monitor now flickers.  I can see what is on the screen but after some time have to look away due to the flickering.  I've changed the "Refresh rate" and still no luck.  Looks like I'll have to stay on 9.10...

please help

---

### Post by antiram on 2010-05-03
boot your 9.10, open a terminal with active second monitor and excute:
xrandr

it shows the current mode setting for the second monitor with a "*" behind. Is this mode setting available with xrandr on 10.4 install? Then use it with eg.
xrandr --output DVI-0 --mode 800x600 --auto

Or is the old mode not available? Error messages?

---

### Post by atlithorn on 2010-05-03
Same problem here

External monitor "shivers" and complains about bad input "Try 1600x1200 60Hz" which is exactly what System->Preferences->Monitor shows.

Have to turn off the external screen to be able to use the laptop at all. If it's on then after a  couple of minutes both screens start blinking and I have to reboot.

Saw something about a fix here: [http://git.kernel.org/?p=linux/kernel/git/airlied/drm-2.6.git;a=commitdiff;h=267364ac17f6474c69b03034340f769b22f46105](http://git.kernel.org/?p=linux/kernel/git/airlied/drm-2.6.git;a=commitdiff;h=267364ac17f6474c69b03034340f769b22f46105) so I tried using "pre-released updates" (lucid-proposed) to see if the update was there and made any difference. No luck. 

Feel like an utter idiot for upgrading, everything was perfect on 9.10.

```
$lspci | grep VGA
01:00.0 VGA compatible controller: ATI Technologies Inc Radeon Mobility X1400

$ xrandr
Screen 0: minimum 320 x 200, current 3000 x 1200, maximum 8192 x 8192
VGA-0 connected 1600x1200+1400+0 (normal left inverted right x axis y axis) 408mm x 306mm
   1600x1200      60.0*+
   1280x1024      75.0     60.0  
   1280x960       60.0  
   1152x864       75.0  
   1024x768       75.1     70.1     60.0  
   832x624        74.6  
   800x600        72.2     75.0     60.3     56.2  
   640x480        72.8     75.0     66.7     60.0  
   720x400        70.1  
LVDS connected 1400x1050+0+0 (normal left inverted right x axis y axis) 286mm x 214mm
   1400x1050      60.0*+   50.0  
   1280x1024      59.9     60.0  
   1280x960       59.9  
   1280x854       59.9  
   1280x800       59.8  
   1280x720       59.9  
   1152x768       59.8  
   1024x768       60.0     59.9  
   800x600        60.3     59.9  
   848x480        59.7  
   720x480        59.7  
   640x480        60.0     59.4  
DVI-0 disconnected (normal left inverted right x axis y axis)
```Let's go guys!

---

### Post by antiram on 2010-05-03
seems a kms bug. you could use the old user mode setting with "nomodeset" or "radeon.modeset=0" as kernel parameter. powermanagment works also with ums. or use mainline-ppa kernel 2.6.34-rc6 (which has the fix) 
[http://kernel.ubuntu.com/~kernel-ppa/mainline/](http://kernel.ubuntu.com/~kernel-ppa/mainline/)

---

### Post by atlithorn on 2010-05-03
Thanks antiram, that did the trick.

In case you don't understand his suggestion:

You need to edit your kernel parameters. 

```
$sudo nano /boot/grub/menu.lst
```

Find the default boot option (most likely the top option)
edit the kernel line to read:


```
kernel        /boot/vmlinuz-2.6.32-22-generic root=UUID=b7d1fda9-dc35-4e0e-b0fb-e287929151c6 ro  radeon.modeset=0 quiet splash 
```

Notice radeon.modeset=0, that's the trick.

Reboot and enjoy,
Thanks again antiram.

---

### Post by Haitao on 2010-06-15
For those using the default Grub2 present in Ubuntu since 2 releases ago (IIRC) the file to edit is /etc/default/grub and you need to add the kernel parameter to the GRUB_CMDLINE_LINUX_DEFAULT="quiet splash".

Then just sudo update-grub and restart for the changes to take effect.

---

### Post by immux on 2010-08-17
> **atlithorn said:**
> Thanks antiram, that did the trick.

In case you don't understand his suggestion:

You need to edit your kernel parameters. 

```
$sudo nano /boot/grub/menu.lst
```

Find the default boot option (most likely the top option)
edit the kernel line to read:


```
kernel        /boot/vmlinuz-2.6.32-22-generic root=UUID=b7d1fda9-dc35-4e0e-b0fb-e287929151c6 ro  radeon.modeset=0 quiet splash 
```

Notice radeon.modeset=0, that's the trick.

Reboot and enjoy,
Thanks again antiram.

is it possible for Intel Mobile 945GM ??

---

### Post by drorlev on 2010-09-12
Thank you antiram, atlithorn and Haitao!

Your posts helped me with a flickering dual-monitor on an LG E300 laptop with an ATI Radeon Xpress 1250 graphic card running Ubuntu 10.4 Lucid Lynx.

Thanks again,
dror

---

### Post by ecowan on 2010-09-20
Yes!!
To clarify for non-hackers, 
GRUB_CMDLINE_LINUX_DEFAULT="radeon.modeset=0 quiet splash"

---

### Post by Charbax on 2010-10-11
solved

---

### Post by legendbb on 2010-10-18
the

GRUB_CMDLINE_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX="radeon.modeset=0"

approach stabilized the screen, but my external VGA goes only up to 1440 x 900 which has a native of 1920x1080

What's the solution to get native res?

Thanks:confused:

---

### Post by awhyte on 2010-11-06
That also fixed my Chrome browser tabs!

Before applying this fix, the Chrome tabs would take a couple seconds to tear off when dragged out of a window, and the "preview" body of the tab wouldn't render correctly while dragging, and docking was pretty janky too.

Now tearoff and docking behavior is fast and smooth.  Thanks.

---

### Post by ryan6 on 2010-11-20
Thank you!


> **Haitao said:**
> For those using the default Grub2 present in Ubuntu since 2 releases ago (IIRC) the file to edit is /etc/default/grub and you need to add the kernel parameter to the GRUB_CMDLINE_LINUX_DEFAULT="quiet splash".

Then just sudo update-grub and restart for the changes to take effect.

> 
Yes!!
To clarify for non-hackers,
GRUB_CMDLINE_LINUX_DEFAULT="radeon.modeset=0 quiet splash"


Thank You! Im using Dell Inspiron E1505. Just to clarify for others super-noobs using the default Grub 2

> sudo gedit /etc/default/grub
then edit the line for GRUB_CMDLINE_LINUX_DEFAULT to read..
> GRUB_CMDLINE_LINUX_DEFAULT="radeon.modeset=0 quiet splash"
save the file and then
> sudo update-grub
then restart

Voila (second monitor should be working)

---

