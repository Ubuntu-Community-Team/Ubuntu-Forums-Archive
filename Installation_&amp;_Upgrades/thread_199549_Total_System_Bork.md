---
title: "Total System Bork"
date: 2006-06-18
forum: Installation &amp; Upgrades
---

### Post by bodhi.zazen on 2006-06-18
I see lots of posts on the Forum, no solutions.

I was running Ubuntu Drapper testing and was quite happy. I had several programs running in WINE as well as QEMU (with kqemu) as well as.. well alot.

I upgraded after the release and my entire system is kaputt!!

List of known problems:

1. At boot GDM fails and the system boots to a CLI.

     Error messages at boot:
       A. resolvconf fails (it has failed for a while)
       B. Starting system log .... Failed
       C. Starting system message bus dbus permission denied.... Failed
       D. Starting GDM....  Failed
       E. Starting HP LInux Printing and Imaging System.... Failed
       F. Starting ClamAV.....  Failed. Unable to open /var/lib/clamav
       G. Second Clam error, looks like a permission error

              /var/lib/clamav/freshclam

       H. Error: Problem with internal logger: Fail

2. I can not log in as any previously configured user. I can log in as root.

3. No network.

4. I can not install from the CD (I added it using synaptic and  apt-cdrom).
The (6.06) CD has been added to my /etc/apt/sources.list but fails with apt-get, aptitiude, and synaptic.

     From sources.list
        deb:cdrom:[Ubuntu 6.06 _Drapper Drake_- Release i386 (20060531)]/ drapper main restricted

     All other sources are commented out.

5. Logged in as ROOT (at CLI). Change user 
     su user
     System prints "No Shell" and does not change to the user.

6. XFCE starts, but no menu-> ctr-alt-backspace back to CLI.

7. Can start KDE or GNOME (as root) with X & startkde or X & gnome-session.

I have chown -r user:user /home/user no help. Set user shell with CLI. no help.


Is there a fix, or back up /home/user and re-install.

Is re-install stable???

---

### Post by fragos on 2006-06-19
Given that Dapper seems stable for most of us and your symptoms seem all over the map, a re-install seems prudent.  I have limited experience with wine and QEMU.  For me wine is considered a last resort.  Wine gets better as time goes on  but IMHO running Widows or DOS aps on Linux seems a bit of an unatural act in a good luck card environment.  Problems can have strange sources.  For example, I tried easyubuntu to install an Nvidia driver.  Not only didn't it work but it also installed a new neon kernel on my AMD x86_64 which already the latest copy of the generic kernel.  Who knows what running a kernel optimized for Intel on an AMD processor will do.

---

### Post by bodhi.zazen on 2006-06-19
Thanks fragos, good advice for sure. 

Wine, qemu, etc were all working prior to upgrade and at least wine was not upgraded with my system upgrade (I watch wine closely due to "regression" problems). None of the error messages seem related to wine or qemu but rather system errors and, as you say, quite extensive.

I seem to have simmilar issues to this post:

[http://www.ubuntuforums.org/showthread.php?t=191477](http://www.ubuntuforums.org/showthread.php?t=191477)

At least I have the same dhcp error:
localhost dhclient: execve (/lib/dhcp3-client/call-dhclient-script, ...): Permission denied.

I posted to that thread proir to starting this one, no answers yet.

My concern is a reinstall will lead to the same problem. I see a lot of posts here, it looks lilke Ubuntu has become somehow unstable/unreliable.

Anyone else ?

---

### Post by rcarring on 2006-06-19
Emulators work hand in hand very closely with the operating system. Wine translates calls to the Windows apis and libraries so that Word for instance can run on Ubuntu. Crossover Office which uses Wine ran best on Breezy, it is still runnable under Ubuntu but is a lot slower.

---

### Post by bodhi.zazen on 2006-06-19
thank you rcarring.

Let me re-phrase my post. I do not seem to be having problems with emulation (have not tried). I do not think my recent upgrade installed a new kernel.

I am having problems with my OS ie booting, networking, and logging in as a non-root user.

Any suggestions?????

---

