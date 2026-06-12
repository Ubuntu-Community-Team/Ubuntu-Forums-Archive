---
title: "Nvidia Optimus + CUDA + bumblebee + 14.04"
date: 2014-10-01
forum: Installation &amp; Upgrades
---

### Post by gasior.tt on 2014-10-01
Hi coders/developers,
 
 I am the unfortunate to have laptop with optimus technology(nvidia gpu + intel integrated gpu), which seems to make a lot of problems to the new Ubutnu users.  
 
 I'm running fresh Ubuntu 14.04 install with Nvidia GPU: gtx 760m, and I want to  install the  following set: nvidia driver + bumblebee + CUDA 6.5  + Nsight Eclipse. I'm interested in running only few program on nvidia GPU via bumblebee and its $optirun command. The rest of the system I want to stay and run on the intel's GPU.

 I've searched the whole internet on how to do that, and each search gave sometimes completely different, and sometimes slightly different answers. I followed some of them and each time I failed.  

 Nvidia driver:  
 
[LIST]
[*]should I     install the latest driver (340.46     [http://www.nvidia.pl/download/driverResults.aspx/78504/pl](http://www.nvidia.pl/download/driverResults.aspx/78504/pl))     and just run it? Or later driver? 
[*]Should I     install the driver via terminal ? Via Software&Updates ? Or     maybe from another repository? 
[*]Some users say     to blacklist opensource nouveau driver. Some user say the     installation process does it automatically. Lots of users end with     the black screen problem 
[/LIST]
  CUDA:
 
[LIST]
[*]some surces say     to ```
sudo apt-get install nvidia-cuda-toolkit
``` some say just ```
sudo apt-get install cuda
``` 
[/LIST]
  
This is what System Details windows says:
[IMG]http://i58.tinypic.com/160zzpi.png[/IMG]

Software & Updates: 
[IMG]http://i59.tinypic.com/rmmfdt.png[/IMG]

 Could someone who DOES  know the problem inside out, paste here the step by step  solution? Which driver, from what source? How to verify each installation and step. It'd be helpful for every user struggling with this issue.  

 
 Please not to paste the links from all over the internet since it's only troublemaking. Please paste your solutions here from the very beginning to the very end

---

### Post by gasior.tt on 2014-10-01
@up

---

### Post by QIII on 2014-10-01
Hello!

A couple of things to help you get a better response when you ask a question ...

1.  You may find a few people on the Forums who are developers (like me) but nary a one of us is a Canonical employee.  So if you are looking for an answer from one of them, this is not the right place.  By putting that as your greeting, you may have chased off a lot of people who might otherwise have helped.  There are a lot of plain old Ubuntu users who have grappled with this issue who might have helped.

2.  Although we have relaxed our rule that used to only allow one bump per 24 hour period, please remember that this is a world-wide forum with members who live in every time zone.  8 hours may not be enough time for everyone to see your post.  Be patient and let everyone have a chance to respond.

3.  We have people who specifically search for unanswered posts.  By adding another post to bump your thread, you have taken your thread out of the query that finds such threads.

4.  Please don't make demands about the manner in which people answer you.  We are all just Ubuntu users like you and we help out as best we can in the time we have to volunteer here.  Accept the help given as it is given without demanding its form.

That said ...

Hybrid graphics arrangements are a very difficult problem in Linux.  OEMs concentrate on making things work for Windows and give Linux short schrift.  This has been going on for several years and the community is still struggling with hammering things out without any help.

As a start, please have a look [here]("https://wiki.ubuntu.com/Bumblebee") and see if there is anything you haven't encountered before that might help with the issue.  I am not going to recreate the wheel here and replicate the article, so you will need to follow the link.

Best wishes... and be patient.

---

### Post by Samarth_Brahmbhatt on 2015-02-02
Bumblebee recommends that you apt-get your drivers from the Ubuntu repositories. At the time of writing, these are nvidia-331 and nvidia-331-updates. None of them worked well with either nvidia-cuda-toolkit (from the Ubuntu repositories) or the CUDA toolkit 5.5, 6.0 or 6.5 from the NVIDIA website.

So if you want the latest drivers, you have to download them from the NVIDIA repositories, and not use Bumblebee. That means your GPU will always stay on. I'm not saying you should do this, I'm just giving you a working option. Here's how I did it:

0. Purge all previous nvidia stuff you might have tried installing
1. Download the latest CUDA toolkit .run file
2. Blacklist the nouveau driver by appending  
> blacklist nouveau
options nouveau modeset=0 
to /etc/modprobe.d/blacklist.conf and rebooting
3. When you reboot, don't log in. Drop to the terminal by CTRL-ALT-F1, and kill lightdm by
> sudo service lightdm stop
4. Extract the individual parts from the cuda toolkit archive you downloaded earlier by
> ./<cuda-archive-name> --extract=<your_fav_dir>
5. Navigate to your_fav_dir
6. Install the Nvidia driver by (this is the most important step)
> sudo ./<NVIDIA_driver_run_name> --no-opengl-files
The --no-opengl-files option prevents overwriting of some GL files. If you don't pass this your screen will freeze after login. Also, select 'no' when it asks you update the xorg.conf file.
7. Reboot and verify through the Additional Drivers utility that you are using a manually installed driver.
8. Navigate again to your_fav_dir and install the cuda toolkit and samples in pretty much the same manner (you don't need to pass any special options now).
9. Enjoy CUDA

---

### Post by Samarth_Brahmbhatt on 2015-06-03
I found a way to use Bumblebee with Nvidia drivers installed from their website (as opposed to from apt-get, which uses the Ubuntu repositories). This is good news for CUDA users, because (at least in my experience) CUDA does not work if the Nvidia drivers are not from the website. Here are the steps for Ubuntu 14.04:

0. Install the Nvidia drivers are described in the above post (#4).

1. Install bumblebee without the nvidia driver dependency
> sudo apt-get install --no-install-recommends bumblebee

2. Change the following in your /etc/bumblebee/bumblebee.conf
> 
(near the top):
Driver=nvidia
(in driver-nvidia section):
LibraryPath=/usr/lib
XorgModulePath=/usr/lib/xorg/modules/drivers,/usr/lib/xorg/modules


3. Reboot

There are still some issues: The GPU does not automatically turn off after a command executed with optirun finishes. You can do so by creating the following script
> 
#!/usr/bin/env bash

modprobe -r nvidia
tee /proc/acpi/bbswitch <<<OFF
cat /proc/acpi/bbswitch

and running is as sudo.

---

### Post by Samarth_Brahmbhatt on 2015-06-03
I found a way to use Bumblebee with Nvidia drivers installed from their website (as opposed to from apt-get, which uses the Ubuntu repositories). This is good news for CUDA users, because (at least in my experience) CUDA does not work if the Nvidia drivers are not from the website. Here are the steps for Ubuntu 14.04:

0. Install the Nvidia drivers are described in the above post (#4).

1. Install bumblebee without the nvidia driver dependency
> sudo apt-get install --no-install-recommends bumblebee

2. Change the following in your /etc/bumblebee/bumblebee.conf
> 
(near the top):
Driver=nvidia
(in driver-nvidia section):
LibraryPath=/usr/lib
XorgModulePath=/usr/lib/xorg/modules/drivers,/usr/lib/xorg/modules


3. Reboot

There are still some issues: The GPU does not automatically turn off after a command executed with optirun finishes. You can do so by creating the following script
> 
#!/usr/bin/env bash

modprobe -r nvidia
tee /proc/acpi/bbswitch <<<OFF
cat /proc/acpi/bbswitch

and running it as sudo.

---

### Post by Samarth_Brahmbhatt on 2015-06-03
I found a way to use Bumblebee with Nvidia drivers installed from their  website (as opposed to from apt-get, which uses the Ubuntu  repositories). This is good news for CUDA users, because (at least in my  experience) CUDA does not work if the Nvidia drivers are not from the  website. Here are the steps for Ubuntu 14.04:

0. Install the Nvidia drivers are described in the above post (#4).

1. Install bumblebee without the nvidia driver dependency
> sudo apt-get install --no-install-recommends bumblebee

2. Change the following in your /etc/bumblebee/bumblebee.conf
> 
(near the top):
Driver=nvidia
(in driver-nvidia section):
LibraryPath=/usr/lib
XorgModulePath=/usr/lib/xorg/modules/drivers,/usr/lib/xorg/modules


3. Reboot

There are still some issues: The GPU does not automatically turn off  after a command executed with optirun finishes. You can do so by  creating the following script
> 
#!/usr/bin/env bash

modprobe -r nvidia
tee /proc/acpi/bbswitch <<<OFF
cat /proc/acpi/bbswitch

and running it as sudo.

---

### Post by mike-surprisetruck on 2016-04-13
Some notes of my own to add to [COLOR=#000000]Samarth_Brahmbhatt's post(s?).
I'm running Ubuntu 14.04 on Dell Precision Laptop with Nvidia Optimus graphics and installed CUDA 7.5

One thing that tripped me up was an error when running optirun:
[/COLOR]```

[COLOR=#333333][ERROR]Cannot access secondary GPU - error: [XORG] (EE) No devices detected.[/COLOR]
```
[COLOR=#000000]
According to [https://wiki.ubuntu.com/Bumblebee#A.22Cannot_access_secondary_GPU.22_error](https://wiki.ubuntu.com/Bumblebee#A.22Cannot_access_secondary_GPU.22_error) and referencing [/COLOR]/etc/bumblebee/xorg.conf.nvidia file. To fix it, I had to run:

```

me@nixtop:~$ lspci -nnvk | grep -A10 "VGA\|NVIDIA"
00:02.0 VGA compatible controller [0300]: Intel Corporation 4th Gen Core Processor Integrated Graphics Controller [8086:0416] (rev 06) (prog-if 00 [VGA controller])
    Subsystem: Dell Device [1028:060d]
    Flags: bus master, fast devsel, latency 0, IRQ 33
    Memory at f7400000 (64-bit, non-prefetchable) [size=4M]
    Memory at d0000000 (64-bit, prefetchable) [size=256M]
    I/O ports at f000 [size=64]
    Expansion ROM at <unassigned> [disabled]
    Capabilities: <access denied>
    Kernel driver in use: i915


00:03.0 Audio device [0403]: Intel Corporation Xeon E3-1200 v3/4th Gen Core Processor HD Audio Controller [8086:0c0c] (rev 06)
--
02:00.0 3D controller [0302]: NVIDIA Corporation GK107GLM [Quadro K1100M] [10de:0ff6] (rev ff) (prog-if ff)
    !!! Unknown header type 7f
...

```
[COLOR=#000000]And place the "[/COLOR]02:00.0"[COLOR=#000000] pci bus id in the following format in the un-commented line from the [/COLOR]/etc/bumblebee/xorg.conf.nvidia file[COLOR=#000000]:
[/COLOR]```
BusID "PCI:02:00:0"
```
[COLOR=#000000]
Also, in [/COLOR][COLOR=#000000] /etc/bumblebee/bumblebee.conf, you must set the following:

[/COLOR]```
TurnCardOffAtExit=true
...
KernelDriver=nvidia

```

[COLOR=#000000]
The first option above fixes the "issue" with the GPU remaining on after optirun launch. I verified it worked by running the following:

[/COLOR]```
me@nixtop:~$ optirun --no-xorg cat /proc/acpi/bbswitch 
0000:02:00.0 ON
me@nixtop:~$ cat /proc/acpi/bbswitch 
0000:02:00.0 OFF

```[COLOR=#000000]

The second option was set to "nvidia-current" for some strange reason... either by default, or by some happenstance of my many attempts at trying to get this setup to work.

Good luck. The hardest part about this was learning that I even had Nvidia Optimus hardware... then finding this thread with the special CUDA addition.
[/COLOR]

---

### Post by shawn40 on 2016-07-25
I've tried your fixes in #4 with CUDA 7.0, NVS 5200M card on a Thinkpad T430s, Ubuntu 14.04 64x. Everything went smoothly but it does not pass deviceQuery test. Also, it didn't ask me to update xorg.conf. For the rest, I chose "accept" and "yes"

Later on, I continued to install bumblebee in #5. I tried to run optirun but it cannot start with this error: 
[ERROR]The Bumblebee daemon has not been started yet or the socket path /var/run/bumblebee.socket was incorrect

I check /var/logsyslog which shows: 
bumblebee[1414]: Module 'nvidia-current' is not found

I tried a check in bumblebee's github troubleshooting at [link]("https://github.com/Bumblebee-Project/Bumblebee/wiki/Troubleshooting") with a negative result

I think your fixes install newest proprietary drivers but then bumblebee still ask for the 'nvidia-current' drivers which reverse the installation. Is there any way to suppress this checking of bumblebee and force the use of new drivers?

---

### Post by Samarth_Brahmbhatt on 2016-07-27
> **shawn40 said:**
> I think your fixes install newest proprietary drivers but then bumblebee still ask for the 'nvidia-current' drivers which reverse the installation. Is there any way to suppress this checking of bumblebee and force the use of new drivers?

As mentioned in #5, you must install bumblebee with the no-install-recommends option, and after the installation edit the bumblebee.conf file.

---

