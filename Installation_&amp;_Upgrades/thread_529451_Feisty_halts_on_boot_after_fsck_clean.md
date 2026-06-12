---
title: "Feisty halts on boot after fsck clean"
date: 2007-08-19
forum: Installation &amp; Upgrades
---

### Post by lispy on 2007-08-19
This is quite a showstopper. I am trying to install Feisty on my moms PC. Never had it fail for me before. But on this machine it installs just fine, once I reboot it hangs after the fsck (it drops from splashscreen to prompt). 

No verbose errors sadly. I am kinda stuck. It's an 80GB Maxtor IDE-HD wich I partitioned fully for Feisty. 80GB OS, 2GB swap. Any ideas?? I hit a wall. ;-/

---

### Post by hailtothethief on 2007-08-21
I just finished dealing with a problem like this a few minutes ago.

First, check the fsck log file since it isn't giving you verbose errors:
```
sudo nano /var/log/fsck/checkfs
```

If you get an error whining about not being able to resolve UUID [big long string of text] then find the actual UUIDs of your system.

```
blkid
```

Write down the UUIDs that are spit out.


Now backup and edit your fstab file
```
sudo cp /etc/fstab /etc/fstab.bak
sudo nano /etc/fstab
```

And check to make sure that the UUIDs line up for each partition. If not, manually imput them.

Also check to make sure that the partitions listed in /etc/fstab match the partitions listed in blkid. If there is an extra partition listed in /etc/fstab, put a '#' (minus quotes) at the beginning of the line(s) that shouldn't be there.

Also check your grub boot list to see if any UUIDs incorrect:

```
sudo cp /boot/grub/menu.lst /boot/grub/menu.lst.bak
sudo nano /boot/grub/menu.lst
```

That solved my problem, and I actually didn't have to go as far as editing the grub list, I just had to comment out an entry in /etc/fstab that didn't actually exist.

If that seems to screw something up, or not do anything at all, run the following to restore your files:

```
sudo cp /etc/fstab.bak /etc/fstab
sudo cp /boot/grub/menu.lst.bak /boot/grub/menu.lst
```

Good luck!

---

### Post by lispy on 2007-08-27
Sorry, I didn't see your post as of today. I will try and reply asap when I get home today.

---

### Post by lispy on 2007-08-27
ok, just tried your advice. But everything looks good. All UUIDs are correct and blkid gives the same values as in fstab or menu.lst.

I wonder if it's related to fsck at all. The logfile just says: "Nothing has been logged". And the fsck on bootup seems to finish fine. Maybe the process AFTER fsck fails me? Any idea what starts up after fsck?

---

### Post by lispy on 2007-08-28
ok, I did something ugly that fixed it: I had an old Feisty alpha CD lying around. I installed it using this one and it worked. Don't asked me why. Just upgrading to feisty final. 

Strange, indeed.

---

### Post by lispy on 2007-08-28
Great, after installing the updates to make it a stable feisty I get the exact same behaviour. No boot after fsck. No errors. No nothing. Weird. And frustrating.

---

### Post by dabl on 2007-08-28
You say it goes to a blank screen with a prompt?  Have tried Alt-F1 at that point?

---

### Post by lispy on 2007-08-29
You mean ctrl+alt+f1?
Or what is Alt+F1 supposed to do? It's not a login shell if that's what you were hoping. :)

It's just the fsck clean...[OK] notice and then nothing else...

---

### Post by Preserved Killick on 2007-08-30
Hi, Lispy.

I am watching this thread carefully because I'm seeing something similar (and sadly, not because I can help you much...).  I'd done an upgrade from edgy to feisty and during the first boot I had to do a forced fsck.    Then the boot sequence got hung up just after this:

... * Running local boot scripts (/etc/rc.local)                      [ OK ]
Timidity is not yet configured.
Enable Alsa Sequencer first by editing /etc/default/timidity.
_

...and it just sits like this.  I can't get a login prompt using alt-F[12345] or buy using cntrl-alt-F[12345]

I'm also having problems with GDM-- if you think it will help us figure this out I can post that error, but in my limited experience, this is a problem I can solve by running the script 'envy' for NVIDIA drivers, if I could only get to a login.

I hope someone here knows what to try.

-- Killick

---

