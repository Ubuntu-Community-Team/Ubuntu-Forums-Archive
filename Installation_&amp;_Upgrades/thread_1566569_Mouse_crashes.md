---
title: "Mouse crashes"
date: 2010-09-02
forum: Installation &amp; Upgrades
---

### Post by techiewannabe on 2010-09-02
Since I installed Lucid, my mouse will work for a while and then, for no apparent reason, stop working. The only way that I can get it to work again is to reboot the computer. 
 
I should also point out that during my install, I recieved serveral crashes. By the end of the install, the system reported to me that my computer may be unstable as it was a "partial install." Efforts to correct this problem have failed. 
 
Any help you can offer would be appreciated.

---

### Post by ajgreeny on 2010-09-02
In view of the error messages at install, I would seriously consider downloading the iso file again, or at the very least checking it with the md5sum and burning and installing again.

I suspect that the crashes at install time were a symptom of a bad burn or iso, and you may not be able to overcome the current problem any other way.

---

### Post by techiewannabe on 2010-09-02
Ajgreeny:
Thanks for your note.
I didn't burn the install from a disc. I updated from the Update Manager. If I use an ISO will that require me to format the drive?
Thanks.
techiewannabe.

---

### Post by ajgreeny on 2010-09-02
It sounds like a bad upgrade in that case, and I still think a new install would be the best way out of the problem.

It would certainly mean a format so you will need to back up all your /home folders and files, but then it is only a 20 min job to install, and another few minutes to update and add all your other apps.

Try the live CD of 10.04 first to make sure it's not a hardware problem, and then consider installing with a separate /home partition.  See [http://www.psychocats.net/ubuntu/installseparatehome](http://www.psychocats.net/ubuntu/installseparatehome)

---

### Post by techiewannabe on 2010-09-02
Ajgreeny:

Thanks for your suggestion. I think I'll do the fresh install and use the separate home partition as you suggest.
 
I won't be able to get to it for a couple of days, but I'll let you know how it goes.
 
Thanks, again.

---

### Post by techiewannabe on 2010-09-03
Ajgreeny:

I can barely believe I'm telling you this. I did a complete install as outlined in the page that you referenced. Unlike the directions on that page, where the writer created 2 partion without a swap partition, I created a swap partition. Other than that, I followed the directions to a "T," creating 3 partitions. (/, /home, and swap.)
 
Indeed, the look and feel of the system was vastly improved over what I had been using with the previously unstable system. I was excited about it and began setting things up. I was confident that the problem was solved. Unfortunately, however, after using it for a while, once again, the mouse failed to operate at all. In fact, it is not just the mouse. I've learned that nothing works. Tab doesn't work; f-tabs don't; etc. 
 
I am running a Compaq R-3000 laptop with a Pentium 4. It has 3 gig of RAM. I feel like it should have plenty of horse-power to handle the OS.
 
Other suggestions?
 
Thanks, again.

---

### Post by davidmohammed on 2010-09-03
when you say "the mouse stops working" - do you mean that the computer appears to freeze and the mouse stops moving?

Possibly/probably this is a graphics issue.

from a terminal session type

lspci | grep VGA


depending on the graphics card you are using, the answer may be to choose an alternative boot option or install additional packages.

---

### Post by techiewannabe on 2010-09-03
Davidmohammed:

Thanks for your note. I mean that the entire system crashes. At first, I thought it was just the mouse, but, in fact, no input device works. I can see the screen but can not do anything with it. I have to reboot the machine to get it to work.

When I put in the command you suggested, I got the following message: 

[INDENT]mountlings@Compaq-laptop:~$ lspci | grep VGA
01:05.0 VGA compatible controller: ATI Technologies Inc RS300M AGP [Radeon Mobility 9100IGP]
[/INDENT]
What does this suggest?

Thanks for your help.

---

### Post by davidmohammed on 2010-09-03
Can I suggest you boot with "nomodeset" as your grub option

Edit the /etc/default/grub file 

```
gksudo gedit /etc/default/grub
```

and add the kernel parameter to the GRUB_CMDLINE_LINUX_DEFAULT="nomodeset quiet splash" line, then run:

```
sudo update-grub
```

---

### Post by techiewannabe on 2010-09-03
Davidmohhamed:

Thanks for your note. 
 
