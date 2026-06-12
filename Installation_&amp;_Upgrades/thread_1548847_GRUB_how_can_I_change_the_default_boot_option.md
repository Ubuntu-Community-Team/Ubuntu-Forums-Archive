---
title: "GRUB: how can I change the default boot option?"
date: 2010-08-09
forum: Installation &amp; Upgrades
---

### Post by zenthor on 2010-08-09
Greetings community,

I just got to finish installing ubuntu lastest version on my new netbook, im really exited about how powerful it can get.

The thing is, I'm still keeping my old Windows 7 partition and data, and I want to access it faster, so, I was wondering if someone could please guide me and help me editing the grub options, to change the timer on it, and the default booting option, I would really appreciate it.

Kind regards,

Steve

---

### Post by sikander3786 on 2010-08-09
Hi.

Install StartUpManager.

```

sudo apt-get install startupmanager

```

[https://help.ubuntu.com/community/StartUpManager](https://help.ubuntu.com/community/StartUpManager)

You can toggle between default operating system, timeout and much more.

Regards.

---

### Post by zenthor on 2010-08-09
okey, great, I'm rusty at this, its been a while since the last time I used ubuntu so I didnt knew there was an application for it, I remember before we had to edit a file, thanks a lot! I'll give this a try in a moment!

---

### Post by garvinrick4 on 2010-08-09
```
gksudo gedit /etc/default/grub
```That code puts you in root so you can change and save. Be careful and focus.

I at times seem to have problems after I change to 800x600 rather than default with startup manager.
You can change grub_timeout here and the resolution. Sometimes or most times with startup manager I change the grub_cmdline_linux-default="quiet splash" by using the GUI startup manager package. Instead  just changing this file and sudo update-grub when through always clean for me. Here is what mine looks like that works fine. Change yours to fit your needs. I do believe going over 800x600 in grub_gfxmode seems to get to small a font in grub menu, for me anyway.

# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.

GRUB_DEFAULT=0
#GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""

# Uncomment to disable graphical terminal (grub-pc only)
#GRUB_TERMINAL=console

# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
GRUB_GFXMODE=800x600

# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID=true

# Uncomment to disable generation of recovery mode menu entries
#GRUB_DISABLE_LINUX_RECOVERY="true"

# Uncomment to get a beep at grub start
#GRUB_INIT_TUNE="480 440 1"

---

### Post by zenthor on 2010-08-09
great, both of you guys options work perfectly, I'm really thankful.

Just one little thing more. Between the options, a non existant OS appears on the list, a Windows Vista, how can I deleat this entry? its the last one on my list.

Thanks in advance.

---

### Post by oldfred on 2010-08-09
Grub's osprober finds the recovery partition and in most cases even with newer XP installs the recovery partition is seen as a Vista install.

I do not know of just a command to edit it out. You can copy the windows entry you want to keep into 40_custom and turn off the osprober so it does not find/duplicate your windows entries.

I used drs305's command to limit ubuntu entries to two, turned off os_prober so it does not look for other systems and totally customized my 40_custom.
Copy the window entry you want to keep from this:
gedit /boot/grub/grub.cfg
Copy them to and edit :
gksudo gedit /etc/grub.d/40_custom

includes line to limit display to two
Grub 2 Title Tweaks Thread -drs305
[http://ubuntuforums.org/showpost.php?p=8082954&postcount=1](http://ubuntuforums.org/showpost.php?p=8082954&postcount=1)

I added this :
gksudo gedit /etc/default/grub
GRUB_DISABLE_OS_PROBER=true
or
sudo chmod a-x /etc/grub.d/30_os-prober

---

### Post by Cavsfan on 2010-08-09
Check out the Tutorial in my signature. It makes the GRUB2 menu maintenance free.
You never have to touch it every time a new kernel is installed.

It also shows how to set up a custom native monitor resolution wallpaper background for GRUB2. 
I have mine looking pretty slick! :D

It is mentioned at the end of **drs305**'s tutorial and shows how to just have 2 lines (Ubuntu only) or 3 lines (dual booting windows).

---

