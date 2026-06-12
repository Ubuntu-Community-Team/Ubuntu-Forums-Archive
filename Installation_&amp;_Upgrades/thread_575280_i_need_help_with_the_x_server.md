---
title: "i need help with the x server"
date: 2007-10-13
forum: Installation &amp; Upgrades
---

### Post by dethzeppelinx on 2007-10-13
i have been having a problom witht he x server not starting or whatever and i have a nvidia graphics card people have givin me tips like 

* hit CTRL and ALT and F1. you enter the console -- if you are not already there.

* log in. If that would not work, check if you're having the righ tkeyboard layout (for example, the brakets are not there where you think they are or y and z are changed or so) just by typing characters like this in the prompt.

* type
sudo X --configure
and start the server like explained (probably
sudo X --config /root/xorg.conf.new
) If (and ONLY if) the dotty screen is visible and you can move the mouse, copy that file (/root/xorg.conf.new or so) to /etc/X11/xorg.conf AFTER YOU MADE A BACKUP OF THE OLD FILE!!):
sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf_old
sudo cp /root/xorg.conf.new /etc/X11/xorg.conf

* restart your X by typing
sudo /etc/init.d/gdm restart

* And in the future just use the STABLE ubuntu release. Even when gutsy is a release candidate, yes, it's a candidate.


but i have no clue what to do there so i was wondering im trying to install the driver for linux on my card but i dont know how can someone explain this to me this is getting very frusturating because i cant get into ubuntu at all and i have to do all the work from windows im running windows vista 32 bit can someone please help me and explain to me what to do thanks

---

### Post by Pumalite on 2007-10-13
When grub comes up select the second ubuntu option.

When its finished you should now have a terminal.

login

run sudo passwd

setup your 'root' password

now run

sudo apt-get install nvidia-glx-new

sudo nvidia-xconfig

sudo shutdown -r now

Then use the normal option to boot ubuntu.

Hopefully you'll have an xserver
__________________

---

### Post by dethzeppelinx on 2007-10-13
im using wuibi to install also and how do i know when grub comes up ?

---

### Post by Pumalite on 2007-10-13
Sorry, I don't know anything about wubi. Can't help you there.

---

