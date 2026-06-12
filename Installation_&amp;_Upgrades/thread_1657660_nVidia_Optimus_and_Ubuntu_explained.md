---
title: "nVidia Optimus and Ubuntu explained"
date: 2011-01-01
forum: Installation &amp; Upgrades
---

### Post by 3602 on 2011-01-01
-------[B]
[COLOR=Red]Incoming transmission
UPDATE[/COLOR][/B] 05 September 2011
It would seem like someone is getting Optimus functional on Ubuntu Linux. See here:
[https://launchpad.net/~bumblebee/+archive/stable](https://launchpad.net/~bumblebee/+archive/stable)
**[COLOR=Red]END UPDATE[/COLOR]**
**[COLOR=Red]End of transmission[/COLOR]**
-------
**First, all thanks go to Ubuntu China** ([http://forum.ubuntu.org.cn/viewtopic.php?f=42&t=298495](http://forum.ubuntu.org.cn/viewtopic.php?f=42&t=298495)).
-------
**1. What is nVidia Optimus?**
With Optimus, the system switches between the integrated (graphics) card and the independent card, so the user can obtain high performance by using the independent card, while a longer battery life can be obtained by using the integrated card. 

** 2. How it works (in a nutshell)**
*High perf*: Integrated + Independent. The independent card is responsible for calculations, and the integrated card is responsible for actually displaying the info from the GRAM.
*Low perf*: Integrated only. In this mode, the integrated card is responsible for both the calculations and the displaying.

In fact, the real displaying part is done solely by the integrated card, which means **there is no way to use only the independent card**, and **there is no way to disable the integrated card**. **It is impossible, either by software or by hardware, to actually switch between the two cards.**

To those of you looking for drivers for Optimus: [COLOR=Red]**STOP**[/COLOR]. Just STOP. The newer nVidia Linux drivers, such as the 260.## release, are for _purely independent cards_, **NOT FOR DUAL-CARDS** (Optimus).

**[COLOR=Red]Worse news[/COLOR]**: [http://www.nvnews.net/vbulletin/showpost.php?p=2183477&postcount=2](http://www.nvnews.net/vbulletin/showpost.php?p=2183477&postcount=2)

** So what to do?**

After a fresh, clean install of Ubuntu,[COLOR=Red]** DO NOT INSTALL THE RESTRICTED DRIVER**[/COLOR]. Check whether your computer is running Optimus. If it isn't explicitly shown on the outer casing (as in my case), run:
```
lspci | grep VGA
```If you have such an output or similar, showing both an Intel card and an nVidia card:
```
00:02.0 VGA compatible controller: Intel Corporation Core Processor Integrated Graphics Controller (rev ##)
02:00.0 VGA compatible controller: nVidia Corporation Device #### (rev ##)
```_You're humped_. Again,**  DO NOT INSTALL THE RESTRICTED DRIVER**. Basically just flat-out don't install any drivers. The system runs the integrated card fine, as as long as Modern Warfare II isn't ported onto Ubuntu you should be fine. My i3-370M + GT 420M runs Tux Racer mighty smooth.

You may, however, be able to find some graphics card switching options in your computer's BIOS. You will need to check your own BIOS. If no switching options are present, then you may be able to switch off the nVidia card to save some juice: [http://linux-hybrid-graphics.blogspot.com/2010/07/using-acpicall-module-to-switch-onoff.html](http://linux-hybrid-graphics.blogspot.com/2010/07/using-acpicall-module-to-switch-onoff.html)
That thing there is still very green, so proceed with caution is what I can say to you.

** What if I already installed the Restricted Driver, and now my computer is not booting X?**
1. Boot into Recovery mode (GRUB). Start failsafe-X.
2. When you're in, go to System > Administration > Additional Drivers to deactivate the nVidia driver.
3. Move Xorg: ```
sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.old
```4. Reboot. Intel card should kick in.
-------
I hope this post helps. All thanks go to the great Ubuntu community. All hail the great Tux!

---

### Post by lithopsian on 2011-01-01
Sweet. Good info.

---

### Post by cascade9 on 2011-01-03
One adition- some laptops with switchable graphics/optimus have a BIOS setting that allows you to force the nvidia GPU, disable the nvidia GPU and/or disbale the intel video. 

If you can force the nvidia GPU, opr disable the intel video in the BIOS then you can install the nvidia drivers with no issues.

---

### Post by dino99 on 2011-01-03
good post, thanks a lot.

Might be a sticky IMHO or better: moved to sub-forum "Tutorials & tips"

---

### Post by curryking1 on 2011-01-03
Sweet, thanks for the effort and info. Just read your response in the thread you linked to here from.

---

### Post by lokutus25 on 2011-01-04
Thanks! This is a perfect resume of the info we can gather around :)
If and when there will be some news they should be posted here. I agree with dino99, this should be a sticky.

---

### Post by iliant on 2011-01-11
Hi there,

> **cascade9 said:**
> One adition- some laptops with switchable graphics/optimus have a BIOS setting that allows you to force the nvidia GPU, disable the nvidia GPU and/or disbale the intel video. 

If you can force the nvidia GPU, opr disable the intel video in the BIOS then you can install the nvidia drivers with no issues.

Is there any real advantage to enabling NVIDIA and installing their proprietary driver (after disabling the Intel graphics)?  At the present with both cards enabled as the BIOS default my T410s can handle only a VGA output and pretty badly for my 23'' samsung TFT monitor, no DVI detection at all via the             thinkpad minidoc. Has anyone experimented with the the NVIDIA card + proprietory driver settings to see if any DVI output is possible?

Regards

---

### Post by hobbystas on 2011-01-15
> **cascade9 said:**
> One adition- some laptops with switchable graphics/optimus have a BIOS setting that allows you to force the nvidia GPU, disable the nvidia GPU and/or disbale the intel video. 

If you can force the nvidia GPU, opr disable the intel video in the BIOS then you can install the nvidia drivers with no issues.

Anybody who can name specific models and bios version that have such an option option?In my case, an asus n61jv ver 2.0x (dont remeber exactly)there is no such option. Although the vendor has issued several newer bios versions, the history file of changes is very poor on description, so the only way to find out is to update your bios (or maybe send an e-mail to asus but im not sure if there is going to be any response). since bios updating, to my perception, is a very risky procedure and should not be applied if there is no necessity, i am trying to gather information for my laptop on that, so i won't have to update the bios for nothing and risking to turn my laptop in to a brick. And if anyone has any information on that direction would be a benefit for all, i thing. Like listing models with specific bios versions that are known to have a graphics switching option. So anybody has any information to share?

---

### Post by Bogart on 2011-01-21
I have a Dell XPS 15 with Intel + Nvidia cards (with Optimus on Windows). I haven't tried to use the Nvidia card at all, but I did notice that blacklisting the nouveau module the laptop seems to run cooler and use less energy. I don't use Ubuntu, so I'm not sure what's the standard way of doing this there, but just to give it a try you can "rmmod nouveau" (as root) and see how it works (to reload it "modprobe nouveau", or reboot).

---

### Post by dh04000 on 2011-01-22
> **cascade9 said:**
> One adition- some laptops with switchable graphics/optimus have a BIOS setting that allows you to force the nvidia GPU, disable the nvidia GPU and/or disbale the intel video. 

If you can force the nvidia GPU, opr disable the intel video in the BIOS then you can install the nvidia drivers with no issues.


Does anyone know if the bios of a Acer AS5745G-7671 has the option to turn off the integrated card and use the Nvidia card only?

Does anyone have a 100% working Nvidia driver install on this laptop?

---

### Post by cascade9 on 2011-01-22
> **iliant said:**
> Is there any real advantage to enabling NVIDIA and installing their proprietary driver (after disabling the Intel graphics)? 

Theres a few. VDPAU, much better 3D performance. 

> **hobbystas said:**
> Anybody who can name specific models and bios version that have such an option option?In my case, an asus n61jv ver 2.0x (dont remeber exactly)there is no such option. Although the vendor has issued several newer bios versions, the history file of changes is very poor on description, so the only way to find out is to update your bios (or maybe send an e-mail to asus but im not sure if there is going to be any response). since bios updating, to my perception, is a very risky procedure and should not be applied if there is no necessity, i am trying to gather information for my laptop on that, so i won't have to update the bios for nothing and risking to turn my laptop in to a brick. And if anyone has any information on that direction would be a benefit for all, i thing. Like listing models with specific bios versions that are known to have a graphics switching option. So anybody has any information to share?

Sometimes you can get thing like 'force nvidia' via BIOS updates, and sometimes you will lose those sorts of options. Eg dell vostro 3700-  

[http://ubuntu-ky.ubuntuforums.org/showthread.php?t=1628590](http://ubuntu-ky.ubuntuforums.org/showthread.php?t=1628590)

I see what you mean about 'poor on description'. Lame. Manufacturers used to give youa full list of what the BIOS update did, not meaningless junk like asus has for the BIOS pages for the N61Jv-

> 
                                                                              BIOS 222
Fix there are noises under AC mode.                                                                                 As for a list of all known models with a BIOS switch to force nvidia (or disable intel)- nice idea, but I dont know of any. 

I dont see BIOS updating as that risky. A lot easier to do BIOS updates from a USB stick than like it was in the past with floppies. Still, its not without risk, and its not something I'd do for fun.

---

### Post by rajciok on 2011-01-24
I only need to know how to run nvidia card If there is not such an option in BIOS. I can only switch to "Reserved" mode that switch my laptop to Intel Card only. Is there such a posibility to run NVIDIA drivers?

My laptop ASUS K52JC model ... and only Windows 7 can handle all the stuff inside. NVIDIA Optimus sucks on linux - thats a pitty... :/

---

### Post by schum3,1415 on 2011-02-01
Thanks 3602, for your clear explanations!

I'm using Ubuntu 10.10 x64 on a Lenovo ThinkPad T410 and I can actually change my  GPU preferences in my BIOS to *Intel HD* or *nVidia Optimus* or *nVidia NVS 3100M*

If I choose *Intel HD* or* nVidia Optimus* everything works fine only that when choosing *nVidia Optimus*. The command:
```
lspci | grep VGA
``` displays:
```
00:02.0 VGA compatible controller: Intel Corporation Core Processor Integrated Graphics Controller (rev ##)
02:00.0 VGA compatible controller: nVidia Corporation Device #### (rev ##)
```Just as 3602 showed. 
On the other hand if I choose *nVidia NVS 3100M* the resolution is very low.

So far for my experiences.

---

### Post by realzippy on 2011-02-01
[I]On the other hand if I choose nVidia NVS 3100M the resolution is very low.
[/I]

..not if you installed the NVIDIA driver then.

............................................................................
Stumbled about this thread,and after answering lots of optimus related graphic problems here in the forum (also was about creating an optimus thread) in the last days/weeks (all the optimus christmas gifts?)I am going to link all related posts to this thread.
Thanks,OP!

Anyway,is it possible to make this thread sticky although it is kinda
proprietary problem?
At last jockey should be stopped from offering NVIDIA drivers for optimus
machines.

---

### Post by johan_olsen on 2011-02-02
Thanks 3602 for the explanation. I have an Asus N73J with NVIDIA GT335M (it is an Optimus) graphic card. I installed the restricted driver, but then it would not start in graphic mode. If I delete the xorg.conf it works, but I can not enable Compiz. So I wonder: Can I never use Compiz with this pc? I use Ubuntu 10.10 64-bit. 

Johan, Norway.

---

### Post by realzippy on 2011-02-02
@ Johan

You should uninstall the nvidia driver,not only delete the xorg.conf
to make the intel driver work as it formerly should have done.
Here on optimus lappy  
VGA compatible controller: Intel Corporation Core Processor Integrated Graphics Controller (rev 02)
does a great job in compiz..

---

### Post by johan_olsen on 2011-02-02
@ realzippy
I removed the driver and rebooted, now it starts in graphic mode, but when I try to enable graphic effects and animations, it tries some seconds, but says "Desktop effects can not be activated" (or something like that - I have Norwegian lang.)

So, it works ok, but I would like to see the softer more friendly screens Compiz offers.

Edit: The xorg.conf is now empty. Should it be?

Edit 2: Solved! I  still have no xorg.conf, but I inastalled Emerald and Cairo Dock, suddenly Compiz woke up! Thanks a lot!!

---

### Post by l00ka on 2011-02-22
Hi people!

I have ASUS N73J laptop with integrated Intel graphic + Nvidia gt 425M graphic card, Optimus tech. While in win7, I have LED indicator  showing which graphic is active; it is blue while integrated gpu is active and white while high performance Nvidia is active.

In Ubuntu, indicator is white from the beginning (OS installation), and in win it would mean that Nvidia gpu is active. I haven't installed any recommended gpu drivers because I lose picture when I install them.

My question is : Is Nvidia really activated or is it a false reading due to driver lacking? And can I somehow find out which gpu is active?

PS. I do not need Nvidia in Ubuntu; I would prefer to run on integrated gpu. I will use it mainly for programming.

Thanx

---

### Post by realzippy on 2011-02-23
Welcome to the forum!

Run
```
lspci | grep VGA
```

...guess both are activated;Intel in use and Nvidia just sucking battery power...check your BIOS for a switch.

---

### Post by l00ka on 2011-02-23
this is response to your code

```
00:02.0 VGA compatible controller: Intel Corporation Core Processor Integrated Graphics Controller (rev 18)
01:00.0 VGA compatible controller: nVidia Corporation Device 0df0 (rev a1)

```in BIOS, I didn't find an option to select gpu :( , but I will investigate the matter further

anyway, thank you for your quick response

---

### Post by cascade9 on 2011-02-23
+1 to realzippy. 

If you cant disable the nVidia GPU in the BIOS (or possibly 'force' the intergrated video only) the nvidia GPU is on, but basicly useless. It will just suck power. 

As for how to turn if off if there is no BIOS switch, I have no idea.

---

### Post by 3602 on 2011-02-24
> **cascade9 said:**
> 
As for how to turn if off if there is no BIOS switch, I have no idea.
Idea.
[http://linux-hybrid-graphics.blogspot.com/2010/07/using-acpicall-module-to-switch-onoff.html](http://linux-hybrid-graphics.blogspot.com/2010/07/using-acpicall-module-to-switch-onoff.html)
But you need to write that into a script to boot, if not you're gonna have to do all that manually on each boot.

---

### Post by realzippy on 2011-02-25
> **3602 said:**
> Idea.
[http://linux-hybrid-graphics.blogspot.com/2010/07/using-acpicall-module-to-switch-onoff.html](http://linux-hybrid-graphics.blogspot.com/2010/07/using-acpicall-module-to-switch-onoff.html)
But you need to write that into a script to boot, if not you're gonna have to do all that manually on each boot.

That might work on Intel/ATI combos,with optimus it not seems to work. **Edit. work always**.

---

### Post by 3602 on 2011-02-25
> **realzippy said:**
> That might work on Intel/ATI combos,with optimus it not seems to work.
If you do not have a folder
/sys/kernel/debug/switcheroo   (only Intel/Ati combos seems to have..)
this does not work..
Wrong. My previous Gateway ID59c-04h which had Optimus can have it turned off. All you need to do is:
```
git clone [http://github.com/mkottman/acpi_call.git](http://github.com/mkottman/acpi_call.git)

cd acpi_call

make

sudo insmod acpi_call.ko

./test_off.sh
```
SUCCESS IS NOT GUARANTEED. It worked for me (power consumption dropped immediately from 17W to 10W after executing).

---

### Post by realzippy on 2011-02-25
..remember if you had  /sys/kernel/debug/switcheroo   ??


tried the test.sh script 3 weeks ago,it did not work.
If you have a minute,please have a look [here]("http://ubuntuforums.org/showpost.php?p=10406261&postcount=9").
Do you have an idea what to do?
Really would like to power M310 off...

---

### Post by 3602 on 2011-02-25
Interesting, that I do not know. Check the battery Rate again.

---

### Post by Raspounch on 2011-02-27
Hey, I've got an Asus N53j which runs with
```

00:02.0 VGA compatible controller: Intel Corporation Core Processor Integrated Graphics Controller (rev 18)
01:00.0 VGA compatible controller: nVidia Corporation GT215 [GeForce GT 335M] (rev a2)

```

First thank's for the info on how to turn off the nvidia chip (with a rather poor bios, no options regarding video at all), not sure it works though, I'll try checking the power consumption after a reboot.

I'm however having trouble enabling effects on compiz with the Intel integrated graphics, I'm currently running without a xorg.conf

Any ideas ? 

(PS johan_olsen's Edit note with Cairo and Emerald did not work for me)

Output of compiz command :
```

Xlib:  extension "GLX" missing on display ":0.0".
compiz (core) - Fatal: glXCreateContext failed
compiz (core) - Error: Failed to manage screen: 0
compiz (core) - Fatal: No manageable screens found on display :0.0

Launching fallback window manager

```

---

### Post by Raspounch on 2011-02-27
Bumping it up.

Also the acpi calls works great, with 2 weird bugs (so far), when the nvidia card is off, weirdly enough if I try to run Skype the computer freezes, hardcore way, can't move mouse and not responding to any keyboard signal, ctrl alt f1 included. Also on shutdown if the nvidia card is off, it freezes too at different stages (really weird too).

For skype I run it before opening a shell that runs the script, after that everything works great whether the nvidia card is on or off, and I wrote a quick script similar to test_off.sh, replacing the end of the command that "works" with ON instead of OFF to turn it back on, and placed it in /etc/rc6.d so it's triggered on shutdown.

Saving more than 1hr battery with the trick !

Still can't run compiz w/ effects though ^^

---

### Post by QuimNuss on 2011-04-04
I can tell the suggestion of 3602 worked for switching from Activated NVIDIADiscrete GPU to Intel Integrated GPU. Now the fan doesn't spin that hard and probably the battery will last longer.

Still no success in getting more functionality out of the integrated card.

A led still informs me that Optimus Mode Activated, but not UMA Mode Activated. "In the UMA Mode system will use only integrated GPU (part of Intel's Arrandale technology) for maximum power-saving. - In the Optimus Mode will allow the system to automatically determine whether to use discrete GPU (dGPU) and integrated GPU (iGPU) depending on task and/or application"

So I'm not sure what I've achieved, but the dGPU seems to be deactivated.

If somebody has any idea how to increase screen resolution post it here!

This post is definetely gathering all the information about the issue.

Somebody has a clue if the issue will be solved one day or another by either nvidia or xorg or nouveau guys?

Thanks to everyone for the work achieved so far!

---

### Post by unrater on 2011-04-12
I would like to have two kernels in Grub, one for nvidia and other to Intel.

Is there a way that we could do that? Can you tell me? I think most of the users with optimus would appreciate that!!

Best Regards

---

### Post by realzippy on 2011-04-12
Easiest solution would be installing 2 Ubuntus.....

---

### Post by unrater on 2011-04-17
That is a little lamy solution :D

Is there a better solution for my question?
> **unrater said:**
> I would like to have two kernels in Grub, one for nvidia and other to Intel.

Is there a way that we could do that? Can you tell me? I think most of the users with optimus would appreciate that!!

Best Regards

---

### Post by realzippy on 2011-04-18
It is not only the kernel:
also xorg.conf and some libraries are different.

---

### Post by gianvito on 2011-05-03
Any news? I have an Asus K53SV (Nvidia GT540m)... I tried to switch off the Nvidia card and it works (battery duration increases a lot)... but the system fan starts to run at its max speed! :confused:

I can't really understand why.... is there a way to control the system fan manually?

---

### Post by 3602 on 2011-05-03
No idea about the fan. I don't think that you can control the fan on a portable...
You may try posting this problem at that blog page...
Good luck.

---

### Post by gewin on 2011-05-03
A large number of new notebooks are coming out with the Nvidia Optimus graphics option. Personally I have finally given up my desktop and use the Acer 4750G as my notebook and desktop replacement. When at home I plug in a HD screen, keyboard and mouse; on the road I have the same notebook, data etc. etc.

The notebook comes with Windows 7 which works perfectly in this environment. I have been an Ubuntu user for many years, so I installed 11.04 to run in this environment and have been tearing my hair out for the last week. 

Thanks for the explanation, I have been through all of the pitfalls. Unfortunately I have now changed my default boot to Windows 7.

From my perspective if Ubuntu is ever to conquer the desktop the developers need to get the install process and support for common technology eg Nvidia Optimus working out of the box before worrying about new things like Unity(I don't want to run special scripts or kernels). At this stage I could not recommend 11.04 to my friends or clients, purely from an install and device support perspective.

---

### Post by 3602 on 2011-05-04
Please do not blame Ubuntu for this. If nVidia is not developing this, nobody else is because Ubuntu cannot reverse-engineer their hardware (or Windows driver).
I'm just happy that fglrx works.

---

### Post by r109chaos on 2011-05-06
I believe my ASUS UL80J is running both.


```
chaos1@fatalerr0r:~$ lspci | grep VGA
00:02.0 VGA compatible controller: Intel Corporation Core Processor Integrated Graphics Controller (rev 18)
01:00.0 VGA compatible controller: nVidia Corporation GT218 [GeForce 310M] (rev a2)
```

Minecraft doesn't run to well. :(

---

### Post by martin-juhl on 2011-05-12
Ok... if any of you guys need optimus support on Ubuntu...

Look here:

[https://github.com/MrMEEE/bumblebee](https://github.com/MrMEEE/bumblebee)

Follow me on [Twitter]("http://twitter.com/martinjuhl")

---

### Post by greatsouls on 2011-05-15
> **dh04000 said:**
> Does anyone know if the bios of a Acer AS5745G-7671 has the option to turn off the integrated card and use the Nvidia card only?

Does anyone have a 100% working Nvidia driver install on this laptop?

I have **ACER ASPIRE 5745G-7566** (i3-370 w/ nVidia 310M and Optimus) and in the BIOS there is an option for video card to select between "Switchable" and "Discrete". I guess "Discrete" means the nVidia dedicated card will be used. I am not 100% sure, though. However, I noticed when installed Ubuntu 11.04 it said the system does not support the new interface (does not have hardware to run it) and booted in Ubuntu Classic Desktop. I switched to "Discrete" graphic in the BIOS, installed the proprietary driver and was able to run the new interface.

Now when I run "System > Administration > Additional Drivers" it says "This driver is activated but not currently in use."
What exactly that means? Which card I am currently using? Intel or nVidia? How can I check that? 

What if want to go back using Intel video (for better battery life) what should I do?
If I change the option in the BIOS back to "Switchable" I cannot boot Ubuntu.

I am new to Linux and any help will be much appreciated...

Here is the result from 'lspci | grep VGA' with "Discrete" option selected in the BIOS
```

lspci | grep VGA
01:00.0 VGA compatible controller: nVidia Corporation GT218 [GeForce 310M] (rev a2)

```Here is the result from 'lspci | grep VGA' with "Switchable" option selected in the BIOS
```

lspci | grep VGA
00:02.0 VGA compatible controller: Intel Corporation Core Processor Integrated Graphics Controller (rev 18)
01:00.0 VGA compatible controller: nVidia Corporation GT218 [GeForce 310M] (rev a2)

```Also, with Discrete selected in the BIOS I am able to run glxlears. With 'Switchable' selected I am getting error:

Xlib:  extension "GLX" missing on display ":0.0".
Error: couldn't get an RGB, Double-buffered visual

---

### Post by glomerulus on 2011-05-16
Hello everyone,

I installed Ubuntu 10.04 Lucid on my xps 15 with core i5 (2410M) and nVidia GeForce 540M with Optimus.

I followed the steps as in the first post on this thread. But somehow i cannot get the Intel graphics to kick in.
When i try to enable desktop visual effects, it searches for drivers for a bit before suggesting me to install drivers for the NVIDIA card. It fails to enable desktop effects.

How do i get the intel graphics to handle desktop effects?

For reference :
```

lspci | grep VGA
00:02.0 VGA compatible controller: Intel Corporation Device 0116 (rev 09)
01:00.0 VGA compatible controller: nVidia Corporation Device 0df4 (rev a1)

```Please help!
I am breaking my head over this since a couple of days. Also created a thread in General Help but nobody replied :(

---

### Post by 3602 on 2011-05-16
You can probably use Metacity instead of Compiz... During the days I got the ID59c I had no idea what "Compiz" was so I never had any desktop effects problem...
Sorry.

---

### Post by glomerulus on 2011-05-16
hey 3602, how do i do that exactly?

If i understand correctly, when i set visual effects to "None" (and not Normal or Extra), am i not using Metacity?

Do u think i am missing intel graphics drivers?

---

### Post by 3602 on 2011-05-16
Sincerely I got no idea what default drivers are used on the Intel HD graphics... You should open a post at Hardware and Laptops and mention "Intel HD graphics driver" in your title. I think you'd get better support there.
Otherwise... in terms of Metacity, use
```
metacity --replace
```
Or, get Ubuntu Tweak and "Enable Metacity compositing feature".
Good luck.

---

### Post by glomerulus on 2011-05-16
Well I was about to try that when compiz just kept hanging on me..
I dont know what i messed up, but anything that i tried wiht the desktop effects would just hang the system showing just the wallpaper and a stuck pointer.

Just did a fresh install of Natty and compiz just worked out of the box! All the effects and everything.
I dont really know how, or what drivers are being used.

**lspci **still shows both Intel integrated graphics and the nVidia card

However, i checked in **Additional Drivers**, and the nVidia driver is not active.

Would have liked to get this working with Lucid, but oh well.. Till someone comes up with a hard solution, or Optimus support

Thanks for your help anyway 3602.. Much appreciated

---

### Post by Starks on 2011-05-17
optimus on ubuntu

[https://github.com/MrMEEE/bumblebee#readme](https://github.com/MrMEEE/bumblebee#readme)

---

### Post by realzippy on 2011-05-17
That looks interesting....
will check it out today and report.

---

### Post by thaibuntu on 2011-05-22
> **realzippy said:**
> That looks interesting....
will check it out today and report.

What's the status?

---

### Post by 3602 on 2011-05-22
Well... Time to update the main post then.

---

### Post by realzippy on 2011-05-24
> **thaibuntu said:**
> What's the status?

It works.Means,you can run 3D apps with the nvidia-card;however,
the desktop itself does not run in 3D,so no compiz.
Also it does not increase battery life,since it does not work together
with VGA switcheroo (on my machine,maybe others do).
So,if you want 3D gaming on Ubuntu,this is a solution,but I prefer
running games in Windows anyway.

---

### Post by bjordan1979 on 2011-05-24
> **realzippy said:**
> It works.Means,you can run 3D apps with the nvidia-card;however,
the desktop itself does not run in 3D,so no compiz.
Also it does not increase battery life,since it does not work together
with VGA switcheroo (on my machine,maybe others do).
So,if you want 3D gaming on Ubuntu,this is a solution,but I prefer
running games in Windows anyway.

Interesting. Thanks for the feedback. I'm real close to buying a Thinkpad T420 and if this works well then it's huge news. It can only get better.

Also what laptop do you have? You may want to let them know so they can add your model to the README file.

Has anyone else tried it?

---

### Post by realzippy on 2011-05-24
..if you really want to buy a Optimus laptop,just watch out for a BIOS graphics switch,and you are fine.

Unfortunately these workarounds are no "Optimus for Linux",means,nice power management using both graphics devices;in W7 this runs great,here it is 
ugly hacking;and it will be unless the MS/Intel/Nvidia gang releases some code.....

Tested it on Packard Bell Easynote TK85,acpidump attached for
anyone who is interested.

---

### Post by roberto.pierpaoli on 2011-05-26
Hi guys,
what about "bumblebee"?
Have you heard about that?
I do not own any laptop using optimus, but I am about to buy one, it would be nice to know that some of you have tried bumblebee with good outcomes...

[http://www.omgubuntu.co.uk/2011/05/bumbleebee-brings-nvidia-optimus-gpu-switching-to-linux-users/](http://www.omgubuntu.co.uk/2011/05/bumbleebee-brings-nvidia-optimus-gpu-switching-to-linux-users/)

---

### Post by 3602 on 2011-05-26
I'd say proceed with caution since that "fix" there is very green.

---

### Post by jocefus on 2011-05-28
I recently got an Alienware M14X. Ubuntu 11.04 installed clean and had 3d effects enabled with the Intel integrated card, but Nvidia gpu is still 'ON' and uselessly draining the battery. With bumblebee and a little work I was able to utilize the Nvidia GPU. With acpi_call I was able to toggle the card on/off. So it is somewhat functioning.
 
It is not automatic. The desktop environment still uses the Intel chip. Anything you want to run with the Nvidia gpu has to be called with the 'optirun' command first. The newest version enables using acpi_call automatically to start/stop card for power savings. (on my machine and many others confirmed) This feature was not turned on by default.
 
The only wierd thing I have noticed so far is that I cannot simply "reboot" after utilizing optirun. I have to completely power down/up otherwise the Nvidia card is absent from the system bios, lscpi (Linux), and device manager (Windows). Not sure yet whether it is bumblebee or acpi_call causing this issue. I'm going to test more when I get the chance.
 
As of now, unless you are ready to follow and help with development, I would recommend steering clear of notebooks using these cards unless you can find out whether the bios supports classic hybrid-disabling features.

---

### Post by rete mirabile on 2011-06-01
Thankyou for the very useful information, I'm a complete newbie.

I've  just installed ubuntu 11.04 64-bit alongside win7 64-bit on a dell xps  15 L502x i7 with *nVidious* Optimus (GT 540M  and intel HD3000).
I  didn't install the nVidia drivers, like you said.  youtube videos and   online flash games all work fine as do glob2 and frozen-bubble. However  etracer (0-60 fps mostly 0-10 fps) and openarena (worse) are very choppy  , glxgears hovers at 60 fps. I assume therefore that the HD3000 3d  acceleration isn't working well. This doesn't much matter as I intend to  use win7 for gaming, but it does nag. Can anyone offer advice on how to  fix this?

---

### Post by 3602 on 2011-06-01
Intel integrated chips are very limited. Back on my GT 420M Optimus all I can play correctly was Extreme Tux Racer. Not even TORCS.

---

### Post by rete mirabile on 2011-06-03
Although I'm not expecting much from the hd3000, I wonder if the performance issues may have more to do with software than hardware:
[http://www.notebookcheck.net/Review-Intel-HD-Graphics-3000-graphics-solution.43710.0.html](http://www.notebookcheck.net/Review-Intel-HD-Graphics-3000-graphics-solution.43710.0.html)
what do you think?

---

### Post by rete mirabile on 2011-06-25
I've been using bumblebee and seems to work well.

---

### Post by Z06Gal on 2011-06-30
Bumblebee is working great for me ;)

---

### Post by StartedTheFire on 2011-07-24
I am SO happy I found this thread. You don't even know how happy I am. First of all I'm just happy because it restores my faith in the order of the universe- before I had no idea why my drivers were updated but it couldn't run unity (not that i like unity) or minecraft at all. Now at least it makes sense!

What's even better is that bumblebee worked great for me, on my Asus N53SV with a 550 card. Just typing ```
optirun java -jar minecraft.jar
``` runs minecraft in glorious definition with zero lag. For whatever dumb java-related reason it actually runs better now in ubuntu than in windows.

90% of the time I hate linux but the 10% of the time when something awesome like this happens it's almost sort of worth it.

---

### Post by Beaucoq on 2011-08-06
All of you people who actually got bumblebee working, that means you got the Nvidia driver working, correct?  I cant seem to get it working... After installing the Nvidia driver I either get a black screen, or only able to run in classic mode with the driver activated but not in use with no 3d acceleration.  As a side note shouldnt the nvidia driver be generating a xorg.conf file? If so could you post a copy of yours?

---

### Post by pikamoku on 2011-08-10
any guide for making bumblebee work fine please? I tried month ago to make it work (ubuntu 11.04 64bit + gnome3-gnomeshell + lenovo b560 with intel+nvidia cards). 
Actually I installed bumblebee but I couldnt make nvidia card work, surely I missed some point to install the correct driver or whatsoever.
Please, any step by step guide? thanks

---

### Post by realzippy on 2011-08-10
From the **README**:


[I]Bumblebee has now been packaged into a PPA @ Launchpad:

[https://launchpad.net/~mj-casalogic/+archive/bumblebee/](https://launchpad.net/~mj-casalogic/+archive/bumblebee/)

This will probably be the most up-to-date version for Ubuntu from now on...

For people currently running the script/git version please do:
[/I]
```
sudo bumblebee-uninstall
sudo apt-get install ppa-purge
sudo ppa-purge ppa:ubuntu-x-swat/x-updates
sudo ppa-purge ppa:xorg-edgers/ppa
sudo apt-add-repository ppa:mj-casalogic/bumblebee
sudo apt-get update
sudo apt-get install bumblebee
```

If you want a GUI to configure use of bumblebee:
```

sudo apt-get install bumblebee-ui
```

..will be in system==>administration

---

### Post by pikamoku on 2011-08-10
thanks, I'll take a look on it. Last time I tried there was no PPA ;)

---

### Post by chukis13 on 2011-08-10
Has anyone tried this driver that was just released the first of this month?
 
[http://www.nvidia.com/object/linux-display-ia32-280.13-driver.html](http://www.nvidia.com/object/linux-display-ia32-280.13-driver.html)

---

### Post by 3602 on 2011-08-10
You know, it's great that people are working to make Optimus work on Linux.

---

### Post by chukis13 on 2011-08-11
Okay, super newb here... I installed bumblebee via terminal with some "sudo apt-get" command I found and followed the set up afterwards. Do I need to activate the nvidia driver now or did bumblebee take care of that? Also, how can I confirm it is working? If I can get WoW working on here with the nvidia card I plan to make Ubuntu my main. Thanks in advance for any and all help.

---

### Post by realzippy on 2011-08-11
I am not on bb now,so I don 't know exactly,but there should be 2
launchers for bumblebee in System ==> Settings *or* Administration
where you could choose eg WoW and add it to your bb list.

---

### Post by chukis13 on 2011-08-11
Okay, so I set wine windows program loader as one of the preferred apps in bumblebee gui, does that mean anything i open with wine will use the bumblebee and use the nvidia card?

---

### Post by rd1381 on 2011-08-14
can you answer these question for me plz?
1)after installing bumblebee i cant run glxgears alone and have to use optirun glxgears.
when i enter   glxgears    it says :                   

                                                                                                                                                     
Xlib:  extension "GLX" missing on display ":0".                                                                                                                                                 
Error: couldn't get an RGB, Double-buffered visual   

but before installing bumblebbe i didn't have this issue.yes frame-rate was low but it didn't give error and it ran.

2) i know from your help on launchpad page that there is a way to turn off nvidia card though i couldn't  do it. now is there a way to tell ubuntu to ignore" Intel" card and boot with nvidia card alone? the reason for this is that i don't care about power consumption but i cant run some apps in optirun mode( like vmware), so i want my ubuntu to see only my nvidia

---

### Post by chukis13 on 2011-08-15
> **rd1381 said:**
> 2) i know from your help on launchpad page that there is a way to turn off nvidia card though i couldn't do it. now is there a way to tell ubuntu to ignore" Intel" card and boot with nvidia card alone? the reason for this is that i don't care about power consumption but i cant run some apps in optirun mode( like vmware), so i want my ubuntu to see only my nvidia
 
I'd like to know this as well.

---

### Post by realzippy on 2011-08-15
AFAIK (may 3602 or anybody correct me) this is not possible.

---

### Post by SuchetBargoti on 2011-08-16
I am trying to get my external monitor working on my Ubuntu 10.04. I haven't installed bumblebee as I have had issues with it before. Also haven't installed the nvidia restricted drivers so dont have that xorg.conf file that all the dual monitor tutorials talk about. 

This is my output from ```
lspci | grep VGA
```

```
00:02.0 VGA compatible controller: Intel Corporation Device 0126 (rev 09)
01:00.0 VGA compatible controller: nVidia Corporation Device 0dcd (rev a1)
```

Can some one give me a hand on how to set up a dual monitor considering I am using my integrated intel card (atleast I think I am) and not my optimus nvidia card.

---

### Post by realzippy on 2011-08-16
I don't know this exactly,but as I understood,there are laptops around where
the laptop screen is driven by the onboard intel chip,while the VGA/DVI
output connector is connected to the discrete nvidia card.
This would mean:
No way.
Maybe someone with more optimus know-how can confirm or correct this.

---

### Post by iammeagain on 2011-09-04
Quick Question: Is there a way to get the mini display port to output without Nvidia drivers for the xps15/l501x? PM if you could, I'll probably forget to check back.


I haven't read this whole thread, but thought I would throw in my tid bit. I did some messing around with the Nvidia 420m on my xps15 aka l501x. I was able to turn off the Nvidia card so it wouldn't drain my battery. Also unless I purged all the Nvidia drivers and reinstalled the Intel ones I couldn't get much 3d to work. 

Heres the info I wrote up. It could use some revising, but I have been more than busy. 
This is the original way I got Nvidia turned off:
[http://ubuntuforums.org/showthread.php?t=1703301](http://ubuntuforums.org/showthread.php?t=1703301)
There is more info if you read, I don't think that is the most up to date process I was using at the time. Haven't messed with it in a while so it isn't fresh in my memory.

Post #26 explains the purging nvidia process:
[http://ubuntuforums.org/showthread.php?p=10754388#post10754388](http://ubuntuforums.org/showthread.php?p=10754388#post10754388)

---

### Post by realzippy on 2011-09-05
Just want to add here that Bumblebee has forked to
[ironhide]("http://www.martin-juhl.dk/2011/08/ironhide-reporting-for-duty/") and [bumblebee Project]("https://launchpad.net/~bumblebee/+archive/stable").

---

### Post by nibodads on 2011-09-08
nice tutorial and i must say very simple...... i learned this much after i bricked the whole os and made a second clean install. and i m happy without nvidia driver in ubuntu in my asus ul80jt......

---

### Post by danger89 on 2011-09-23
Bad news about nVIdia Optimus in combination with Linux :( However I see hope in the Bumblebee Project.

---

### Post by TweFoju on 2011-10-01
ok guys can you guys tell me if i am doing these steps the right way?

so i clean install 11.04

then i do this as the 1st step:


[LIST]
[*]**sudo apt-add-repository ppa:mj-casalogic/bumblebee**
[*]**sudo apt-get update && sudo apt-get install bumblebee**
[/LIST]
this is to download the Bumblebee, after this, i restart Laptop

then i use these command to switch on and off between the nVidia and Intel:

> 
sudo apt-get install git
git clone [EMAIL="git@github.com:mkottman/acpi_call.git"]git@github.com:mkottman/acpi_call.git[/EMAIL] cd acpi_call make sudo insmod acpi_call.ko
chmod +x ./test_off.sh


> ./test_off.sh


then using these command to switch on and off ( Nvidia )

> echo '\_SB.PCI0.PEG0.GFX0.DOFF' > /proc/acpi/call

echo '\_SB.PCI0.PEG0.GFX0.DON' > /proc/acpi/call


Source:

[http://linux-hybrid-graphics.blogspot.com/2010/07/using-acpicall-module-to-switch-onoff.html](http://linux-hybrid-graphics.blogspot.com/2010/07/using-acpicall-module-to-switch-onoff.html)

and both of the Additional driver, the original "Nvidia accelerated graphics driver" and the " experimental nVidia 3D support" from BumbleBee is both inactive and not in use

so does this make my steps correct to use the nVidia?

---

### Post by Matt_Fussell on 2011-12-14
I've encountered this issue on a Dell Vostro 360 all in one.  I've tried installing the latest driver from Nvidia.  I've tried Ironhide (although I may have done it incorrectly) and as of this post I am unable to install bumblebee from the PPA (were they removed?).

I was denied permission (even though I accepted the key) to the acpi_call script, and am now currently at at loss.

Is there anyone who has established a solution to this?

I'm running Ubuntu 11.10.

---

### Post by Trilby on 2011-12-14
This may be of use to people having trouble with Optimus/Nvidia.
[http://ubuntuforums.org/showthread.php?t=1882402](http://ubuntuforums.org/showthread.php?t=1882402)

---

### Post by Matt_Fussell on 2011-12-15
> **Trilby said:**
> This may be of use to people having trouble with Optimus/Nvidia.
[http://ubuntuforums.org/showthread.php?t=1882402](http://ubuntuforums.org/showthread.php?t=1882402)

I've tried ironhide twice on a fresh install without any success.  I'm not sure if I'm not doing it correctly or if it's just not working, and I'm not willing to rule out either of the cases at the moment.  It does tell me that there is no graphics profile for my machine, so if I get it working, I should submit it.  If I could get it working, I'd love to submit it, but so far, no dice.

---

### Post by Henri Lebesgue on 2012-01-04
Thanks, that is some real good information!

---

### Post by shevek. on 2012-01-11
I have a Dell Inspiron N5110 (with Optimus) and had an issue with battery life and lack of 3D acceleration. I solved both problems by disabling the Nvidia, adding script to startup, removing Nvidia controllers and activating 3D in the Intel card. More in detail:
[http://ubuntuforums.org/showpost.php?p=11603104&postcount=28](http://ubuntuforums.org/showpost.php?p=11603104&postcount=28)

---

### Post by Lekensteyn on 2012-01-20
Using acpi_call directly is now deprecated, especially if you are using the _OFF methods. Use bbswitch instead which is used by Bumblebee 3.0 [http://askubuntu.com/q/36930/6969](http://askubuntu.com/q/36930/6969)

---

### Post by 3602 on 2012-01-20
Um, has the Bumblebee/Ironhide bunch started a new thread?

---

### Post by sbnwl on 2012-02-17
Hi there,
[Lekensteyn]("http://ubuntuforums.org/member.php?u=911495") above is correct. New bumblebee version 3.0 is working out of box. Thanks to [https://wiki.ubuntu.com/Bumblebee](https://wiki.ubuntu.com/Bumblebee)

For my ASUS K53SV netbook, (NVIDIA GT540M) it is a **great power saving** too. With default Ubuntu 11.10 installation, my power consumption was nearly 30 W. I managed to cut it down to 22 W with some kernel options before boot using this ([http://www.phoronix.com/scan.php?page=article&item=intel_i915_power&num=1](http://www.phoronix.com/scan.php?page=article&item=intel_i915_power&num=1)) 

But Still the battery was lasting only for 2hr and 50 minutes at 20% screen brightness.

I installed today BUmblebee 3.0, (had never tried it in past, nor did for Ironhide). After installation and reboot it came to 12W consumption. Battery is now reading 4 hr and 40 minutes, and mind that the display brightness is at 50%. 
I have tested some of the games on wine, which are working fine with bumblebee "optirum wine yourgame" command. 

**ONLY Bumblebee has managed to calm down my discrete NVIDIA card**, which was by default always ON in my default Ubuntu 11.10 installation, and was consuming alone 10 W of power, cutting my battery down by 2 hours.

Enjoy the solution.:guitar:

---

### Post by sbnwl on 2012-02-17
I now have one query, probably someone can tell me.

My NVIDIA card logo on my ASUS K53SV netbook reads CUDA(TM) on it. 

Is it safe to follow the instructions suggested at [http://samiux.blogspot.in/2011/05/howto-nvidia-cuda-toolkit-40-on-ubuntu.html](http://samiux.blogspot.in/2011/05/howto-nvidia-cuda-toolkit-40-on-ubuntu.html) ?

Mind that I already have installed Bumblebee 3.0 as suggested at [https://wiki.ubuntu.com/Bumblebee](https://wiki.ubuntu.com/Bumblebee)

I fear the nvidia-current installation suggested on above CUDA page could break my already installation of Bumblebee 3.0 package.

I use parallel computing on desktops for FE simulations, so just curious about the CUDA technology.

[]("http://samiux.blogspot.in/2011/05/howto-nvidia-cuda-toolkit-40-on-ubuntu.html")

---

