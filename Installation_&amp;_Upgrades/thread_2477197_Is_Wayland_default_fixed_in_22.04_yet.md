---
title: "Is Wayland default fixed in 22.04 yet?"
date: 2022-07-17
forum: Installation &amp; Upgrades
---

### Post by jgwphd on 2022-07-17
I just installed 22.04 and did all the updates and upgrades I could  find, but my machine (Dell desktop with NVIDIA card) comes up in X11  with no option (or gear on the log in / password screen) for Wayland.  And, my understanding is Wayland is supposed to be the default. I have  been looking at numerous posts bug reports (lots of duplicates) about  this (FOR EXAMPLE  [https://ubuntuforums.org/showthread.php?t=2473861&page=2&highlight=1968929](https://ubuntuforums.org/showthread.php?t=2473861&page=2&highlight=1968929))  and I can't determine if this bug is fixed? ...all I know is I still  have it? The situation is "explained???" in: bug#  [https://bugs.launchpad.net/ubuntu/jammy/+source/gdm3/+bug/1968929](https://bugs.launchpad.net/ubuntu/jammy/+source/gdm3/+bug/1968929)  Also  the last post on the activity log (7-5) seems to be saying it is still a  "bug"   ...[https://bugs.launchpad.net/ubuntu/jammy/+source/gdm3/+bug/1968929/+activity](https://bugs.launchpad.net/ubuntu/jammy/+source/gdm3/+bug/1968929/+activity) Can  someone PLEASE tell me if this bug is fixed or not?....maybe I am  missing something!  And if it is fixed where can I find the information  to get my system repaired? 

BTW, in one bug report someone  claimed that I could delete/rename this rules file "61-gdm.rules" or if I  comment out some of the instructions I might be able to get Wayland  back. Any guidance is appreciated. Many Thanks for your assistance!

---

### Post by ubfan1 on 2022-07-17
"This bug was fixed in the package gdm3 - 42.0-1ubuntu7" comment #46 on the bug, so do you have that version installed?   I've made no changes to my 22.04/Nvidia 515, laptop. Wayland is offered, but is not the default.  Seems to work just fine for anything I do.

---

### Post by jgwphd on 2022-07-19
I checked Synaptic and I have the package "gdm3 - 42.0-1ubuntu" installed. I reinstalled it again for more fun :) and I still have the problem.....No Wayland! ...BTW, A question: In Synaptic do I need to do a "complete removal" first and then reinstall it?

I have a Dell XPS 8930** desktop machine **with i7-9700 CPU with 16GB of memory with an **NVIDIA GeForce GTX 1650/PCIe/SSE2 / NVIDIA Corporation TU117**

If you read the comments past #46 on the bug report they all seem to be saying it is **not **fixed. comment #48, 49, 50 followed by other discussion comments about "phased rollout" and possible issues (comment #59). The full activity log says **"bug" on last entry at 2022-07-05**. If this is supposed to be fixed I am totally confused!?!? 

I also went to the terminal and issued the following commands (comment #51):
     1. sudo apt update
 2. sudo apt full-upgrade
 3. Reboot

                  Still NO Wayland

Is there someplace where I can get a package that works?  Do I need to point to another repository (I am at the "Server for the United States"?  ....Any assistance or guidance is appreciated!!

An update: Followed the instructions at: [https://linuxconfig.org/how-to-enable-disable-wayland-on-ubuntu-22-04-desktop](https://linuxconfig.org/how-to-enable-disable-wayland-on-ubuntu-22-04-desktop) and changed the /etc/gdm3/custom.conf file by uncommenting the line #WaylandEnable=false and set it to true "WaylandEnable=true" then rebooted ....still **NO** wayland

---

### Post by ubfan1 on 2022-07-19
Anything in /var/log/gdm3 log files?  Which Nvidia driver are you using (515 is the one enabling Wayland)?  I did nothing to a fresh Ubuntu 22.04 install, added the Nvidia 515, and got the Wayland choice -- no rules changes or config file editing.

---

### Post by jgwphd on 2022-07-19
Software and updates indicates I am using nvidia-driver-470. There is a selection of drivers here (8 plus an open source driver). The nvidia-driver-515 (proprietary, tested) was at the top of the list which I am going to install and see if that works. I looked at the config file and see all the test around Nvidia and system specifics. BTW, I have two 515 drivers one is nvidia-driver-515 (proprietary, tested) and the other is nvidia-driver-515-server (proprietary). I also have an open source driver listed at the end. I will us the nvidia-driver-515 (proprietary, tested) not the other two unless you tell me differently.

UPDATE: No log file found in the gdm3 directory (Do I have to enable the log file or will one be created when an error occurs?). Updated the driver to nvidia-driver-515 (proprietary, tested) and rebooted. Still **NO** Wayland!

---

### Post by ubfan1 on 2022-07-19
I assume the log file would be created if any errors occur.  You got the right 515 driver, so now the trick is to ensure you undo anything you did earlier (deleting rules, editing config files, ...) although the EnableWayland=true should be OK, that is the default, and I have left the line as a comment.

---

### Post by jgwphd on 2022-07-19
After I try something I** always** put any changes back (that didn't work), so I don't confuse the problem or create others. Everything is back to where it was from the upgrade from 21.10 to 22.04 except installing the new nvidia-driver-515 (proprietary, tested) driver. BTW, I never changed the rules or config files but reading the comments were useful for a better understanding. The only change I tried was un-commenting the line #WaylandEnable=false and set it to true "WaylandEnable=true". BUT I put that back to being commented and =false again. What is next?

BTW, This seems to be saying that this is still a bug: [https://ubuntuforums.org/printthread.php?t=2473861&pp=10&page=2](https://ubuntuforums.org/printthread.php?t=2473861&pp=10&page=2) ....am I missing something? Next to last comment says:

"gdm3 has been patched, so Wayland should be available again to those of us who don't use nVidia graphics.

[https://bugs.launchpad.net/ubuntu/+s...43/comments/31]("https://bugs.launchpad.net/ubuntu/+source/gdm3/+bug/1969243/comments/31")

I'm afraid it's a mixed blessing: while Intel and AMD graphics can use  Wayland again, nVidia users will still have to wait&#8212;hopefully not for  too long."

---

### Post by ubfan1 on 2022-07-20
Wayland definitely is available for my U22.04/Nvidia 515 laptop, but just not the default (first choice). The choices read 1)ubuntu, and 2ubuntu on wayland when using the Nvidia 515 driver.  When using the nouveau driver, the choices read 1)ubuntu and 2)ubuntu on xorg, so the default is Wayland.  The wayland choice works fine for whatever I try, but I mostly still just use xorg.

---

### Post by jgwphd on 2022-07-20
I decided to try a different driver and picked the open source one (I usually try to stay away from Nvidia. It always seems to be a source of complexity/problems - I was thinking of just yanking the card out of my machine and putting it in the trash but I run dual screens and wanted to use the Nvidia for another video plug in). I installed the **open source nouveau driver and the system came up in Wayland **(according to the about information in settings). The gear was shown on the log in screen as 1)ubuntu and 2)ubuntu on xorg. Ok I was thinking I could use the nouveau driver if it works for everything else. This is crazy that the Nvidia drivers don't work with Wayland yet the open source one does with Wayland **"BUT"** the screen plugged into the Nvidia card is all color distorted under xorg (mostly bright yellow, white and pink) but works fine with Wayland. I am going to do more testing and see if there are any other issues with Wayland (BTW, skype screen sharing only works in Xorg and with this driver using Wayland that capability is lost). This whole situation seems to be a series of tradeoffs. I will reinstall the 515 driver and use Xorg for now. Do you have any other suggestions or ideas. As far as I am concerned this Wayland using Nvidia is still broken. I am beginning to think it may be a Nvidia card hardware issue or the chip set used in this particular Nvidia card. Do you know a way to check that out? The nvidia card is: **NVIDIA GeForce GTX 1650/PCIe/SSE2 / NVIDIA Corporation TU117 **from the settings about information

---

### Post by jgwphd on 2022-07-31
Unless someone has any suggestions than I am concluding that Wayland using Nvidia is still broken (at least for my hardware: **NVIDIA GeForce GTX 1650/PCIe/SSE2 / NVIDIA Corporation TU117 **from the settings about information). I feel burned again by Nvidia and would recommend that people stay away from Nvidia. My experience over the years is that Nvidia always seems to be a source of complexity/problems and this is just another example.

---

### Post by ubfan1 on 2022-07-31
How about any necessary wayland packages?  The following are on my system:
ii  libnvidia-egl-wayland1:amd64               1:1.1.9-1.1                             amd64        Wayland EGL External Platform library -- shared library
ii  libwayland-client0:amd64                   1.20.0-1                                amd64        wayland compositor infrastructure - client library
ii  libwayland-client0:i386                    1.20.0-1                                i386         wayland compositor infrastructure - client library
ii  libwayland-cursor0:amd64                   1.20.0-1                                amd64        wayland compositor infrastructure - cursor library
ii  libwayland-cursor0:i386                    1.20.0-1                                i386         wayland compositor infrastructure - cursor library
ii  libwayland-egl1:amd64                      1.20.0-1                                amd64        wayland compositor infrastructure - EGL library
ii  libwayland-egl1:i386                       1.20.0-1                                i386         wayland compositor infrastructure - EGL library
ii  libwayland-server0:amd64                   1.20.0-1                                amd64        wayland compositor infrastructure - server library
ii  libwayland-server0:i386                    1.20.0-1                                i386         wayland compositor infrastructure - server library
ii  xwayland                                   2:22.1.1-1ubuntu0.1                     amd64        X server for running X clients under Wayland

---

### Post by jgwphd on 2022-08-02
I am away from that machine for a few days. I'll check using Synaptic when I get back. BTW, which driver do you suggest I run? The "515" one? .

---

### Post by ubfan1 on 2022-08-02
Definitely the Nvidia 515 driver, that is the one which allowed Wayland to run again with the Nvidia drivers.

---

### Post by bingodingo on 2022-08-07
This might be muddying the waters (I haven't followed the detail of announcements), but I'm wondering if Wayland is, generally speaking, *not* the default if you have an Nvidia driver:
With version 22.04, Ubuntu switches to the Wayland display server by  default once again. However, it will be limited to systems without  Nvidia graphics cards at the time of release due to some known issues. ([https://itsfoss.com/ubuntu-22-04-release-features/](https://itsfoss.com/ubuntu-22-04-release-features/)).

My 2 cents: I think there's too much fluffing around with presentation / packaging like this. 
I would rather a slower release cycle, with rock solid performance, and give me a newer kernel rather than putting some much time / money into presentation.

---

### Post by ubfan1 on 2022-08-07
The default video depends on the driver, as well as the graphics card.  Nvidia hardware running wit the nouveau driver defaults to Wayland, with the Nvidia 515 driver, the default is xorg, but with a Wayland option. Previous Nvidia drivers don't offer a choice, they run xorg.  Several releases ago, the setup was to switch on demand, but that was dropped.

---

### Post by jgwphd on 2022-08-21
I have all these modules showing up in Synaptic, except none of then have the "amd64" designation.

---

### Post by jgwphd on 2022-08-21
> **ubfan1 said:**
> How about any necessary wayland packages?  The following are on my system:
ii  libnvidia-egl-wayland1:amd64               1:1.1.9-1.1                             amd64        Wayland EGL External Platform library -- shared library
ii  libwayland-client0:amd64                   1.20.0-1                                amd64        wayland compositor infrastructure - client library
ii  libwayland-client0:i386                    1.20.0-1                                i386         wayland compositor infrastructure - client library
ii  libwayland-cursor0:amd64                   1.20.0-1                                amd64        wayland compositor infrastructure - cursor library
ii  libwayland-cursor0:i386                    1.20.0-1                                i386         wayland compositor infrastructure - cursor library
ii  libwayland-egl1:amd64                      1.20.0-1                                amd64        wayland compositor infrastructure - EGL library
ii  libwayland-egl1:i386                       1.20.0-1                                i386         wayland compositor infrastructure - EGL library
ii  libwayland-server0:amd64                   1.20.0-1                                amd64        wayland compositor infrastructure - server library
ii  libwayland-server0:i386                    1.20.0-1                                i386         wayland compositor infrastructure - server library
ii  xwayland                                   2:22.1.1-1ubuntu0.1                     amd64        X server for running X clients under Wayland

I have all these modules except they don't show up with the "amd64" designation. When I returned after being out for two weeks ...now the system, after maintenance,will only boot with Wayland and one of the displays (I am running dual displays) comes up for a second during boot but blanks out and is unusable after that. When I select "the gear" with Ubuntu under xorg and type in my password the system "thinks" for about 10 seconds and then goes back to the same password screen. I can't get past this with selecting xorg. With Grub I booted with a prior kernel and it worked again with xorg and dual displays (using nvidia 515 driver). Nvidia is such a piece of "(fill in your favorite pejorative)".

---

### Post by ubfan1 on 2022-08-21
With a fresh install of Ubuntu 22.04 you should be running a 64 bit system, not sure how the 64 bit amd libwayland packages were missed.  Check with ldd /bin/Xwayland to see what version shared libraries the Xwayland program is expecting.

---

### Post by jgwphd on 2022-08-21
@ubfan1 Why the two "ii" in front of each library module listed in your reply? Is that part of the library module name??? Can you expand on how to do this "Check with ldd /bin/Xwayland to see what version shared libraries the Xwayland program is expecting."? thanks

BTW, did you see that when I returned after being out for two weeks ...now the system, after  maintenance,will only boot with Wayland and one of the displays (I am  running dual displays) comes up for a second during boot but blanks out  and is unusable after that. When I select "the gear" with Ubuntu under  xorg and type in my password the system "thinks" for about 10 seconds  and then goes back to the same password screen. I can't get past this  with selecting xorg. With Grub I booted with a prior kernel and it  worked again with xorg and dual displays (using nvidia 515 driver).

---

### Post by jgwphd on 2022-08-21
Command output from the terminal:

$ ldd /bin/Xwayland 
    linux-vdso.so.1 (0x00007ffda29f9000)
    libpixman-1.so.0 => /lib/x86_64-linux-gnu/libpixman-1.so.0 (0x00007fa444305000)
    libXfont2.so.2 => /lib/x86_64-linux-gnu/libXfont2.so.2 (0x00007fa4442d7000)
    libXdmcp.so.6 => /lib/x86_64-linux-gnu/libXdmcp.so.6 (0x00007fa4442cf000)
    libwayland-client.so.0 => /lib/x86_64-linux-gnu/libwayland-client.so.0 (0x00007fa4442bf000)
    libxcvt.so.0 => /lib/x86_64-linux-gnu/libxcvt.so.0 (0x00007fa4442ba000)
    libdrm.so.2 => /lib/x86_64-linux-gnu/libdrm.so.2 (0x00007fa4442a4000)
    libepoxy.so.0 => /lib/x86_64-linux-gnu/libepoxy.so.0 (0x00007fa44416d000)
    libgbm.so.1 => /lib/x86_64-linux-gnu/libgbm.so.1 (0x00007fa44415c000)
    libm.so.6 => /lib/x86_64-linux-gnu/libm.so.6 (0x00007fa444075000)
    libxshmfence.so.1 => /lib/x86_64-linux-gnu/libxshmfence.so.1 (0x00007fa444070000)
    libgcrypt.so.20 => /lib/x86_64-linux-gnu/libgcrypt.so.20 (0x00007fa443f32000)
    libtirpc.so.3 => /lib/x86_64-linux-gnu/libtirpc.so.3 (0x00007fa443f04000)
    libXau.so.6 => /lib/x86_64-linux-gnu/libXau.so.6 (0x00007fa443efc000)
    libGL.so.1 => /lib/x86_64-linux-gnu/libGL.so.1 (0x00007fa443e75000)
    libc.so.6 => /lib/x86_64-linux-gnu/libc.so.6 (0x00007fa443c4d000)
    /lib64/ld-linux-x86-64.so.2 (0x00007fa444624000)
    libz.so.1 => /lib/x86_64-linux-gnu/libz.so.1 (0x00007fa443c31000)
    libbz2.so.1.0 => /lib/x86_64-linux-gnu/libbz2.so.1.0 (0x00007fa443c1e000)
    libfontenc.so.1 => /lib/x86_64-linux-gnu/libfontenc.so.1 (0x00007fa443c14000)
    libfreetype.so.6 => /lib/x86_64-linux-gnu/libfreetype.so.6 (0x00007fa443b4a000)
    libbsd.so.0 => /lib/x86_64-linux-gnu/libbsd.so.0 (0x00007fa443b32000)
    libffi.so.8 => /lib/x86_64-linux-gnu/libffi.so.8 (0x00007fa443b25000)
    libwayland-server.so.0 => /lib/x86_64-linux-gnu/libwayland-server.so.0 (0x00007fa443b0f000)
    libexpat.so.1 => /lib/x86_64-linux-gnu/libexpat.so.1 (0x00007fa443ade000)
    libstdc++.so.6 => /lib/x86_64-linux-gnu/libstdc++.so.6 (0x00007fa4438b0000)
    libgpg-error.so.0 => /lib/x86_64-linux-gnu/libgpg-error.so.0 (0x00007fa44388a000)
    libgssapi_krb5.so.2 => /lib/x86_64-linux-gnu/libgssapi_krb5.so.2 (0x00007fa443836000)
    libGLdispatch.so.0 => /lib/x86_64-linux-gnu/libGLdispatch.so.0 (0x00007fa44377e000)
    libGLX.so.0 => /lib/x86_64-linux-gnu/libGLX.so.0 (0x00007fa44374a000)
    libpng16.so.16 => /lib/x86_64-linux-gnu/libpng16.so.16 (0x00007fa44370f000)
    libbrotlidec.so.1 => /lib/x86_64-linux-gnu/libbrotlidec.so.1 (0x00007fa4436ff000)
    libmd.so.0 => /lib/x86_64-linux-gnu/libmd.so.0 (0x00007fa4436f2000)
    libgcc_s.so.1 => /lib/x86_64-linux-gnu/libgcc_s.so.1 (0x00007fa4436d2000)
    libkrb5.so.3 => /lib/x86_64-linux-gnu/libkrb5.so.3 (0x00007fa443607000)
    libk5crypto.so.3 => /lib/x86_64-linux-gnu/libk5crypto.so.3 (0x00007fa4435d8000)
    libcom_err.so.2 => /lib/x86_64-linux-gnu/libcom_err.so.2 (0x00007fa4435d0000)
    libkrb5support.so.0 => /lib/x86_64-linux-gnu/libkrb5support.so.0 (0x00007fa4435c2000)
    libX11.so.6 => /lib/x86_64-linux-gnu/libX11.so.6 (0x00007fa443482000)
    libbrotlicommon.so.1 => /lib/x86_64-linux-gnu/libbrotlicommon.so.1 (0x00007fa44345f000)
    libkeyutils.so.1 => /lib/x86_64-linux-gnu/libkeyutils.so.1 (0x00007fa443458000)
    libresolv.so.2 => /lib/x86_64-linux-gnu/libresolv.so.2 (0x00007fa443442000)
    libxcb.so.1 => /lib/x86_64-linux-gnu/libxcb.so.1 (0x00007fa443418000

---

### Post by ubfan1 on 2022-08-22
So the ldd output definitely shows that Xwayland needs the amd64 libraries, not the i386.  The dpkg -l output, uses letter codes for state of the package, see the dpkg-query man page, but ii is the code for fully installed.  Partially removed packages typically have "rc", and those can sometimes cause problems.  I suppose you could try the xwayland install again and see if the amd64 libraries get picked up, or if that fails, individually install the libraries (append :amd64 to the package name if necessary).

---

### Post by jgwphd on 2022-08-22
Ok, so it is now clear to me that ALL the strange behavior is due to having the wrong libraries. I have no idea how that happened??? Leaving that aside, how should I go about fixing this? Can you please explain how I do an Xwayland install? ...using synaptic? ....or something else such as sending me some terminal commands for me to copy and utilize. Or should I just kill the system and do a fresh install of 22.04. If I can fix it with something that I can trust like synaptic, that would be my preference. Many thanks for all your assistance!!!

---

### Post by ubfan1 on 2022-08-22
sudo apt-get install xwayland  should get all the libs, i386 and amd64.  If for some reason that doesn't work, sudo apt-get install libnvidia-egl-wayland1:amd64 for all of them.  Of course, if you don't know how that happened in the first place, the question is what other libraries are missing?  If any more turn up, maybe a fresh install would be best.

---

### Post by jgwphd on 2022-08-23
Ok, I'll give sudo apt-get install xwayland try. Thanks

---

### Post by jgwphd on 2022-08-23
Neither suggestion worked to get the amd64 versions (correct libraries)

**~/Desktop$** sudo apt-get install xwayland 
[sudo] password for ___: 
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
xwayland is already the newest version (2:22.1.1-1ubuntu0.1).
xwayland set to manually installed.
0 upgraded, 0 newly installed, 0 to remove and 129 not upgraded.
**~/Desktop$** sudo apt-get install libnvidia-egl-wayland1:amd64
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
libnvidia-egl-wayland1 is already the newest version (1:1.1.9-1.1).
libnvidia-egl-wayland1 set to manually installed.
0 upgraded, 0 newly installed, 0 to remove and 129 not upgraded.
[B]~/Desktop$ 

[/B]Do you have any other suggestions?

---

### Post by jgwphd on 2022-08-24
Do you have any other suggestions?

---

### Post by ubfan1 on 2022-08-24
Check again with dpkg -l |grep -i wayland   and ensure you don't already have te 64 bit versions, and since the installs seem to think nothing needs to be done, sudo apt-get purge the i386 libs, then try the 64 bit installs again.

---

### Post by pbear42 on 2022-08-24
> **jgwphd said:**
> Or should I just kill the system and do a fresh install of 22.04.
Frankly, that was my reaction when I saw **ubfan1's** second post (July 19th).  Stuff like this is why I always do a fresh install for major upgrades.  The trick is to have detailed notes on how to set up the system.  All the settings you modify (and where they will be found), all the apps you install, and all the app settings you modify.  Some folks put a shortcut to the doc on their desktop, so it can be updated easily.  IMHO, detailed notes are more useful than a system image.

---

### Post by jgwphd on 2022-08-25
I executed the command (below) and only one "i386" shows up for client0 with a duplicate marked "amd64". All have the "ii" marking 

$ dpkg -l |grep -i wayland
ii  kwayland-data                               4:5.92.0-0ubuntu1                            all          Qt library wrapper for Wayland libraries - data files
ii  kwayland-integration:amd64                  4:5.24.4-0ubuntu1                            amd64        kwayland runtime integration plugins
ii  libkf5waylandclient5:amd64                  4:5.92.0-0ubuntu1                            amd64        Qt library wrapper for Wayland libraries
ii  libnvidia-egl-wayland1:amd64                1:1.1.9-1.1                                  amd64        Wayland EGL External Platform library -- shared library
ii  libqt5waylandclient5:amd64                  5.15.3-1                                     amd64        QtWayland client library
ii  libqt5waylandcompositor5:amd64              5.15.3-1                                     amd64        QtWayland compositor library
ii  libva-wayland2:amd64                        2.14.0-1                                     amd64        Video Acceleration (VA) API for Linux -- Wayland runtime
ii  libwayland-client0:amd64                    1.20.0-1                                     amd64        wayland compositor infrastructure - client library
ii  libwayland-client0:i386                     1.20.0-1                                     i386         wayland compositor infrastructure - client library
ii  libwayland-cursor0:amd64                    1.20.0-1                                     amd64        wayland compositor infrastructure - cursor library
ii  libwayland-egl1:amd64                       1.20.0-1                                     amd64        wayland compositor infrastructure - EGL library
ii  libwayland-server0:amd64                    1.20.0-1                                     amd64        wayland compositor infrastructure - server library
ii  qtwayland5:amd64                            5.15.3-1                                     amd64        QtWayland platform plugin
ii  xwayland                                    2:22.1.1-1ubuntu0.1                          amd64        X server for running X clients under Wayland
bruce@bruce-XPS-8930:~/Desktop$

---

### Post by jgwphd on 2022-08-26
Based on the information in my prior post should I use Synaptic to purge the wayland i386 compositor infrastructure client library; the line in the listing in my prior post with "ii libwayland-client0:i386                     1.20.0-1                                      i386         wayland compositor infrastructure -  client library" or is it needed for something else. Any advice welcome. Thanks!

---

### Post by ubfan1 on 2022-08-26
The only amd64 exclusive wayland library I have is  libnvidia-egl-wayland1, all the others are both amd64 and i386 (but I don't have the qt... libs).  I shouldn't hurt to leave them they are in a different location from the amd64 libs.

---

### Post by jgwphd on 2022-08-26
So, I guess I am screwed. You seem to be saying that there is no way to fix this situation. I tend to agree with pbear42. It seems all the weird issues I've ever had are always associated with an upgrade. Never a fresh install. Also, my recollection is most of then are with NVIDIA present. My conclusion is never do upgrades if you have NVIDIA in your system. Better yet avoid NVIDIA. It is not worth the extra expense and complexity hassle. My 2 cents from experience.

---

### Post by kurt18947 on 2022-08-27
> **jgwphd said:**
> So, I guess I am screwed. You seem to be saying that there is no way to fix this situation. I tend to agree with pbear42. It seems all the weird issues I've ever had are always associated with an upgrade. Never a fresh install. Also, my recollection is most of then are with NVIDIA present. My conclusion is never do upgrades if you have NVIDIA in your system. Better yet avoid NVIDIA. It is not worth the extra expense and complexity hassle. My 2 cents from experience.

Avoiding Nvidia has been my policy for some years. When I had an Nvidia card installed the open source driver had power management issues, the Nvidia driver seemed to work okay. This was long before Wayland. But why bother? My desktops all have AMD cards purchased off Ebay as pulls from working systems. Notebooks are all Intel video. No need to knowingly complicate my life, I have enough complications from 'surprises'.

---

### Post by jgwphd on 2022-08-27
Anyone have any suggestions about how I might rescue my system? Last chance :-) ...before I do a reinstall and reload all my applications, tools etc. Again to everyone who tried to help, Thank-you. Also a Thank you to kurt18947 and pbear42. I appreciate you sharing your NVIDIA experiences.

---

### Post by geomcd1949 on 2022-08-27
As I understand it, in order for Ubuntu 22.04 to recognize that a monitor has a greater resolution than 1080p, these things must be present:

-- a GPU that supports, or is supported by, Nvidia driver #515, and

-- an HDMI 2.1 cable that connects the GPU to the monitor.

I had a Quadro K4200, which doesn't support -- or isn't supported by -- driver #515. I got a Quadro M4000, which does support -- or is supported by -- driver #515.

This setup still resulted in Ubuntu 22.04 reporting that the monitor had a max resolution of 1080.

Only when I upgraded the cable to HDMI 2.1 did Ubuntu report the monitor's max resolution as 2160.

---

### Post by jgwphd on 2022-08-28
@geomcd1949 - Thanks for the information. I am out traveling for a week and when I get back I'll check out the monitor and cable to identify exactly what I have. I am running NVIDIA driver #515 and have the machine working (somewhat) with an earlier kernel. I have a back up machine I am using but I'd really like to find out what is going on because if the cable is a problem than doing a reinstall won't help ....BUT it was working until I did the upgrade which tells me that the hardware is ok ...but then again, NVIDIA is involved.

---

### Post by geomcd1949 on 2022-08-28
Nvidia page to determine proper/latest driver for your GPU: [https://www.nvidia.com/Download/index.aspx?lang=en-us](https://www.nvidia.com/Download/index.aspx?lang=en-us)

---

### Post by jgwphd on 2022-09-01
@geomdc1949 I have **NVIDIA GeForce GTX 1650/PCIe/SSE2 / NVIDIA Corporation TU117 installed in a Dell XPS 8930[B] desktop machine **with i7-9700 CPU with 16GB of memory. [/B]I went to the Nvidia website you suggested and found Linux x64 (AM/EM64T) display driver.[SIZE=2]. The Nvidia site recommends 515.65.01 2022.8.2 Is that correct? If that is true then why this notice? "Note that many Linux distributions provide their own packages of the  NVIDIA Linux Graphics Driver in the distribution's native package  management format. This may interact better with the rest of your  distribution's framework, and you may want to use this rather than  NVIDIA's official package." What?????? Read the discussion here [https://www.nvidia.com/Download/driverResults.aspx/191961/en-us/](https://www.nvidia.com/Download/driverResults.aspx/191961/en-us/) in the "additional information" tab. I am confused about what NVIDA want me to do? It seems their stuff doesn't really work....[/SIZE]

---

### Post by geomcd1949 on 2022-09-01
This might be a stupid suggestion. If it is, I apologize.

When my system running Nvidia boots up, I get no icon in the lower right corner of the screen until I click inside the password block. When I click inside the box, the lower right icon then appears, and I can click on it and the choices appear. I then click on my choice and then type in my password and hit Enter.

It took me a long time to figure this out.

---

### Post by ubfan1 on 2022-09-01
The Nvidia driver 515.65.01 supplied by Canonical in the standard repositories also comes with system specific scripts to rebuild the driver when the kernel gets updated. Nvidia doesn't attempt to supply such scripts for every possible system, they just supply the driver.  Canonical drivers have been keeping pretty current with Nvidia's releases, so no the old suggestions of using the graphics-drivers PPA are really out of date.

---

### Post by jgwphd on 2022-09-01
@ubfan1 Aren't these instructions at [SIZE=2][https://www.nvidia.com/Download/driv.../191961/en-us/]("https://www.nvidia.com/Download/driverResults.aspx/191961/en-us/") in the "additional information" tab accomplishing what you are saying?[/SIZE] "Installation instructions: Once you have downloaded the driver, change  to the directory containing the driver package and install the driver by  running, as root,  sh ./NVIDIA-Linux-x86_64-515.65.01.run

One of  the last installation steps will offer to update your X configuration  file. Either accept that offer, edit your X configuration file manually  so that the NVIDIA X driver will be used, or run nvidia-xconfig"

---

### Post by jgwphd on 2022-09-01
@geomcd1949 ...when I get back in town I'll look a  that behavior again. But as I recall the selection becoming visible  didn't effect the problem one way or the other....

---

### Post by jgwphd on 2022-09-01
@ubfan1 Aren't these instructions at [SIZE=2][https://www.nvidia.com/Download/driv.../191961/en-us/]("https://www.nvidia.com/Download/driverResults.aspx/191961/en-us/") in the "additional information" tab accomplishing what you are saying?[/SIZE]  "Installation instructions: Once you have downloaded the driver, change   to the directory containing the driver package and install the driver  by  running, as root,  sh ./NVIDIA-Linux-x86_64-515.65.01.run

---

### Post by jgwphd on 2022-10-11
I never did get it running correctly and was wasting time. I just reinstalled 22.04

---

