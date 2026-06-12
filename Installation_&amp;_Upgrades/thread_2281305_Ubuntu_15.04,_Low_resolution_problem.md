---
title: "Ubuntu 15.04, Low resolution problem"
date: 2015-06-06
forum: Installation &amp; Upgrades
---

### Post by golden_eye_ on 2015-06-06
I have just installed Ubuntu 15.04 64-bit on my machine having *intel hd graphics 4600* and the maximum resolution is 640x480. I have tried the first suggestion from [here]("http://askubuntu.com/questions/316221/resolution-hd-1920x1280-with-intel-graphics-in-ubuntu-12-04-lts") without any success and tried to use intel graphics driver installer, but it says 'Distribution not supported'.

How can I fix this issue?


[IMG]http://i57.tinypic.com/2cpvn9w.png[/IMG]

---

### Post by sudodus on 2015-06-06
Maybe it works for you according to the following link
[URL="http://ubuntuforums.org/showthread.php?t=2269309"]
Change display resolution[/URL]

---

### Post by golden_eye_ on 2015-06-06
It has worked partially. Maximum resolution is now 1204x768, while it should be 1280x1024. Beside graphics is slower 
than before now!

---

### Post by sudodus on 2015-06-07
There seems to be problems with the driver for your graphics hardware in 15.04.

Have you tried if it works better with one the point versions ***14.04.1 LTS or 14.04.2 LTS*** of the long time support version 14.04 LTS? You can start trying *live* without installing.

You can also try the very newest version, the daily build of wily werewolf, to be released in October as 15.10. You can find it via the testing tracker

