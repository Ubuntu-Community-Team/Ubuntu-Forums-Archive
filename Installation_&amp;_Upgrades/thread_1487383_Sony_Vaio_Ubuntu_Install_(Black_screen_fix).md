---
title: "Sony Vaio Ubuntu Install (Black screen fix)"
date: 2010-05-18
forum: Installation &amp; Upgrades
---

### Post by atreides8081 on 2010-05-18
I had some difficulty installing Ubuntu 10.04 onto a Sony Vaio notebook. The screen would go black while loading.  Here is how I fixed the problem.

Sony Vaio S Series.  VPCS117GG  (PCG-51111W)
(Should also fix problems on similar notebooks with NVIDIA graphics cards)

The basic problem is that the display driver does not recognise the display somehow and it all turns to custard.  If you can boot in text modes and run with vesa drivers you can get started, then apply the work around later.  

Here's how I did it...
(I dont understand all this, it just happened to work, someone might be able to explain)

1. When the cd loads press F6 to change other options.  'quiet splash' needs to be replaced with 'nomodeset' in the boot options.  When it loads install ubuntu as normal.  (Try 'single nomodeset i8042.nopnp' if it doesnt work, the aim is to get x started in low res).

2. After installation on first boot change boot options. Try 'single nomodeset i8042.nopnp'.  It should boot to a menu. Select to continue booting until you get a command prompt. (or load x in low res)  

3. You need the file attached.  Download or copy to /etc/X11/

4. Rename file to sony.bin

