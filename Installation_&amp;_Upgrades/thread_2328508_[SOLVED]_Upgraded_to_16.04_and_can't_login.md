---
title: "[SOLVED] Upgraded to 16.04 and can't login"
date: 2016-06-21
forum: Installation &amp; Upgrades
---

### Post by vpiercy on 2016-06-21
Hi, 

I upgraded to 16.04 and I get the login screen, type in my password, hit enter, and get the password screen again. 

So...do I use an install disk to delete my profile files in /etc? 

Thanks!

---

### Post by RobGoss on 2016-06-21
Hello is this your first time installing Ubuntu? make sure your using the correct user name & password

---

### Post by DuckHook on 2016-06-22
> **vpiercy said:**
> Hi, 

I upgraded to 16.04 and I get the login screen, type in my password, hit enter, and get the password screen again. 

So...do I use an install disk to delete my profile files in /etc? 

Thanks!Do not touch anything in /etc or you risk rendering your OS unbootable.

Instead, the next time you boot up, rather than trying to log into the GUI, do <Ctrl>+<Alt>+<F1> to switch to a TTY. It will ask for user (the name you set up with) and password (nothing will display even as you type). When you get to a bash shell, do:```
ls -lanF .Xauthority
```It should look like this:```
-rw------- 1 1000 1000 49 Jun 21 20:24 .Xauthority
```The important part is the:```
1000 1000
```If these two numbers are anything other than "1000", do:```
sudo rm ~/.Xauthority
``````
sudo reboot
```...and try logging in normally. Linux is case-sensitive and very explicit, so make sure you type in the commands exactly as above with the dot and capital X.

If the .Xauthority line is fine, but the problem persists, then we will have to do further detective work.

---

### Post by Impavidus on 2016-06-22
+1 to DuckHook's suggestion. It's probably overkill, but it should work in most cases.

The root cause of the problem may be incorrect usage of sudo, possibly during the upgrade.

---

### Post by vpiercy on 2016-06-22
Thank you all for the suggestions and help! 