Forgive me, but I'm afraid I don't fully understand what you're suggesting. (I'm not very competent with the command line, yet.) I understand your directions in general. However, when it comes to adding a kernel parameter, I have no idea. Exactly, how do I put such an instruction into the terminal? Is there a specific command I should write? Is there a site that you suggest I read?
 
Thanks for your help.

---

### Post by davidmohammed on 2010-09-03
sure - 

from the menu choose

Applications --> Accessories --> terminal

Then type the commands shown (pressing the enter key at the end of the line to type)

The first command will display and editor with the file /etc/default/grub.  Just edit the line shown to contain those values.  Save the file

The type the next command (press enter).

When you have finished.  Reboot.

---

### Post by techiewannabe on 2010-09-04
Davidmohammed:

The good news is that your suggestion seemed to solve the problem, although I can't be certain until I've been using the computer it for a while. The bad news is much worse! My screen went black! I couldn't see my desktop. I couldn't see the Internet when I was trying to use Firefox. I could only see the bar across the top of the screen, and the bar along the bottom of the screen. I couldn't change the desktop image. I was able to open programs and see them. 

When I went back into the command line and reversed the commands that you suggested, everything went back to normal. 

I think your idea might be on the right track, but obviously I can't use the commands that we talked about. 

Any other ideas?

Thanks for your help.

---

### Post by davidmohammed on 2010-09-04
you might want to try and install the ATI proprietary driver instead of the opensource driver you are using.

See [here]("https://help.ubuntu.com/community/BinaryDriverHowto/ATI") for an explanation and how to identify if your graphics card is supported by ATI and its proprietary driver

In summary - see if there is a graphics hardware driver offered to you by System --> Administration --> Hardware drivers.

If there isn't, follow the guide to identify if your card is supported - if it is, there is a guide to download and install.

---

### Post by ajgreeny on 2010-09-04
I think you will be stuck with the ati/radeon open source driver for that card, and unfortunately it is less than brilliant since ubuntu 9.10 came along with its newer version of the xorg server.

There is just a chance that a different /etc/X11/xorg.conf file may help, though you will probably find that there is no such file at the moment.  If you add it manually it will be read and acted on at start of an x-session.  What is needed in the file, however, is more difficult to know.  I have an ati 9200SE card and here is my xorg.conf to use as a template; if it does not work just delete it and you will be back to the current situation.  Change the resolution figures to match your monitor, and check if the card is an AGP and comment out the AGPMode line and vendor and boardname perhaps, if needed, but the rest is worth a try.  Note this runs your x-session at 16 bit colour, which I find is better than 24 bit with these older ati cards.
```
# xorg.conf (X.Org X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# Note that some configuration settings that could be done previously
# in this file, now are automatically configured by the server and settings
# here are ignored.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

 Section "Device"
    Option        "EnableDepthMoves"    "True"
    Option        "EnablePageFlip"    "True"
    Option        "DMAForXv"        "True"
    Option        "AccelDFS"        "True"
    Option        "ColorTiling"        "True"
    Option        "RenderAccel"        "True"
    Option        "VGAAccess"        "True"
    Option        "AccelMethod"        "EXA"
    Option        "DRI"            "True"
    Option        "MigrationHeuristics"    "greedy"
    Option        "TripleBuffer"        "True"
    Option        "EXAOptimizeMigration"  "true"
    Option        "EXANoComposite"    "No"
    Option        "BackingStore"        "true"
    Option        "AGPMode"        "8"
    Identifier    "Card0"
    Driver        "radeon"
    VendorName    "ATI Technologies Inc"
    BoardName     "RV280 AP [Radeon 9200 PRO]"
EndSection

Section "Monitor"
    Identifier    "Configured Monitor"
            HorizSync    30-80
            VertRefresh    50-75
EndSection

Section "Module"
    Load  "dri2"
    Load  "dri"
    Load  "dbe"
    Load  "extmod"
    Load  "glx"
EndSection

Section "Screen"
    Identifier    "Default Screen"
    Monitor        "Configured Monitor"
    Device        "Configured Video Device"
    DefaultDepth    16
    SubSection "Display"
        Modes        "1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
EndSection

Section "Extensions"
    Option "RENDER" "Enable"
    Option "Composite" "True"
    Option "XVideo" "Enable"
    Option "XINERAMA" "False"
EndSection

Section "DRI"
    Mode        0666
EndSection

```

---

### Post by techiewannabe on 2010-09-04
Thanks to everyone for your suggestions. I decided to reinstall Jaunty which I had been using without trouble for quite a while.

---

