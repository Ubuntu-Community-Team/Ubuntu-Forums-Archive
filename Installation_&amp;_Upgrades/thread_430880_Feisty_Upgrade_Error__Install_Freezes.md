---
title: "Feisty Upgrade Error / Install Freezes"
date: 2007-05-02
forum: Installation &amp; Upgrades
---

### Post by munkie2 on 2007-05-02
Alright...I decided to upgrade to fiesty last night so I opened up update-manager and clicked on the Upgrade to Feisty Button(or whatever it says).  Everything went smoothly(all the upgrades were downloaded just fine) but when it came to the installation my whole computer froze with 5 minutes left(only like 50 or so packages left to install - and dont ask me why my computer froze, it has a history of doing that >.<).  Now these things happen:


****When I choose "Kernel 2.6.17-11-386" from grub I get this:

An Ubuntu loading screen but the bar never moves and nothing happens.

****When I choose "Kernel 2.6.17-11-386 Recovery Mode" from grub I get this:

(A bunch of loading text...)
Begin: Waiting for root file system... ...      (then after a short time)

Check root = boot arg cat /proc/cmdline
or missing modules, devices: cat /proc/modules ls /dev
Alert! /dev/disk/by-uuid/44549307-3bd2-4e48-49ece2ca5262 does not exist.  Dropping to a shell!

Busy Box v1.1.3 Built in Shell(ash)

Then I get a prompt

****When I choose "Kernel 2.6.17-10-386" from grub I get this:

An ubuntu login comes up(after the ubuntu loading screen) and I can log in.  However, when I hit enter to login I get to a beige screen then nothing happens.

****When I choose "kernel 2.6.17-10-386 Recovery Mode" from grub I get this:

I get a command line(with root privileges) but well, Im at a loss for what to do.


Thank you in advance for any help!

---

### Post by john.wheeler on 2007-05-04
I have the identical experience (and the same kernel versions). I managed to download all of the Feisty install files, but left the computer (a Dell D620 laptop) unattended for a couple of hours. When I came back, I couldn't boot.

Like you, I can get to a command shell in recovery mode with the 2.6.17-10 kernel but I don't know how to proceed from there. My instinct is to try to repeat the install from the command line, but I don't know how to do this. 

If you find out, I would very grateful if you could share the information; I'll do likewise!

Thanks,

John Wheeler
[email]john.wheeler.au@gmail.com[/email]

---

