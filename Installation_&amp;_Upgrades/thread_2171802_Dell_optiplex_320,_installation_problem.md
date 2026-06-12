---
title: "Dell optiplex 320, installation problem"
date: 2013-09-01
forum: Installation &amp; Upgrades
---

### Post by stevecobb76 on 2013-09-01
I recorded the whole install and crash with my cell phone because I don't know what is going on.
I have heard this computer is a ubuntu killer and there is sata issues so this time I disabled the sata drives in cmos and here is the link to the video on you tube.

[https://www.youtube.com/watch?v=h7Xe5iWRtCg](https://www.youtube.com/watch?v=h7Xe5iWRtCg)

it should not be this hard to install ubuntu.

---

### Post by stevecobb76 on 2013-09-01
specs: 
dell optiplex 320
64 bit
dual core
1.8 ghz cpu
2 pata hd's
4 sata hd's (disabled in cmos) for this video
ati hd5450 video card 

for the love of god, I just want ubuntu to work....
this is about the 20th time I have tried.
each time I try changing something to make it install
1 time I did get it to install but it soon locked up and crashed and would not reboot into linux!!!!
I have tried to install ubuntu 64 and 32, and I have tried to install mint 64 and 32 I have also tried different version of each of these!!!!
that is 4 versions and it is always different errors and install fail every time....

---

### Post by stevecobb76 on 2013-09-01
I can install ubuntu on my netbook
I can even install ubuntu on my rooted android phone
but the machine I really need it on gives me hell!!!!

---

### Post by mörgæs on 2013-09-01
Hi, welcome to the fora.

Yes, the 320 is a well-known problem (unlike most of the Dells, which almost never give me any hassle).

The crash in your film looks like a kernel panic. As a first test, are you able to install the [minimal]("https://help.ubuntu.com/community/Installation/MinimalCD") 13.04?

---

### Post by stevecobb76 on 2013-09-01
I have only used ubuntu and mint.. I prefer ubuntu
I will conduct the test "install minimal 13.04" and then I will let you know what happened with video or pictures.

---

### Post by stevecobb76 on 2013-09-01
as per morgeas, I did the first test. I installed ubuntu 13.04 minimal.
no problems at all until the end of the install when I got a grub 2 install fatal error.
one of the options was to install lilo instead of grub but that didn't seem to work.
os was not found I do have screenshots of error if you want I will post it.

as with my last test, sata hd's were disabled in cmos and also cmos set to boot from pata drives
also I **_DID NOT_** install any optional software!!!

so, where do I go from here...

[SIZE=5][U][B]UBUNTU OR BUST
thank you for all the help!!!
[/B][/U][/SIZE]

---

### Post by stevecobb76 on 2013-09-01
also after skip and continue to pass the grub 2 error after several tries, on reboot I get _**grub rescue **_prompt!

---

### Post by stevecobb76 on 2013-09-02
getting closer.... I tried Kubuntu. installed with only 1 error that whizzed by to fast for me to record it. and I got some trivial errors after running it. I just ran the update and installed firefox... it is not ubuntu like I wanted but I think that I can get used to it. it has a unique user interface/gui... that is for sure.

I will keep working on ubuntu though

---

### Post by sudodus on 2013-09-02
Are you installing to the whole drive, or have you got Windows on the drive and want to keep it? Since you have many HDD drives, I suggest that you try to install Ubuntu or an Ubuntu based flavour (Lubuntu or Xubuntu) or derivative (Mint ...) onto its own HDD using all of it.

For old hardware I would suggest that you try an older version of ***Ubuntu, 12.04 LTS***, and/or why not a lighter version, maybe ***Lubuntu, Xubuntu, LXLE*** or ***Precise Gnome Classic Tweaks***.

You can also avoid the standard installers and try the new** [One Button Installer]("https://wiki.ubuntu.com/phillw/OBI")**, that I am making ready for a wider group of people to use right now.

What graphics chip/card is there in the computer? Maybe that is one of the obstacles, that the built-in graphics drivers do not work. In that case you can use the ***nomodeset*** boot option and (after the installation) try to install a proprietary driver.

---

### Post by sudodus on 2013-09-02
> **stevecobb76 said:**
> getting closer.... I tried Kubuntu. installed with only 1 error that whizzed by to fast for me to record it. and I got some trivial errors after running it. I just ran the update and installed firefox... it is not ubuntu like I wanted but I think that I can get used to it. it has a unique user interface/gui... that is for sure.

I will keep working on ubuntu though

Congratulations :KS

If Kubuntu works, Ubuntu and the other flavours should work too, because it is the same engine under the hood, the same hardware drivers ... please share with the forum community, what tweaks you used to make it work :-)

---

### Post by mörgæs on 2013-09-02
If you have a running Kubuntu you can add the Ubuntu desktop environment with 

```
sudo apt-get install ubuntu-desktop
```

After that you can choose at boot time which desktop environment you want.


Which BIOS do you use?

---

### Post by stevecobb76 on 2013-09-02
add on graphics card is a ati hd 5450 
in windows it uses the ccc catylist control center drivers (pain in the rear to make stable)
the motherboard has a radeon hd 5400 builtin

bios ver.:  1.09

