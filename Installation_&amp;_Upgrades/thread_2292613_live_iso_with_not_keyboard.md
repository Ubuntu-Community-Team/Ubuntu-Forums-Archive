---
title: "live iso with not keyboard ?"
date: 2015-08-29
forum: Installation &amp; Upgrades
---

### Post by Sandgoose on 2015-08-29
trying to boot the live usb on a system with no keyboard but Im just given the grub options screen that I am expected to select.


did a little searching and found [http://askubuntu.com/questions/47522/how-to-bypass-try-it-install-screen-when-booting-from-usb-live-session-wit](http://askubuntu.com/questions/47522/how-to-bypass-try-it-install-screen-when-booting-from-usb-live-session-wit) but it already seems to be out of date, config files seem to change syntax every single release


I edited it so grub.cfg only had one entry and it still waits for me to press enter :/

config looks something like

menuentry "balh" {
linux (kernel and parms)
initrd (init rd location)
}

works fine on a keyboard system but not sure what to add to make it boot right into this ?

Thanks

edit:nevermind searching more found I got past it by adding "set timeout=5" and "set default=0" above the menu entry

---

### Post by sudodus on 2015-09-01
I'm glad you found a solution :-)

Please click on **Thread Tools** at the top of the page and mark this thread as SOLVED, it will help other users (to find your solution).

---

