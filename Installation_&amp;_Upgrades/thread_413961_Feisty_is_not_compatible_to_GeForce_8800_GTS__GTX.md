---
title: "Feisty is not compatible to GeForce 8800 GTS / GTX"
date: 2007-04-19
forum: Installation &amp; Upgrades
---

### Post by redlabour on 2007-04-19
Not well done.

Feisty is not compatible to all GeForce 8800GTS/GTX.All you can do is using the Alternate ISO and manually upgrade X.

Good knows if this was happend to  Microsoft the Audience was laughing. This Bug is known for Weeks and as you can see not fixed :

[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-nv/+bug/91556](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-nv/+bug/91556)

---

### Post by redlabour on 2007-04-19
**Update:**

Works for me now after choosing manually the Resolution at Bootscreenmenu for LiveCD Modus.

But after HD Install the Problem resists. Why isnt Ubuntu LiveCD saving the Resolution to the HD Install like Knoppix does ????

---

### Post by Awperator on 2007-04-19
Sorry I'm a bit of a noob when it comes to ubuntu. I have an 8800gts, running feisty, and I enabled the restricted driver, but then when I rebooted X server crashed. I went to the Xserver, and I did a
sudo dpkg-reconfigure -phigh xserver-xorg
and I had to choose the vesa driver. I'm now running on that. How do I enable the Nvidia driver and not have Xserver crash? If you can please spell out the steps because I am noob. Thanks.

---

### Post by redlabour on 2007-04-19
> **Awperator said:**
> Sorry I'm a bit of a noob when it comes to ubuntu. I have an 8800gts, running feisty, and I enabled the restricted driver, but then when I rebooted X server crashed. I went to the Xserver, and I did a
sudo dpkg-reconfigure -phigh xserver-xorg
and I had to choose the vesa driver. I'm now running on that. How do I enable the Nvidia driver and not have Xserver crash? If you can please spell out the steps because I am noob. Thanks.

You can not - did you not read the Topic Description ???? 

**Feisty is [SIZE="6"]not compatible[/SIZE] to GeForce 8800 GTS / GTX**

:guitar: :lolflag:

---

### Post by marco999 on 2007-04-19
Yes u can just install it from the Nvidia website via the .run package.

After u remove ur restricted-modules-generic 2.6.20-15 package using synaptic

Marco999

---

### Post by redlabour on 2007-04-20
> **marco999 said:**
> Yes u can just install it from the Nvidia website via the .run package.

After u remove ur restricted-modules-generic 2.6.20-15 package using synaptic

Marco999

Every tried to run the nVidia Website without working X ??? :lolflag:

---

### Post by etherealremnant on 2007-04-20
Ever heard of not being a jerk about it?

If you change your driver to VESA as was previously offered, you can get to the nvidia website easily to get the new drivers.

Or if you're a pro, you can just use the application "links" at the console to browse to nvidia's website without graphics. What a concept.

---

### Post by redlabour on 2007-04-20
I did all of that -  after Rebooting the Screen is black after GRUB.

---

### Post by etherealremnant on 2007-04-20
Boot in recovery mode, then edit /boot/grub/menu.lst and remove the splash and quiet options from there.

---

### Post by etherealremnant on 2007-04-20
Well, I just made a clean install of Feisty from the live CD and I didn't have any problems when I rebooted. The splash worked and everything.

The automatic settings importer though didn't do jack garbage. It didn't import any of my firefox profiles. LAME!

---

### Post by pierre.s.rosen on 2007-04-20
I just installed Feisty this morning and I am having the same issue with my EVGA 8800 GTS card.  I'll have to tweak it manually.  These type of driver problems should NOT be an issue in a stable release of Ubuntu.  This is something which should work out of the box.  :confused: 

Oh, and my Firefox preferences weren't imported either.  One of my Gaim accounts was imported though, not all 4.

Also, my X-Fi sound card isn't supported by ALSA yet...*sigh*...

---

### Post by methinks on 2007-04-20
This isn't new, I've had that problem for a while now. If you use the nvidia drivers, it all goes very easily.

