---
title: "Skip grub OS selection screen"
date: 2011-02-17
forum: Installation &amp; Upgrades
---

### Post by gofurygo on 2011-02-17
Hello

Im using the following system setup:

When I boot my business computer, I can choose between 3 setups, 2 Windows XP, 1 DOS. I installed Ubuntu with 1 Windows XP system which looks something like this:

System 1 (XP)
System 2 (XP) --> after selection, Im able to choose between the XP system and Ubuntu on a new screen
System 3 (DOS)

Now interesting for me is obviously System 2. After I select System 2, I can choose between XP and Ubuntu. After I select Ubuntu, I come to another screen, where I can choose again between 4 Ubuntu entries with different kernel versions (including their recovery modes) AND both XP systems (yes, again).

I installed Grub Customizer. I removed all the XP entries and all but 1 Ubuntu entry from this screen. I also set the timeout until booting Ubuntu on this screen to 1 second to start as quick as possible and Ubuntu boots fine.

My question now is, is there a way to skip the screen with former kernel and XP selection and boot Ubuntu directly after already choosing (between XP and Ubuntu) on the first screen? I know, 1 second "waiting" is not too bad:D but skipping the screen completly would be superb. I played with Grub customize, but cant seem to find the appropriate setting... Hope you guys can light me up...

Thanks in advance

---

### Post by sikander3786 on 2011-02-17
I think you've installed Ubuntu inside Windows using the Wubi installer.

Please post the complete output of this command.

```
cat /etc/default/grub
```

---

### Post by bcbc on 2011-02-17
This link shows how to hide grub when it detects a multi-os situation. But it's not recent and grub has changed a bit, so the scripts may look a little different.

[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:hide_menu:](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:hide_menu:)

You want to be careful - not hiding it - but deleting older kernels from the grub menu. They're useful if you have a problem booting the current kernel.

---

### Post by gofurygo on 2011-02-17
Sikander:

Yes you are absolutely right, I used the wubi installer. Here is the output you asked for:
```
# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.

GRUB_DEFAULT="0"
GRUB_HIDDEN_TIMEOUT="0"
GRUB_HIDDEN_TIMEOUT_QUIET="true"
GRUB_TIMEOUT="1"
GRUB_DISTRIBUTOR="`lsb_release -i -s 2> /dev/null || echo Debian`"
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""

# Uncomment to enable BadRAM filtering, modify to suit your needs
# This works with Linux (no patch required) and with any kernel that obtains
# the memory map information from GRUB (GNU Mach, kernel of FreeBSD ...)
#GRUB_BADRAM="0x01234567,0xfefefefe,0x89abcdef,0xefefefef"

# Uncomment to disable graphical terminal (grub-pc only)
#GRUB_TERMINAL="console"

# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
#GRUB_GFXMODE="640x480"

# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID="true"

# Uncomment to disable generation of recovery mode menu entries
#GRUB_DISABLE_LINUX_RECOVERY="true"

# Uncomment to get a beep at grub start
#GRUB_INIT_TUNE="480 440 1"

GRUB_SAVEDEFAULT="false"
```bcbc:
thanks for the link...this looks promising ;)

---

