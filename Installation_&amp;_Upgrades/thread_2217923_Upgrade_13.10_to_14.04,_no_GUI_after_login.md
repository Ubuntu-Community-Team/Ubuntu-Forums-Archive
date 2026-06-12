---
title: "Upgrade 13.10 to 14.04, no GUI after login"
date: 2014-04-18
forum: Installation &amp; Upgrades
---

### Post by chernobyl2 on 2014-04-18
Under 13.10, I was using a dual-screen setup. After upgrading to 14.04, only one screen is active. After typing my password, the top bar and login options disappear but the "14.04 LTS" remains in the lower left corner of the screen and I am unable to access any GUI elements.

I am able to access a VT console (Ctrl+Alt+F1) and issuing "sudo service lightdm restart" does kick out a fresh login screen.

I am guessing the issue is with parts of the dual-monitor configuration. I set it up using the "Display" option in the system settings originally; now I can't access that since I have no GUI after login. Attempting to run GUI applications (e.g. update-manager) from a VT just gives an error (assert fails, and a core dump).

This is using an NVidia GeForce 6400 card. Running "sudo nvidia-xconfig" didn't do anything useful - it just created an identical clone of what became xorg.conf.backup during its operation.

Any suggestions, mighty Ubuntu community? It sounds like this might be the same problem as seen in this thread:

[http://ubuntuforums.org/showthread.php?t=2217735](http://ubuntuforums.org/showthread.php?t=2217735)

However, I don't have the luxury of a blank DVD or a /home partition so re-installing from scratch is going to be a major problem.

---

### Post by tekwizmailg on 2014-04-29
Hi Chernobyl2,

I am having the exact same problem, 'Dual Monitor Setup', 'NVidia GeForce GTX 650Ti', 'No GUI after logging in', and '14.04 LTS' in the lower left corner of the screen.
Unfortunatly, I don't have an answer to this problem. :(

I tried typing 'startx' in the tty1 console and managed to get an error as follows:
```
Loading extension GLX
modprobe: ERROR: ../libkmod/libkmod-module.c:809 kmod_module_insert_module() could not find module by name='nvidia_331'
modprobe: ERROR: could not insert 'nvidia_331': Function not implemented
```
I'm not sure what that means, but I will look it up and post if I find anything useful!

-RJ

---

### Post by tekwizmailg on 2014-04-29
I found an askubuntu post that I found helpful: [http://askubuntu.com/questions/130387/stuck-at-login-screen](http://askubuntu.com/questions/130387/stuck-at-login-screen)
(It's the third answer down)

I tried this command:
```
grep -e '(EE)' /var/log/Xorg.0.log
```
and received the same error messages as the answer at askubuntu had:
```
(EE) No devices detected.
(EE) Failed to initialize GLX extension (Compatible NVIDIA X driver not found)
```

It seems to be a problem with Xorg not being able to initiate a dual monitor setup with NVidia drivers. (Just a guess though)

I'll post again if I find anything else.

---

### Post by tekwizmailg on 2014-04-30
Ok, so here is what fixed it for me:

Download your drivers from NVidia's website: [http://www.nvidia.com/Download/index.aspx?lang=en-us](http://www.nvidia.com/Download/index.aspx?lang=en-us) (if you are using an NVidia graphics card that is)
It should be similar to: NVIDIA-Linux-x86_64-331.67.run
This may be more complex than it sounds if you you are unable to login. I had to installed xfce4 (a desktop manager).

After downloading is complete, restart your computer for good measure.

Before you login, enter your the terminal by pressing [ctrl]+[alt]+[f1].
Then log into the terminal with your username and password.

Now stop the X session using this command: sudo services lightdm stop

Now navigate to the download location of the .run file using 'cd' and 'ls' commands.

Now run the .run file using root privileges: sudo ./NVIDIA-Linux-x86_64-331.67.run

The NVidia installer should now be able to walk you through the installation process without problems. Remember to have the installer auto configure X (it should ask you in the process).

When the installer is complete, restart your computer using this command: sudo shutdown -r now

And everything should be good! It was for me at least! I hope this post will help future ubuntuers who have this problem! Good luck!

-RJ

---

### Post by tscloud on 2014-08-18
I had the same problem.  I have been using 14.04 for months w/ no issues.  I came home one day to find my Thinkpad w520 shutdown and it was not by me.  Very scary.

I booted and I got the ""14.04 LTS" remains in the lower left corner of the screen".  I switched to a virtual console and did "sudo startx".  After what seemed quite a while I got the same:

```

Loading extension GLX
modprobe: ERROR: ../libkmod/libkmod-module.c:809 kmod_module_insert_module() could not find module by name='nvidia_331'
modprobe: ERROR: could not insert 'nvidia_331': Function not implemented

```

I read previous posts in this thread and thought that nvidia-331 might be a problem do a I "sudo apt-get remove nvidia-331".  Reboot.  X started but w/ VERY low resolution.  I'm afraid I don't remember just how low.  It was using the Nouveau drivers.  I opened up Update Manager -> Additional Drivers and swithed to Nvidia 304 (nvidia-304, not ...-updates).  Rebooted and everything was back.  Went back and switched back to nvidia-331.38 (not ...-updates).  Rebooted.  Everything seems fine.

Don't know if this applies to this thread but the situation seems quite similar.  Suggestions above got me going on what I did so I am greatful.

---

