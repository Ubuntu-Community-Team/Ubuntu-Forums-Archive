---
title: "Brightness and startup setting problems"
date: 2013-04-18
forum: Installation &amp; Upgrades
---

### Post by chessmate on 2013-04-18
Hello,

I decided to migrate a few weeks ago and even though I have some stability issues, which is something I did't have before, I am glad I had done that step forward.
I will appreciate a lot your help if you give me a hand with this:

 - First of all I have a dim problem and the brightness of my screen is always at its maximum no matter what I do. Here I copy some output that my terminal gives me:

username@computersname-MacBook:~$ ls /sys/class/backlight
apple_backlight
username@computersname-MacBook:~$ lsmod | grep video
uvcvideo               72249  0 
videobuf2_core         32212  1 uvcvideo
videodev              100265  2 uvcvideo,videobuf2_core
videobuf2_vmalloc      12757  1 uvcvideo
videobuf2_memops       13213  1 videobuf2_vmalloc
username@computersname-MacBook:~$ cat /proc/cmdline
BOOT_IMAGE=/boot/vmlinuz-3.5.0-27-generic root=UUID=5f59014a-f5f9-4946-986d-652003df4751 ro quiet splash vt.handoff=7
username@computersname-MacBook:~$ sudo nano ect/default/grub
the file does not exist

 - Second, When I startup my laptop either my bluetooth as my wireless are turned on automaticly. If I turn them off before I restart the computer they show on once restarted and I have no idea why.


Thank you for your help in advance.!!! I truly appreciate it.

chessmate

---

