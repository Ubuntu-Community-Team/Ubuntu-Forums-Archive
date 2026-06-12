---
title: "Can't get Ubuntu 16.04 TLS (or any other linux) to run on this system - Help!"
date: 2017-11-24
forum: Installation &amp; Upgrades
---

### Post by thefoolisme on 2017-11-24
Hi there, 

I've got an old PC with an ASUS A8N-SLI Premium motherboard, an AMD X2 4800+ chip, and two NVIDIA graphics cards in SLI.  It's an old desktop I've been using as a file/print server for a while, first with Windows Home Server, then with Windows Home Server 2011. 2011 doesn't play nice with Windows 10, so I figured I would change it over to Ubuntu. I have desktop experience, and thought the server would be a good project.  I got the Server version to install, but upon reboot, it won't start.

I did some basic research, and it seems the Nouveau drivers may be the culprit, but I haven't been able to figure out how to fix it. I even downloaded CentOS and SUSE just for giggles to see if they had an issue, and they all seem to get hung in the same place.

Does anyone have any thoughts on how to fix this? Photo attached of the monitor screen.

 [ATTACH=CONFIG]277652[/ATTACH]

---

### Post by ubfan1 on 2017-11-24
You're probably right it's a graphics driver problem -- when you boot, you should get a grub menu, but if you don't (because there is only one OS on the machine), then hold down a key like shift or maybe tab to force grub to show up.  There are instructions at the bottom of the grub screen for editing (type e), then use the arrow keys to go to the line starting with "linux" and replace the "quiet splash" words with "nomodeset".  Then type F10 or ctrlX to boot (again instructions at the bottom of the screen) and see if that gets you running.  Now a server does not have a gui interface, so may a light weight desktop like lubuntu might be better.

---

### Post by thefoolisme on 2017-11-24
"Quiet Splash" isn't in my grub edit screen. Not sure why it's not, because I see the Quiet Splash comment in the forums for this, but it isn't. Maybe I can add the entire code in there to negate it, but I would need to know the whole thing and where to put it.

I know the server doesn't have a GUI, which was why I chose it to try to avoid this issue, but it is still there. Any other thoughts? 

Thanks.

---

### Post by VMC on 2017-11-25
Whats the output of journal:
```
journalctl -p err -b
```

---

### Post by thefoolisme on 2017-11-25
Here's my boot script, and the journal response.

[ATTACH=CONFIG]277660[/ATTACH][ATTACH=CONFIG]277661[/ATTACH]

---

### Post by ubfan1 on 2017-11-25
add the nomodeset before the "ro" and after the "root=UUID..." on the linux line.  Forget the "quiet splash", they are not needed, and suppress the startup progress and error messages anyway.

---

### Post by thefoolisme on 2017-11-25
OK. Thanks! That got me to the login prompt.  :-)

Now, I'm afraid to screw this up. I just ran updates successfully.   How do I keep "nomodeset" in the bootscript so it doesn't crash every time there is a reboot? Any suggestions? I'm going to try to install a light GUI too.

---

### Post by ubfan1 on 2017-11-25
Put the nomodeset into the file /etc/default/grub on the line GRUB_CMDLINE_LINUX_DEFAULT="nomodeset"

---

### Post by thefoolisme on 2017-11-25
OK. That works. I'm good, and I installed a lubuntu desktop and it still works.  

Thanks!!!!

---

