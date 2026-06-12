---
title: "No display or wireless after Karmic install"
date: 2009-11-27
forum: Installation &amp; Upgrades
---

### Post by icksa on 2009-11-27
Hello:

I installed 64 bit Karmic on my Inspiron 15n laptop today and neither my display or my wireless card works. I have an intel integrated graphics card and a broadcom bc4312 wireless card - more details below

1) Display issues

My display did not work during the installation so I had to install using an alternate cd. When the computer boots, it displays "grub loading" for 1 second, then a blinking cursor for about 5 seconds, then nothing. After a minute or so, I hear the ubuntu login sound, so I know that X has started. Hitting Ctrl+Alt+F1 doesn't take me to a console, just the same black display. I tried plugging in an external monitor, and everything seems to work on that. I can see the splash screen before X starts, then the prompt to login. Using the external monitor, I installed all of the Karmic updates with no improvement. 

To reiterate, the problem occurs before X even starts. When the display goes blank, there is a weird screen distortion for a second, but that is all. I can't even get to a text console. 

2) Wireless issues

The system->administration->hardware drivers dialog has the option to install the b43 wireless driver. I installed it, but my wireless still does not work. I googled around and saw that some suggested installing bcmwl-kernel-source package, which I think is the proprietary driver. This causes my computer to immediately crash. Restarting leads to an immediate kernel panic.

So these are my pretty serious usability issues. I think I will wait a day or so to see if anyone can help. Otherwise, I am going to upgrade to a clean Jaunty install. Everything works fine in Jaunty...

Thanks
Milad

---

### Post by ajgreeny on 2009-11-27
I wonder if your x problem is related to compiz, which seems to be the window manager by default on install, even if your card can not use it successfully.  It could be worth trying Alt+F2 to get a run dialog and using ```
metacity --replace
``` in that.

If it doesn't work, I'm afraid I have no other suggestions to try.  You will need to await other responses, I think.

---

### Post by icksa on 2009-11-27
Hi:

Thanks for the suggestion, but unfortunately it didn't help. I should mention that I tried googling around on the display issue, but unfortunately most of the problems seemed to involve ATI/NVIDIA issues which kicked in when X was starting up. My problem seems to start as soon as grub begins booting the kernel.

Thanks

---

### Post by icksa on 2009-11-27
Ha! Ok, after looking around I managed to find out that you can get the display to work after adding the kernel boot option:

i915.modeset=0

To do this, you have to edit the file: /etc/default/grub

Add i915.modeset=0 to the GRUB_CMDLINE_LINUX_DEFAULT line, so I changed mine from:
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
to:
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash i915.modeset=0"

Then type "sudo update-grub" and restart, hopefully your display will work!

---

### Post by icksa on 2009-11-27
Yes! I got the wireless to work too. The fix involved entering the command:

sudo apt-get --reinstall install bcmwl-kernel-source

I did try to install this package before from synaptic which crashed my computer. I guess the --reinstall does something I don't know about. Anyway everything is working now.

THanks
Milad

---

