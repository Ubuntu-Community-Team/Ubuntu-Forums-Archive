---
title: "Resoltion Problem , please help , please"
date: 2011-11-03
forum: Installation &amp; Upgrades
---

### Post by x_mot on 2011-11-03
Hello Guys 
I'm a newbie in ubuntu , my first time with ubuntu 10.04 was last week , every thing went kewl until i update the Nvidia driver from the additional drivers , my resolution stuck with 800*600 and i cant see all the screen .
so i decided to improve to Ubuntu 11.10 , and i updte the Nvidia, but also same problem.

If i must say i'm really newbie "I don't know any command" , so please clarify your answer.

Thanks In advance.

Assad

---

### Post by x_mot on 2011-11-03
maybe i should tell that i have an internal card(with the motherboard and i dont need to use it ) and external card( the nvidia).

---

### Post by x_mot on 2011-11-03
can any one help me ?

---

### Post by matt_symes on 2011-11-03
Hi

Have you disabled the internal graphics card in the BIOS ?

I will not really be able to help until tonight, maybe....

To get the ball rolling for others, open a terminal and type

```
sudo lshw -c display
```Enter your password. It will not be echoed to the screen. 

This will tell us about your video hardware as seen by Ubuntu.

Copy and paste the text produced back into your next reply by highlighting the text and right clicking and select copy. You can also copy and paste commands from here into the terminal and this saves typing errors.

Then in the terminal type

```
xrandr
```Copy and paste the results back here. This will tell us about the resolutions you currently have.

```
cat /etc/X11/xorg.conf
```Copy and paste the results of this back here as well. This is a configuration file used to configure your display with the video driver.

Commands in the terminal are case sensitive so in the above x11 is not the same as X11.

That should get the ball rolling for you.

Please wait 24 hours before bumping your posts. People come and go on here all the time and everybody has different skills. If you bump too soon somebody may give you a slap on the proverbial wrist :)

Kind regards

---

### Post by x_mot on 2011-11-03
Hay Matt_symes
really happy to see someone answered, so thank you.
sorry for my hesitation :P

here are the code and its result.



sudo lshw -c display

 >  *-display               
       description: VGA compatible controller
       product: G96 [GeForce 9400 GT]
       vendor: nVidia Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       version: a1
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vga_controller bus_master cap_list rom
       configuration: driver=nvidia latency=0
       resources: irq:18 memory:fa000000-faffffff memory:c0000000-dfffffff memory:f8000000-f9ffffff ioport:ef00(size=128) memory:fb000000-fb07ffff


xrandr

> 
assad@assad-GA-MA74GM-S2:~$ xrandr
xrandr: Failed to get size of gamma for output default
Screen 0: minimum 320 x 240, current 640 x 480, maximum 640 x 480
default connected 640x480+0+0 0mm x 0mm
   640x480        50.0* 
   320x240        51.0  



cat /etc/X11/xorg.conf
> 
Section "Device"
	Identifier	"Default Device"
	Option	"NoLogo"	"True"
EndSection



i hope i done every thing correctly , and i'm waiting for ur replay , thanks again

Assad:)

---

### Post by matt_symes on 2011-11-04
Hi

Sorry for my late reply. I have been very busy. I thought someone else may have jumped in here.

I think it may be having trouble reading your EDID information from your monitor. So a couple of questions.

Are you using a KVM (keyboard video mouse switch) ?

What is the make and model of your monitor ? What connector type is it connected to ?

Can you post the output of

```
grep "(EE)" /var/log/Xorg.0.log
```

This will tell us a bit more information as to the problem.

Kind regards

---

### Post by MAFoElffen on 2011-11-04
> **x_mot said:**
> Hay Matt_symes
really happy to see someone answered, so thank you.
sorry for my hesitation :P

sudo lshw -c display

xrandr

cat /etc/X11/xorg.conf

i hope i done every thing correctly , and i'm waiting for ur replay , thanks again

Assad:)
How about posting the results of 
```

xrandr -prop
sudo hwinfo --monitor
sudo hwinfo --framebuffer

```If hwinfo returns command not found, please install it and run again:
```

sudo apt-get install hwinfo

```Instead of posting a snippet of the /var/log/xorg.0.log. please post the whole log....