> **redlabour said:**
> Every tried to run the nVidia Website without working X ??? :lolflag:
it's called **wget** (I admit, you have to know the actual address before hand)

What you need to do is to install the **Build essentials**, download the nvidia drivers, then run the script that runs the installer

---

### Post by RawMustard on 2007-04-20
Well I had feist 32bit beta working with 8800gtx.  Tried to install 64bit feisty and get a black screen, can't do jack :(  So I install final feisty 32bit, now I can't get my 8800 to work at all with the nvidia driver.  tried both restricted manager and manually from  downloaded package.  I have a working xorg.conf file but it can't load the nvidia module!  This release of feist has been rushed I reckon!

---

### Post by Tine on 2007-04-20
Have you guys tried installing nvidia drivers with envy?
[http://www.albertomilone.com/nvidia_scripts1.html](http://www.albertomilone.com/nvidia_scripts1.html)

---

### Post by pierre.s.rosen on 2007-04-20
To clarify, my 8800GTS was working out of the box on both the Live CD and the initial install.  It was only when I tried to install the proprietary drivers that xorg crapped out on me.  This new highly tauted feature to quickly manage proprietary devices and blobs didn't work as advertised.  Boo...Hisss.

I have a feeling that there are lots of cutting edge, first adapters who are going to be mucho pissed off about this release of Ubuntu.  Is it :-({|= for Ubuntu?  Do I need to try out a new distro, after 2 years of Ubuntu-bliss?

---

### Post by frogotronic on 2007-04-20
> **etherealremnant said:**
> Well, I just made a clean install of Feisty from the live CD and I didn't have any problems when I rebooted. The splash worked and everything.

The automatic settings importer though didn't do jack garbage. It didn't import any of my firefox profiles. LAME!

mmmmm....if you did a clean install of Feisty Fawn, did you reformat/erase your former partition during the clean install?

-CH

---

### Post by d58e7 on 2007-04-20
I tried installing the nvidia driver manually through the console but I get a complaint saying the Kernal Source tree is missing, how do I fix this error?

---

### Post by RawMustard on 2007-04-20
you need to install the kernel headers for your kernel
check here for details. [http://www.nvnews.net/vbulletin/showthread.php?t=72490]("http://www.nvnews.net/vbulletin/showthread.php?t=72490")

---

### Post by methinks on 2007-04-20
> **d58e7 said:**
> I tried installing the nvidia driver manually through the console but I get a complaint saying the Kernal Source tree is missing, how do I fix this error?

assuming you're at the console when this happens, try
**sudo apt-get install build-essential**
This should install all the headers, compilers, tools that you need to do the install. Once that's done, you should be able to run the nvidia installer

---

### Post by d58e7 on 2007-04-20
> **methinks said:**
> assuming you're at the console when this happens, try
**sudo apt-get install build-essential**
This should install all the headers, compilers, tools that you need to do the install. Once that's done, you should be able to run the nvidia installer

I tried that and it tells me everything is up to date, but when I try to install the drivers it tells me it can't find the kernal source tree

---

### Post by Visceral Monkey on 2007-04-20
I can get it to boot up on my 8800gts with no problem..but nothing I do can get the 3d drivers to work. Can someone give us a short, numbered list of the steps required to get 3d working on the 8800 series of cards? I've tried every guide available with no luck...

---

### Post by mac.ryan on 2007-04-20
Just wishing to inform that the same problem (and the same solution as well!) apply for **nVidia GeForce Go 7950 GTX** running on 64 bit version (maybe also on 32, but 64 is what I am running on).

I am _far from blaming the devs_, yet this "restricted manager" had to be the *mighty fixer* for avoiding the scripting stuff... it's a pity.

---

### Post by RawMustard on 2007-04-20
Ok I just did a clean install of Ubuntu Feisty 32bit and got my 8800GTX working on the Nvidia Drivers from their site.  I uninstalled restricted packages, nvidia-glx and edited the file /etc/default/linux-restricted-modules with DISABLED_MODULES="nv"

I then rebooted to a terminal and made sure gdm wasn't running with, sudo /etc/init.d/gdm stop I then cd to my folder containing the nvidia driver and ran the file.  Everything was aok after I went through this.

Hope this helps some.

The restricted drivers manager is borked, don't use it!  Tried it twice with same results, broken system!

Just make sure you do what this page says and make sure x and gdm aren't running when you install the driver.

[http://www.nvnews.net/vbulletin/showthread.php?t=72490]("http://www.nvnews.net/vbulletin/showthread.php?t=72490")

---

### Post by etherealremnant on 2007-04-20
> **cement_head said:**
> mmmmm....if you did a clean install of Feisty Fawn, did you reformat/erase your former partition during the clean install?

-CH

I was talking about importing my settings off of the Windows drive.

Its never offered to import settings off another Feisty or Edgy install.

I wouldn't mind so much except now I have to remember how to get my Alt+S functionality back for sending posts on forums instead of opening the stupid history menu.

---

### Post by etherealremnant on 2007-04-20
Well I tried installing the native nVidia drivers...

I uninstalled the restricted modules from Ubuntu as well as the restricted manager, installed build-essential, and everything seemed to be alright when I ran the nvidia installer.

Well I finished it, rebooted, and it loads the module fine and everything (from looking at the X server log, everything loads) but then it can't find /sbin/lrm-video and dumps me back to console. Any ideas?

I edited my xorg.conf and put nv back in there for now... but I'd really like to have some acceleration going.

---

### Post by bbzbryce on 2007-04-21
See what I wrote in this thread regarding getting it to work:

[http://ubuntuforums.org/showthread.php?p=2503808&posted=1#post2503808](http://ubuntuforums.org/showthread.php?p=2503808&posted=1#post2503808)

For a quick recap I sucessfully installed the 64 bit version of Ubuntu using the Desktop install CD and have the NVIDIA drivers for my 8800 GTS working fine. The built in desktop effects don't show the title bars which is somewhat disappointing, but oh well.

---

### Post by shrisha on 2007-04-22
Hi everybody. Thisi is my first post. I'm complitely new bie in Linux. After few days of fighting with Ubuntu I finaly got working Nvidia driver for my 8800 GTX.
So, for this, first I used Envy script . Then, When I got message about bad luck, I did all recomendation. Like install kernel headers for my kernel and so on, you will see it. Then I took driver from Nvidia, downloaded by Envy, it will situated there \usr\share\envy\nvidia-graphics-drivers\NVIDIA-Linux-x86_64-1.0-9755-pkg2.run ,copied to my desktop and in recovery boot run nvidia driver. When Nvidia driver compile everything itself,  finaly I got this working. 
Within last few days, when I began my Linux journey, Always one question coming to my mind, Why everything is so complicated in Linux. :) I quite often use command line in windows but here it's little too much for me. Well, let see If I will stay with you guys. :) Anyway, it's a challenge for me, that's what I like it.

---

### Post by bbzbryce on 2007-04-22
The main reason why this is complicated is it's new hardware, and involves proprietary drivers. For us the install and boot required changing the default vesa command line which wont work for other people. Hopefully the next Ubuntu installer will work better for us 8800 and newer video card users but that's just kind of what happens with new hardware, its not always going to work perfectly.

---

### Post by lunaticitizen on 2007-04-23
hello guys, I'm a beginner in linux and I tried to install nvidia driver for my 8800 gtx from system -> administrator -> restricted driver managers.

However apparently it didn't work and my feisty won't boot anymore. Could you please tell me step by step to, at least, uninstall the nvidia driver and get back into ubuntu?

Since I am a beginner please be patient with me :) Thanks in advance...

---

### Post by frodon on 2007-04-23
> **bbzbryce said:**
> See what I wrote in this thread regarding getting it to work:

[http://ubuntuforums.org/showthread.php?p=2503808&posted=1#post2503808](http://ubuntuforums.org/showthread.php?p=2503808&posted=1#post2503808)

For a quick recap I sucessfully installed the 64 bit version of Ubuntu using the Desktop install CD and have the NVIDIA drivers for my 8800 GTS working fine. The built in desktop effects don't show the title bars which is somewhat disappointing, but oh well.I believe the nvidia-glx-new package (in the repositories) is made for this purpose as it contains the latest nvidia drivers.

[https://launchpad.net/ubuntu/gutsy/i386/nvidia-glx-new/1.0.9755+2.6.20.5-15.20](https://launchpad.net/ubuntu/gutsy/i386/nvidia-glx-new/1.0.9755+2.6.20.5-15.20)
[https://launchpad.net/ubuntu/gutsy/amd64/nvidia-glx-new/1.0.9755+2.6.20.5-15.20](https://launchpad.net/ubuntu/gutsy/amd64/nvidia-glx-new/1.0.9755+2.6.20.5-15.20)

The nividia site confirm that this version of the nvidia drivers supports 8800 GTS / GTX cards

For the window border problem add this in the device section of your xorg.conf file and it should be good :
```
Option "AddARGBGLXVisuals" "True"
```Don't forget to restart your xserver.

---

### Post by lunaticitizen on 2007-04-23
> **lunaticitizen said:**
> hello guys, I'm a beginner in linux and I tried to install nvidia driver for my 8800 gtx from system -> administrator -> restricted driver managers.

However apparently it didn't work and my feisty won't boot anymore. Could you please tell me step by step to, at least, uninstall the nvidia driver and get back into ubuntu?

Since I am a beginner please be patient with me :) Thanks in advance...

I found the solution by myself :redface:  Now I'm trying to install the driver again! :guitar: :lolflag:

---

### Post by lunaticitizen on 2007-04-23
> **frodon said:**
> I believe the nvidia-glx-new package (in the repositories) is made for this purpose as it contains the latest nvidia drivers.

[https://launchpad.net/ubuntu/gutsy/i386/nvidia-glx-new/1.0.9755+2.6.20.5-15.20](https://launchpad.net/ubuntu/gutsy/i386/nvidia-glx-new/1.0.9755+2.6.20.5-15.20)
[https://launchpad.net/ubuntu/gutsy/amd64/nvidia-glx-new/1.0.9755+2.6.20.5-15.20](https://launchpad.net/ubuntu/gutsy/amd64/nvidia-glx-new/1.0.9755+2.6.20.5-15.20)

The nividia site confirm that this version of the nvidia drivers supports 8800 GTS / GTX cards

For the window border problem add this in the device section of your xorg.conf file and it should be good :
```
Option "AddARGBGLXVisuals" "True"
```Don't forget to restart your xserver.

Well I tried to run the .deb file you provided but it gave me an error message ---> Error: Dependency is not satisfiable: nvidia-kernel-1.0.9755

Did I do something wrong? :confused:

---

### Post by frodon on 2007-04-23
The links i gave are just for informative purpose, to install this package just open synaptic and search nvidia-glx-new then install it or open a terminal and type :
```
sudo apt-get install nvidia-glx-new
```

---

### Post by lunaticitizen on 2007-04-23
> **frodon said:**
> The links i gave are just for informative purpose, to install this package just open synaptic and search nvidia-glx-new then install it or open a terminal and type :
```
sudo apt-get install nvidia-glx-new
```
Hello there. Thanks a lot for the solution. It worked! :) By the way I have some questions. How do I know that the driver has been enabled and is running now? When I checked in System --> Settings --> Desktop Effects (sorry I don't know the exact option in English since I'm using the Japanese edition of Ubuntu) , the driver was still inactive, and the computer asked me if I want to enable it.  

There were, indeed, two more options when I was in GRUB splash screen. The older two are the generic ones, I believe. I just feel that my computer is not as responsive as Vista (I'm also using Vista). Shouldn't Ubuntu be more responsive? :KS  I can feel it when I opened new tabs in firefox. It was quite slow, I think. Or is it because the driver is still in beta version?

Thanks in advance! :)

---

### Post by frodon on 2007-04-23
Firefox is a special case, it has always been a bit slow on linux and even on windows sometimes (just my opinion), try epiphany (the gnome web browser) you will be impressed how fast it is. About your kernel question i would say that in general it's better to use the generic kernel because it will use the architecture which fit the best you proscessor.

The first time you enabled the nvidia drivers your xorg.conf file (it's the one who describe your display config) should have been modifyed to use nvidia drivers, the command i gave you just installed you the latest nvidia drivers which introduce the support of 8800 GTS / GTX cards.

Anyway if you want to be sure that you have nvidia drivers enabled type this command and watch if you see this as output **Driver          "nvidia"**  : ```
cat /etc/X11/xorg.cong | grep -i nvidia
```

---

### Post by lunaticitizen on 2007-04-23
> **frodon said:**
> Firefox is a special case, it has always been a bit slow on linux and even on windows sometimes (just my opinion), try epiphany (the gnome web browser) you will be impressed how fast it is. About your kernel question i would say that in general it's better to use the generic kernel because it will use the architecture which fit the best you proscessor.

The first time you enabled the nvidia drivers your xorg.conf file (it's the one who describe your display config) should have been modifyed to use nvidia drivers, the command i gave you just installed you the latest nvidia drivers which introduce the support of 8800 GTS / GTX cards.

Anyway if you want to be sure that you have nvidia drivers enabled type this command and watch if you see this as output **Driver          "nvidia"**  : ```
cat /etc/X11/xorg.cong | grep -i nvidia
```

Thank you for such a fast response! :) I have typed the command you gave and indeed it gave me the Identifier and Device as Nvidia G80 :) 

Once again, thanks a lot for your help :KS

---

### Post by kaahen on 2007-04-23
Can someone please explain step by step how to configure the 8800GTX on Feisty?

I am noob, so please be as explicit as possible.

Thanks in advancce.

---

### Post by redlabour on 2007-04-23
> **kaahen said:**
> Can someone please explain step by step how to configure the 8800GTX on Feisty?

I am noob, so please be as explicit as possible.

Thanks in advancce.

[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

---

### Post by frodon on 2007-04-23
> **redlabour said:**
> [http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)Sorry but this is really the worst advice to give for a beginner to make him using envy and thus the nvidia installer, because it's sure that on next kernel update he will have a blue screen on reboot, most of beginners don't know that if they don't use the nvidia drivers of the ubuntu repositories they have to install again and again the nvidia drivers on each kernel update.

@kaahen, to install the latest nvidia drivers of the official ubuntu repositories open a terminal (Application > Accessories > Terminal) then paste and execute these commands :
```
sudo apt-get install nvidia-glx-new
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf_backup
sudo nvidia-xconfig --no-composite
```

---

### Post by redlabour on 2007-04-23
> **frodon said:**
> Sorry but this is really the worst advice to give for a beginner to make him using envy and thus the nvidia installer, because it's sure that on next kernel update he will have a blue screen on reboot, most of beginners don't know that if they don't use the nvidia drivers of the ubuntu repositories they have to install again and again the nvidia drivers on each kernel update.

@kaahen, to install the latest nvidia drivers of the official ubuntu repositories open a terminal (Application > Accessories > Terminal) then paste and execute these commands :
```
sudo apt-get install nvidia-glx-new
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf_backup
sudo nvidia-xconfig --no-composite
```

He has a 8800GTX - Envy is the only Option he can use this Time. Read Launchpad and the Bugtracker. ;)

[https://bugs.launchpad.net/envy/+bug/108734](https://bugs.launchpad.net/envy/+bug/108734)

[https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/107831](https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/107831)

---

### Post by frodon on 2007-04-23
Go to nvidia site, chose graphic drivers > Geforce 8800 series > linux x86 and you get the 1.0-9755 nvidia drivers aka the nvidia-glx-new package.

[http://www.nvidia.com/content/drivers/drivers.asp](http://www.nvidia.com/content/drivers/drivers.asp)

So no need to go outside the repositories except in case of specific problems.

---

### Post by redlabour on 2007-04-23
> **frodon said:**
> Go to nvidia site, chose graphic drivers > Geforce 8800 series > linux x86 and you get the 1.0-9755 nvidia drivers aka the nvidia-glx-new package.

[http://www.nvidia.com/content/drivers/drivers.asp](http://www.nvidia.com/content/drivers/drivers.asp)

So no need to go outside the repositories except in case of specific problems.

Which Part of the Launchpad Bugtracker did you not understand???

> **redlabour said:**
> He has a 8800GTX - Envy is the only Option he can use this Time. Read Launchpad and the Bugtracker. ;)

[https://bugs.launchpad.net/envy/+bug/108734](https://bugs.launchpad.net/envy/+bug/108734)

[https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/107831](https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/107831)

---

### Post by frodon on 2007-04-23
redlabour, don't mix all the things, you have a problem with your 8800 GTX but this bug has been fixed and many users are now fine with their 8800 series card, so no need to answer someone asking instructions to configure his/her 8800 card by envy without giving any warnings neither explaining how it works.
Most users are more likely to not have problems with the nvidia-glx-new packages, for those who still have envy is a good option indeed but not the first choice for a beginner especially without any explanation on what happen when there's a kernel update.

Now if you want to link launchpad bug tracker, i guess you know this one (you posted inside) which shows that the fix has been commited (even if you still have problems) and that the devs have handled this issue :
[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-nv/+bug/91556](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-nv/+bug/91556)

---

### Post by redlabour on 2007-04-23
> **frodon said:**
> redlabour, don't mix all the things, you have a problem with your 8800 GTX but this bug has been fixed and many users are now fine with their 8800 series card,

Ok - i let you waste the Time of other without Envy. BTW - the Bug has fixed in the last 2 Hours ? Wow - Link ??? :popcorn:

What you have linked is the Bug at the Bootscreen. Not the 3D Bug. 

[nvidia-glx-new NVidia driver missing libwfb](https://launchpad.net/ubuntu/+source/linux-restricted-modules-2.6.20/+bug/98641)

---

### Post by kaahen on 2007-04-24
Sorry, as I told you I am beginner, I don't understand the links you indicated to me I mean Envy and so on, I just followed the instructions you told me before, that is:

sudo apt-get install nvidia-glx-new
...
sudo nvidia-xconfig --no-composite

When I restarted I had these problems:

- Failed to start the X server
- Failed to load module "wfb" (it doesn't exist)
- NVIDIA(0): Need libwfb but wfbScreenInit not found
- Fatal server error: Addscreen /ScreenInit failed for driver 0

And after that the only thing I can do is restarting manually the computer. I reseted in recovery mode and I replace de xconf_backup.

Please if you can explain what is Envy and how I can use it to configure my card as simple as possible would be nice.
Or maybe you suggest that I wait till a easier way of configuring comes up.

Thanks in advance

---

### Post by redlabour on 2007-04-24
> **kaahen said:**
> 
- Failed to start the X server
- Failed to load module "wfb" (it doesn't exist)
- NVIDIA(0): Need libwfb but wfbScreenInit not found
- Fatal server error: Addscreen /ScreenInit failed for driver 0

And after that the only thing I can do is restarting manually the computer. I reseted in recovery mode and I replace de xconf_backup.

Please if you can explain what is Envy and how I can use it to configure my card as simple as possible would be nice.
Or maybe you suggest that I wait till a easier way of configuring comes up.

Thanks in advance

Yes and this is excactly the Problem i mean before.

Go here and try again with this Module if you use the 32bit Version of Ubuntu : 

[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-nv/+bug/91556/comments/25](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-nv/+bug/91556/comments/25)

---

### Post by methinks on 2007-04-24
My problem isn't to get the driver working, but to **keep** it working.
I can install the driver from the console without a problem, using nvidia's installer. From there, I can then use gnome normally. The problem is that the fix disappears as soon as I reboot, meaning I have to go through the hassle every time I start my computer.

Gonna try removing the "restricted" manager when I get home, would that do it?

---

### Post by redlabour on 2007-04-24
> **methinks said:**
> My problem isn't to get the driver working, but to **keep** it working.
I can install the driver from the console without a problem, using nvidia's installer. From there, I can then use gnome normally. The problem is that the fix disappears as soon as I reboot, meaning I have to go through the hassle every time I start my computer.

Gonna try removing the "restricted" manager when I get home, would that do it?

Which Errormessage appears when it is not working after Reboot?

---

### Post by methinks on 2007-04-24
I'll write it down next time it happens, but I believe that it tells me that there are no screens found.

---

### Post by kaahen on 2007-04-25
Noob question, but,in the link you indicated me there's this:

[http://users.tkk.fi/~tjaalton/dpkg/xserver-xorg-video-nv_2.0.2-1ubuntu0_i386.deb](http://users.tkk.fi/~tjaalton/dpkg/xserver-xorg-video-nv_2.0.2-1ubuntu0_i386.deb)

You mean that I have to download and execute it, restart and I will have my card well configurated?. I did it with Envy and didn't work.

I installed this program, I tried the Desktop effects and didn't work. Is that what I had to do?

Thanks for your support.

---

### Post by noenter1 on 2007-04-29
This is how i installed the driver:
After it gives me the x error it goes to the terminal. I login and do the following(only difference is i had already downloaded the driver) Download the nvidia driver into in you home folder using: ```
 wget http://us.download.nvidia.com/XFree86/Linux-x86/1.0-9755/NVIDIA-Linux-x86-1.0-9755-pkg1.run 
```  then type: ```
 sudo sh NVIDIA-Linux-x86-1.0-9755-pkg1.run -n -s --x-prefix=/usr/lib/xorg/ --kernel-source-path=/usr/src/linux-headers-`uname -r` 
```
Make sure you use `(button above the tab button) not ' around uname r. Let the installer configure your xorg.conf. Then you can either restart your computer(ctrl+alt+del) or start X(by typing X).

---

### Post by kaahen on 2007-04-29
Thanks a lot, that really worked.

---

### Post by noenter1 on 2007-04-29
No problem, glad I could help.

---

### Post by Strofcon on 2007-04-30
This is what I ended up having to do in order to have a bootable Ubuntu along with acceleration. 
Beware, this is a looong post! I tried to give as much detail as possible (probably more than necessary in some places) so that newbies like myself don't get lost!

NOTE: This is MY situation - I do not claim that this will be the best, or even a suitable solution for ALL cases of problems with Feisty and 8800 cards!

I'll try my best to give credit where it's due for the following fixes and such. If I miss someone, let me know. :-)

I have an EVGA 8800 GTS 320MB, and running a Core 2 Duo E6400, so this is all done with the x86_64 version of Feisty. :-)


First, I had to boot into recovery mode and edit the grub boot file as follows:
sudo nano /boot/grub/menu.lst
Then scroll down until you find the line that reads: ####End Default Options##
On the line that reads something similar to "kernel /boot/vlminuz...."
Delete "quiet splash" from the end of the line.
Then (on my machine) I had to enter a display mode between 1 and 6 (they have different values associated with them, but you have to enter the mode number in my case.) I used 6.
Before:
  kernel /boot/vmlinuz-2....... ro quiet splash
After: 
  kernel /boot/vmlinuz-2....... ro 6
(Thanks bbzbryce - This Thread)


This got me to my desktop.
Now time to make sure I have everything the NVidia drivers will need when I go to install them.
This is actually from here: [[COLOR="Red"]Fix nVidia acceleration in Feisty (8800 and Legacy)[/COLOR]]("http://ubuntuforums.org/showthread.php?p=2539048") (Top post)
sudo apt-get install build-essential
sudo apt-get install xserver-xorg-dev

Now, time to edit the restricted modules file...
sudo nano /etc/default/linux-restricted-modules-common
Change the line that reads DISABLED_MODULES=""  to DISABLED_MODULES="nv"

Time to reboot and hope everything remains somewhat functional!

Now it was time to get the drivers and install them. THIS IS NOT THE END! Seems like it should be, but it wasn't for me, so just keep reading. :-)
First download them...
```
wget http://us.download.nvidia.com/XFree86/Linux-x86_64/1.0-9755/NVIDIA-Linux-x86_64-1.0-9755-pkg2.run
```
(Of course you should find out the correct URL beforehand, as it may have changed)

To run the installer, you need to be in a console and kill the Xserver. Hit Ctrl-Alt-F2 to load up a console, log in, and then type:
sudo /etc/init.d/gdm stop
This kills X.

Now... in the directory that you downloaded the driver to...
sudo sh NV*

This will prompt you for some stuff, just answer yes to the kernel module stuff, and it will likely tell you it can't find a precompiled version. It will then try to compile one for you, which you should allow. It will spit out some more stuff, and then ask if you want to let the installer modify your xorg.conf file. Tell it yes!!!

Now you should be in the clear! Right? Wrong!
Upon rebooting, you'll likely be confronted by an XServer crash. It will say something along the lines of "Can't find the nVidia module!!! The world is going to END!!!" (Maybe a bit more toned down than that) Not to worry though!!!

First off, your original xorg.conf file is backed up and saved as xorg.conf.backup (or something similar) so if you lose faith in me now and want to revert back to having your simple desktop, you can just swap the files and you'll be ok again. (It acts like the drivers never ran through their installer if you get rid of the modified xorg.conf and use the original.)

Now, the final fix (for me) was actually just a small note by eyelessfade in this thread... He mentioned, somewhat glibly, that the 8800 series needs the nvidia-glx-new package. I had nothing else to lose, so I booted into recovery mode and ran:
apt-get install nvidia-glx-new

Perfect! Suddenly I could boot without fail! No black screen, no X crash. I guess it pays to read EVERY post in the thread. :-)

NOW... Finally, the problems are starting to wane. One change remained for me, and that was to suppress some of the 43 miles of output I saw on the screen when I booted. So I changed my /boot/grub/menu.lst file back to it's original state, BUT... it still leaves me with a blank screen and no boot. The best I can figure is that the splash option is just... I dunno. Won't go there!

Anyways, I finally decided to change that line to read:
kernel /boot/vmlinuz-2....... ro quiet 6

This suppressed some of the boot text, and still lets everything run just fine. Desktop Effects and all! :-)


Again, this worked for me, and won't work for everyone. I did all of these things as a last ditch effort, because doing all of the above-recommended things by themselves (or in any other combination) left me with a horribly broken Ubuntu which had to be reinstalled. Don't know why it worked this way, but I'm glad it did! Anyways take what you can from it. Enjoy!

---

### Post by CaptSaltyJack on 2007-04-30
I'm lost on this, guys.

I've got a PC with two 8800GTS cards linked via SLI.

I boot the Feisty desktop CD, and it won't even load the installer.  X bombs out on me.  I try safe graphics mode, and eventually I just get a black screen.

PS: This is a fresh install on an empty HD.

---

### Post by Strofcon on 2007-04-30
When you boot from the disk, it should bring up the menu for "Run/Install Ubuntu" or something, followed by the safe graphical mode, blah blah blah. Sounds like that's working, so you need to look at the bottom of the screen, and where it says "F* VGA" (I forget if it's F4 or F5), hit that key. Then choose the very bottom option, and that should let you then select the "Install" option in the main menu, then boot into the LiveCD version to run the installer.

Wow... that probably doesn't make any sense. Let me know...

---

### Post by CaptSaltyJack on 2007-04-30
Nope, still doesn't work.  X crashes on me still, after changing VGA to 1024x768x32

---

### Post by Strofcon on 2007-04-30
Ok. Let me think on it a bit. I have a final in about 15 minutes so I have to start getting to class, but if I come up with any ideas I'll let you know.

---

### Post by CaptSaltyJack on 2007-04-30
Thanks, much appreciated :)

---

