---
title: "Aaaaaahhhhhhh!! Help!!"
date: 2011-04-28
forum: Installation &amp; Upgrades
---

### Post by roh8880 on 2011-04-28
I didn't do anything different than the last time!

What happened?

[IMG]http://i615.photobucket.com/albums/tt233/roh8880/photo-1.jpg[/IMG]

---

### Post by roh8880 on 2011-04-28
I just upgraded and now I have no GUI!! I'm not all that savvy with computer lingo, so if you could break it down to me with hand puppets?

Is there a command line I can type to get to me GUI?

---

### Post by ppv on 2011-04-28
Maybe try "startx" at the command line.

---

### Post by roh8880 on 2011-04-28
Nope, didn't work:(:(:(

It says > NVIDIA failed to load the NVIDIA kernel module. Please check your system's kernel log for additional error messages.
        Failed to load module "nvidia" (module specific error, 0)
        No drivers available.
        
        Fatal server error:
        no screens found

---

### Post by roh8880 on 2011-04-28
Anybody? I run my business from that computer! It has everything that on it! The longer I'm down, customers get angry!

---

### Post by ivanovnegro on 2011-04-28
Im sorry to see this but why the hell you did not an backup before??? Or at least tried the Live CD before installing it also has the option to upgrade from the CD if you did not want to make a fresh install.
For me it seems your graphics card is not supported but I am not sure but I know there are issues with some NVidia cards.

---

### Post by 23dornot23d on 2011-04-28
If you do 

sudo apt-get update

does it list everything updating without errors ?

---

### Post by Elfy on 2011-04-28
> **roh8880 said:**
> Anybody? I run my business from that computer! It has everything that on it! The longer I'm down, customers get angry!
That was bad planning then.

> **23dornot23d said:**
> If you do 

sudo apt-get update

does it list everything updating without errors ?

If this doesn't help, you could try fixing the grpahics from the recovery menu or even renaming xorg (I suspect you have one and the driver's not installed yet) and rebooting - should start with nouveau then.

---

### Post by oceanfirehawk on 2011-04-28
Anytime you upgrade any OS, the manufactures/OS makers always suggest you do a backup. Doesn't matter if its Apple, Linux, or MS. Hope this works out for you.

---

### Post by roh8880 on 2011-04-28
No errors, restarted, still no GUI

---

### Post by StrayEddy on 2011-04-28
Foudn this on another post:
 
If the above don't work, try 
Code:
sudo telinit 5
This tells your computer to go to runlevel 5 (GUI). If that doesn't work, then something must not be installed right. Do 
Code:
sudo aptitude install ubuntu-desktop
and hopefully that will fix it.

---

### Post by Hedgehog1 on 2011-04-28
Please do the following:

Using another PC (OR by running your PC from an old LiveCD/LiveUSB), download the correct Natty ISO for your PC (or better yet bit torrent it today - servers are swamped) and create a LiveCD from the ISO.

Next, boot off you LiveCD, select 'Try' and then use it to backup your data to an external hard drive or USB stick.

Next, click in the install 11.04 and select the upgrade option:

[IMG]http://img848.imageshack.us/img848/874/upgradetonatty.png[/IMG]

This will repeat the COMPLETE upgrade with you having to wait on the swamped servers.

Hopefully, all will be well ofter this.

If not, we will still need you to have a LiveCD to do additional fixes.

***The Hedge***

:KS

---

### Post by Elfy on 2011-04-28
> **roh8880 said:**
> No errors, restarted, still no GUI

What nvidia card do you have to start with?

[Did you read the release notes?]("https://wiki.ubuntu.com/NattyNarwhal/ReleaseNotes")

Have you tried to rename xorg so that the system doesn't try and load nvidia drivers?

---

### Post by ivanovnegro on 2011-04-28
> **Hedgehog1 said:**
> Please do the following:

Using another PC (OR by running your PC from an old LiveCD/LiveUSB), download the correct Natty ISO for your PC (or better yet bit torrent it today - servers are swamped) and create a LiveCD from the ISO.

Next, boot off you LiveCD, select 'Try' and then use it to backup your data to an external hard drive or USB stick.

Next, click in the install 11.04 and select the upgrade option:

[IMG]http://img848.imageshack.us/img848/874/upgradetonatty.png[/IMG]

This will repeat the COMPLETE upgrade with you having to wait on the swamped servers.

Hopefully, all will be well ofter this.

If not, we will still need you to have a LiveCD to do additional fixes.

***The Hedge***

:KS

+1 Would be my next step.

---

### Post by 23dornot23d on 2011-04-28
Before we install or change anything .......

its better usually to assess what we can and cannot do ,,,,,,,

As Forrest Pixie pointed out it may be as simple as removing the xorg.conf ..... or creating another one.

My first thoughts were just to make sure that you had a internet connection and no errors showing up ..... 

which seems good ....... was no need to reboot ........ we just updated some lists that's all  ........


If you check to see if the xorg.conf exists ....... type in 

(cd is for Change directory)

cd /etc/X11/

(ls is for list )