The reason I asked for those, is that the info returned from randr only returned 640x480 as the highest resolution of your monitor.

Along with that, you said you had installed NVidia drivers (?), but your xorg.conf file tells another story...
```

Section "Device"
       Identifier    "Default Device"
       Option    "NoLogo"    "True"
EndSection                      

```The content above iis a basic xorg.conf file that is not pointing to a nvidia driver... No line in the Device Section saying: Driver "nvidia"

In fact there is no specific driver configured at all, which would try opensourced drivers on it's own until it found something on it's own...

So after gathering that info-- Open a terminal session:
```
[FONT=monospace]
[/FONT]sudo apt-get update 
sudo nvidia-installer --uninstall 
sudo apt-get remove nvidia-* 
sudo apt-get install 'uname -r' 
sudo apt-get install nvidia-current   
sudo nvidia-xconfig
sudo apt-get upgrade

```That should remove any remnants of any nivida driver that might be there (installed, half installed or orphaned...)  If the second or third line reports back that none were found or didn't exist- That's fine. We just want to make sure.

Reboot and test.  You should then be using NVidia Drivers.

Please repost the /var/log/Xorg.0.log file again... I want to make sure that the NVidia driver is being loaded and that it is reading the EDID data from your monitor.  If not- then there might be a little more work to do...

---

### Post by rastatab on 2011-11-04
greetings rasta, came across this thread looking for a solution for the same sort of problem, couldn't get 11.10 to install on my desktop, so I used an older v 8.04 that worked well on my system and upgraded from that, thinking it would fix the black screen on the 11.10 install problem.
now only get a low rez 640-480 screen.
would you be able to help.
Did all the commands you posted. with thanks.

---

### Post by x_mot on 2011-11-04
Hello guys 
i'm really pleased to get reply from you guys .

