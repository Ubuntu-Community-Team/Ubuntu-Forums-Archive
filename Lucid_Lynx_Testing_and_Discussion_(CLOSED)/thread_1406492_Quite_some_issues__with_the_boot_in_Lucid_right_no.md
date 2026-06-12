---
title: "Quite some issues  with the boot in Lucid right now"
date: 2010-02-14
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by gjoellee on 2010-02-14
(This post gets updated)
Does anyone else have the same issues or is it only me?


[LIST]
[*]Plymouth appears for less than 0,5 sec during boot, or it show up but seams to "freeze" until GDM loads.
[*]GDM freeze about 50% of the time, making me not able to log in.
[*]Looks like it takes about 15 sec for KMS to kicks in.
[*]Sometimes the wireless drivers fails to load. It can be solved by reboot, but it is really annoying.
[*]GDM sometimes fail to load, sometimes it loads just fine.
[/LIST]

---

### Post by Anduu on 2010-02-14
I have a couple of issues of my own.
[LIST]
[*]I haven't been able to boot to a desktop normally for some time now.The process just hangs with no errors.I have to boot in recovery mode and start GDM from there.

[*]If a scheduled disk check of my /home partition occurs during boot Plymouth exits almost immediately and GDM starts up.If an attempt is made to log in Gnome barfs as it cannot access the home directory.
[/LIST]

---

### Post by dino99 on 2010-02-14
on my end, boot is ok till login. Then desktop appear with some icons but without the top task bar, i have to wait (can't do anything else anyway !!!) about 10 seconds to get this task bar on top and the one at bottom to.

---

### Post by amsterdamharu on 2010-02-14
First time install I've had some problems, also booting the live live CD. I forgot what it was but switching to tty1 it said something about not being able to boot or something. After a while it continued booting.

After install from live CD desktop item "install ...." and updating there have been no problems at all. Everything worked out of the box without tweaking and gksu gedit stuff.

I use a Hasee Q130W laptop.

---

### Post by glasen on 2010-02-14
> **gjoellee said:**
> [*]Plymouth appears for less than 0,5 sec during boot, or it show up but seams to "freeze" until gdm loads.
For me it is 3s but it takes about 10s before the logo is showing up.

> [*]GDM freeze about 50% of the time, making me not able to log in.
Are you sure the system is completely freezed? There is a bug with "hdparm" which causes a 15-30s hang on system startup. After this time the harddisk gets reseted and the system starts up normally. Adding "nohdparm" to line "GRUB_CMDLINE_LINUX_DEFAULT" in the file "/etc/default/grub" might help.

> [*]Looks like it takes about 15 sec for KMS to kick in
See above. Seems to be a bug with Plymouth.

> [*]Sometimes the wireless drivers fails to load. It ca be solved by reboot, but it is really annoying.
Works perfectly for me. Must be an driver problem with your wireless card.

---

### Post by gjoellee on 2010-02-14
> **Anduu said:**
> I have a couple of issues of my own.
[LIST]
[*]I haven't been able to boot to a desktop normally for some time now.The process just hangs with no errors.I have to boot in recovery mode and start GDM from there.
[*]If a scheduled disk check of my /home partition occurs during boot Plymouth exits almost immediately and GDM starts up.If an attempt is made to log in Gnome barfs as it cannot access the home directory.
[/LIST]


Got the same thing :D

> **dino99 said:**
> on my end, boot is ok till login. Then desktop appear with some icons but without the top task bar, i have to wait (can't do anything else anyway !!!) about 10 seconds to get this task bar on top and the one at bottom to.

Got that issue with the panel as well. It takes some time for it to load.

> **glasen said:**
> For me it is 3s but it takes about 10s before the logo is showing up.


Are you sure the system is completely freezed? There is a bug with "hdparm" which causes a 15-30s hang on system startup. After this time the harddisk gets reseted and the system starts up normally. Adding "nohdparm" to line "GRUB_CMDLINE_LINUX_DEFAULT" in the file "/etc/default/grub" might help.


See above. Seems to be a bug with Plymouth.


Works perfectly for me. Must be an driver problem with your wireless card.

I will try the hdparm thingy...maybe I can boot up without using recoverymode to be sure it works!

Actually, I have not seen the driver issue lately, but I cannot yet confirm it is solved as I have not been able to use Ubuntu for a while this week because of xorg issues.

And actually I have found one more issue. System seams to kind of freeze if I enter the system menu (Using Gnome Main Menu, and a custom theme, is that has something to do with it). Nothing happens...cannot even move the cursor, but notify-osd still works....!

---

### Post by dino99 on 2010-02-14
"Actually, I have not seen the driver issue lately, but I cannot yet confirm it is solved as I have not been able to use Ubuntu for a while this week because of xorg issues."

i'm having this since 1 or 2 weeks now with "sevenmachine ppa" package:

(WW) Open ACPI failed (/var/run/acpid.socket) (No such file or directory)

---

### Post by amsterdamharu on 2010-02-14
[U][U]Thanks gjoellee, just ruined my perfect desktop experience :). Plymouth isn't working here too. I didn't even know what it was and what is was supposed to do. But I am luckier than you with my hardware and get my login within 15 seconds of choosing what kernel to boot so never gave it any thought.


[/U][/U]

---

### Post by gjoellee on 2010-02-14
> **amsterdamharu said:**
> [U][U]Thanks gjoellee, just ruined my perfect desktop experience :). Plymouth isn't working here too. I didn't even know what it was and what is was supposed to do. But I am luckier than you with my hardware and get my login within 15 seconds of choosing what kernel to boot so never gave it any thought.


