---
title: "Ubuntu 16.04 GUI not working after upgrade"
date: 2019-11-15
forum: Installation &amp; Upgrades
---

### Post by urubu66 on 2019-11-15
So I had a 14.04 on a computer I don't really use anymore, today I did the upgrade dist, took a couple hours, everything seemed fine.
At the end it asked me to reboot, as expected. Upon reboot I get this


[https://i.imgur.com/DGPW4gl.jpg](https://i.imgur.com/DGPW4gl.jpg)

I had to reset as nothing seemed to respond. After starting up I get this screen now

[https://i.imgur.com/QPe6orT.jpg](https://i.imgur.com/QPe6orT.jpg)
a CTRL ALT F2 gives me the expected terminal-like thing, which seemed to work fine and made me think it's just the GUI that's the problem. 

But then I tried to do a sudo apt-get update, which didn't work either and gave me
[https://i.imgur.com/RjaCOTC.jpg](https://i.imgur.com/RjaCOTC.jpg)

so maybe it's a bigger problem?

It would be a major inconvenience if I had to wipe the partition and do a clean install, so any and all help is appreciated.

---

### Post by mörgæs on 2019-11-16
Hi, welcome to the fora.

I understand that a clean install of 18.04 or 19.10 might take some time if you have a complicated setup. On the other hand: 

Your post has been sitting for 20 hours without getting an answer. If you get one after X hours of additional waiting the solution may or may not work. If it does you will be running 16.04 and some day in the future you will have to repeat the process in order to get to a more recent release. We don't know wheter that will be smooth sailing or if problems are going to reappear. 

I tend to go for a clean install in these cases.

---

### Post by Impavidus on 2019-11-18
+1 to mörgæs.

Furthermore, you didn't really use that 14.04 system anymore, so it can't be that valuable. You may have some valuable data on it, but that's all backed up, right? I suggest a fresh install of 18.04 or 19.10. Normally I don't recommend to install interim releases, but both of them are just a single upgrade away from the next LTS release.

Two of the screenshots you provided clearly indicate file system problems. Formatting the partition and making a fresh install should fix that. Unless your hard drive is broken, which isn't unlikely.

---

### Post by urubu66 on 2019-11-23
Thanks for the advice. I've backed up all the files. 
Problem is that I have Telegram and Skype on there, with histories that go back to 2014 and I'm not sure those are able to get backed up in any way. 
It won't be the end of the world if I lose them, but it would be worth it to spend a couple extra hours to try and preserve.

Also, and this is more philosophical than anything, I like the idea of every problem being solvable.

---

### Post by mörgæs on 2019-11-23
Even if you manage to upgrade you will need a backup of the two sets of data. Better to do it before attempting.  

At least for Skype it looks easy: [https://support.skype.com/en/faq/FA34894/how-do-i-export-my-skype-files-and-chat-history](https://support.skype.com/en/faq/FA34894/how-do-i-export-my-skype-files-and-chat-history)

---

### Post by rsteinmetz70112 on 2019-11-26
I just saw this post.
If you're still watching this.

Can you get to the graphic login screen? 
Does the error appear after you login or before?

I'm not sure why you system is trying to load website on reboot. That is pretty odd. Do you know why that happens?
It is likely something left over from you 14.04 installation.

Since you can get to a terminal session I'd suggest trying to run ```
startx
``` and see what happens.

You might also try adding another user and logging into that user to get to a gui.

I suspect your problem is with the user set up.

---

### Post by urubu66 on 2020-01-14
Hi guys,
so after posting here and before rsteinmetz commented, I was searching around, found some manual somewhere on how to install xubuntu desktop over ubuntu, which gave me a functional yet extremely buggy gui. I uninstalled some programs that I thought might have been causing the problem, wine1.4 being the main suspect, but it didn't seem to change much. Just picked up the laptop again for the first time since, dedicated to get it working:D

So far I have 
-Xubuntu background, all my desktop shortcuts, none of them work
-no taskbar anywhere
-no titlebar on most programs I get started (the one that contains _ square X usually)
-the apt-get update command doesn't work
-CTRL ALT T doesn't work

What does work is, I can right click on the desktop, launch a terminal and I can start firefox and probably any other program using this method, which makes me mildly confident that whatever problem that is here is solvable.

I suppose the first thing to do is figure out why I can't update my system? 

```

sudo apt-get update
Hit:1 http://security.ubuntu.com/ubuntu xenial-security InRelease
Hit:2 http://archive.canonical.com/ubuntu xenial InRelease                     
Hit:3 http://archive.ubuntu.com/ubuntu xenial InRelease                        
*** Error in `appstreamcli': double free or corruption (fasttop): 0x0000000001fd3940 ***
======= Backtrace: =========
/lib/x86_64-linux-gnu/libc.so.6(+0x777e5)[0x7fb8c871a7e5]
/lib/x86_64-linux-gnu/libc.so.6(+0x8037a)[0x7fb8c872337a]
/lib/x86_64-linux-gnu/libc.so.6(cfree+0x4c)[0x7fb8c872753c]
/usr/lib/x86_64-linux-gnu/libappstream.so.3(as_component_complete+0x439)[0x7fb8c8a9fd19]
/usr/lib/x86_64-linux-gnu/libappstream.so.3(as_data_pool_update+0x44a)[0x7fb8c8aa0f0a]
/usr/lib/x86_64-linux-gnu/libappstream.so.3(as_cache_builder_refresh+0x1c2)[0x7fb8c8a96272]
appstreamcli(ascli_refresh_cache+0x12e)[0x4049de]
appstreamcli(as_client_run+0x6fb)[0x403ceb]
/lib/x86_64-linux-gnu/libc.so.6(__libc_start_main+0xf0)[0x7fb8c86c3830]
appstreamcli(_start+0x29)[0x403519]
======= Memory map: ========
00400000-00408000 r-xp 00000000 08:04 1058779                            /usr/bin/appstreamcli
00607000-00608000 r--p 00007000 08:04 1058779                            /usr/bin/appstreamcli
00608000-00609000 rw-p 00008000 08:04 1058779                            /usr/bin/appstreamcli
015e9000-03190000 rw-p 00000000 00:00 0                                  [heap]
7fb8bc000000-7fb8bc021000 rw-p 00000000 00:00 0 
7fb8bc021000-7fb8c0000000 ---p 00000000 00:00 0 
7fb8c3bbd000-7fb8c3e95000 r--p 00000000 08:04 1050973                    /usr/lib/locale/locale-archive
7fb8c3e95000-7fb8c574b000 r-xp 00000000 08:04 1053126                    /usr/lib/x86_64-linux-gnu/libicudata.so.55.1
7fb8c574b000-7fb8c594a000 ---p 018b6000 08:04 1053126                    /usr/lib/x86_64-linux-gnu/libicudata.so.55.1
7fb8c594a000-7fb8c594b000 r--p 018b5000 08:04 1053126                    /usr/lib/x86_64-linux-gnu/libicudata.so.55.1
7fb8c594b000-7fb8c594c000 rw-p 018b6000 08:04 1053126                    /usr/lib/x86_64-linux-gnu/libicudata.so.55.1
7fb8c594c000-7fb8c5950000 r-xp 00000000 08:04 659587                     /lib/x86_64-linux-gnu/libuuid.so.1.3.0
7fb8c5950000-7fb8c5b4f000 ---p 00004000 08:04 659587                     /lib/x86_64-linux-gnu/libuuid.so.1.3.0
7fb8c5b4f000-7fb8c5b50000 r--p 00003000 08:04 659587                     /lib/x86_64-linux-gnu/libuuid.so.1.3.0
7fb8c5b50000-7fb8c5b51000 rw-p 00004000 08:04 659587                     /lib/x86_64-linux-gnu/libuuid.so.1.3.0
7fb8c5b51000-7fb8c5c59000 r-xp 00000000 08:04 685945                     /lib/x86_64-linux-gnu/libm-2.23.so
7fb8c5c59000-7fb8c5e58000 ---p 00108000 08:04 685945                     /lib/x86_64-linux-gnu/libm-2.23.so
7fb8c5e58000-7fb8c5e59000 r--p 00107000 08:04 685945                     /lib/x86_64-linux-gnu/libm-2.23.so
7fb8c5e59000-7fb8c5e5a000 rw-p 00108000 08:04 685945                     /lib/x86_64-linux-gnu/libm-2.23.so
7fb8c5e5a000-7fb8c5e7b000 r-xp 00000000 08:04 671028                     /lib/x86_64-linux-gnu/liblzma.so.5.0.0
7fb8c5e7b000-7fb8c607a000 ---p 00021000 08:04 671028                     /lib/x86_64-linux-gnu/liblzma.so.5.0.0
7fb8c607a000-7fb8c607b000 r--p 00020000 08:04 671028                     /lib/x86_64-linux-gnu/liblzma.so.5.0.0
7fb8c607b000-7fb8c607c000 rw-p 00021000 08:04 671028                     /lib/x86_64-linux-gnu/liblzma.so.5.0.0
7fb8c607c000-7fb8c61fb000 r-xp 00000000 08:04 1072629                    /usr/lib/x86_64-linux-gnu/libicuuc.so.55.1
7fb8c61fb000-7fb8c63fb000 ---p 0017f000 08:04 1072629                    /usr/lib/x86_64-linux-gnu/libicuuc.so.55.1
7fb8c63fb000-7fb8c640b000 r--p 0017f000 08:04 1072629                    /usr/lib/x86_64-linux-gnu/libicuuc.so.55.1
7fb8c640b000-7fb8c640c000 rw-p 0018f000 08:04 1072629                    /usr/lib/x86_64-linux-gnu/libicuuc.so.55.1
7fb8c640c000-7fb8c6410000 rw-p 00000000 00:00 0 
7fb8c6410000-7fb8c6413000 r-xp 00000000 08:04 685959                     /lib/x86_64-linux-gnu/libdl-2.23.so
7fb8c6413000-7fb8c6612000 ---p 00003000 08:04 685959                     /lib/x86_64-linux-gnu/libdl-2.23.so
7fb8c6612000-7fb8c6613000 r--p 00002000 08:04 685959                     /lib/x86_64-linux-gnu/libdl-2.23.so
7fb8c6613000-7fb8c6614000 rw-p 00003000 08:04 685959                     /lib/x86_64-linux-gnu/libdl-2.23.so
7fb8c6614000-7fb8c662a000 r-xp 00000000 08:04 670824                     /lib/x86_64-linux-gnu/libgcc_s.so.1
7fb8c662a000-7fb8c6829000 ---p 00016000 08:04 670824                     /lib/x86_64-linux-gnu/libgcc_s.so.1
7fb8c6829000-7fb8c682a000 rw-p 00015000 08:04 670824                     /lib/x86_64-linux-gnu/libgcc_s.so.1
7fb8c682a000-7fb8c699c000 r-xp 00000000 08:04 1072599                    /usr/lib/x86_64-linux-gnu/libstdc++.so.6.0.21
7fb8c699c000-7fb8c6b9c000 ---p 00172000 08:04 1072599                    /usr/lib/x86_64-linux-gnu/libstdc++.so.6.0.21
7fb8c6b9c000-7fb8c6ba6000 r--p 00172000 08:04 1072599                    /usr/lib/x86_64-linux-gnu/libstdc++.so.6.0.21
7fb8c6ba6000-7fb8c6ba8000 rw-p 0017c000 08:04 1072599                    /usr/lib/x86_64-linux-gnu/libstdc++.so.6.0.21
7fb8c6ba8000-7fb8c6bac000 rw-p 00000000 00:00 0 
7fb8c6bac000-7fb8c6bdc000 r-xp 00000000 08:04 1062980                    /usr/lib/x86_64-linux-gnu/libprotobuf-lite.so.9.0.1
7fb8c6bdc000-7fb8c6ddb000 ---p 00030000 08:04 1062980                    /usr/lib/x86_64-linux-gnu/libprotobuf-lite.so.9.0.1
7fb8c6ddb000-7fb8c6ddc000 r--p 0002f000 08:04 1062980                    /usr/lib/x86_64-linux-gnu/libprotobuf-lite.so.9.0.1
7fb8c6ddc000-7fb8c6ddd000 rw-p 00030000 08:04 1062980                    /usr/lib/x86_64-linux-gnu/libprotobuf-lite.so.9.0.1
7fb8c6ddd000-7fb8c6fd1000 r-xp 00000000 08:04 1049127                    /usr/lib/x86_64-linux-gnu/libxapian.so.22.7.0
7fb8c6fd1000-7fb8c71d1000 ---p 001f4000 08:04 1049127                    /usr/lib/x86_64-linux-gnu/libxapian.so.22.7.0
7fb8c71d1000-7fb8c71d8000 r--p 001f4000 08:04 1049127                    /usr/lib/x86_64-linux-gnu/libxapian.so.22.7.0
7fb8c71d8000-7fb8c71d9000 rw-p 001fb000 08:04 1049127                    /usr/lib/x86_64-linux-gnu/libxapian.so.22.7.0
7fb8c71d9000-7fb8c71f6000 r-xp 00000000 08:04 1054508                    /usr/lib/x86_64-linux-gnu/libyaml-0.so.2.0.4
7fb8c71f6000-7fb8c73f6000 ---p 0001d000 08:04 1054508                    /usr/lib/x86_64-linux-gnu/libyaml-0.so.2.0.4
7fb8c73f6000-7fb8c73f7000 r--p 0001d000 08:04 1054508                    /usr/lib/x86_64-linux-gnu/libyaml-0.so.2.0.4
7fb8c73f7000-7fb8c73f8000 rw-p 0001e000 08:04 1054508                    /usr/lib/x86_64-linux-gnu/libyaml-0.so.2.0.4
7fb8c73f8000-7fb8c75a9000 r-xp 00000000 08:04 1051853                    /usr/lib/x86_64-linux-gnu/libxml2.so.2.9.3
7fb8c75a9000-7fb8c77a8000 ---p 001b1000 08:04 1051853                    /usr/lib/x86_64-linux-gnu/libxml2.so.2.9.3
7fb8c77a8000-7fb8c77b0000 r--p 001b0000 08:04 1051853                    /usr/lib/x86_64-linux-gnu/libxml2.so.2.9.3
7fb8c77b0000-7fb8c77b2000 rw-p 001b8000 08:04 1051853                    /usr/lib/x86_64-linux-gnu/libxml2.so.2.9.3
7fb8c77b2000-7fb8c77b3000 rw-p 00000000 00:00 0 
7fb8c77b3000-7fb8c77ba000 r-xp 00000000 08:04 1048604                    /usr/lib/x86_64-linux-gnu/libffi.so.6.0.4
7fb8c77ba000-7fb8c79b9000 ---p 00007000 08:04 1048604                    /usr/lib/x86_64-linux-gnu/libffi.so.6.0.4
7fb8c79b9000-7fb8c79ba000 r--p 00006000 08:04 1048604                    /usr/lib/x86_64-linux-gnu/libffi.so.6.0.4
7fb8c79ba000-7fb8c79bb000 rw-p 00007000 08:04 1048604                    /usr/lib/x86_64-linux-gnu/libffi.so.6.0.4
7fb8c79bb000-7fb8c79d2000 r-xp 00000000 08:04 685963                     /lib/x86_64-linux-gnu/libresolv-2.23.so
7fb8c79d2000-7fb8c7bd2000 ---p 00017000 08:04 685963                     /lib/x86_64-linux-gnu/libresolv-2.23.so
7fb8c7bd2000-7fb8c7bd3000 r--p 00017000 08:04 685963                     /lib/x86_64-linux-gnu/libresolv-2.23.so
7fb8c7bd3000-7fb8c7bd4000 rw-p 00018000 08:04 685963                     /lib/x86_64-linux-gnu/libresolv-2.23.so
7fb8c7bd4000-7fb8c7bd6000 rw-p 00000000 00:00 0 
7fb8c7bd6000-7fb8c7bf5000 r-xp 00000000 08:04 664737                     /lib/x86_64-linux-gnu/libselinux.so.1
7fb8c7bf5000-7fb8c7df4000 ---p 0001f000 08:04 664737                     /lib/x86_64-linux-gnu/libselinux.so.1
7fb8c7df4000-7fb8c7df5000 r--p 0001e000 08:04 664737                     /lib/x86_64-linux-gnu/libselinux.so.1
7fb8c7df5000-7fb8c7df6000 rw-p 0001f000 08:04 664737                     /lib/x86_64-linux-gnu/libselinux.so.1
7fb8c7df6000-7fb8c7df8000 rw-p 00000000 00:00 0 
7fb8c7df8000-7fb8c7e11000 r-xp 00000000 08:04 664798                     /lib/x86_64-linux-gnu/libz.so.1.2.8
7fb8c7e11000-7fb8c8010000 ---p 00019000 08:04 664798                     /lib/x86_64-linux-gnu/libz.so.1.2.8
7fb8c8010000-7fb8c8011000 r--p 00018000 08:04 664798                     /lib/x86_64-linux-gnu/libz.so.1.2.8
7fb8c8011000-7fb8c8012000 rw-p 00019000 08:04 664798                     /lib/x86_64-linux-gnu/libz.so.1.2.8
7fb8c8012000-7fb8c8015000 r-xp 00000000 08:04 1050839                    /usr/lib/x86_64-linux-gnu/libgmodule-2.0.so.0.4800.2
7fb8c8015000-7fb8c8214000 ---p 00003000 08:04 1050839                    /usr/lib/x86_64-linux-gnu/libgmodule-2.0.so.0.4800.2
7fb8c8214000-7fb8c8215000 r--p 00002000 08:04 1050839                    /usr/lib/x86_64-linux-gnu/libgmodule-2.0.so.0.4800.2
7fb8c8215000-7fb8c8216000 rw-p 00003000 08:04 1050839                    /usr/lib/x86_64-linux-gnu/libgmodule-2.0.so.0.4800.2
7fb8c8216000-7fb8c822e000 r-xp 00000000 08:04 685951                     /lib/x86_64-linux-gnu/libpthread-2.23.so
7fb8c822e000-7fb8c842d000 ---p 00018000 08:04 685951                     /lib/x86_64-linux-gnu/libpthread-2.23.so
7fb8c842d000-7fb8c842e000 r--p 00017000 08:04 685951                     /lib/x86_64-linux-gnu/libpthread-2.23.so
7fb8c842e000-7fb8c842f000 rw-p 00018000 08:04 685951                     /lib/x86_64-linux-gnu/libpthread-2.23.so
7fb8c842f000-7fb8c8433000 rw-p 00000000 00:00 0 
7fb8c8433000-7fb8c84a1000 r-xp 00000000 08:04 659341                     /lib/x86_64-linux-gnu/libpcre.so.3.13.2
7fb8c84a1000-7fb8c86a1000 ---p 0006e000 08:04 659341                     /lib/x86_64-linux-gnu/libpcre.so.3.13.2
7fb8c86a1000-7fb8c86a2000 r--p 0006e000 08:04 659341                     /lib/x86_64-linux-gnu/libpcre.so.3.13.2
7fb8c86a2000-7fb8c86a3000 rw-p 0006f000 08:04 659341                     /lib/x86_64-linux-gnu/libpcre.so.3.13.2
7fb8c86a3000-7fb8c8863000 r-xp 00000000 08:04 685955                     /lib/x86_64-linux-gnu/libc-2.23.so
7fb8c8863000-7fb8c8a63000 ---p 001c0000 08:04 685955                     /lib/x86_64-linux-gnu/libc-2.23.so
7fb8c8a63000-7fb8c8a67000 r--p 001c0000 08:04 685955                     /lib/x86_64-linux-gnu/libc-2.23.so
7fb8c8a67000-7fb8c8a69000 rw-p 001c4000 08:04 685955                     /lib/x86_64-linux-gnu/libc-2.23.so
7fb8c8a69000-7fb8c8a6d000 rw-p 00000000 00:00 0 
7fb8c8a6d000-7fb8c8ab8000 r-xp 00000000 08:04 1053482                    /usr/lib/x86_64-linux-gnu/libappstream.so.0.9.4
7fb8c8ab8000-7fb8c8cb8000 ---p 0004b000 08:04 1053482                    /usr/lib/x86_64-linux-gnu/libappstream.so.0.9.4
7fb8c8cb8000-7fb8c8cb9000 r--p 0004b000 08:04 1053482                    /usr/lib/x86_64-linux-gnu/libappstream.so.0.9.4
7fb8c8cb9000-7fb8c8cba000 rw-p 0004c000 08:04 1053482                    /usr/lib/x86_64-linux-gnu/libappstream.so.0.9.4
7fb8c8cba000-7fb8c8d0c000 r-xp 00000000 08:04 1049588                    /usr/lib/x86_64-linux-gnu/libgobject-2.0.so.0.4800.2
7fb8c8d0c000-7fb8c8f0b000 ---p 00052000 08:04 1049588                    /usr/lib/x86_64-linux-gnu/libgobject-2.0.so.0.4800.2
7fb8c8f0b000-7fb8c8f0c000 r--p 00051000 08:04 1049588                    /usr/lib/x86_64-linux-gnu/libgobject-2.0.so.0.4800.2
7fb8c8f0c000-7fb8c8f0d000 rw-p 00052000 08:04 1049588                    /usr/lib/x86_64-linux-gnu/libgobject-2.0.so.0.4800.2
7fb8c8f0d000-7fb8c908d000 r-xp 00000000 08:04 1051163                    /usr/lib/x86_64-linux-gnu/libgio-2.0.so.0.4800.2
7fb8c908d000-7fb8c928d000 ---p 00180000 08:04 1051163                    /usr/lib/x86_64-linux-gnu/libgio-2.0.so.0.4800.2
7fb8c928d000-7fb8c9291000 r--p 00180000 08:04 1051163                    /usr/lib/x86_64-linux-gnu/libgio-2.0.so.0.4800.2
7fb8c9291000-7fb8c9293000 rw-p 00184000 08:04 1051163                    /usr/lib/x86_64-linux-gnu/libgio-2.0.so.0.4800.2
7fb8c9293000-7fb8c9295000 rw-p 00000000 00:00 0 
7fb8c9295000-7fb8c93a4000 r-xp 00000000 08:04 663966                     /lib/x86_64-linux-gnu/libglib-2.0.so.0.4800.2
7fb8c93a4000-7fb8c95a3000 ---p 0010f000 08:04 663966                     /lib/x86_64-linux-gnu/libglib-2.0.so.0.4800.2
7fb8c95a3000-7fb8c95a4000 r--p 0010e000 08:04 663966                     /lib/x86_64-linux-gnu/libglib-2.0.so.0.4800.2
7fb8c95a4000-7fb8c95a5000 rw-p 0010f000 08:04 663966                     /lib/x86_64-linux-gnu/libglib-2.0.so.0.4800.2
7fb8c95a5000-7fb8c95a6000 rw-p 00000000 00:00 0 
7fb8c95a6000-7fb8c95cc000 r-xp 00000000 08:04 685949                     /lib/x86_64-linux-gnu/ld-2.23.so
7fb8c9799000-7fb8c97a8000 rw-p 00000000 00:00 0 
7fb8c97a9000-7fb8c97aa000 rw-p 00000000 00:00 0 
7fb8c97aa000-7fb8c97ca000 r--s 00000000 08:04 5066                       /usr/share/mime/mime.cache
7fb8c97ca000-7fb8c97cb000 r--s 00000000 08:04 537501                     /home/travelshark/.local/share/mime/mime.cache
7fb8c97cb000-7fb8c97cc000 r--p 00025000 08:04 685949                     /lib/x86_64-linux-gnu/ld-2.23.so
7fb8c97cc000-7fb8c97cd000 rw-p 00026000 08:04 685949                     /lib/x86_64-linux-gnu/ld-2.23.so
7fb8c97cd000-7fb8c97ce000 rw-p 00000000 00:00 0 
7fff67cd4000-7fff67cf5000 rw-p 00000000 00:00 0                          [stack]
7fff67d75000-7fff67d77000 r--p 00000000 00:00 0                          [vvar]
7fff67d77000-7fff67d79000 r-xp 00000000 00:00 0                          [vdso]
ffffffffff600000-ffffffffff601000 r-xp 00000000 00:00 0                  [vsyscall]
Aborted (core dumped)
Reading package lists... Done
E: Problem executing scripts APT::Update::Post-Invoke-Success 'if /usr/bin/test -w /var/cache/app-info -a -e /usr/bin/appstreamcli; then appstreamcli refresh > /dev/null; fi'
E: Sub-process returned an error code



```

Happy new year guys, and any help is appreciated :D

---

### Post by Impavidus on 2020-01-15
Now we know where the error in the third screenshot of your original post comes from. Your appstreamcli is damaged, most likely the executable file is corrupt. That's a helper tool for package management. If you really want to fix this, that tool must be reinstalled. It's in the appstream package. As package management will be broken until you reinstalled it, you may have to do this using a live disk.

How was that executable file damaged? It seems that you've got damaged files all over the place. I'll stick to my original suggestion: fresh install, but keep in mind that your hard drive may be broken.

---

### Post by urubu66 on 2020-01-15
Alright, thanks for the comment.

 I doubt it's the hard drive, the system is a dual boot with Win7 and that works fine - or as fine as an early generation intel i3 on a system with plenty of Windows rot can be expected to work:P

I found out that the thing has happened to others, and there seems to be a fix (hope it's ok to link to this)

[https://bugs.launchpad.net/ubuntu/+source/appstream/+bug/1583845](https://bugs.launchpad.net/ubuntu/+source/appstream/+bug/1583845)

[https://bugs.launchpad.net/ubuntu/+source/appstream/+bug/1579712/comments/24](https://bugs.launchpad.net/ubuntu/+source/appstream/+bug/1579712/comments/24)

which, for me, would translate into

```

Remove `/usr/bin/appstreamcli`

cd /tmp && mkdir asfix
cd asfix
wget [https://launchpad.net/ubuntu/+archive/primary/+files/appstream_0.9.4-1ubuntu1_i386.deb]("https://launchpad.net/ubuntu/+archive/primary/+files/appstream_0.9.4-1ubuntu1_amd64.deb")
wget [https://launchpad.net/ubuntu/+archive/primary/+files/libappstream3_0.9.4-1ubuntu1_i386.deb]("https://launchpad.net/ubuntu/+archive/primary/+files/libappstream3_0.9.4-1ubuntu1_amd64.deb")
sudo dpkg -i *.deb


```

Would you predict this to work, or did I overlook something?

---

### Post by urubu66 on 2020-01-15
Apparently it doesn't work :(

```

travelshark@Sharkmove:~$ cd /usr
travelshark@Sharkmove:/usr$ cd bin
travelshark@Sharkmove:/usr/bin$ rm appstreamcli 
rm: remove write-protected regular file 'appstreamcli'? y
rm: cannot remove 'appstreamcli': Permission denied
travelshark@Sharkmove:/usr/bin$ sudo rm appstreamcli 
[sudo] password for travelshark: 
travelshark@Sharkmove:/usr/bin$ sudo apt-get update
Hit:1 http://archive.canonical.com/ubuntu xenial InRelease
Hit:2 http://archive.ubuntu.com/ubuntu xenial InRelease
Hit:3 http://security.ubuntu.com/ubuntu xenial-security InRelease
Reading package lists... Done                 
travelshark@Sharkmove:/usr/bin$ cd /tmp && mkdir asfix
travelshark@Sharkmove:/tmp$ cd asfix
travelshark@Sharkmove:/tmp/asfix$ wget https://launchpad.net/ubuntu/+archive/primary/+files/appstream_0.9.4-1ubuntu1_i386.deb
--2020-01-15 15:58:16--  https://launchpad.net/ubuntu/+archive/primary/+files/appstream_0.9.4-1ubuntu1_i386.deb
Resolving launchpad.net (launchpad.net)... 91.189.89.222, 91.189.89.223, 2001:67c:1560:8003::8003, ...
Connecting to launchpad.net (launchpad.net)|91.189.89.222|:443... connected.
HTTP request sent, awaiting response... 303 See Other
Location: https://launchpadlibrarian.net/259142433/appstream_0.9.4-1ubuntu1_i386.deb [following]
--2020-01-15 15:58:17--  https://launchpadlibrarian.net/259142433/appstream_0.9.4-1ubuntu1_i386.deb
Resolving launchpadlibrarian.net (launchpadlibrarian.net)... 91.189.89.229, 91.189.89.228, 2001:67c:1560:8003::8008, ...
Connecting to launchpadlibrarian.net (launchpadlibrarian.net)|91.189.89.229|:443... connected.
HTTP request sent, awaiting response... 200 OK
Length: 31054 (30K) [application/x-debian-package]
Saving to: ‘appstream_0.9.4-1ubuntu1_i386.deb’

appstream_0.9.4-1ub 100%[===================>]  30.33K  --.-KB/s    in 0.04s   

2020-01-15 15:58:17 (700 KB/s) - ‘appstream_0.9.4-1ubuntu1_i386.deb’ saved [31054/31054]

travelshark@Sharkmove:/tmp/asfix$  wget  https://launchpad.net/ubuntu/+archive/primary/+files/libappstream3_0.9.4-1ubuntu1_i386.deb
--2020-01-15 15:59:12--  https://launchpad.net/ubuntu/+archive/primary/+files/libappstream3_0.9.4-1ubuntu1_i386.deb
Resolving launchpad.net (launchpad.net)... 91.189.89.223, 91.189.89.222, 2001:67c:1560:8003::8004, ...
Connecting to launchpad.net (launchpad.net)|91.189.89.223|:443... connected.
HTTP request sent, awaiting response... 303 See Other
Location: https://launchpadlibrarian.net/259142434/libappstream3_0.9.4-1ubuntu1_i386.deb [following]
--2020-01-15 15:59:12--  https://launchpadlibrarian.net/259142434/libappstream3_0.9.4-1ubuntu1_i386.deb
Resolving launchpadlibrarian.net (launchpadlibrarian.net)... 91.189.89.228, 91.189.89.229, 2001:67c:1560:8003::8007, ...
Connecting to launchpadlibrarian.net (launchpadlibrarian.net)|91.189.89.228|:443... connected.
HTTP request sent, awaiting response... 200 OK
Length: 108760 (106K) [application/x-debian-package]
Saving to: ‘libappstream3_0.9.4-1ubuntu1_i386.deb’

libappstream3_0.9.4 100%[===================>] 106.21K  --.-KB/s    in 0.09s   

2020-01-15 15:59:13 (1.19 MB/s) - ‘libappstream3_0.9.4-1ubuntu1_i386.deb’ saved [108760/108760]

travelshark@Sharkmove:/tmp/asfix$ sudo dpkg -i *.deb
(Reading database ... 397529 files and directories currently installed.)
Preparing to unpack appstream_0.9.4-1ubuntu1_i386.deb ...
Unpacking appstream:i386 (0.9.4-1ubuntu1) over (0.9.4-1) ...
Selecting previously unselected package libappstream3:i386.
Preparing to unpack libappstream3_0.9.4-1ubuntu1_i386.deb ...
De-configuring libappstream3:amd64 (0.9.4-1) ...
Unpacking libappstream3:i386 (0.9.4-1ubuntu1) ...
dpkg: error processing package libappstream3:i386 (--install):
 package libappstream3:i386 0.9.4-1ubuntu1 cannot be configured because libappstream3:amd64 is at a different version (0.9.4-1)
dpkg: error processing package libappstream3:amd64 (--install):
 package libappstream3:amd64 0.9.4-1 cannot be configured because libappstream3:i386 is at a different version (0.9.4-1ubuntu1)
dpkg: dependency problems prevent configuration of appstream:i386:
 appstream:i386 depends on libappstream3 (>= 0.9.3); however:
  Package libappstream3:i386 is not configured yet.

dpkg: error processing package appstream:i386 (--install):
 dependency problems - leaving unconfigured
Processing triggers for man-db (2.7.5-1) ...
Processing triggers for libc-bin (2.23-0ubuntu10) ...
Errors were encountered while processing:
 libappstream3:i386
 libappstream3:amd64
 appstream:i386
travelshark@Sharkmove:/tmp/asfix$ firefox
[Parent  3916, Gecko_IOThread] WARNING: pipe error (102): Connection reset by  peer: file  /build/firefox-hE9N0Y/firefox-70.0.1+build1/ipc/chromium/src/chrome/common/ipc_channel_posix.cc,  line 358
[Parent 3916, Gecko_IOThread] WARNING: pipe error (54):  Connection reset by peer: file  /build/firefox-hE9N0Y/firefox-70.0.1+build1/ipc/chromium/src/chrome/common/ipc_channel_posix.cc,  line 358

###!!! [Parent][RunMessage] Error: Channel closing: too late to send/recv, messages will be lost

travelshark@Sharkmove:/tmp/asfix$ 

```

---

### Post by mörgæs on 2020-01-15
Windows 7 is out of support. Are you sure that you want to keep it?

---

### Post by Impavidus on 2020-01-15
It might work, but you'll need the 64-bit version. Replace the i386 in the wget commands with amd64.

Personally, I'd perform a fresh install. And the fact that that old Windows install still works doesn't guarantee that there's no physical hard drive problem in the Ubuntu partition. It uses a different part of the hard drive. But I agree, the diagnosis "broken hard drive" is a hunch, not a guarantee.

---

### Post by urubu66 on 2020-01-15
oh ok, I thought since I have intel and not AMD I should replace it. With the original command I get some progress

```

travelshark@Sharkmove:~$ wget https://launchpad.net/ubuntu/+archive/primary/+files/libappstream3_0.9.4-1ubuntu1_amd64.deb
--2020-01-15 21:04:02--  https://launchpad.net/ubuntu/+archive/primary/+files/libappstream3_0.9.4-1ubuntu1_amd64.deb
Resolving launchpad.net (launchpad.net)... 91.189.89.222, 91.189.89.223, 2001:67c:1560:8003::8004, ...
Connecting to launchpad.net (launchpad.net)|91.189.89.222|:443... connected.
HTTP request sent, awaiting response... 303 See Other
Location: https://launchpadlibrarian.net/259142419/libappstream3_0.9.4-1ubuntu1_amd64.deb [following]
--2020-01-15 21:04:02--  https://launchpadlibrarian.net/259142419/libappstream3_0.9.4-1ubuntu1_amd64.deb
Resolving launchpadlibrarian.net (launchpadlibrarian.net)... 91.189.89.228, 91.189.89.229, 2001:67c:1560:8003::8007, ...
Connecting to launchpadlibrarian.net (launchpadlibrarian.net)|91.189.89.228|:443... connected.
HTTP request sent, awaiting response... 200 OK
Length: 98708 (96K) [application/x-debian-package]
Saving to: ‘libappstream3_0.9.4-1ubuntu1_amd64.deb’

libappstream3_0.9.4 100%[===================>]  96.39K  --.-KB/s    in 0.09s   

2020-01-15 21:04:03 (1022 KB/s) - ‘libappstream3_0.9.4-1ubuntu1_amd64.deb’ saved [98708/98708]

travelshark@Sharkmove:~$ wget https://launchpad.net/ubuntu/+archive/primary/+files/appstream_0.9.4-1ubuntu1_amd64.deb
--2020-01-15 21:04:22--  https://launchpad.net/ubuntu/+archive/primary/+files/appstream_0.9.4-1ubuntu1_amd64.deb
Resolving launchpad.net (launchpad.net)... 91.189.89.223, 91.189.89.222, 2001:67c:1560:8003::8003, ...
Connecting to launchpad.net (launchpad.net)|91.189.89.223|:443... connected.
HTTP request sent, awaiting response... 303 See Other
Location: https://launchpadlibrarian.net/259142418/appstream_0.9.4-1ubuntu1_amd64.deb [following]
--2020-01-15 21:04:22--  https://launchpadlibrarian.net/259142418/appstream_0.9.4-1ubuntu1_amd64.deb
Resolving launchpadlibrarian.net (launchpadlibrarian.net)... 91.189.89.229, 91.189.89.228, 2001:67c:1560:8003::8008, ...
Connecting to launchpadlibrarian.net (launchpadlibrarian.net)|91.189.89.229|:443... connected.
HTTP request sent, awaiting response... 200 OK
Length: 30134 (29K) [application/x-debian-package]
Saving to: ‘appstream_0.9.4-1ubuntu1_amd64.deb’

appstream_0.9.4-1ub 100%[===================>]  29.43K  --.-KB/s    in 0.03s   

2020-01-15 21:04:23 (868 KB/s) - ‘appstream_0.9.4-1ubuntu1_amd64.deb’ saved [30134/30134]

travelshark@Sharkmove:~$ sudo dpkg -i *.deb
[sudo] password for travelshark: 
(Reading database ... 397531 files and directories currently installed.)
Preparing to unpack appstream_0.9.4-1ubuntu1_amd64.deb ...
Unpacking appstream (0.9.4-1ubuntu1) over (0.9.4-1ubuntu1) ...
dpkg: warning: downgrading apt from 1.2.29ubuntu0.1 to 1.0.1ubuntu2
Preparing to unpack apt_1.0.1ubuntu2_amd64.deb ...
Unpacking apt (1.0.1ubuntu2) over (1.2.29ubuntu0.1) ...
Preparing to unpack libappstream3_0.9.4-1ubuntu1_amd64.deb ...
Unpacking libappstream3:amd64 (0.9.4-1ubuntu1) over (0.9.4-1) ...
Selecting previously unselected package teamviewer.
Preparing to unpack teamviewer_amd64.deb ...
Unpacking teamviewer (14.4.2669) ...
dpkg: dependency problems prevent configuration of apt:
 libapt-pkg5.0:amd64 (1.2.29ubuntu0.1) breaks apt (<< 1.1~exp14) and is installed.
  Version of apt to be configured is 1.0.1ubuntu2.

dpkg: error processing package apt (--install):
 dependency problems - leaving unconfigured
Setting up libappstream3:amd64 (0.9.4-1ubuntu1) ...
dpkg: dependency problems prevent configuration of teamviewer:
 teamviewer depends on libqt5webkit5 (>= 5.5) | qt56-teamviewer; however:
  Package libqt5webkit5 is not installed.
  Package qt56-teamviewer is not installed.
 teamviewer depends on libqt5x11extras5 (>= 5.5) | qt56-teamviewer; however:
  Package libqt5x11extras5 is not installed.
  Package qt56-teamviewer is not installed.
 teamviewer depends on qml-module-qtquick-controls (>= 5.5) | qt56-teamviewer; however:
  Package qml-module-qtquick-controls is not installed.
  Package qt56-teamviewer is not installed.
 teamviewer depends on qml-module-qtquick-dialogs (>= 5.5) | qt56-teamviewer; however:
  Package qml-module-qtquick-dialogs is not installed.
  Package qt56-teamviewer is not installed.

dpkg: error processing package teamviewer (--install):
 dependency problems - leaving unconfigured
Setting up appstream (0.9.4-1ubuntu1) ...
AppStream cache update completed, but some metadata was ignored due to errors.
Processing triggers for man-db (2.7.5-1) ...
Processing triggers for libc-bin (2.23-0ubuntu10) ...
Processing triggers for gnome-menus (3.13.3-6ubuntu3) ...
Processing triggers for desktop-file-utils (0.22-1ubuntu5) ...
Processing triggers for mime-support (3.59ubuntu1) ...
Processing triggers for bamfdaemon (0.5.3~bzr0+16.04.20160415-0ubuntu1) ...
Rebuilding /usr/share/applications/bamf-2.index...
Processing triggers for hicolor-icon-theme (0.15-0ubuntu1) ...
Errors were encountered while processing:
 apt
 teamviewer
travelshark@Sharkmove:~$ sudo apt-get update
Hit http://archive.ubuntu.com xenial InRelease
Get:1 http://security.ubuntu.com xenial-security InRelease [109 kB]            
Hit http://archive.canonical.com xenial InRelease                              
Get:2 http://archive.ubuntu.com xenial/main amd64 Packages [1,201 kB]          
Get:3 http://security.ubuntu.com xenial-security/main amd64 Packages [806 kB]  
Hit http://archive.canonical.com xenial/partner amd64 Packages                 
Hit http://archive.canonical.com xenial/partner i386 Packages                  
Get:4 http://archive.canonical.com xenial/partner Translation-en [1,672 B]     
Get:5 http://security.ubuntu.com xenial-security/universe amd64 Packages [467 kB]
Hit http://archive.ubuntu.com xenial/universe amd64 Packages                   
Get:6 http://security.ubuntu.com xenial-security/main i386 Packages [627 kB]   
Get:7 http://archive.ubuntu.com xenial/main i386 Packages [1,196 kB]           
Hit http://archive.ubuntu.com xenial/universe i386 Packages                    
Get:8 http://archive.ubuntu.com xenial/main Translation-en [568 kB]
Get:9 http://security.ubuntu.com xenial-security/universe i386 Packages [402 kB]
Get:10 http://security.ubuntu.com xenial-security/main Translation-en [308 kB] 
Get:11 http://archive.ubuntu.com xenial/universe Translation-en [4,354 kB]     
Get:12 http://security.ubuntu.com xenial-security/universe Translation-en [192 kB]
Fetched 10.2 MB in 11s (877 kB/s)                                              
AppStream cache update completed, but some metadata was ignored due to errors.
Reading package lists... Done
N: Ignoring file '50unattended-upgrades.ucf-old' in directory '/etc/apt/apt.conf.d/' as it has an invalid filename extension
W: Unknown Multi-Arch type 'no' for package 'compiz-core'
W: Unknown Multi-Arch type 'no' for package 'compiz-gnome'
W: Unknown Multi-Arch type 'no' for package 'libxapian-dev'
W: Ignoring Provides line with DepCompareOp for package python-cffi-backend-api-max
W: Ignoring Provides line with DepCompareOp for package python-cffi-backend-api-min
W: Ignoring Provides line with DepCompareOp for package python3-cffi-backend-api-max
W: Ignoring Provides line with DepCompareOp for package python3-cffi-backend-api-min
W: Unknown Multi-Arch type 'no' for package 'kwin'
W: Unknown Multi-Arch type 'no' for package 'kwin-dev'
W: Unknown Multi-Arch type 'no' for package 'kwin-wayland'
W: Unknown Multi-Arch type 'no' for package 'kwin-x11'
W: Unknown Multi-Arch type 'no' for package 'libkf5sysguard-dev'
W: Ignoring Provides line with DepCompareOp for package php-psr-http-message-implementation
W: Ignoring Provides line with DepCompareOp for package php-psr-log-implementation
W: Ignoring Provides line with DepCompareOp for package php-seclib
W: Ignoring Provides line with DepCompareOp for package php-sabre-http
W: Ignoring Provides line with DepCompareOp for package php-math-biginteger
W: Ignoring Provides line with DepCompareOp for package pypy-cffi
W: Ignoring Provides line with DepCompareOp for package pypy-cffi-backend-api-max
W: Ignoring Provides line with DepCompareOp for package pypy-cffi-backend-api-min
W: Unknown Multi-Arch type 'no' for package 'compiz-core'
W: Unknown Multi-Arch type 'no' for package 'compiz-gnome'
W: Unknown Multi-Arch type 'no' for package 'libxapian-dev'
W: Ignoring Provides line with DepCompareOp for package python-cffi-backend-api-max
W: Ignoring Provides line with DepCompareOp for package python-cffi-backend-api-min
W: Ignoring Provides line with DepCompareOp for package python3-cffi-backend-api-max
W: Ignoring Provides line with DepCompareOp for package python3-cffi-backend-api-min
W: Unknown Multi-Arch type 'no' for package 'kwin-dev'
W: Unknown Multi-Arch type 'no' for package 'kwin-wayland'
W: Unknown Multi-Arch type 'no' for package 'kwin-x11'
W: Unknown Multi-Arch type 'no' for package 'libkf5sysguard-dev'
W: Ignoring Provides line with DepCompareOp for package pypy-cffi
W: Ignoring Provides line with DepCompareOp for package pypy-cffi-backend-api-max
W: Ignoring Provides line with DepCompareOp for package pypy-cffi-backend-api-min
W: You may want to run apt-get update to correct these problems
travelshark@Sharkmove:~$ 


```

---

### Post by urubu66 on 2020-01-15
Making some progress, uninstalled teamviewer and some other programs, on the next boot got a popup about a software upgrade, did that, rebooted again. 

Still have most of the original problems of no taskbar, no title bar on programs, ctrl alt t doesn't work, I can only start programs from the terminal, I can only start one program at a time, and to boot I get a black screen with some text that I have then to CTRL ALT F2, login and use startx to get to the gui. But I can do updates and install and remove programs, so I'll get there:)

Recently received this internal error report
```

atm getting a
"Sorry, Ubuntu 16.04 has experienced an internal error.

ExecutablePath    
    /sbin/plymouthd
Package
    plymouth 0.9.2-3ubuntu13


```

I'm guessing that might be another big step? any idea how to fix this one?

---

### Post by Impavidus on 2020-01-15
The amd64 instruction set for processors was introduced by AMD, hence the name, but the same works on Intel CPUs. This time they though about making things compatible.

I see that your sudo dpkg -i *.deb tried to install an old version of apt. Maybe you somehow got an old .deb for apt in the current directory? In any case, not a good idea. Installation failed, but it seems apt still works and you managed to install some upgrades. That should have brought apt back the the right version.

---

### Post by urubu66 on 2020-01-18
I was thinking, would a dist upgrade to 18.04 maybe be a good idea? At least it would give me a different set problems which are searchable online and maybe one of them would solve it?

---

### Post by mörgæs on 2020-01-18
No, a clean install of 19.10 would. It could relieve you from a wrecked Ubuntu and from Windows 7. 

Upgrading itself is a risky project and many posts in the forum deal with upgrades going haywire.

---

### Post by Impavidus on 2020-01-18
On a clean system, release upgrades work fine (usually). But on a broken system, release upgrades make things worse. As stated above, try a fresh install. If that doesn't work, nothing works.

---

