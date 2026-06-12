---
title: "Ubuntu 13.10 upgrade worked, but slow login and no wallpaper?"
date: 2013-10-19
forum: Installation &amp; Upgrades
---

### Post by bswilson on 2013-10-19
I have successfully upgraded from 13.04 to 13.10 with seemingly no problems (with the process). However, my login to Unity is very, very slow and under no circumstances can I change the background from solid black to anything else - colors, wallpapers, pictures - nothing. And after a few minutes my desktop seems to essentially freeze. I have to Ctrl-Alt-F1 to a command shell and reboot.

Has anyone else experienced this? Other than the lightdm log file, is there a better place for me to try and troubleshoot this?

***Edit: **I have tried using System Settings, Nautilus, Shotwell, and Image Viewer to set the desktop wallpaper - none will work.*

***Edit: **I was able to find [a link on the internet with instructions]("http://www.dedoimedo.com/computers/ubuntu-ringtail-nvidia.html") to re-install my NVIDIA driver. Problem solved..*

---

### Post by neelson2 on 2013-10-23
I also upgraded successfully to 13.10, but have a lot of small problems. Maybe just a clean reinstall helps

---

### Post by bswilson on 2013-10-24
So, even with my problems I have been able to use my Ubuntu 13.10 system. However, today I had an X server crash and now I cannot launch anything but low-graphics mode. I've tried the NVIDIA solutions listed [here]("http://askubuntu.com/questions/141606/how-to-fix-the-system-is-running-in-low-graphics-mode-error"), to no avail. My system is absolutely unusable now. Any ideas?

---

### Post by craig10x on 2013-10-24
Did you use the software updater upgrade method?  I suspect that is more troublesome then using the option that i use (which i think is only offered if you run 1 ubuntu on your system...
that is to use the live session cd's installer option to UPGRADE instead of just doing a clean install...works like a charm for me...you can try using that first....even though you are already running 13.10 the live installer should give you the option of doing it again...in the re-do it may be able to straighten everything out...nothing to lose at this point...

Oh, and always turn off any ppas you have in software sources prior to an upgrade (uncheck the box)...

---

### Post by bswilson on 2013-10-28
> Oh, and always turn off any ppas you have in software sources prior to an upgrade (uncheck the box)...

Yeah, I failed to do that, but the Software Updater prompted me to disable them, to which I replied in the affirmative. I'm afraid that this did something to my system. I have seemingly overcome being able to log in, but I can only log into a Gnome 3 interface. I don't seem to have any choice to switch to Unity, for example.

***Edit: **OK actually I CAN switch to Unity or Gnome 2, etc. I did not immediately see how but now I see the GUI-based method of changing. Sorry. *

---

### Post by mauro-rossi on 2013-12-17
Hi, can you explain what you exactly did to solve? I'm stuck with the same problem.

My configuration Ubuntu 13.10 with nvidia 331 drivers from xorg edgers PPA. I've also tried with nvidia 304, but nothing changes

Mauro

---

### Post by JasonWDTX on 2014-01-05
I also have the same problem with ubuntu 13.10 and I do NOT have any nvidia componants that need nvidia drivers. How do you solve this with 13.10?

---

