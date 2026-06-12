---
title: "Slow boot in Ubuntu 14.04."
date: 2015-01-09
forum: Installation &amp; Upgrades
---

### Post by wonjun on 2015-01-09
Hello,

From the Grub menu to the Desktop screen - it takes slightly more than 1 minute. I'm wondering if there is a way to improve my boot time?


Details:
OS : Ubuntu 14.04 LTS
Processor : Intel i5, 3337U
RAM : 6 GB
Video card : NVIDIA GeForce GT 620M 1GB gDDR3 Graphic Memory (Optimus)


[https://www.dropbox.com/s/jhe053q9auz11cz/boottime?dl=0](https://www.dropbox.com/s/jhe053q9auz11cz/boottime?dl=0)
shows the details of the boot when I compiled 
dmesg > boottime

---

### Post by kerry_s on 2015-01-09
just don't shut down. use the suspend. i never turn mine off/shutdown.

---

### Post by MAFoElffen on 2015-01-09
That link you posted, sends me an sdx file ,that does not work for me... And that is odd that it does not work.

Go to the /var/log/bootchart directory. Find the latest <computerName><version><date>.png file and attach it to a post. What that graphics file will show in chart form is on-boot each process that starts up when, and how long it took.

(In the future, this is available in more detail, in a different flavor, through systemd... But we're still testing that in the V cycle, to see if that is ready for public consumption.)

---

### Post by jrdobelmann on 2015-01-09
I don't know for sure, but a basic tip would be to try and cut down on the amount of daemons and programs your computer loads when it boots up.  Check through your startup programs, and if there are any programs that you don't necessarily need on startup, try removing them and see if that speeds things up.

---

### Post by kerry_s on 2015-01-09
> **jrdobelmann said:**
> I don't know for sure, but a basic tip would be to try and cut down on the amount of daemons and programs your computer loads when it boots up.  Check through your startup programs, and if there are any programs that you don't necessarily need on startup, try removing them and see if that speeds things up.

i don't recommend messing with the startup apps. unless your adding or removing things you added.

---

### Post by wonjun on 2015-01-10
> **MAFoElffen said:**
> That link you posted, sends me an sdx file ,that does not work for me... And that is odd that it does not work.

Go to the /var/log/bootchart directory. Find the latest <computerName><version><date>.png file and attach it to a post. What that graphics file will show in chart form is on-boot each process that starts up when, and how long it took.

(In the future, this is available in more detail, in a different flavor, through systemd... But we're still testing that in the V cycle, to see if that is ready for public consumption.)




Yes, that is strange, as its a text file. (gedit)
I can't seem to find the /var/log/bootchart directory.

---

### Post by wonjun on 2015-01-10
> **jrdobelmann said:**
> I don't know for sure, but a basic tip would be to try and cut down on the amount of daemons and programs your computer loads when it boots up.  Check through your startup programs, and if there are any programs that you don't necessarily need on startup, try removing them and see if that speeds things up.


I have disabled some of the startup programs that my computer loads, but can't see any benefit. :(

---

### Post by MAFoElffen on 2015-01-10
I used this in Dev cyles to see what was going on:
[https://wiki.ubuntu.com/BootCharting](https://wiki.ubuntu.com/BootCharting)

If not installed (since it doesn't have that directory, it may not be), then
```

sudo apt-get install bootchart

```
No config needed to it. After each reboot, a chart graphics file will appear in that directory.

If you have limited space on your storage, you may want to remove it after you are through using it... It archives old iterations, but will, over time and different distro's, eventually add up. 
```

sudo apt-get remove bootchart
sudo rm -rf /var/log/bootchart

```
Not documented, but the reason it adds up, is it isolates the name of the installed OS version as different iteration roll-overs.

---

### Post by MAFoElffen on 2015-01-10
The real way to break this down is to divide that into:
-Is this because of something in your kernel and core system boot?
-Is this something is your Plymouth, X Graphics Layer, Desktop boot?

The way to divide that up is to first boot into a text mode with debug and verbose messaging turn on. At the grub menu, remove "quiet splash" and append 
```

--verbose debug drm.debug=0xe plymouth:debug text

```That will boot into a text mode, with a lot of messages telling you what is going on (in detail). That will end at a text console with prompt asking you to log in with your credentials.

Log in. At the CLI prompt, enter 
```

startx
[code]
Plymouth, XServer and the Desktop will load (without going through the graphical login manager).

That would give you an idea of where it is stalling... and record all of what went on on the /var/log/syslog and /var/log/Xorg.0.log files. The only thing that would skip is the Graphical login.

When you exit out of the desktop, it will exit back down to console prompt... So, instead, if select reboot, it will reboot the computer and start normal. That, or shutdown from the prompt:
[code]
sudo shutdown -P now

```

---

### Post by oldfred on 2015-01-11
Another thing to check is the loading of drivers as you boot. 
If you remove quiet splash you see boot process, but now with quick booting that can go by too quick.
But all the booting is in /var/log/dmesg so you can use Log File Viewer or just open it with a text editor.
You want to look for errors, warning, repeated tries at loading and either failure or later success and long differences in timestamps. No need to post entire thing, it is long and most not useful. 

My old laptop says 28.6 seconds after grub loading.
But I do have a long time with either a firewire that does not exist and drive is MBR, or mounting swap? oldfred off to check his system.

```
[    1.884273] firewire_core: created device fw0: GUID 00080da0d15d3e31, S400
[   26.440289] Adding 3065852k swap on /dev/sda6.  Priority:-1 extents:1 across:3065852k 

```

---

### Post by pfeiffep on 2015-01-12
> **wonjun said:**
> Hello,

From the Grub menu to the Desktop screen - it takes slightly more than 1 minute. I'm wondering if there is a way to improve my boot time?

Details:
OS : Ubuntu 14.04 LTS
Processor : Intel i5, 3337U
RAM : 6 GB
Video card : NVIDIA GeForce GT 620M 1GB gDDR3 Graphic Memory (Optimus)

[https://www.dropbox.com/s/jhe053q9auz11cz/boottime?dl=0](https://www.dropbox.com/s/jhe053q9auz11cz/boottime?dl=0)
shows the details of the boot when I compiled 
dmesg > boottime 
Steps that I took when I first started using Ubuntu 12.10 (most of these have remained similar in 14.04)
Most of the ideas came from this [site]("https://sites.google.com/site/easylinuxtipsproject/speed")
[LIST]
[*]Installed gnome session fallback (now called flashback) 
[*]Changed swappiness to 10 
[*]installed preload 
[*]installed Bleachbit (I run in just prior to shut down) (the operations this performs can be done manually at command line - I prefer the gui) 
[*]disabled from startup those applications I don't use or need (be careful here you CAN break your installation) 
[*]I only keep 2 kernels (current + 1 previous) 
[*]If you have a multi boot system (2 OSes installed) Changed grub time out 
[/LIST]
I really didn't have a boot time issue that I was attempting to solve, these steps just seemed to make sense to me. I haven't measured my boot time, but my perception is it pretty constant.

---

### Post by MAFoElffen on 2015-01-12
pfieffep-
And with 15.04, that will all change (in a major way!), but generally, will be faster anyways. The tools are there to really micro-manage and analyze startup and times.

Outside of fixing something that is wrong or a "problem", when we switch to systemd, if you are investing time on tuning the init, that process will be "different". That is less than 3 months away now...

For example- Removing old kernels will save you some space, up the kernel update process for Desktop now does that a part of the Kernel update process (where it used to be that you had to remove on your own... Be that as it may, havinf 2 kernels or 20, does not affect the startup process.

For the Kernel startup process you can do some tuning, but the next update in a couple months and that whole process changes the how it starts. Fingers crossed- that will happen then (or eventually.)

Look at the attachment.
That is a 15 year old (2005) SLI board w/ 14.04. If you look from start to around 40 seconds, it is screaming. From 40 seconds to 155 seconds, It is bored. Between 155 second to 205 seconds, It is crunching things again.

The slack time between (95 seconds of sleep)... It is playing a high resolution animated custom slash... and I am entering my credentials at no rush, logging in at my own sweet time. Not even flexing any muscle to do any of that.

In the first 40 seconds, that includes spinning up 10 drives and mounting local shares.

Next jump, after entering the credentials... Network authenticated login, network shares, XServer with nVidia SLI on four montiors, with custom EDID and 1920x1080i. Also Kicks off temp and fan queries, server health queiries, network load queries, local weather, synching with the network time server, etc... and brings all that back into my Conky desktop script. (all in that last 50 seconds). You can see that it is not woking hard those last 50 seconds. Most of that is waiting on other network attached resources to bring back info, for it to fill in the Conky Desktop.

Admittedly, I have allot more going on that an average user.

---

### Post by pfeiffep on 2015-01-13
> **MAFoElffen said:**
> pfieffep-
And with 15.04, that will all change (in a major way!), but generally, will be faster anyways. The tools are there to really micro-manage and analyze startup and times.

Outside of fixing something that is wrong or a "problem", when we switch to systemd, if you are investing time on tuning the init, that process will be "different". That is less than 3 months away now...Thanks for your reply. I'll certainly test out 15.04 eventually,  but I plan to stay with LTS. After 38 years in the computer industry  starting with Harris super-minis I only want to keep abreast of the  newest features in a superficial way; hence the not using CLI to do the  work.

> For example- Removing old kernels will save you some space, up the kernel update process for Desktop now does that a part of the Kernel update process (where it used to be that you had to remove on your own... Be that as it may, havinf 2 kernels or 20, does not affect the startup process.

For the Kernel startup process you can do some tuning, but the next update in a couple months and that whole process changes the how it starts. Fingers crossed- that will happen then (or eventually.)I absolutely understand the startup process - this step was keep a small hard drive from filling up

> Look at the attachment.
That is a 15 year old (2005) SLI board w/ 14.04. If you look from start to around 40 seconds, it is screaming. From 40 seconds to 155 seconds, It is bored. Between 155 second to 205 seconds, It is crunching things again.

The slack time between (95 seconds of sleep)... It is playing a high resolution animated custom slash... and I am entering my credentials at no rush, logging in at my own sweet time. Not even flexing any muscle to do any of that.

In the first 40 seconds, that includes spinning up 10 drives and mounting local shares.The attachment is way to small for me to read effectively

> Next jump, after entering the credentials... Network authenticated login, network shares, XServer with nVidia SLI on four montiors, with custom EDID and 1920x1080i. Also Kicks off temp and fan queries, server health queiries, network load queries, local weather, synching with the network time server, etc... and brings all that back into my Conky desktop script. (all in that last 50 seconds). You can see that it is not woking hard those last 50 seconds. Most of that is waiting on other network attached resources to bring back info, for it to fill in the Conky Desktop
Admittedly, I have allot more going on that an average user.I hope that I don't have to resort to analyzing to this level just to 'use' an OS (I had enough of that in my professional life).

---

### Post by wonjun on 2015-01-13
Thanks for your replies. I've attached my bootchart image.
Since I was busy, I couldn't do what MAFoElffen suggested at the end of page 1. I will let you know the details soon.

---

### Post by wonjun on 2015-01-13
I do not know why the picture is so unclear.
Here's the dropbox link.

[https://www.dropbox.com/s/wduj623ev0ynhyf/trusty-20150113-3.png?dl=0](https://www.dropbox.com/s/wduj623ev0ynhyf/trusty-20150113-3.png?dl=0)

---

