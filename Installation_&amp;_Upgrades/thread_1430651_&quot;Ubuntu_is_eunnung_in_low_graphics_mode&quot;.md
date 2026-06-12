---
title: "&quot;Ubuntu is eunnung in low graphics mode&quot; (EE) open /dev/fe0: No such file or dierctor"
date: 2010-03-15
forum: Installation &amp; Upgrades
---

### Post by popolvar on 2010-03-15
Hello all,

let us start with the problem. After making and update my Karmic Koala and trying to set up lamp through tasksell, i have rebooted my notebook. Then the ubuntu logo was displayied and i get an

"Ubuntu is eunnung in low graphics mode"
(EE) open /dev/fe0: No such file or dierctory

i have done some googling and figured that it has most likely to do with ubuntu trying to using frame buffer wrongly. First I have tried to follow some advices posted at 

[https://wiki.ubuntu.com/FrameBuffer#...ns%20in%20GRUB]("https://wiki.ubuntu.com/FrameBuffer#Setting%20different%20framebuffer%20resolutions%20in%20GRUB")

like this


[LIST]
[*]"vga=normal", or "nofb", disables the framebuffer
[*]if "nofb" does not help, try "nomodeset" to disable kernel mode setting
[*]"vga=ask" will able you to set a value at each boot good for testing out the various modes.
[/LIST]
non of them worked. Being unable to disable framebuffer i  modified the grub2 (in fact it is 1.97~beta4), to use my true resolution. That didn't work out either

now i after editing the grub menu by pressing ''e'' i get__

recordfail=1
if [ -n ${have_grubenv} ]; then save_env recordfail; fi
set quiet=1insmod ext2
set root=(hd0,5)
search --no-floppy --fs-uuid --set c763a81d-d00b-4880-9111-9c305affc67b
linux   /boot/vmlinuz-2.6.31-20-generic root=UUID=c763a81d-d00b-4880-9111-9c305affc67b ro   quiet splash
initrd  /boot/initrd.img-2.6.31-20-generic

i have tried 

'nomodeset'
'nofb'
'i915.modeset=0' at various places
remove 'quiet'
put the 'nosplash' 'nomodeset'

and i still get the error. 

The /dev/fb0 is really not there, btw. I have tried to create it by 

mknod /dev/fb0 c 29 0 

which creted the file but after reboot it is not there anymore

MAKEDEV didn't work.

i have also tried this workaround 

cd /etc/init
sudo mv failsafe-x.conf failsafe-x.conf-disable
cd /etc/init.d
sudo mv failsafe-x failsafe-x-disable
but didn't work

Pleassse help

popolvar

---

### Post by popolvar on 2010-03-21
ok at the and of the it turned out that my xorg was broken

so i just had to run 

sudo apt-get install ubuntu-desktop

it restored the desktop and left all of my data and apps intact (as far i can tell of course)

this one also get me rid of the error, but upon this the desktop gui mode didn't start at all and i had only the console

cd /etc/init
sudo mv failsafe-x.conf failsafe-x.conf-disable
cd /etc/init.d
sudo mv failsafe-x failsafe-x-disable

when trying to fix the problem also set the correct framebuffer(FB) size as described in

[http://forums.debian.net/viewtopic.php?f=5&t=41881](http://forums.debian.net/viewtopic.php?f=5&t=41881)

post by jheaton5, but i doubt hat it had any relevance, as originally my FB was disabled

---

