---
title: "How to open sudoers file if operation not permitted"
date: 2014-10-14
forum: Installation &amp; Upgrades
---

### Post by andromeda2 on 2014-10-14
Hello, I'm a newbie Ubuntu user. I use Lubuntu desktop 14.04.1 64-bit as an guest OS on VMware Workstation.

I wrongly operate an tutorial to modify the usermod group. In the process, I execute this command:
```

sudo /usr/sbin/usermod -G svn andromeda
sudo /usr/sbin/usermod -G svn marc

```

** [FONT=fixedsys]andromeda[/FONT]** is my default user and [FONT=fixedsys]**marc** [/FONT]is my second user. Apparently,  since then, I can't access or doing anything with sudo command. The  terminal output is:
```
andromeda is not in the sudoers file. This incident will be reported.
```

I  have Googling and search the absolute way to fix it but the main and  crudest issue is: I still can't open the sudoers file using gksu or sudo  (which highly impossible). [This page]("http://askubuntu.com/questions/151200/my-main-username-is-not-in-the-sudoers-file") seems can help me but I still don't understand how to do that correctly while I can't open sudoers file or Root Terminal.

Is there any way to open sudoers file while the operation wasn't permitted?
Anyone can help me here?

Sorry for my bad english, bad question or mistakes. Any help would be very very appreciated.

Thank a lot in advance,
Andromeda

---

### Post by Lars Noodén on 2014-10-14
Have you tried this one?

[http://www.psychocats.net/ubuntu/fixsudo](http://www.psychocats.net/ubuntu/fixsudo)

---

### Post by andromeda2 on 2014-10-14
> **Lars Noodén said:**
> Have you tried this one?

[http://www.psychocats.net/ubuntu/fixsudo](http://www.psychocats.net/ubuntu/fixsudo)


Ok, I will try it but at the first, I need to know how to enter the Lubuntu in recovery mode on VMware Workstation just because the Grub screen doesn't displayed whenever my Lubuntu powered on. 

Anyway, thanks a lot for the answer.
Best regards!

Andromeda

---

### Post by Elfy on 2014-10-14
Press shift while it's booting - grub will show then.

---

### Post by andromeda2 on 2014-10-14
> **Elfy said:**
> Press shift while it's booting - grub will show then.

Actually, many posts are suggest me to do this but it always fail to enter the grub while hold the shift key. However, after trying at several times, it works and displays the Grub screen.

And **Lars Nooden**'s answer is absolutely working!

Thanks a lot to all for any attentions!

Best regards,
Andromeda

---

### Post by Elfy on 2014-10-14
You can set it so the grub shows by default, I do, though I have the time set for 2 seconds.  

```
# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.
# For full documentation of the options in this file, see:
#   info -f grub -n 'Simple configuration'

GRUB_DEFAULT=0
[COLOR="#0000CD"]#GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=2[/COLOR]
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
#GRUB_CMDLINE_LINUX_DEFAULT="quiet splash init=/lib/systemd/systemd "
#GRUB_CMDLINE_LINUX_DEFAULT="init=/lib/systemd/systemd "
#GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX_DEFAULT=""
GRUB_CMDLINE_LINUX=""
GRUB_DEFAULT=saved
GRUB_SAVEDEFAULT=true

# Uncomment to enable BadRAM filtering, modify to suit your needs
# This works with Linux (no patch required) and with any kernel that obtains
# the memory map information from GRUB (GNU Mach, kernel of FreeBSD ...)
#GRUB_BADRAM="0x01234567,0xfefefefe,0x89abcdef,0xefefefef"

# Uncomment to disable graphical terminal (grub-pc only)
#GRUB_TERMINAL=console

# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
#GRUB_GFXMODE=640x480

# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID=true

# Uncomment to disable generation of recovery mode menu entries
#GRUB_DISABLE_RECOVERY="true"

# Uncomment to get a beep at grub start
#GRUB_INIT_TUNE="480 440 1"
```

---

### Post by andromeda2 on 2014-10-14
> **Elfy said:**
> You can set it so the grub shows by default, I do, though I have the time set for 2 seconds.  

```
# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.
# For full documentation of the options in this file, see:
#   info -f grub -n 'Simple configuration'

GRUB_DEFAULT=0
[COLOR=#0000CD]#GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=2[/COLOR]
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
#GRUB_CMDLINE_LINUX_DEFAULT="quiet splash init=/lib/systemd/systemd "
#GRUB_CMDLINE_LINUX_DEFAULT="init=/lib/systemd/systemd "
#GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX_DEFAULT=""
GRUB_CMDLINE_LINUX=""
GRUB_DEFAULT=saved
GRUB_SAVEDEFAULT=true

# Uncomment to enable BadRAM filtering, modify to suit your needs
# This works with Linux (no patch required) and with any kernel that obtains
# the memory map information from GRUB (GNU Mach, kernel of FreeBSD ...)
#GRUB_BADRAM="0x01234567,0xfefefefe,0x89abcdef,0xefefefef"

# Uncomment to disable graphical terminal (grub-pc only)
#GRUB_TERMINAL=console

# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
#GRUB_GFXMODE=640x480

# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID=true

# Uncomment to disable generation of recovery mode menu entries
#GRUB_DISABLE_RECOVERY="true"

# Uncomment to get a beep at grub start
#GRUB_INIT_TUNE="480 440 1"
```


Thanks a lot, Elfy. It definitely worked.
Best regards,
Andromeda

---

