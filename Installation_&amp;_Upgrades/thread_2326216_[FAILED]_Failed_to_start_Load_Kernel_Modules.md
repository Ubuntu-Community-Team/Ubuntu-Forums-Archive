---
title: "[FAILED] Failed to start Load Kernel Modules"
date: 2016-05-29
forum: Installation &amp; Upgrades
---

### Post by francisco37 on 2016-05-29
I tried to upgrade my system from Ubuntu 14.04. My laptop froze for a few hours. Nor even the pointer did anything. So I switched off by pressing the power button for a few seconds.
This uncompleted installation is the origin of my problem.
When I reboot the system, grub appears and then, the following message:
```
[FAILED] Failed to start Load Kernel Modules
See 'systemctl status systemd-modules-load.service' for details
```
Plus some other lines that end with an _ 
[IMG]https://67.media.tumblr.com/c9c2dfd21e12c75b38e220c1d20b07f5/tumblr_o7ykwsCRmD1vw7tbzo1_540.jpg[/IMG]
When I open a command line by pressing CTRL+ALT+F1 I'm able to enter 
```
$sudo systemctl status systemd-modules-load.service
```
 and I get the following output:
[IMG]https://65.media.tumblr.com/c84aaa61501b7632326550c05debe7db/tumblr_o7yk1agEk01vw7tbzo1_540.jpg[/IMG]

If I repeat the systemctl command, I get sometimes other process instead of 179, for example, 183. 
Just in case it's needed,
```
$sudo ls /lib/systemd/system/systemd-modules-load.service
```
give me 
```
/lib/system/systemd-modules-load
```
(written in green)

```
journalctl
```
outputs a lot of data. The red lines are the following ones:
[IMG]https://66.media.tumblr.com/4329cf27584ff0c52da7053239165edb/tumblr_o7ymgsb44d1vw7tbzo1_540.jpg[/IMG]

[IMG]https://65.media.tumblr.com/a39a0bdfc5d59bd488492c94667542c5/tumblr_o7ymh5nYPL1vw7tbzo1_540.jpg[/IMG]

[IMG]https://66.media.tumblr.com/1f593d05614ac48fc9a969f18d9b788a/tumblr_o7ymhwo6kK1vw7tbzo1_540.jpg[/IMG]
I really appreciate a little bit of help here. I don't know what to do next and I've searched the web finding nothing.

P.D.: Sorry for the language, English is not my mother language. Besides I'm a newbie using the console.

---

### Post by kansasnoob on 2016-05-29
If you can boot into Recovery mode from the grub boot menu you might try what I said here:

[http://ubuntuforums.org/showthread.php?t=2318779&p=13466943#post13466943](http://ubuntuforums.org/showthread.php?t=2318779&p=13466943#post13466943)

You could try the same commands in a TTY using CTRL+ALT+F1 as you have been.

---

### Post by francisco37 on 2016-05-30
Thank you very much!
That solved my problem!
It was easier and less serious than I thought.
Thank you again kansasnoob.

---

