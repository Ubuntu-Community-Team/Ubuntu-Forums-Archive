---
title: "Device not found, Grub Rescue, Post-Installation Error:"
date: 2010-05-19
forum: Installation &amp; Upgrades
---

### Post by webmanoffesto on 2010-05-19
Hello from a Noobie,

I just (for the first time ever) installed a version of Ubuntu. It is 10.04. I installed off of the Live Disk. I was having a great time until the first time I went to boot into it and I got the message 
"Error: No such device: "long number" 
Grub Rescue> "

I found some forum talk
[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/403408](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/403408)
and
[http://ubuntuforums.org/showthread.php?t=1301144](http://ubuntuforums.org/showthread.php?t=1301144)

But they are discussing a different version of Ubuntu.

Also, I booted again from the Live Disk and attempted to follow the instructions above
I tried to edit /usr/lib/grub/grub-mkconfig_lib . I tried to change line 147 (remove ALL the info from inside the quotes). 

I couldn't because I didn't have permission to modify the file. 

1. How do I get permission?
2. Do the instructions in the links above apply to 10.04?

Please help.

---

### Post by themusikid on 2010-10-27
*bump* I need the solution to this as well... anything?

---

### Post by drs305 on 2010-10-27
Take a look at this thread. It uses the command line but if you have problems understanding it just ask here or in that thread:

[Grub Rescue Prompt Megathread]("http://ubuntuforums.org/showthread.php?t=1594052")
To get to the command line, press "c"

If you want to try to 'wing it', you see a Grub menu during boot, and you know what partition it is installed on (sda1, sda5, etc):
Highlight the first entry.
Press "e" to edit the menu item.
Use the cursor and delete the entire "search" line.
On the linux line, change the part  "root=UUID=<uuid>" to "root=/dev/sdXY" with XY being your Ubuntu partition (sda1, sda5, etc)
Press CTRL-x to try and boot.

---

### Post by webmanoffesto on 2010-10-28
I switched to Puppy Linux and that worked great. Last week I successfully  installed Ubuntu, with no problems. I have no idea why it worked this time. Anyway, Puppy Linux was fun and I recommend trying that too [http://www.puppylinux.org/](http://www.puppylinux.org/) .

---

