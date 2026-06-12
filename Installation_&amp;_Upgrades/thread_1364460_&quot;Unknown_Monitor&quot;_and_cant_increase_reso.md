---
title: "&quot;Unknown Monitor&quot; and cant increase resolution beyoud 800x600"
date: 2009-12-25
forum: Installation &amp; Upgrades
---

### Post by AniruddhaJoshi on 2009-12-25
Team,

**Issue**: Display preferences shows "Unknown Monitor" and I can't increase resolution above 800x600.

**System and Hardware details**: 
Ubuntu : v9.10
Motherboard : Asus P5KPL-AM/PS
Display Driver: Intel Corporation 82G33/G31 Express Integrated Graphics Controller [8086:29c2] (rev 10)

**Details**: the resolution i am using is too small. i want to increase the resolution. when i am pressing the "Detect Monitors" it shows "unknown Monitor" also the resolution is restricted to 800x600.

I am a first time user of Linux. Thanks to Ubuntu team for wonderful OS. Please let know what i have to do. i Googled a lot on "intel G33  driver for linux", "Unknown Monitor" on Ubuntu/Google webiste but believe could not find the right solution.

i think Ubuntu v9.10 already provides the Intel G33 display driver because i was downloading/installing something and it said "Error: the later version is already installed".

If i need to download/install something request to provide step/by/step procedure. Because yet i am not able to understand from where/how to install make/compile code. where to place the downloaded files etc.

Thanks / Regards,
AJ

---

### Post by taurus on 2009-12-25
What kind of monitor do you have, CRT or LCD?  What's the size and resolution of it?

---

### Post by AniruddhaJoshi on 2009-12-25
**Monitor Details**:
Manufacturer: DAEWOO 431X
Type : CRT
i can set normally 1280x1024 resolution. i think its 14".

---

### Post by taurus on 2009-12-25
Is this your monitor?

[http://www3.dealtime.com/xPF-Daewoo-431X-14-in](http://www3.dealtime.com/xPF-Daewoo-431X-14-in)

You have the wrong resolution there since according to the link, the max is 1024 x 768.

---

### Post by AniruddhaJoshi on 2009-12-26
Yes Taurus, this is the one i am using. sorry for the incorrect resolution earlier.

Please refer attached screencap of 'Display Preferences' it shows a maximum of 800x600.

---

### Post by sharaq on 2009-12-26
First open a terminal > Applications >> Accesories >> Terminalin the terminal type :
  ** 1) **  ```
 **$ xrandr**
```  (without the $ mark)
this will display the allowed resolutions
something like this :

> Screen 0: minimum 320 x 200, current 1024 x 768, maximum 4096 x 4096
**VGA1** connected 800x600+0+0 (normal left inverted right x axis y axis) 267mm x 200mm
   800x600        85.1* +
   640x480        75.0     60.0  
   720x400        70.1  
then type 
** 2)**   ```
 **$ cvt 1024 768**
```  (any resolution that you want similar to this)

the output will be similar to this :
> [B]# 1024x768 59.92 Hz (CVT 0.79M3) hsync: 47.82 kHz; pclk: 63.50 MHz
Modeline "1024x768_60.00"   63.50  1024 1072 1176 1328  768 771 775 798 -hsync +vsync[/B]
[B]
3)[/B]```
** $ xrandr --newmode <Modeline>**
```  (copy the modeline of the previous output to the place mode line)
for example :```
**$ xrandr --newmode "1024x768_60.00"   63.50  1024 1072 1176 1328  768 771 775 798 -hsync +vsync**
```**4)  **```
**$ xrandr --addmode VGA1 1024x768_60.00**
```  (here for **VGA1** you have to use what ever that was there for** $ xrandr** output in **step 1**)

**5)** ```
 **$xrandr --output VGA1 --mode 1024x768_60.00 **
``` (replace VGA1 accordingly, **remember to use the numbers within inverted commas in step 3 , after --newmode for 1024x768_60.00**  )

***Running these would change your resolution but this is temporary.these steps were done to make sure that these commands work . After step 5 you should see the resolution change.If this is successful proceed to the next step  

**6)**
```
**$ sudo gedit /etc/gdm/Init/Default**
```(this will ask for your root password type the password and a text editor will appear)
in this you will see a text line like this 
> [B]PATH=/usr/bin:$PATH
OLD_IFS=$IFS
[/B]just below this paste the** step 3 to 5** commands
and then save it.

example :
> 
#!/bin/sh
# Stolen from the debian kdm setup, aren't I sneaky
# Plus a lot of fun stuff added
#  -George

PATH=/usr/bin:$PATH
OLD_IFS=$IFS
[B]xrandr --newmode "1024x768"   70.00  1024 1072 1176 1328  768 771 775 798 -hsync +vsync

xrandr --addmode VGA1 1024x768_60.00

xrandr --output VGA1 --mode 1024x768[/B]

if [ -x '/usr/bin/xsplash' ];

then
        /usr/bin/xsplash --gdm-session --daemon
this worked in karmic ......I think this will be helpful to you if you want know more about [**xrandr**]("https://wiki.ubuntu.com/X/Config/Resolution")

