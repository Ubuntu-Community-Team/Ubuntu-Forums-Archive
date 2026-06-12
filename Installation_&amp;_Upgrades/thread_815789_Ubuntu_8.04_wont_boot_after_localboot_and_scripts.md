---
title: "Ubuntu 8.04 wont boot after localboot and scripts"
date: 2008-06-02
forum: Installation &amp; Upgrades
---

### Post by BrianP42 on 2008-06-02
I have just received my Ubuntu 8.04 LTS desktop disc and installed it on a second 10Gb HDD everything went well but when I try to boot up it stops on "Running localboot scripts(/etc/rc.local)(OK)" and wont progress further.I have seen the problem elsewhere in Google but the fix is beyond me as a novice.If anyone can help me please show details with no expectation of previous knowledge.The comp also has a 80Gb HDD with Win 2000, 2.8Ghz Celeron D,512 Mb Ram,MSI PM8M3-V M/Board,Samsung CRT 17" Monitor.Hope you can help,thanks in advance.BrianP

---

### Post by PmDematagoda on 2008-06-02
What is the VGA card you use?

Also, when you reach that error message, switch to a tty with Ctrl+Alt+F1 and then execute:-
```
sudo xfix
```

After that is done, do:-
```
sudo /etc/init.d/gdm restart
```
And see if that fixes the problem.

---

### Post by BrianP42 on 2008-06-02
Thanks for the quick response.Taking the recommended steps I got a message "Ubuntu running in low graphics mode,your screen and graphics card could not be detected correctly,to use higher resolution visual effects or multiple screens,you have to configure the display yourself." I ticked the box "Always run in low graphics mode." and everything looks good, I have rebooted OK so do I have to live with the low graphics or can I configure it with help? The graphics card is onboard the MSI PM8M3-V motherboard (I have just checked the AGP slot is empty).There is reference to VIA VT8237R plus chipset in the hand book which might be the graphics IC if that is any help.I really appreciate you assistance to get this going, please dont forget I am a novice for further directions.
Thanks again BrianP

---

### Post by PmDematagoda on 2008-06-03
Post the VGA card you use.

Also, try reconfiguring the X-Server with:-
```
sudo dpkg-reconfigure -phigh xserver-xorg
```
and see if that allows you to run the X-Server in normal mode.

---

### Post by BrianP42 on 2008-06-03
Hi and thanks again for the reply, the VGA is onboard the MSI PM8M3-V M/Board and is called S3 UniChrome Pro integrated Graphics.
I have tried sudo dpkg-reconfigure -phigh xserver-xorg with the following results:-
Package ex-server is not installed and no info is available.
Use dpkg --info (=dpkg-deb --info) to examine archive files and dpkg --contents (=dpkg-deb --contents) to list their contents.
/usr/sbir/dpkg-reconfigure. exserver-xorg is not installed.

My knowledge is so small it took me a while to find out how to get into the DOS type page with Application/ Accessories/Terminal to input and I have got a Ubuntu book on order so maybe you will suggest I wait until I get more fimiliar with Ubuntu.I cant get the email going on the Ubuntu installed computer because I cant see the "Forward" button on the page because of the safe screen resolution.When I use 8.04 with the disc the resolution is 1080X768 I think but the installed is much lower.Thanks again, you help is appreciated.BrianP

---

### Post by PmDematagoda on 2008-06-03
Are you sure that you executed:-
```
sudo dpkg-reconfigure -phigh xserver-xorg
```
and not:-
```
sudo dpkg-reconfigure -phigh exserver-xorg
```
because the error suggests that you made a mistake in spelling. The command has to be exact.

---

### Post by BrianP42 on 2008-06-05
Hi, sorry about the error.The result was xserver-xorg postinst warning: overwriting possibly-customised configuration file; back up in /etc/x11/org.config 20080605092343 After that I get brian@brian-desktop: ...$prompt
In the Dialog box "Ubuntu is running in Low Graphic" I have selected Samsung Syncmaster 750s and set the res at 1080X784 and the graphics card as S3 Unichrome but iut still reverts back to the safe mode.Thanks BrianP

---

### Post by PmDematagoda on 2008-06-05
Post the outputs of:-
```
cat /etc/X11/xorg.conf
```
and
```
cat /var/log/Xorg.0.log
```

---

