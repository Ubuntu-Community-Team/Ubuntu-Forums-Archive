---
title: "monitor out of range"
date: 2010-02-12
forum: Installation &amp; Upgrades
---

### Post by 1993gandy on 2010-02-12
hi i got a copy of ubuntu 9.10 desktop edition in the post today and i tried installing it. i can select language and it shows the menu for installing "try ubuntu without installing etc." but when i say install or try then it comes up with a s***load of code and its not on the screen for very long and then when it goes my monitor says "frequency out of range" what do i have to do so that i can install it.
my specs. are:
asrock k7vm2 mobo
amd duron 1.8GHz
1gb kingston ram
nvidia 7200gs 256mb
neoview (idk what model)

the person that i got this computer from said that ubuntu works and i know that it does on this computer because i been on it when he had this pc with ubuntu, the only problem is that he doesnt remember what he did to get it working on it :(

---

### Post by tommcd on 2010-02-12
When you boot the live CD you should get this screen:
[https://help.ubuntu.com/community/BootOptions#Main%20Start%20Page%20Options](https://help.ubuntu.com/community/BootOptions#Main%20Start%20Page%20Options)
First, choose the option: "check disc for defects" and let that run. This will check all the files on the CD. If it does not pass, then the CD is bad and you will need to burn a new one.

Assuming the check passes and the CD is good, then boot the live CD again and hit F6 for Other Options. Then type vga=771 as discussed here:
[http://ubuntuforums.org/showthread.php?t=1306976&page=2](http://ubuntuforums.org/showthread.php?t=1306976&page=2)
If vga=771 does not work, then try the other vga= options listed there.
If that does not work, then try switching between analog and digital cables if you have them available as discussed in that thread. Or perhaps, if all else fails, try a different monitor. Your nvidia graphics card should work ok, so Ubuntu is likely having trouble autodetecting your monitor.

And welcome to the Ubuntu forums!

---

