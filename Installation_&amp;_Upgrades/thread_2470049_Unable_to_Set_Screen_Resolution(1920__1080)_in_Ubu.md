---
title: "Unable to Set Screen Resolution(1920 * 1080) in Ubuntu 20.0.4"
date: 2021-12-18
forum: Installation &amp; Upgrades
---

### Post by ankitprumi on 2021-12-18
[https://i.stack.imgur.com/68DsI.jpg](https://i.stack.imgur.com/68DsI.jpg)

I recently purchased a 24" LG PC. when I start my PC it shows a warning that your screen resolution is not currently set to 1920*1080. I try to solve this warning by using a terminal. but can't solve this issue. I set 1920 * 1080 new screen resolution using the below command cvt 1920 1080
```
cvt 1920 1080
sudo xrandr -0-newmode "1920x1080_60.00"  173.00  1920 2048 2248 2576  1080 1083 1088 1120 -hsync +vsync
sudo xrandr --addmode VGA-1 "1920x1080_60.00"
```
[https://i.stack.imgur.com/dGCtL.png](https://i.stack.imgur.com/dGCtL.png)

After applying a new resolution still getting issues. Also, the screen does not fully fit in the monitor.

---

### Post by MAFoElffen on 2021-12-18
Just some observations to take note of:

- Though you can do it that way (out of many ways)... Setting the resolution via xrandr is "temporary" for the current session. If you do it that way, there are other things you need to do to continue that, or it will not be there (again) when you reboot. There is no persistence with xrandr.
- If you add a modeline via xrandr,  inside of an xorg.conf file for XServer, or other methods... You need to enure the modeline matches your video hardware and display. Many GPU's can process many forms of modlelines for a specific resolution, but that does not mean it is a match for a specific connected display. From what you described as being your current issues, there may be a problem with the modeline not being a good match between the two. There are many ways to calculate a modeline and have it display a resolution, but that means you need to find which one is that match between.
- When you said you upgraded to a '24" LG PC'... Did you really mean that you have a PC and upgraded to a 24" LG display or TV?
- If we knew the display Make (LG) and model (?), and the video GPU information, you may be making this harder than it needs to be. Just saying...

If you ran the UbuntuForum's 'system-info' script in my signature line, it has a fairly extensive graphics hardware and settings section in it's report, that would help us determine what is going on, and help us to make a recommendation based on those facts. Just choose to upload the report to a Pastebin and post the URL of that report in a post.

---

### Post by DuckHook on 2021-12-19
Please don't post large graphics to the forums. This is very problematic for helpers with low speeds, who are on limited data plans, or are viewing from smartphones or small screens. 

If you must post resource-intensive images, please post them as attachments using the paperclip icon in the *Adv Reply* toolbar.

For similar reasons, please use the default fonts and styles in your postings. Odd fonts/styles are hard to read on mobile devices or for those with reading difficulties.

---

### Post by ankitprumi on 2021-12-20
Hello @[MAFoElffen]("https://ubuntuforums.org/member.php?u=1044547")
I generated system report using your provided script. see below pastebin URL

[https://termbin.com/7lno](https://termbin.com/7lno)

---

### Post by MAFoElffen on 2021-12-20
I'm analyzing the report right now. Just got off a closing shift.. I is almost 1 am here. 

What is your Brand and model of Display please? I have everything except that information. I see on LG 24" at 720p (1280x720), one at 1080p (1920x1080)...

On your CPU, which is an APU which Intel UDH 630 Graphics... the internal APU is capable of 4K support, but your motherboard specs by Gigabyte says the motherboard is limited to a MAX res of only 1920x1200(???)

---

### Post by ankitprumi on 2021-12-20
Hello @[MAFoElffen]("https://ubuntuforums.org/member.php?u=1044547")

My PC Brand - LG
Model Number - 24MP88HV-S

Thank you

---

### Post by MAFoElffen on 2021-12-20
Thank you...

---

### Post by MAFoElffen on 2021-12-20
> **ankitprumi said:**
> I recently purchased a 24" LG PC. when I start my PC it shows a warning that your screen resolution is not currently set to 1920*1080. I try to solve this warning by using a terminal. but can't solve this issue. I set 1920 * 1080 new screen resolution using the below command cvt 1920 1080
```

cvt 1920 1080
sudo xrandr -0-newmode "1920x1080_60.00" 173.00 1920 2048 2248 2576 1080 1083 1088 1120 -hsync +vsync
sudo xrandr --addmode VGA-1 "1920x1080_60.00"
```
After applying a new resolution still getting issues. Also, the screen does not fully fit in the monitor.
Okay. You have a custom built Desktop PC, built with an OEM Gigabyte H410M S2 V3 motherboard, connected to an LG 24mp88hv-s display. 

The lowest common denominator limiting your display resolution is your display, which is 1920x1080 @60Hz or 1080p... 

The next limiting factor is your motherboard, which is only capable of 1920x1200. 

Your GPU is capable of 4K resolutions if it was in another motherboard that supported it 'and' connected to a 4K display... 

Your highest resolution possible with your hardware "is" 1920x1080.

I'm preparing a post with not just different modelines to try as a last resort... But for things to try before having to resorting to add modelines. 

This make take a bit, but I am working on it.

Question... Why did you spec VGA-1 instead of _____? On xrandr. it might have given you another name for an HDMI port... Unless you are actually connected to the display by only through a VGA adapter, which would limit things down to the lowest denominator...

---

### Post by ankitprumi on 2021-12-20
Hello @[MAFoElffen]("https://ubuntuforums.org/member.php?u=1044547")[COLOR=#000000] 
Our system shows DP-1 instead of HDMI-1 or VGA-1.
Do we need to change gigabyte motherboard ( which is compatible with HDMI LG 24" monitor)?[/COLOR]

---

### Post by MAFoElffen on 2021-12-20
> **ankitprumi said:**
> Hello @[MAFoElffen]("https://ubuntuforums.org/member.php?u=1044547")[COLOR=#000000] 
Our system shows DP-1 instead of HDMI-1 or VGA-1.
Do we need to change gigabyte motherboard ( which is compatible with HDMI LG 24" monitor)?[/COLOR]
#1. "DP-1" That's what I thought... Instead of VGA-1. But I did not want to assume that nor blurt out that I knew it was different.
#2. No. Your board will do 1080p/1920x1080... which is what you are trying for.

Note: I bought a 4K Display on last year's Black Friday sales, thinking It would be great on my PC... I kept losing track of mouse cursor at that resolution. LOL.

---

### Post by ankitprumi on 2021-12-20
@[MAFoElffen]("https://ubuntuforums.org/member.php?u=1044547")[COLOR=#000000] 

So what is solution to fix this issue?
Can we change default graphics using BIOS setting?

[/COLOR]

---

### Post by MAFoElffen on 2021-12-20
Sorry for the delay.

The Intel i950 Graphics Driver is internal to the Linux Kernel... So there are so nay ways to do this...

First by giving the Linux Kernel a 'hint' by passing it a boot parameter to set it in that mode early... Open a terminal session and edit the grub default file in an elevated mode...
```

sudo gedit /etc/default/grub

```
Go down to the line that says
```

#GRUB_GFXMODE=640x480

```
And change it to 
```

#GRUB_GFXMODE=1920x1080x32

```
Go to the line that says
```

GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"

```
And change to
```

video=uvesafb:mode_option=1920x1080-32,mtrr=3,scroll=ywrap

```
Save and exit. Update Grub to pick up the changes...
```

sudo update-grub
sudo reboot

```
That should set the resolution of 1920x1080 at the kernel Boot, using KMS, and be at that resolution when the Splash screen starts, then gets to the Graphical login... So it should recognize that mode as 'Native' and preferred. That way everything should be more fluid and forced into something different than it is not... 

Once it gets to the desktop, open Settings > Display.... Check the resolution and see that it recognized it as a setting, and that is selected.

If it is still not in that resolution or needs adjustment to display correctly... I have calculated 4 modelines that should work for your APU/Display combination:
```

                                                                                                 [TABLE]
[TR="bgcolor: #ffffff"]
[TD]XFree86 Modeline[/TD]
[TD="colspan: 7"]Modeline "1920x1080@60" 182.28 1920 1952 2640 2672 1080 1102 1113 1135[/TD]
[/TR]
[TR="bgcolor: #ffffff"]
[TD]CVT Modeline[/TD]
[TD="colspan: 7"]Modeline "1920x1980_59.98" 324.75 1920 2072 2280 2640 1980 1983 1993 2051 -HSync +VSync[/TD]
[/TR]
[TR="bgcolor: #ffffff"]
[TD]CVT-RB Modeline[/TD]
[TD="colspan: 7"]Modeline "1920x1980_59.95" 254 1920 1968 2000 2080 1980 1983 1993 2037 +HSync -VSync[/TD]
[/TR]
[TR="bgcolor: #ffffff"]
[TD]CVT-RBv2 Modeline[/TD]
[TD="colspan: 7"]Modeline "1920x1980_60" 244.44 1920 1928 1960 2000 1980 2023 2031 2037 +HSync -VSync[/TD]
[/TR]
[/TABLE]


```
If seeting the resolution via KMS while booting does not work for you, and if it still doesn't recognize the resolution correctly in the DE desktop, then test these modes with 'xrandr' to see which works best for your hardware combination. Since 'xrandr' is not persistent, you could set it as persistent by adding it to the User's .bashrc file (if you were running Wayland)... ut since your PC is using XServer for Graphics, Better is to add the modeline that works best to a User Override xorg.conf file, to declare the mode, and set it...

Is that enough information to start trying things? For more info on xorg.conf files and modlines, I think I have some examples in my Graphics Resolution sticky in my signature line... You should also see which resolution and indicators of any problems in your /var/log/Xorg.0.log file...

Please ask questions if you need anything explained. Please keep me posted on your progress.

---

### Post by ankitprumi on 2021-12-22
Hello @[MAFoElffen]("https://ubuntuforums.org/member.php?u=1044547")[COLOR=#000000] 

Sorry for late response.

I follow your all provided steps. I think you forgot to remove # from this line [/COLOR][FONT=Ubuntu Mono, monospace][COLOR=#000000]#GRUB_GFXMODE=1920x1080x32. I removed this(#) in grub file. Still issue not resolved. I am still confuse in adding new mode lines. It would be great if you access my system using Any desk and help me to fix this issue. would you please give your email id so i can give my any desk id to access PC[/COLOR][/FONT]

[FONT=Ubuntu Mono, monospace][COLOR=#000000]Thank you[/COLOR][/FONT]

---

### Post by MAFoElffen on 2021-12-22
I did forget to remove the '#" comment. Good catch.

Could you please post your /var/log/Xorg.0.log file?

Will PM you...

I'm writing a custom xorg.conf file for you. Did you try the modelines I posted... by trying to add and test them with xrandr to port DP-1?

---

### Post by ankitprumi on 2021-12-22
Hello @[MAFoElffen]("https://ubuntuforums.org/member.php?u=1044547")[COLOR=#000000] [/COLOR]

I checked in var/log folder but didn't found [COLOR=#000000]Xorg.0.log  file
see below attached screenshot
[/COLOR]https://ibb.co/4892xsy

No i didn't try the mode lines

Thank you

---

### Post by MAFoElffen on 2021-12-22
> **ankitprumi said:**
> I checked in var/log folder but didn't found [COLOR=#000000]Xorg.0.log  file
see below attached screenshot
[/COLOR]https://ibb.co/4892xsy

I'm confused now. You system reports that is is using X11 (Not Wayland) as a Graphics Session and is running as Xorg on VTTY2... Hoe can it be running XServer and not be generation an xorg log? Something is very odd about this.

---

### Post by ankitprumi on 2021-12-28
Dear [MAFoElffen]("https://ubuntuforums.org/member.php?u=1044547"), 
Any update ? I am still waiting for solution to fix this issue.

---

### Post by MAFoElffen on 2021-12-28
Background: I had Skype'ed him and looked at screen shares of his machine, while I talked through things... Until I got a call from a girlfriend that she was having a family emergency and needed some moral support.... Until then, the diagnosis was that...

It says it is running X11 and Xorg, not Wayland, but is not creating a /var/log/Xorg.0.log at all. I had him change his default file for his grub defaults, and add Kernel boot parameters for KMS, which it ignores...

The graphics driver for his UHD 630 APU, is the i915, which is being used, and is inside the Kernel. But for some reason, any change to it is being ignored. Almost as when he is upgrading his Grub via...
```

sudo update-grub

```
That it is not picking up the changes... Because through scanning some of his other systems logs, it say his kernel boot line is setting his video to 1024x768... Even though it says in two different ways in his grub defualts, it is setting it to 1920x1080. Not sure if it is really not updating the grub menu, or it is truly ignoring the grub parameters during the boot process, but I didn't see where it was even trying to pass anything for 1920x1080 at all...

That leaves a few things... Which I asked you (the OP) to do to try, and get back to me on. 
(1) Post the output from the above command to see if it finishes successfully.
(2) Try the 5 modelines I gave you via PM and texts, to see if they displayed correctly.
(3) Reinstall Ubuntu 20.04.3 fresh, using the HWE Install.
(4) Reinstall Ubuntu 21.10 fresh, as it would have a newer Kernel, which would be the latest Intel Graphics code.
(5) File a Bug with Launchpad, which would be more detailed diagnostics, and help anyone else with similar hardware.

I left you a list of the above things to try... We talked about all those, except #1. Where are you on those?

---

### Post by guiverc on 2022-01-03
@[MAFoElffen]("https://ubuntuforums.org/member.php?u=1044547")

I just noticed [https://bugs.launchpad.net/ubuntu/+source/ubuntu-release-upgrader/+bug/1956204](https://bugs.launchpad.net/ubuntu/+source/ubuntu-release-upgrader/+bug/1956204) (#ubuntu-bugs-announce) which refers to this thread...

---

### Post by ankitprumi on 2022-01-03
Dear [MAFoElffen]("https://ubuntuforums.org/member.php?u=1044547")[COLOR=#000000] [/COLOR],
I recently upgraded to ubuntu 21.10. But still not solve resolution issue. 


I created the latest system report. 
[https://termbin.com/l7yy](https://termbin.com/l7yy)

---

### Post by Jonners59 on 2022-01-07
> **ankitprumi said:**
> 

Dear Ankit
Thank you for your PM but looking through all the advice in this thread it looks like you are in good hands if you follow the steps.  Have you reported a bug yet as recommended?

Also, I have found in the past that sometimes you end up with multiple GRUB installs.  It may be worth having a cleanout and reinstalling - suggest doing searches here on GRUB issues.  I know that some years ago I had such and there was an application/script someone made that sorted and cleaned the GRUB.

Good luck

Jonathan

---

### Post by MAFoElffen on 2022-01-07
I reviewed the report... I can see from the report that you are now on Linux Kernel  5.13.0-22-generic and have HWE installed. I can see that instead of  using XServer (like previous), that you are now using Wayland. I can see that your are  still only at resolution 1024x768...

Okay... It's time to dive deeper into this... Please post the results of
```

xrandr -q

```
Then install this small utility
```

sudo apt install read-edid

```
Then post the results of 
```

sudo get-edid | sudo parse-edid

```
Then post the results of
```

sudo find /sys | grep -i edid

```
And then post the contents of your '/etc/default/grub" file...

Remember to post all output and file contents within CODE Tags.

---

### Post by Bashing-om on 2022-01-07
ankitprumi - Hey

In response to your PM - I too can add nothing to the help you are already receiving. You are in the best possible hands now.

happy trails

Bashing-om

---

### Post by MAFoElffen on 2022-01-08
You had also PM'ed me... The 'buck stops here' and I am here to help you. Thatimplies that need to be willing to provide me answers to my questions for information. You are "my hands" and eyes with this.

If you look through my posts in this thread, there is a lot I have asked you that you have not answered yet. I am patient. I can wait.

Actually, I was still waiting on answers to my questions 'before" your last PM... All I can say it "Tag. You are it."

---

### Post by QIII on 2022-01-08
@ankitprumi

I hope you are not still PMing for support.  That is a rude disservice to the rest of the community since they will not be able to learn from your experience.

---

### Post by ajgreeny on 2022-01-08
I am late to this discussion but do you have more than one Linux OS on your machine?

If so it could simply be that another OS's grub is in charge of the system, not grub from your current problem OS.

---

### Post by MAFoElffen on 2022-01-08
I told you that I would come back to this thread and help you here...

After I posted here yesterday, you PM'ed me again and asked if I was available today. I am-- Right "HERE" on your thread, where it is appropriate.

I am still waiting for "answers and information" from you **here** on this thread... You have not answered those. Every time I ask you if you had tried the things I have given you to try, you say you have not done those. All my requests for information and how to get that information, seem to be ignored(?) 

Not sure what more I can do, if those things are not done or answered... I'm still waiting patiently on you.

---

### Post by Bashing-om on 2022-01-08
ankitprumi -

^^ +10 
The forum also has the mandate as a platform for learning. That places an onus on all of us to read, comprehend and follow through to the end. We are only as good as the tools that you provide.

Smile
Ubuntu loves you :D

---

### Post by ankitprumi on 2022-01-12
Anyone please suggest solution to fix this issue.

---

### Post by MAFoElffen on 2022-01-13
We have... If you look through this thread, your PM's on this Forum, the messages from Skype with me,.. You have several lists (from me and others) of things to try and report information back, so we can go on with this.

You have done none of those things, nor provided needed feedback where we can go on. "Please help" or "suggest something" is not feedback or any kind of answers to those questions. I can only do so much in a vacuum. I can not read minds. (I wish I could.) Do you not agree?

My latest questions would have explored if your PC does not see the EDID from your LG television... And if your grug.cfg file is actually getting updated with the suggested boot parameters you were given to try...

Maybe look through those and post some of that information. (Please.)

---

### Post by ankitprumi on 2022-01-21
Dear @[COLOR=#000000]MAFoElffen,

We have followed all your steps you provided us. we installed windows 10 and screen resolution works properly. so it's not hardware issue. See below attached screenshots. we spent so many hours on this issue. we are using ubuntu for workstation(web & mobile development)

we are happy if you guide us to resolve this issue in ubuntu.

Thank you[/COLOR]

---

### Post by MAFoElffen on 2022-01-22
I went back through this thread, your PM's and our previous Skype Messages... Here is all th things I have asked you to do, which you have not tried, or were short on returning feedback on:

> **MAFoElffen said:**
> The Intel i950 Graphics Driver is internal to the Linux Kernel... So there are so nay ways to do this...

First by giving the Linux Kernel a 'hint' by passing it a boot parameter to set it in that mode early... Open a terminal session and edit the grub default file in an elevated mode...
```

sudo gedit /etc/default/grub

```
Go down to the line that says
```

#GRUB_GFXMODE=640x480

```
And change it to
```

#GRUB_GFXMODE=1920x1080x32

```
Go to the line that says
```

GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"

```
And change to
```

video=uvesafb:mode_option=1920x1080-32,mtrr=3,scroll=ywrap

```
Save and exit. Update Grub to pick up the changes...
```

sudo update-grub
sudo reboot

```
That should set the resolution of 1920x1080 at the kernel Boot, using KMS, and be at that resolution when the Splash screen starts, then gets to the Graphical login... So it should recognize that mode as 'Native' and preferred. That way everything should be more fluid and forced into something different than it is not...

Once it gets to the desktop, open Settings > Display.... Check the resolution and see that it recognized it as a setting, and that is selected.

If it is still not in that resolution or needs adjustment to display correctly... I have calculated 4 modelines that should work for your APU/Display combination:
```

                                                                                                
XFree86 Modeline    Modeline "1920x1080@60" 182.28 1920 1952 2640 2672 1080 1102 1113 1135
CVT Modeline    Modeline "1920x1980_59.98" 324.75 1920 2072 2280 2640 1980 1983 1993 2051 -HSync +VSync
CVT-RB Modeline    Modeline "1920x1980_59.95" 254 1920 1968 2000 2080 1980 1983 1993 2037 +HSync -VSync
CVT-RBv2 Modeline    Modeline "1920x1980_60" 244.44 1920 1928 1960 2000 1980 2023 2031 2037 +HSync -VSync


```
If setting the resolution via KMS while booting does not work for you, and if it still doesn't recognize the resolution correctly in the DE desktop, then test these modes with 'xrandr' to see which works best for your hardware combination. Since 'xrandr' is not persistent, you could set it as persistent by adding it to the User's .bashrc file (if you were running Wayland)... ut since your PC is using XServer for Graphics, Better is to add the modeline that works best to a User Override xorg.conf file, to declare the mode, and set it...

Is that enough information to start trying things? For more info on xorg.conf files and modlines, I think I have some examples in my Graphics Resolution sticky in my signature line... You should also see which resolution and indicators of any problems in your /var/log/Xorg.0.log file...

Please ask questions if you need anything explained. Please keep me posted on your progress.


## Skype Call.. ##
During the Skype Call, I had you do some commands that scanned your system log, and the Kernel Boot line was still going directly to only 1027x768, which made me thinking that for some reason, that your grub files that the system was booting from were not updating correctly... I asked you to post your /boot/grub.grub.cfg file. Even though thatis dynaimically built, that would have should it it was picking up the changes from your /etc/defaults/grub file successfully. I asked to see you /etc/defaults/grub file, qhixh now you resinstalled to 21.10, so I have no idea what it looks like now...

I also PM'ed you over 5 modelines for you to try, which your TV's manual said it was compliant with. You did not try any of them. The next thing would have been to take a picture of the results of whatused to be called "vbeinfo" from grub cli, to see what modes are possible during the BIOS boot stage... With the latest version of Grub, that command changed names to what is now "videoinfo". 

For the original picture of the error... That is 'early' during the kernel boot, and would need to be dealt with by a boot parameter setting his video... Not by something after the Linux Graphics Layer starts...

> **MAFoElffen said:**
> Background: I had Skype'ed him and looked at screen shares of his machine, while I talked through things... Until I got a call from a girlfriend that she was having a family emergency and needed some moral support.... Until then, the diagnosis was that...

It says it is running X11 and Xorg, not Wayland, but is not creating a /var/log/Xorg.0.log at all. I had him change his default file for his grub defaults, and add Kernel boot parameters for KMS, which it ignores...

The graphics driver for his UHD 630 APU, is the i915, which is being used, and is inside the Kernel. But for some reason, any change to it is being ignored. Almost as when he is upgrading his Grub via...
```

sudo update-grub

```
That it is not picking up the changes... Because through scanning some of his other systems logs, it say his kernel boot line is setting his video to 1024x768... Even though it says in two different ways in his grub defualts, it is setting it to 1920x1080. Not sure if it is really not updating the grub menu, or it is truly ignoring the grub parameters during the boot process, but I didn't see where it was even trying to pass anything for 1920x1080 at all...

That leaves a few things... Which I asked you (the OP) to do to try, and get back to me on.
(1) Post the output from the above command to see if it finishes successfully.
(2) Try the 5 modelines I gave you via PM and texts, to see if they displayed correctly.
(3) Reinstall Ubuntu 20.04.3 fresh, using the HWE Install.
(4) Reinstall Ubuntu 21.10 fresh, as it would have a newer Kernel, which would be the latest Intel Graphics code.
(5) File a Bug with Launchpad, which would be more detailed diagnostics, and help anyone else with similar hardware.

I left you a list of the above things to try... We talked about all those, except #1. Where are you on those?


> **MAFoElffen said:**
> I reviewed the report... I can see from the report that you are now on Linux Kernel 5.13.0-22-generic and have HWE installed. I can see that instead of using XServer (like previous), that you are now using Wayland. I can see that your are still only at resolution 1024x768...

Okay... It's time to dive deeper into this... Please post the results of
```

xrandr -q

```
Then install this small utility
```

sudo apt install read-edid

```
Then post the results of
```

sudo get-edid | sudo parse-edid

```
Then post the results of
```

sudo find /sys | grep -i edid

```
And then post the contents of your '/etc/default/grub" file...

Remember to post all output and file contents within CODE Tags.


****
So you think you can backtrack through those and provide the missing information?

---

### Post by ankitprumi on 2022-01-24
[IMG]https://ibb.co/k4fqGfB[/IMG][COLOR=#0E101A]Dear @[**MAFoElffen**]("https://ubuntuforums.org/member.php?u=1044547"),[/COLOR]
[COLOR=#0E101A]
[/COLOR]
[COLOR=#0E101A]I tried the Linux Kernal process for setting screen resolution. I followed all the steps you provided. After rebooting the system I got grub files logs but the resolution didn't show in the display settings.[/COLOR]
[COLOR=#0E101A]
[/COLOR]
[COLOR=#0E101A]After I  tried setting modelines using the xrandr command. [/COLOR]


[COLOR=#0E101A]But it's still getting the issue. Please see the given below attachments.[/COLOR]
[COLOR=#0E101A]
[/COLOR][https://ibb.co/k4fqGfB](https://ibb.co/k4fqGfB)

[https://ibb.co/MDyT2jC](https://ibb.co/MDyT2jC)[COLOR=#0E101A]
[/COLOR]
[COLOR=#0E101A]Can you please guide how to set modelines? How can I set modelines which are provided by you (four modelines)?

[/COLOR]
[COLOR=#0E101A][IMG]https://ibb.co/k4fqGfB[/IMG][IMG]https://ibb.co/MDyT2jC[/IMG][/COLOR]
[COLOR=#0E101A]Thank you,[/COLOR]
[COLOR=#0E101A]Ankit[/COLOR]

---

### Post by MAFoElffen on 2022-01-24
> **ankitprumi said:**
> [COLOR=#0E101A]I tried the Linux Kernal process for setting screen resolution. I followed all the steps you provided. After rebooting the system I got grub files logs but the resolution didn't show in the display settings.[/COLOR][COLOR=#0E101A]
And "again", where have you posted any of those results? Where is a cut-and-paste of your /etc/default/grub file posted within CODE TAG's? Where is a cut-and-paste of your /boot/gub/grub.cfg file posted within CODE TAG's?[/COLOR]
> **ankitprumi said:**
> 
[COLOR=#0E101A]After I  tried setting modelines using the xrandr command. [/COLOR]

[COLOR=#0E101A]But it's still getting the issue. Please see the given below attachments.[/COLOR]
[https://ibb.co/k4fqGfB](https://ibb.co/k4fqGfB)

[https://ibb.co/MDyT2jC](https://ibb.co/MDyT2jC)[COLOR=#0E101A]
[/COLOR]
[COLOR=#0E101A]"XWAYLAND0" is not a 'port' name interpreted by xrandr... Starnge. What are the results of that if you use Login using XServer instead of Wayland? This is a problem  which I will idscuss further below...
[/COLOR][COLOR=#0E101A]> **ankitprumi said:**
> Can you please guide how to set modelines? How can I set modelines which are provided by you (four modelines)?[/COLOR]
NO... I will not.

Why? So far you do not have a track record of being able to follow instructions very well. There is a danger in setting modelines, that if you do not know what you are doing, which you would have to follow instructions to the letter, or you could damage your display internally. If something like that happens, that is on you, your responsibility... Next, what you just showed me is that you tried one modeline out of the many I calculated for you to try, and when that didn't work, you gave up(?) Or did the other not work also? Show me. And that, and what is really going on, that is why modelines for you would be a last-resort... And that would only covers a part of your problem.

**************
**[COLOR=#ff0000]_[SIZE=3]Where is all the other information???[/SIZE]_[/COLOR]**

Let me tell you why I need that "other information": 

When you LG display comes up, it looks for a preferred mode, which it says is "1920x1080". If not set to that, it displays a message box saying... Presto: The picture you posted in Post #1 in this thread... It needs to be in that mode early in the boot process (so KVM). Modelines which would change the resolution of X in the desktop, do not start or cannot make any affect in change, until after you log in... After the graphical login screen, when the desktop boots and displays.

Your GPU (within your processor can display a lot higher resolution than this, but for some reason, your motherboard limits the resolution down to 1920x1080... Which is okay to you, because that is the mode your display and you want.

Your xrandr results are different than before, where you told me that it was showing your video port as DP-1. It was showing your onboard video port is as a display port?  That was odd enough until now, with the name it came up with... Because here is what you have on your gigabyte motherboard?
> 
Integrated Graphics Processor-Intel[SUP]®[/SUP] HD Graphics support: 
[LIST=1]
[*]1 x D-Sub port, supporting a maximum resolution of 1920x1200@60 Hz 
[/LIST]
 Maximum shared memory of 512 MB

So the Video port on the Board is not even 'digital", it is a 15-pin D-Sub, Analog VGA port... How does that get interpreted as Display Port? Do you have a cable or adapter problem? It seems as such, as the results from xrandr is not showing correctly for that display. There are many modes missing. That is why I need the EDID information queried on that, because something is wrong in how your system does not see your display correctly. Please post those results for that.

But remember me saying it needs to be in that mode early in the boot process? Which means it needs to be down (preferred) with KMS kernel modesetting. Via Grub. For grub to change to a resolution, it needs to be valid in the BIOS of the system, and be seen by the Grub boot loader. This si why I need you to post the results of "videoinfo" from the Grub CLI. I have already posted information on how you can do that twice already... Those would be the Video modes, that your system BIOS can do, and are seen by grub, and can be set at boot... Then with setting at boot, I asked for you to post your [COLOR=#0E101A]/etc/default/grub file, /boot/gub/grub.cfg dile, and the results of sudo update-grub... I don't want to hear you did that... I want to see what it is, and any errors or success. Because what it is is doing, without me seeing those, is not rational...[/COLOR]

Start to understanding why I need that additional information now? If you cannot provide that, then we are at an impasse.

---

### Post by ankitprumi on 2022-01-25
[COLOR=#0E101A]Dear @[**MAFoElffen**]("https://ubuntuforums.org/member.php?u=1044547"),[/COLOR]
[COLOR=#0E101A]
[/COLOR]
[COLOR=#0E101A]I switched Wayland to Xorg by below reference[/COLOR]
[COLOR=#0E101A]
[/COLOR]
[COLOR=#0E101A][https://fostips.com/switch-back-xorg-ubuntu-21-04/](https://fostips.com/switch-back-xorg-ubuntu-21-04/)[/COLOR]
[COLOR=#0E101A]
[/COLOR]
[COLOR=#0E101A]so now when I execute the xrandr command in the terminal it shows DP-1 is connected. See below-attached screenshots[/COLOR]
[COLOR=#0E101A][https://ibb.co/nsdZ0LR](https://ibb.co/nsdZ0LR)[/COLOR]
[COLOR=#0E101A]
[/COLOR]
[COLOR=#0E101A]I updated grub files using commands given by you. See below-attached video[/COLOR]
[COLOR=#0E101A][https://drive.google.com/file/d/1BGJ1hf0HQFDf4Ak5CwRGjkwjzqZZ1Gyp/view?usp=sharing](https://drive.google.com/file/d/1BGJ1hf0HQFDf4Ak5CwRGjkwjzqZZ1Gyp/view?usp=sharing)[/COLOR]
[COLOR=#0E101A]
[/COLOR]
[COLOR=#0E101A][https://ibb.co/B2Ff5t9](https://ibb.co/B2Ff5t9)[/COLOR]
[COLOR=#0E101A]
[/COLOR]
[COLOR=#0E101A]Please See below-attached video of reboot pc[/COLOR]
[COLOR=#0E101A][https://drive.google.com/file/d/1MQX2Kzwz56wzazj253cDo6cJbKLpa9Ah/view?usp=sharing](https://drive.google.com/file/d/1MQX2Kzwz56wzazj253cDo6cJbKLpa9Ah/view?usp=sharing)[/COLOR]
[COLOR=#0E101A]
[/COLOR]
[COLOR=#0E101A]I applied the 3 modelines (out of 4) given by you.

[/COLOR]
[COLOR=#0E101A] ```

 cvt 1920 1980 60
```[/COLOR]```

[COLOR=#0E101A] xrandr --newmode  "..."[/COLOR]
[COLOR=#0E101A] xrandr --addmode DP-1 "..."[/COLOR]

```[COLOR=#0E101A]

[/COLOR]
[COLOR=#0E101A]
[/COLOR]
[COLOR=#0E101A]See below video of setting modeline for 1920 * 1080 resolution.[/COLOR]
[COLOR=#0E101A][https://drive.google.com/file/d/1xMHwuM8hHTtEB5yFYwtvofB4xkGqc9_E/view?usp=sharing](https://drive.google.com/file/d/1xMHwuM8hHTtEB5yFYwtvofB4xkGqc9_E/view?usp=sharing)[/COLOR]
[COLOR=#0E101A]
[/COLOR]
[COLOR=#0E101A]when I set resolution 1920 * 1080 it shows dark on both left and right sides(vertical). Please see below-attached image[/COLOR]
[COLOR=#0E101A][https://ibb.co/GRZQfdk](https://ibb.co/GRZQfdk)[/COLOR]
[COLOR=#0E101A]
[/COLOR]
[COLOR=#0E101A]Please see the video of setting modeline for 1920 * 1980_60 resolution. [/COLOR]
[COLOR=#0E101A][https://drive.google.com/file/d/1Cw_-rVd4ecov39guzPcpG6WBOrbhoufR/view?usp=sharing](https://drive.google.com/file/d/1Cw_-rVd4ecov39guzPcpG6WBOrbhoufR/view?usp=sharing)[/COLOR]
[COLOR=#0E101A]
[/COLOR]
[COLOR=#0E101A]Please see the video of setting modeline for 1920 * 1980_59.98 resolution. (It's not working)[/COLOR]
[COLOR=#0E101A][https://drive.google.com/file/d/15HkAdF31nayOfDrfpaHPX-BI0mX75Vtm/view?usp=sharing](https://drive.google.com/file/d/15HkAdF31nayOfDrfpaHPX-BI0mX75Vtm/view?usp=sharing)[/COLOR]
[COLOR=#0E101A]
[/COLOR]
[COLOR=#0E101A]Please see the video of setting modeline for 1920 * 1980_59.95 resolution. (It's not working)[/COLOR]
[COLOR=#0E101A][https://drive.google.com/file/d/1Ua69JXZe862SS3eFHyQo_n7PIgw-rK-o/view?usp=sharing](https://drive.google.com/file/d/1Ua69JXZe862SS3eFHyQo_n7PIgw-rK-o/view?usp=sharing)[/COLOR]
[COLOR=#0E101A]
[/COLOR]
[COLOR=#0E101A]Below are the results of various commands. [/COLOR]
[COLOR=#0E101A]
[/COLOR]
[COLOR=#0E101A]xrandr -q[/COLOR]
[COLOR=#0E101A]
[/COLOR]
```

[COLOR=#0E101A]Screen 0: minimum 320 x 200, current 1024 x 768, maximum 16384 x 16384[/COLOR]
[COLOR=#0E101A]DP-1 connected primary 1024x768+0+0 (normal left inverted right x axis y axis) 0mm x 0mm[/COLOR]
[COLOR=#0E101A]  1024x768 60.00* [/COLOR]
[COLOR=#0E101A]  800x600 60.32 56.25  [/COLOR]
[COLOR=#0E101A]  848x480 60.00  [/COLOR]
[COLOR=#0E101A]  640x480 59.94  [/COLOR]
[COLOR=#0E101A]  1920x1080_60.00 59.96  [/COLOR]
[COLOR=#0E101A]  1920x1980_59.98 59.93  [/COLOR]
[COLOR=#0E101A]  1920x1980_59.95 59.93  [/COLOR]
[COLOR=#0E101A]  1920x1980_60.00 59.98  [/COLOR]
[COLOR=#0E101A]HDMI-1 disconnected (normal left inverted right x axis y axis)[/COLOR]

```
[COLOR=#0E101A]
[/COLOR]
[COLOR=#0E101A]sudo apt install read-edid[/COLOR]
[COLOR=#0E101A]
[/COLOR]
```

[COLOR=#0E101A]Reading package lists... Done[/COLOR]
[COLOR=#0E101A]Building dependency tree... Done[/COLOR]
[COLOR=#0E101A]Reading state information... Done[/COLOR]
[COLOR=#0E101A]read-edid is already the newest version (3.0.2-1.1).[/COLOR]
[COLOR=#0E101A]The following packages were automatically installed and are no longer required:[/COLOR]
[COLOR=#0E101A] chromium-codecs-ffmpeg-extra gstreamer1.0-vaapi libgstreamer-plugins-bad1.0-0 libva-wayland2[/COLOR]
[COLOR=#0E101A]Use 'sudo apt autoremove' to remove them.[/COLOR]
[COLOR=#0E101A]0 upgraded, 0 newly installed, 0 to remove and 11 not upgraded.[/COLOR]

```
[COLOR=#0E101A]
[/COLOR]
[COLOR=#0E101A]sudo get-edid | sudo parse-edid[/COLOR]
```

[COLOR=#0E101A]This is read-edid version 3.0.2. Prepare for some fun.[/COLOR]
[COLOR=#0E101A]Attempting to use i2c interface[/COLOR]
[COLOR=#0E101A]No EDID on bus 0[/COLOR]
[COLOR=#0E101A]No EDID on bus 1[/COLOR]
[COLOR=#0E101A]No EDID on bus 2[/COLOR]
[COLOR=#0E101A]No EDID on bus 4[/COLOR]
[COLOR=#0E101A]No EDID on bus 5[/COLOR]
[COLOR=#0E101A]No EDID on bus 6[/COLOR]
[COLOR=#0E101A]No EDID on bus 7[/COLOR]
[COLOR=#0E101A]No EDID on bus 8[/COLOR]
[COLOR=#0E101A]No EDID on bus 9[/COLOR]
[COLOR=#0E101A]No EDID on bus 10[/COLOR]
[COLOR=#0E101A]1 potential busses found: 3[/COLOR]
[COLOR=#0E101A]Bus 3 doesn't really have an EDID...[/COLOR]
[COLOR=#0E101A]Couldn't find an accessible EDID on this computer.[/COLOR]
[COLOR=#0E101A]Attempting to use the classical VBE interface[/COLOR]
[COLOR=#0E101A]
[/COLOR]
[COLOR=#0E101A]Performing real mode VBE call[/COLOR]
[COLOR=#0E101A]Interrupt 0x10 ax=0x4f00 bx=0x0 cx=0x0[/COLOR]
[COLOR=#0E101A]Function unsupported[/COLOR]
[COLOR=#0E101A]Call failed[/COLOR]
[COLOR=#0E101A]
[/COLOR]
[COLOR=#0E101A]VBE version 0[/COLOR]
[COLOR=#0E101A]VBE string at 0x0 "O&#65533;"[/COLOR]
[COLOR=#0E101A]
[/COLOR]
[COLOR=#0E101A]VBE/DDC service about to be called[/COLOR]
[COLOR=#0E101A]Report DDC capabilities[/COLOR]
[COLOR=#0E101A]
[/COLOR]
[COLOR=#0E101A]Performing real mode VBE call[/COLOR]
[COLOR=#0E101A]Interrupt 0x10 ax=0x4f15 bx=0x0 cx=0x0[/COLOR]
[COLOR=#0E101A]Function unsupported[/COLOR]
[COLOR=#0E101A]Call failed[/COLOR]
[COLOR=#0E101A]
[/COLOR]
[COLOR=#0E101A]Reading next EDID block[/COLOR]
[COLOR=#0E101A]
[/COLOR]
[COLOR=#0E101A]VBE/DDC service about to be called[/COLOR]
[COLOR=#0E101A]Read EDID[/COLOR]
[COLOR=#0E101A]
[/COLOR]
[COLOR=#0E101A]Performing real mode VBE call[/COLOR]
[COLOR=#0E101A]Interrupt 0x10 ax=0x4f15 bx=0x1 cx=0x0[/COLOR]
[COLOR=#0E101A]Function unsupported[/COLOR]
[COLOR=#0E101A]Call failed[/COLOR]
[COLOR=#0E101A]
[/COLOR]
[COLOR=#0E101A]The EDID data should not be trusted as the VBE call failed[/COLOR]
[COLOR=#0E101A]Error: output block unchanged[/COLOR]
[COLOR=#0E101A]I'm sorry nothing was successful. Maybe try some other arguments[/COLOR]
[COLOR=#0E101A]if you played with them, or send an email to Matthew Kern <pyrophobicman@gmail.com>.[/COLOR]
[COLOR=#0E101A]Partial Read... Try again[/COLOR]

```
[COLOR=#0E101A]
[/COLOR]
[COLOR=#0E101A]sudo find /sys | grep -i edid[/COLOR]
[COLOR=#0E101A]
[/COLOR]
```

[COLOR=#0E101A]/sys/kernel/debug/dri/0/HDMI-A-1/edid_override[/COLOR]
[COLOR=#0E101A]/sys/kernel/debug/dri/0/DP-1/edid_override[/COLOR]
[COLOR=#0E101A]/sys/devices/pci0000:00/0000:00:02.0/drm/card0/card0-HDMI-A-1/edid[/COLOR]
[COLOR=#0E101A]/sys/devices/pci0000:00/0000:00:02.0/drm/card0/card0-DP-1/edid[/COLOR]
[COLOR=#0E101A]/sys/module/drm_kms_helper/parameters/edid_firmware[/COLOR]
[COLOR=#0E101A]/sys/module/drm/parameters/edid_firmware[/COLOR]
[COLOR=#0E101A]/sys/module/drm/parameters/edid_fixup[/COLOR]

```
[COLOR=#0E101A]
[/COLOR]
[COLOR=#0E101A]Please see attached video of these various commands[/COLOR]
[COLOR=#0E101A][https://drive.google.com/file/d/1fEYNoflze9UNgXNRXwFhuz11YCcit8y6/view?usp=sharing](https://drive.google.com/file/d/1fEYNoflze9UNgXNRXwFhuz11YCcit8y6/view?usp=sharing)[/COLOR]
[COLOR=#0E101A]
[/COLOR]
[COLOR=#0E101A]Below are the lists I tried[/COLOR]
[COLOR=#0E101A]
[/COLOR]
[COLOR=#0E101A](1) Post the output from the above command to see if it finishes successfully. (Done)[/COLOR]
[COLOR=#0E101A](2) Try the 5 modelines I gave you via PM and texts, to see if they displayed correctly. (Done)[/COLOR]
[COLOR=#0E101A](3) Reinstall Ubuntu 21.10 fresh, as it would have a newer Kernel, which would be the latest Intel Graphics code. (Done)

Thank You,
Ankit[/COLOR]

---

### Post by MAFoElffen on 2022-01-25
Very good work.

One thing you forgot, that I reminded you of in my last post... I posted the instructions of it twice already. I will give instructions now for the third time:
Boot up your computer and just after the BIOS POST, repeaeted hit the <ESC> key to bring up the Grub Boot Menu. At the Grub Boot Menu, press the <C> key to drop down to a Grub CLI prompt. Enter the Command
```

videoinfo

```
Take a picture of the output... Remember? These will be the video settin which the BIOS of your motherboard says it can do, and what Grub sees from the connected display...

One more new command to post output of now. Based on the output that you just posted. 
```

sudo parse-edid < [COLOR=#0E101A]/sys/devices/pci0000:00/0000:00:02.0/drm/card0/card0-DP-1/edid[/COLOR]

```
That is the port that xrandr says is connected to a display...

There is an "oddity" from your output. xrandr and your booted Linux system says that are two video ports physically there (HDMI-1 an DP-1), with one connected (DP-1). Both are on bus 0, slot 2, which would be the APU of your CPU... The Spec's for your Gigabyte Motherboard say that is only has a VGA Port. This conflicts. 

*** Please take a picture of the back of your computer showing the video ports. If you can open your case cover and see the Gigabyte motherboard "model number", please take a picture of it.

---

### Post by ankitprumi on 2022-01-26
[COLOR=#0E101A]Dear @[MAFoElffen]("https://ubuntuforums.org/member.php?u=1044547")[/COLOR][COLOR=#0E101A]
[/COLOR]
[COLOR=#0E101A]Please see the below attachment of videoinfo results[/COLOR][COLOR=#0E101A]
[/COLOR]
[https://ibb.co/PFLctbZ](https://ibb.co/PFLctbZ)

[COLOR=#0E101A]See below attachment of computer back portion[/COLOR][COLOR=#0E101A]
[/COLOR]
[https://ibb.co/HzBpnTB](https://ibb.co/HzBpnTB)
[https://ibb.co/hDvQ4zk](https://ibb.co/hDvQ4zk)[COLOR=#0E101A]
[/COLOR]
[COLOR=#0E101A]Gigabyte motherboard model number is: H410M S2 V3 (1.1/1.3)[/COLOR]
[COLOR=#0E101A]
[/COLOR]
[COLOR=#0E101A]Thank you,[/COLOR]
[COLOR=#0E101A]Ankit [/COLOR]

---

### Post by MAFoElffen on 2022-01-26
The two pictures the back of your PC and the cable... Not really being a cable, but an off-brand, low-end VGA to HDMI adapter. That is your problem/challenge.

Is it not a direct hookup to your display, that a cable would be. This device being between your computer, and your display, is why your system does not see the EDID Table from your display. Rather, it sees the capabilies of the VGA to HDMI adapter, which is the three resolutions 1024x768x32, 800x600x32, and 640x480x32. That is why KMS uses the highest of those 3, 1024x768. That is why those 3 resolutions show in Ubuntu Settings...

And since it is converting analog to digital, by a translation, that is why the modeset's are getting distorted. Why because there is never a direct sync between the two ends.

Your monitor LG 24mp88hv-s Display has 2 HDMI ports and 1 D-sub (and a 3mm Audio In). If you connect a D-Sub cable directly from your computer to the D-Sub on your computer... and an audio cable between both... Without that VGA to HDMI adapter, everything should just start working. The system will hten see your monitor and all your modes from the Display will be seen by the computer. It will be plug-and-play. 

If you want to tweak it "after" that, the KMS Modesetting and other features will be fixed by that also. (Where they can be set and will be honored.)

*** This is why the system could be see the modes of you monitor, whihc is within it's EDID tables.

---

### Post by ankitprumi on 2022-01-26
[COLOR=#0E101A]Dear @[MAFoElffen]("https://ubuntuforums.org/member.php?u=1044547") [/COLOR]
[COLOR=#0E101A]
[/COLOR]
[COLOR=#0E101A]I am wondering if resolution works properly in windows 10 then why is it's an issue in ubuntu 21.10?[/COLOR]
[COLOR=#0E101A]
[/COLOR]
[COLOR=#0E101A]Thank You, [/COLOR]
[COLOR=#0E101A]Ankit[/COLOR]

---

### Post by MAFoElffen on 2022-01-26
Linux depends on the hardware and the signals from to confirm compatibility to help it know what it is connected to. It runs on many things. without specialized drivers.

Windows doesn't claim to work on everything, so it just pushes what it should be without the 'confirmation' first.Your Display probably had a driver, that LG provided to MS, and that  driver said it could do certain things... So Windows didn't have to  guess. If there is a problem, then the hardware is suspect first... Then adjustments and drivers.

MS is starting to go the route of Apple... Where your hardware needs to be "this level of standards" to be able to run and not have problems. But say that in a less kind way: System Requirements, or be left behind.

That is not to say that Windows doesn't have their own peculiar problems. I was a Dell. HP & Lenovo Service Tech. A user should not have t reinstall Windows 11 5-6 times, in as many months, on their own, (While under warranty on a new computer) because MS was working things out.

---

### Post by ankitprumi on 2022-01-26
Hello @[MAFoElffen]("https://ubuntuforums.org/member.php?u=1044547")[COLOR=#000000] 

Thank you so much for your help. Currently we are using HDMI to VGA converter. We will try other HDMI cables and check if the issue is resolve.

Thank You,
Ankit[/COLOR]

---

