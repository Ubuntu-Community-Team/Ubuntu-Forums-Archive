---
title: "Unity lost after installing recommended Nvidia driver"
date: 2013-05-31
forum: Installation &amp; Upgrades
---

### Post by dckirba on 2013-05-31
Hello everyone,

Hope you're having a great day. I've just installed Ubuntu 13.04 on an older desktop that I have lying around the house. The computer has an older Nvidia card (Quadro FX 3000), and the recommended driver was the Nvidia 173 driver. Using Nouveau, the speed of compositing was just too slow. I went ahead and installed the driver under Software Sources, and ran nvidia-config. Upon reboot, I was presented with a login screen as usual, but after login I have only the wallpaper. I dug around a little and found this useful answer on askubuntu: [http://askubuntu.com/a/76951]("http://askubuntu.com/a/76951")

Unfortunately, my ttys are all garbled. The text is white on black and reversed. It still writes from left to right, but the characters are mirror images. Also, since the resolution is really low in the ttys, it's impossible to read what is happening. However, it is still possible to run commands, so I did. I was able to download and install ccsm, run it, and activate the Unity plugin.


[IMG]https://dl.dropboxusercontent.com/u/5934612/Nvidia%20Pains/Screenshot%20from%202013-05-31%2016%3A38%3A06.png[/IMG]


I restarted the computer, but still just a wallpaper. I am able to access a terminal with Ctrl-Alt-T, and then run programs from there. That's how I'm using Firefox right now. But there is no Unity, and no window manager.


[IMG]https://dl.dropboxusercontent.com/u/5934612/Nvidia%20Pains/Screenshot%20from%202013-05-31%2016%3A19%3A47.png[/IMG]


[IMG]http://db.tt/rRCp9Eet[/IMG]

I tried restarting Compiz from the terminal with ```
dconf reset -f /org/compiz/
``` followed by ```
unity --reset-icons &disown
```. The second command spits out a lot of information and then ends with a segmentation fault. (file attached) [ATTACH]243330[/ATTACH]

I've kind of reached my wit's end on this one guys. I've tried all the solutions I could find on the net and narrowed the problem down to Unity+Nvidia, but am not sure what my next steps should be. Should I just install another desktop manager, maybe plain gnome3 or Xubuntu, and give it a try? I'd really like to get Unity to work if possible.

Thanks in advance for your time and help,

Cheers,
David

Update: I have also tried the workaround posted here: [https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/1166765]("https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/1166765") with no results.

---

### Post by dino99 on 2013-05-31
hi David,
i wonder if running nvidia-config is a good idea nowadays, as the kernel directly deals with X; that said, delete xorg.conf to see if its better.
Have you tried to login with Gnome (aka gnome-shell) instead of unity (ubuntu) ? you'll get quite the same feeling with less headaches ):P

---

### Post by dckirba on 2013-05-31
Hi dino,

Thanks for your time. Initially, I installed the driver and did not run nvidia-xconfig. I just rebooted and tried nvidia-settings, but it said I wasn't using the driver. So I ran nvidia-xconfig and things were fine except for Unity missing.

I did just try installing gnome-shell. I was asked to choose between lightdm and gdm, so I chose gdm during the install process. I rebooted only to find that I was stuck at a resolution too high for my monitor so had to go into one of the ttys. This is a new install so I'm currently in the process of wiping the slate clean again and see if I can do this cleaner. I'll post back in an hour or so if I run into new issues :)

Thanks again,
David

---

### Post by hydrodog on 2013-06-01
I am just having the same problem, and though I didn't have the same problem with unreadable terminals, it is very frustrating.

FIrst thing I can suggest is ctrl-alt-f1, f2, etc.  which gives you a text terminal that you can type commands into.

---

### Post by dckirba on 2013-06-01
Thanks hydrohog,

I'm away from the desktop for the weekend, but I have found some promising links that may help you too. By the way, it is the text terminals that are unreadable for me :( The only way I can work around that is by choosing recovery mode and then resuming boot from the grub menu. Here are the links. I hope one works for you:

[http://askubuntu.com/questions/202574/desktop-does-not-show-when-i-installed-nvidia-drivers]("http://askubuntu.com/questions/202574/desktop-does-not-show-when-i-installed-nvidia-drivers")
[http://ubuntuforums.org/showthread.php?p=12303179#post12303179]("http://ubuntuforums.org/showthread.php?p=12303179#post12303179")
[http://falkvinge.net/2013/02/15/how-to-install-nvidia-drivers-in-ubuntu-12-10-quantal/]("http://falkvinge.net/2013/02/15/how-to-install-nvidia-drivers-in-ubuntu-12-10-quantal/")

Let me know if something works for you :) Have a great weekend,

David

---

### Post by dckirba on 2013-06-15
Well guys, I had a chance to sit down and try some of the solutions I mentioned in my prvious post. Unfortunately, none of them work for me. Does anyone know of any other solutions that I have missed? 

Thanks in advance,
David

---