> If **step 6** isn't working then read this post by [COLOR="Red"]**mpatrick**[/COLOR]
[http://ubuntuforums.org/showthread.php?t=1364460&page=5]("http://ubuntuforums.org/showthread.php?t=1364460&page=5")
Thank you mpatrick..

---

### Post by AniruddhaJoshi on 2009-12-26
It worked!!!

Thanks a lot sharaq. only thing i changed in step 4 
xrandr --addmode VGA1 1024x768


to 
xrandr --addmode VGA1 1024x768[COLOR=Red]_60.00[/COLOR]

Thanks again sharaq and taurus. the monitor still shows "unknown" but i am happy with 1024x768 resolution :-)

---

### Post by sharaq on 2009-12-26
if you want you can change the refresh rate to a much higher value if you want, may be **70.00**or something... it is better for you eyes.... to do that just change the values **[COLOR="Red"]60.00[/COLOR]**

---

### Post by sarum on 2009-12-27
Hello, I have the same 800x600 problem. I followed your advice to stage 3 and got this reply:-
X Error of failed request:  BadName (named color or font does not exist)
  Major opcode of failed request:  149 (RANDR)
  Minor opcode of failed request:  16 (RRCreateMode)
  Serial number of failed request:  21
  Current serial number in output stream:  21
If you can help in any way I'd be very grateful
Thankyou.......sarum

---

### Post by sharaq on 2009-12-27
what is the operating system you are using? is it ubuntu 5.10??
I've used this in 9.10..

if you miss out any part of the output it gives this error message(which you have copied from the step 2)recheck it. I think you have missed the last part of it ,most likely, the part in bold letters. 
>  $ xrandr --newmode "1024x768_60.00" 63.50 1024 1072 1176 1328 768 771 775 798 -hsync **+vsync**

hope this will help you....

---

### Post by woohhaa on 2009-12-27
Thanks sharaq, that also helped me get off the darn 800x600 resolution in 9.10.

---

### Post by Jenarobfreaky on 2009-12-27
I need help.  I am a newbie to ubuntu.  I tried to use your xrandr --addmode VGA1 1024x768_60.00, however came up with error message, xrandr: cannot find output "VGA1" Please help
 
Thanks

---

### Post by imari2542 on 2009-12-27
This is just what I was looking to do.  The resolution was fine before I did upgrades from 8.04-> 8,10-> 9.04 but but then for some reason not correct in 9.10.

Thanks so much!

---

### Post by sharaq on 2009-12-27
> **Jenarobfreaky said:**
> I need help.  I am a newbie to ubuntu.  I tried to use your xrandr --addmode VGA1 1024x768_60.00, however came up with error message, xrandr: cannot find output "VGA1" Please help
 
Thanks

hmm..... read **step1** carefully, whatever is there for VGA1 in your output, use that not VGA1 ....

cheers!!!!happy new year everybody !!!!

---

### Post by Malik_2009 on 2009-12-30
[COLOR=black][FONT=Verdana][SIZE=3]I followed the same steps exactly, but I could not change the resolution. Although I made this process many times, since I thought I made mistake, the results were the same, no change the resolution.[/SIZE][/FONT][/COLOR]
[COLOR=black][FONT=Verdana][SIZE=3]When I run this step: $xrandr --newmode "1024x768_60.00" 63.50 1024 1072 1176 1328 768 771 775 798 -hsync +vsync[/SIZE][/FONT][/COLOR]
[COLOR=black][FONT=Verdana][SIZE=3]I got this message:[/SIZE][/FONT][/COLOR]
[COLOR=black][FONT=Verdana][SIZE=3]X Error of failed request: BadName(named color or font does not exist)[/SIZE][/FONT][/COLOR]
[COLOR=black][FONT=Verdana][SIZE=3]   Major opcode of failed request: 149(RANDR)[/SIZE][/FONT][/COLOR]
[COLOR=black][FONT=Verdana][SIZE=3]   Minor opcode of failed request : 16 (RRCreateMode)[/SIZE][/FONT][/COLOR]
[COLOR=black][FONT=Verdana][SIZE=3]   Serial number of failed request: 18[/SIZE][/FONT][/COLOR]
[COLOR=black][FONT=Verdana][SIZE=3]   Current serial number in output stream: 18[/SIZE][/FONT][/COLOR]
[COLOR=black][FONT=Verdana][SIZE=3]I run ubuntu9.10 using sun vb, and the OS is windows7[/SIZE][/FONT][/COLOR]
[COLOR=black][FONT=Verdana][SIZE=3]Sony laptop CW series, and the graphics card is nVIDIA, Geforce G210M, processor T9600 2.8Ghz[/SIZE][/FONT][/COLOR]
[COLOR=black][FONT=Verdana][SIZE=3] [/SIZE][/FONT][/COLOR]
[COLOR=black][FONT=Verdana][SIZE=3]I tried this way many times, but I have the same problem each time. Furthermore, use this command for xorg.conf which is sudo /etc/X11/xorg.conf and I do not find any file for xorg.[/SIZE][/FONT][/COLOR]
[COLOR=black][FONT=Verdana][SIZE=3]Other thing, when I use system>Administration> Hardware Drivers[/SIZE][/FONT][/COLOR]
[COLOR=black][FONT=Verdana][SIZE=3]ubuntu tries to find Drivers, but I got an empty window[/SIZE][/FONT][/COLOR]
[COLOR=black][FONT=Verdana][SIZE=3] [/SIZE][/FONT][/COLOR]
[COLOR=black][FONT=Verdana][SIZE=3]Please help me to solve this problem because I am very new with linux and I like it and I would to be good user of Ubuntu.[/SIZE][/FONT][/COLOR]
[COLOR=black][FONT=Verdana][SIZE=3]Thank you for help[/SIZE][/FONT][/COLOR]
[FONT=Calibri][SIZE=3] [/SIZE][/FONT]

