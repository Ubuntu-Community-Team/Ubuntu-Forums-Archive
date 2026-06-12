---
title: "HP DV2700 laptop, ubuntu, lubuntu nvidia video card problems"
date: 2015-05-01
forum: Installation &amp; Upgrades
---

### Post by aaronr2 on 2015-05-01
I am trying to get ubuntu 14.04 on my laptop. hp dv2700, nvidia geforce 7150m, 4gb ram, amd 64 bit processor.

After installing the system works but the video is very very glitchy, odd colors in the wrong places, yellow boxes in the screen, very slow response. 

I did the sudo apt-get update and upgrade then installed the driver needed in the additional driver menu, then after reboot I get a black screen, no menus, no login, nothing but blank.

I thought maybe ubuntu was not going to work for me so I tried mint, even worse video issue, black screen with a white box in the top left 1/3 of the screen.

Then tonight I tried lubuntu, same thing as mint, black screen with the top 1/3 a white box.


I have googled this and followed instructions with no luck.

Any ideas or things to try? It worked great on ubuntu 12.10 but no one upgraded it and support ran out.

---

### Post by aaronr2 on 2015-05-02
No ideas at all?

---

### Post by Vladlenin5000 on 2015-05-04
Well, the first idea that comes to mind is to stop distro hopping. All those you tried are the same under the hood and the available drivers are also the same. Everything that matters is really the same. That "Windows mentality" of trowing software after software hoping that some will stick isn't conducive here.

Now, your machine... It's old but should be enough for standard Ubuntu. Are you sure about the graphics? Anywhere I looked I see an Intel Graphics Media Accelerator X3100 mentioned, not Nvidia. What driver have you installed exactly?

---

### Post by kc1di on 2015-05-04
you need to install the correct nvidia proprietary drive for that card. go to software center >edit>additional drivers and install the recommended driver.
you may need to use the nomodeset parameter in the boot line to get to it the first time. good luck.  
I believe the driver you want is the 346.xx [ here is a page]("http://www.howopensource.com/2012/10/install-nvidia-geforce-driver-in-ubuntu-12-10-12-04-using-ppa/") that can help.

---

### Post by aaronr2 on 2015-05-09
Sorry for the late reply, I was away for a bit.

I was "distro hopping" because I thought maybe 14.04 was too much for the hardware.

I went to the additional drivers tool and added the correct driver. After which the system boots only to a black screen with no graphics, cannot even access the terminal after the driver is added.


Yes, I am sure it is Nvidia graphics.

---

### Post by Bashing-om on 2015-05-09
aaronr2; Hello;

We are here to help;
Let's get an idea of what is going on, and what should be happening that is not:
post back the outputs of terminal commands:
```

lspci -vnn | grep VGA -A 12
sudo lshw -C display
cat /var/log/Xorg.0.log

```

Maybe all we need to do is clean things up and then install the correct graphics driver.

[INDENT][INDENT]it could happen
[/INDENT][/INDENT]

---

### Post by aaronr2 on 2015-05-09
> **Bashing-om said:**
> aaronr2; Hello;

We are here to help;
Let's get an idea of what is going on, and what should be happening that is not:
post back the outputs of terminal commands:
```

lspci -vnn | grep VGA -A 12

[B][I]00:12.0 VGA compatible controller [0300]:Nvidia corporation c67 [Geforce 7150M/ nforce 630M] [10de:0531] (rev a2) (prog-if 00 [VGA controller])
[/I][/B] [B][I]Sub system: hewlett-Packard company device [103c:30d6]
[/I][/B][B][I]flags : bus master, 66mhz, fast devsel, latency 0, IRQ 42
[/I][/B][B][I]memory at f4000000 (32bit, non prefechable) [size=16m]
[/I][/B][B][I]memory at d000000 (64bit, prefetchable) [size=256m]
[/I][/B][B][I]memory at f000000 64bit, (non prefetchable) [size=16m]
[/I][/B][B][I][virtual] expansion ROM at f1000000 [disabled] [size=128k]
[/I][/B][B][I]capabilities:access denied
kernel driver in use: nouveau

00:18.0 Host bridge [0600]: advanced micro devices, inc. [AMD] k8 [athlon64/opteron] hypertransport technology configuration [1022:1100]
flags: fast devsel

[/I][/B]
sudo lshw -C display

[B][I]description: vga compatible controller
[/I][/B][B][I]product: c67 geforce 7150m/ nforce 630m
[/I][/B][B][I]vendor: NVIDIA corporation
[/I][/B][B][I]physical id:12
[/I][/B][B][I]bus info: pci@0000:00:12.0
[/I][/B][B][I]version a2
[/I][/B]***width 64 bits***
[B][I]clock 66mhz
[/I][/B][B][I]capabilities pm msi vga_controller bus_master cap_list rom
[/I][/B][B][I]configuration:driver=noveau latency=0
resources:irq:42 memory:f4000000-f4fffff memory:d000000-dffffff memory:f000000-f0fffff memory:f1000000-f101ffff




[/I][/B]
cat /var/log/Xorg.0.log
***bash: cat/var/log/Xorg.0.log: no such file or directory***


```