### Post by BrianP42 on 2008-06-06
Identifier     "Configured Mouse"
Driver         "mouse"
Option         "CorePointer"
EndSection
Section "Device"
            Identifier "Configured Video Device"
EndSection
Section "Monitor"
            Identifier "Configured Monitor"
EndSection
Section "Screen"
            Identifier "Default Screen"
            Monitor "Configured Monitor"
            Device "Configured Video Device"
EndSection
Section  "ServerLayout"
            Identifier Default Layout"
            Screen "Default Screen"
EndSection
brian@brian-desktop : $prompt


(**)Configured Mouse: Sensitivity 1
(**)Option "CoreKeyboard"
(**)Generic Keyboard:always report core events
(**)Option "Protocol" "Standard"
(**)Generic Keyboard:Protocol: standard
(**)Option "Autorepeat" "500  30"
(**)Option XkbRules" "xorg"
(**)Generic Keyboard XkbRules: "xorg"
(**)Option "XkbModel" "pc105"
(**)Generic Keyboard:XkbModel: "pc105"
(**)Option "XkbLayout"  "us"
(**)Generic Keyboard: XkbLayout: "us"
(**)option "CustomKeycodes" "off"
(**)Generic Keyboard: CustomKeycodes disabled
(II)evaluating device (Generic Keyboard)
(II)XINPUT :Adding extended input device"Generic Keyboard"(type:KEYBOARD)
(II)evaluating device (Configured Mouse)
(II)XINPUT:Adding extended input device "Configured Mouse" (type:MOUSE)
(--)Configured Mouse:PnP-detected protocol:ExplorerPS/2
(II)Configured Mouse: ps2EnableDataReporting:succeeded
Set Client version: 0 9
SetGrabKeyState-disabled
SetGrabKeyState-enabled
brian@brian-desktop: $prompt
I think I mentioned that Ubuntu is on another computer with no email access because of safe mode screen so I have to write it down then input it into the forum page so I hope there is no errors, thanks again for your help..BrianP

---

### Post by PmDematagoda on 2008-06-07
Install the Unichrome drivers with:-
```
sudo apt-get install xserver-xorg-video-unichrome
```
and then run:-
```
sudo xfix
```
and see if that fixes the problem.

---

### Post by BrianP42 on 2008-06-07
Hi,Result of input: 
Reading Package list...Done
Building dependency tree
Reading state information...Done
Some packages could not be installed.This may mean that you have requested an impossible situation or if you are using the unstable distribution that some required packages have not yet been created or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that the package is simply not installable and a bug report against that package should be filed.
The following information may help to resolve the situation.
The following packages have unmet dependencies:
  xserver-xorg-video-unichrome: Depends: xserver-xorg-core (>= 1:1.1.1) but it is not going to be installed
E;Broken packages
brian@brian-desktop: $prompt

sudo xfix result:
sudo: xfix: command not found
brian@brian-desktop: $prompt
Thanks BrianP

---

### Post by PmDematagoda on 2008-06-08
Post the output of:-
```
cat /etc/apt/sources.list
```

---

