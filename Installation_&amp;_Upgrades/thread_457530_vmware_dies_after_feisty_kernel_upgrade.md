---
title: "vmware dies after feisty kernel upgrade"
date: 2007-05-28
forum: Installation &amp; Upgrades
---

### Post by strungoutfan78 on 2007-05-28
Ok so recently I finally got vmware-player working pretty much flawlessly.  I was very proud of myself for doing this.  So today I get the bright idea that I oughtta upgrade my kernel.  #-oOops#-o.  Now even though vmware has been updated as well,  all I get when I try to run it is this message:

[HTML]Cannot open the disk '/home/neil/vmware/windows.vmdk' 
or one of the snapshot disks it depends on.
Reason: No medium found.[/HTML]

I've no idea what this means, as everything is still right where it oughtta be.

Also for some reason I could only get it to run as root before the upgrade.  At some point it began allowing me to run it without entering a root password.  Strange.  I think I may have added myself to a group I shouldn't have while I was setting up my Samba server.:-s

---

### Post by NZ-Wanderer on 2007-05-28
Hate to be the bearer of bad tidings, but the new kernel (16) has broken a lor of things (including vmware)

Check this thread out (warning its a long one now.) 

[http://ubuntuforums.org/showthread.php?t=456662](http://ubuntuforums.org/showthread.php?t=456662)

What I did in the end was to use the package manager to completly remove all instances of 2.6.20-16 (there were 3)

I did find afterwards that my vmware server still didn't run, but it was no hassle to run vmware-install.pl again...

---

### Post by strungoutfan78 on 2007-05-28
I wish i could run it.  I completely removed all instances of the 2.6.20-16 menace, along with all the vmware packages.  Now when I try and reinstall it the only option it gives me ist to install the 2.6.20-16 kernel modules.  I can add the -15 in there with it, but if i deselect the -16 it automatically deselects everything else, as if the only way I can install it is with the 2.6.20-16 modules.  Maybe I need to compile from source.

Strange.  After I got rid of my new kernel I noticed my Virtual Box left with it as well.  Something strange is definitely going on here.


*EDIT* OK. So Virtual Box is fine.  Just reinstalled the .deb and all is well.  Writing this from a virtual install of VirtuaLinux.  Still working on the vmware....

---

### Post by NZ-Wanderer on 2007-05-28
Hmmm, well I was in 15 when I uninstalled 16, however I didn't uninstall my vmware servers files, I just installed over the top of them..
I wish I could be of more help, but I only know enuff to muddle my way through simple issues, this broken 16 was way beyond me, that's why I took the easy way out and got rid of it..

> **strungoutfan78 said:**
> I wish i could run it.  I completely removed all instances of the 2.6.20-16 menace, along with all the vmware packages.  Now when I try and reinstall it the only option it gives me ist to install the 2.6.20-16 kernel modules.  I can add the -15 in there with it, but if i deselect the -16 it automatically deselects everything else, as if the only way I can install it is with the 2.6.20-16 modules.  Maybe I need to compile from source.

Strange.  After I got rid of my new kernel I noticed my Virtual Box left with it as well.  Something strange is definitely going on here.

---

### Post by zero244 on 2007-05-28
The fact that vmware doesnt work with Fiesty is the reason I went beck to Edgy. My kernal is at 2.6.11 and I dont plan on updating it beyond that. It seems that 2.6.15 or lower will run vmware.
There is a fix for this if you look at the vmware forums. But it is not an easy fix......its a long drawn out compiling blah blah fix.
Most likely Vmware will eventually update their software. I installed the latest version 1.03 which is an improvement over 1.02 in that it fixes a memory leak and completely frees up memory used after you close Vmware.
I personally did not see any major improvements in Fiesty over Edgy. I will stay with Edgy for the time being.

---

### Post by NZ-Wanderer on 2007-05-28
The latest VMware server runs perfectly on Fiesty (apart from the new kernel, but that not vmware fault) - the vmware team fixed the problem in the major release before last.. - No longer any need to use any kind of fix in Fiesty.. (Like the player, the server is free for use, and it gives you heaps more options)

> **zero244 said:**
> The fact that vmware doesnt work with Fiesty is the reason I went beck to Edgy. My kernal is at 2.6.11 and I dont plan on updating it beyond that. It seems that 2.6.15 or lower will run vmware.
There is a fix for this if you look at the vmware forums. But it is not an easy fix......its a long drawn out compiling blah blah fix.
Most likely Vmware will eventually update their software. I installed the latest version 1.03 which is an improvement over 1.02 in that it fixes a memory leak and completely frees up memory used after you close Vmware.
I personally did not see any major improvements in Fiesty over Edgy. I will stay with Edgy for the time being.

---

### Post by strungoutfan78 on 2007-05-28
> **NZ-Wanderer said:**
> The latest VMware server runs perfectly on Fiesty (apart from the new kernel, but that not vmware fault) - the vmware team fixed the problem in the major release before last.. - No longer any need to use any kind of fix in Fiesty.. (Like the player, the server is free for use, and it gives you heaps more options)

This is very true, as the vmware player was running fairly well before i upgraded my kernel.  No patches were necessary. 

I just removed the remaining traces of my vmware install and installed the latest version 1.04 from source and all seems to be ok.  Actually, the player seems to be running about twice as fast as the precompiled version from the repo.  Maybe this was not all in vain....;)

---

### Post by NZ-Wanderer on 2007-05-28
Congrats, glad you got it working, and with a speed increase too :D:D

> **strungoutfan78 said:**
> This is very true, as the vmware player was running fairly well before i upgraded my kernel.  No patches were necessary. 
I just removed the remaining traces of my vmware install and installed the latest version 1.04 from source and all seems to be ok.  Actually, the player seems to be running about twice as fast as the precompiled version from the repo.  Maybe this was not all in vain....;)

---

### Post by strungoutfan78 on 2007-05-28
I really appreciate the heads up **wanderer**.  I never would have thought it was an issue with the kernel.  I've been so pleased with ubuntu coming from opensuse that it never would have occured to me.

---

### Post by laser_in_your_eye on 2007-06-05
all i had to do was run sudo /usr/bin/vmware-config.pl again (as suggested on another post) and vmware now runs fine with the new kernel.

haven't had any other problems with 16 either :D

---

