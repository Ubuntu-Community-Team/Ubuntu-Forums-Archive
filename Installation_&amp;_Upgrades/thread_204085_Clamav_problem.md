---
title: "Clamav problem"
date: 2006-06-26
forum: Installation &amp; Upgrades
---

### Post by RESmonkey on 2006-06-26
I tired getting clamav through automatix, something went wrong.  I don't think it is fully installed, but every time I go to Ubuntu Update sofware popup thing, and install stuff, it all fails because of this E: Clamav error

[[IMG]http://images6.theimagehosting.com/Screenshot.149.th.png[/IMG]](http://server6.theimagehosting.com/image.php?img=Screenshot.149.png)

Please help, updates aren't working because of this clamav thing.  I don't know how to remove or anything.

---

### Post by arnieboy on 2006-06-26
[QUOTE=RESmonkey]I tired getting clamav through automatix, something went wrong.  I don't think it is fully installed, but every time I go to Ubuntu Update sofware popup thing, and install stuff, it all fails because of this E: Clamav error

[[IMG]http://images6.theimagehosting.com/Screenshot.149.th.png[/IMG]](http://server6.theimagehosting.com/image.php?img=Screenshot.149.png)

Please help, updates aren't working because of this clamav thing.  I don't know how to remove or anything.[/QUOTE]
u mean synaptic.. automatix does not install clamav.

---

### Post by RESmonkey on 2006-06-26
[QUOTE=arnieboy]u mean synaptic.. automatix does not install clamav.[/QUOTE]

yes, that.  My bad.  Can you help me?

---

### Post by z_diver on 2006-06-26
[quote=RESmonkey]yes, that.  My bad.  Can you help me?[/quote] 
Try running "sudo aptitude purge clamav"  That should remove clamav, unzoo, clamav-freshclam, clamav-base, libclamav1 and then run "sudo aptitude remove arj" to complete the uninstallation.

Now, the same old question... why use linux if you want to run antivirus software?  I realize that there are platforms where that can be helpful but this isn't one of them.

---

### Post by RESmonkey on 2006-06-26
[QUOTE=z_diver]Try running "sudo aptitude purge clamav"  That should remove clamav, unzoo, clamav-freshclam, clamav-base, libclamav1 and then run "sudo aptitude remove arj" to complete the uninstallation.

Now, the same old question... why use linux if you want to run antivirus software?  I realize that there are platforms where that can be helpful but this isn't one of them.[/QUOTE]


Hmm...right before i did this i ran Synaptic and removed as much clamav as I could.  This tooks some stuff out, as well (i think?). 

Thanks, so far there have been no more updates, so ill see if it worked as soon as the messege comes up to update

---

### Post by tbresson on 2006-07-04
I just had the same problem.

I believe it's because I installed the application aswell as the daemon.
I'm not sure, but I think you'll have to choose?

---