I went into Recovery mode after bootup and tried the suggestions here: [http://askubuntu.com/questions/223501/ubuntu-gets-stuck-in-a-login-loop](http://askubuntu.com/questions/223501/ubuntu-gets-stuck-in-a-login-loop). 

When I type

```
ls -lah
```

I get a list of all my folders and files. I can go to /home or /root and get what looks like the list of files and folders that should be there. 


The username and password are good because I used them in console mode. 

Finally, when I tried DuckHook's suggestion, I got exactly the output that was supposed to occur for .Xauthority: 

```
1000 1000
``` 

I tried [COLOR=#000000]<Ctrl>+<Alt>+<F1>[/COLOR] and typed

```
mv .Xauthority .Xauthority.bak
```

Then did [COLOR=#000000]<Ctrl>+<Alt>+<F7> t[/COLOR] to get the login screen and the same behavior occurred. I typed the password. Ubuntu would try (purple screen) and then I'd get the password challenge screen again. 

So...ima stumped. I do have the install disk handy.... All my data is there and backed up. I'd just hate to 1) reload everything and 2) not know why this is happening. 

Thank you for the help!

---

### Post by X-RED_Tech on 2016-06-22
You can remove (rm) ./Xauthority as suggested by DuckHook and either way you must reboot (also as suggested). It'll be recreated in the next boot.
There could be other issues, including some problem with graphics drivers due to the upgrade, or something you did (or didn't) when trying to compile the driver/software for your overpriced overhyped mouse. The point being there's little to nothing of info to start with.

---

### Post by DuckHook on 2016-06-22
Use <Ctrl>+<Alt>+<F1> to get to a TTY at login again, and login.

Lets look at .xsession-errors and .xsession-errors.old. They may tell us something:```
cat .xsession-errors
``````
cat .xsession-errors.old
```You needn't post the output, since it would be difficult for you to do so without a working desktop environment. We just want to know if something jumps out at you: usually along the lines of "cannot connect" or "failed to authorize" or something similar. Also, follow the instructions on your referenced link and check /tmp to see if it has the right permissions:```
ls -ld /tmp
```It should look like this:```
drwxrwxrwt 12 root root 300 Jun 22 09:17 /tmp
```The important stuff are the ten letters at the left "drwxrwxrwt", and "root root". If different, post results to this thread. If everything above looks in order, then it doesn't hurt to delete and rebuild .ICEauthority as well. The session will create another one the next time it successfully starts:```
rm ~/.ICEauthority
```

Before next step (reconfiguring lightdm), let's hear back from you on what is in .xsession-errors.

---

### Post by vpiercy on 2016-06-23
Thanks so much for your help!

Here is the output you asked for from those commands:

```
$ cat .xsession-errors
```

```

Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".
openConnection: connect: No such file or directory
cannot connect to brltty at :0
upstart: gnome-session (Unity) main process (1592) terminated with status 1
upstart: unity-settings-daemon main process (1585) killed by TERM signal
upstart: logrotate main process (1442) killed by TERM signal
upstart: upstart-dbus-session-bridge main process (1490) terminated with status 1
upstart: hud main process (1583) killed by TERM signal
upstart: unity-panel-service main process (1600) killed by TERM signal
upstart: Disconnected from notified D-Bus bus
upstart: bamfdaemon main process (1561) killed by TERM signal 

```


```
$ cat .xsession-errors.old
```

```

Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".
openConnection: connect: No such file or directory
cannot connect to brltty at :0
upstart: gnome-session (Unity) main process (2942) terminated with status 1
upstart: unity-settings-daemon main process (2935) killed by TERM signal
upstart: logrotate main process (2782) killed by TERM signal
upstart: hud main process (2933) killed by TERM signal
upstart: unity-panel-service main process (2949) killed by TERM signal
upstart: Disconnected from notified D-Bus bus
upstart: bamfdaemon main process (2846) killed by TERM signal
upstart: unity7 main process (2939) killed by SEGV signal

```

```
$ ls -la /tmp
```

```

total 44
drwxrwxrwt 10 root root 4096 Jun 23 09:09 .
drwxr-xr-x 26 root root 4096 Jun 22 07:57 ..
drwxrwxrwt 2 root root 4096 Jun 23 04:03 .font-unix
drwxrwxrwt 2 root root 4096 Jun 23 04:03 .ICE-unix
drwx------ 3 root root 4096 Jun 23 04:04 systemd-private-e545f3da83694fdbb8b6e37ca69863be-colord.service-YxeVY3
drwx------ 3 root root 4096 Jun 23 04:04 systemd-private-e545f3da83694fdbb8b6e37ca69863be-rtkit-daemon.service-I0tprF
drwx------ 3 root root 4096 Jun 23 04:03 systemd-private-e545f3da83694fdbb8b6e37ca69863be-systemd-timesyncd.service-R9mHbC
drwxrwxrwt 2 root root 4096 Jun 23 04:03 .Test-unix
-r--r--r-- 1 root root 11 Jun 23 04:04 .X0-lock
drwxrwxrwt 2 root root 4096 Jun 23 04:04 .X11-unix
drwxrwxrwt 2 root root 4096 Jun 23 04:03 .XIM-unix

```

I haven't deleted .ICEauthority yet.

---

### Post by deadflowr on 2016-06-23
I wonder about that glx error.
What does:
```
dpkg -l | grep glx
``` 
show?

---

### Post by DuckHook on 2016-06-24
> **deadflowr said:**
> I wonder about that glx error.+1

@OP

In addition to deadflowr's instructions, did you at any time change or install proprietary nVidia drivers? Please also post results of:```
lspci -vk | grep -iA15 vga
```

---

### Post by vpiercy on 2016-06-24
Thanks again. And yes, I did have an Nvidia driver for my Nvidia card. 

For 
```
[COLOR=#000000][FONT=&amp]dpkg -l | grep glx[/FONT][/COLOR]
```

I got

```
ii  libgl1-mesa-glx:amd64             11.2.0-1ubuntu2                                amd64        free implementation of the OpenGL API -- GLX runtimeii  
libgl1-mesa-glx:i386                        11.2.0-1ubuntu2                         i386         free implementation of the OpenGL API -- GLX runtimeii  
libxcb-glx0:amd64                           1.11.1-1ubuntu1                        amd64        X C Binding, glx extensionii  
libxcb-glx0:i386                            1.11.1-1ubuntu1                          i386         X C Binding, glx extension



```

For 
```
[COLOR=#000000][FONT=&amp]lspci -vk | grep -iA15 vga[/FONT][/COLOR]
```

I got

```
01:00.0 VGA compatible controller: NVIDIA Corporation GM204 [GeForce GTX 970] (rev a1) (prog-if 00 [VGA controller])    
Subsystem: Micro-Star International Co., Ltd. [MSI] GM204 [GeForce GTX 970]
    
Flags: bus master, fast devsel, latency 0, IRQ 11
Memory at de000000 (32-bit, non-prefetchable) [size=16M]    
Memory at c0000000 (64-bit, prefetchable) [size=256M]
Memory at d0000000 (64-bit, prefetchable) [size=32M]
I/O ports at e000 [size=128]
Expansion ROM at df000000 [disabled] [size=512K]
Capabilities: <access denied>
Kernel modules: nvidiafb, nouveau, nvidia_358
01:00.1 Audio device: NVIDIA Corporation GM204 High Definition Audio Controller (rev a1)
Subsystem: Micro-Star International Co., Ltd. [MSI] GM204 High Definition Audio Controller
Flags: bus master, fast devsel, latency 0, IRQ 17
Memory at df080000 (32-bit, non-prefetchable) [size=16K]
Capabilities: <access denied>

```

---

### Post by DuckHook on 2016-06-24
For some reason, you have two competing video modules (drivers) fighting for the same device. I would recommend first try disabling the closed proprietary module. Please do:```
sudo nano /etc/modprobe.d/blacklist.conf
```...then add the following at the end of the file:```
# added by vpiercy 2016-06-23 to disable closed-source nVidia proprietary driver in favour of nouveau
blacklist nvidia_358
```...write the changes to file, then exit nano with <Ctrl>+<o>, <Ctrl>+<x>. This will allow your system to boot with just the nouveau driver without interference from a competing driver. If this doesn't work, you can repeat the process but this time, blacklisting the nouveau driver and allowing the nVidia driver to run. Reboot and see if this doesn't solve your problem.

Unless you need the closed-source proprietary driver for gaming or some other special purpose, it is a good idea to run with just the open driver.

---

### Post by vpiercy on 2016-06-25
I blacklisted the nVidia driver, saved, exited, re-opened the file, verified the save, and exited again. 

Restarted and got the purple Ubuntu password screen. Logged in and...got the password screen again.

I then removed .ICEauthority as suggested in a previous post. Rebooted, and got the repeated password challenge after logging in. 

To blacklist nouveau, would I just type in the following to that file? 

```
[COLOR=#000000]# added by vpiercy 2016-06-24 to disable nouveau driver in favour of nVidia proprietary driver
[/COLOR][COLOR=#000000]blacklist nouveau[/COLOR]
```

I could try 

```
[COLOR=#000000][FONT=&amp]lspci -vk | grep -iA15 vga[/FONT][/COLOR]
```

again and see if anything is different. 

Thanks!

---

### Post by DuckHook on 2016-06-25
Before blacklisting nouveau try the lspci command to see if nVidia is no longer loaded. You must never have two video drivers competing to drive the same video card.

To blacklist nouveau, you must also *reverse* the blacklisting of nvidia, else you will have *no* video driver.

It is also possible that merely blacklisting nvidia is not enough. Proprietary video drivers in particular install other libraries and config files that are specific to each driver. So it may also be necessary to completely purge nvidia to give nouveau a proper working environment.

It is becoming clear that you did not just do a pristine upgrade from 14.04 to 16.04. Perhaps it is time that you went into detail about your system specs, and all of the software customizing that you did prior to the upgrade. Your original post mentions deleting profiles in /etc. Did you do anything of that sort that you have not mentioned? Have you installed other apps or services that may have changed your system configuration from default values?

If your system is too far removed from baseline, it makes becomes geometrically harder to chase down the problems and it makes ever more sense to simply re-install from scratch to get back to a pristine system.

---

### Post by vpiercy on 2016-06-25
I didn't remove or change anything from /etc. When I was finding information suggesting that, that's when I posted here. 

I added a proprietary mouse driver and the nVidia driver. Other than just some extra apps and monitoring utilities, Steam, games, Dropbox, that's about it. 

What commands will give the system specs that would be helpful? 

If you think we are at the point that I should do a clean install, I will. I appreciate your time and advice.

---

### Post by DuckHook on 2016-06-26
Sorry for the belated reply.

If your only big changes were to video and mouse, and /etc was largely untouched, this shouldn't be too difficult. Although sometimes there's a lot to be said for a complete reinstall (especially since you had the forethought to back up), let's try a few more things first in this case.

The problem (or at least one of the problems) appears to be duelling video drivers, so lets' fix that and see if it works.

Do another lspci to see if both drivers are still showing up. You needn't post the results. Just look at the "kernel modules" line and see if it still looks like this:```
Kernel modules: nvidiafb, nouveau, nvidia_358
```...(bad) or now looks like this:```
Kernel modules: nvidiafb, nouveau
```...(good). If you still get the bad result, do:```
lsmod | egrep -i 'nvidia|nouveau|video'
```...this will tell you what video drivers are still being loaded. The only one should be nouveau. If you did the blacklisting step correctly, nVidia should not show up anywhere.

Also, please tell us:

[LIST=1]
[*]*Why* did you install the proprietary driver? Was it because nouveau would not work with your video card?
[*]*How* did you install the proprietary driver? Was it through the repos, a ppa, or compiled from nVidia? Such details are very important.
[*]Are you willing to live with nouveau?
[*]
[/LIST]
It may be time to purge the nVidia driver. You can always reinstall it later if it turns out that you need it. If you installed through the repos, do:```
sudo apt purge nvidia-358
```Note that the driver *package* has a dash "-" in the name whereas that driver *module* has an underscore "_". Make sure to use the dash in the apt purge command, but the underscore in the prior blacklist attempts. If you installed your driver in any way other than directly from the repos, the above may not work and you will have to await further instructions after letting us know installation method.

*EDIT*

A reminder that you cannot remove or purge a running driver. You must first successfully blacklist the nvidia driver and reboot into nothing but nouveau for the apt purge command to work.

---

### Post by vpiercy on 2016-06-27
After doing 

```
lspci
```

I saw nVidia lines but nothing with nouveau. 

So the output for 

```
[COLOR=#000000][FONT=&amp]lsmod | egrep -i 'nvidia|nouveau|video'[/FONT][/COLOR]
```

was the following:

```

uvcvideo               
90112  0videobuf2_vmalloc      
16384  1 uvcvideovideobuf2_memops       
16384  1 videobuf2_vmalloc     videobuf2_v4l2         
28672  1 uvcvideo                  videobuf2_core         
36864  2 uvcvideo,videobuf2_v4l2   v4l2_common            
16384  1 videobuf2_v4l2  videodev              
176128  4 uvcvideo,v4l2_common,videobuf2_core,videobuf2_v4l2 media                  
24576  2 uvcvideo,videodev video                  
40960  2 i915_bpo,asus_wmi

```

I can't tell what driver is running, but I don't see "nVidia."

1. I installed the nVidia driver because I thought I would get better performance and efficiency, however marginal, from my card. Nouveau worked before.
2. I installed the proprietary drivers through the Ubuntu repos, I believe. There were two versions of the proprietary driver that came up when I looked in "Additional drivers" through Ubuntu's menus. I didn't do anything fancy to get them. It was Ubuntu automagic or nothing. 
3. I can live with nouveau if it'll run Steam games well enough. 

When I tried to purge the nVidia driver, I got a list of unmet dependencies. I checked the blacklist file and verified again that the line

```
[COLOR=#000000][FONT=&amp]blacklist nvidia_358[/FONT][/COLOR]
``` was there.

---

### Post by DuckHook on 2016-06-27
lsmod is saying that you have neither nvidia loaded (which is expected since it is blacklisted) nor nouveau (which, though disappointing, is not entirely surprising probably because it fails due to some residual incompatible settings and config files). The inability to remove the nvidia module means that your problems are definitely non-trivial. You may even have a broken dpkg database and be stuck in dependency hell.

At this point, it is probably easier to reinstall than to try chasing down broken packages, especially since the process would have to be done by you laboriously retyping all of the various reports, outputs and inputs from one system into another.

For what it's worth, I don't think you did anything wrong here. You mention that your problems started right after an upgrade and this is usually the sort of breakage we see in an unsuccessful upgrade. BTW, the next time you do such a network upgrade, it would probably be a good idea to put the system back into as close to default or pristine state as possible beforehand. This includes removing the proprietary drivers. Then the system can upgrade from a more common state that has been stress-tested by many people.

Since you have backups, you appear to be well prepared to reinstall.

To answer the crux of your questions: I doubt that you will be happy with nouveau if you are a gamer. It is an excellent little driver if you stick to graphically undemanding productivity apps, but it won't measure up to the proprietary nvidia driver for graphically intense apps or games. However, after you have installed a pristine OS and before you restore any data, Webupd8 has coincidentally (and fortuitously) just provided a [link]("http://www.webupd8.org/2016/06/how-to-install-latest-nvidia-drivers-in.html") for the newest *stable* nvidia drivers. I don't normally recommend PPAs to people, but you have one of the newer nvidia cards and could probably use a more current driver. Also, Webupd8 is a responsible site, so I'm less worried about their recommended PPAs than most. Last but not least, this PPA only stocks *stable* drivers, which is a refreshing change from other PPAs which confusingly also stock beta and experimental drivers.

Let us know which way you want to go.

---

### Post by MAFoElffen on 2016-06-27
Just a reminder... 

No one asked what the system's GPU was?
```

sudo lspci | grep -i ''vga
sudo lshw -n -c video
ls /etc/X11/xorg.conf

```
Logically think of the changes we had in the 16.04 do-release-upgrade process. Previous versions would rename the xorg.conf file and put a time stamp on it, then create a new xorg.conf file.

Release 16.04, on release upgrade, backs up the xorg.conf file, but I noticed it does not always create a new xorg.conf file, so is not there by default on the upgrade. Out of 10 desktops I've upgraded here, none ended up with an active xorg.conf file.

This glx error occurs often when the system has nvidia --or-- even more often with intel/nvidia ... in this last release upgrade, and needs the prime driver. If the Xorg.conf file is not there... that prime driver is not working... That error used to come up in the past if the nvidia and nouveau drivers were both trying to load at the same time.

The instructions I have posted in my graphics sticky here... post #2... link to .Xauthority:
You can check it and see if it is there
```

ls -l ~/.Xauthority

``` 
It should be there and the user should be the owner. If there and owner is root, that is not right and someone tried to startx as root. root does not have a home directory so cannot start an X session (no lock on .Xauthority file).

Please also post or attach the file /var/log/Xorg.0.log (<-- This will show if it got past the .Xauthority process.)

These instructions for fixing a suspect ~?.Xauthority file, as root, from the recovery root console. (So also as a SysAdmin):
```

rm /home/User_Name/.Xauthority
touch  /home/User_Name/.Xauthority
chmod 600  /home/User_Name/.Xauthority
chown UserName  /home/User_Name/.Xauthority

```
Use the user's name in place or User_name. If not as root, and as the user, the commands are still the same, but you could use ~/ to shortcut the $HOME...

EDIT-- But if it got a GLX error, that is after the xauth step... So look at the Xorg.0.log file to look for a conflict or driver error.

---

### Post by DuckHook on 2016-06-28
> **MAFoElffen said:**
> ...No one asked what the system's GPU was?Good day, MAFoElffen! Glad you are jumping in here, since your video knowledge is far better than mine. OP did post GPU in post #11. His is a GeForce GTX970.> That error used to come up in the past if the nvidia and nouveau drivers were both trying to load at the same time....shown in post #11 as well. Nouveau and nvidia fighting for control.> so cannot start an X session (no lock on .Xauthority file).The first thing tried. See OP post #5> EDIT-- But if it got a GLX error, that is after the xauth step... So look at the Xorg.0.log file to look for a conflict or driver error....I'm stumped. This one is a tough nut to crack. Especially concerned that OP cannot remove nvidia driver, thus pointing to dpkg issues and not just driver issues. But happy you've dived in as you have way more experience cracking such nuts than me.

---

### Post by MAFoElffen on 2016-06-28
LOL! I missed a whole page before jumping in (sorry for that). I have same card on my Server Management Console (I get bored so it is also a gamer)... My main gamer is two GTX 980ti's in SLI. on top of two Opteron 16-core CPU's.

From what I see here:
- Blacklist the Nouveau driver.  (post #1 of my sticky in my sigline) NVidia's install script will do this, but you do not want it to even try to load that driver on that card!!! (Bad experience on that. Card had just been released.)
- Remove the old nvidia drivers.  (post #1 of my sticky)
- Go to NVidia Downloads with Firefox. (Chromium's Java flavor has problems with NVidia's site)
- Autorecognise for the correct driver. (Java web app on that page).
- Write down the path to and the full file name of. (current version is 367.27)
- make the script executable
```

cd /Path_To/File/
chmod +x scriptname.run

```
- Restart with "nomodeset text" kernel boot option in Grub (instructions linked from post #2 in my sticky) or to a recovery root console
- run the install script (full binary directions linked from Post #2 in my sticky).

Or add and use the edgers ppa. I use NVidia's, but I'm used to commandline. I haven't checked lately, but what used to be in main didn't support that card seties. But the driver was in Edgers. Like I've said, I've always used the NVidia Binaries.

If any more details or see something that needs updating in those instructions, please let me know.

---

### Post by DuckHook on 2016-06-28
> **MAFoElffen said:**
> I get bored so it is also a gamer:shock:

You game on your ***server management console***??? I knew you were a high-wire act, but this takes gonads. You must eat whole cows for breakfast.

@OP

You are in good hands now. MAFoElffen has forgotten more about video than I've ever learned. I hand you off to him.

---

### Post by vpiercy on 2016-06-28
I feel terrible with all this great info coming through. I reinstalled last night. Kubuntu DVD installer quit on me about 89% of the way from being finished. Couldn't cleanup the intramfs script so it just dumped me, asking for a bug report. I used the Ubuntu Minimal CD, had it handy, and now I'm working in Xubuntu. (The Software store doesn't work--the cursor just spins away when I click it. So hopefully I can fix that.) Just got Steam to work--not from the repos but from a gdebi command on the .deb file from Valve's site. 

I want to thank DuckHook for sticking with me through this. The PPA link to the stable nVidia drivers is really nice to know about.

Thank you!

---

### Post by MAFoElffen on 2016-06-28
No problem. There are hundreds of ways to get to the same point. A reinstall is still a solution where you have a running, working system. That was the goal.

Good Luck and enjoy...

Now that you are working to your satisfaction, please revisit this thread and mark is as solved. (Upper right of page in this thread > Select Link "Thread Tools" > Select link "Mark Thread as Solved") This helps other to find answers to their similar problems.

But you might want to wait for that until we get you completely working... Ubuntu Software Center does take a while to start, even with a good internet connection. Remind me-- CPU, Memory and Network card? Failing on your installs, I'm wondering on those spec's.

I also use the .deb from Steam... If you have a slow connection, that is going to make Steam updates last forever. Could you visit: [www.speedtest.net]("http://www.speedtest.net") and tell us what is
tsays your net stats are (speedwise).

---

### Post by vpiercy on 2016-06-28
Here's an edited, condensed version of my hardware specs. Hopefully I didn't leave out anything relevant or leave in too much that's irrelevant. 

```
sudo lshw
```

```
ubuntuv

    width: 64 bits
    capabilities: smbios-3.0 dmi-3.0 vsyscall32
    configuration: boot=normal chassis=desktop family=To be filled by O.E.M. sku=SKU 
  *-core
       description: Motherboard
       product: MAXIMUS VIII RANGER
       vendor: ASUSTeK COMPUTER INC.
       physical id: 0
       version: Rev 1.xx
      
       slot: Default string
     *-firmware
          description: BIOS
          vendor: American Megatrends Inc.
          physical id: 0
          version: 1202
          date: 11/10/2015
          size: 64KiB
          capacity: 15MiB
          capabilities: pci apm upgrade shadowing cdboot bootselect socketedrom edd int13floppy1200 int13floppy720 int13floppy2880 int5printscreen int9keyboard int14serial int17printer acpi usb biosbootspecification [COLOR=#0000ff]uefi[/COLOR]
     *-cache:0
          description: L1 cache
          physical id: 41
          slot: L1 Cache
          size: 128KiB
          capacity: 128KiB
          capabilities: synchronous internal write-back data
          configuration: level=1

     *-cpu
          description: CPU
          product: Intel(R) Core(TM) i7-6700K CPU @ 4.00GHz
          vendor: Intel Corp.
          physical id: 45
          bus info: cpu@0
          version: Intel(R) Core(TM) i7-6700K CPU @ 4.00GHz
          serial: To Be Filled By O.E.M.
          slot: LGA1151
          size: 800MHz
          capacity: 4200MHz
          width: 64 bits
          clock: 100MHz
          capabilities: x86-64 fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx pdpe1gb rdtscp constant_tsc art arch_perfmon pebs bts rep_good nopl xtopology nonstop_tsc aperfmperf eagerfpu pni pclmulqdq dtes64 monitor ds_cpl vmx est tm2 ssse3 sdbg fma cx16 xtpr pdcm pcid sse4_1 sse4_2 x2apic movbe popcnt tsc_deadline_timer aes xsave avx f16c rdrand lahf_lm abm 3dnowprefetch epb intel_pt tpr_shadow vnmi flexpriority ept vpid fsgsbase tsc_adjust bmi1 hle avx2 smep bmi2 erms invpcid rtm mpx rdseed adx smap clflushopt xsaveopt xsavec xgetbv1 dtherm ida arat pln pts hwp hwp_notify hwp_act_window hwp_epp cpufreq
          configuration: cores=4 enabledcores=4 threads=8
     *-memory
          description: System Memory
          physical id: 46
          slot: System board or motherboard
          size: 16GiB
        *-bank:0
             description: DIMM Synchronous 2133 MHz (0.5 ns)
             product: KHX2133C14D4/4G
             vendor: Kingston
             physical id: 0
             slot: ChannelA-DIMM1
             size: 4GiB
             width: 64 bits
             clock: 2133MHz (0.5ns)
        *-bank:1
             description: DIMM Synchronous 2133 MHz (0.5 ns)
             product: KHX2133C14D4/4G
             vendor: Kingston
             physical id: 
             slot: ChannelA-DIMM2
             size: 4GiB
             width: 64 bits
             clock: 2133MHz (0.5ns)
        *-bank:2
             description: DIMM Synchronous 2133 MHz (0.5 ns)
             product: KHX2133C14D4/4G
             vendor: Kingston
             physical id: 
             slot: ChannelB-DIMM1
             size: 4GiB
             width: 64 bits
             clock: 2133MHz (0.5ns)
        *-bank:3
             description: DIMM Synchronous 2133 MHz (0.5 ns)
             product: KHX2133C14D4/4G
             vendor: Kingston
             physical id: 
             slot: ChannelB-DIMM2
             size: 4GiB
             width: 64 bits
             clock: 2133MHz (0.5ns)

             *-usb:1
                   description: Mouse
                   product: Razer DeathAdder
                   vendor: Razer
                   physical id: 8
                   bus info: usb@1:8
                   version: 1.00
                   capabilities: usb-2.00
                   configuration: driver=usbhid maxpower=100mA speed=12Mbit/s
     
           *-display
                description: VGA compatible controller
                product: GM204 [GeForce GTX 970]
                vendor: NVIDIA Corporation
                physical id: 0
                bus info: pci@0000:01:00.0
                version: a1
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress vga_controller bus_master cap_list rom
                configuration: driver=nvidia latency=0
                resources: irq:134 memory:de000000-deffffff memory:c0000000-cfffffff memory:d0000000-d1ffffff ioport:e000(size=128) memory:df000000-df07ffff
           *-multimedia
                description: Audio device
                product: GM204 High Definition Audio Controller
                vendor: NVIDIA Corporation
                physical id: 0.1
                bus info: pci@0000:01:00.1
                version: a1
                width: 32 bits
                clock: 33MHz
                capabilities: pm msi pciexpress bus_master cap_list
                configuration: driver=snd_hda_intel latency=0
                resources: irq:17 memory:df080000-df083fff
        
        *-communication
             description: Communication controller
             product: Sunrise Point-H CSME HECI #1
             vendor: Intel Corporation
             physical id: 16
             bus info: pci@0000:00:16.0
             version: 31
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi bus_master cap_list
             configuration: driver=mei_me latency=0
             resources: irq:132 memory:df24d000-df24dfff
        
        *-network
             description: Ethernet interface
             product: Ethernet Connection (2) I219-V
             vendor: Intel Corporation
             physical id: 1f.6
             bus info: pci@0000:00:1f.6
             logical name: enp0s31f6
             version: 31
             serial: 30:5a:3a:00:79:08
             size: 1Gbit/s
             capacity: 1Gbit/s
             width: 32 bits
             clock: 33MHz
             capabilities: pm msi bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
             configuration: autonegotiation=on broadcast=yes driver=e1000e driverversion=3.2.6-k duplex=full firmware=0.7-4 ip=192.168.1.176 latency=0 link=yes multicast=yes port=twisted pair speed=1Gbit/s
             resources: irq:131 memory:df200000-df21ffff
     
```

Attached is a png of Speedtest results. 

Thanks!

---

### Post by MAFoElffen on 2016-06-29
LOL--> Your connection is almost twice as fast as mine. So that part is working fine for you.


Next test... Look at your /etc/apt/sources.list. Look for the address of the server that hosts your repo for main. For example, mine is 
```

en.archives.ubuntu.com

```
Ping that domain name. Mine averages 138ms.

Time how long it takes to start Ubuntu Softare Center. This morning on this machine, it takes 38 seconds.

---

### Post by vpiercy on 2016-06-30
Thanks for the reply!

I pinged

```
us.archive.ubuntu.com
```

and got repeating lines that said the following, +/- .3 ms: 

```
64 bytes from economy.canonical.com (91.189.91.23): icmp_seq=5 ttl=45 time=71.4 ms


```

RepoGen looks like an easy way to generate a new sources.list file: [https://repogen.simplylinux.ch/generate.php](https://repogen.simplylinux.ch/generate.php). Would I have to generate keys for any added site with commands like this: 

```
sudo apt-key adv --keyserver pgp.mit.edu --recv-keys 5044912E
wget -q -O- http://archive.getdeb.net/getdeb-archive.key | sudo apt-key add -
```

I clicked "Software" in Xubuntu's start list and the cursor clock spun  for a while and nothing happened. It's been at least 10 minutes since I  initiated that. The cursor isn't spinning anymore when I float it over  the toolbar though.

---

### Post by MAFoElffen on 2016-06-30
Odd... 


 Please post the results of, based on what you are having trouble with...

If you are talking about the Xubuntu flavored software center?
```

sudo apt-cache policy software-center
sudo apt-cache policy gnome-software
sudo apt-cache policy gnome-software-common

```
Or if you are talking about the Software Updater?
```

sudo apt-cache policy software-updater 

```

Sorry by just saying "Software," that could be a few different things.

---

### Post by vpiercy on 2016-07-01
For Xubuntu "Software" center, I get the following: 

```
software-center:
  [COLOR=#0000cd]Installed: (none)[/COLOR]
  Candidate: 16.01+16.04.20160420
  Version table:
     16.01+16.04.20160420 500
        500 http://us.archive.ubuntu.com/ubuntu xenial/universe amd64 Packages
        500 http://us.archive.ubuntu.com/ubuntu xenial/universe i386 Packages
        500 http://01.archive.ubuntu.com/ubuntu xenial/universe amd64 Packages
        500 http://01.archive.ubuntu.com/ubuntu xenial/universe i386 Packages


```

For gnome software: 

```
gnome-software:
  Installed: 3.20.1+git20160426.1.a976144-ubuntu-xenial-0ubuntu1
  Candidate: 3.20.1+git20160426.1.a976144-ubuntu-xenial-0ubuntu1
  Version table:
 *** 3.20.1+git20160426.1.a976144-ubuntu-xenial-0ubuntu1 500
        500 http://us.archive.ubuntu.com/ubuntu xenial-updates/main amd64 Packages
        500 http://01.archive.ubuntu.com/ubuntu xenial-updates/main amd64 Packages
        100 /var/lib/dpkg/status
     3.20.1+git20160420.1.ca63436.ubuntu-xenial-0ubuntu2 500
        500 http://us.archive.ubuntu.com/ubuntu xenial/main amd64 Packages
        500 http://01.archive.ubuntu.com/ubuntu xenial/main amd64 Packages
```

For gnome software common: 

```
gnome-software-common:
  Installed: 3.20.1+git20160426.1.a976144-ubuntu-xenial-0ubuntu1
  Candidate: 3.20.1+git20160426.1.a976144-ubuntu-xenial-0ubuntu1
  Version table:
 *** 3.20.1+git20160426.1.a976144-ubuntu-xenial-0ubuntu1 500
        500 http://us.archive.ubuntu.com/ubuntu xenial-updates/main amd64 Packages
        500 http://us.archive.ubuntu.com/ubuntu xenial-updates/main i386 Packages
        500 http://01.archive.ubuntu.com/ubuntu xenial-updates/main amd64 Packages
        500 http://01.archive.ubuntu.com/ubuntu xenial-updates/main i386 Packages
        100 /var/lib/dpkg/status
     3.20.1+git20160420.1.ca63436.ubuntu-xenial-0ubuntu2 500
        500 http://us.archive.ubuntu.com/ubuntu xenial/main amd64 Packages
        500 http://us.archive.ubuntu.com/ubuntu xenial/main i386 Packages
        500 http://01.archive.ubuntu.com/ubuntu xenial/main amd64 Packages
        500 http://01.archive.ubuntu.com/ubuntu xenial/main i386 Packages
```

The Updater seems to work. (It said there were updates this morning and installed them no problem.) But the output of the command wasn't what I expected: 

```
N: Unable to locate package software-updater


```

I'm currently looking online for ways to add the Xubuntu software center.

---

