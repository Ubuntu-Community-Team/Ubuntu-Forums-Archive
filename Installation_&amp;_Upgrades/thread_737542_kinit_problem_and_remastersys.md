---
title: "kinit problem and remastersys"
date: 2008-03-27
forum: Installation &amp; Upgrades
---

### Post by wandalalakers on 2008-03-27
I get this error after booting a custom remastersys live cd that I made.
I've tried doing "sudo remastersys backup custom.iso" and "sudo remastersys dist" and to create the image I still get the same result below.

kinit: name_to_dev_t(/dev/disk/by-uuid/a bunch of numbers)= sda5(8,5)
kinit: trying to resume from /dev/disk/by-uuid...
kinit: No resume image, doing normal boot.
ubuntu 7.10 desktop tty1
desktop login

I've also tried "sudo dpkg-reconfigure xserver-xorg" once I logged on with my username and password to see if I can get to a desktop but nothing happens.
Can anyone tell me what I'm doing wrong?  Thx

---

### Post by wandalalakers on 2008-03-28
Oh well.  I guess no one has seen this error.

---

### Post by sh4d0w808 on 2008-03-28
Try to ask the developer of Remastersys...

---

### Post by wandalalakers on 2008-03-28
Great minds think alike.  I just posted this problem on their forum this morning.  Thx for responding.

---

### Post by eel on 2008-04-11
did you find your answer there?
i have the same problem but i don't know what remastersys is so technically speaking i might not have the same problem at all but whatever it is it gives the same error message as you got. 
Furthermore i am now stuck in a screenresolution of 640 x 480.

---

### Post by wandalalakers on 2008-04-11
This is how I fixed my problem.  I'm using kubuntu 7.10 by the way.
If you still have problems please let me know.
What video card do you have?

I modified my kdmrc file.
For some reason my boot screen was a plain jane login screen.
I modified a line in my kdmrc file so that the kubuntu theme was enabled.

Here is a copy of my kdmrc file.
(use kdesu kate /etc/kde3/kdm/kdmrc to edit your kdmrc file)

[General]
ConfigVersion=2.3
ConsoleTTYs=tty1,tty2,tty3,tty4,tty5,tty6
PidFile=/var/run/kdm.pid
ReserveServers=:1,:2,:3
ServerVTs=-7
StaticServers=:0

[Shutdown]
BootManager=None
HaltCmd=/sbin/poweroff
RebootCmd=/sbin/reboot

[X-*-Core]
AllowNullPasswd=false
AllowRootLogin=false
AllowShutdown=Root
AutoReLogin=false
ClientLogFile=.xsession-errors-%s
Reset=/etc/kde3/kdm/Xreset
Session=/etc/kde3/kdm/Xsession
Setup=/etc/kde3/kdm/Xsetup
Startup=/etc/kde3/kdm/Xstartup

[X-*-Greeter]
AntiAliasing=true
ColorScheme=kubuntuColours
EchoMode=OneStar
FaceSource=AdminOnly
FailFont=Sans Serif,10,-1,5,75,0,0,0,0,0
GUIStyle=Plastik
GreetFont=Sans Serif,22,-1,5,50,0,0,0,0,0
GreetString=
GreeterPos=50,50
HiddenUsers=
Language=en_GB
LogoArea=Logo
LogoPixmap=/usr/share/apps/kdm/pics/kdelogo.png
MaxShowUID=29999
MinShowUID=1000
Preloader=/usr/bin/preloadkde
SelectedUsers=
ShowUsers=NotHidden
SortUsers=true
StdFont=Sans Serif,10,-1,5,50,0,0,0,0,0
Theme=/usr/share/apps/kdm/themes/kubuntu
UseBackground=true
UseTheme=true
UserCompletion=false
UserList=false

[X-:*-Core]
AllowNullPasswd=true
AllowShutdown=All
NoPassEnable=false
NoPassUsers=
ServerArgsLocal=-nolisten tcp
ServerCmd=/usr/bin/X -br

[X-:*-Greeter]
AllowClose=true
DefaultUser=false
FocusPasswd=true
LoginMode=DefaultLocal
PreselectUser=None

[X-:0-Core]
AutoLoginAgain=false
AutoLoginDelay=0
AutoLoginEnable=false
AutoLoginLocked=false
AutoLoginUser=glenise
ClientLogFile=.xsession-errors

[Xdmcp]
Enable=false
Willing=/etc/kde3/kdm/Xwilling

---

### Post by wandalalakers on 2008-04-11
With X server/X window not loaded type dpkg-reconfigure xserver-xorg.
I'm using a Nvidia fx 5200 card in this particular pc.
I think the first time I used remastersys I used the "make a distributable copy to share with friends" option.
The 2nd time I used the "backup complete system including user data" option.
Both times I got the "kinit: No resume image, doing normal boot" error.

---