### Post by BrianP42 on 2008-06-08
brian@briandesktop:~$
cat /etc/apt/sources.list
#deb cdrom:[Ubuntu 8.04 _Hardy Heron_ Release
i386 (20080423)]/ hardy main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.
deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) hardy main restricted
debsrc
[http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) hardy main restricted
## Major bug fix updates produced after the final release of the
## distribution.
deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) hardyupdates
main restricted
debsrc
[http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) hardyupdates
main restricted
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) hardy universe
debsrc
[http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) hardy universe
deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) hardyupdates
universe
debsrc
[http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) hardyupdates
universe
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) hardy multiverse
debsrc
[http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) hardy multiverse
deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) hardyupdates
multiverse
debsrc
[http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) hardyupdates
multiverse
## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) hardybackports
main restricted universe multiverse
# debsrc
[http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) hardybackports
main restricted universe multiverse
## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) hardy partner
# debsrc
[http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) hardy partner
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardysecurity
main restricted
debsrc
[http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardysecurity
main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardysecurity
universe
debsrc
[http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardysecurity
universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardysecurity
multiverse
debsrc
[http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardysecurity
multiverse
brian@briandesktop:~$

---

### Post by PmDematagoda on 2008-06-08
Do:-
```
sudo apt-get update
```
and execute:-
```
sudo apt-get install -f
```
and see if that fixes the broken packages. If it doesn't, post the output of:-
```
dpkg -C
```

---

### Post by BrianP42 on 2008-06-08
brian@brian-desktop:~$ sudo apt-get update 
[sudo] password for brian:  
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) hardy Release.gpg 
Ign [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) hardy/main Translation-en_AU 
Ign [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) hardy/restricted Translation-en_AU 
Ign [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) hardy/universe Translation-en_AU 
Ign [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) hardy/multiverse Translation-en_AU 
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) hardy-updates Release.gpg 
Ign [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) hardy-updates/main Translation-en_AU 
Ign [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) hardy-updates/restricted Translation-en_AU 
Ign [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) hardy-updates/universe Translation-en_AU 
Ign [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) hardy-updates/multiverse Translation-en_AU 
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) hardy Release  
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) hardy-updates Release               
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security Release.gpg            
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/main Translation-en_AU 
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) hardy/main Packages 
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/restricted Translation-en_AU 
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/universe Translation-en_AU 
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/multiverse Translation-en_AU 
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) hardy/restricted Packages 
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) hardy/main Sources 
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) hardy/restricted Sources 
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) hardy/universe Packages 
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) hardy/universe Sources 
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) hardy/multiverse Packages 
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) hardy/multiverse Sources 
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) hardy-updates/main Packages 
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) hardy-updates/restricted Packages 
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) hardy-updates/main Sources 
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) hardy-updates/restricted Sources 
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security Release 
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) hardy-updates/universe Packages 
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) hardy-updates/universe Sources 
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) hardy-updates/multiverse Packages 
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) hardy-updates/multiverse Sources 
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/main Packages 
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/restricted Packages 
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/main Sources 
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/restricted Sources 
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/universe Packages 
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/universe Sources 
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/multiverse Packages 
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/multiverse Sources 
Reading package lists... Done 

brian@brian-desktop:~$ sudo apt-get install -f 
Reading package lists... Done 
Building dependency tree        
Reading state information... Done 
0 upgraded, 0 newly installed, 0 to remove and 59 not upgraded. 
brian@brian-desktop:~$  


brian@brian-desktop:~$dpkg -C
brian@brian-desktop:~$

Cant get this to do anything, I have tried prefixing with sudo but it just asks for my password then the same result.

When I installed 8.04 last week I downloaded over 100Mb of updates and now it appears there is another 100Mb of updates, would these be the same? if so should I download them? Thanks BrianP

---

### Post by BrianP42 on 2008-06-13
Hi PmDematagoda, please let me know if this problem of mine is now abandoned . This will allow me to persue it elsewhere, thanks BrianP

---

### Post by PmDematagoda on 2008-06-13
Did you try installing the unichrome driver package again with:-
```
sudo apt-get install xserver-xorg-video-unichrome
```
?

---

### Post by BrianP42 on 2008-06-13
Result of trying to install unichrome driver package with suggested code

brian@brian-desktop:~$ sudo apt-get install xserver-xorg-video-unichrome

Reading package lists... Done

Building dependency tree       

Reading state information... Done

Some packages could not be installed. This may mean that you have

requested an impossible situation or if you are using the unstable

distribution that some required packages have not yet been created

or been moved out of Incoming.



Since you only requested a single operation it is extremely likely that

the package is simply not installable and a bug report against

that package should be filed.

The following information may help to resolve the situation:



The following packages have unmet dependencies:

  xserver-xorg-video-unichrome: Depends: xserver-xorg-core (>= 1:1.1.1) but it is not going to be installed

E: Broken packages

brian@brian-desktop:~$

---

### Post by PmDematagoda on 2008-06-14
Post the output of:-
```
sudo apt-get install -f
```

---

### Post by BrianP42 on 2008-06-14
brian@brian-desktop:~$ sudo apt-get install -f
Reading package list... Done
Building dependency tree
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded
brian@brian:~$
PS I have downloaded and installed all the current updates.

---

### Post by PmDematagoda on 2008-06-15
Then try installing the VIA driver with:-
```
sudo apt-get install xserver-xorg-video-via
```
and do:-
```
sudo dpkg-reconfigure xserver-xorg
```
and choose the driver as via and any other options you may want. After that is done, start the X-Server with:-
```
sudo /etc/init.d/gdm start
```
and see if it now works.

---

