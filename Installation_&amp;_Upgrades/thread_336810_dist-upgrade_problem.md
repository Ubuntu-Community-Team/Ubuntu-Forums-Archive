---
title: "dist-upgrade problem"
date: 2007-01-12
forum: Installation &amp; Upgrades
---

### Post by BKK on 2007-01-12
Hi, I hope some one is able to help me out. 

I am most familiar with doing things the graphical way so here's what I have done

-click the little icon to update
it then says I need to do a dist-upgrade
-click the dist-upgrade button
i then get this error:
Could not calculate the upgrade etc etc...
here is the /var/log/dist-upgrade info...

apt.log

Starting
Starting 2
Investigating nvidia-glx
Package nvidia-glx has broken dep on nvidia-kernel-1.0.9629
  Considering linux-restricted-modules-2.6.17-10-generic 2 as a solution to nvidia-glx 0
  Removing nvidia-glx rather than change nvidia-kernel-1.0.9629
Done
MarkUpgrade() called on a non-upgrable pkg: 'ubuntu-desktop'
ERROR:root:Dist-upgrade failed: 'A essential package would have to be removed'
Starting
Starting 2
Investigating nvidia-glx
Package nvidia-glx has broken dep on nvidia-kernel-1.0.9629
  Considering linux-restricted-modules-2.6.17-10-generic 2 as a solution to nvidia-glx 0
  Removing nvidia-glx rather than change nvidia-kernel-1.0.9629
Done
MarkUpgrade() called on a non-upgrable pkg: 'ubuntu-desktop'
ERROR:root:Dist-upgrade failed: 'A essential package would have to be removed'
Starting
Starting 2
Investigating nvidia-glx
Package nvidia-glx has broken dep on nvidia-kernel-1.0.9629
  Considering linux-restricted-modules-2.6.17-10-generic 2 as a solution to nvidia-glx 0
  Removing nvidia-glx rather than change nvidia-kernel-1.0.9629
Done
MarkUpgrade() called on a non-upgrable pkg: 'ubuntu-desktop'
ERROR:root:Dist-upgrade failed: 'A essential package would have to be removed'
Starting
Starting 2
Investigating nvidia-glx
Package nvidia-glx has broken dep on nvidia-kernel-1.0.9629
  Considering linux-restricted-modules-2.6.17-10-generic 2 as a solution to nvidia-glx 0
  Removing nvidia-glx rather than change nvidia-kernel-1.0.9629
Done
MarkUpgrade() called on a non-upgrable pkg: 'ubuntu-desktop'
ERROR:root:Dist-upgrade failed: 'A essential package would have to be removed'
Starting
Starting 2
Investigating nvidia-glx
Package nvidia-glx has broken dep on nvidia-kernel-1.0.9629
  Considering linux-restricted-modules-2.6.17-10-generic 2 as a solution to nvidia-glx 0
  Removing nvidia-glx rather than change nvidia-kernel-1.0.9629
Done
MarkUpgrade() called on a non-upgrable pkg: 'ubuntu-desktop'

I see that it has something to do with my nvidia graphics...but I am not sure what I need to do!

Thanks

---

### Post by an.echte.trilingue on 2007-01-12
Broken deps like that are most often caused by a change in the repos since you updated apt on what is there.

```
sudo apt-get update
sudo apt-get dist-upgrade
```

If that does not work, it should give you some helpful output.

You can also try removing your nvidia drivers, dist-upgrading, and reinstalling the nvidia drivers (all without rebooting or logging out) and then reboot.  Have a rescue CD ready if you go this route, though.

Good luck,
-mat

---

### Post by BKK on 2007-01-13
Thanks that got it...I will try to become more fluent using the command line!

Thanks again!

---

### Post by TimmyJ on 2007-01-20
Hey I have an identical problem but for some reason the posted solution doesn't work for me. The nvidia-glx package was removed during the dist-upgrade and now whenever I try to get it back I get the same "depends: nvidia-kernel-1.0.9629" error. Any ideas on how I can fix this?

---

### Post by Seine on 2007-01-20
There are a number of threads about this issue currently. I'm happy to say this solution worked for me.

---

### Post by bkeithly on 2007-01-20
Envy does it!!!!

---

### Post by Seine on 2007-01-21
Well I *envy* you because I now have a broken x-server after reboot.  :(

---