[http://iso.qa.ubuntu.com/](http://iso.qa.ubuntu.com/)

and for example this link for Ubuntu Desktop amd64 in Wily Daily: [Link to the download information]("http://iso.qa.ubuntu.com/qatracker/milestones/340/builds/95166/downloads")

---

### Post by golden_eye_ on 2015-06-18
Haven't anyone faced and solved this?

---

### Post by monkeybrain20122 on 2015-06-18
What exactly is your graphic card? Does it work on 14.04? 

Alternatively you can upgrade your graphic driver [https://launchpad.net/~oibaf/+archive/ubuntu/graphics-drivers](https://launchpad.net/~oibaf/+archive/ubuntu/graphics-drivers)
install ppa-purge in case you have to revert the change (see the instructions on the link)

P.s The driver is being built right now, wait an hour or so before you upgrade.

---

### Post by golden_eye_ on 2015-06-20
When executing this command
> LIBGL_DRIVERS_PATH=/usr/lib/dri-alternates glxgears -info
I get the following error
> libGL error: unable to load driver: swrast_dri.so
libGL error: failed to load driver: swrast
X Error of failed request:  BadValue (integer parameter out of range for operation)
  Major opcode of failed request:  154 (GLX)
  Minor opcode of failed request:  3 (X_GLXCreateContext)
  Value in failed request:  0x0
  Serial number of failed request:  35
  Current serial number in output stream:  37



---

### Post by sudodus on 2015-06-20
> Haven't anyone faced and solved this?

Maybe none of us here. But please make it easier for us to help by trying what we suggest, and telling us the result. That way, step by step, we might find a working solution :-)

Have you tried if it works better with one the point versions ***14.04.1 LTS or 14.04.2 LTS*** of the long time support version 14.04 LTS? You can start trying *live* without installing.

---

### Post by golden_eye_ on 2015-06-20
I haven't tried ***14.04.1 LTS or 14.04.2 LTS  ***but used **14.04** (max resolution 640x480) and 15.04 (live, max resolution 1024x768, graphics lags a lot).

---

### Post by sudodus on 2015-06-20
So 15.04 works better than 14.04. You might try the newest point release 14.04.2 LTS (live, don't install until you know that it works). I looked for your graphics card/chip via the internet and I think it is quite new. This makes me think you should use the newest possible version of Ubuntu, which is still being developed, Wily Werewolf to be released in October as 15.10. You can find it via the testing tracker

[http://iso.qa.ubuntu.com/](http://iso.qa.ubuntu.com/)

and for example this link for Ubuntu Desktop amd64 in Wily Daily: [Link to the download information]("http://iso.qa.ubuntu.com/qatracker/milestones/340/builds/95166/downloads")

The following link gives us hope, that there should be a linux driver,

[http://www.intel.com/support/graphics/sb/cs-010512.htm](http://www.intel.com/support/graphics/sb/cs-010512.htm)

---

### Post by golden_eye_ on 2015-06-20
I hope that this driver ([https://launchpad.net/~oibaf/+archive/ubuntu/graphics-drivers](https://launchpad.net/~oibaf/+archive/ubuntu/graphics-drivers)) would work but its creating some problem (mentioned in previous post)

---

### Post by sudodus on 2015-06-20
Well, good luck and let us know your results :-)

---

### Post by blm-ubunet on 2015-06-20
Can you post your latest /var/log/Xorg.0.log file as an atttachment ?

15.04 & 14.04 (with additional hardware enablement stack) should have had out-of-the-box support for this 2 year old CPU/GPU.

---

### Post by golden_eye_ on 2015-06-23
Here is the log.
[http://pastebin.com/s4YEf2Xd](http://pastebin.com/s4YEf2Xd)

---

### Post by Ty_Scheun on 2015-06-23
[FONT=Ubuntu][COLOR=#111111]Press CTRL+ALT+T and run xrandr. Reply with the results[/COLOR][/FONT]

---

### Post by Ty_Scheun on 2015-06-23
[COLOR=#111111][FONT=Ubuntu]In /etc/X11/xorg.conf, look for these two lines :[/FONT][/COLOR][INDENT]HorizSync 28.0 - 33.0
VertRefresh 43.0 - 72.0
[/INDENT]
[COLOR=#111111][FONT=Ubuntu]and replace them with[/FONT][/COLOR][INDENT]HorizSync 30.0 - 83.0
VertRefresh 56.0 - 75.0
[/INDENT]

---

### Post by Ty_Scheun on 2015-06-23
[FONT=Helvetica Neue]You can try setting your resolution to the desired level manually.[/FONT]
[FONT=Helvetica Neue]First, run this command, changing the example 1920x1080 resolution to the resolution you want:[/FONT]
```
cvt 1920 1080
```
[FONT=Helvetica Neue]That will spew out something like this:[/FONT]

```
# 1920x1080 59.96 Hz (CVT 2.07M9) hsync: 67.16 kHz; pclk: 173.00 MHz
Modeline "1920x1080_60.00"  173.00  1920 2048 2248 2576  1080 1083 1088 1120 -hsync +vsync

```
[FONT=Helvetica Neue]We're only interested in the chunk after the quotes and before the -hsync, e.g.[/FONT]
```
173.00  1920 2048 2248 2576  1080 1083 1088 1120
```
[FONT=Helvetica Neue]Use that in the next command to add a graphics mode:[/FONT]
```
xrandr --newmode clever_name 173.00  1920 2048 2248 2576  1080 1083 1088 1120
```
[FONT=Helvetica Neue]Now, add your new mode to your VGA output:[/FONT]
```
xrandr --addmode VGA1 clever_name
```
[FONT=Helvetica Neue]Finally, switch your VGA monitor to use it:[/FONT]
```
xrandr --output VGA1 --mode clever_name
```
[FONT=Helvetica Neue]Now that that works, you can make it take effect every time you log in. To do so, create the following files somewhere:[/FONT]
[FONT=Helvetica Neue]fix-resolution.sh with what is called a shebang line and then the last three commands you ran that got it working before, e.g.:[/FONT]
```
#!/bin/sh
xrandr --newmode clever_name 173.00  1920 2048 2248 2576  1080 1083 1088 1120
xrandr --addmode VGA1 clever_name
xrandr --output VGA1 --mode clever_name
```
[FONT=Helvetica Neue]fix-resolution.desktop with the following contents:[/FONT]
```
[Desktop Entry]
Name=fix resolution
Exec=/usr/bin/local/fix-resolution.sh
```
[FONT=Helvetica Neue]Now, copy the files to the appropriate places on your hard drive and make the script executable. From a terminal:[/FONT]
```
cp fix-resolution.sh /usr/local/bin
chmod +x /usr/local/bin/fix-resolution.sh
cp fix-resolution.desktop /etc/xdg/autostart

```
[FONT=Helvetica Neue]This will run the commands that force your monitor to the proper resolution every time someone logs into your computer.

Hope you get it to work! ;)[/FONT]

---

### Post by golden_eye_ on 2015-06-23
1) I haven't found any [COLOR=#111111][FONT=Ubuntu]/etc/X11/xorg.conf in 15.04 and created one using the command provided in this post[1].[/FONT][/COLOR] There is no HorizSync and VertRefresh in this file. After creating this file, resolution has increased to 1024x768 from 640x480 and the graphics has become very slow.

2) If I try to execute the following command
> xrandr --newmode clever_name 173.00  1920 2048 2248 2576  1080 1083 1088 1120
I get this error
> xrandr: Failed to get size of gamma for output default

Here is the complete output
> 
maruf@lion:~$ 
maruf@lion:~$ cvt 1280 1024
# 1280x1024 59.89 Hz (CVT 1.31M4) hsync: 63.67 kHz; pclk: 109.00 MHz
Modeline "1280x1024_60.00"  109.00  1280 1368 1496 1712  1024 1027 1034 1063 -hsync +vsync
maruf@lion:~$ xrandr --newmode random_res 109.00  1280 1368 1496 1712  1024 1027 1034 1063
xrandr: Failed to get size of gamma for output default
maruf@lion:~$ xrandr --addmode VGA1 ransom_res
xrandr: Failed to get size of gamma for output default
xrandr: cannot find output "VGA1"
maruf@lion:~$ 




xrandr output
> 
maruf@lion:~$ xrandr
xrandr: Failed to get size of gamma for output default
Screen 0: minimum 640 x 480, current 1024 x 768, maximum 1024 x 768
default connected primary 1024x768+0+0 0mm x 0mm
   1024x768       61.0* 
   800x600        61.0  
   640x480        60.0  
  clever_name (0x18c)  109.0MHz
        h: width  1280 start 1368 end 1496 total 1712 skew    0 clock   63.7KHz
        v: height 1024 start 1027 end 1034 total 1063           clock   59.9Hz
  random_res (0x18d)  109.0MHz
        h: width  1280 start 1368 end 1496 total 1712 skew    0 clock   63.7KHz
        v: height 1024 start 1027 end 1034 total 1063           clock   59.9Hz
maruf@lion:~$ 




Resolution 1280x1024 has been appeared in display option. When I select that option, it creates an error showing max and min resolution.
You can visualize the slowness of graphics. Screenshot taking window is also visible the screenshot!

[IMG]http://i.imgur.com/C7CUn9b.png[/IMG]


[1][ http://askubuntu.com/questions/4662/where-is-the-x-org-config-file-how-do-i-configure-x-there]("http://http://askubuntu.com/questions/4662/where-is-the-x-org-config-file-how-do-i-configure-x-there")


i am really disappointed :confused:

---

### Post by Ty_Scheun on 2015-06-23
Are you using a VGA Port for your monitor? If its HDMI you are using, I could provide help for that
You can also manually set it with ```
xrandr -s [COLOR=#000000]1280x1024[/COLOR]
```

---

### Post by Ty_Scheun on 2015-06-23
[COLOR=#000000]Yet another way to change!

First open a terminal[/COLOR][COLOR=#000000][I]Applications >> Accesories >> Terminal
[/I]
[/COLOR]
[COLOR=#000000]in the terminal type :[/COLOR]
[B]1)Code:
 ```
**$ xrandr
```**
(without the $ mark)
this will display the allowed resolutions
something like this :

```
[I]Screen 0: minimum 320 x 200, current 1024 x 768, maximum 4096 x 4096
**VGA1** connected 800x600+0+0 (normal left inverted right x axis y axis) 267mm x 200mm
800x600 85.1* +
640x480 75.0 60.0 
720x400 70.1
[/I]
```

then type 
[B]2)Code:
 ```
**$ cvt 1024 768**
```
(any resolution that you want similar to this)

the output will be similar to this :
```
[I][B]# 1024x768 59.92 Hz (CVT 0.79M3) hsync: 47.82 kHz; pclk: 63.50 MHz
Modeline "1024x768_60.00" 63.50 1024 1072 1176 1328 768 771 775 798 -hsync +vsync[/B]
[/I]
```

[B]
3)Code:
```
** $ xrandr --newmode <Modeline>**
```
(copy the modeline of the previous output to the place mode line)
for example :Code:
```
**$ xrandr --newmode "1024x768_60.00"   63.50  1024 1072 1176 1328  768 771 775 798 -hsync +vsync**
```
[B]4)Code:
```
**$ xrandr --addmode VGA1 1024x768_60.00**
```
(here for [B]VGA1 you have to use what ever that was there for[B] $ xrandr output in [B]step 1)

[B]5)Code:
 ```
**$xrandr --output VGA1 --mode 1024x768_60.00 **
```
(replace VGA1 accordingly, [B]remember to use the numbers within inverted commas in step 3 , after --newmode for 1024x768_60.00 )

***Running these would change your resolution but this is temporary.these steps were done to make sure that these commands work . After step 5 you should see the resolution change.If this is successful proceed to the next step 


[B]6)
Code:
```
**$ sudo gedit /etc/gdm/Init/Default**
```
(this will ask for your root password type the password and a text editor will appear)
in this you will see a text line like this 
[I][B]PATH=/usr/bin:$PATH
OLD_IFS=$IFS
[/B]
[/I]

just below this paste the[B] step 3 to 5 commands
and then save it.

example :
[I]#!/bin/sh
# Stolen from the debian kdm setup, aren't I sneaky
# Plus a lot of fun stuff added
# -George

PATH=/usr/bin:$PATH
OLD_IFS=$IFS
[B]xrandr --newmode "1024x768" 70.00 1024 1072 1176 1328 768 771 775 798 -hsync +vsync

xrandr --addmode VGA1 1024x768_60.00

xrandr --output VGA1 --mode 1024x768[/B]

if [ -x '/usr/bin/xsplash' ];

then
/usr/bin/xsplash --gdm-session --daemon
[/I]

this worked in karmic ......I think this will be helpful to you if you want know more about [**xrandr**]("https://wiki.ubuntu.com/X/Config/Resolution")
[/B][/B][/B][/B][/B][/B][/B][/B][/B][/B][/B]

---

### Post by golden_eye_ on 2015-06-23
I always get this error when executing any command related to xrandr.

> xrandr: Failed to get size of gamma for output default

---

### Post by Ty_Scheun on 2015-06-23
open a terminal and type in this:

```
[COLOR=#000000]lspci
[/COLOR][COLOR=#000000]cat /etc/X11/[/COLOR][COLOR=#000000]xorg.conf[/COLOR]
```

reply with results

---

### Post by Ty_Scheun on 2015-06-23
You need to add a modeline for xrandr to work. add the modeline in the etc/X11/xorg.conf

[COLOR=#111111][FONT=Ubuntu]You don't need sudo to register the new mode with xrandr, try without sudo. Then you'll have to apply the new resolution with:[/FONT][/COLOR]
```
xrandr --addmode <your_connection_type> 1200x1000_60.00
```
[COLOR=#111111][FONT=Ubuntu]Where is usually VGA1, DP1 or HDMI1. Check the output of xrandr to know the exact name of the connected output.[/FONT][/COLOR]

---

### Post by Ty_Scheun on 2015-06-23
There is no full report of the output of xrandr? just that?

---

### Post by Ty_Scheun on 2015-06-23
Do you use HDMI, VGA, or DVI

---

### Post by golden_eye_ on 2015-06-23
lspci [http://pastebin.com/i1k4aDsr](http://pastebin.com/i1k4aDsr)
xorg.conf [http://pastebin.com/7n5SJARk](http://pastebin.com/7n5SJARk)

Not sure about the connection type. How can I get that info?
My monitor model: [http://www.cowboom.com/product/752259](http://www.cowboom.com/product/752259)

---

### Post by Ty_Scheun on 2015-06-23
Add a new modeline, then try xrandr

```
[FONT=courier new][COLOR=#800000]cvt (your preffered resolution)[/COLOR][/FONT]
```

---

### Post by golden_eye_ on 2015-06-23
I have done it before without any success. Please check previous posts.

---

### Post by golden_eye_ on 2015-06-28
So, no more ubuntu! :shock:

---

### Post by golden_eye_ on 2015-06-29
Last night It worked (Resolution: 1280x1024) suddenly.
After a restart Resolution is now 640x480 again!.

---

### Post by blm-ubunet on 2015-07-03
remove "nomodeset" from your grub kernel boot options cmd line & reboot.

---

### Post by NoWayWin8 on 2015-07-03
> **golden_eye_ said:**
> I have just installed Ubuntu 15.04 64-bit on my machine having *intel hd graphics 4600* and the maximum resolution is 640x480.

I also have the Intel HD 4600 graphics. Worked right out of the box on 14.04.2 with the default intel driver (i915) that Ubuntu installed automatically. What does your Xorg log show happening with the graphics devices?

---

### Post by blm-ubunet on 2015-07-03
The OP posted this in post #14 after I asked for it..
It clearly shows "nomodeset" kernel boot option is causing the intel (modesetting) driver being unloaded..

---

### Post by golden_eye_ on 2015-07-06
If I remove "nomodeset" the screen become green and the machine restarts.

---

### Post by Milla_Makia on 2015-08-28
Kind of solved this.

I just removed my other screen and resolution works fine for now, but I cant open monitors window, cause it crashes with Ubuntu 15.10. With Ubuntu 15.04 it might say Built in Display, which is BS or then it finds my displays, if i installed Ubuntu the way i tell later. If installation goes correct it works perfect every time. Build in display mode, when istallation have gone bad sometimes changes resolution, like the same way as the fellas, who started this topic.

When I installed Ubuntu 15.04 my resolution also messed up and problem is, that Ubuntu thinks that Im using "Built in Display", like this fellas Ubuntu also, who made this topic.

When i just override old version in Ubuntu 15.04 the resolution doesnt work, but when I installed it completely and destroyed old partition it worked just fine with both displays. This 15.10 doesnt work and Im gonna go back to Ubuntu 15.04. So if Ubuntu installs itself with 800x600 resolution its not gonna work, but when it installs itself with normal (high  resolution) mode its gonna work. 14.04 and other Ubuntus worked just fine. With 15+ problems started.

My first Display is ASUS (dont remember the model) 2560x1440 and second display is HD LG TV. Graphic card is some Nvidia. Don't know wheres the problem, but please solve it, that i can use Ubuntu 15.10.

Now its time to reinstall Ubuntu. Thanks and bye. ):P

----------

Update:
Okey, now i installed 15.04 and it works fine. Displays says, that My primary is Ancor communications inc. 27", its really Asus PB278WR 27" Secondary it says, that is Goldstar Company LTD 7", It's really LG 32LD450N. Graphic card is Nvidia GT218 (G210).

----------

Update 2:
Installed Geforce drivers and 15.10 seems to work just fine with both displays now. [http://www.howopensource.com/2012/10/install-nvidia-geforce-driver-in-ubuntu-12-10-12-04-using-ppa/](http://www.howopensource.com/2012/10/install-nvidia-geforce-driver-in-ubuntu-12-10-12-04-using-ppa/)

---

