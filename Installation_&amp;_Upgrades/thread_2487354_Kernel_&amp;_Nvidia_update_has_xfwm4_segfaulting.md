---
title: "Kernel &amp; Nvidia update has xfwm4 segfaulting"
date: 2023-05-31
forum: Installation &amp; Upgrades
---

### Post by Ken_g6 on 2023-05-31
I've been running XUbuntu fine for years. Upgraded to 20.04 in the last few months without major issues. This morning I installed a simple kernel update and it broke xfce.

First I was in a graphical login loop. A search for solutions led me to upgrade my Nvidia driver from 470 to 525. That fixed the login, but xfce won't start. Syslog says kernel... xfwm4... segfault at 10 ip... error 4 in libpthread-2.31.so, six times.

I also tried removing ~/.config/xfce* with no useful effect. Ideas?

---

### Post by #&amp;thj^% on 2023-05-31
I had nothing but woe's with nVidia-525, and I use the PPA driver version of:
```
apt policy nvidia-driver-530 nvidia-dkms-530
nvidia-driver-530:
  Installed: 530.41.03-0ubuntu2
  Candidate: 530.41.03-0ubuntu2
  Version table:
 *** 530.41.03-0ubuntu2 500
        100 http://archive.ubuntu.com/ubuntu lunar-proposed/multiverse amd64 Packages
        500 https://ppa.launchpadcontent.net/graphics-drivers/ppa/ubuntu lunar/main amd64 Packages
        100 /var/lib/dpkg/status
nvidia-dkms-530:
  Installed: 530.41.03-0ubuntu2
  Candidate: 530.41.03-0ubuntu2
  Version table:
 *** 530.41.03-0ubuntu2 500
        100 http://archive.ubuntu.com/ubuntu lunar-proposed/multiverse amd64 Packages
        500 https://ppa.launchpadcontent.net/graphics-drivers/ppa/ubuntu lunar/main amd64 Packages
        100 /var/lib/dpkg/status

```
Is the correct dkms installed?
Also can you post this back?
```
inxi -bz
System:
  Kernel: 6.2.0-20-generic arch: x86_64 bits: 64 Desktop: Unity v: 7.7.0
    Distro: Ubuntu 23.04 (Lunar Lobster)
Machine:
  Type: Laptop System: LENOVO product: 82B5 v: Lenovo Legion 5 15ARH05
    serial: <superuser required>
  Mobo: LENOVO model: LNVNB161216 v: SDK0J40709 WIN
    serial: <superuser required> UEFI: LENOVO v: EUCN37WW date: 04/14/2022
Battery:
  ID-1: BAT0 charge: 56.4 Wh (100.0%) condition: 56.4/60.0 Wh (94.0%)
CPU:
  Info: 6-core AMD Ryzen 5 4600H with Radeon Graphics [MT MCP] speed (MHz):
    avg: 1456 min/max: 1400/3000
Graphics:
  Device-1: NVIDIA TU117M [GeForce GTX 1650 Ti Mobile] driver: nvidia
    v: 530.41.03
  Device-2: Syntek Integrated Camera type: USB driver: uvcvideo
  Display: x11 server: X.Org v: 1.21.1.7 driver: X: loaded: nvidia
    unloaded: fbdev,modesetting,nouveau,vesa gpu: nvidia,nvidia-nvswitch
    resolution: 1920x1080~120Hz
  API: OpenGL v: 4.6.0 NVIDIA 530.41.03 renderer: NVIDIA GeForce GTX 1650
    Ti/PCIe/SSE2
Network:
  Device-1: Realtek RTL8111/8168/8411 PCI Express Gigabit Ethernet
    driver: r8169
  Device-2: NetGear A6100 AC600 DB Wireless Adapter [Realtek RTL8811AU]
    type: USB driver: N/A
  Device-3: Realtek RTL8153 Gigabit Ethernet Adapter type: USB driver: r8152
  Device-4: Realtek RTL8153 Gigabit Ethernet Adapter type: USB driver: r8152
Drives:
  Local Storage: total: 4.56 TiB used: 1.33 TiB (29.2%)
Info:
  Processes: 372 Uptime: 1h 9m Memory: 7.61 GiB used: 2.73 GiB (35.9%)
  Shell: Bash inxi: 3.3.25

```

---

### Post by Ken_g6 on 2023-05-31
Driver and dkms match. Aptitude did a good job.

