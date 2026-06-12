---
title: "The volume 'Boot&quot; has only 0 bites disk space remaining"
date: 2014-10-22
forum: Installation &amp; Upgrades
---

### Post by Shoalster on 2014-10-22
I have the message :   The volume 'Boot" has only 0 bites disk space remaining 
                                I used the  "sudo apt-get autoremove"  command which was the instruction given to another in the forum with my identical problem and now my computer will not boot.   I get a black screen with white lettering and blinking cursor and the scroll lock and cap lock lights on the keyboard flash.  I took picture of lettering on the screen with my phone. If it can be of any use I could attach.

---

### Post by ajgreeny on 2014-10-22
There is no way that autoremove command could do that to your OS as far as I'm aware; I suspect there must be more to it than that, so use **Boot-Repair** from my signature (it runs in a live DVD or USB) and post back the link for the report it gives you.

There is no way, from what you have said so far, that we can help you out as we don't have anywhere near enough information.

By the way, do you have an encrypted system or one using LVM?  If not there is no advantage to having a separate /boot partition; quite the opposite as there are very many threads recently with exactly the same problem as you are seeing.

---

### Post by Shoalster on 2014-10-22
I know it wasn't a lot of information as far as the gibberish on my screen when I try to boot.  I was just posting exactly what happened after running the command.  When I upgraded to 14.04 I did a clean install wiping out Windows and followed the instructions at the time . Did not deliberately set up a / boot partition to my knowledge so must have been some default process.   Also, I searched other threads for my problem and that's where  I learned to run the command.    I didn't see anybody with the problem of not being able to boot after running the command and restart so I considered this a new thread. I'm no genius on this stuff so I'm sure some won't have the patience to bother with this.  I'll try the boot repair . If no progress I'll reinstall.   Thanks

---

### Post by ian-weisser on 2014-10-22
> **Shoalster said:**
> Did not deliberately set up a / boot partition to my knowledge so must have been some default process. 

A separate /boot is needed for optional LVM and/or encrypted installs.
Otherwise the default is _not_ a separate /boot.

If you search on the topic in this forum, you will quickly find how to fix your /boot problem...if you can boot.

When you followed the 'autoremove' advice (a link would help), exactly what happened? What did it do?

---

### Post by Shoalster on 2014-10-22
Link :  [http://ubuntuforums.org/showthread.php?t=2248846](http://ubuntuforums.org/showthread.php?t=2248846)     I typed the command into terminal , it did it's thing and instructed me to restart the computer.  I restarted the computer.  The obligatory HP screen appears for the normal 5 seconds then the HD reverts to no activity and the monitor goes to sleep mode.  If I hit the enter key I get a page as I described in post 1 .  It starts out :   un-block(0,0)    [ 0.5944569]  CPU: 1 PID: 1 Comm: swapper/0 Not tainted 3.13.0-37-generic #64-Ubuntu............followed by hardware name and then several rows of digits and letters most of which are F and zeros then a sequence of bracketed numbers that correspond with items such as : dump stack, panic, mount_block_root, prepare namespace, kernel_init_freeable      etc etc.     I can boot from live USB and that's all so if I can repair from that then good otherwise all is lost to a fresh install.

---

### Post by Shoalster on 2014-10-24
And thank you

---

