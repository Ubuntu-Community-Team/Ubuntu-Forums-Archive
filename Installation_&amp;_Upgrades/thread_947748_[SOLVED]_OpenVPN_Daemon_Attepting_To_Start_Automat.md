---
title: "[SOLVED] OpenVPN Daemon Attepting To Start Automatically"
date: 2008-10-14
forum: Installation &amp; Upgrades
---

### Post by sickanimations on 2008-10-14
So after a few hours (ok, about 10) I've installed OpenVPN, transferred my configuration from the previous windows-based OpenVPN server and got it working when I run it on a new Ubuntu installation.

The problem is that even though a daemon is installed and there's a initscript in /etc/rc2.d - OpenVPN's daemon isn't running after boot. Inspection of /etc/log/daemon.log indicates that the daemon doesn't even attempt to run.

What's wrong? What do I need to post?

Thanks :)

---

### Post by sickanimations on 2008-10-14
Oh and I should mention that I'm very new to Linux so don't hate on me. This is probably really simple to most people - confirming whether a process is being executed or not.

---

### Post by cariboo on 2008-10-14
You should have your openvpn start up script in at least run levels 2,3 and 5 in other words the script has to also be in rc3.d and rc5.d

See attached screenshot for runlevel info.

Jim

---

### Post by kevdog on 2008-10-14
I suggest if you want to add something to startup, do it the proper way using the update-rc.d utility: (Borrowed):



    You can use update-rc.d for start-only or stop-only scripts

    Start my script on startup :
    # update-rc.d -f my_script start 99 2 3 4 5 .

    where
    - start is the argument given to the script (start, stop).
    - 99 is the start order of the script (1 = first one, 99= last one)
    - 2 3 4 5 are the runlevels to start

    Dont forget the dot at the end
    More info in /etc/rcS.d/README

    Start my_script on shutdown and reboot :
    # update-rc.d -f my_script start 90 0 6 .

    Stop my_script on halt and reboot :
    # update-rc.d -f my_script reboot 90 0 6 .

    If you want to make your own demon, you can use the skeleton file provided at
    /etc/init.d/skeleton

    about runlevels :

    To know which runlevel you are running, simply type
    $ runlevel

    more info about runlevels here : [http://oldfield.wattle.id.au/luv/boot.html#init](http://oldfield.wattle.id.au/luv/boot.html#init)



This is proper way of doing it!!

---

### Post by sickanimations on 2008-10-15
Thanks for that. I am beginning to understand runlevels.

It turns out that the rc.d script was in 0, 2, 3, 4, 5 - after using -remove". Just re-added now, I'll let you know of the result.


[UPDATE]
Hooray, it works. Just checked /vars/log/daemon.log and it attempted to start. Even though it failed, this is a good thing. It only failed because I'm testing on wireless and the IP address hadn't been assigned yet. 

Thank you!

Solution:
[B]Start my script on startup :
# update-rc.d -f my_script start 99 2 3 4 5 .[/B]

---

### Post by sickanimations on 2008-10-15
Additional information for others having problems:

Even though the init scripts were S99, they weren't delayed enough to execute after DHCP IP address allocation so I used the command

**sleep 10**

at the top of the openvpn init script ( /etc/init.d/openvpn ) to give enough time. It worked.

This isn't a very elegant solution so if anybody has a better way, please let me know.

Regards.

---

