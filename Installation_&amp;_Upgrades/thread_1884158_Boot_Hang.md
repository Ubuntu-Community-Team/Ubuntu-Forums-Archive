---
title: "Boot Hang"
date: 2011-11-20
forum: Installation &amp; Upgrades
---

### Post by svtguy88 on 2011-11-20
Alright,
I've got a problem that I had originally thought was video related, but now I'm thinking otherwise.

My system hangs on boot.  It stops at the purple-ish screen that follows the Grub menu.  If I boot with the Grub splash screen disabled, the last line of ouput says something to the effect of "/dev/sdc1 re-mounted.  Opts: error=remount-ro" and then it hangs.

If I boot with rescue mode, I'm able to get to the desktop.  I've already cleaned unfinished package installs and tried deleting the /var/ureadahead/pack file, as suggested online, but I get the same result.

Also, I edited the Grub options to boot rescue mode without the "nomodeset" flag, just to test if it is something video related, and the system booted fine, so video isn't the issue...

Ideas?

---

### Post by MAFoElffen on 2011-11-20
> **pkmgarf said:**
> Alright,
I've got a problem that I had originally thought was video related, but now I'm thinking otherwise.

My system hangs on boot.  It stops at the purple-ish screen that follows the Grub menu.  If I boot with the Grub splash screen disabled, the last line of ouput says something to the effect of "/dev/sdc1 re-mounted.  Opts: error=remount-ro" and then it hangs.

If I boot with rescue mode, I'm able to get to the desktop.  I've already cleaned unfinished package installs and tried deleting the /var/ureadahead/pack file, as suggested online, but I get the same result.

Also, I edited the Grub options to boot rescue mode without the "nomodeset" flag, just to test if it is something video related, and the system booted fine, so video isn't the issue...

Ideas?
Could you post the results of 
```

lspci -vnn | grep VGA

```and your /etc/default/grub file?

---

### Post by svtguy88 on 2011-11-20
lspci:

```
pat@PowerEdge1800:~$ lspci -vnn | grep VGA
07:05.0 VGA compatible controller [0300]: ATI Technologies Inc Radeon RV100 QY [Radeon 7000/VE] [1002:5159] (prog-if 00 [VGA controller])
	Flags: bus master, VGA palette snoop, stepping, medium devsel, latency 32, IRQ 17
```

grub config:

```
GRUB_DEFAULT=0
GRUB_HIDDEN_TIMEOUT=5
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT=
GRUB_CMDLINE_LINUX=

# Uncomment to enable BadRAM filtering, modify to suit your needs
# This works with Linux (no patch required) and with any kernel that obtains
# the memory map information from GRUB (GNU Mach, kernel of FreeBSD ...)
#GRUB_BADRAM="0x01234567,0xfefefefe,0x89abcdef,0xefefefef"

# Uncomment to disable graphical terminal (grub-pc only)
#GRUB_TERMINAL=console

# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
GRUB_GFXMODE=1024x768

# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID=true

# Uncomment to disable generation of recovery mode menu entries
#GRUB_DISABLE_RECOVERY="true"

# Uncomment to get a beep at grub start
#GRUB_INIT_TUNE="480 440 1"
```

I've made a few small changes to the /etc/default/grub file, but nothing too major, I don't think.

I should also mention that my was (accidentally) using the Precise PPA for an update.  I had enabled Precise's PPA to install an updated version of Pithos, but forgot to comment it out.  I updated via Update Manager a few days later (yesterday).  I've since disabled the PPA.

However, my problems were exactly the same before the update...

---

### Post by MAFoElffen on 2011-11-20
> **pkmgarf said:**
> lspci:

```
pat@PowerEdge1800:~$ lspci -vnn | grep VGA
07:05.0 VGA compatible controller [0300]: ATI Technologies Inc Radeon RV100 QY [Radeon 7000/VE] [1002:5159] (prog-if 00 [VGA controller])
    Flags: bus master, VGA palette snoop, stepping, medium devsel, latency 32, IRQ 17
```grub config:

```
GRUB_DEFAULT=0
GRUB_HIDDEN_TIMEOUT=5
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT=
GRUB_CMDLINE_LINUX=

# Uncomment to enable BadRAM filtering, modify to suit your needs
# This works with Linux (no patch required) and with any kernel that obtains
# the memory map information from GRUB (GNU Mach, kernel of FreeBSD ...)
#GRUB_BADRAM="0x01234567,0xfefefefe,0x89abcdef,0xefefefef"

# Uncomment to disable graphical terminal (grub-pc only)
#GRUB_TERMINAL=console

# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
GRUB_GFXMODE=1024x768

# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID=true

# Uncomment to disable generation of recovery mode menu entries
#GRUB_DISABLE_RECOVERY="true"

# Uncomment to get a beep at grub start
#GRUB_INIT_TUNE="480 440 1"
```I've made a few small changes to the /etc/default/grub file, but nothing too major, I don't think.

I should also mention that my was (accidentally) using the Precise PPA for an update.  I had enabled Precise's PPA to install an updated version of Pithos, but forgot to comment it out.  I updated via Update Manager a few days later (yesterday).  I've since disabled the PPA.

However, my problems were exactly the same before the update...
Okay... I'm testing Precise... Right not up on Solaris 11. Let me start up one of my Precise test boxes...

Yes there was xserver and OpenGL updates in Precise.  You may have to ensure your sources are straightened out, then reinstall Xserver and OpenGL. from the onieric repo's.  Because they are most certainly more recent shema wise, you may have to do the reinstall by remove / install.

What video driver are you using with that?

---

### Post by svtguy88 on 2011-11-20
I'm using the radeon driver. When I use the recovery mode, X starts perfectly fine, running at my normal resolution. 

 Also, I understand that some updates that got done could potentially cause problems, however, I had the exact same issues while using strictly Oneiric software.

---

### Post by theoldmaster on 2011-11-20
I've been having the same problems. I unplugged my cd drive and now it boots fine, still looking for my solution though.
Sata HDD     ide cd drive.

---

### Post by MAFoElffen on 2011-11-20
> **pkmgarf said:**
> I'm using the radeon driver. When I use the recovery mode, X starts perfectly fine, running at my normal resolution. 

 Also, I understand that some updates that got done could potentially cause problems, however, I had the exact same issues while using strictly Oneiric software.
I have an idea... In your /etc/default/grub file, line 19, where you have:
```

GRUB_GFXMODE=1024x768

``` 
Please change it to:
```

GRUB_GFXMODE=1024x768x24

```
then update grub...

---

### Post by svtguy88 on 2011-11-21
I actually tried putting that line in there to try and *help* the problem.  I do remember reading that some people had luck with appending the color bit-depth.  Ill give it a try in the morning.

That said, I still fail to understand why using rescue mode works.  As far as I can tell, everything is the same in rescue mode (once booted to the desktop).  What exactly does rescue mode do, other than give you a menu to enter a shell, clean packages, etc.?  The only differences in the Grub entry (that I see, when hitting "e" on the Grub menu to edit) between rescue mode and non-rescue mode are the following options:  rescue, nomodeset. That, and the linux grahics payload line is missing in the rescue mode entry...other than that, the look the same...so why does rescue mode boot?

If X starts in rescue mode perfectly fine (1440x900 and glxinfo shows DRI), isn't my issue likely non-graphics related?  Still, I'll try adding "x24" or "-24" (as I read that worked for some) to my Grub entry tomorrow morning when I can take the system down.

---

### Post by svtguy88 on 2011-11-21
Ok.  I changed the GRUB_GFXMODE line to include the color depth, but I get the same result.

What I did realize, however, is that by adding the "recovery" flag to the non-recovery boot entry, I can force the system to boot.  By adding "recovery" the system prompts me with the recovery menu.  If I select "remount file system as r/w" it completes this and asks me to push enter, putitng me back at the recovery menu.  If I then select "resume normal boot" the machine boots successfully.  

However, if I do NOT first remount the filesystem as r/w, and just seletc "resuem normal boot" the system hangs at the same place as it does without booting with the "recovery" flag.