5. Install the latest nvidia driver.  (I got it from nvidia web site, i'm not sure if the one already included is ok, you may be able to skip this)

6. Edit /etc/X11/xorg.conf.  Find the section and add the 2 options lines to the device lines.
```

Section "Device"
   Identifier          "Device0"
   Driver              "nvidia"
   VendorName         "NVIDIA Corporation"
   Option             "ConnectedMonitor"   "DFP-0"
   Option             "CustomEDID"          "DFP-0:/etc/X11/sony.bin"
EndSection

```

7. Restart the xserver and see if all is ok.  (should see the nvidia logo on load).

8. Set your system to always load with the boot option 'nomodeset', so it doenst crash on load, instead of 'quiet splash'.

Some people around here I am sure can explain some of this better if anyone has questions, but I thought it might be a starting point for users like me who were stuck for a couple of days.  (most of this info I got from different posts on this and other sites, relating to different notebooks and put it all together).  

Hopefully an update soon will fix all of this.

---

### Post by atreides8081 on 2010-05-21
And this fixes the sound on the same Sony Vaio


```

sudo add-apt-repository ppa:ubuntu-audio-dev/ppa
sudo apt-get update
sudo apt-get install linux-alsa-driver-modules-$(uname -r)

```

and reboot.

(it worked for me on a sony vaio.)

---

### Post by Vinnare on 2010-05-22
> **atreides8081 said:**
> I had some difficulty installing Ubuntu 10.04 onto a Sony Vaio notebook. The screen would go black while loading.  Here is how I fixed the problem.

Sony Vaio S Series.  VPCS117GG  (PCG-51111W)
(Should also fix problems on similar notebooks with NVIDIA graphics cards)

The basic problem is that the display driver does not recognise the display somehow and it all turns to custard.  If you can boot in text modes and run with vesa drivers you can get started, then apply the work around later.  

Here's how I did it...
(I dont understand all this, it just happened to work, someone might be able to explain)

1. When the cd loads press F6 to change other options.  'quiet splash' needs to be replaced with 'nomodeset' in the boot options.  When it loads install ubuntu as normal.  (Try 'single nomodeset i8042.nopnp' if it doesnt work, the aim is to get x started in low res).


**I don't understand this **:Try 'single nomodeset i8042.nopnp' if it doesnt work, the aim is to get x  started in low res. **What I did was to put in the CD, kept pressing F6 till the installation screen appeared (without pressing F6 even that wouldn't appear! :()**. **Then in the installation screen I changed the F6 option to 'nomodeset'**. [B]Then I proceeded to run the LIVE version just to check if the OS started and it did. There I started the installation which completed without a hiccup. But after reboot (once the CD is out)everything is fine till the Grub loads, after that the same black screen appears! I don't understand how to fix it. In fact I don't understand your second point below-

[/B]>  
2. After installation on first boot change boot options. Try 'single nomodeset i8042.nopnp'.  It should boot to a menu. Select to continue booting until you get a command prompt. (or load x in low res)  

**How to change the boot options on the first boot after installation?:confused: Mine simply boots to black screen,. Do I have to boot in recovery mode? Please help, I too have a Sony VAIO CW26FG. Could you please post some screen shots? That might help.**
> 
3. You need the file attached.  Download or copy to /etc/X11/

4. Rename file to sony.bin

5. Install the latest nvidia driver.  (I got it from nvidia web site, i'm not sure if the one already included is ok, you may be able to skip this)

6. Edit /etc/X11/xorg.conf.  Find the section and add the 2 options lines to the device lines.
```

Section "Device"
   Identifier          "Device0"
   Driver              "nvidia"
   VendorName         "NVIDIA Corporation"
   Option             "ConnectedMonitor"   "DFP-0"
   Option             "CustomEDID"          "DFP-0:/etc/X11/sony.bin"
EndSection

```7. Restart the xserver and see if all is ok.  (should see the nvidia logo on load).

8. Set your system to always load with the boot option 'nomodeset', so it doenst crash on load, instead of 'quiet splash'.

Some people around here I am sure can explain some of this better if anyone has questions, but I thought it might be a starting point for users like me who were stuck for a couple of days.  (most of this info I got from different posts on this and other sites, relating to different notebooks and put it all together).  

Hopefully an update soon will fix all of this.

---

### Post by atreides8081 on 2010-06-02
Can you see the GRUB menu?  When your computer first starts?

If so press 'e' to edit the command.  change 'quiet splash' to 'single nomodeset i8042.nopnp'.

This should help you get to a command prompt, or load X in a simple mode.  Follow the other steps to configure the graphics driver.  Once you get the graphics diver working and saved in this mode, you should always boot with the 'nomodeset' option, but you can leave 'quiet splash' there so it looks pretier when it boots.  (You can configure this as a permanent change)

(Sorry I'm not an expert I fumbled my way through this myself).

---

### Post by rootie on 2010-06-11
Just want to say thanks for your post, Atreides. But it seems my Vaio has more problems than that... After I got it to load the USB installer once (with your fix), it started throwing this strange error about stdins and all. Add to that the mess Sony made of their partitions... 

Anyway, now I am now happily dual-booting with Karmic. Doesn't pay to be on the bleeding edge, haha. Hope it worked out for you and everyone else.

---

### Post by mrtappy123 on 2010-07-03
Hi atreides8081 and anyone else who can help,

I'm having some problems installing Ubuntu 10.4 on my old Sony Vaio along side Windows XP. It seems the be the same problem you have had as when you click "install" or "try..." it loads up the splash (loading screen) and then just goes to a blank screen and the disc appears to stop.

I have followed your steps but am having some problems. 

Your first step,


> 1. When the cd loads press F6 to change other options. 'quiet splash' needs to be replaced with 'nomodeset' in the boot options. When it loads install ubuntu as normal. (Try 'single nomodeset i8042.nopnp' if it doesnt work, the aim is to get x started in low res).


I don't know if I did this step right; what i did was to load the CD in the drive. When the computer loads up, the menu with install options appear. Then i clicked F6 as you said and a menu in the corner opens with many options, also the "boot options", a command line sort of thing, became editable at the bottom. It is here that I saw that the last part of the code was quiet splash. So I then replaced 'quiet splash' with 'nomodeset' and i also have tried with 'single nomodeset i8042.nopnp' on another instants. The screen then shows a load of code, which  I suppose is the stuff thats normally hidden by the loading screen. Then it freezes (or appears to) with the bottom line being... Infact here is a photo showing the the screen...
> Here is a photo: [[IMG]http://img31.imageshack.us/img31/6266/imag0017aw.th.jpg[/IMG]](http://img31.imageshack.us/i/imag0017aw.jpg/)
Im not sure if this is what i'm waiting for or whether something has gone wrong. im really having difficulty understanding the continuing steps from here.

you say > the aim is to get x started in low res I don't understand what X is although i assume its like a 0pen command panel? well nothing like that opens, and nothing has ever installed on the hard drive that i can view through windows?

later you go...
> 3.You need the file attached. Download or copy to /etc/X11/

4. Rename file to sony.bin

I assume this means that Ubuntu must be installed by this point. In my case it hasn't installed on the first step so i think there is a issue.

Any help would be greatly appreciated
Regards and looking forward to a response

---

### Post by chrisdk on 2010-07-18
Hey there,

These steps have been a great help, but I am stuck at one point, as being a Linux newbie is not helping me too much. :-(

I switched the quietsplash to single nomodeset i8042.nopnp and the laptop booted to the recovery console, and i hit resume normal booting. I got to the command prompt, but I now have no clue as to how to load the new drivers

"2. After installation on first boot change boot options. Try 'single nomodeset i8042.nopnp'. It should boot to a menu. Select to continue booting until you get a command prompt. (or load x in low res) 

3. You need the file attached. Download or copy to /etc/X11/

4. Rename file to sony.bin"

Between Steps 2 and 3, what do i need to do to get files from online, move them to specific places etc? Any help is much apprecited, apologies for my noobness.

This is where I am at - 

[IMG][[IMG]http://img35.imageshack.us/img35/5228/1004140.th.jpg[/IMG]](http://img35.imageshack.us/i/1004140.jpg/) Uploaded with [ImageShack.us](http://imageshack.us)[/IMG]

OK - so I got into Ubuntu ok by using failsafe graphics mode, but I cannot paste the sony.bin file into the x11 folder, as I don't have permission. I have read lots about root user and root settings, but can't seem to find any options that let me paste this file.

---

### Post by atreides8081 on 2010-07-27
Sorry I'm no expert, but I fumbled my way through this myself.

If you just need permission to copy the file to that location just put 'sudo' in front of the copy command so it executes as the root user.

When I did this I was in graphics mode, just in lo res.  I copied of an SD card, but I am sure there is heaps of different ways to do it.

---

### Post by chrisdk on 2010-07-27
Thanks for the help. I figured it out after much googling, I imagine this is a typical Linux learning curve.

---

### Post by Niky Di Vito on 2010-08-26
I have a Sony Vaio Z with HDSS 250 and I had to install Ubuntu 10.10 because, I think for the particularity of the RAID, in no way I was able to install Ubuntu 10.04. Obviously I met problems of black screen that for now I resolved with the "single nomodeset practice" in low resolution; neither the other way explained above, trought "customedid" solved the problem. There'is some also attempt to try?
Thanks

---

### Post by mdegale on 2010-09-26
@[atreides8081]("http://ubuntuforums.org/member.php?u=1078054") Thanks very much for this - worked perfectly on my Sony Vaio S Series VPCS116FG .  I'd been working off a default config for nearly a month having failed to get the config right from all the other posts. Thanks for pulling it together.

---

### Post by saliflo on 2010-10-08
This has been working 10.04 and 10.10 alfa, beta till nvidia upgrade. I can'y solve black screen problem after last update. Do u have any actual solution?

---

### Post by b8e5n on 2010-10-11
To fix the problem on the final version of mavericks, beceause i've seen that it was installing the version 260 of the nvidia drivers, i reinstalled the version 256 from the official website, and now it works again! :)

---

### Post by saliflo on 2010-10-11
b8e5n, could you give detailed explanation. I can't get it.

---

### Post by b8e5n on 2010-10-11
It is quite simple, just go on the official website of nvidia, go to driver download page, chose your video card and your linux distribution (x86 or x64), then download it (my version is 256.53). You are going to have a .run file which is a a shell script. You cannot directly run it under the X. So you need to restart the computer, then when you are in the grub, choose the recovery boot option. Then choose continue starting, and you will be in the shell without going in the X. The just run the command "sudo sh $HOME/Downloads/NVIDIA-Linux-x86_64-256.53.run" (depending where is the file). Then just follow the instructions, click continue, etc. It will ask you about driver removal, just agree, and after the installation you can run normally, and if you have done the previous settings for the EDID, it should work directly.
Good luck

---

### Post by 3tareh on 2010-10-15
hi,
you said: 
you should always  boot with the 'nomodeset' option, but you can leave 'quiet splash' there  so it looks pretier when it boots.  (You can configure this as a  permanent change)

how can i configure this as a permanent change?

---

### Post by b8e5n on 2010-10-15
I don't know why he said that we should always boot with the grub option "nomodeset", because for me it is working fine, but it  easy to change that permanently:
edit the "/etc/grub/default" file (as root) and in the line starting with "GRUB_CMDLINE_LINUX_DEFAULT=" add "nomodeset" after "quiet splash".
then "sudo update-grub2"

---

### Post by lakerssuperman on 2010-10-15
Hello,

I am trying to get a Sony VPCCW17FX to work with the NVIDIA DRIVERS.  It has a G210m chip.  Anyone have any experience with this fix and this model?


EDIT: This solution does seem to work.  I can't say that I'm thrilled by the fact that this doesn't "just work" but thank you very much for the solution.  Stay classy.

---

### Post by saliflo on 2010-10-20
> **b8e5n said:**
> It is quite simple, just go on the official website of nvidia, go to driver download page, chose your video card and your linux distribution (x86 or x64), then download it (my version is 256.53). You are going to have a .run file which is a a shell script. You cannot directly run it under the X. So you need to restart the computer, then when you are in the grub, choose the recovery boot option. Then choose continue starting, and you will be in the shell without going in the X. The just run the command "sudo sh $HOME/Downloads/NVIDIA-Linux-x86_64-256.53.run" (depending where is the file). Then just follow the instructions, click continue, etc. It will ask you about driver removal, just agree, and after the installation you can run normally, and if you have done the previous settings for the EDID, it should work directly.
Good luck

Thanks, it works

---

### Post by khoi0107 on 2010-10-24
Hi guys !!! 
Recently I install ubuntu 10.10 on my Sony Vaio laptop. After the CD  boot I always got a black screen, after a week i figured that there's  nothing wrong, it's just the screen doesnt show up on my laptop's  screen. So I use an external monitor and [COLOR=Red]**It showed up as normal.**[/COLOR]
 
But I cant stay this way, I need to have it show up on my laptop's creen.
I tried to use "additional driver" to activate latest Nvidia driver but  after that even my external monitor doesnt work too. Latest driver  doesnt work properly i guess.
I did try to install older driver version manually but after I turned of  gdm, install driver and reboot, my ubuntu always starts with tty1  command terminal. tried ctrl+alt+7 but it stucked at (checking battery  state), startx doesnt help me return to graphical screen too.

I got help from a moderator here but the best result so far  is to edit my /etc/default/grub. Change
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash" 
to
GRUB_CMDLINE_LINUX_DEFAULT="nomodeset"
Sudo update-grub
after the reboot I have it shows up on my laptop's screen. But it seems  low-bit color,a bit grand to me(compared to external monitor, both w/o  driver). Anw i checked system/preference>monitor . It showed up that  my monitor:unknown. I can't choose other resolutions, refresh rate = 0. 
[IMG]http://img87.imageshack.us/img87/7461/testll.jpg[/IMG]

I always know its my widescreen is the problem. I have had a lot of  problems dealing wgames/application (on windows) can't work on 16:9  mode.  
 The external monitor is 5:4 screen ithat's why it can work, i guess
Can anybody help me install a stable Nvidia driver, or help my ubuntu to recognize my monitor plz

I've tried 2 weeks for this and Im hopeless now, I'm newbie so sorry for any dump question :sad:. Everything I tried in the past weeks is in here [http://ubuntuforums.org/showthread.php?t=906865&highlight=khoi0107&page=13](http://ubuntuforums.org/showthread.php?t=906865&highlight=khoi0107&page=13)
Sorry for my English, Im not native spearker :sad: 
**My laptop is SONY VAIO VPCCW19FX, Nvidia GeForce GT 230M, widescreen monitor**
Plz help

---

### Post by yankee-whiskey on 2010-11-16
Hi, I just got the same problem with yours --exactly the one you are suffering and i have now fixed it after googling.
Here's the procedure:

1. Download sonycw.txt and rename to sonycw.bin (you can find it at [http://forum.ubuntu.org.cn/viewtopic.php?t=261463](http://forum.ubuntu.org.cn/viewtopic.php?t=261463)  A command of Chinese will help)

2. Copy sonycw.bin to /etc/X11  (You should be root)
3. if xorg.conf has already in the /etc/X11,
       then:
       cover the orginal PART with:
       Section "Device"
       Identifier "Device0"
       Driver "nvidia"
       VendorName "NVIDIA Corporation"
       Option "ConnectedMonitor" "DFP-0"
       Option "CustomEDID" "DFP-0:/etc/X11/sonycw.bin"
       EndSection

    if you do not have xorg.conf,
       then create one and save these into your file:

       Section "Screen"
       Identifier	"Default Screen"
       DefaultDepth	24
       EndSection

       Section "Module"
       Load	"dri"
       Load	"GLcore"
       EndSection

       Section "Device"
       Identifier "Device0"
       Driver "nvidia"
       VendorName "NVIDIA Corporation"
       Option "ConnectedMonitor" "DFP-0"
       Option "CustomEDID" "DFP-0:/etc/X11/sonycw.bin"
       EndSection


4. search and install nvidia-gx-185-dev in the synaptic package manager
5. reboot and goood luck!


Translated from Chinese to English, original site: [http://forum.ubuntu.org.cn/viewtopic.php?t=261463](http://forum.ubuntu.org.cn/viewtopic.php?t=261463)

---

### Post by porolycapa on 2010-12-12
Here is my solution to the same problem:

[http://ubuntuforums.org/showthread.php?p=10231010#post10231010](http://ubuntuforums.org/showthread.php?p=10231010#post10231010)

---

### Post by codegrinder on 2011-02-12
I have the same problem with Ubuntu 10.10 x86_64 and Sony Vaio VPCS11V9R. Managed to make it work with nv &#1076;&#1088;&#1072;&#1081;&#1074;&#1077;&#1088; and EDID solution, still no nvidia drivers for 310M from official nvidia website managed to work. System / Administration / Additional drivers didn't work either. Could anyone help?

---

