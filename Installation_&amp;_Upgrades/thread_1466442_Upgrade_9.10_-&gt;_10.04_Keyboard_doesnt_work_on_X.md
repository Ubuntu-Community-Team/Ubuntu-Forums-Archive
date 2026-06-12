---
title: "Upgrade 9.10 -&gt; 10.04: Keyboard doesnt work on X login anymore"
date: 2010-04-30
forum: Installation &amp; Upgrades
---

### Post by Mescaline on 2010-04-30
Hi there!

Just before Lucid was released, I installed karmic on a vanilla VM in 64-bit mode, and all was good.

Did a desktop setup and afterwards installed Eclipse, and I was happy: A new system for coding on-the-go!

Now, after upgrading to Lucid with do-release-upgrade -d, I can no longer enter my password on X login. The keyboard just doesn't work for some reason. When I enable the onscreen keyboard, and click my password, I can login.

The strange thing is that my keyboard works like a charm after I've logged into my X session?

Has anyone ever seen this, and even better, does anyone know a solution so I can enter my password using the keyboard again, instead of the mouse? ;)

---

### Post by madu on 2010-04-30
I have the same problem. I was using a USB wireless mouse and changed to a wired USB thinking that could be the problem. But still same problem.

My case is a little different. For me, the CTRL key is pressed. For example, when I type h in FireFox, it opens the history. So the CTRL is someho pressed. Strange thing is, this happens a while after I log in. 

Lucid screwed me up big..

---

### Post by robvas on 2010-04-30
I have a blue Apple keyboard connected to my Thinkpad T60, the G3/iMac style. It worked fine before, and now with 10.04 I have to disconnect/reconnect it once or twice to get the system to recognize it after rebooting. Noticed the same thing when I used the LiveCD.

---

### Post by anton_es on 2010-04-30
i have a dell laptop with logitech kb+mouse connected per usb. I have to unplug/plugin both to get any reaction from the loginscreen, very annoying.

---

### Post by OverloadBR on 2010-04-30
SOLUTION for Keyboard error

Boot with live distro before installing;
Setup your system then use the install option;
The new installation will work properly!

If you have installed 9.10 and upgraded it, just follow:
1) boot the 10.04 live;
2) mount your root filesystem (for ex: mount /dev/sda1 /media/tmp)
3) set your mounted partition as the main root filesystem with:
$ sudo chroot / /media/tmp
This will set the "/media/tmp" as your "/"
4) Edit your /etc/default/console-setup like
$ sudo gedit /etc/default/console-setup
Adjust the following:

XKBMODEL="pc105"
XKBLAYOUT="us"
XKBVARIANT=""
XKBOPTIONS=""

change "us" for your own language if desired...

Save changes and reboot your system.
Now it is ready to work!

---

### Post by Mescaline on 2010-05-01
This works for me, thanks a bunch! \\:D/

Should this be addressed as a bug, or is this expected behaviour?

---

### Post by Monkbel on 2010-05-01
console-setup solution doesn't help my case. still no keyboard on login.

The same issue is discussed here: [http://ubuntuforums.org/showthread.php?t=1466482](http://ubuntuforums.org/showthread.php?t=1466482)

---

### Post by Meghnaad on 2010-05-03
On My DELL Inspiron Desktop USB Key board and Mouse were not working .
I followed the steps which I mentioned in My blog
Link:
> [http://blog.ichinmay.com/2010/05/03/ubuntu-10-04-upgrade-from-9-10-usb-keyboard-mouse-problem/](http://blog.ichinmay.com/2010/05/03/ubuntu-10-04-upgrade-from-9-10-usb-keyboard-mouse-problem/)
Let me know if they were helpful
My Friend Dawood helped me to Solve this Problem,
I Just followed the Instructions.

---

