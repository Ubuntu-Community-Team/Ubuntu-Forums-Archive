---
title: "Server to GUI Upgrade"
date: 2014-06-05
forum: Installation &amp; Upgrades
---

### Post by jacob38 on 2014-06-05
I was able to get Ubuntu Server 13.1 on my Dell PowerEdge 1600SC; though, it was only the command line. I then used the steps provided here ([http://askubuntu.com/questions/53822/how-do-you-run-ubuntu-server-with-a-gui](http://askubuntu.com/questions/53822/how-do-you-run-ubuntu-server-with-a-gui)) and get the update and desktop files downloaded. Now my server has been sitting with a black screen for quite some time. The system sounds like it is very busy, but the screen is still black.

Is this normal?

---

### Post by jacob38 on 2014-06-05
OK, so I feel a little dumb. I hit the keyboard arrow keys and got the screen back...it seemed to be a console screen saver. The tasks were completed but still in command line mode. I sent the update command again to make sure it was all updated if any new updates were needed. As nothing else was happening I rebooted the system with the reboot command. The standard boot sequence started, linux stated, but now I am back to a black screen and hitting the arrow keys do not solve the problem, nor does moving the mouse.

...help please?

---

### Post by jacob38 on 2014-06-05
Now the monitor is saying the input signal is out of range....hmmmm

---

### Post by steeldriver on 2014-06-05
It may be a video driver issue - do you know what graphics card the machine has? Can you get a CLI login using Ctrl-Alt-F1 or Ctrl-Alt-F2?

---

### Post by jacob38 on 2014-06-05
Yes, I got to the CLI login with Ctrl+Alt+F1. I was able to login with the command line.

---

### Post by jacob38 on 2014-06-05
I also made sure that xorg was installed, it is installed and up to date...

---

### Post by jacob38 on 2014-06-05
Video Card: Embedded ATI Rage XL (8MB)

---

### Post by jacob38 on 2014-06-05
Nevermind, Ubuntu was not working...I have been trying for days and used so many different suggestions. I am sad to say but I am now going to use CentOS 6. It works right off the bat for the server without issues.

I still use Ubuntu for some other Industrial PC uses, but as for my server...CentOS 6 just won.

---

