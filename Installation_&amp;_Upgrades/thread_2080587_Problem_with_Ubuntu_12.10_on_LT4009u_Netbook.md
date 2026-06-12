---
title: "Problem with Ubuntu 12.10 on LT4009u Netbook"
date: 2012-11-04
forum: Installation &amp; Upgrades
---

### Post by 71yama on 2012-11-04
Hello. I've never had a problem with installing Ubuntu on any f my pcs or laptops, now I bought this gateway notebook and I can't get it working. It came with windows 7 starter edition which I replaced with Ubuntu, the installation went smoothly without any issues until it asked to reboot. It starts to load then stops and hangs like that forever, if I try to install it again it says that there is already Ubuntu 12.10 installed on the machine and it doesn't change anything if I replace the installation or install another one next to the old one. If I want to try Ubuntu from cd without installing it won't load either. I thought to use windows xp cd to quick format the drive and start again, but the installer says it didn't detect any hard drives. It's a 320gb Toshiba and currently the partitions look like this:

/dev/sda
 /dev/sda1    ext4    319010MB  7515MB
 /dev/sda5    swap   1060MB     0MB

I would appreciate any help.

---

### Post by 71yama on 2012-11-04
After it starts to load services which all appear to be [ OK ] (the last one being * Stopping save kernel message), It hangs and when I press power button it goes:

acpid: exiting
speech-dispatcher disabled; edit/etc/default/speech-dispatcher
*Asking all remaining processes to terminate...
*All processes ended within 1 second...
modem-manager[722]: <info> Caught signal 15, shutting down...

*Deactivating swap...
unmount: /run/lock: not mounted
unmount: /run/shm: not mounted
*Will now halt
[    51.806879] hub 3-0:1.0:   >hub_port_status failed (err = -110)
[    51.809001] hub 3-0:1.0:   >hub_port_status failed (err = -110)


and shuts down.

---

### Post by 71yama on 2012-11-04
When trying to install older version of Ubuntu, 8.04.4's menu will open but after selecting "install system" it hangs, same with Ubuntu 11.

I just tried Ubuntu 10.04.4 it installed and started with no problems. I'd still like to know what the problem with 12.10 was if anyone can help. Thanks

---

### Post by critin on 2012-11-04
Did it work with windows?  Have you used it at all since you bought it?
You might try an older version than 12.10, it's not quite stable yet. 12.04?

EDIT:  *Sorry, you posted before I did.*  

I'm curious about how it worked before taking off windows.

Will it not run a live session at all?

---

### Post by 71yama on 2012-11-04
It wouldn't run being installed next to windows 7, live session wasn't loading either. 10.04 worked and that's the only one I ever used. I was hoping that 12 would come better equipped and getting wifi to work would be easier, but I guess I can live without it.

---

### Post by rbcrbc on 2012-11-11
Just got the LT4009u Netbook yesterday - same problem.

Windows works perfectly, ubuntu install mostly works, but freezes during boot. I believe the problem to be the GMA900 video card and the xorg config.

By trying different options at boot (recovery mode, nosplash, and similar), I can get to a prompt.

By looking at xorg logs, seems like it either can't find a valid driver, or xorg freezes / crashes, or ... causes the machine to freeze / crash, to the point that I need a hard reboot.

---

### Post by rbcrbc on 2012-11-11
ok, I can get the graphical interface to start. Still debugging, but, if you:

1) boot in recovery mode (from grub)
2) get a terminal
3) as root, run command like:

cat > /usr/share/X11/xorg.conf.d/05-modeset <<EOF
Section "Device"
    Identifier "gma500_gfx"
    Driver     "modesetting" 
EndSection
EOF

It then starts the graphical interface.

---

### Post by rbcrbc on 2012-11-11
Also, still playing with the settings, but if from grub menu you change:

gfxmode $linux_gfx_mode

to

gfxmode 1024x600

(which is the screen resolution)

splash screen seems to be working? And brightness and content of screen doesn't seem messed up.

---

### Post by rbcrbc on 2012-11-11
So, ok, most of it is working stably.

1) As described above, create the file in /usr/share/X11/xorg.conf.d, reboot.

2) in /etc/defaults, modify the grub config file, to have:
GRUB_GFXMODE=1024x600
GRUB_GFXPAYLOAD_LINUX=1024x600

(remember to uncomment the first one, and to add the second one)

3) run upgrade-grub2 to update the grub config

4) reboot

Also :) if your touchpad is not working, remember that you can enable / disable it by using F6.

We spent about 30 minutes trying to understand why the synaptics driver wasn't working... when in facts it was working perfectly well, I just had tried to use F6 before when moving windows around.

The next problem we're tackling now is that when waking up from suspend mode, the screen is full of garbage.