```
 System:
  Kernel: 5.4.0-150-generic x86_64 bits: 64 Desktop: Xfce 4.14.2 
  Distro: Ubuntu 20.04.6 LTS (Focal Fossa) 
Machine:
  Type: Desktop System: Gigabyte product: N/A v: N/A serial: <filter> 
  Mobo: Gigabyte model: Z170N-WIFI-CF v: x.x serial: <filter> 
  UEFI [Legacy]: American Megatrends v: F4 date: 09/04/2015 
CPU:
  Quad Core: Intel Core i7-6700 type: MT MCP speed: 1434 MHz 
  min/max: 800/4000 MHz 
Graphics:
  Device-1: NVIDIA GP106 [GeForce GTX 1060 3GB] driver: nvidia v: 525.105.17 
  Display: x11 server: X.Org 1.20.13 driver: nvidia 
  resolution: 1920x1080~60Hz 
  OpenGL: renderer: NVIDIA GeForce GTX 1060 3GB/PCIe/SSE2 
  v: 4.6.0 NVIDIA 525.105.17 
Network:
  Device-1: Intel Ethernet I219-V driver: e1000e 
  Device-2: Intel I211 Gigabit Network driver: igb 
  Device-3: Intel Wireless 8260 driver: iwlwifi 
Drives:
  Local Storage: total: 16.83 TiB used: 15.10 TiB (89.8%) 
Info:
  Processes: 305 Uptime: 5m Memory: 31.31 GiB used: 1.34 GiB (4.3%) 
  Shell: bash inxi: 3.0.38 

```

---

### Post by Ken_g6 on 2023-05-31
I looked again at syslog without grepping for error and I found an additional error code:

```
Code: 7e 8f 45 31 d2 ba 01 00 00 00 be 01 00 00 00 48 89 ef b8 ca 00 00 00 0f 05 e9 73 ff ff ff e8 13 b7 ff ff 0f 1f 00 f3 0f 1e fa <8b> 47 10 89 c2 81 e2 7f 01 00 00 90 83 e0 7c 75 7b 53 48 83 ec 10
```

