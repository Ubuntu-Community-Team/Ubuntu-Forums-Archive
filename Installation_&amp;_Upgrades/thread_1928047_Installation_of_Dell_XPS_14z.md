---
title: "Installation of Dell XPS 14z"
date: 2012-02-19
forum: Installation &amp; Upgrades
---

### Post by Kalyan-sg on 2012-02-19
After one year on Ubuntu using an old laptop, I finally have enough courage to place an order for Dell XPS 14z with the following specs:
 
[LIST]
[*]2nd generation Intel® CoreTM     i7-2640M processor (2.80 GHz with Turbo Boost 2.0 
up to 3.50     GHz)
[*]8GB 1333MHz DDR3 SDRAM (2 x 4GB)
[*]750GB 7200RPM Hard Drive
[*]NVIDIA® GeForce® GT 520M 1GB     graphics
[*]9.5mm SATA Slot Load DVD+/-RW
[*]Intel® Centrino® Advanced-N 6230 with Bluetooth v3.0+HS
[/LIST]
 I shall get the notebook at the end of the month from Dell & I want to install Ubuntu 11.10 as soon as it arrives! If someone has already done the installation, kindly let me know the steps that I should follow.
 I shall of course post detailed steps as I go through the installation. Looking forward to this eagerly!!
  Kalyan

---

### Post by Kalyan-sg on 2012-02-29
Sorry Folks,
Dell Singapore has changed their delivery date from 1st March to 12th March...they must be short of components...I am so disappointed!!

---

### Post by Kalyan-sg on 2012-03-06
Got the XPS 14z. Using Ubuntu 11.10 to post this reply. Everything is working. Wifi is fine as well!! Have not loaded any Nvidia driver as yet. Will probably try today!...great experience so far!!

---

### Post by Kalyan-sg on 2012-03-06
[SIZE=2]**I have used a 32-bit version of Ubuntu 11.10**
So far,
1 - wifi ...OK
2 - DVD drive ...OK
3 - Using a Targus wireless mouse supplied by Dell ...OK
4 - Sound ...OK
5 - Touchpad ...OK

**So far I have not used any additional drivers.  NVIDIA has released a driver for this card on Februry 13th. Is that the one to use or should I use Bumblebee? Not Sure!!**

The laptop is not heating up, The HDD 750GB  is almost noiseless. Nothing negative to report.[/SIZE]

---

### Post by Kalyan-sg on 2012-03-08
I tried to use the new NVIDIA driver from NVIDIA site and followed their instructions. The computer crashed and ended up with a blank screen. I could recover but every time I tried to start the computer I had to go through the recovery mode!!

So, I reinstalled the Ubuntu 11.10 again, but this time I used 64-bit version. Everything worked but the NVIDIA card. But without that I am still OK using the intel graphics, which is also very good. So, do not install the NVIDIA graphic card, unless you have sufficient knowledge.

I might try the Bumblebee option next week. But for now the computer is working just fine and I am very happy that I got this and the UBUNTU OS works so well compared to my old HP laptop!!

All my office colleagues say it looks like and behaves like [I]MacBook Pro.

**I think it is better than that!!**
[/I]

---

