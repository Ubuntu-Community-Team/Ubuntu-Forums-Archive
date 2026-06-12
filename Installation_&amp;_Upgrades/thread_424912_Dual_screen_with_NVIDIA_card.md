---
title: "Dual screen with NVIDIA card"
date: 2007-04-27
forum: Installation &amp; Upgrades
---

### Post by mach777 on 2007-04-27
Getting dual screen on my NVIDIA card for 7.04:

1. Downloaded the drivers from the nvidia site.

2. Stopped gnome with: sudo /etc/init.d/gdm stop

3. Alt-F2 to a new text terminal and log on. 

3.1 sudo apt-get install build-essential   (the nvidia driver needs it)

3.2 Install the driver with: "sh <filename of driver>". next->next->next->

4. I rebooted here, just issuing "sudo /etc/init.d/gdm start" might work.

5. Once in X again, open nvidia config panel hidden in applications menu under system something.

6. For best config, use separate X windows (not twinview), but enable the checkbox under the monitor setup (dont remember what it is called) so you can move windows between them. With twinview, everything you maximize end up stretched across both screens. :(

7. [SIZE="4"]IMPORTANT[/SIZE]
Since you are not root, the NVIDIA panel won't SAVE your changes when you click 'Save', so use the PREVIEW changes button , copy that text, open a root text editor (like "sudo kedit"), and open /etc/X11/xorg.conf.  Paste the preview text in, save file. Took me a long time to figure this out.

8. Hit ctrl-alt-backspace to restart your xwindows.

---