@matt_symes
1-good luck with things you busy with and thanks for reply.
About KVM thing , I never knew about it , but I read litl bit and no I dont use this , its regular PC 
and the link here have the specs [http://www.superwarehouse.com/ViewSonic_VA902B_Black_19_LCD_Monitor/VA902B/p/623492](http://www.superwarehouse.com/ViewSonic_VA902B_Black_19_LCD_Monitor/VA902B/p/623492)
 
about the 
code you gave me 
grep "(EE)" /var/log/Xorg.0.log


the result is 
```

	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    12.213] (EE) Failed to load module "nv" (module does not exist, 0)

```

that all I can tell you and thanks again. 



@MAFoElffen
Thanks for reply too , and I did what you asked me  and firsts come first


xrandr -prop

```

usage: xrandr [options]
  where options are:
  -display <display> or -d <display>
  -help
  -o <normal,inverted,left,right,0,1,2,3>
            or --orientation <normal,inverted,left,right,0,1,2,3>
  -q        or --query
  -s <size>/<width>x<height> or --size <size>/<width>x<height>
  -r <rate> or --rate <rate> or --refresh <rate>
  -v        or --version
  -x        (reflect in x)
  -y        (reflect in y)
  --screen <screen>
  --verbose
  --current
  --dryrun
  --nograb
  --prop or --properties
  --fb <width>x<height>
  --fbmm <width>x<height>
  --dpi <dpi>/<output>
  --output <output>
      --auto
      --mode <mode>
      --preferred
      --pos <x>x<y>
      --rate <rate> or --refresh <rate>
      --reflect normal,x,y,xy
      --rotate normal,inverted,left,right
      --left-of <output>
      --right-of <output>
      --above <output>
      --below <output>
      --same-as <output>
      --set <property> <value>
      --scale <x>x<y>
      --transform <a>,<b>,<c>,<d>,<e>,<f>,<g>,<h>,<i>
      --off
      --crtc <crtc>
      --panning <w>x<h>[+<x>+<y>[/<track:w>x<h>+<x>+<y>[/<border:l>/<t>/<r>/<b>]]]
      --gamma <r>:<g>:<b>
      --primary
  --noprimary
  --newmode <name> <clock MHz>
            <hdisp> <hsync-start> <hsync-end> <htotal>
            <vdisp> <vsync-start> <vsync-end> <vtotal>
            [+HSync] [-HSync] [+VSync] [-VSync]
  --rmmode <name>
  --addmode <output> <name>
  --delmode <output> <name>

```




sudo hwinfo --monitor


```

> hal.1: read hal dataprocess 13747: arguments to dbus_move_error() were incorrect, assertion "(dest) == NULL || !dbus_error_is_set ((dest))" failed in file ../../dbus/dbus-errors.c line 280.
This is normally a bug in some application using the D-Bus library.
libhal.c 3483 : Error unsubscribing to signals, error=The name org.freedesktop.Hal was not provided by any .service files
35: None 00.0: 10000 Monitor                                    
  [Created at fb.71]
  Unique ID: rdCR.EY_qmtb9YY0
  Hardware Class: monitor
  Model: "Generic Monitor"
  Vendor: "Generic"
  Device: "Monitor"
  Resolution: 640x480@73Hz
  Driver Info #0:
    Max. Resolution: 640x480
    Vert. Sync Range: 50-90 Hz
    Hor. Sync Range: 31-38 kHz
  Config Status: cfg=new, avail=yes, need=no, active=unknown


```

sudo hwinfo --framebuffer

```
> hal.1: read hal dataprocess 13681: arguments to dbus_move_error() were incorrect, assertion "(dest) == NULL || !dbus_error_is_set ((dest))" failed in file ../../dbus/dbus-errors.c line 280.
This is normally a bug in some application using the D-Bus library.
libhal.c 3483 : Error unsubscribing to signals, error=The name org.freedesktop.Hal was not provided by any .service files
02: None 00.0: 11001 VESA Framebuffer                           
  [Created at bios.464]
  Unique ID: rdCR.y0ssy634OaE
  Hardware Class: framebuffer
  Model: "NVIDIA G96 Board - 09740000"
  Vendor: "NVIDIA Corporation"
  Device: "G96 Board - 09740000"
  SubVendor: "NVIDIA"
  SubDevice: 
  Revision: "Chip Rev"
  Memory Size: 14 MB
  Memory Range: 0xf9000000-0xf9dfffff (rw)
  Mode 0x0300: 640x400 (+640), 8 bits
  Mode 0x0301: 640x480 (+640), 8 bits
  Mode 0x0303: 800x600 (+800), 8 bits
  Mode 0x0305: 1024x768 (+1024), 8 bits
  Mode 0x0307: 1280x1024 (+1280), 8 bits
  Mode 0x030e: 320x200 (+640), 16 bits
  Mode 0x030f: 320x200 (+1280), 24 bits
  Mode 0x0311: 640x480 (+1280), 16 bits
  Mode 0x0312: 640x480 (+2560), 24 bits
  Mode 0x0314: 800x600 (+1600), 16 bits
  Mode 0x0315: 800x600 (+3200), 24 bits
  Mode 0x0317: 1024x768 (+2048), 16 bits
  Mode 0x0318: 1024x768 (+4096), 24 bits
  Mode 0x031a: 1280x1024 (+2560), 16 bits
  Mode 0x031b: 1280x1024 (+5120), 24 bits
  Mode 0x0330: 320x200 (+320), 8 bits
  Mode 0x0331: 320x400 (+320), 8 bits
  Mode 0x0332: 320x400 (+640), 16 bits
  Mode 0x0333: 320x400 (+1280), 24 bits
  Mode 0x0334: 320x240 (+320), 8 bits
  Mode 0x0335: 320x240 (+640), 16 bits
  Mode 0x0336: 320x240 (+1280), 24 bits
  Mode 0x033d: 640x400 (+1280), 16 bits
  Mode 0x033e: 640x400 (+2560), 24 bits
  Mode 0x0345: 1600x1200 (+1600), 8 bits
  Mode 0x0346: 1600x1200 (+3200), 16 bits
  Mode 0x0347: 1400x1050 (+1400), 8 bits
  Mode 0x0348: 1400x1050 (+2800), 16 bits
  Mode 0x0349: 1400x1050 (+5600), 24 bits
  Mode 0x034a: 1600x1200 (+6400), 24 bits
  Mode 0x0352: 2048x1536 (+8192), 24 bits
  Mode 0x0360: 1280x800 (+1280), 8 bits
  Mode 0x0361: 1280x800 (+5120), 24 bits
  Mode 0x0362: 768x480 (+768), 8 bits
  Mode 0x0364: 1440x900 (+1440), 8 bits
  Mode 0x0365: 1440x900 (+5760), 24 bits
  Mode 0x0368: 1680x1050 (+1680), 8 bits
  Mode 0x0369: 1680x1050 (+6720), 24 bits
  Mode 0x037b: 1280x720 (+5120), 24 bits
  Mode 0x037c: 1920x1200 (+1920), 8 bits
  Mode 0x037d: 1920x1200 (+7680), 24 bits
  Config Status: cfg=new, avail=yes, need=no, active=unknown

```


thats all  and if there any thing please tell me . I hope every things gone well :P 

thanks all who trying to help me and w8ing for more replys

---

### Post by x_mot on 2011-11-04
i don't know guys , i dis activate the update in the "additional drivers update" and re install the xorg.cofg , and it works just fine with the optimum resolution .

also i still have problem with the game i'm playing , flashing in the screen " the flashing in the game or either i'm using the ubuntu overall " but still better that stuck withing 600*400


i dont know if someone have something to help

---

### Post by MAFoElffen on 2011-11-05
> **x_mot said:**
> i don't know guys , i dis activate the update in the "additional drivers update" and re install the xorg.cofg , and it works just fine with the optimum resolution .

also i still have problem with the game i'm playing , flashing in the screen " the flashing in the game or either i'm using the ubuntu overall " but still better that stuck withing 600*400

i dont know if someone have something to help
Good deal on the resolution. Like I was trying to say, which your data confirmed, that the driver was not setup and needed to be reinstalled.  You did and now its working.

Which driver did you select and are now using? nvidia-current or nvidia-173?  That may have some bearing on what you are experiencing now...  You said ??? I'm trying to figure out what problem you are having with what game(?) Please explian
> 
flashing in the screen " the flashing in the game
Could I get a better translation on that?  I don't understand... What is it doing, not doing or doing wrong?

---

### Post by x_mot on 2011-11-05
> **MAFoElffen said:**
> Good deal on the resolution. Like I was trying to say, which your data confirmed, that the driver was not setup and needed to be reinstalled.  You did and now its working.

Which driver did you select and are now using? nvidia-current or nvidia-173?  That may have some bearing on what you are experiencing now...  You said ??? I'm trying to figure out what problem you are having with what game(?) Please explian
Could I get a better translation on that?  I don't understand... What is it doing, not doing or doing wrong?

thanks for reply
i meant by flashing , is that the screen keeps blinks , you know what , its like shutted for a sec , and then works fine.
tha game i'm playing is tibia MMORPG , there is a console also keep blinking and lags a litl bit

i hope thats good info

ah about the setting i use is nvidia 173 and i disabled it , when i eanable it , the resolution will damn again.
thanks 
Assad

---

### Post by MAFoElffen on 2011-11-05
> **x_mot said:**
> thanks for reply
i meant by flashing , is that the screen keeps blinks , you know what , its like shutted for a sec , and then works fine.
tha game i'm playing is tibia MMORPG , there is a console also keep blinking and lags a litl bit

i hope thats good info

ah about the setting i use is [COLOR=Red]nvidia 173[/COLOR] and i disabled it , when i enable it , the resolution will damn again.
thanks 
Assad
According to the Hex ID of your Card, you should be using nvidia-current instead of nvidia-173... which is going to be another trip to Aditional drivers to remove nividia-173 and to install/activate nvidia-current.  Check here for reference on the driver pick:
[COLOR=Red][SIZE=2][COLOR=Black][SIZE=1]**[Finding the Right NVidia Driver from the Card ID]("http://ubuntuforums.org/showpost.php?p=10910784&postcount=284")**

Next step is test the graphics in your game again... If it is still having issues, start nvidia settings in in System Settings. Go to the X Screen 0 > OpenGL Settings > ...Make sure the "Sync to VBlank is disabled. (Meaning, it's checkbox should not be checked.)
[/SIZE][/COLOR][/SIZE][/COLOR]

---