---

### Post by sharaq on 2009-12-30
So, you are using Ubuntu in Virtualbox right,
just try installing guest additions for it, (but, I'm not sure whether that will work or not..)
see whether you have given necessary resources to the Ubuntu OS from VB........

but if you really want to try using Ubuntu try installing within windows option(WUBI).Then follow these steps.

if not just dual boot it with windows.

about **xorg.conf**.... in 9.10 xorg.conf is not there.... but if you want you can make a xorg.conf file and make the necessary adjustments.but writing xorg.conf that'll be difficult...if you can copy the xorg from 9.04 and paste it there,that'll work.

---

### Post by naushu on 2010-01-01
Hi Sharaq,
I had same problem with my UBUNTU9.10.Your tips worked fine for me. 
But whenever I reboot my PC , all settings are losing. If I follow the steps once again, my display resolution will become 1024x768 again. How to keep this settings permanently?

Thanks in advance,
Naushad

---

### Post by sharaq on 2010-01-01
Just like i've said in **step 5**
use,

```
**sudo gedit /etc/gdm/Init/Default**
```

In that file paste those commands as i have shown you, Oh!!! and **remember to save the file !!!**.... then it'll be permanent. 
just paste in the place as I've shown.

---

### Post by r.v.the.evil on 2010-01-01
hello plz solve my lcd reolution it also shows unknown monitor
bt resolition is 1280x800
yet it does not seems to be

---

### Post by sharaq on 2010-01-01
this is for jaunty uses(9.04)
to [COLOR="Red"]r.v.the.evil[/COLOR]

first type 

**```
sudo gedit /etc/X11/xorg.conf
```**

in that under monitor 

> Section "Monitor"
    
    VendorName **"........."**
    ModelName **".........."**
    Modeline        "**MODELINE output from  the cvt command of step 2 ** 

if there is no mode line add one.

Do those changes and you don't have to change the **/etc/gdm/init/default** thing, if you have just **undo it**,,, also before doing this if you are confused just read my 1st reply to this thread.

---

### Post by r.v.the.evil on 2010-01-01
bt i m also using 9.10
i forgot to update status here

---

### Post by r.v.the.evil on 2010-01-01
u can see my screen snapshots here at given link 
the resolution is set to 1280x800
[http://ubuntuforums.org/showthread.php?t=1368817](http://ubuntuforums.org/showthread.php?t=1368817)

---

### Post by mmarton on 2010-01-02
Sharaq:
Did everything that you prescribed and I got the resolution to change.  Excellent. I also pasted the three commands into  the file after opening up a new window with $ sudo gedit /etc/gdm/Init/Default and saved the file.  But my settings were gone when I rebooted.  Any other ideas?

---

### Post by owenisred on 2010-01-02
After trying so many different ways to overcome the resolution problem myself - I got it working a different way: Ill stick it in here to help anyone who is having trouble with sharap's fix

1. open terminal (Applications > Accessories)
2. Type >  gksudo gedit /etc/apt/sources.list 			 		 hit enter and type your password (if you are prompted) and enter again.
3. Scroll to the bottom of the text that appears and paste
> 
deb [http://ppa.launchpad.net/siretart/ppa/ubuntu](http://ppa.launchpad.net/siretart/ppa/ubuntu) jaunty main
deb-src [http://ppa.launchpad.net/siretart/ppa/ubuntu](http://ppa.launchpad.net/siretart/ppa/ubuntu) jaunty main
5. open a new terminal
6. type 
> sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com 0xce90d8983e731f79

7. Wait fr the thing to download
8. New terminal type

> sudo apt-get update

9. Again add password if necessary
10 type 
> sudo apt-get install xserver-xorg-video-intel-2.4

thatl be you

type > sudo /etc/init.d/gdm restart to reset ubuntu.

When i did it my monitor went crazy and I had to switch off at plug, but then on opening ubuntu again resolution was fine :)

Hope I helped 

Owen.

---

### Post by zonefull on 2010-01-04
thx sharaq it realy worked but once i reboot everythin gets back as it never happened 
i followed your saving steps tho >.<
could u help me pass this :D

---

### Post by far_pro on 2010-01-07
my system has the same problem ...when i reboot dislay gets back to 800x600...help!

---

### Post by sohaila on 2010-01-07
Hi,

I've been using Ubuntu for 1 week, having installed 9.10 on an old Toshiba laptop. I have the same screen resolution problem. When I follow the steps in the earlier thread I can create the new mode and add it to the output (default in my case), but when I try to set it I get the following message from xrandr:


[LIST]
[*]screen cannot be larger than 800x600 (desired size 1024x768 )
[/LIST]

Any help would be appreciated.

---

### Post by sharaq on 2010-01-10
You can use a script to run at startup if this is not working go to the following link and read **posts 13 and 14**

[http://ubuntuforums.org/showthread.php?t=1370258&page=2]("http://ubuntuforums.org/showthread.php?t=1370258&page=2")

---

### Post by swapnasarit on 2010-01-10
hi,
I am also facing the same problem.
I followed the thread 

if I run these command in shell my resolution getting changed 

but when I reboot the machine it set itself to 800x600
I have pasted the code in /etc/gdm/Init/Default 

how to fix it permanently ?

code :
xrandr --newmode "1280x800_60"   83.50  1280 1352 1480 1680  800 803 809 831 -hsync +vsync
xrandr --addmode VGA1 1280x800_60
xrandr --output VGA1 --mode 1280x800_60

---

### Post by User0123 on 2010-01-12
> **sohaila said:**
> Hi,

I've been using Ubuntu for 1 week, having installed 9.10 on an old Toshiba laptop. I have the same screen resolution problem. When I follow the steps in the earlier thread I can create the new mode and add it to the output (default in my case), but when I try to set it I get the following message from xrandr:


[LIST]
[*]screen cannot be larger than 800x600 (desired size 1024x768 )
[/LIST]

Any help would be appreciated.

I have the same issue when trying to force my monitor into higher resolutions, (its a HDTV, I'm trying to get it into 1920x1080) It still doesn't want to go higher than 800x600 though.

---

### Post by Lorin Ricker on 2010-01-12
By coincidence!... This very problem happened to my daughter's PC yesterday afternoon when she did the upgrade from 9.04/JJ to 9.10/KK -- Doesn't appear that she "did anything wrong" during the upgrade; Karmic just failed to recognize her monitor, even though Jaunty (and Hardy before that) handled it just fine.  Who broke that code?

Anyway, the above recipe fixed things up fine.  Many thanks to the community for recognizing the problem quickly and providing a very clear and usable fix!  Thank you, Sharaq!

-- Lorin

---

### Post by Lorin Ricker on 2010-01-12
Hmm, mmarton.  We rebooted my daughter's PC immediately after editing the /etc/gdm/Init/Default file, and the fix _is_ persistent for us.  I just rebooted it again after reading your problem, and the fix indeed stays in place after a second reboot.  There's nothing that I know of that would somehow "sneakily revert" your edits to the file...  More likely, they're not being saved correctly in the first place.

However, you say that you're using "sudo gedit <file>" rather than "**gk**sudo gedit <file>".  Various Ubuntu "tips and tricks" books that I've read have emphasized using gksudo for any application which is a graphical user interface (like gedit), rather than just sudo (which is for com-line commands only).

Do a "$ sudo cat /etc/gdm/Init/Default" both before and after you edit the file (using **gksudo**) to confirm the contents/state at each point.  Once you edit the file correctly, the fix (lines) _should_ persist!

-- Lorin

---

### Post by Lorin Ricker on 2010-01-12
Note that when you use the unadorned "$ xrandr" command to show/report your monitor's current configuration, it might actually say something other than "VGA1" (although that's probably what most folks see).  Don't just blindly use "VGA1" in your subsequent xrandr commands... use whatever display name your original command gives you!  -- L

---

### Post by CodeRage on 2010-01-12
> **Lorin Ricker said:**
> Note that when you use the unadorned "$ xrandr" command to show/report your monitor's current configuration, it might actually say something other than "VGA1" (although that's probably what most folks see).  Don't just blindly use "VGA1" in your subsequent xrandr commands... use whatever display name your original command gives you!  -- L

A good example of it not being "VGA1" or such in my case, it showed up as > default connected 1024x768+0+0 0mm x 0mm so I used > default in place of "VGA1". 

I hope this helps others with the elusive VGA1. 

FYI: My machine is a Dell Inspiron 1501.


Thanks and you're welcome.

CR

---

### Post by Darkseren on 2010-01-13
Yay Thank you so much! this is an awesome fix for an annoying problem!

---

### Post by Tourdog on 2010-01-13
Tried this method but it doesn't work.  Could it be the Karmic 64 bit issue or is it the "gdm" problem?   Or something else?   

I have read of the "script" method but this seems more elegant.........

Any thoughts?   :(

TIA!

---

### Post by sharaq on 2010-01-15
It can't be a 64 bit issue, I'm running in 64 bit. May be the gdm issue. 
anyways the script works, right ???. Yeah ! true that's not a good fix for the problem. the screen does crazy thing on start up 

Try that gdm fix.

How did you install your Nvidia drivers. Using **envyng** or ....another method?

---

### Post by Tourdog on 2010-01-17
Sharag,
I used "system- preferences- Hardware Drivers.   I tried "Owenisred"  method too but am stopped with:

W:  GPG error: [http://packages.medibuntu.org](http://packages.medibuntu.org) karmic Release:  The following signatures couldn't be verified because the public key is not available:   NO PUBKEY ..........................................

 I have about 4 issues yet to solve on my 64 bit Karmic 9.10 and all seem to hinge on security code in the distro.

I have seen and have been stopped by that GPG error many times before!  Huge frustration.   :(    The "script" method also stops me with......   "Access Denied"!  I have all the passwords too.

Anybody know of an easy way (anyway) to solve the GPG error ie NO PUBKEY?

---

### Post by sharaq on 2010-01-18
ok try installing your Nvidia drivers using envyng.
**1)**
open a terminal 

**```
$ sudo apt-get install envyng 
```**

then after that 
**2)**
**```
$ sudo envyng -t
```**

and uninstall Nvidia drivers. then reboot the computer and then again run the command in **step 2**
and now install Nvidia drivers.

**3)**
after that go to 

> system >> Administration >> Nvidia X server settings
then  go to **x server display configuration** and change to the resolution you want, and click **save to X configuration** then click **show preview** and copy the content to /etc/X11/xorg.conf  (**remember to back up the current xorg.conf file first)**

To do that use 

**```
$ gksudo gedit /etc/X11/xorg.conf
```**

delete the content and replace it with the copied one from Nvidia X server settings and **save the file**

---

### Post by perspectoff on 2010-01-18
The original post was about an Intel graphics card.

I had the same problems in Jaunty and Karmic. I had to rollback the Intel graphics to 2.4 (the version used in Intrepid) following the instructions found here:

[https://wiki.ubuntu.com/ReinhardTartler/X/RevertingIntelDriverTo2.4](https://wiki.ubuntu.com/ReinhardTartler/X/RevertingIntelDriverTo2.4)

I have not had recent problems with ATI or NVidia drivers (although I did with NVidia way back in Intrepid).

---

### Post by mpatrick on 2010-01-27
[FONT=Arial][SIZE=2]First of all thanks to Sharaq for your excellent post and help.

I followed his instructions and the resolution changed and worked fine

However as with many other posts I could not keep this permanent by editing the /etc/gdm/Init/Default file as he suggested

As wizel post in thread [http://ubuntuforums.org/showthread.php?t=1370258&page=2](http://ubuntuforums.org/showthread.php?t=1370258&page=2) I confirmed that the gdm file was not being used at startup hence reason why pasting xrandr commands into this file did not change resolution upon restarting!!

So I then created script file /usr/local/bin/increase_resolution.sh as detailed in wizels other post in thread above

However when I created this file    	you can [/SIZE][/FONT][FONT=Arial][SIZE=2]see resolution changing once starts up. More annoyingly using this I [/SIZE][/FONT][FONT=Arial][SIZE=2]had to remove my clock and CPU monitor applets on the desktop as showing in middle of screen.
Even more annoyingly [/SIZE][/FONT][FONT=Arial][SIZE=2]I noticed that when starting up from cold cairo dock was in middle of screen and changed colour on lots of menu's looks to  grey. [/SIZE][/FONT]

---

### Post by mpatrick on 2010-01-27
*Oops sorry I have to carry on from my original post as seems to be limit on amount of text (new to this posting)*

Only way to overcome this was to log back in again then all worked ok but not a very good fix for me!!


So the reason I am posting is the way I found to overcome this is as follows from thread [https://wiki.ubuntu.com/X/Config/Resolution](https://wiki.ubuntu.com/X/Config/Resolution)


Copy and paste the relevent xrandr command line strings you need for your resolution (determined from sharaqs earlier post in this forum) into file below so they're executed when you log in


```
sudo gedit ~/.xprofile
```Make file executable and hey presto


An example of my .xprofile file is below with the 3 xrar commands


```


xrandr --newmode "1440x900_60.00"  106.50  1440 1528 1672 1904  900 903 909 934 -hsync +vsync

xrandr --addmode VGA1 1440x900_60.00

xrandr --output VGA1 --mode 1440x900_60.00


```
After doing this my resolution shows itself changing during startup screen and everything on my desktop now works correctly, ie all panels lining up, cairo dock in right place, clock and system monitor applets all ok on desktop. So problem solved for me.


Only thing to remember with this fix is that will need to do for each user on pc.


I hope that above makes sense and that is might help someone else


Thanks

---

### Post by ccroy on 2010-02-07
Hi, I'm Chris and I'm new to Ubuntu. I just installed 8.10 on my system. I have the "Unknown Monitor 800x600" problem it seems many people are having.

I have an SiS 65x/M750/740 PCI/AGP VGA Display adapter on the motherboard of my PC. I am using my HDTV as a monitor. In Windows XP I can select 1024x768 and it all look good.

When I use the xrandr commands in terminal following Sharaq's post I have this problem:

> chris@chris-desktop:~$ xrandr --output default --mode 1024x768_60.00
xrandr: Configure crtc 0 failed
Does anyone know what "Configure crtc 0 failed" means?

The screen tries to resize for a split second and remains at 800x600.

If I go to: System\Preferences\Screen Resoultion my monitor is still "Unknown" but I have a 1024x768 option, but nothing happens when I apply it?

Thanks

---

### Post by lunk on 2010-02-10
Hello, I only got to the third step:  xrandr --newmode &quot;1368x768_60.00&quot;   85.25  1368 1440 1576 1784  768 771 781 798 -hsync +vsync

where it writes:
Error of failed request:
  BadName (named color or font does not exist)
   Major opcode of failed request:  152 (RANDR)
   Minor opcode of failed request:  16 ()
   Serial number of failed request:  13
   Current serial number in output stream:  13
  I have the Intel GMA X4500 card, might this be the problem? I have heard the card acts up.
 I have kubuntu 8.10  Thanks

---

### Post by Jarvus on 2010-02-11
Why do we have to go to hell and back to get our monitors supported resolution to work in Ubuntu?

I have tried all of this
[http://ubuntuforums.org/showpost.php?p=8560183&postcount=6](http://ubuntuforums.org/showpost.php?p=8560183&postcount=6)
[http://ubuntuforums.org/showthread.php?t=1364460&page=5](http://ubuntuforums.org/showthread.php?t=1364460&page=5)
And then I have no idea whats going on with this.
[http://ubuntuforums.org/showthread.php?t=1370258&page=2](http://ubuntuforums.org/showthread.php?t=1370258&page=2)

Which is fricken crazy!!! For the life of me I cannot get 1280x1024 to be activated on login.

This is just nuts.

Words cannot even describe how stupid this is.

What is the matter with ubuntu and resolutions? It is gonna cause me to have a Heart Attack.

I officially give up trying for the sake of my Heart!!!!!!

---

### Post by Jarvus on 2010-02-11
Below helped me out and actually worked.
[http://www.linuxreaders.com/2009/11/04/change-ubuntu-9-10-resolution/](http://www.linuxreaders.com/2009/11/04/change-ubuntu-9-10-resolution/)

---

### Post by Caps18 on 2010-02-12
> **Jarvus said:**
> Why do we have to go to hell and back to get our monitors supported resolution to work in Ubuntu?

I have tried all of this
[http://ubuntuforums.org/showpost.php?p=8560183&postcount=6](http://ubuntuforums.org/showpost.php?p=8560183&postcount=6)
[http://ubuntuforums.org/showthread.php?t=1364460&page=5](http://ubuntuforums.org/showthread.php?t=1364460&page=5)
And then I have no idea whats going on with this.
[http://ubuntuforums.org/showthread.php?t=1370258&page=2](http://ubuntuforums.org/showthread.php?t=1370258&page=2)

Which is fricken crazy!!! For the life of me I cannot get 1280x1024 to be activated on login.

This is just nuts.

Words cannot even describe how stupid this is.

What is the matter with ubuntu and resolutions? It is gonna cause me to have a Heart Attack.

I officially give up trying for the sake of my Heart!!!!!!

In the 10 years I have been using Linux, this is the one problem that has plagued almost every single install.  Why this doesn't get fixed is beyond me.  I don't even care about 3D acceleration or anything fancy, I just want the basic HD resolutions to work right out of the box with any graphics card.  In Windows I can pick modes that the monitors can't handle, in Linux I can't use th resolutions that the monitor should be using.

---

### Post by Jarvus on 2010-02-13
> **Caps18 said:**
> In the 10 years I have been using Linux, this is the one problem that has plagued almost every single install.  Why this doesn't get fixed is beyond me.  I don't even care about 3D acceleration or anything fancy, I just want the basic HD resolutions to work right out of the box with any graphics card.  In Windows I can pick modes that the monitors can't handle, in Linux I can't use th resolutions that the monitor should be using.

 I am so glad someone else is with me on this subject, seems like the moderators don't give a hoot. I so agree with you, resolution should work right out of the box with any gfx cards just like Microsoft Windows. I've had this prob ever since i started using [[COLOR=Red]Ubuntu 4.10[/COLOR]]. They need to get this sorted out badly, it is about time to work on this problem and not worry about example: [changing name of software sources to software store or w/e there doing.]

---

### Post by etnlIcarus on 2010-02-14
Just wanted to give my thanks for this fix and also make an enquiry. I'd also like to thank everyone in this thread for making no noticeable usage of the colloquialism, "automagic". ****, that phrase annoys me.

I've got a Samsung HDTV with 100hz, that I use as my PC monitor. It recently occurred to me that the reason videos looks so jumpy, is due to:
a) most videos being between 23.9 to 25 FPS
b) my monitor's refresh rate being stuck at 60hz (30 FPS)
c) my TV trying to kick that up to 100hz (50 FPS).

This resulted in most videos going crazy at 1 second intervals, with any motion on screen becoming jumpy. Forcing 50hz modesetting with xrandr has fixed the issue.


Now, for my enquiry.

I'm still on 9.04 and have the following in my xorg.conf:
```
Section "Monitor"
	Identifier	"Configured Monitor"
	VertRefresh	50-60
	Modeline "1920x1080_50.00"  141.45  1920 2032 2232 2544  1080 1081 1084 1112  -HSync +Vsync
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	DefaultDepth	24
	SubSection "Display"
		Modes		"1920x1080_50.00" "1440x900" "1280x1280" "1280x1024" "1280x960" "1152x921" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
EndSection
```

Yet no 50hz option is available in xrandr or xfce4-display-settings.

Additionally, I don't have a graphical login manager, I just use login and, "startx", manually, so I can't do the gdm init fix

I could create a script with the relevant xrandr commands and add it to my autostart folder, except in the past, when I've added scripts that alter modesetting, to xfce4's startup process, I've had xfce components like xfce4-panel crash, making that an undesirable fix.

Cheers in advance.

---

### Post by etnlIcarus on 2010-02-14
NM, figured out an alternative. Added this to my .xinitrc:
```
exec sh bin/xrandr_fix.sh &
exec xfce4-session
```

---

### Post by ccroy on 2010-02-20
Oh my God I am so happy! I did it!, well I cheated sort of, but I learned a lot!

After numerous attempts using the xrandr command I started to look at threads that mentioned xorg.conf. and started modifying it. Last night tried a "virtual resize" and the horizontal sync was totally gone and I had an unreadable screen. Fortunately I'm still just playing around with Unbuntu so I reloaded Unbuntu onto my root partition, installed all the updates and was back to where I started at least.

Today I found another thread that mentioned the "lspci" command. Finally I could see that SiS drivers were there for my chipset. Then I simply copied the xorg.conf that another user posted:

> Section "Device"
        Identifier      "Silicon Integrated Systems [SiS] 65x/M650/740 PCI/AGP VGA Display Adapter"
        Driver          "sis"
        BusID           "PCI:1:0:0"
EndSection

Section "Monitor"
        Identifier      "Generic Monitor"
        Option          "DPMS"
        HorizSync       28-51
        VertRefresh     43-60
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Device          "Silicon Integrated Systems [SiS] 65x/M650/740 PCI/AGP VGA Display Adapter"
        Monitor         "Generic Monitor"
        DefaultDepth    24
        SubSection "Display"
                Depth           1
                Modes           "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           4
                Modes           "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           8
                Modes           "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           15
                Modes           "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           16
                Modes           "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           24
                Modes           "1024x768" "800x600" "640x480"
        EndSubSection
EndSection


then I commented out the default values in my orignal xorg.conf with # 

I now have a working 1024x768 mode which is what I had with Windows XP.

So nice not to have to scroll all over anymore!

So, now what I need is a good resource, even a book, that lists command line commands and what they do. sort of like the "man" pages, but an overview. I'm only learning commands as I stumble across them.

Thanks so much everyone for your posts. Seems like I've found something that works!

Chris

---

### Post by legend_018 on 2010-03-06
> **sharaq said:**
> what is the operating system you are using? is it ubuntu 5.10??
I've used this in 9.10..

if you miss out any part of the output it gives this error message(which you have copied from the step 2)recheck it. I think you have missed the last part of it ,most likely, the part in bold letters. 


hope this will help you....


I get this same error, and i know it's typed in correctly. Any other ideas on this one?

---

### Post by legend_018 on 2010-03-06
> **sarum said:**
> Hello, I have the same 800x600 problem. I followed your advice to stage 3 and got this reply:-
X Error of failed request:  BadName (named color or font does not exist)
  Major opcode of failed request:  149 (RANDR)
  Minor opcode of failed request:  16 (RRCreateMode)
  Serial number of failed request:  21
  Current serial number in output stream:  21
If you can help in any way I'd be very grateful
Thankyou.......sarum


I get this same error, and I know it's being typed in correctly the xrandr --newmode line. : (. Any other ideas.

---

### Post by MeanRoy on 2010-03-06
[[COLOR="Red"]I'm definitely with you here![/COLOR]]("http://ubuntuforums.org/showpost.php?p=8812146&postcount=45")

My problem is a little different.

When I first tried the live CD the resolution choices included 1280 X 1024 and it worked just fine setting to that.
After I installed Ubuntu9.1 to my second HD I was able to set the res. to 1280 X 1024 with no problem.
It remained at that setting through several re-boots.

Then I tried to get Windoz back. I re-installed Grub2 etc. but it didn't work. (I have windoz on the first HD and Ubuntu on a second HD. - I'm on the trail of fixing that problem ...)

I restored the Windoz 2K MBR and fired up Windoz. Fine, it's back.
When I loaded the UbuntuLive CD though, I found I was limited,  as most in this thread, to 800 X 600.

I've played a bit with some of the solutions in this thread and have no doubt I'll get it working again.

Which brings me to my real question:
It is apparent that Ubuntu has a means of checking the monitor and building a table of available resolutions at installation.

Why would it work initially and subsequently fail? 

Is there a way to force a scan from a terminal with an option helping the scanner?

Roy.

------ edit ---------
The monitor I'm using is an NEC multisync LCD1700V

---

### Post by MeanRoy on 2010-03-06
[COLOR="Red"][SIZE="4"]OK, Ubuntu is totally blameless![/SIZE][/COLOR]
After cogitating on the fact that the resolution settings originally worked fine I shut the system down and re-seated the connectors.

That did it, after re-booting all is well.

Still have my boot problem but I'm hot on the trail. ;)

> [SIZE="1"]OK, since others have changed resolution with xrandr I tried to do the same. Unfortunately it didn't work for me. Here's the I/O:
```
ubuntu@ubuntu:~$ cvt 1024 768
# 1024x768 59.92 Hz (CVT 0.79M3) hsync: 47.82 kHz; pclk: 63.50 MHz
Modeline "1024x768_60.00"   63.50  1024 1072 1176 1328  768 771 775 798 -hsync +vsync
ubuntu@ubuntu:~$ xrandr --newmode "1024x768_60.00"   63.50  1024 1072 1176 1328  768 771 775 798 -hsync +vsync
ubuntu@ubuntu:~$ xrandr --addmode default 1024x768_60.00
ubuntu@ubuntu:~$ xrandr --output default --mode 1024x768_60.00
xrandr: Configure crtc 0 failed
ubuntu@ubuntu:~$ xrandr
Screen 0: minimum 320 x 240, current 800 x 600, maximum 1280 x 1024
default connected 800x600+0+0 0mm x 0mm
   800x600        60.0*    56.0  
   768x576        60.0  
   720x576        60.0  
   856x480        60.0  
   800x480        60.0  
   720x480        61.0  
   640x480        60.0  
   400x300        60.0  
   320x240        61.0  
   856x600        60.0  
   1280x1024_60.00   59.9  
   1024x768_60.00   59.9  
ubuntu@ubuntu:~$ 
```
(The 1280x1024 is the first I tried, when it didn't work I tried to back off to 1024x768 but got the same result.)
Having read some of the other threads I ran lspci and got this:
```
ubuntu@ubuntu:~$ lspci
00:00.0 Host bridge: Silicon Integrated Systems [SiS] 730 Host (rev 02)
00:00.1 IDE interface: Silicon Integrated Systems [SiS] 5513 [IDE] (rev d0)
00:01.0 ISA bridge: Silicon Integrated Systems [SiS] SiS85C503/5513 (LPC Bridge)
00:01.1 Ethernet controller: Silicon Integrated Systems [SiS] SiS900 PCI Fast Ethernet (rev 82)
00:01.2 USB Controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 07)
00:01.3 USB Controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 07)
00:01.4 Multimedia audio controller: Silicon Integrated Systems [SiS] SiS PCI Audio Accelerator (rev 02)
00:02.0 PCI bridge: Silicon Integrated Systems [SiS] Virtual PCI-to-PCI bridge (AGP)
00:0b.0 Communication controller: Agere Systems Venus Modem (V90, 56KFlex)
01:00.0 VGA compatible controller: Silicon Integrated Systems [SiS] 630/730 PCI/AGP VGA Display Adapter (rev 31)
```
Since I haven't been able to fix my boot problem yet I can't try the fix that worked for ccroy yet.

Roy.[/SIZE]

---

### Post by legend_018 on 2010-03-07
here is an update. Modified that file so it looks like this now. See below under xorg.config. Rebooted. No change. 800X600 is the highest it will go. 

HERE IS ME RUNNING THESE COMMANDS AGAIN AFTER rebooting. Good news, it let me run all the commands without errors finally. but than got the error at the end. 


$ xrandr
Screen 0: minimum 320 x 240, current 800 x 600, maximum 800 x 600
default connected 800x600+0+0 0mm x 0mm
   800x600        60.0*    56.0  
   640x480        60.0  
   400x300        60.0     56.0  
   320x240        60.0  
  1024x768_60.00 (0x6c)   63.5MHz
        h: width  1024 start 1072 end 1176 total 1328 skew    0 clock   47.8KHz
        v: height  768 start  771 end  775 total  798           clock   59.9Hz
chayse@chayse-desktop:~$ xrandr --output default --mode 1024x768_60.00
xrandr: cannot find mode 1024x768_60.00
chayse@chayse-desktop:~$ xrandr --addmode default 1024x768_60.00
chayse@chayse-desktop:~$ xrandr --output default --mode 1024x768_60.00
xrandr: screen cannot be larger than 800x600 (desired size 1024x768)

_**xorg.config**_

Section "ServerLayout"
  Identifier "Default Layout"
  Screen 0 "Screen0" 0 0
EndSection

Section "Monitor"
  Identifier "Monitor0"
  Modeline "1024x768_60.00" 63.50 1024 1072 1176 1328 768 771 775 798 -hsync +vsync
  Option "PreferredMode" "1024x786_60.00"
EndSection

Section "Device"
  Identifier "Device0"
  Driver "nv"
 Option "UseEDID" "false"
EndSection

Section "Screen"
  Identifier "Screen0"
  Device "Device0"
  Monitor "Monitor0"
  DefaultDepth 24
  SubSection "Display"
    Modes "1024x768_60.00"
    Depth 24
  EndSubSection
EndSection

---

### Post by mawiles on 2010-03-07
interesting, everything works upto step5

mystdragon@dragon-1:~$ cvt 1440 900
# 1440x900 59.89 Hz (CVT 1.30MA) hsync: 55.93 kHz; pclk: 106.50 MHz
Modeline "1440x900_60.00"  106.50  1440 1528 1672 1904  900 903 909 934 -hsync +vsync
mystdragon@dragon-1:~$ xrandr --newmode "1440x900_60.00"  106.50  1440 1528 1672 1904  900 903 909 934 -hsync +vsync
mystdragon@dragon-1:~$ xrandr --addmode default 1440x900_60.00
mystdragon@dragon-1:~$ xrandr --output default --mode 1440x900_60.00
xrandr: screen cannot be larger than 800x600 (desired size 1440x900)
mystdragon@dragon-1:~$ 

Any assistance would be appreciated.

I had previously tried jamming the settings in the xorg.conf file, but it was being ignored.  I have tried many different drivers, all the way down to 171. I have tried envyng thing.  And by the way... this is NOT an Ubuntu problem, it is derived from both XORG and the video drivers.  Every distro I have tried including Sabayon 5 have this issue with my system, which is a fairly simple system.  Nvidia 8800 GT.  I don't know why the powers that be fix this.  It is insanely more difficult than editing the old xorg.conf file, which used to work in Versions 9.04 and below.

---

### Post by mawiles on 2010-03-08
Very interesting indeed.  I never got anything to work, manually editing xorg.conf, using the xrandr methods.  However, I removed the DVI cable and put back the analog cable with an adapter to the nvidia 8800 GT card, and everything now is working, including Twinview.  I hooked my old 19" CRT to have a dual screen.  So if your stuck like I was, and nothing seemed to work, and you are using a DVI cable, you might want to consider trying an analog cable.:p

---

### Post by sdleihssirhc on 2010-04-08
I'm having the "Connection crtc 0 failed" error. I can do --newmode, and then --addmode, but I can't --output to my new resolution. Any ideas?

---

### Post by etnlIcarus on 2010-04-08
> **mawiles said:**
> Very interesting indeed.  I never got anything to work, manually editing xorg.conf, using the xrandr methods.  However, I removed the DVI cable and put back the analog cable with an adapter to the nvidia 8800 GT card, and everything now is working, including Twinview.  I hooked my old 19" CRT to have a dual screen.  So if your stuck like I was, and nothing seemed to work, and you are using a DVI cable, you might want to consider trying an analog cable.:p
Back in the good ol' days of long and complicated xorg.conf files that actually did anything, I'd generally have to install while using a VGA cable, then switch to a DVI cable, once I had the box up and running.

---

