---
title: "Upgrade failed"
date: 2005-10-14
forum: Installation &amp; Upgrades
---

### Post by Domhnull on 2005-10-14
I followed the instructions to upgrade Hoary to Breezy.  I had to try sudo apt-get -f install to fix issues along the way.  Eventually it seemed complete, everything looked updated.  I rebooted...

...and the system is dead. 

gdm won't start but I can't even get to a command line.  A blue screen (who decided to make it blue?) of death comes up saying that xserver isn't properly configured, do I want to see the logs, select <yes> or <no> - only I can't select either. Nothing happens.  I can't get to a prompt unless I boot to recovery mode.  But I'm afraid I don't know what to do to fix this.  

Any suggestions would be welcome.  Thank you.

---

### Post by meborc on 2005-10-14
reinstall from CD... srry to say this, but usually it is the simplest and the best solution... :???:

---

### Post by wezzer-foo on 2005-10-14
try pressing ctrl+alt+f6 to get text login (I'm not sure if that's the correct way to get there) and then insert command:
```
sudo dkpg-reconfigure xserver-xorg
```

And if you have ssh server installed, you can login from another machine and from there run that command.

Reinstalling from cd might _not_ be the best solution for this...

---

### Post by joselin on 2005-10-14
After reboot i had the same problem, but been solved after doing:

```
dpkg-reconfigure -a
```

---

### Post by Domhnull on 2005-10-14
Thanks for the suggestions.  Still not quite there.  I ran the dist-upgrade again - and it seemed that some packages hadn't updated.  After that I was able to reboot - but it just went straight to a command line.  I tried the dpkg-reconfigure commands but that didn't make any difference.

Plus, now the new kernel shows in grub but when I try to boot with it I get kernel panic.

I'd already backed up critical files.  I'm going to backup some non-critical files (music, etc.) and then just do a fresh install.  I'd hoped that the update would go smoothly, but no such luck.  I'll try a fresh install and if Breezy still won't work properly I'll just go back to Hoary.

---

### Post by wgscott on 2005-10-14
I've had this happen (apart from the Kernel panic) in the past, but not this time.  I avoided it I believe by issuing the following commands prior to reboot (I have an nvidia graphics card):

```

sudo apt-get install nvidia-glx
sudo apt-get install nvidia-settings
sudo nvidia-glx-config enable

```


I also found my upgrade/install using apt-get wasn't complete.  I used synaptic to finish the job, as it seemed better at resolving dependencies (and I am not a gui person).

---

### Post by Brunellus on 2005-10-14
probably that weirdo GPG error that's been bugging people lately

---

### Post by jnoreiko on 2005-10-14
I'm having the same problem exactly.


[QUOTE=joselin]After reboot i had the same problem, but been solved after doing:

```
dpkg-reconfigure -a
```[/QUOTE]

what does that command do?
I've run it and getting a LOT of questions I don't entirely understand.

EDIT: it's just frozen on "glide2 configuration".
It says "No 3Dfx card supported by glide 2 found!"
And there's a line overprinted on the screen: "syslogd: /dev/xconsole: no such file or directory"

---

