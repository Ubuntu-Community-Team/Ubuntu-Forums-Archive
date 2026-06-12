---
title: "My problem : black screen after grub. I suppose problems with the Nvidia card."
date: 2013-11-30
forum: Installation &amp; Upgrades
---

### Post by jj.wauters on 2013-11-30
My problem : black screen after grub. I suppose problems with the Nvidia card.
Working in Ubuntu Recovery mode the system always indicates :
"The system is running in low-graphics mode" 
"Stand by one minute while the system restarts"
From here the system hangs, or I can continue in terminal mode (Ctrl-Alt-F1) and in some very rare occasions
it goes further in GUI mode.
After installing Ubuntu the Nvidia driver version 319 was installed (and did not work)
I have download the latest Linux 64bit Nvidia driver 331.20.
During his installation I get the message "Distribution-provided pre-install script failed".
Is there a way to configure this machine or should I stop after a week messing with Ubuntu?

Specifications :
Machine : HP Envy 15 Notebook
OS : Windows 8.1 preinstalled
OS : Ubuntu 12.04
Processor : Intel i7 4700 MQ
Memory :
- RAM : 12GB
- HardDrive : 1000GB
Graphics :
- Intel HD Graphics 4600
- Nvidia Geforce GT740M

---

### Post by Bashing-om on 2013-12-01
jj.wauters; Hi ! Welcome to the forum .

Unfortunately Nvidia offers little support for switchable graphics to linux.
There are some options:
If you are running version 13.10. see these docs:
[https://wiki.ubuntu.com/X/Config/HybridGraphics](https://wiki.ubuntu.com/X/Config/HybridGraphics)
With some support back to 12.04.3

[http://rudrageek.com/linux-now-supports-hybrid-graphics-systems-ubuntu-13-10/](http://rudrageek.com/linux-now-supports-hybrid-graphics-systems-ubuntu-13-10/)

And there is also the optimus technology of the BumbleBee project;
[https://wiki.ubuntu.com/Bumblebee](https://wiki.ubuntu.com/Bumblebee)
[http://www.webupd8.org/2013/04/bumblebee-321-released-with-ubuntu-1304.html](http://www.webupd8.org/2013/04/bumblebee-321-released-with-ubuntu-1304.html)
[http://ubuntuforums.org/showthread.php?t=1657660](http://ubuntuforums.org/showthread.php?t=1657660)

Lastly if you are running version 13.10, there has been a lot of work done by the developers of open source graphics drivers, see:
[https://launchpad.net/~oibaf/+archive/graphics-drivers/](https://launchpad.net/~oibaf/+archive/graphics-drivers/) 
Updated and Optimized Open Graphics Drivers Supported Ubuntu versions:- 13.10 (saucy)

[INDENT][INDENT]my regards
[/INDENT][/INDENT]

---

### Post by jj.wauters on 2013-12-02
Hello Bashing-Om


Thanks for the suggestions. In the meantime my problem is solved and apparently not due to the driver.

 As I was forced to do many times a hard reset and between the attempts I also tried starting grub in recovery mode with &#8220;Run in failsafe graphic mode&#8221; and/or &#8220;update grub bootloader&#8221;, I remarked that
 the &#8220;nomodeset&#8221; keyword was disappeared in grub. After editing and updating grub from terminal, the GUI starts like expected.

This thread can be closed.

Regards

---

### Post by Bashing-om on 2013-12-02
jj.wauters; Good deal !

Caveat: Running with a permanent "nomodeset" not the best thing to do .. as this option disables kernel mode setting.

Closing the thread: Only you can do that and only if you are satisfied that the original situation has been resolved.
1st post -> thread tools.

[INDENT][INDENT]good things do happen
[/INDENT][/INDENT]

---