[/U][/U]

My boot time is still normal (not an extra 15sec), it is just weird...:p

---

### Post by guyster on 2010-02-14
My boot experience is OK with Lucid, but I'm having an interesting issue that I really hope I can fix soon as it is really weird.  Any time I press the enter key, whether it be to a password prompt, in the terminal or what have you, my system simply freezes with no return.  If I use mouse clicks, or shift+tab to OK and press spacebar, I can get through.  Any suggestions for a work around?  I used the CD image from yesterday to do my install.  Thanks much for any help.


Guy

---

### Post by dino99 on 2010-02-14
when your system freeze can you check htop or nothing at all ?

---

### Post by Anduu on 2010-02-14
> **dino99 said:**
> when your system freeze can you check htop or nothing at all ?

In my case when boot hangs all TTY's are blank with flashing cursor.Attempting to return with F7 produces a blank screen as well.Sometimes Ctrl+Alt+Delete will reboot but frequently a hard reset is required.

> Are you sure the system is completely freezed? There is a bug with "hdparm" which causes a 15-30s hang on system startup. After this time the harddisk gets reseted and the system starts up normally. Adding "nohdparm" to line "GRUB_CMDLINE_LINUX_DEFAULT" in the file "/etc/default/grub" might help.


On a couple of occasions I have left it sit for > 15 minutes.Boot never finishes.

---

### Post by Didius Falco on 2010-02-14
> **guyster said:**
> My boot experience is OK with Lucid, but I'm having an interesting issue that I really hope I can fix soon as it is really weird.  Any time I press the enter key, whether it be to a password prompt, in the terminal or what have you, my system simply freezes with no return.  If I use mouse clicks, or shift+tab to OK and press spacebar, I can get through.  Any suggestions for a work around?  I used the CD image from yesterday to do my install.  Thanks much for any help.


Guy

That's part of the error in plymouth at the moment. See this thread: [http://ubuntuforums.org/showthread.php?t=1401805](http://ubuntuforums.org/showthread.php?t=1401805)

and this bug report: [https://bugs.launchpad.net/ubuntu/+source/plymouth/+bug/516412](https://bugs.launchpad.net/ubuntu/+source/plymouth/+bug/516412)

One way around it is to just remove plymouth until they get it fixed:

```
sudo apt-get remove plymouth
```

You'll find a different way to get past it in those two threads, but since it's just a workaround and not a fix, I prefer to just install it again when they update it.

Regards,

Didius

---

### Post by gunnar123 on 2010-02-15
I manually installed this plymouth version and this got rid of my problem, see:
[http://ohioloco.ubuntuforums.org/showthread.php?p=8829081#post8829081](http://ohioloco.ubuntuforums.org/showthread.php?p=8829081#post8829081)

---