ls

______________________________________________________________________

You could boot from a live CD and back-up all your data first .......... is a wise decision ......

I was not going to get you to change anything that would cause any more problems 
just assessing the situation .......

But best to get a backup first ,,,,,,,,,,, ( will watch and learn - as we have a few helpers now )

---

### Post by ninja9578 on 2011-04-28
I'm downloading an install CD now, I'll let you know if this fixes the problem.  It seems to be a problem with the Nvidia drivers.  Looks like this was a known bug, but they didn't put any checks in the upgrade procedure for it.  I'll let you know if reinstalling fixes the problem.

---

### Post by roh8880 on 2011-04-28
> **23dornot23d said:**
> Before we install or change anything .......

its better usually to assess what we can and cannot do ,,,,,,,

As Forrest Pixie pointed out it may be as simple as removing the xorg.conf ..... or creating another one.

My first thoughts were just to make sure that you had a internet connection and no errors showing up ..... 

which seems good ....... was no need to reboot ........ we just updated some lists that's all  ........


If you check to see if the xorg.conf exists ....... type in 

(cd is for Change directory)

cd /etc/X11/

(ls is for list )

ls

______________________________________________________________________

You could boot from a live CD and back-up all your data first .......... is a wise decision ......

I was not going to get you to change anything that would cause any more problems 
just assessing the situation .......

But best to get a backup first ,,,,,,,,,,, ( will watch and learn - as we have a few helpers now )


xorg.conf does not exist. > No such file or directory

---

### Post by ninja9578 on 2011-04-28
They released this way too early.  The install CD I downloaded isn't even bootable.  My recommendation is to reinstall 10.10 until this version is more mature.  I'm doing that now, I don't think there is a way to fix this problem, I've been on the net and talking to my support team for most of the day.

---

### Post by roh8880 on 2011-04-28
> Using another PC (OR by running your PC from an old LiveCD/LiveUSB), download the correct Natty ISO for your PC (or better yet bit torrent it today - servers are swamped) and create a LiveCD from the ISO.

Next, boot off you LiveCD, select 'Try' and then use it to backup your data to an external hard drive or USB stick.

Next, click in the install 11.04 and select the upgrade option:

How do I make a new live CD?

---

### Post by roh8880 on 2011-04-28
> **ninja9578 said:**
> They released this way too early.  The install CD I downloaded isn't even bootable.  My recommendation is to reinstall 10.10 until this version is more mature.  I'm doing that now, I don't think there is a way to fix this problem, I've been on the net and talking to my support team for most of the day.

Is there a way to revert to 10.10 without a GUI?

---