### Post by BrianP42 on 2008-06-15
brian@brian-desktop:~$ sudo apt-get install xserver-xorg-video-via
[sudo] password for brian:
Reading package lists... Done
Building dependency tree
Reading state information... Done
xserver-xorg-video-via is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
brian@briandesktop:~$ sudo dpkg-reconfigure xserver-xorg
xserver-xorg postinst warning: overwriting possiblycustomised
configuration file; backup in /etc/X11/xorg.conf.20080615153347
brian@briandesktop:~$
sudo /etc/init.d/gdm start
* Starting GNOME Display Manager... [ OK ]
brian@briandesktop:~$

---

### Post by BrianP42 on 2008-06-15
I entered inputs as advised and got the above results but no change in display. I did it all over again and rebooted a couple of times but no progress. Thyanks BrianP

---

### Post by PmDematagoda on 2008-06-15
Try:-
```
startx
```

---

### Post by BrianP42 on 2008-06-15
brian@brian-desktop:~$ startx
X: user not authorized to run the X server, aborting.
xinit: Server error.
Couldnt get a file descriptor referring to the console
brian@briandesktop:~$

---

### Post by PmDematagoda on 2008-06-15
Do:-
```
sudo startx
```
I thought the normal user was allowed to start the X-Server(I had done that), but I guess that was wrong, sorry.

---

### Post by BrianP42 on 2008-06-15
brian@brian:~$ sudo startx
[sudo] password for brian

X: warning; process set for priority -1 instead of requested priority 0  

Fatal server error:
Server is already actice for display 0 If this server is no longer running remove /tmp/.X0-lock
and start again.
briaa@brian-desktop:~$

---

### Post by PmDematagoda on 2008-06-15
Do:-
```
sudo /etc/init.d/gdm stop && sudo killall Xorg
```
after that is done, try starting the X-Server again.

---

### Post by BrianP42 on 2008-06-16
Back to square one. I did a copy and paste of the command to Applications/Terminal/brian@brian-desktop:~$
and I got the black screen with text ending with the line
"Running local boot scripts(etc/rc.local) (OK)
Then it just hung there 10 mins until I did a reboot.
You said "after that is done try starting X-server again" but I'm not sure how to do that so if I have to do that later please let me know what the code is. Thanks BrianP

---

### Post by PmDematagoda on 2008-06-16
The command was given previously, it's:-
```
sudo startx
```

---

### Post by BrianP42 on 2008-06-16
When I enter "sudo /etc/init.d/gdm stop && sudo killall Xorg" as you requested I get a black screen with 5 lines of text the last one being"Running local boot scripts(etc/rc.local)  (OK) which stops dead there. The next line is a rapid cursor and if I enter "sudo startx" there nothing happens so do I reboot and press ESC to select some other place to enter sudo startx?

---

### Post by BrianP42 on 2008-06-18
Hi Abantu, no I didnt get it going but I did get to open but in "Low Graphics Mode" using the codes below as provided by Pmdematagoda but if you follow to the last page it looks like he has abandoned me.I will have to start another forum entry and hope someone picks it up that can help me. Everything works OK in Low Graphichs but I cant get the email to work because the page is too big and the Forward button is off the page so I cannot click on it. [COLOR="Red"] Also, when you reach that error message, switch to a tty with Ctrl+Alt+F1 and then execute:-

Code:
sudo xfixAfter that is done, do:-

Code:
sudo /etc/init.d/gdm restartAnd see if that fixes the problem.[/COLOR]
The above got me going after I had entered these commands I got it to open OK but like I said in Low Graphics mode. I think my problem is the S3 Unichrome Pro Video software isnt installed.Sorry I cant help you, Regards BrianP.

---

### Post by PmDematagoda on 2008-06-19
The problem is that you can't seem to install the UniChrome driver BrianP42.

There is a driver called OpenChrome, perhaps you can use that, you refer to it's usage and how to install it [here]("https://help.ubuntu.com/community/OpenChrome").

---

### Post by BrianP42 on 2008-06-21
Dear anxious readers, I found an 7 year old TNT2 video card I kept when I updated this computer so I bunged it into the MSI M/board with the onboard S3 Unichrome video which wouldn't work and what do you know, what can only be described as a miracle occured.I now have the correct resolution and you would think I had won the lottery.
I currently disconnect either HDD power cable to alternate between Windows and Ubuntu to boot up and I suspect there is a way to achieve this with the sides of the computer fully assembled.This is my next exciting project.Thanks for all assistance.
BrianP

---

