---
title: "Installing 15.04 on Asus N550JX"
date: 2015-09-04
forum: Installation &amp; Upgrades
---

### Post by tavis2 on 2015-09-04
I just bought this laptop and haven't seen it covered, so I figured I would share my installation experience.
First, before the installation begins, I had to add the argument nouveau.noaccel=1 to the kernel command line when booting the installation media from USB (press "e" to do this at the first prompt).  Otherwise, the Nouveau driver would create a kernel panic. I also removed the "quiet splash" options so I could see what was going on.  Once the installation began, I no longer had any graphics card issues.
So, my experience was that most things worked without any tinkering: Graphics card, internal speakers and mic, webcam, suspend.

Things that didn't work:
1. As users of similar models have found, the fn keys to dim the screen don't work.  This can be easily fixed by adding "acpi_osi= " to the boot command line in /etc/default/grub, and then running "sudo update-grub"; on the next reboot, they worked.
2. I could not get the external subwoofer to work.  I am pasting instructions below that I used based on experiences of others with similar laptops, but they didn't help.  Hopefully they will point someone in the right direction.  Warning: After doing this, it took a bit of fiddling with pavucontrol to get my internal mic working again, so I wouldn't plunge into it unless you have some time on your hands.



a. Add the following line to /etc/modprobe.d/alsa-base.conf:
options snd-hda-intel model=asus-mode6 patch=,alsa/n550-bass


b. Add the following file as /lib/firmware/alsa/n550-bass
[codec]
0x10ec0668 0x104311cd 0

[pincfg]
0x1a 0x80106111

c. Reboot; install and launch hdajackretask, set all channels so that they output to hdmi

d.  Add the following lines as /usr/share/pulseaudio/alsa-mixer/profile-sets/extra-hdmi.conf:

[Mapping analog-surround-21]
        device-strings = surround40:%f
        channel-map = front-left,front-right,lfe,lfe
        paths-output = analog-output analog-output-speaker
        priority = 7
        direction = output


e. install and fiddle with pavucontrol to get the mic working again.

.... But no luck with the subwoofer.  I have a feeling that this laptop uses a different pin configuration than the others, and I wasn't in the mood to spend more time figuring out what it was.  The subwoofer is kind of crappy anyway (I listened to in under Windows.)  So I'm giving up for now, but if someone wants to solve it, maybe they can post the solution below.

---

### Post by LK_gandalf_ on 2015-11-16
Thanks, great post. 
I have a N550JK which I guess is very similar. Same problem here with the subwoofer, but for me it's important right now, so I need to fix it. I also think that hdajack is the solution, but we need the help of an expert to know how to configure it.

Have you tried this? It screwed my audio, but maybe you find some information.
[http://ubuntuforums.org/showthread.php?t=2217683](http://ubuntuforums.org/showthread.php?t=2217683)

---

