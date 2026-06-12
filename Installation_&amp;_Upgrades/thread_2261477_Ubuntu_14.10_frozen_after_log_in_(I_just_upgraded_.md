---
title: "Ubuntu 14.10 frozen after log in (I just upgraded from 14.04)"
date: 2015-01-19
forum: Installation &amp; Upgrades
---

### Post by anargyrosp on 2015-01-19
[TABLE]
[TR]
[TD="class: votecell"] 

              [/TD]
              [TD="class: postcell"]                Dear community, 

I have an issue that I realize that many people face, but unfortunately I have not found yet a proper answer.

  
My **Dell Inspiron N5010,  Intel (R) Core(TM) i5 CPU M  460 @ 2.53GHz 2.53 GHZ &#8214; RAM 3,00 GB &#8214; 4 AMD Radeon Graphics Processor  (0x68E0)** with dual boot the last 4 years (1 windows 7 and 1 Ubuntu) was last night upgraded from 14.04 to 14.10.
After the restart (last  step of upgrading) my computer freezes after logging in. Mouse is working, keyboard is working, obviously the graphics are lower  than usual, and I can't connect to wifi (I try to connect before loging  in)

  Can anyone support me?

Thanks in advance

      

[/TD]
[/TR]
[/TABLE]

---

### Post by zach25 on 2015-01-19
The exact same thing happened to me a while back. I tried everything, but the only thing that worked for **me**, was reinstall 14.04... For some reason 14.10 did not agree with my set up, and also it seems, others as well.

---

### Post by anargyrosp on 2015-01-20
> **zach25 said:**
> The exact same thing happened to me a while back. I tried everything, but the only thing that worked for **me**, was reinstall 14.04... For some reason 14.10 did not agree with my set up, and also it seems, others as well.

Hi Zach!

I am sorry to hear that.
I kind of managed to go a bit further but still I am stuck.

I did this ```
sudo apt-get remove fglrx-*
``` which improved my resolution and now after log in I can finally see my desktop with the 3 files I had on it but no launchpad or dash.

I have a feeling that there is an issue with the windowsmanager, because the only time I managed to see error report I noticed something about xorg.
And, always, when I try something it tells me that some lib wine-compholio was installed but not needed anymore.

I hope that someone of the guru inside here has a good solution. It will be a nightmare to save 300 GB for doing a clean installation.

---

### Post by jhay2 on 2015-01-20
hi i fixed my problem with that by replacing lightdm-gtk with lightdm-webkit 


try it , it might work with you

---

### Post by anargyrosp on 2015-01-20
Thanks for the positive energy jhay2!!

Can you please tell me how to do this replacing you suggest?

Thank you again

---

### Post by jhay2 on 2015-01-20
just install sudo apt-get install lightdm-webkit-greeter :)  

then , search google for lightdm web themes the download the themes 

do this on terminal via ctrl+alt+F1 if you cant log on to your desktop  

then extract your lightdm-webkit themes to this folder /usr/share/lightdm-webkit/themes

maybe download the themes on other device then extract and just copy the extracted folder on your usb and connect to your ubuntu , then move the folder to your /use/share/lightdm-webkit/themes

check what folder your usb mounted using df command 

then copy the extracted folder to lightdm-webkit/themes

sudo cp /media/your user/your drive/extractedfolder /usr/share/lightdm-webkit/themes/extractedfolder

then , go to /etc/lightdm

sudo gedit ./lightdm-webkit-greeter.conf 

setup according to your prepared themes 

example 


#
# background = Background file to use, either an image path or a color (e.g. #772953)
# theme-name = GTK+ theme to use
# font-name = Font to use
# xft-antialias = Whether to antialias Xft fonts (true or false)
# xft-dpi = Resolution for Xft in dots per inch (e.g. 96)
# xft-hintstyle = What degree of hinting to use (hintnone, hintslight, hintmedium, or hintfull)
# xft-rgba = Type of subpixel antialiasing (none, rgb, bgr, vrgb or vbgr)
#
[greeter]
background=/usr/share/backgrounds/warty-final-ubuntu.png
theme-name=Ambiance
webkit-theme=mac-pretty
font-name=Ubuntu 11
xft-antialias=true
xft-dpi=96
xft-hintstyle=slight
xft-rgba=rgb




then save 

then make lightdm-webkit-greeter active by editing /usr/share/xgreeters/lightdm-gtk-greeter.desktop

like this 

[Desktop Entry]
Name=LightDM GTK+ Greeter
Comment=This runs the GTK+ greeter, it should only be run from LightDM
Exec=lightdm-webkit-greeter
Type=Application
X-Ubuntu-Gettext-Domain=lightdm


then reboot your system :)

goodluck

---

### Post by anargyrosp on 2015-01-20
How am I supposed to search themes on google and download them if I can't use my computer. 
Is there a command for doing this?

I understand this command ```
sudo apt-get install lightdm-webkit-greeter
``` but what next?
I know you probably have better things to do, but if you have some time be more descriptive.
How do I extract.

As I say in previous message, my computer shows no windows, no launchpad, no dash.

Thank you again for the attention and help

---

### Post by anargyrosp on 2015-01-21
The problem is solved thanks to the help from the Greek forum adslgr.com. In case some one of you can read Greek, the thread is [here]("http://www.adslgr.com/forum/threads/844403-%CE%A4%CE%BF-thread-%CF%84%CE%BF%CF%85-Ubuntu-14-10-Utopic-Unicorn/page3").
So, what we did to save my ubuntu 14.10 utopic unicorn from clean install?

**1. Install a desktop environment to work in it** (before I couldn't work, the only way to go to terminal was ctrl+alt+F6, and then I had to reboot because there was no way back to the desktop)

```
sudo apt-get install lxde
sudo service lightdm restart
```

and yes I had a desktop again. Very different from Unity, not so beautiful and delicate, but obviously functional.

[B]2. Repair any unbroken packages:

[/B]```
sudo apt-get update
sudo apt-get dist-upgrade
sudo apt-get clean
sudo apt-get autoclean
sudo apt-get autoremove
```

[B]3. Clean user's settings:

[/B]```
sudo apt-get install debsums
sudo apt-get clean
sudo debsums_init
sudo debsums -cs
```

When I was doing the sudo debsums -cs I realized that it was not actually moving on, so I kind of skipped it :)

[B]4. Reset default settings:

[/B]```
rm  .Xauthority
rm -r ~/.compiz
rm -r ~/.cache/compizconfig-1
dconf reset -f /org/compiz/
setsid unity
```

I wish that it helps the people who have similar problem :)
Credits to adslgr team and especially to sotos4421, but thanks to ubuntuforums.org for giving us ideas.

---

### Post by andreas38 on 2015-03-23
On step 4 i had to do this to work:

```
rm .Xauthority
rm -r ~/.compiz
rm -r ~/.cache/compizconfig-1
**export DISPLAY=:0**
dconf reset -f /org/compiz/
setsid unity
```

---