Possibly relevant: [https://gitlab.com/libvirt/libvirt/-/issues/218](https://gitlab.com/libvirt/libvirt/-/issues/218)

---

### Post by MAFoElffen on 2023-06-01
Please run this (1falen is on the Test Team of this Project)
```

wget -N -t 5 -T 10 https://github.com/UbuntuForums/system-info/raw/main/system-info && \
chmod +x system-info && \
./system-info --details

```
(C)ontinue (first letter <c>, <Enter>) when prompted that there might be some utilities missing. When asked if you want to upload the report, say (Y)es. Copy the URL of the pastebin the report gets uploaded to... That would show us a bit of detial about the hardware and installed system that you have installed on.

You say you are using Xubuntu 20.04.6, nVidia driver version 525, and using Linux Kernel  5.4.0-150-generic, Xfce 4.14.2 ... The nVidia card is GeForce GTX 1060 3GB... The motherboard is Gigabyte model: Z170N-WIFI-CF, with a 7th Gen i7... (I have most of that hardware to test and try to recreate...)

The crash you posted linked to at GitLab was about something that only happened with kernel a call (from Linix Kernel 5.4.0-84-generic) when service libvirtd (version 7.0.0) was restarted... This error supposedly went away if libvirt version 7.-.6 was used... Are you saying that you have KVM / QEMU installed and see this error, with a different version of Kernel and Libvirt? Or did you Google the dump and it brought up that link?

Maybe we should see 
```

sudo dmesg | grep -i 'warning\|error'

```

Your chief complaint is that desktop  "xfwm4 does not start"... Before login, press <Ctrl><F4> to toggle to Console Session vtty4 and use your UserName and Password to log in. Then do
```

rm -r ~/.cache/sessions/*

```
Then toggle back to <Ctrl><F7> to get back to the Graphical Login and login, trying to start xfwm4... Sometimes that cache gets corrupted and clearing that cache helps with that.

---

### Post by Ken_g6 on 2023-06-01
I don't much trust rando scripts. I really don't trust rando scripts asking for sudo. That link was just something I googled, yes. dmesg adds nothing relevant, just initializations that mention "errors". 

Interesting, clearing the session cache fixed it... temporarily. Launching Terminal or Firefox crashes xfwm4 with the same error. But I can launch a dice game called Tali without error.

I'm thinking of doing something that's probably really stupid: switching libc6 to the Debian version. Because my error and the googled link mention libpthread. I'll sleep on it.

---

### Post by QIII on 2023-06-01
Hello.

1.  Those are not "rando scripts".  They are not scripts at all.  They are very standard commands that will provide a specific tool and return diagnostic information.  If you do not understand them, you are always free to ask for explanation or clarification.  In fact, you stand to learn something by doing so.  But please don&#8217;t dismiss them as suspicious.

2.  MAFoElffen is a long time member of the Forums, a former member of the Forums Staff, and is extremely knowledgeable.  Please give MAFoElffen some credit before casting a suspicious eye on someone who is trying to help.

3. 1Fallen is well known to the community and to the Staff.  There is no need for mistrust there.  You may rest assured that there is no nefarious intent.  Neither is there any lack of understanding &#8211; especially with regard to Xubuntu.  Again:  someone is trying to help.

4.  Given the length of time since you joined, it seems you might by now understand that this is generally how support is provided in the Linux community.  The extent to which you are unwilling to use the commands and provide the feedback requested will be reflected in the completeness of the advice those volunteers will be able to provide.  Your choice, of course.

&#8220;Something stupid&#8221;?  I wouldn&#8217;t say that.  Ill-advised, perhaps.  It&#8217;s more probably simply unnecessary.  Arbitrarily changing something before diagnostic information has been made available for others to examine might complicate the process of finding a solution.

---

### Post by MAFoElffen on 2023-06-01
LOL. 

I don't "have" to help you. I am just a volunteer here to provide support. We are not paid. I just like to help people that need help. 

That is why I authored that Script, am the Project Leader, and gave it to the Forum: To help Members here to easily be able to come up with informed recommendations for solutions... The report it generates, enables that.

I submitted that Script to the Ubuntu Forum's Admin Council, for their successful review, acceptance and endorsement... Then I was made the Administrator for their GitHub Repo for it. I hope others will carry it on, when I no longer can. I hope it will benefit the community here and outlive me.

That Script you suspect:
One of the two stickies on this Forum: [https://ubuntuforums.org/showthread.php?t=2475931](https://ubuntuforums.org/showthread.php?t=2475931)
 The UbuntuForums GitHub Repo for STABLE: [https://github.com/UbuntuForums/system-info](https://github.com/UbuntuForums/system-info)
The DEV GitHub Repo: [https://github.com/Mafoelffen1/system-info/blob/main/system-info](https://github.com/Mafoelffen1/system-info/blob/main/system-info)
The PPA for the Debian packages: [https://launchpad.net/~mafoelffen/+archive/ubuntu/system-info?field.series_filter=](https://launchpad.net/~mafoelffen/+archive/ubuntu/system-info?field.series_filter=)
The development thread, here on the Forum: [https://ubuntuforums.org/showthread.php?t=2465764](https://ubuntuforums.org/showthread.php?t=2465764)
The external review by DistroWatch: [https://distrowatch.com/dwres.php?resource=showheadline&story=14292](https://distrowatch.com/dwres.php?resource=showheadline&story=14292)

You don't know me. I'll leave all that to your own investigation:
[https://wiki.ubuntu.com/mafoelffen](https://wiki.ubuntu.com/mafoelffen)
 [https://launchpad.net/~mafoelffen](https://launchpad.net/~mafoelffen)

I do a few things "Ubuntu"...

---

### Post by Ken_g6 on 2023-06-01
I'm sorry. I didn't see the sticky before. I'm also grumpy having to do everything on my phone. Here's my paste: [https://pastebin.ubuntu.com/p/ngzDVMdFZP/](https://pastebin.ubuntu.com/p/ngzDVMdFZP/)

---

### Post by MAFoElffen on 2023-06-01
I see a good system install and configuration on good hardware... (???) Nothing leaps out at me at this point.

Clearing the cache starts fine, then escalates back to where it was, and is progressing. Like you, I think it is from that recent update, where, just after, it started. I didn't see any problems here, when trying to recreate it here with the 4 VM's that I built.

I suspect something along the lines of libc6, libglib or xfce4-session... But your's getting segfaults and core dumps in your syslogs, I think it's really something for Launchpad to look into (deeply). I suspect they will talk you through doing backtraces on your crashes for them to analyze what may be going on.

I would file it (starting) against xfce4, and let them figure out where to change that to from there.

I checked many bug reports at GitLab on xfce4 and segfaults, but couldn't find anythig more recent than the last closed out a few months ago... Nothing caught my eye, like what you have described so far. 

I am curious what they find. So please, provide me a link to follow the bug report.

---

### Post by Ken_g6 on 2023-06-02
Issue just created: [https://gitlab.xfce.org/xfce/xfwm4/-/issues/727](https://gitlab.xfce.org/xfce/xfwm4/-/issues/727)

I'm not sure how long I'll stick with it.  It's very hard to use this computer without a window manager, though Chromium loads sufficiently large that it's mostly working.  It's probably time to look for a new distro anyway, because I'm not a fan of snaps, as you might have noticed.

---

### Post by MAFoElffen on 2023-06-02
LOL!!! Yes. I noticed that in that report. I sincerely applaud what I saw there. I think we might have similar backgrounds in some things. I saw from the original install, that you have a lot of experience using Ubuntu for very many years.

What I suspect, your problem won't matter if you change to Debian, Arch, RHEL, SUSE... It is related to upstream xfce4 itself... I went through related Bug Reports for all distro's. Although with versioning of the framework, it could be resolved just by those.

Like me, you have been a Linux User for many years. From time to time, things just happen during updates. People make mistakes. We are all human. I face this very often doing development cycle testing, verifications, etc. 

This seems to be a bad regression call hidden somewhere in the code, where it is making a bad call to something, caused by a 'perfect storm' type of conditions. Reporting that as a Bug "somewhere" helps, not just you, but others that might be caught up and affected by that. That is basically how Linux grows and gets better. Someone has to take a step to make that happen.

I understand that it means a bit of work and time to do that. I submit Bug Reports many times over the years. Especially in my support of the Linux Graphics Layer. I try to look at Linux as a whole. 

Reporting this as a Bug Report-- You 'can' help in that way. Since xfce4 is upstream (XFCE), reporting it through Launchpad.net will get Ubuntu, Debian and XFCE working on it to find out what is wrong, and get it corrected.

See the logic in that?

---

### Post by Ken_g6 on 2023-06-02
I see, I reported in the wrong place. [https://bugs.launchpad.net/ubuntu/+source/gtk-theme-switch/+bug/2022818](https://bugs.launchpad.net/ubuntu/+source/gtk-theme-switch/+bug/2022818)

I see the value in reporting the bug, but I also want to get my main machine working normally again.  I'm trying to decide how long I should wait to see if Launchpad finds a quick solution, or if I should get a new SSD for a new OS and set the current one aside.  Big SSDs have gotten cheap. :)

---

### Post by Ken_g6 on 2023-06-03
I found a workaround!  The Fluxbox window manager is minimal enough that it interferes very little with xfce and helps a lot.

[LIST=1]
[*]Start a terminal window.  Right-click on the desktop and point to the Applications menu if necessary.  Starting a new window manager has to be done from X, not from a ctrl-alt terminal.
[*]The first time, run `sudo apt install fluxbox`
[*]Run fluxbox.
[*]Fluxbox showed me its own panel, but it also restored Xfce's!  So I right-clicked on the Fluxbox panel and hid it.
[/LIST]
Everything's nearly normal now. :)  Window headings look a little weird and the control menu (upper-left) doesn't seem to do anything.  Maybe that's normal with Fluxbox.  Chromium is also having an issue where dropdown menus flicker and disappear immediately.  I don't know if that's related; my main browser is Firefox.

---

### Post by MAFoElffen on 2023-06-03
Maybe they can change that to xcfe4... Or maybe they will have you refile that against that. IDK. Dealing with a few personal fires at the moment.

---

### Post by Ken_g6 on 2023-06-14
Someone kindly made a suggestion on the XFCE site.  It seems to have worked:

```
xfconf-query -p /general/vblank_mode -c xfwm4 -s off
```

---

### Post by MAFoElffen on 2023-06-14
I'm happy that you found some resolution to that. Curious just what that command did to resolve that. 

For my own curiosity and learning what worked for that... Could you please post the link to that so I can see what it did?

---

### Post by Ken_g6 on 2023-06-14
"disabling GL vblank" is what somebody said it's for, in the link at the top of page 2 in this thread, which I'm posting again here:

[https://gitlab.xfce.org/xfce/xfwm4/-/issues/727](https://gitlab.xfce.org/xfce/xfwm4/-/issues/727)

---