Maybe all we need to do is clean things up and then install the correct graphics driver.
[INDENT][INDENT]it could happen
[/INDENT]
[/INDENT]



Now this is a fresh install, as soon as I add the Nvidia driver and reboot it goes to a blank screen on boot, cant access terminal or anything.

---

### Post by Bashing-om on 2015-05-09
aaronr2; Well;

As you can see presently the opensource driver 'nouveau' is installed.
Want to try and install the Nvidia proprietary driver available in ubunu's software repository ? - Worth a shot -
```

sudo service lightdm stop
sudo apt-get update
sudo apt-get upgrade
sudo apt-get install linux-headers-generic
sudo apt-get install nvidia-current nvidia-settings

```
Reboot the system, and now do you boot to the GUI ?

[INDENT][INDENT]Maybe yes
[INDENT][INDENT][INDENT]could be not so yes
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by aaronr2 on 2015-05-09
I completed that. Reboots to a solid black screen :(

---

### Post by Bashing-om on 2015-05-09
aaronr2; Humm ....

Totally unexpected result of a "black screen" .
Let's look and try and see what the story is:
Can you boot to terminal ? At the login screen what results with key combo ctl+alt+F1 ?
Else we do other to get to a terminal.
Post back these outputs.
```

dpkg -l | grep -i nvidia
sudo lshw -C display
cat /var/log/Xorg.0.log

```
If needed we can install the pastebin utility to relay info .

[INDENT][INDENT]how come, why not
[/INDENT][/INDENT]

---

### Post by aaronr2 on 2015-05-09
I'm running in recovery mode because ctrl alt f1 still only produces a blank screen. it appears the left part of the screen is cut off in the terminal in recovery mode, hopefully that doesn't affect us.

> **Bashing-om said:**
> aaronr2; Humm ....

Totally unexpected result of a "black screen" .
Let's look and try and see what the story is:
Can you boot to terminal ? At the login screen what results with key combo ctl+alt+F1 ?
Else we do other to get to a terminal.
Post back these outputs.
```

dpkg -l | grep -i nvidia

****[I][B]ii libcuda-304 304.125-0ubuntu0.0.1
amd64 nvidia cuda runtime library
ii nvidia-304 304.125-0ubuntu0.0.1
amd64 nvidia legacy binary driver - version 304.125
ii nvidia-current 304.125-0ubuntu0.0.1
amd64 transitional package for nvidia-current
ii nvidia-libopencl1-304 304.125-0ubuntu0.0.1
amd64 nvidia opencl driver and icd loader library
ii-nvidia-opencl-icd-304 304.125-0ubuntu0.0.1
amd64 nvidia opencl icd
ii nvidia-settings 331.20-ubuntu8
amd64 tool for configuring nvidia graphics driver[/B][/I]

sudo lshw -C display

[I][B]description: vga compatible controller
product: c67 [geforce 7150m/ nforce630m]
vendor: nvidia corporation
physical id: 12
bus info: pci@0000:00:12.0
version: a2
width: 64 bits
clock: 66mhz
capabilities: pm msi vga_controller bus_master cap_list rom
configuration: driver=nvidia latency=0
resources: irq:19 memory f4000000-f4fffff memory:d000000-dffffff memory:f000000-f0fffff memory: f100000-f101ffff[/B][/I]

cat /var/log/Xorg.0.log

[I][B][  27.753] (**) nvidia(0) :frequincies has been enabled on all display devices.)
[27.774] (II) xkb: reuse xkmfile /var/lib/xkb/server-B20D7FC7F597315E3E501AEF10E0D866E8E92.xkm
[31.465] (II) xkb: reusue xkmfile/var/lib/xkb/server-34CEB476A3CB596DA76FD7010A029F76732EF824.xkm
[64.685] (II) evdev:HP WMI hotkeys:close
[64.685] (II) unloadmodule: evdev
[64.685] (II) evdev:alps ps/2 device: close
[64.685] (II) unloadmodule: "evdev"
[64.685] (II) unload module: "synpatics"
[64.685] (II) evdev: AT translated set 2 keyboard : close
[64.685] (II) unloadmodule: "evdev"
[64.685] (II) evdev: HP webcam: close
[64.685] (II) unloadmodule: "evdev"
[64.685] (II) evdev: sleep button: close
[64.685] (II) unloadmodule: "evdev"
[64.685] (II) evdev: power button: close
[64.686] (II) unloadmodule: "evdev"
[64.686] (II) evdev: video bus:close
[64.686] (II) unload module: "evdev"
[64.686] (II) evdev : power button: close
[64.686] (II)unloadmodule: "evdev"
[64.775] (ee) server terminated successfully (0). closing log file.[/B][/I]




```
If needed we can install the pastebin utility to relay info .
[INDENT][INDENT]how come, why not
[/INDENT]
[/INDENT]


---

### Post by alex375 on 2015-05-09
and /var/log/dmesg.0  would be cool
scanned on first recovery after black screen

---

### Post by aaronr2 on 2015-05-09
> **alex375 said:**
> and **/var/log/dmesg.0**  would be cool
scanned on first recovery after black screen

typing in this gets permission denied

---

### Post by alex375 on 2015-05-09
sudo nano **/var/log/dmesg.0**    

but better install leafpad and

sudo leafpad **/var/log/dmesg.0**

---

### Post by aaronr2 on 2015-05-09
> **alex375 said:**
> sudo nano **/var/log/dmesg.0**


typing in that exact phrase results in sudo: nano/var/log/dmesg.0: command not found


Sorry if I"m a noob and missing something obvious preventing this from working.

---

### Post by alex375 on 2015-05-09
sudo  nano    space                     /var/log/dmesg.0

copy/paste from previous post
but better install leafpad

---

### Post by aaronr2 on 2015-05-09
> **alex375 said:**
> sudo  nano    space                     /var/log/dmesg.0

Is there something in here I should be looking for? I am hand typing all of these over from the non working computer and that command yields 885 lines.

---

### Post by aaronr2 on 2015-05-09
I rebooted the system and let it sit and after about 9 minutes the screen does finally load but it is so slow and unresponsive you cant access anything.

---

### Post by Bashing-om on 2015-05-09
aaronr2; Hummmm ...

Sorta suck here, and trying to think my way through;
You have the correct driver installed for your graphics card per:
[http://www.nvidia.com/object/IO_32667.html](http://www.nvidia.com/object/IO_32667.html)

BUT; do we have a driver conflict at this time ?
> 
ii libcuda-304 304.125-0ubuntu0.0.1
amd64 nvidia cuda runtime library

ii nvidia-304 304.125-0ubuntu0.0.1
amd64 nvidia legacy binary driver - version 304.125

ii nvidia-current 304.125-0ubuntu0.0.1
amd64 transitional package for nvidia-current

ii nvidia-libopencl1-304 304.125-0ubuntu0.0.1
amd64 nvidia opencl driver and icd loader library


Can someone else advise if there is a conflict here, before we purge and re-install ?
--------------------
For relaying the log files we have the pastebinit utility . If we need to, can do.
------------------------------------------

[INDENT][INDENT]sometimes, I just do not know
[/INDENT][/INDENT]

---

### Post by alex375 on 2015-05-09
you need ctrl+w 'nvidia'
all lines

---

### Post by aaronr2 on 2015-05-09
> **alex375 said:**
> you need ctrl+w 'nvidia'

Can I do this from recovery mode? after it boots up (10 or so minutes) you can't press any buttons or type anything. after it booted it took another 6 minutes just to allow me to click the settings tab.

---

### Post by alex375 on 2015-05-09
scanned on first recovery after black screen

---

### Post by aaronr2 on 2015-05-09
doesn't appear to do anything productive. now when I type into the terminal nothing appears.

---

### Post by alex375 on 2015-05-09
sudo cat  /var/log/dmesg.0 | grep nvidia -ni

---

### Post by aaronr2 on 2015-05-09
> **alex375 said:**
> sudo cat  /var/log/dmesg.0 | grep nvidia -ni

this yields


[13.850596] input: hda nvidia mic as /devices/pci0000:00/0000:00:07.0/sound/card0/input17
[13.850753] input: hda headphone as /devices/pci000:00/000:00:07.0/sound/card0/input18
[14.634566] nvidia: module license 'nvidia' taints kernel
[14.649861] nvidia: module verification failed: signature and/or required key missing - tainting kernel
[14.660697] [drm] initialized nvidia -drm 0.0.0 20140818 for 0000:00:12:0 on minor 0
[14.660714 nvrm: loading nvidia unix x86_64 kernel module 304.125 mon dec 1 19:58:28 pst 2014

---

### Post by aaronr2 on 2015-05-10
> **aaronr2 said:**
> this yields


[13.850596] input: hda nvidia mic as /devices/pci0000:00/0000:00:07.0/sound/card0/input17
[13.850753] input: hda headphone as /devices/pci000:00/000:00:07.0/sound/card0/input18
[14.634566] nvidia:** module license 'nvidia' taints kernel**
[14.649861] nvidia: **module verification failed: signature and/or required key missing - tainting kernel**
[14.660697] [drm] initialized nvidia -drm 0.0.0 20140818 for 0000:00:12:0 on minor 0
[14.660714 nvrm: loading nvidia unix x86_64 kernel module 304.125 mon dec 1 19:58:28 pst 2014


Is this correct? 

I really appreciate the help I have been given thus far, I'm just in extreme need of getting this thing going properly again.

Thanks in advance for any insight provided.

---

### Post by Bashing-om on 2015-05-11
aaronr2; Hey;

My thought remains; purge Nvidia and then (RE-)install :

Try this:
```

sudo apt-get remove --purge nvidia*
sudo apt-get purge nvidia-\*
sudo service lightdm stop
sudo apt-get update
sudo apt-get upgrade
sudo apt-get install linux-headers-generic
sudo apt-get install nvidia-current nvidia-settings

```
Rebbot the system:
```

sudo shutdown -r now

```
Edit : A conflict in driver source ? are there any PPAs involved ? check:
```

cat -n /etc/apt/sources.list
tail -v -n +1 /etc/apt/sources.list.d/*

```
If there are any problems encountered, OR any errors the system reports; post back the complete command and response to the error(s). If needed we can redirect the outputs to files and/or to a pastebin to facilitate the transfer of the information .

Maybe
[INDENT][INDENT]nothin' but a thing
[/INDENT][/INDENT]

---

### Post by anders650 on 2015-12-15
I realize that this is an old thread, but a solution my be of interest to future readers.
I have the same HP dv2700 notebook with Nvidia GeForce 7150M graphics. Following is a guide to a fresh installation of Ubuntu 14.04 or higher.

Boot from a USB stick.
In order to have a readable screen you must enter the "nomodeset" boot option in the grub configuration. 
In Ubuntu 14.04 you select manual configuration by pressing any key at the first screen, then F6 Other Options, check the nomodeset option, press esc, then proceed with the installation.
If you are installing 15.10 and have created the USB stick boot image on an earlier version of Ubuntu you may come to a screen with a prompt "boot:". Here you enter the command ```
live nomodeset
```
Then run Install Ubuntu from the desktop.

Once the installation is completed you get to a login screen. Proceed with the login. You will get to a desktop that has lower than desired resolution and quite poor performance when it comes to speed. Don't worry, we will fix it by installing the nvidia proprietary driver and adjust a configuration of OpenGL. 

From the desktop do:[INDENT]System Settings[/INDENT]
[INDENT]Software & Updates[/INDENT]
[INDENT]tab Additional Drivers[/INDENT]
[INDENT]select nvidia-304-updates[/INDENT]
[INDENT]Apply changes[/INDENT]
[INDENT]Close[/INDENT]

By now the system has most likely found that there are updates available, go ahead and install the updates. 
Restart.

You may notice that the login screen has a slightly higher resolution than last time. This is a good sign that the nvidia driver is working.
Login.
You will come to a blank or even black screen with only the pointer arrow.
Go to the terminal by pressing Ctrl Alt F1.
Login with your username and password.
Enter the commands 
```
export DISPLAY=:0
dconf write /org/compiz/profiles/unity/plugins/opengl/enable-x11-sync false
sudo reboot
```

After you login you will have a nice high resolution Unity desktop and the performance will be quite OK given the age of the hardware.

If you create additional users, you have to go through the exercise on the terminal for each user. For some reason that I don't quite understand you may find that you have to repeat the dconf command twice when creating additional accounts. If the additional account is not an administrator you have to "logout" and then login with an administrator account before you can issue the reboot command.

The "enable-x11-sync" configuration is needed due to a reported bug. I got my inspiration from [Bug #1425701]("https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/1425701")

Hope this helps someone with an old HP notebook.

---

