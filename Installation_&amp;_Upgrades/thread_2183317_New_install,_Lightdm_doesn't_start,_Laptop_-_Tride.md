---
title: "New install, Lightdm doesn't start, Laptop - Trident Cyberblade i1"
date: 2013-10-24
forum: Installation &amp; Upgrades
---

### Post by Justcameron on 2013-10-24
New lubuntu 13.10 install on an old laptop (used to be running Windows ME.) 
Used alternate install CD as the laptop has only 128MB of RAM

When booting up, it goes to the lubuntu splash screen with the little dots which light up. After that, the screen goes blank. Doesn't respond to CTRL ALT F2 either. 

I can get into grub and edit the kernel boot options. And the kernel loads (eg. if I remove "quiet splash $vt_handoff" and replace with "text" I can boot and login to a tty. 

I note when I'm booting and there is text rushing past it says "Starting load fallback graphics drivers [Fail]" at least I think that's what it says.. I don't know how to pause it to read it.

Have been reading [this sticky]("http://ubuntuforums.org/showthread.php?t=1743535") and have tried  "nomodeset" "xforcevesa" and "i915.modeset=0 xforcevesa" (separately, not together) without any luck.

The laptop is an Acer TravelMate 212TX
800mhz CPU
128MB RAM

```
$ lspci | grep VGA
01:00.0 VGA compatible controller: Trident Microsystems CyberBlade/i1 (rev 5d)


$ sudo lshw -C display
*-display UNCLAIMED
  description: VGA compatible controller
  product: Cyberblade/i1
  vendor: Trident Microsystems
  physical id: 0
  bus info: pci@0000:01:00.0
  version: 5d
  width: 32 bits
  clock 66MHz
  capabilities: agp agp-1.0 pm vga_controller cap_list
  configuration: latency=32
  resources: memory:80800000-80ffffff memory:80100000-8011ffff memory:81000000-817fffff memory:80120000-8012ffff



$ sudo more /var/log/lightdm/x-0.log
...
Initializing built-in extension DRI2
Loading extension GLX
X: ../../dix/pixmap.c:112: AllocatePixmap: Assertion `pScreen->totalPixmapSize > 0' failed.


$sudo more /var/log/lightdm/lightdm.log
...
[+0.07s] DEBUG: DisplayServer x-0: Launching X Server
[+0.08s] DEBUG: Launching process 1169: /usr/bin/X -core :0 -auth /var/run/lightdm/root/:0 -nolisten tcp vt7 -novtswitch
[+0.08s] DEBUG: DisplayServer x-0: Waiting for ready signal from X server :0
[+0.09s] DEBUG: Acquired bus name org.freedesktop.DisplayManager
[+0.09s] DEBUG: Registering seat with bus path /org/freedesktop/DisplayManager/Seat0
[+3.58s] DEBUG: Process 1169 terminated with signal 6
[+3.58s] DEBUG: DisplayServer x-0 X server stopped
...

```

I haven't yet worked out networking and don't have any floppy disks so I don't know how I can get logfiles from the laptop to this forum, I typed the above out manually. Which is why there is only snippets of the logs. If anyone wants to see any other logs, can you tell me what I'm looking for please?

So... help?

---

### Post by LuvLinuxOS on 2013-10-28
Justcameron,

> The laptop is an Acer TravelMate 212TX
800mhz CPU
128MB RAM

I looked at your laptop specs up on the net.  I think that using shared video memory will take you system below the minimum requirement for Lubuntu 13.10.  I have alot of older hardware myself so you might want to try Lubuntu 13.04 as I have found this to be the very best version for older equipment. you can get it [here]("http://cdimage.ubuntu.com/lubuntu/releases/13.04/release/").  If that do not solve your problem, being that I am an loyal ;-) Ubuntu / Lubuntu user it hurts me to recommend another distro.... although it is in the Debian family... Check out [DSL here]("http://www.damnsmalllinux.org") or visit my [blog]("http://luvlinuxos.blogspot.com") to see me demo it in an older post.  I hope this helps!!!

Be Blessed...I Am!!!

---

