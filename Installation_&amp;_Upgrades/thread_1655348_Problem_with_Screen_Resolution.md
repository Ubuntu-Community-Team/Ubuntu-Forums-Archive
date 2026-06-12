---
title: "Problem with Screen Resolution"
date: 2010-12-29
forum: Installation &amp; Upgrades
---

### Post by saimanoj on 2010-12-29
[LEFT]I installed a new copy of Ubuntu 10.10(Maverick). I tried it for some time before installing and also after installing its fine. But when i updated my sytem using the "Update Manager"(it is nearly 200 MB) and restarted the system my system resolution is really unbearable(640x480) for my 19 Inches Wide screen Monitor. Many windows pushed their important buttons outside of the screen and when i tried to change the screen resolution using ARandR there is only one other option i.e. is 320x240 which is still low.

I used Ubuntu previously for a small time before i have an internet connection(9.04 and 9.10). Then again used Ubuntu 10.04 Ultimate Edition 2.6 for a few days. Now I have internet connection but updating gave me a good desktop resolution after some copy and paste of commands. I remember a command xrandr out of them.
But typing xrandr now gives an error msg.
The result of the command is as follows:

saimanoj@saimanoj-desktop:~/c$ xrandr
xrandr: Failed to get size of gamma for output default
Screen 0: minimum 320 x 240, current 640 x 480, maximum 640 x 480
default connected 640x480+0+0 0mm x 0mm
   640x480        50.0* 
   320x240        51.0  

Info: I am using an Nvidia graphic card with Intel Core 2 Duo processor x64 architecture.
Please tell me how to get a decent resolution for my desktop.
I really love Ubuntu. So, please help me love it more...
[/LEFT]

---

### Post by sikander3786 on 2010-12-29
Please post the output of these commands.

Applications > Accessories > Terminal:

```
lspci | grep VGA
```

```
glxinfo | grep vendor
```

```
cat /etc/X11/xorg.conf
```

Note, capital 'X' for X11.

---

### Post by saimanoj on 2010-12-29
The output of the specified commands are as follows:

saimanoj@saimanoj-desktop:~$ lspci|grep VGA
01:00.0 VGA compatible controller: nVidia Corporation G96 [GeForce 9400 GT] (rev a1)


saimanoj@saimanoj-desktop:~$ glxinfo | grep vendor
server glx vendor string: NVIDIA Corporation
client glx vendor string: NVIDIA Corporation
OpenGL vendor string: NVIDIA Corporation


saimanoj@saimanoj-desktop:~$ cat /etc/X11/xorg.conf

Section "Screen"
    Identifier    "Default Screen"
    DefaultDepth    24
EndSection

Section "Module"
    Load    "glx"
EndSection

Section "Device"
    Identifier    "Default Device"
    Driver    "nvidia"
    Option    "NoLogo"    "True"
EndSection


Thanks for your reply.

---

### Post by sikander3786 on 2010-12-29
Try reconfiguring your graphics.

```
sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.old
```

```
sudo dpkg-reconfigure -phigh xserver-xorg
```

Reboot.

Let us know how that goes :-)

---

### Post by saimanoj on 2010-12-29
Both of the commands executed without displaying any errors or any output on terminal.

After Rebooting.

It is a little bit better now as i can change the resolution to 800x600.
Can I increase it a little further to 1024x768.

Previously when i was using Ubuntu 10.04 Ultimate Edition 2.6 (which has many built-in softwares by default). It supported a very good desktop graphics and effects. Also please tell me good softwares or packages for enabling good desktop effects.

Thanks for your reply.

---

### Post by saimanoj on 2010-12-29
Also my screen is displaced towards right by one cm.
How to correct it.

---

### Post by cause4concern on 2010-12-30
Hi,
I just found my computer with a similar problem when I turned it on today. After browsing the forums for an hour, I found that the working solution is described here:

[http://www.ubuntugeek.com/how-change-display-resolution-settings-using-xrandr.html](http://www.ubuntugeek.com/how-change-display-resolution-settings-using-xrandr.html)

I hope it works for you. 

About the displacement by one cm, that is probably just the monitor setting. When this happens on my monitor, I just hit the auto-adjust button which does the job in under 2 seconds. You may have to do it manually via the on-screen menu of your monitor.

Peace.

---

### Post by saimanoj on 2010-12-30
Thankyou cause4concern.
You reminded me of the auto adjust button of my monitor.
It helped me a lot.

---

### Post by saimanoj on 2010-12-30
When i execute the command xrandr this is what it says..

saimanoj@saimanoj-desktop:~$ xrandr
xrandr: Failed to get size of gamma for output default
Screen 0: minimum 640 x 480, current 800 x 600, maximum 800 x 600
default connected 800x600+0+0 0mm x 0mm
   800x600        61.0* 
   640x480        60.0  
  1024x768_60.00 (0x5e)   63.5MHz
        h: width  1024 start 1072 end 1176 total 1328 skew    0 clock   47.8KHz
        v: height  768 start  771 end  775 total  798           clock   59.9Hz

I have just executed this command:
$ xrandr --newmode “1024x768_60.00&#8243;   63.50  1024 1072 1176 1328  768 771 775 798 -hsync +vsync
xrandr: Failed to get size of gamma for output default
X Error of failed request:  BadName (named color or font does not exist)
  Major opcode of failed request:  150 (RANDR)
  Minor opcode of failed request:  16 (RRCreateMode)
  Serial number of failed request:  19
  Current serial number in output stream:  19

is the output on terminal.

Then the next command in sequence as shown in the above link is 
$ xrandr --addmode VGA1 1024x768_60.00
xrandr: Failed to get size of gamma for output default
xrandr: cannot find output "VGA1"

So, its not working.
Please tell me how to increase my screen resolution further.
Thanks in advance.

---

### Post by saimanoj on 2010-12-30
Please tell me if there is a way to remove any installed drivers.
I think it will be fine if i can uninstall all the graphic drivers of nvidia.

---

### Post by cause4concern on 2010-12-30
I'm glad I helped at least a little bit. It seems you may have a bit different problem than me, I was just hoping the same solution would work for you. 
I don't know what is the "gamma output" problem about, you have to google that on your own. However I do have one more piece of advice. The "VGA1" parameter of the xrandr command has to be replaced with one that's valid for your computer, for example, in my case it was VGA-0 (with the dash). You can find out what it is, if you install a package named ARANDR and run it from System => Preferences.


good luck :p

---

### Post by saimanoj on 2010-12-30
I have ARandR already installed, but where in that software can i know which VGA is with me.

---

### Post by worxguy on 2010-12-30
Just finished a similar scenario last night. Attempted to upgrade to 10.10 thru update manager. All went well until reboot, which almost immediately shut down to black screen. Restarted in recovery mode and ended up with the resolution issue you describe. Finally figured out my nvidia driver was gone/not working. Managed to get into system>administration>additional drivers and downloaded/installed nvidia version 173. Problem resolved. But, now, About Ubuntu tells me I'm running Ubuntu 11.04 Natty Narwhal. How can that be?
Good luck,
worxguy

---

### Post by saimanoj on 2010-12-31
But I cant find system>administration>additional drivers
Please tell me precisely as i am a newbie..
Also please tell me how to know the current Ubuntu version( any command please).

Actually now you are running Ubuntu 11.04 Natty Narwhal Alpha 1 Release, which is already released.
For more information 
[http://www.ubuntu.com/testing/natty/alpha1](http://www.ubuntu.com/testing/natty/alpha1)

---

### Post by cause4concern on 2010-12-31
You can reveal your version of Ubuntu by clicking System => About :) I'm sorry but everything else at this point goes beyond my Linux knowledge, I wish I could help more. I just started reading the Linux Administration Handbook, which I got for XMAS. Perhaps I can help in a few months :-)

:lolflag:

---

### Post by worxguy on 2011-01-01
[B][I]But I cant find system>administration>additional drivers"
[/I][/B]
Nope. They don't show, because of the screen resolution issue. Keystrokes Alt+F1 should reveal them, tho.

[B][I]Actually now you are running Ubuntu 11.04 Natty Narwhal Alpha 1 Release, which is already released.
For more information 
[http://www.ubuntu.com/testing/natty/alpha1](http://www.ubuntu.com/testing/natty/alpha1):[/I][/B]
I don't know about that, but running lsb_release -a in a terminal will tell you what version you really have.

Then, there's this bug report:
[https://bugs.launchpad.net/ubuntu/+source/ubuntu-docs/+bug/690248](https://bugs.launchpad.net/ubuntu/+source/ubuntu-docs/+bug/690248)

good luck,
worxguy

---

### Post by saimanoj on 2011-01-02
> [B][I]Actually now you are running Ubuntu 11.04 Natty Narwhal Alpha 1 Release, which is already released.
For more information 
[http://www.ubuntu.com/testing/natty/alpha1](http://www.ubuntu.com/testing/natty/alpha1):[/I][/B]
I don't know about that, but running lsb_release -a in a terminal will tell you what version you really have.

Then, there's this bug report:
[https://bugs.launchpad.net/ubuntu/+s...cs/+bug/690248]("https://bugs.launchpad.net/ubuntu/+source/ubuntu-docs/+bug/690248")
Yes, i think you are right. It is a bug.
I thought that you have upgraded to Ubuntu 11.04 Natty Narwhal by typing "update-manager -d" in the Run Application(press Alt+F2) but i think i was wrong.

---

### Post by saimanoj on 2011-01-02
> **worxguy said:**
> [B][I]But I cant find system>administration>additional drivers"
[/I][/B]
Nope. They don't show, because of the screen resolution issue. Keystrokes Alt+F1 should reveal them, tho.



But when I press Alt+F1 my Applications Menu is opening.
How to open the Additional Drivers.
Please Help

---

### Post by saimanoj on 2011-01-02
I set my screen resolution to 800x600 from 640x480
From the beginning onwards it is going back to the previous resolution(640x480) every time i restart(or shutdown ) my computer. How to make the change premanent??

---

### Post by saimanoj on 2011-01-04
Hello Everybody,
Please help me set my screen resolution properly
it is really awkward after installing updates using Update Manager.
Do I have to reinstall Ubuntu for this Issue.

---

### Post by dino99 on 2011-01-04
ok give it a try,

As actual kernel directly deals with X, there is no need of oldish xorg.conf, so remove it:

sudo rm /etc/X11/xorg.conf

first be sure to use only genuine ubuntu repo:
open synaptic (system admin synaptic) repo tabs to check your prefs (disable exotic repo if any)

then update and search "nvidia" on top of synaptic: remove/purge (right click) ALL the installed nvidia packages, then reinstall: nvidia-current, nvidia-common, nvidia-settings

then reboot

---

### Post by saimanoj on 2011-01-05
> **dino99 said:**
> ok give it a try,

As actual kernel directly deals with X, there is no need of oldish xorg.conf, so remove it:

sudo rm /etc/X11/xorg.conf

first be sure to use only genuine ubuntu repo:
open synaptic (system admin synaptic) repo tabs to check your prefs (disable exotic repo if any)

then update and search "nvidia" on top of synaptic: remove/purge (right click) ALL the installed nvidia packages, then reinstall: nvidia-current, nvidia-common, nvidia-settings

then reboot
Please tell me what is repo , exotic repo and how to disable it.
Thankyou dino99.

Additional Info : 
1) Now I am running Ubuntu 11.04 Alpha 1 release.
2) I am a Newbie.

---

### Post by saimanoj on 2011-01-30
I solved it by removing the nvidia-173 driver using software center.
It is working well now.
Thank you all of you

---

