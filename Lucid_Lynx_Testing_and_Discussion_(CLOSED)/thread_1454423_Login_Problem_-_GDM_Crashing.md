---
title: "Login Problem - GDM Crashing"
date: 2010-04-14
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by The Real Dave on 2010-04-14
A login problem for me, first real problem in Lucid. Did an apt-get upgrade and apt-get dist-upgrade yesterday, and now, I get to the login screen, click my username (up to which point everything works perfectly), and then it freezes, and crashes. The screen goes black, and the login screen restarts itself.

Selecting "Other" is fine, up until it asks for a password. Typing the username works, but when you hit enter, the password dialog appears, but it freezes right away, and restarts again. 

Can anyone help with this, or point me in the right direction? Do I need to report it on Launchpad?

---

### Post by ranch hand on 2010-04-14
Can you boot through recovery?

---

### Post by The Real Dave on 2010-04-14
Yup, and when I hit "Resume Boot", I get a regular console.

I should have mentioned, that when I reach the GDM Login, I can switch to a console, and login there, so presumably not a permissions problem.

Up until the point when I click on the username, everything's fine. When it should allow me to enter in my password though, it freezes, and then seems to restart GDM.

---

### Post by Arand on 2010-04-14
When running a development release, you should report bugs whenever possible.
For more details see: [https://help.ubuntu.com/community/ReportingBugs](https://help.ubuntu.com/community/ReportingBugs)

A quick search for "login gdm lucid" in launchpad brings these bugs:
[https://bugs.launchpad.net/ubuntu/+source/gdm/+bug/526379](https://bugs.launchpad.net/ubuntu/+source/gdm/+bug/526379)
[https://bugs.launchpad.net/ubuntu/+source/gdm/+bug/516520](https://bugs.launchpad.net/ubuntu/+source/gdm/+bug/516520)

Check if any of them apply, and if so, see if you can provide the requested information.

Another thing worth trying is starting in recovery mode from the grub menu (hold shift on boot to show it if you don't already). And choose failsafe X/gnome from the menu presented there. And see if this works.

The logs located at ~/.xsession-errors* and /var/log/gdm/* might be of interest to narrow down the issue.

 - Arand

---

### Post by ranch hand on 2010-04-14
If the bugs linked by Arand do not fit just run;
```

ubuntu-bug gdm

```
This will collect info from your box and send it to LP.  You will need to login or get an account (easy).  Make sure the bug is marked as public so others can join the FUN (unless your password is included in any of the attached files).

If your password is included I would mark it as public and change the password.

---

### Post by The Real Dave on 2010-04-14
It seems to be this bug.

[https://bugs.launchpad.net/ubuntu/+s...dm/+bug/526379](https://bugs.launchpad.net/ubuntu/+s...dm/+bug/526379)

Or at the very least similar. As far as I can tell, it's an Xorg problem >.<

I've added a comment to the bug, along with my .xsession-errors, /var/log/gdm/:0-greeter.log.1 and /var/log/Xorg.0.log.old.

Thanks for your help guys :)

---

### Post by Arand on 2010-04-14
From the errors in your logs, it does not look related to that bug.
I would say report a new bug, describe it well, and attach the files there.

Just as a side note. this looks like it may be the point of interest in your case:> (...)
(II) No input driver/identifier specified (ignoring)

Backtrace:
0: /usr/bin/X (xorg_backtrace+0x3b) [0x80e937b]
1: /usr/bin/X (0x8048000+0x61c7d) [0x80a9c7d]
2: (vdso) (__kernel_rt_sigreturn+0x0) [0x66f410]
Segmentation fault at address (nil)

Caught signal 11 (Segmentation fault). Server aborting

Please consult the The X.Org Foundation support 
	 at [http://wiki.x.org](http://wiki.x.org)
 for help. 
Please also check the log file at "/var/log/Xorg.0.log" for additional information.

(II) Power Button: Close
(...)

Also, from the .xsession-errors, it seems like it's trying to start openbox and conky, is that really as it should be?> (...)
Conky: desktop window (43) is root window
Conky: drawing to desktop window
Conky: drawing to double buffer
Openbox-Message: Unable to find a valid menu file "/var/lib/openbox/debian-menu.xml"
Openbox-Message: Unable to find a valid menu file "debian-menu.xml"
(...)
Again, I do believe you should report a separate bug, since thie issue might be similar when it comes to symptoms, but the cause very different.

---

### Post by The Real Dave on 2010-04-14
> **Arand said:**
> From the errors in your logs, it does not look related to that bug.
I would say report a new bug, describe it well, and attach the files there.

Just as a side note. this looks like it may be the point of interest in your case:
Also, from the .xsession-errors, it seems like it's trying to start openbox and conky, is that really as it should be?
Again, I do believe you should report a separate bug, since thie issue might be similar when it comes to symptoms, but the cause very different.

Yup, Openbox and Conky are correct. I run an Openbox desktop instead of Gnome in Lucid. Those messages from Conky and Openbox AFIK are normal, at least, I believe that they're the same on other Openbox desktops I've set up. 

However, if you believe I should, I will report a new bug. Thanks for the advice.

---

### Post by jrothwell97 on 2010-04-14
If you're using the nvidia-96 driver, it's [this bug here](https://bugs.launchpad.net/bugs/553200) in the upstream driver that's causing GDM to crash.

---

### Post by The Real Dave on 2010-04-14
Yup, I'm using the 96 driver, and that appears to be it alright. Thank you :)

---

### Post by Arand on 2010-04-14
EDIT: I was wrong here, ignore.

Once again, comparing the Xorg.0.log it does not look related, since in the logs at [https://bugs.launchpad.net/bugs/553200](https://bugs.launchpad.net/bugs/553200) does not show the crash yours do...

- Arand

---

### Post by The Real Dave on 2010-04-15
If you don't mind, can you show which part is different? I can't seem to find it. Cheers.

---

### Post by Arand on 2010-04-15
Ah, ignore last post, I must've confused the Xorg logs there for a while, I though that none of the logs attached to the bug had the backtrace of yours, but it seems they do have (well at least the ".old" one), huh, I must be getting old and going blind.

And the backtrace is exactly similar, so yes, my guess it's very likely that very issue.

Seems like they've got a hunch on how to fix it.

For the time being, I guess that reverting to nouveau might be desirable (seeing as how you are unable to get into gnome at all at the moment, if I've undestood things correctly):
> **Technoviking said:**
> (...)
2) Open the terminal and type the following commands:
```
sudo update-alternatives --config gl_conf
```
(and select the alternative provided by mesa)
```
sudo ldconfig
sudo update-initramfs -u
sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf_old
```

and restart your computer.
(...)Hopefully these instructions should be follow-able from the recovery mode root shell, or a chroot. Drop the sudo if you are already root.


 - Arand

---

### Post by The Real Dave on 2010-04-20
This issue has since been fixed. 

See [Launchpad #553200]("https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-96/+bug/553200") for the details and the fix :)

Marking as solved. Thanks to those who tried to help here :)

---

