---
title: "Upgrade to 12.04 broke unity and bluetooth"
date: 2012-05-03
forum: Installation &amp; Upgrades
---

### Post by edvar on 2012-05-03
This is the worst upgrade I did since 8.10 to 9.04 when everything went pear shaped and I had to rebuild everything from scratch. From then on I always upgraded to every new release without any major issues until 11.04 when I decided to do a clean install but went back to the upgrade path to 11.10 and so on.

I had a pretty stable oneiric 11.10 setup until I decided to install a kernel update to version 3.0.0-19 last week. After that unity just became unusably slow. I rolled back the kernel to 3.0.0-18 and everything went back to normal. Yesterday I decided to upgrade to precise 12.04 to see if I could get to the latest kernel and fix all the issues. 

After the upgrade, first head ache: "No such partition" after the GRUB menu. I was finally able to fix it using the Live CD but little I knew it was just the beginning of my problems.

As soon as I booted, same problem as before: Unity slow as a dead dog. So slow it was almost barely frozen. I tried to reboot to the old 3.0.0-18 kernel to see if it would solve the problem as it did on oneiric but no luck. It was also very slow on the old kernel.

I rebooted the machine again and managed to login using the Unity 2D session. Everything was fine and back to normal speed and it made me suspect of video driver problems. I rolled back to the very old and stable NVIDIA driver 173 but still same problem.

Anyway, now I'm using Unity 2D and it somehow puts me back on track as I can at least run XBMC and watch my movies. This is my HTPC with all my media connected to my TV and it also doubles as my always on remote file/ssh server.

As this computer stays on my living room, I drive it using a bluetooth keyboard (Logitech DiNovo Edge). After the upgrade it doesn't work anymore. I manage to connect and pair for a couple of seconds and then it stops working. I found this on /var/log/syslog:

May  3 22:02:22 kernel: [  889.530528] Bluetooth: Generic Bluetooth USB driver ver 0.6
May  3 22:02:23 kernel: [  889.787980] Bluetooth: HIDP (Human Interface Emulation) ver 1.2
May  3 22:02:29 kernel: [  896.194237] Bluetooth: hci0 urb e363bd80 submission failed
May  3 22:03:43 kernel: [  970.346300] Bluetooth: hci0 urb e5039a80 submission failed

Any ideas on how to get Unity 3D back and ,more importantly, bluetooth working again? Any help would be greatly appreciated.

---

### Post by edvar on 2012-05-03
Guess I just got lucky and found this 5 minutes after I posted this thread:

[http://blog.neolocus.com/2012/04/ubuntu-12-04-lts-precise-pangolin-and-logitech-dinovo-keyboard-issue/](http://blog.neolocus.com/2012/04/ubuntu-12-04-lts-precise-pangolin-and-logitech-dinovo-keyboard-issue/)

It solved the bluetooth problem! Now I just need my Unity 3D back...

---

### Post by edvar on 2012-05-07
I tried this to no avail:

[http://askubuntu.com/questions/125608/unity-3d-no-longer-works-after-installing-12-04](http://askubuntu.com/questions/125608/unity-3d-no-longer-works-after-installing-12-04)

Compiz takes 100% CPU and Unity 3D remains unusable. When I kill Compiz then XORG takes over the CPU instead.

I tried installing Gnome Shell since it doesn't use Compiz but same problem. The only usable desktop environment on my computer now is Unity 2D. Anything with 3D Acceleration is unbearably slow.

Tried old kernels and old drivers and nothing works. Any ideas?

---

### Post by edvar on 2012-05-09
I managed to get it fixed... At least temporarily.

I installed the latest updates to unity and the nvidia driver and still had same problem. Then I read somewhere it'd be a good idea to delete the whole ~/.config folder. Did that and my Unity 3D was back to normal.

However now after a couple of minutes XOrg takes over 100% of the CPU and the whole computer freezes.

It's very frustrating...

EDIT: Gnome Shell works fine. It seems Unity 3D is causing some sort of memory leak on X

---