I'm lost...I mean, I can get the system to boot, but why only after remount the filesystem using the recovery menu?

---

### Post by mike0042 on 2011-11-23
I'm seeing the same problem. Added the following to end of /etc/default/rcS so I could log in from my laptop and diagnose:

> (
/bin/sleep 10
/sbin/ifconfig eth0 192.168.11.3 up
/bin/mkdir /var/run/sshd
/usr/sbin/sshd
) >/dev/null 2>&1 &

Looking at lsof output I see the following line:

> mountall  363  root   11r      REG                0,3        0     263 /proc/359/mountinfo

This is odd because process 359 no longer exists. Need to try and track what it was. Also, strace on the mount all process shows the following:

> Process 363 attached - interrupt to quit
select(13, [3 4 6 7 12], [], [3 11 12], NULL

So it looks like mountall is stuck in a select() call. I added the --verbose option to mountall in /etc/init/mountall.conf but that doesn't seem to provide any additional information. Also did a touch of /forcefsck which still exists. Still confused myself.

---

### Post by MAFoElffen on 2011-11-23
> **pkmgarf said:**
> Ok.  I changed the GRUB_GFXMODE line to include the color depth, but I get the same result.

What I did realize, however, is that by adding the "recovery" flag to the non-recovery boot entry, I can force the system to boot.  By adding "recovery" the system prompts me with the recovery menu.  If I select "remount file system as r/w" it completes this and asks me to push enter, putitng me back at the recovery menu.  If I then select "resume normal boot" the machine boots successfully.  

However, if I do NOT first remount the filesystem as r/w, and just seletc "resuem normal boot" the system hangs at the same place as it does without booting with the "recovery" flag.

I'm lost...I mean, I can get the system to boot, but why only after remount the filesystem using the recovery menu?
I'm still researching this for you. Digging through the recovery-mode recovery-menu scripts and the runlevel scripts to see what I can come up with.

---

### Post by fdrake on 2011-11-23
> **pkmgarf said:**
> Ok.  I changed the GRUB_GFXMODE line to include the color depth, but I get the same result.

What I did realize, however, is that by adding the "recovery" flag to the non-recovery boot entry, I can force the system to boot.  By adding "recovery" the system prompts me with the recovery menu.  If I select "remount file system as r/w" it completes this and asks me to push enter, putitng me back at the recovery menu.  If I then select "resume normal boot" the machine boots successfully.  

However, if I do NOT first remount the filesystem as r/w, and just seletc "resuem normal boot" the system hangs at the same place as it does without booting with the "recovery" flag.

I'm lost...I mean, I can get the system to boot, but why only after remount the filesystem using the recovery menu?

can you post your fstab
```

less /etc/fstab

```
also try to boot unplugging any usb device and check if that is the problem.

---

### Post by MAFoElffen on 2011-11-24
> **MAFoElffen said:**
> I'm still researching this for you. Digging through the recovery-mode recovery-menu scripts and the runlevel scripts to see what I can come up with.

Okay... a few things for you to try-

1. Add "xforcevesa" to the kernel boot parameters. 

2. Reboot the computer forcing fsck to eval (repair if needed) the filesystem on the subsequent boot:
```

shutdown -rF now

```

---

### Post by svtguy88 on 2011-11-24
I'm away from the system right now for the Thanksgiving holiday.  I'll try what you suggested and post my /fstab.

That said, I ran an update (don't worry too much - my software sources are all back to Oneiric), and a fresh kernel image got installed.  I tried booting the machine (not in recovery) and I got different results than before.  I don't recall exactly the errors, but I will repost later tonight or tomorrow.

---

### Post by MAFoElffen on 2011-11-24
> **pkmgarf said:**
> I'm away from the system right now for the Thanksgiving holiday.  I'll try what you suggested and post my /fstab.

That said, I ran an update (don't worry too much - my software sources are all back to Oneiric), and a fresh kernel image got installed.  I tried booting the machine (not in recovery) and I got different results than before.  I don't recall exactly the errors, but I will repost later tonight or tomorrow.
Happy Thanksgiving.

---