as far as the windows installation,
windows 7 is installed on one of the sata drives (disabled in cmos)
what I am doing is:
[B]to use windows I disable the pata drives and enable the sata drives
to use linux I disable the sata drives and enable the pata drive [/B](this make sence to me until I get ready to dual boot)
**kubuntu currently installed on pata drives (whole drive)**
**windows 7 installed on sata drive**

_**windows and linux have no effect on each other this way!!!!**_
I am also responding to this post from kubuntu. 
kubuntu had 1 graphic crash, but that was before I got to the update.

---

### Post by sudodus on 2013-09-02
I'm glad that the graphics work for you, because it can be quite tricky to get old ATI/Radeon graphics working in linux due to poor support in built-in as well as proprietary drivers. So I suggest that you stick with the version and flavour, that you are running now. By the way, Kubuntu it is, but which version (12.04 LTS or 13.04)?

Check with ```
lsb_release -a
```

And if you want another desktop environment, you can try to install the other desktop according to *mörgæs*, and select desktop at the log in screen.

If you still want to try another version or flavour you can install it to a third drive (internal or external), you try a light-weight desktop that might make your computer faster (good for playing video), ***Xubuntu*** or ***Precise Gnome Classic Tweaks***. If you already have 12.04 LTS, it is only a question of adding some packages to your existing installation.

sudo apt-get install xubuntu-desktop

and the big command box at [Precise Gnome Classic Tweaks]("https://help.ubuntu.com/community/PreciseGnomeClassicTweaks")

> I also want to use the Zukitwo-Dust gtk theme and change the cursor and icon themes as described [here]("http://ubuntuforums.org/showpost.php?p=11993655&postcount=70") (three commands):  

```
sudo add-apt-repository ppa:caffeine-developers/ppa -y && sudo add-apt-repository ppa:alexmurray/indicator-sensors -y && sudo add-apt-repository ppa:webupd8team/themes -y && sudo apt-get update && sudo apt-get install gnome-panel indicator-applet indicator-applet-session shiki-colors-metacity-theme caffeine indicator-sensors zukitwo-theme-all zukitwo-colors-theme -y && gconftool-2 --set "/apps/metacity/global_keybindings/panel_run_dialog" --type string "<Alt>F2" && gsettings set org.gnome.desktop.screensaver lock-enabled false && gsettings set com.ubuntu.update-notifier auto-launch false && gconftool-2 --set "/apps/metacity/general/button_layout" --type string ":minimize,maximize,close" && gconftool-2 -s --type string /apps/metacity/general/theme Shiki-Colors-Metacity && echo export LIBOVERLAY_SCROLLBAR=0 >> ~/.xprofile && gsettings set org.gnome.desktop.interface menus-have-icons true && gsettings set org.gnome.desktop.interface buttons-have-icons true && gsettings set org.gnome.desktop.background show-desktop-icons true && gsettings set org.gnome.nautilus.desktop volumes-visible true && gsettings set org.gnome.desktop.interface gtk-theme Zukitwo-Dust && gsettings set org.gnome.desktop.interface icon-theme ubuntu-mono-dark && gsettings set org.gnome.desktop.interface cursor-theme DMZ-White
```
The results: 

***Precise Gnome Classic Tweaks*** and several ***Lubuntu*** based versions are available via the One Button Installer too.

---

### Post by mörgæs on 2013-09-02
> **stevecobb76 said:**
> 
bios ver.:  1.09


Then I would upgrade. If you look at [1.10]("http://www.dell.com/support/drivers/us/en/19/DriverDetails?driverId=R224665&fileId=2731118881") for example, you will see that it fixes a boot problem.

---

### Post by stevecobb76 on 2013-09-02
> **mörgæs said:**
> If you have a running Kubuntu you can add the Ubuntu desktop environment with 

```
sudo apt-get install ubuntu-desktop
```

After that you can choose at boot time which desktop environment you want.


Which BIOS do you use?

as per morgaes (again win for me) 
I installed the ubuntu desktop on kubuntu 
there was 2 minor errors after install but then no errors after update and restart
it looks like ubuntu, and it feels like ubuntu.... 
[SIZE=5][COLOR=#ff0000]_**WIN for me thanks to morgaes!!!!!!!**_[/COLOR][/SIZE] Thank you on behalf of all the .05% of people who use the dell optisuck 320

if anyone has any other ideas of how to make ubuntu install without kernel panic I will try it

now for the dual boot.... 
should I make a new thread for that? I guess having kubuntu preinstalled on one hd and windows preinstalled on another hd and then making them play nice in a dual boot? time to read up on grub I guess?

---

### Post by Bucky Ball on 2013-09-02
*Thread moved to **Installation & Upgrades**.*

Yes, post a new thread re. dual-boot in this sub-forum.

---

### Post by stevecobb76 on 2013-09-02
partly solved and closed for now!!!! thanks all!!!
thread closed

---

### Post by mörgæs on 2013-09-02
Good that you got it solved. Please mark the thread so in Thread Tools (it will benefit the aforementioned .05%). 

A 'closed' thread means something else in our context.

---

### Post by Bucky Ball on 2013-09-02
> **mörgæs said:**
>  Please mark the thread so in Thread Tools (it will benefit the aforementioned .05%). 

Ah, that function is back! Great, better change my signature. ;)

---

