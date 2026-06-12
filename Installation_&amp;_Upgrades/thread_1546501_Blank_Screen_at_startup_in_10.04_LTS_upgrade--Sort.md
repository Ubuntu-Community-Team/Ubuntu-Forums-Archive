---
title: "Blank Screen at startup in 10.04 LTS upgrade--Sort of solved"
date: 2010-08-05
forum: Installation &amp; Upgrades
---

### Post by JCMB1 on 2010-08-05
After finally getting Ubuntu 10.04 to work, I decided to update my files to receive the blank screen.

OK, the most useful hint I found was from [myles.tonnies]("http://ubuntuforums.org/member.php?u=948548") [here]("http://ubuntuforums.org/showpost.php?p=9472157&postcount=107") where he makes the point:
> Just a tid bit for new users. To access the GRUB menu after an install,  hold down the SHIFT Key. Then follow the instructions in post 14.The shift key did indeed get me into a useful menu with the options of starting Ubuntu in either an old version of Linux (2.6.31.22), or a new version (2.6.32.24).  Since the new version was giving me grief, I opted for the old one.

The older version will get me into Ubuntu, but I receive the following error messages flashing on the screen before Ubuntu loads:
> mount: mount.img name on /dev failed: no such device
chroot: cannot execute*** /etc/apparmor.d/initramfs***[COLOR=#cc0000]: no such file or directory[/COLOR] 

(forgive me for any errors since I copied this from a blurry photo of the screen).

I have to admit to not being too worried about that message since Ubuntu loads and appears to work.

Anyway, I try to get into grub using the terminal with these results:

> michael@michael-laptop:~$ sudo edit /etc/default/grub
[sudo] password for michael: 
Warning: unknown mime-type for "/etc/default/grub" -- using "application/octet-stream"
Error: no "edit" mailcap rules found for type "application/octet-stream"
michael@michael-laptop:~$ sudo gedit /etc/dfault/grubno file showed up (that's pretty much copied from what happened).

Oh yeah, I have to remember to hit the shift key when I boot the computer or I end up with the blank screen and nothing happens.

Questions? Comments? Help?

---

### Post by davidmohammed on 2010-08-05
black screens are usually graphics issues - possible fixes depend on the graphics card you are using.

When you display the grub screen - choose the latest kernel using the up-and-down arrow keys then press e to edit.

Find the line ending with "quiet splash --"

add one of the following options immediately preceding "quiet splash --"

nomodeset
i915.modeset=1
i915.modeset=0

then press CTRL+X to boot.

e.g. the line should read something like "... nomodeset quiet splash --"

---

### Post by JCMB1 on 2010-08-05
OK, I tried that, but how do I keep from having to do that everytime I boot my computer???

---

### Post by davidmohammed on 2010-08-05
open your terminal

type

sudo nano /etc/default/grub

change
GRUB_CMDLINE_LINUX=""

to add your option

e.g.
GRUB_CMDLINE_LINUX="noapic"

save

type

sudo update-grub

---

### Post by JCMB1 on 2010-08-05
Tried that:
> 
Anyway, I try to get into grub using the terminal with these results:

     
                                               [QUOTE]  michael@michael-laptop:~$ sudo edit /etc/default/grub
[sudo] password for michael: 
Warning: unknown mime-type for "/etc/default/grub" -- using "application/octet-stream"
Error: no "edit" mailcap rules found for type "application/octet-stream"
michael@michael-laptop:~$ sudo gedit /etc/dfault/grub                                 
no file showed up (that's pretty much copied from what happened).[/QUOTE]Any other suggestions?????

---

### Post by davidmohammed on 2010-08-06
please type in EXACTLY as posted - i.e. sudo nano /etc/default/grub
NOT sudo edit /etc/default/grub

---

### Post by JCMB1 on 2010-08-06
OK, starting with using e to edit the latest kernel and 

> add one of the following options immediately preceding "quiet splash --"

nomodeset
i915.modeset=1
i915.modeset=0

then press CTRL+X to boot.resulted in a screen with small "ubuntu" logos at the top and a frozen computer.  The only way the computer would restart one time was to unplug it.

The one exception was **i915.modeset=1**

 **sudo nano /etc/default/grub **produced something I could edit and I added it to come up with 
GRUB_CMDLINE_LINUX="**i915.modeset=1**"

And it works fine now.

Thank you.

---

