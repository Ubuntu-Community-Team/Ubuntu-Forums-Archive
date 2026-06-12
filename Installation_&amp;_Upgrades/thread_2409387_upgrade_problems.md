---
title: "upgrade problems"
date: 2019-01-01
forum: Installation &amp; Upgrades
---

### Post by heatopher2 on 2019-01-01
Hello, I've just upgraded from ubuntu 16.04 to 18.04, and had a bit of a hairy experience doing it, to be honest. Everything was ticking along as normal during the download and install part, until the process just froze, saying that there was a problem with the existing grub file, which is just one that gives me the choice between Ubuntu or Windows. It just hung for a very long time, and I had no idea what to do. I guess I should have written to you guys, but didn't think about it. In the end, I just stopped things, which I realise is probably the worst thing i could do.

At first I actually thought that I'd lost everything, as I got a really basic prompt upon rebooting, but finally I got onto a recovery process, and was pleasantly surprised to find the system up and running eventually. But no doubt a few things didn't install properly, and I'm generally worried of course that it might be unstable. I've run sudo apt-get update and upgrade, but I suppose there are still a few other steps that I could take to check that everything is in the right place. Is there a way to check for broken and/or missing packages?

At login, I get a prompt saying "No symbol table. Press any key to continue." Pressing any key boots things up fine, but is there any way to get rid of that message? I'm supposing that it's something to do with the GRUB file? I tried following the suggestions here, 

[https://askubuntu.com/questions/837035/no-symbol-table-press-any-key-to-continue/837421](https://askubuntu.com/questions/837035/no-symbol-table-press-any-key-to-continue/837421)

but still getting that message :confused:

The one other annoying aesthetic problem that I've got is that I can't get the workspace switcher grid to work. Installed the unity tweak tool, enabled workspaces, set the number I want (6x6), but that doesn't work. I also put that setting into CompizConfig Settings Manager, as suggested in this thread:

[URL="https://askubuntu.com/questions/819585/workplace-switcher-stopped-working-in-ubuntu-16-04"]https://askubuntu.com/questions/819585/workplace-switcher-stopped-working-in-ubuntu-16-04
[/URL]
but that doesn't do the trick either. All help appreciated! Thanks very much in advance :)

---

### Post by clementc on 2019-01-01
Hi [**heatopher2**]("https://ubuntuforums.org/member.php?u=2055648"),

[FONT=arial]You mentioned that you tried following the suggestions from [here]("https://askubuntu.com/questions/837035/no-symbol-table-press-any-key-to-continue/837421"), can you please confirm that you tried the grub-install and update-grub commands?
[SIZE=3]
[/SIZE][/FONT]If yes, and if your system is configured to use (U)EFI rather than legacy BIOS, could you please try running the following command and remove any obsolete entries: sudo efibootmgr (please see [this page]("https://askubuntu.com/questions/63610/how-do-i-remove-ubuntu-in-the-bios-boot-menu-uefi/63613#63613") for more information on how to remove old entries).

Please note that modifying GRUB or the UEFI bootloader always puts you in a situation where your system wouldn't boot at all if something goes wrong. Please only follow these instructions if you feel comfortable doing so and after you have backed up all important data.

Regarding checking for broken/missing packages, I would try the following:
```
sudo apt update
sudo apt upgrade
sudo apt dist-upgrade
sudo apt autoremove
sudo apt autoclean
```

Regarding the workspace grid switcher, you mentioned [this page]("https://askubuntu.com/questions/819585/workplace-switcher-stopped-working-in-ubuntu-16-04"), can you please confirm that you have tried all solutions offered there? If not, what have you already tried?

---

### Post by heatopher2 on 2019-01-02
Hi again!

One thing at a time. I'll deal with the GRUB stuff first...

I did update-grub, but not grub-install. I've tried that just now on the disk where the grub file is, and I get this:

```
sudo grub-install /dev/sdb
Installing for i386-pc platform.
grub-install: warning: this GPT partition label contains no BIOS Boot Partition; embedding won't be possible.
grub-install: error: embedding is not possible, but this is required for cross-disk install.

```

I also tried it on the partition where (I guess, looking at gparted information) grub is installed, but nothing happens with that.

```
sudo grub-install /dev/sdb2
[sudo] password for kizza: 
Installing for i386-pc platform.
grub-install: error: unable to identify a filesystem in hostdisk//dev/sdb; safety check can't be performed.
```

To explain what's going on, precisely.... I've got a dual-boot system, with Windows and Ubuntu. Both Windows and Ubuntu are on the primary SSD, and because the Windows MBR takes over the whole boot process, I followed some clever advice, and put the grub file on the  storage hard drive. Everything was working fine before this upgrade, and I have no idea why the upgrade process would have been so bothered about it. This is what the /etc/default/grub/grub.cfg file looks like (I don't really remember how the Windows dual-boot part of it all works - is that somewhere else?):

```
# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.
# For full documentation of the options in this file, see:
#   info -f grub -n 'Simple configuration'

GRUB_DEFAULT=0
GRUB_TIMEOUT_STYLE=hidden
GRUB_TIMEOUT=200
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""

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

Sorry, I forgot about this part:

```
sudo efibootmgr
[sudo] password for kizza: 
EFI variables are not supported on this system.
```

I had already tried that, I think....

As for the other stuff.... I've run all those update and upgrade commands, so let's see....

And for the workspace switcher, yes, I've tried everything on that post!

---

### Post by clementc on 2019-01-02
Hi  				 				 					 						 	[**[COLOR=#000000]heatopher2[/COLOR]**]("https://ubuntuforums.org/member.php?u=2055648"),

Assuming that /dev/sdb is your storage hard drive, GRUB should be installed on /dev/sdb and not /dev/sdb2 according to what you mentioned above.

Then your BIOS should be configured to boot from the storage hard drive first, so that GRUB can take precedence over Windows bootloader located on your SSD drive.

Can you please also advise if your BIOS is configured to boot using UEFI or the legacy BIOS system?

Finally, you can use command "sudo dpkg-reconfigure grub-pc" to tell the system where you want grub's MBR code installed.

Once your booting issue is resolved, we can look at the remaining issues.

---

### Post by heatopher2 on 2019-01-13
Hellooo, sorry for the delay.

Yes, it's UEFI. I remember sorting that out when I did the initial dual-boot installation.

I've just run "sudo dpkg-reconfigure grub-pc", and what happened was that it seemed not to be working first time, but then it actually finished its business the second time. I took screenshots second time round, but I can't access them now, because...... they would be in my home directory, which I can't get to right now, as GRUB isn't working. This is what I'm seeing when I boot from sdb:

```
error: file '/boot/grub/i386-pc/bufio.mod' not found
Entering rescue mode
grub rescue > _
```

And of course I don't know what to do! Fortunately I'm not completely without computer access, as I am booting Windows from sda. So grateful that the initial setup was a sensible one.

---

### Post by heatopher2 on 2019-01-20
Hi, please forgive the BUMP, but nobody replied, and for the time being I can't get onto Ubuntu at all, for obvious reasons!!!

---

### Post by heatopher2 on 2019-02-04
Hello, my thread seems to have fallen down/through a wormhole here. I  have been too busy to research very much by myself, so would appreciate a  little help in getting things going again :D

---

### Post by heatopher2 on 2019-03-08
Hi, just wondering if anyone is replying on this forum any more! I wrote the posts above two months ago, and never heard anything back. Of course I can try another forum, but I'm assuming that this should be the number one place for what I'm trying to sort out :confused::)

---

