---
title: "Gutsy First Update"
date: 2007-12-31
forum: Installation &amp; Upgrades
---

### Post by rcparmar on 2007-12-31
Morning.

I've been running feisty for some time - quite happily so. Yesterday, I decided to do a fresh install of gutsy. I preserved the old partitions (/home and /data) but chose to reformat /.

The installation went fine - though after reboot, I noticed that I didn't see the orange progress bars before the login screen appeared (in fact my monitor complained about getting a signal with too high a refresh rate). I ignored that.

I logged in and update manager stated that there were about 149 updates available, so I let update-manager download the packages. This is where the trouble started. 

After about downloading 15 packages, update-manager froze - in fact it more than froze. The entire machine was dead - no hard drive activity, no caps-lock button light, nothing. I ended up pulling the plug. I tried a few more times and in each case the update manager would pick up downloading the files from where it had left off, download a few packages and then just die again. I gave up last night whilst it was trying to download a new kernel.

I had installed some new memory - so I forced a full bios memory test - which came up with ok. Whilst booting, I tried ctrl-alt-f1, and noticed that there was a warning about ACPI. Thinking that power management might be an issue, I disabled power management in the bios and rebooted. I left the machine on for some time with a screen saver running, and all appeared well. So, there appears to be something awry with update-manager.

Does anybody have any ideas?

Thanks

---

### Post by rcparmar on 2007-12-31
update: sorted out the loading screen not displaying - I updated /etc/usplash.conf which referenced the screen as being 1280x1024 - changed it to 1024x768. I had to run

sudo update-usplash-theme usplash-theme-ubuntu

as per [http://ubuntuforums.org/showthread.php?t=579596&page=2](http://ubuntuforums.org/showthread.php?t=579596&page=2)

With regard to the more fundamental problem of update-manager not working, I've tried doing this:

sudo apt-get --reinstall install update-manager-core update-manager

but it still hangs.

BTW, where does gutsy cache the packages on the hard drive?

Any help out there?

---

### Post by rcparmar on 2008-01-02
The plot thickens ...

I decided that perhaps there was something wrong with the update-manager front end, so I thought I'd give apt-get a go:

sudo apt-get clean
sudo apt-get update

and then I issued lots of 

sudo apt-get --reinstall install <package name>

where <package name> was the name of each package identified by update-manager.

Now for small packages this appeared to work a treat, though when I let it loose on larger packages e.g. openoffice.org, whilst **downloading** the package the machine in its entirity would hang - needing a hard reboot. Is there something wrong with apt-get ? or atleast the part of it which is responsible for networking?

I have to say, this is the first ubuntu installation that I've had problems with an I'm rather disappointed. Things just worked before.

---