ctrl+alt+fn+f1 will get you a "text console"
service lightdm restart will restart X, and get you a working console again.

---

### Post by rbcrbc on 2012-11-11
Ok, to get the resume from suspend to work, just remove, as root:

rm /usr/lib/pm-utils/sleep.d/99video

Don't know which part messes the screen up, but a similar bug was filed here:

[https://bugs.launchpad.net/ubuntu/+source/pm-utils/+bug/689814](https://bugs.launchpad.net/ubuntu/+source/pm-utils/+bug/689814)

---

### Post by atirado0617 on 2012-11-13
I am having the same issue! :-( 
I just got the NetBook yesterday and the first thing I did was try to install Ubuntu 12.10 using a USB. The first problem I was having is that it did not boot past the SYSLINUX screen. After, I decided to run the Windows Ubuntu Installation from within windows. It installed just fine but then stops and hangs forever... Help!? I don't want to live in a windows environment!

---

### Post by rbcrbc on 2012-12-09
Follow the instructions I left a few messages ago, and you should be set. (start in recovery mode).

---

### Post by rbcrbc on 2012-12-09
BTW - don't know the cause yet. 

But either because of my WNDR3700 (running a nightly build of dd-wrt, not always reliable) or the proprietary broadcom drivers (wl) and the BCM4313 network card in this laptop, wireless was very unreliable at my place.

Example:

$ ping 8.8.8.8

while running tcpdump on the netbook would show the arp request, but no arp reply for the gateway. On the gateway, with tcpdump, I would see both request and reply. If I hardcode the mac address of the gateway with ip neigh, still the replies and many packets don't make it back to the netbook, despite being visible on the gateway.

WORKAROUND

the opensource driver (bcma, brcmsmac and friends) seems to work much more reliably. A quick hack to get it used by default is to:

sudo mv /etc/modprobe.d/blacklist-bcm43.conf ~/

and reboot.

---

### Post by nominal on 2012-12-23
Hey,

rbcrbc -- none of your instructions worked for me. When I booted into safe mode and rand the commands as root, it said the directory was read only.

---------

My story: This was my friend's netbook and he wanted to place a clean install of Lubuntu on it. Initially he had Windows 7 starter and Ubuntu (through Wubi) dual boot on it. We tried a Live USB install of 12.10, but it just ended up messing up the laptop.

[LIST=1]
[*]I took the netbook home with me and played around with it for the next day and a half:
[*]I wiped the HDD clean with [DBAN]("http://www.dban.org/"). I wrote the DBAN image to a thumb drive using Universal-USB-Installer.
[*]I tried installing Ubuntu 12.10 from a Live USB. I tried unetbootin and Universal-USB-Installer -- touching the keyboard would freeze the boot menu, or sometimes, I would get the "syslinux 4.03 2010-10-22 EDD" screen hang.
[*]I tried Linux Mint too -- which "Failed to start the X Server". At this point I was beginning to think it was a graphical problem.
[*]I tried FreeBSD as well. It wouldnt install (so many errors).
[*]I also tried alternate installs of Ubuntu 12.04 and 10.04. Nothing.
[*]Then I installed Fedora with a few errors. Then when I tried the alternate Lubuntu 12.10 install -- it let me re-install GRUB, but then when I went to the full install I got more errors.
[*]Then I used [Image Writer for Windows]("https://launchpad.net/win32-image-writer/") with Ubuntu 12.10 -- and somehow it worked and booted into Live mode. But if I hit "Try Ubuntu 12.10, it would freeze." I installed it clean anyway, but then upon restart it wouldnt boot. I tried setting the boot options in GRUB found [here ]("http://ubuntuforums.org/showthread.php?t=1613132") (nomodeset, etc) but none of those worked either.
[/LIST]

**[SIZE="4"]So how did I get it to finally work?[/SIZE]**
[LIST=1]
[*]I wrote **Kubuntu 12.04.1** (not 12.10 -- for now, just give up on 12.10 and stick to 12.04 LTS) to a flash drive **(using Image Writer)** and it booted into Live mode. 
[*]Then I installed it. It even installed with only one error!
[*]Then I just installed the Lubuntu desktop environment:
[*]```
sudo apt-get install Lubuntu-desktop
``` and then I installed the updates and restarted the netbook a few times to make sure everything was OK.


And it was.

[*]I followed the terminal commands [here ]("http://www.psychocats.net/ubuntu/purelubuntuprecise")to removed Kubuntu and 'keep' Lubuntu and all is well in the world.

[/LIST]

From my experience, you must use **kubuntu-12.04.1-desktop-i386** with **Image Writer** and _not_ unetbootin. I had a 2GB USB stick formatted to FAT32.

---