### Post by yosephcs on 2012-03-19
HI there, I have followed your posts and found them to be helpful. But I have one question (If you have encountered the same. I installed Ubuntu on Dell XPS 14z core i5 after removing Windows 7. The problem is that the primary memory I have physically is 8GB and Ubuntu found only 3GB. Can you think of any solution for this. Thank you in advance.

---

### Post by ubuntukid on 2012-03-20
> **yosephcs said:**
> HI there, I have followed your posts and found them to be helpful. But I have one question (If you have encountered the same. I installed Ubuntu on Dell XPS 14z core i5 after removing Windows 7. The problem is that the primary memory I have physically is 8GB and Ubuntu found only 3GB. Can you think of any solution for this. Thank you in advance.

I'm guessing you downloaded the 32-bit ubuntu iso. 32-bit systems can't use more than that amount of ram. You need to download and install the 64-bit version of Ubuntu. That should solv your problem.

---

### Post by dbowlin17 on 2012-03-25
hey, do you have a status report? are things still going smoothly? what do you think of the computer? also, what is your battery life like, and have you tried other things out like SD card reader or webcams?

Thanks

---

### Post by jbcfarina on 2012-03-28
I am thinking about buying it, could you test if an external monitor works?

---

### Post by Kalyan-sg on 2012-04-01
> **yosephcs said:**
> HI there, I have followed your posts and found them to be helpful. But I have one question (If you have encountered the same. I installed Ubuntu on Dell XPS 14z core i5 after removing Windows 7. The problem is that the primary memory I have physically is 8GB and Ubuntu found only 3GB. Can you think of any solution for this. Thank you in advance.

Maybe you should try 12.04 beta 2. I just checked the memory to be 7.7GB.

I am on 12.04 beta 2, which I loaded on my XPS 14z at 12 midnight yesterday. So far so good!

Generally quite happy! 

Good Luck

Kalyan

---

### Post by Kalyan-sg on 2012-04-01
> **dbowlin17 said:**
> hey, do you have a status report? are things still going smoothly? what do you think of the computer? also, what is your battery life like, and have you tried other things out like SD card reader or webcams?

Thanks

The computer is really fantastic  and as I write I am on 12.04 beta. Webcam was absolutely ok on 11.04. Not sure if ok on 12.04 beta 2. Will let you know by today. I did not try the SD. Still not using Bumblebee...maybe by next week! Not on battery as well so cannot report that. SD card also have to try.

But one thing, DO NOT UPGRADE to 12.04 beta 2 it completely screwed up the computer. I could not even restart. I was also not careful to save all my files. So I lost them. So, later I did a complete fresh install of 12.04 beta 2 with USB and it worked like a charm!!

I have installed Skype 2.2 it is working and the now I see that the webcam is ok!

Best of luck
Kalyan

---

### Post by Kalyan-sg on 2012-04-01
> **ubuntukid said:**
> I'm guessing you downloaded the 32-bit ubuntu iso. 32-bit systems can't use more than that amount of ram. You need to download and install the 64-bit version of Ubuntu. That should solv your problem.

I was using 64-bit system for both 11.10 and now for 12.04 beta 2. I recommend 64-bit system. Working fine so far!!
Kalyan

---

### Post by Kalyan-sg on 2012-04-01
> **jbcfarina said:**
> I am thinking about buying it, could you test if an external monitor works?

This XPS 14z only has HDMI connection, so I have ordered a VGA converter from HDMI from e-bay costing US$ 1.99...it has not arrived...I want to try out on a projector and then report the same!

Kalyan

---

### Post by Kalyan-sg on 2012-04-02
> **jbcfarina said:**
> I am thinking about buying it, could you test if an external monitor works?

Dell XPS 14z does not have a VGA port only a HDMI port. I wanted to try out with a projector! So, I am getting a HDMI --> VGA converter from ebay...not yet arrived. Once it is there I can try out the projector output!

At the moment I am on 12.04 beta 2. It is working great on XPS 14z!!

Kalyan

---

### Post by Kalyan-sg on 2012-04-02
> **Kalyan-sg said:**
> Got the XPS 14z. Using Ubuntu 11.10 to post this reply. Everything is working. Wifi is fine as well!! Have not loaded any Nvidia driver as yet. Will probably try today!...great experience so far!!
Reading all the posts in the net, it may be better to wait for Bumblebee to have a stable version for 12.04. Maybe by end-April...just hopeful!! At the moment it is probably wiser to stick to Intel graphics!

---

### Post by Kalyan-sg on 2012-04-02
Changes in Desktop after installing Ubuntu 12.04 (Beta 2) 
[LIST]
[*]Put the Terminal in the Launcher     Panel on  Desktop. This can be easily done. Start Terminal from Dash     (typing  Terminal) and the Terminal icon will appear at the Desktop     panel.  Right click the icon and choose 'Lock to Launcher'. This can     be  followed for all the launcher icons that you are using more      frequently and you want to keep on the Desktop. You can start the      other from the Dash anyway.
[*]Install Synaptic Package Manager      from the Ubuntu Software Centre. I use this many time when I am      installing new software, where there could be packages to install      and some packages to remove. This is done very neatly in Synaptic.      But I operate this from Dash.
[*]Install LibreOffice from  Synaptic,     choosing the options that you want Precise Pangolin does  not install     the whole office. I install the whole office! In XPS  14z, I have a     750GB hard disk, so no worries.
[*]Now I remove  all theses icons from     Desktop Panel &#8211; Writer, Impress & Calc and  put the LibreOffice     icon. This way I have just one icon of  LibreOffice and not three.     This allows me to choose the program that  I want (e.g. the Drawing     or the Formula package, which I use quite  often),.
[*]Now I need to install the super     graphic packages  Inkscape and Gimp from Synaptic while carefully     choosing the options  that I want. I keep Inkscape icon on the     Desktop Panel and I use  Gimp from the Dash.
[*]I use the Tomboy Notes very     frequently so I install it from the Software Centre and put the icon     at the Desktop.
[*]I  install MyUnity from the     Software Centre but do not keep on  Desktop. I mainly use this to     resize the icons on the Desktop.
[*]I  installed Pidgin Internet     Messenger (was using Empathy with 11.10  but had some problem with     choosing my Google Talk account, so I went  back to Pidgin, which is     working fine!).
[*]The I used VLC player using this     site     [http://news.softpedia.com/news/How-to-Install-VLC-2-0-on-Ubuntu-11-10-253805.shtml](http://news.softpedia.com/news/How-to-Install-VLC-2-0-on-Ubuntu-11-10-253805.shtml)     ...worked fine and I kept the icon on the Desktop
[*]Then  I installed CmapTools, which     is a concept mapping software, which I  use very frequently. It is     bin file. But very easy to install. The  instruction to install a bin     file is given here:     [http://www.ehow.com/how_4578189_install-bin-file-ubuntu-linux.html](http://www.ehow.com/how_4578189_install-bin-file-ubuntu-linux.html)      But I cannot keep the launcher on the Desktop Panel (I wish this      could solved!). So, I keep the CmapTools Launcher in my Home      directory.
[*]I also use QtOctave & Octave     but I do not keep them on the Desktop.
[*]I installed Skype 2.2 Beta. I do     not keep it on the Desktop.
[*]I also installed Cheese from the     Web-cam and keep this on the Desktop.
[*]Installed Scribus from Synaptic with its help files for publication work. I access this from Dash & not from the Desktop.
[*]So,  finally my Desktop Launcher     Panel is like this from top: Dash, Home  Folder, Firefox Web Browser,     Ubuntu Software Centre, Ubuntu One (I  use use everyday for     back-up...5Gb is free), System Settings,  LibreOffice, Inkscape VG     Editor, Tomboy Notes, Cheese Webcam Booth,  VLC Media Player, Pidgin     Internet Messenger, Workspace Switcher  & finally Trash.
[/LIST]

---

### Post by rodpott on 2012-04-03
Hi everybody. I have installed 12.04 Beta1 on dell XPS 14z as well. I also installed the bumblebee- package which will massive enhance the battery performance from about 1:20 to 3:30 hours because the nvidia-chip is disabled by default and not using power.

My recommandation is to change the following setting if you want have more wireless speed:
sudo nano /usr/lib/pm-utils/power.d/wireless

search for:
        iwl*) if [ -f "/sys/class/net/$1/device/power_level" ]; then
                 iwlevel_ac=0
                 iwlevel_batt=3

and change it to:
        iwl*) if [ -f "/sys/class/net/$1/device/power_level" ]; then
                 iwlevel_ac=0
                 **iwlevel_batt=0**

After that you will have much more wireless speed in the battery mode.

---

### Post by Kalyan-sg on 2012-04-03
Thanks for the info. Why did you install Beta 1 as the Beta 2 for 12.04 is already available? Can you give us steps for successful Bumblebee installation in 12.04?
Thanks in advance!

> **rodpott said:**
> Hi everybody. I have installed 12.04 Beta1 on dell XPS 14z as well. I also installed the bumblebee- package which will massive enhance the battery performance from about 1:20 to 3:30 hours because the nvidia-chip is disabled by default and not using power.

My recommandation is to change the following setting if you want have more wireless speed:
sudo nano /usr/lib/pm-utils/power.d/wireless

search for:
        iwl*) if [ -f "/sys/class/net/$1/device/power_level" ]; then
                 iwlevel_ac=0
                 iwlevel_batt=3

and change it to:
        iwl*) if [ -f "/sys/class/net/$1/device/power_level" ]; then
                 iwlevel_ac=0
                 **iwlevel_batt=0**

After that you will have much more wireless speed in the battery mode.

---

### Post by rodpott on 2012-04-04
Hi again,

now I made an update to Beta2. Here are the easy steps to install bumblebee:
```
[LEFT][FONT=Arial][SIZE=1][COLOR=Black]sudo apt-add-repository ppa:bumblebee/stable[/COLOR][/SIZE][/FONT][/LEFT]
[COLOR=#3C3C3C][FONT=sans-serif][LEFT][FONT=Arial][SIZE=1][COLOR=Black]sudo apt-get update[/COLOR][/SIZE][/FONT][/FONT][/COLOR][/LEFT]
[COLOR=#3C3C3C][FONT=sans-serif][LEFT][FONT=Arial][SIZE=1][COLOR=Black]sudo apt-get install bumblebee bumblebee-nvidia[/COLOR][/SIZE][/FONT][SIZE=1][COLOR=Black]
[/COLOR][/SIZE][/FONT][/COLOR][/LEFT]
[COLOR=#3C3C3C][FONT=sans-serif][LEFT][SIZE=1][COLOR=Black]sudo usermod -a -G bumblebee USERNAME [/COLOR][/SIZE][/FONT][/COLOR][/LEFT]

```

/rod

---

### Post by rodpott on 2012-04-04
I also had the following problem: [FONT=Arial][SIZE=1][COLOR=Black][COLOR=#3C3C3C][FONT=sans-serif]"Computer hibernates when unplugged from powersource[/FONT][/COLOR][/COLOR][/SIZE][/FONT][B][FONT=Arial][SIZE=1][COLOR=Black]"

Here are the steps to handle this for the XPS 14z:
[/COLOR][/SIZE][/FONT][/B]
1. sudo apt-get install dconf-tools
2. dconf-editor
3. Navigate to the 'org.gnome.settings-daemon.plugins.power' section
4. Uncheck 'use-time-for-policy'

---

### Post by rodpott on 2012-04-04
Here are the Dell guides to change Hardware components of the Dell XPS 14z:

In my case i have changed the harddisk drive to a intel ssd.

[http://support.euro.dell.com/support/edocs/systems/xpsl412z/en/om/index.htm](http://support.euro.dell.com/support/edocs/systems/xpsl412z/en/om/index.htm)

---

### Post by ptosiani on 2012-04-04
Hello!

I just got my XPS 14z yesterday. 

I have a 256Gb SSD and the nVidia GeForce GT 520M.

I'm trying to adapt my self to 'unity' although having only access to unity-2D makes it very difficult. 

Anyone succeeded in installing the nvidia drivers? I've always being able to install drivers using the 'additional drivers' tool, but this time, even if I add all the sources, I can't. 

I also want to recommend this post to get back some of those good old indicators (the last ubuntu version I used was 10.04 LTS):

[http://www.techdrivein.com/2011/05/10-useful-application-indicators-for.html]("http://www.techdrivein.com/2011/05/10-useful-application-indicators-for.html")

---

### Post by rodpott on 2012-04-04
Please see my post, how to installing the bumblebee driver package instead of the nvidia driver.


> **ptosiani said:**
> Hello!

I just got my XPS 14z yesterday. 

I have a 256Gb SSD and the nVidia GeForce GT 520M.

I'm trying to adapt my self to 'unity' although having only access to unity-2D makes it very difficult. 

Anyone succeeded in installing the nvidia drivers? I've always being able to install drivers using the 'additional drivers' tool, but this time, even if I add all the sources, I can't. 

I also want to recommend this post to get back some of those good old indicators (the last ubuntu version I used was 10.04 LTS):

[http://www.techdrivein.com/2011/05/10-useful-application-indicators-for.html](http://www.techdrivein.com/2011/05/10-useful-application-indicators-for.html)

---

### Post by Kalyan-sg on 2012-04-05
> **rodpott said:**
> Hi again,

now I made an update to Beta2. Here are the easy steps to install bumblebee:
```
[LEFT][FONT=Arial][SIZE=1][COLOR=Black]sudo apt-add-repository ppa:bumblebee/stable[/COLOR][/SIZE][/FONT][/LEFT]
[COLOR=#3C3C3C][FONT=sans-serif][LEFT][FONT=Arial][SIZE=1][COLOR=Black]sudo apt-get update[/COLOR][/SIZE][/FONT][/LEFT]
[/FONT][/COLOR][COLOR=#3C3C3C][FONT=sans-serif][LEFT][FONT=Arial][SIZE=1][COLOR=Black]sudo apt-get install bumblebee bumblebee-nvidia[/COLOR][/SIZE][/FONT][SIZE=1][COLOR=Black]
[/COLOR][/SIZE][/LEFT]
[/FONT][/COLOR][COLOR=#3C3C3C][FONT=sans-serif][LEFT][SIZE=1][COLOR=Black]sudo usermod -a -G bumblebee USERNAME [/COLOR][/SIZE][/LEFT]
[/FONT][/COLOR]
```/rod

Hi rodpott
I have a silly question to ask (not so tech savvy like you!). 

Kindly confirm that USERNAME should be replaced with my username for the XPS 14z Linux computer...right??


OK I have already installed Bumblebee. Thanks to rodfott for help! 

You can type in Terminal 
optirun glxspheres

to check if the installation is successful! Mine is!!

Get the details from 
[http://www.ivegotavirus.com/blog/2012/01/23/installing-bumblebee-3-0-tumbleweed-on-ubuntu/](http://www.ivegotavirus.com/blog/2012/01/23/installing-bumblebee-3-0-tumbleweed-on-ubuntu/)

Good Luck!

---

### Post by rodpott on 2012-04-05
you are right. "username" should be replaced with your username you use for the login.

> **Kalyan-sg said:**
> Hi rodpott
I have a silly question to ask (not so tech savvy like you!). 

Kindly confirm that USERNAME should be replaced with my username for the XPS 14z Linux computer...right??


OK I have already installed Bumblebee. Thanks to rodfott for help! 

You can type in Terminal 
optirun glxspheres

to check if the installation is successful! Mine is!!

Get the details from 
[http://www.ivegotavirus.com/blog/2012/01/23/installing-bumblebee-3-0-tumbleweed-on-ubuntu/](http://www.ivegotavirus.com/blog/2012/01/23/installing-bumblebee-3-0-tumbleweed-on-ubuntu/)

Good Luck!

---

### Post by rodpott on 2012-04-05
If you run into this problem when you try to start an application using the optirun command:

[ERROR]Cannot access secondary GPU - error: XORG NVIDIA(0): No display devices found for this X screen.

You can solve this by doing the following:
If you are using the nvidia-current driver:
```
echo 'Section "ServerLayout" Identifier "Layout0" Option "AutoAddDevices" "true" EndSection  Section "Device" Identifier "Device1" Driver "nvidia" VendorName "NVIDIA Corporation" Option "NoLogo" "true" Option "UseEDID" "true" Option "ConnectedMonitor" "DFP" EndSection' | sudo tee /usr/share/X11/xorg.conf.d/10-nvidia-current-latitude-e6530.conf
```

If you're using the nvidia-current-updates driver:
```

echo 'Section "ServerLayout" Identifier "Layout0" Option "AutoAddDevices" "true" EndSection  Section "Device" Identifier "Device1" Driver "nvidia" VendorName "NVIDIA Corporation" Option "NoLogo" "true" Option "UseEDID" "true" Option "ConnectedMonitor" "DFP" EndSection' | sudo tee /usr/share/X11/xorg.conf.d/10-nvidia-current-updates-latitude-e6530.conf
```

---

### Post by ptosiani on 2012-04-07
Yep, I follow those instructions and worked very well, I now have the whole Unity 3D experience, Thank you! 

> **rodpott said:**
> Please see my post, how to installing the bumblebee driver package instead of the nvidia driver.

---

### Post by ptosiani on 2012-04-07
How are you guys managing the Bright/Contrast of the screen? 

I found that the screen is very bright and it's very uncomfortable to work with. 

I have to work with the display with 25% Brightness. (xbacklight -set  25) 

Is there any other tool or way to change the back-light or the contrast of the screen?

---

### Post by rodpott on 2012-04-08
> **ptosiani said:**
> How are you guys managing the Bright/Contrast of the screen? 

I found that the screen is very bright and it's very uncomfortable to work with. 

I have to work with the display with 25% Brightness. (xbacklight -set  25) 

Is there any other tool or way to change the back-light or the contrast of the screen?

Hi, i haven't got that problem. My screen has a nice brightness and is not to bright. Maybe it has something to do with an earlier setting in windows. I have heared about problems, on some older notebooks some settings can only modify with the windows-driver.

---

### Post by Kalyan-sg on 2012-04-17
> **ptosiani said:**
> How are you guys managing the Bright/Contrast of the screen? 

I found that the screen is very bright and it's very uncomfortable to work with. 

I have to work with the display with 25% Brightness. (xbacklight -set  25) 

Is there any other tool or way to change the back-light or the contrast of the screen?

Hi

After installing Bumblebee, you are able to run nvidia-settings using:
optirun nvidia-settings -c :8
Then you can change the various settings.

Bumblebee stopped working several times after upgrades (you are getting many updates these days for 12.04 Beta 2).

So, needed to reinstall.

After reinstall it works again!

Good Luck

Kalyan

---

### Post by ptosiani on 2012-04-20
Great, TY for that tip.

I also had to install back that cpu-freq indicator:

[http://www.noobslab.com/2011/07/cpu-frequency-scaling-indicator-on.html](http://www.noobslab.com/2011/07/cpu-frequency-scaling-indicator-on.html)

Because the fan coolers were running at full speed all time, only with chrome and netbeans running...

I have my CPU at 1GHz now, 

I also installed [http://www.lm-sensors.org/](http://www.lm-sensors.org/) and it looks like CPU temp is around 47ºC.

---

### Post by abdelazizk on 2012-04-20
Hi all,

I have always been using ubuntu in all my last laptops. I just bought Dell XPS 14z with i5 processor but no NVIDIA card, just the intel HD 3000 Graphics. I'm waiting for 26 April to download the final release of LTS 12.04. 
I'm using windows 7 now and battery can keep up to 4 hours and 30 minutes. what about with 12.04? do you get same battery duration??
are you using compiz?

---

### Post by ptosiani on 2012-04-21
I'm getting 3.5h on a default configuration.

If you play with fan speed / processor frequency and other parameters you can get 4h.

---

### Post by rodpott on 2012-04-21
> **ptosiani said:**
> I'm getting 3.5h on a default configuration.

If you play with fan speed / processor frequency and other parameters you can get 4h.

How is your rate in battery overview? My rate is about 16w if i just browsing the web...

---

### Post by abdelazizk on 2012-04-22
Hi all,

didn't move to ubuntu yet, waiting for 26 April for final 12.04 release. But on windows I can get more than 4 hours easily. 
If 3:30 is battery duration on ubuntu with default conf, then we can easily get to 4:30 if you place logs and applications' cache in RAM, specially google chrome.

---

### Post by rodpott on 2012-04-22
> **abdelazizk said:**
> Hi all,

didn't move to ubuntu yet, waiting for 26 April for final 12.04 release. But on windows I can get more than 4 hours easily. 
If 3:30 is battery duration on ubuntu with default conf, then we can easily get to 4:30 if you place logs and applications' cache in RAM, specially google chrome.

Would be nice if you can give us a step by step guide to configure it.

Rod

---

### Post by abdelazizk on 2012-04-23
first of all backup your /etc/fstab

sudo cp /etc/fstab /etc/fstab-bak

then move tmp and var to ram by using tmpfs, you have to add these lines to /etc/fstab:

none /var/log tmpfs size=10M 0 0
none /tmp tmpfs size=100M 0 0
none /var/tmp tmpfs size=20M 0 0

and then restart.

this will speed up web browsing a lot !!!

you can also change the swapping threshold if you have 8G of RAM.
ubuntu starts swapping by default when RAM is 40% full (which means 60% free). You can change 60% to 20% or 10% by executing this command.

sudo sysctl vm.swappiness=20

then reactivate swap using this command:

sudo swapoff -av
sudo swapon -av

Moving tmp to RAM and using less swap will decrease access to disk which will speed up ubuntu and save lots of energy.
These manips are also relevant for SSD disks.

enjoy !!!

---

### Post by rodpott on 2012-04-24
Anyone has problems with the lan interface? I just get a 100mbit connection. It is not the cable/hardware because same system with windows 7 is ok.

ethtool -s has no effect at all

---

### Post by rodpott on 2012-04-26
After the last update the network is gigabit again.

---

### Post by Kalyan-sg on 2012-05-01
> **jbcfarina said:**
> I am thinking about buying it, could you test if an external monitor works?

Everything works on 12.04 except the external monitor. I just got the HDMI to VGA connector but no luck with the external monitor. Is there an easy solution yet?

---

### Post by abdelazizk on 2012-05-07
Hello,

So I just installed Ubuntu LTS 12.04. It's very fast !!
Problem is fan is always up and loud. 
Is someone having the same problem?

---

### Post by naps22 on 2012-05-09
Hi

I have the same, fan is constantly on.

Like in windows, you can visually see if the cpu is under-clocked using turbo boost monitor.  Is there any equivalent software for ubuntu?

Another question is how 12.04 handles multiple graphic cards.  I have Intel HD and Nvidia GT 520M.  Again in windows there is an option that allows system automatically choose which card to use depending on the stress.  

I have tried to install 'nvidia-current' but no luck, the card was not found.

---

### Post by rodpott on 2012-05-12
> **naps22 said:**
> Hi

I have the same, fan is constantly on.

Like in windows, you can visually see if the cpu is under-clocked using turbo boost monitor.  Is there any equivalent software for ubuntu?

Another question is how 12.04 handles multiple graphic cards.  I have Intel HD and Nvidia GT 520M.  Again in windows there is an option that allows system automatically choose which card to use depending on the stress.  

I have tried to install 'nvidia-current' but no luck, the card was not found.

Hi, please see a few posts above. You need to install the bumblebee driver, otherwise your second video-card is running all the time. This will produce more heat in your system and thats the reason why your fan is running all the time. Please let me know if that help you.

Here again for you:
```
sudo apt-add-repository ppa:bumblebee/stable
sudo apt-get update
sudo apt-get install bumblebee bumblebee-nvidia
sudo usermod -a -G bumblebee USERNAME
```To use the nvidia-card for your apps you need to run the "optirun" command.

---

### Post by rodpott on 2012-05-12
> **Kalyan-sg said:**
> Everything works on 12.04 except the external monitor. I just got the HDMI to VGA connector but no luck with the external monitor. Is there an easy solution yet?

Hi, i have no problems using the HDMI-port of my xps. Do you use another way?

---

### Post by naps22 on 2012-05-15
Hi

I have installed bumblebee successfully, however the fan did not stop.

I have managed to use bbswitch with bumblebee and turn the nvidia card off. 

Currently I only got the "2nd Generation Core Processor Family Integrated Graphics Controller" as my only graphic.

when I do lswh -class display it only shows up one card. It used to show 2 after installing bumblebee.

I think that the only reason why the fan is still running is that the intel card is not in power save mode.  I have powerTop and I checked the graphic card and it never goes below 100%. 

Is there any way to enable intel graphic power save mode ?

Thanks

---

### Post by rodpott on 2012-05-16
> **naps22 said:**
> Hi

I have installed bumblebee successfully, however the fan did not stop.

I have managed to use bbswitch with bumblebee and turn the nvidia card off. 

Currently I only got the "2nd Generation Core Processor Family Integrated Graphics Controller" as my only graphic.

when I do lswh -class display it only shows up one card. It used to show 2 after installing bumblebee.

I think that the only reason why the fan is still running is that the intel card is not in power save mode.  I have powerTop and I checked the graphic card and it never goes below 100%. 

Is there any way to enable intel graphic power save mode ?

Thanks

Same here! I think the problem with the fan is something else. Do you have a SSD? In my XPS is a SSD. Maybe this is reducing the heat and the fan-noise. Is somebody here who has the same problem?

In powertop the intelchip is also on 100%...

Try to use the following to show up both video-devices:

start a program using the optirun switch in terminal.
for example:
```
optirun firefox
```than during firefox is running with optirun switch run the command again:
```
lshw -class display
```What do you see now?

---

### Post by abdelazizk on 2012-05-16
Hi all,

What is the brand of SSD disks installed by default in Dell XPS 14z?

---

### Post by rodpott on 2012-05-18
> **abdelazizk said:**
> Hi all,

What is the brand of SSD disks installed by default in Dell XPS 14z?

I installed it by my own, so i cannot say what the default type is.

---

### Post by Kalyan-sg on 2012-05-30
Now I have a new problem on this XPS 14z running on Ubuntu 12.04. The Scribus 1.4.0 does not run properly. Every time I try to get an image in to Scribus, the program crashes. I  think it has something to do Nvidea Optimus card. So, I tried with Optirun Scribus. But still the same problem. Looks like the bottom line is that if you are going to use Linux avoid Nvidea Optimus card...as there is no solution is sight!! ... sigh! I installed Scribus (32-bit) on a Windows 7 laptop, it is working fine. I am really angry!!

---

### Post by ubu2008 on 2012-05-30
Response to this:

> This XPS 14z only has HDMI connection, so I have ordered a VGA converter from HDMI from e-bay costing US$ 1.99...it has not arrived...I want to try out on a projector and then report the same!

To use external VGA monitor/projector there is another way. There is an adaptor by SIIG from USB to VGA. I have used that on another computer to talk to projector.

---

### Post by jbcfarina on 2012-06-02
I have an adaptaer from mini-display port to vga and I make it work following this:
[URL="http://itviking.net/blog/m11xr3-bumblebee-and-the-dual-screen-setuphttp://"]
http://itviking.net/blog/m11xr3-bumblebee-and-the-dual-screen-setup[/URL]

And here my /etc/bumblebee/xorg.conf.nvida

```

 Section "ServerLayout"
    Identifier "Layout0"
    Screen     "Screen0"
    InputDevice  "Keyboard0" "CoreKeyboard"
    InputDevice  "Mouse0" "CorePointer"
    Option "AutoAddDevices" "false"
 EndSection

Section "Files"
    ModulePath "/usr/lib/nvidia-current/xorg,/usr/lib/xorg/modules"
EndSection

Section "Extensions"
    Option         "Composite" "Enable"
EndSection

Section "Device"
    Identifier "Device1"
    Driver "nvidia"
    VendorName "NVIDIA Corporation"
    Option "NoLogo" "true"
    Option "UseEDID" "true"
    Option "ConnectedMonitor" "DFP-1"
    Option "RenderAccel" "true"
    Option "AllowGLXWithComposite" "true"
EndSection

Section "Module"
    Load           "glx"
EndSection

Section "Monitor"
    Identifier    "Monitor0"
EndSection

Section "InputDevice"
    Identifier      "Keyboard0"
    Driver          "void"
    Option          "CoreKeyboard"
EndSection

Section "InputDevice"
    Identifier      "Mouse0"
    Driver          "void"
    Option          "CorePointer"
EndSection

Section "Screen"
    Identifier "Screen0"
    Monitor "Monitor0"
    Device "Device1"
    Defaultdepth 24
# depending on your monitor, I didnt need the following section
#    SubSection "Display"
#     Depth 24
#    Modes "1920x1080"
#    Modes "1600x1200"
#    EndSubSection
EndSection

```

I hope it helps. 
Using the siig usb to vga solution, you change monitors using the "monitors" default app? are you using bumblebee?

---

### Post by Kalyan-sg on 2012-06-05
> **rodpott said:**
> Hi, i have no problems using the HDMI-port of my xps. Do you use another way?
  What is the version of Bios r u using? Have you upgraded to A05? If you have how did u upgrade the bios?

---

### Post by Dave0r on 2012-08-16
hi, I've been running 12.04 on my 14z now for a while, but its heating up quite a lot and making me resistant to using it for a prolonged amount of time. 

I have installed Bumblebee, but the cores are still running at about 48-50c in idle, compared to my windows 7 partition that is running at 39-41 in idle, watching a youtube video on Ubuntu (firefox & chrome) will shoot the core temps up to the 61-65c range.

Do any of you know what might be happening? I am going to try installing the cpu frequency scaler mentioned earlier in the thread, hoping that lowering it will stop it heating up so much?

---

### Post by samuelcersosimo on 2012-09-05
Hi, Dave0r.
Having the same complains, I started to search for some solutions and, after a few tweaks, managed to cool down my CPU to an acceptable level.

What I did was installing Bumblebee, Jupiter and also going to LessWatts.org and trying some tips (not sure if they made any diference).

But I strongly recomend Bumblebee and Jupiter. Post here if you see the diference just by installing those two.

Don't try the nVIDIA proprietary drivers yet. I hear they're a bad trip.

B.R.

---

### Post by agee on 2012-09-06
hey guys, so i just got a xps14z with an i5 and  the   nvidia 520m and i am having trouble getting the 3d unity to work! 

i have installed bumblee and the optirun command works but unity is always running in the 2d mode! 

also i tried bbswitch  and it just says that the card if off and i cannot turn it on.. 

anyone have any ideas? or where to debug? 
still kinder new to linux but getting there haha.

---

### Post by agee on 2012-09-06
> **agee said:**
> hey guys, so i just got a xps14z with an i5 and  the   nvidia 520m and i am having trouble getting the 3d unity to work! 

i have installed bumblee and the optirun command works but unity is always running in the 2d mode! 

also i tried bbswitch  and it just says that the card if off and i cannot turn it on.. 

anyone have any ideas? or where to debug? 
still kinder new to linux but getting there haha.


nevermind it sorted it self out after a few reboots :)

---

### Post by ptosiani on 2012-09-11
> **abdelazizk said:**
> Hi all,

What is the brand of SSD disks installed by default in Dell XPS 14z?
Use the following command: 

sudo hdparm -I /dev/sda

In my case: 
Model Number:       LITEONIT LCT-256M3S

---

### Post by ptosiani on 2012-09-11
Can anyone please describe the behavior they have when they lock the screen (Ctrl + alt + L). 

I was expecting the screen to turn off, but instead I get a bright black screen. anyone know how to fix this? 

Thank you.

---

### Post by atarisal on 2012-10-02
Hi Dell XPS 14z users,

Have to someone happened that the system hangs during  the loading  of the OS? 
It happens to me very often. Other times, the system hangs after showing the desktop image. The only option is to reboot and try  again. It does not happen when starting in safe mode.
Do you have any idea how to solve or to detect the problem?

Thanks to all!

---

### Post by samuelcersosimo on 2013-03-20
Guys, I've opened a thread in Ubuntu Forums with my check-list to solve most of the issues when running Ubuntu 12.04 LTS on our Dell XPS 14z (L412z). Solved temperature, nVIDIA, battery, touchpad sensibility for example.

See if those tips work for you:
[http://ubuntuforums.org/showthread.php?t=2127448](http://ubuntuforums.org/showthread.php?t=2127448)

---

