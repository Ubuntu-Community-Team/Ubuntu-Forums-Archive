---
title: "Unable to Boot Ubuntu -- After Install"
date: 2007-07-05
forum: Installation &amp; Upgrades
---

### Post by Jeff Nyman on 2007-07-05
I apologize as there's a lot of detail here but I've tried to cover my bases before asking for help. I have browsed these fora and tried to find my own answers. So here's the situation.

I'm installing Ubuntu Linux. I finally got that to work. It wouldn't just install. It kept locking up on me. I had to go into a mode to change the boot string to say acpi=off. Anyway, finally got it installed.

So when I boot up, I get GRUB. No problem. I select Ubuntu Linux. (Kernel 2.6.20-15-generic) No problem. I get the Ubuntu message of "Starting up..." And then the Ubuntu graphic with the progress bar. And ... problem.

Nothing happens.

For a good two minutes. Then I get:

[COLOR="Blue"]BusyBox v1.1.3 (Debian 1:1.1.3-3ubuntu3) Built-in shell (ash)
/bin/sh: can't access tty; job control turned off
(initramfs)[/COLOR]

Now, I've seen all the things in this fora regarding how at least the slow startup is a known issue and it requires you to change your /boot/grub/menu.lst and add irqpoll.

That would be fine --- except, I can't do that from the prompt I'm left at. The directory doesn't exist and I can't issue any commands (like sudo or vi) anyway.

So the next bit of advice I found suggested that I should boot into the recovery mode of Ubuntu. So I did that. A bunch of stuff comes up as the system goes through its boot up.

I get a few [COLOR="blue"]ata3: failed to recover some devices[/COLOR] messages. Those seem to be related to the irqpoll issue (if I'm reading these fora correctly). But then it finally gets this:

[COLOR="blue"]Check root= bootarg cat /proc/cmdline
or missing modules, devices: cat /proc/modules ls /dev
ALERT! /dev/disk/by-uuid/..... does not exist. Dropping to a shell!
/bin/sh: can't access tty; job control turned off
(initramfs)[/COLOR]

The fora here suggest I should do this in relation to the above problem:

[COLOR="Green"]modprobe ide-disk
modprobe ide-generic
mount -t ext3 /dev/hda1 /root[/COLOR]

However, that doesn't work. I get:

[COLOR="Blue"]mount: Mounting /dev/hda1 on /root failed: No such file or directory[/COLOR]

So .... I'm not sure what else to try here. I can't seem to get into anything that lets me modify my boot string.

Anyone have any ideas? Hopefully I've provided enough information here. I tried to balance giving too much against not giving enough.

Any help would be appreciated and I'm happy to clarify if I've made anything here unclear.

- Jeff

---

### Post by Jeff Nyman on 2007-07-05
Well, update here. And, darn it, isn't it always that you find the obvious after you post?

I found on the boot menu (GRUB, that is) that I could modify the boot string. So I cliked 'e' to edit the line that boots Ubuntu. I then modified the kernel line with irqpoll.

I then booted and it worked fine. Then I was able to modify menu.lst directly. That seems to have done the trick.

I apologize as I probably could have figured this out before posting.

---