### Post by CyberNerdz on 2011-04-28
[http://ubuntuforums.org/showthread.php?t=835573](http://ubuntuforums.org/showthread.php?t=835573)

---

### Post by ninja9578 on 2011-04-28
> **roh8880 said:**
> Is there a way to revert to 10.10 without a GUI?

From what I've seen, there isn't a way to revert even in the GUI.  It seems Ubuntu lacks the basic revert functionality, which I found very upsetting.  Even Windows has a that ability :(

I'm trying an 11.04 download that's a little different, maybe this one will work.  I'm going to try one more time before hosing my system.

---

### Post by pascaltch on 2011-04-28
> **roh8880 said:**
> Anybody? I run my business from that computer! It has everything that on it! The longer I'm down, customers get angry!

what happens when you press ctrl and alt then F7 touch on your keyboard ?

---

### Post by Hedgehog1 on 2011-04-28
> **ninja9578 said:**
> From what I've seen, there isn't a way to revert even in the GUI.  It seems Ubuntu lacks the basic revert functionality, which I found very upsetting.  **_Even Windows has a that ability :(_**

I'm trying an 11.04 download that's a little different, maybe this one will work.  I'm going to try one more time before hosing my system.

Uninstall Windows 7?  I missed that when I installed it.  Course, I wasn't looking for it.

Be aware you can load Natty/11.04 and still use the 'Classic’ UI: [**_Natty Info: Your UI options_**]("http://ubuntuforums.org/showthread.php?t=1741293")


***The Hedge***

:KS

---

### Post by NadirPoint on 2011-04-28
Over the past couple weeks I built a brand new box, just for Natty.

Hasn't done anything yet, except boot a LiveCD.

Until tonight...  :guitar:

---

### Post by PatrickD-52761 on 2011-04-28
> **ninja9578 said:**
> They released this way too early.  The install CD I downloaded isn't even bootable.  My recommendation is to reinstall 10.10 until this version is more mature.  I'm doing that now, I don't think there is a way to fix this problem, I've been on the net and talking to my support team for most of the day.

Out of curiosity (and also a warning for the OP and anyone else looking for solutions to this issue), when you burned the Live CD, did you choose the lowest burn speed or a higher one?  IIRC, it's recommended on the website (and is definitely recommended in other circles) to use the slowest (lowest) burn speed available.  That reduces the risk of CD corruption (like not being able to boot).

If you check at [http://www.ubuntu.com/download](http://www.ubuntu.com/download), and choose the "CD" Option in the burn section, then click "Show me How", it recommends to burn at the lowest speed possible.  They really don't show you how to change that, but I would click on "Properties" next to the drive that you're burning it to. The speed setting *SHOULD* be in there.

I've done this myself (burning at a higher speed) and ran into problems.   So, when it comes to burning iso files, "Slow and steady wins the  race."

Have a great day:)
Patrick.

P.S. Changing the burn speed is done differently in different programs. If their help menu doesn't tell you how to change the speed, I would recommend Google or your preferred search engine.

---

### Post by ninja9578 on 2011-04-28
> **Hedgehog1 said:**
> Uninstall Windows 7?  I missed that when I installed it.  Course, I wasn't looking for it.
Yes, if you upgrade and decide you want to go back, you can go back to XP.  Most OSs have this feature, which is why I never bothered doing a deep backup before upgrading.  I've learned my lesson.

> Be aware you can load Natty/11.04 and still use the 'Classic’ UI: [**_Natty Info: Your UI options_**]("http://ubuntuforums.org/showthread.php?t=1741293")


***The Hedge***

:KS
How?  Is there a way to load that up now that we are already stuck out of the desktop?  I can't even get X's failsafe to display.

---

### Post by Hedgehog1 on 2011-04-28
> **NadirPoint said:**
> Over the past couple weeks I built a brand new box, just for Natty.

Hasn't done anything yet, except boot a LiveCD.

Until tonight...  :guitar:

Looking forward to your reports on your new box!!!


***The Hedge***

:KS

---

### Post by ninja9578 on 2011-04-28
> **PatrickD-52761 said:**
> Out of curiosity (and also a warning for the OP and anyone else looking for solutions to this issue), when you burned the Live CD, did you choose the lowest burn speed or a higher one?  IIRC, it's recommended on the website (and is definitely recommended in other circles) to use the slowest (lowest) burn speed available.  That reduces the risk of CD corruption (like not being able to boot).

If you check at [http://www.ubuntu.com/download](http://www.ubuntu.com/download), and choose the "CD" Option in the burn section, then click "Show me How", it recommends to burn at the lowest speed possible.  They really don't show you how to change that, but I would click on "Properties" next to the drive that you're burning it to. The speed setting *SHOULD* be in there.

I've done this myself (burning at a higher speed) and ran into problems.   So, when it comes to burning iso files, "Slow and steady wins the  race."

Have a great day:)
Patrick.

P.S. Changing the burn speed is done differently in different programs. If their help menu doesn't tell you how to change the speed, I would recommend Google or your preferred search engine.

I know how to do that, I burned it at 8x (the slowest) and I had the burner verify the disc after it was done, there is nothing wrong with the disc.  Perhaps I downloaded the wrong image.

---

### Post by roh8880 on 2011-04-28
Ok, I've tried booting from a live CD and it still does the same thing. I've tried to update the drivers from here
[http://ubuntuforums.org/showthread.php?t=835573](http://ubuntuforums.org/showthread.php?t=835573)

Nothing.

Anyone else have a solution for me to try?

---

### Post by ninja9578 on 2011-04-28
> **roh8880 said:**
> Ok, I've tried booting from a live CD and it still does the same thing. I've tried to update the drivers from here
[http://ubuntuforums.org/showthread.php?t=835573](http://ubuntuforums.org/showthread.php?t=835573)

Nothing.

Anyone else have a solution for me to try?

I tried that too, but wasn't surprised when it didn't work.  Look at the date on it, it's almost three years old.

---

### Post by roh8880 on 2011-04-28
> **pascaltch said:**
> what happens when you press ctrl and alt then F7 touch on your keyboard ?

[IMG]http://i615.photobucket.com/albums/tt233/roh8880/photo-2.jpg[/IMG]

After ctl+alt+F7

---

### Post by roh8880 on 2011-04-28
Screw all this! I'm just going to make a 10.10 install disk, break out my hot-swap dock, back up my files manually, and do a fresh install of 10.10

---

### Post by marek_online on 2011-04-28
Don't know if it will do you any good, but I had an nvidia driver problem after upgrading too.

I removed and reinstalled every nvidia package I could manage, to no avail.

Then I installed just nvidia-current (and its dependencies). Initially, this didn't work either, but it turned out that the appropriate linux-headers for my kernel (in may case 2.6.38-8-pae, use "uname -r" to check what yours is) were missed. Installed those and the nvidia drivers ran through their postinstall procedure properly during the headers installation. Everything working smoothly now.

---

### Post by Hedgehog1 on 2011-04-28
> **roh8880 said:**
> Screw all this! I'm just going to make a 10.10 install disk, break out my hot-swap dock, back up my files manually, and do a fresh install of 10.10

That may be your best plan for today.

When time (and emotion) allows, try a Natty install on a clean disk and then move your documents over to it when you are comfortable with it.

A quite weekend works (if you get those, not everyone does)


***The Hedge***

:KS

---

### Post by roh8880 on 2011-04-28
So, I'm doing a Memtest86 before I reinstall 10.04 LTS.

This is taking forever!

---

### Post by 23dornot23d on 2011-04-28
Out of interest what does the following have in it .......

[COLOR=Red]**less /var/log/Xorg.0.log**[/COLOR]

(Capital X in Xorg.zero.log - ctrl-z will get you out or continue to the end ....)

maybe some more clues .... in there ......
also did you try this ..... if you are going to wipe your system it may be worth trying it first.

sudo apt-get install nvidia-xconfig (if its not already installed)
[COLOR=Red][B]nvidia-xconfig
[/B] [/COLOR]to create a xorg.conf file ....... 

( you still have a few options if you want to try to solve it - did you back everything up ? )

What graphics card is it by the way ...... 

```

NVIDIA failed to load the NVIDIA kernel module. Please check your system's kernel log for additional error messages.
        Failed to load module "nvidia" (module specific error, 0)
        No drivers available.
        
        Fatal server error:
        no screens found                      

```From the error you got its an Nvidia but which model ...

The way it usually works is there is a driver that should exist on the system for your graphics card
this driver is then picked up from the header files for the kernel
the kernel gets compiled to include it .......

as long as you have the correct drivers installed for the graphics card ..... and the kernel has picked them up ok
then the xorg.conf can set the display  to be used 
( to the best of my knowledge - they have messed about with the way it boots up and plymouth can be a problem too )

So sometimes - well nearly always I swap and I use [COLOR=Red]**kdm**[/COLOR] to boot up to the desktop ........ 

[COLOR=Red]**sudo apt-get install kdm**[/COLOR]

you still can run ubuntu and even swap back ..... to gdm later if it should solve a problem .....

I like the menu better too ...... but thats as much as I can say at this moment in time ..... 

maybe someone else has some more useful info .....

Ok best of luck - guess you went back to 10.04 ....... which in itself is not such a bad decision ..... time is in your favour for
the new release to get better and some of the problems to get solved.

---

### Post by roh8880 on 2011-04-28
SOLVED!!

```
sudo apt-get install kdm
```

This allowed me to reset the driver info! I now have a GUI! Thank you 23dornot23d! Now I don't have to wipe my hard drive! My hardware wasn't compatible with unity. So it shut it down. HA!

GOD I LOVE THIS SITE!

HEY ADMIN!! Give 23dornot23d a prize! He rocks! :guitar:

---

### Post by roh8880 on 2011-04-28
Damn, I knew it was too good to be true.

I updated the drivers and now my menu is missing and my second monitor is not being recognised when it was just before my drivers were updated.

Any ideas 23dornot23d?

---

### Post by 23dornot23d on 2011-04-28
I use two monitors .....

go to admininistration Nvidia-settings

and check out the display configuration is set ok ..... you may need to re-write your xorg.conf from there


save to xconfiguration file once done ..... you will need your password to do this too

check this and post a screen shot too ..... if you would please

mine looks like this I have 3 monitors but am only using two .... but yours will look similar ....

its probably the xorg.conf that just needs updating ..... I hope

[IMG]http://i.min.us/ikUjjs.jpeg[/IMG]

---

### Post by roh8880 on 2011-04-28
Ok, I rebooted into safe mode, I have my menus back, but now I can't change the driver accelerators and my second monitor is still not being recognised.

---

### Post by 23dornot23d on 2011-04-28
You are going too fast ..... go back in normal mode .....

we will solve one problem at a time ..... the monitors need setting up with the
nvidia driver running ,,,,  (not in safe-mode) ... as I know that .... nvidia-settings will only run with the nvidia drivers loaded .....

and you need this to set the two monitors up .....

The desktop can be sorted after that

---

### Post by roh8880 on 2011-04-28
> **23dornot23d said:**
> I use two monitors .....

go to admininistration Nvidia-settings

and check out the display configuration is set ok ..... you may need to re-write your xorg.conf from there


save to xconfiguration file once done ..... you will need your password to do this too

check this and post a screen shot too ..... if you would please

mine looks like this I have 3 monitors but am only using two .... but yours will look similar ....

its probably the xorg.conf that just needs updating ..... I hope

[IMG]http://i.min.us/ikUjjs.jpeg[/IMG]


It doesn't want to let me save the configuration, but I found that the second monitor had been disabled.

---

### Post by 23dornot23d on 2011-04-28
ok go to configure on the screen I have shown and enable it ...... twinview will allow you to try it out

mine says at first it will not save it - but then it asks for the password and as long as you enter 
the root password correctly here - then you should be able to save it .......... let me know where you get to

and post a screen shot ..... gives me an idea what you have ...... 

(I use [COLOR=Red]**[minus]("http://min.us/") **[/COLOR]..... just drag and drop a ksnapshot onto it and go to the share tab grab the link and add it where there
is a picture in edit mode on here ..........)

---

### Post by roh8880 on 2011-04-28
[IMG]http://i615.photobucket.com/albums/tt233/roh8880/photo-3.jpg[/IMG]

It won't let me save to the xorg file. It says that it's unable to open the X config file for writing

---

### Post by 23dornot23d on 2011-04-28
Ok it did enable the screen though .......

Looks to me as if it did from your screenshot ....

so now we need to alter the xorg.conf 

might have to do this manually and add it ..... not sure why its not letting you write to it though what happens when you press ok

it should then ask for your password

---

### Post by roh8880 on 2011-04-28
It doesn't ask for a password at all and once I quit, the second screen stays disabled. Can you walk me through rewriting the xorg file?

---

### Post by 23dornot23d on 2011-04-28
You are given something like 20 seconds or so to accept the layout and it should remain set ....
are you accepting this - you should do ...... maybe thats why you cannot save it ....



when you click to save the xorg.conf file ..... there is a option to preview it ......

from here you can cut and paste the code you need ....

[IMG]http://i.min.us/ing5vo.jpeg[/IMG]





gksudo gedit /etc/X11/xorg.conf

Should allow you to manually alter it ...... make sure you check what you do in this though ..... as it is important.

keep a backup too ..... of the one that works incase you have to revert back to it ......



mine looks like this in the preview ....

```

# nvidia-settings: X configuration file generated by nvidia-settings
# nvidia-settings:  version 270.29  (buildd@roseapple)  Fri Feb 25 14:43:24 UTC 2011


Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0" 0 0
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
    Option         "Xinerama" "0"
EndSection

Section "Files"
EndSection

Section "InputDevice"

    # generated from default
    Identifier     "Mouse0"
    Driver         "mouse"
    Option         "Protocol" "auto"
    Option         "Device" "/dev/psaux"
    Option         "Emulate3Buttons" "no"
    Option         "ZAxisMapping" "4 5"
EndSection

Section "InputDevice"

    # generated from default
    Identifier     "Keyboard0"
    Driver         "kbd"
EndSection

Section "Monitor"

    # HorizSync source: edid, VertRefresh source: edid
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "PHILIPS 107E"
    HorizSync       30.0 - 70.0
    VertRefresh     50.0 - 160.0
    Option         "DPMS"
EndSection

Section "Monitor"
    Identifier     "Monitor1"
    VendorName     "Unknown"
    ModelName      "ORN ORION"
    HorizSync       14.0 - 46.0
    VertRefresh     47.0 - 61.0
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 9300M GS"
EndSection

Section "Device"
    Identifier     "Device1"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 9300M GS"
    BusID          "PCI:1:0:0"
    Screen          1
EndSection

Section "Screen"

# Removed Option "metamodes" "DFP-0: nvidia-auto-select +0+1080, DFP-1: 1920x1080 +0+0"
# Removed Option "metamodes" "DFP-0: NULL, DFP-1: 1920x1080 +0+0"
# Removed Option "metamodes" "CRT: nvidia-auto-select +1920+0, DFP-0: NULL, DFP-1: 1920x1080 +0+0"
# Removed Option "metamodes" "CRT: nvidia-auto-select +0+0, DFP-0: 1024x768 +0+1024"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView" "1"
    Option         "TwinViewXineramaInfoOrder" "DFP-1"
    Option         "metamodes" "CRT: nvidia-auto-select +1920+0, DFP-1: 1920x1080 +0+0"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

Section "Screen"

# Removed Option "metamodes" "CRT: nvidia-auto-select +0+0"
    Identifier     "Screen1"
    Device         "Device1"
    Monitor        "Monitor1"
    DefaultDepth    24
    Option         "TwinView" "0"
    Option         "metamodes" "DFP-1: 1920x1080 +0+0"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection




```

and this is it in the proper xorg.conf file

```

# nvidia-settings: X configuration file generated by nvidia-settings
# nvidia-settings:  version 270.29  (buildd@roseapple)  Fri Feb 25 14:43:24 UTC 2011


Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0" 0 0
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
    Option         "Xinerama" "0"
EndSection

Section "Files"
EndSection

Section "InputDevice"

    # generated from default
    Identifier     "Mouse0"
    Driver         "mouse"
    Option         "Protocol" "auto"
    Option         "Device" "/dev/psaux"
    Option         "Emulate3Buttons" "no"
    Option         "ZAxisMapping" "4 5"
EndSection

Section "InputDevice"

    # generated from default
    Identifier     "Keyboard0"
    Driver         "kbd"
EndSection

Section "Monitor"

    # HorizSync source: edid, VertRefresh source: edid
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "PHILIPS 107E"
    HorizSync       30.0 - 70.0
    VertRefresh     50.0 - 160.0
    Option         "DPMS"
EndSection

Section "Monitor"
    Identifier     "Monitor1"
    VendorName     "Unknown"
    ModelName      "ORN ORION"
    HorizSync       14.0 - 46.0
    VertRefresh     47.0 - 61.0
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 9300M GS"
EndSection

Section "Device"
    Identifier     "Device1"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 9300M GS"
    BusID          "PCI:1:0:0"
    Screen          1
EndSection

Section "Screen"

# Removed Option "metamodes" "DFP-0: nvidia-auto-select +0+1080, DFP-1: 1920x1080 +0+0"
# Removed Option "metamodes" "DFP-0: NULL, DFP-1: 1920x1080 +0+0"
# Removed Option "metamodes" "CRT: nvidia-auto-select +1920+0, DFP-0: NULL, DFP-1: 1920x1080 +0+0"
# Removed Option "metamodes" "CRT: nvidia-auto-select +0+0, DFP-0: 1024x768 +0+1024"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView" "1"
    Option         "TwinViewXineramaInfoOrder" "DFP-1"
    Option         "metamodes" "CRT: nvidia-auto-select +1920+0, DFP-1: 1920x1080 +0+0"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

Section "Screen"

# Removed Option "metamodes" "CRT: nvidia-auto-select +0+0"
    Identifier     "Screen1"
    Device         "Device1"
    Monitor        "Monitor1"
    DefaultDepth    24
    Option         "TwinView" "0"
    Option         "metamodes" "DFP-1: 1920x1080 +0+0"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection



```


Yours will obviously be different to this ...... do not try using mine .....

---

### Post by roh8880 on 2011-04-28
Ok, code copied, what's next?

---

### Post by 23dornot23d on 2011-04-28
[COLOR=Red]**gksudo gedit /etc/X11/xorg.conf**[/COLOR]


this will open your xorg.conf 


you need to put the new configuration into it now ....... 

basically just cut and paste ........

Then save it ....... as

[COLOR=Red][B]/etc/X11/xorg.conf


Then if all has gone well and no errors made ..... it will reboot with both monitors working
[/B][/COLOR]

---

### Post by trollger on 2011-04-28
Get a rescue CD (like ) and a usb stick. Run the live Linux CD and back your files up to the USB stick. Format the damned partition and start over (you might want to stick with Ubuntu 10). Thats what I would have done to start with.

try [http://ubuntu-rescue-remix.org/](http://ubuntu-rescue-remix.org/) or [http://www.knoppix.net/](http://www.knoppix.net/)

Good luck. Oh and next time click try Ubuntu first ;)

I see you have some stuff working so don't do anytihng to radicle.

---

### Post by roh8880 on 2011-04-28
Nope, it keeps rebooting me into low graphics mode.

The system won't allow me to change the proprietary drivers in the system/administration/Additional Drivers

I think that I may need a new graphics card. Do you suggest any ones that work with Unity?

---

### Post by roh8880 on 2011-04-28
I just rebooted and now my menu has disappeared again.

---

### Post by 23dornot23d on 2011-04-28
You just had nvidia-settings running .....

So the driver was installed and working ......

If its not rebooted using the xorg.conf - then there is a problem in that file
possibly ......

You are so close to it working ...... there is not a problem with the driver as far as
I could see ......

why are you doing this .... at what point did nvidia-settings stop working ?

```

The system won't allow me to change the proprietary drivers in the system/administration/Additional Drivers


```I do not give in on small problems thats why I have 13 different Linux systems running on my laptop .... 
Your Graphics card and driver are fine ...... you posted a [screen shot showing both monitors set up earlier]("http://ubuntuforums.org/showpost.php?p=10734878&postcount=45") in the
thread .......

---

### Post by roh8880 on 2011-04-28
I clicked on that magic little button that said "It's ok! I'll be your friend. My name is 11.04, what's yours? We really should UPDATE."

So after the update was completed, I rebooted and that's when everything started to go awry!

As you can see from the earlier pages in this thread and the pics of my terminal only OS.

And the screenshot that I posted of my monitors set up was before it was saved. My problem is that every time I open the xorg.conf file from terminal, there is absolutely nothing there. Even after I click save as, close, then reopen.

---

### Post by 23dornot23d on 2011-04-28
Not sure what happened with the xorg.conf file ...... but that is where the problem is.

if you cut the text from the preview as I said and posted it into the xorg.conf and saved it there would be text in it.

If you want to go back to 10.04 I am not here to stop you ...... maybe one comment 
from someone changed your mind on the direction you want to go ......

This was the part where you need to copy the text ...... [LINK]("http://ubuntuforums.org/showpost.php?p=10734946&postcount=48")

when you press the preview button there will be text there ....... this has to be cut from there and pasted into the 

**[COLOR=Red]/etc/X11/xorg.conf [/COLOR]**

file


post the file or the text so I can see it please ....... after you complete this step your graphics will be working ......

( no need for another graphics card and no need for other drivers ....... )

If you need to take time out do so ...... there is always another day ,,,,,,

---

### Post by roh8880 on 2011-04-28
Interesting new development. I rebooted my computer again, and it gave me the "running in low graphics mode" tiny screen again.

This time I selected "Restart X"

and it went to the New 11.04 configuration like magic. Not sure what just happened, but it's there.

---

### Post by roh8880 on 2011-04-28
Alas, I rebooted, and now it's gone. But the other monitor works now, but instead of a cursor, it's a large "X". Oh, and my menu options like applications and places are not there.

---

### Post by 23dornot23d on 2011-04-28
Glad to hear that ...... its worked ..... the large X comes up when you restart the xserver but soon goes back to normal.

You may find it does this next time too ...... 
I have seen this before ...... but it is working from the xorg then and both screens are ok .

Can you use compiz ..... that would let me know you are in or close to being able to use UNITY ......
if compiz is working and nvidia setings is working then the driver is working corectly and xorg.conf is set up ok too.

Ok lets see if we can sort the desktop out now ...... are you in classic or unity ...... can you do a screen shot
so we can go from here ..... or do you need to do other things .....

pressing alt+f2 and typing Unity .... does that do anything


I really need to see what you have .....

With dual monitors the Unity icon menu will be on the left hand side of the primary monitor
this means it may autohide on the right hand side monitor ...... and be awkward to select

---

### Post by roh8880 on 2011-04-28
```
ghost@ghost:~$ compiz
compiz (core) - Error: Screen 0 on display ":0.0" already has a window manager; try using the --replace option to replace the current window manager.
ghost@ghost:~$ 

```

It doesn't look like I can . . .


And I'm in classic now. Unity seems to have stopped working for me.

---

### Post by erniej on 2011-04-28
I had the same problem after updating the proprietary graphics drivers. Start the computer and, when the GRUB screen appears, chose recovery mode. I deleted the proprietary graphics driver and everything worked fine again. Above all: DON'T PANIC!

---

### Post by 23dornot23d on 2011-04-28
At this point you had it working ......

> 
Interesting new development. I rebooted my computer again, and it gave me the "running in low graphics mode" tiny screen again.

This time I selected "Restart X"

and it went to the New 11.04 configuration like magic. Not sure what just happened, but it's there.
4 minutes later you rebooted 

> 
Alas, I rebooted, and now it's gone. But the other monitor works now,  but instead of a cursor, it's a large "X". Oh, and my menu options like  applications and places are not there.     

and as far as I can tell you dropped back into safe mode ..... 
and thats why you said this ......

> 
And I'm in classic now. Unity seems to have stopped working for me.     
So when you reboot again ...... what happens ?

do not go deleting anything ......

You have the right drivers and they work .....  we have proved that already ...... this screen shot the only one I have seen proves it to me.

This as far as I know cannot display in safe mode ...... neither can it tell you what monitors and graphics card you have installed ....
which here is the GeForce 9500 GT ..... without it working correctly ....... 

[IMG]http://i615.photobucket.com/albums/tt233/roh8880/photo-3.jpg[/IMG]

if I can only stop you re-booting it once you are in the right mode .....

You can tell when you are in the correct mode the Nvidia Settings will work ......

Then you can set up the Desktop as you want it .....

---

### Post by roh8880 on 2011-04-28
After I reboot, my monitors go all crazy. Everything appears to be there, but the cursor is off centered. Everything I click happens further right of where the cursor actually is. It won't allow me to take a screen shot either, and now my sound shuts off after a few seconds of me logging in. I have to leave sound pref and gnome alsa mixer open for the sound to work.


Ok, I'm shutting down for the night. It seems that the only way I can get everything to go back to normal is using a safe mode session.

I'll just use this till there is a patch to fix it, I suppose.

---

### Post by 23dornot23d on 2011-04-29
> 
After I reboot, my monitors go all crazy. Everything appears to be  there, but the cursor is off centered. Everything I click happens  further right of where the cursor actually is. It won't allow me to take  a screen shot either, and now my sound shuts off after a few seconds of  me logging in. I have to leave sound pref and gnome alsa mixer open for  the sound to work.
Then it is using the xorg.conf ..... and there is a problem still with it ..... you may have the monitors set the wrong way around ...... or something ......

Nvidia settings and writing the proper xorg.conf file will solve the majority of what you are seeing here ...... you have to work out why its not letting you write the xorg.conf file to disk.

That will save any errors occurring while you are trying to cut and paste it ......

Its been a long session ..... but hopefully tomorrow you will see that you have
achieved to get from a terminal display to a GUI .....  sound is another problem
but we were dealing with the monitor and the settings ...... one thing at a time 
and you will sort it ......

Best of luck with getting it going and I hope this helped in some small way ......

(Your [primary display is probably better off being on the left side]("http://i.min.us/ing75K.png") .... with the unity menu being over to the left on a two monitor system .....)
as it is harder to work with in the middle of the two monitors.

---

### Post by myoldhouse on 2011-04-29
Don't you have to have Administrator privileges to write to xorg.conf? Try starting Nvidia settings from a terminal:

$ sudo nvidia-settings

That should give you the proper permissions to write into /etc/X11 directory.

---

### Post by 23dornot23d on 2011-04-29
> **myoldhouse said:**
> Don't you have to have Administrator privileges to write to xorg.conf? Try starting Nvidia settings from a terminal:

$ sudo nvidia-settings

That should give you the proper permissions to write into /etc/X11 directory.

I agree with this ...... this sounds as if it should work ....... 

( On one of my system's that I updated I found this also failed to write the xorg.conf file though .... maybe a bug with the latest version - not sure yet - 
We will find out if this user or others try this and find it will still not write a xorg.conf .... 
no harm in trying and it should allow for a easy way to alter the screen layout and resolutions if it will write the file.  )

[COLOR=Red]**$ sudo nvidia-settings**[/COLOR]

---

### Post by kolbiel on 2011-04-29
> **erniej said:**
> I had the same problem after updating the proprietary graphics drivers. Start the computer and, when the GRUB screen appears, chose recovery mode. I deleted the proprietary graphics driver and everything worked fine again. Above all: DON'T PANIC!


erniej, could you give a step by step instruction for dummies how you did this? have the same problem here. cheers

---

### Post by fk_ on 2011-04-29
hi

I believe there's the option in boot menu but you probably can't see it because by default menu isn't shown and you have to press ESC.
There should be one option marked "recovery mode" of "safe mode" or something like that.

Guys, I have experience in recovering systems from very serious crashes and would be glad to help you.

Please excuse my English just in case.

---

### Post by kolbiel on 2011-04-29
Ok, how do I delete the proprietary graphics driver while in recovery mode?

---

### Post by fk_ on 2011-04-29
you should just disable it in you xorg configuration
just open /etc/X11/xorg.conf with you favorite editor and find the line containing "nvidia" then simply comment this line by adding # to the very beginning.

For example, this is the piece of my xorg.conf that should be modified:

> Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
EndSection

after editing it should look like this
> Section "Device"
    Identifier     "Device0"
    #Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
EndSection

the options here are these:
1. You can just disable driver definition and ubuntu will try to use another driver like VESA, nv or nouveau if any of them was installed before.
2. You can modify this line by changing "nvidia" to "nv", "nouveau" or "vesa".
3. You can run nvidia-settings which will generate xorg.conf from scratch and this frequently solves many troubles.
4. You can simply remove xorg.conf (or backup it which is much better :) ). Then xorg server will use VESA driver and very common configuration which may show you desktop but with some artifacts like improper resolution or something else non-fatal.

---

### Post by VideoRoy on 2011-04-29
Actually this is the same problem I had on 2 computers now and I solved it a different way.  Just do not use the PAE kernel if you do not really care about using all your RAM.  On my laptop and desktop it just does not matter to me.

I did not read the whole thread here but if you can still boot to the main menu, choose the menu entry that says Older Linux Versions and choose the top entry which should be Linux-Generic without the PAE in the title.

If you can boot fine the follow my last post in the thread below and just remove the PAE entries.  Once you are up a running and have more time you can go back and play with the PAE kernels which is what I will do as well.

[http://ubuntuforums.org/showthread.php?t=1742199]("http://ubuntuforums.org/showthread.php?t=1742199")

---

### Post by fk_ on 2011-04-29
well, I'm using x64 so don't have to care about PAE
but thanks for the pointing to this problem - you never know what can help in future :)

---

### Post by jespdj on 2011-04-29
> **roh8880 said:**
> Anybody? I run my business from that computer! It has everything that on it! The longer I'm down, customers get angry!
Why did you be so careless with immediately installing a major new version on this machine if it is so important for your business?

Don't fix it if it ain't broken. You might be better off running an LTS (long-term support) version of Ubuntu if this is a business critical machine.

---

### Post by VideoRoy on 2011-04-29
> **fk_ said:**
> well, I'm using x64 so don't have to care about PAE
but thanks for the pointing to this problem - you never know what can help in future :)
Sorry, I was referring to the OP where the PAE is shown on the screen and his failure mode was the same as 2 of my units.  All my systems are 64 bit HW but I run 32 bit Ubuntu on all but one of them due to some application compatibility.

I should have read the whole thread but I thought this was a quick fix.

---

### Post by samriggs on 2011-05-02
I have a cousin that has the same issue, I found this link for him that might be able to help you folks out, not sure though because this is linux mint but it's based on ubuntu so it might help out.
At least I hope it does for you to make life easier.
But check first because you folks are using unity now and this works on ubuntu 9 and 10
[Nvidia 6150le help]("http://forums.linuxmint.com/viewtopic.php?f=59&t=48077")

Good luck with the install and hope it goes better :)

---

### Post by fk_ on 2011-05-11
> **samriggs said:**
> I have a cousin that has the same issue, I found this link for him that might be able to help you folks out, not sure though because this is linux mint but it's based on ubuntu so it might help out.
At least I hope it does for you to make life easier.
But check first because you folks are using unity now and this works on ubuntu 9 and 10
[Nvidia 6150le help]("http://forums.linuxmint.com/viewtopic.php?f=59&t=48077")

Good luck with the install and hope it goes better :)

I haven't used mint for a while but I guess it uses the same environment as ubuntu does.
The problems with booting liveCD are concerned to the graphics system unavailability - unity hardly depend on 3d and needs video chip with proper 3d hardare and software to work (even run).
To see what happens you need to look in the xorg log files /var/log/Xorg.0.log. The lines which begin with (EE) - that's what you need to pay attention to. You can simply smoke google - just copy and paste content of such line to the search form =)

---

