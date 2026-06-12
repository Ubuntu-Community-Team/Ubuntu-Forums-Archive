---
title: "Update manager not working"
date: 2011-08-06
forum: Installation &amp; Upgrades
---

### Post by peterson43 on 2011-08-06
Update manager on my computer (running ubuntu 10.04) isn't working. I can open it up from the System menu, but when I press "check" or "Install updates" it the cursor just spins in circles like it's thinking but it never does anything. I can't even quit the program. 

I recently did two things that might have caused the problem. 

1) I upgraded yesterday from 8.04 to 10.04. I don't remember if I ran Upgrade Manager or not earlier today but I think I might have. 

2) I have a dual-boot system and I re-partitioned my hard drive this evening. I shrunk the partition with Ubuntu on it, moved the swap partition over, and expanded the Windows partition. The first time I logged in after re-partitioning the hard drive I got an information message saying that the Update manager hadn't loaded correctly. That was when I first noticed the problem, so I suspect that it has something to do with me moving around files in the re-partitioning. 

Anyone know what I can do to fix things?

---

### Post by Hakunka-Matata on 2011-08-07
Does your  partitioning look OK?
```

sudo fdisk -lu
```what partitioning program did you use?

---

### Post by peterson43 on 2011-08-07
I'm not sure what things are supposed to look like, but when I ran sudo fdisk -lu and got the following. 

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x9285df27

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1            2048    10403839     5200896   27  Unknown
Partition 1 does not end on cylinder boundary.
/dev/sda2   *    10403840   136351743    62973952    7  HPFS/NTFS
Partition 2 does not end on cylinder boundary.
/dev/sda3       136351744   234436607    49042432    5  Extended
Partition 3 does not end on cylinder boundary.
/dev/sda5       136353792   148070399     5858304   82  Linux swap / Solaris
/dev/sda6       148072448   204148735    28038144   83  Linux
/dev/sda7       204150303   234435599    15142648+  83  Linux


The only thing funny is that there is some extra space available between some of the partitions for some reason. 

I used gparted to partition the hard drive.

By the way, I'm somewhat new to the forums. How do I get my terminal commands/results to appear in a nice box like everyone else does?

---

### Post by Hakunka-Matata on 2011-08-07
The fdisk output doesn't show any glaring problems to my less than expert eye.  You do have the boundary comments.  I'd boot to a liveCD and use GParted to "**check**" the partitions for errors.  That may fix things.  Highlight each partition, right click on it and select check.  


> By the way, I'm somewhat new to the forums. How do I get my terminal  commands/results to appear in a nice box like everyone else does? 	

When you reply, use the "go advanced" method, and then use the different formatting methods:

[LIST]
[*]wrap code items using the **# symbol.**
[*]wrap quotes using the **quote symbol **- rest your pointer on each symbol above and see information
[/LIST]

---

### Post by peterson43 on 2011-08-07
I booted the Live CD and checked the partitions using gparted. It didn't seem to report any errors. I couldn't check the extension partition and the swap partition (even when I turned the swap partition off). 

The Update Manager still isn't working. I can open Update Manager up, but I can't do anything with it. Even if I click on the "Settings..." button it just thinks and thinks and never does anything. 

Does anyone have any other ideas? Do I need to reinstall Update Manager?

---

### Post by Hakunka-Matata on 2011-08-07
I see no problem with reinstalling update-manager-core in synaptic.

OK, how about 'settings' in update manager?,  Have you checked to see if it looks OK, like does it have a mirror selected?  

See included graphic

---

### Post by peterson43 on 2011-08-07
> **Hakunka-Matata said:**
> I see no problem with reinstalling update-manager-core in synaptic.

OK, how about 'settings' in update manager?,  Have you checked to see if it looks OK, like does it have a mirror selected?  

See included graphic
Like I said in my above post, clicking "settings" in update manager also fails to do anything. The system just sits and thinks. 

Also, once it starts "thinking" I can't close update manager. I have to kill it with 
```
killall update-manager
```

---

### Post by Hakunka-Matata on 2011-08-07
> **peterson43 said:**
> I booted the Live CD and checked the partitions using gparted. It didn't seem to report any errors. I couldn't check the extension partition and the swap partition (even when I turned the swap partition off). 

The Update Manager still isn't working. I can open Update Manager up, but I can't do anything with it. Even if I click on the "[COLOR=Red]Settings...[/COLOR]" button it just thinks and thinks and never does anything. 

Does anyone have any other ideas? Do I need to reinstall Update Manager?

Sorry, I missed that.....

---

### Post by peterson43 on 2011-08-07
I used synaptic package manager to re-install update-manager-core and that seemed to fix the problem at first. It was able to install the 4 updates that were waiting to be installed, but when I checked for more updates it got most of the way through the search and then reported the following error message: 


```
Could not download all repository indexes

The repository may no longer be available or could not be contacted
because of network problems. If available an older version of the failed
index will be used. Otherwise the repository will be ignored. Check your
network connection and ensure the repository address in the preferences
is correct.
```

followed with some more details about the error

```

GPG error: http://ppa.launchpad.net lucid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY F7A629A71FC0F4DDFailed to fetch http://ppa.launchpad.net/jon-oberheide/ppa/ubuntu/dists/jaunty/main/binary-i386/Packages.gz  404  Not Found
Failed to fetch http://ppa.launchpad.net/jon-oberheide/ppa/ubuntu/dists/jaunty/main/source/Sources.gz  404  Not Found
Failed to fetch http://ppa.launchpad.net/madman2k/ubuntu/dists/hardy/main/binary-i386/Packages.gz  404  Not Found
Failed to fetch http://ppa.launchpad.net/madman2k/ubuntu/dists/hardy/restricted/binary-i386/Packages.gz  404  Not Found
Failed to fetch http://ppa.launchpad.net/madman2k/ubuntu/dists/hardy/universe/binary-i386/Packages.gz  404  Not Found
Failed to fetch http://ppa.launchpad.net/madman2k/ubuntu/dists/hardy/multiverse/binary-i386/Packages.gz  404  Not Found
Some index files failed to download, they have been ignored, or old ones used instead.

```

I tried checking the settings and things seemed to be fine (though I don't know what to be looking for really). 

Now, the update manager is acting up again and won't do anything when I click 'settings' 'check' or 'install updates' so it kind of seems that I'm back to square one. Any ideas what the above errors might mean?

---

### Post by peterson43 on 2011-08-07
I just noticed that in the error details above that some of the lines mention "hardy." I just upgraded from hardy to lucid. Could this be part of the problem?

---

### Post by peterson43 on 2011-08-08
Okay, maybe I've managed to solve things. I went through the error messages I posted above, the first error was 

> GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY F7A629A71FC0F4DD

Did a little searching and found this [thread]("http://ubuntuforums.org/showthread.php?t=1805824&highlight=W%3A+GPG+error%3A+lucid+Release%3A+signatures+couldn%27t+verified+public+key") that showed me how to fix it. Basically it's two lines of code to get and add the key. 

```


gpg --keyserver keyserver.ubuntu.com --recv F7A629A71FC0F4DD

gpg --export --armor F7A629A71FC0F4DD | sudo apt-key add -

```

The next lines in the code seemed to maybe be referring to packages that I'd added in the past that no longer work (they referred to jaunty or hardy). Those errors were
> 
Failed to fetch [http://ppa.launchpad.net/jon-oberheide/ppa/ubuntu/dists/jaunty/main/binary-i386/Packages.gz](http://ppa.launchpad.net/jon-oberheide/ppa/ubuntu/dists/jaunty/main/binary-i386/Packages.gz)  404  Not Found
Failed to fetch [http://ppa.launchpad.net/jon-oberheide/ppa/ubuntu/dists/jaunty/main/source/Sources.gz](http://ppa.launchpad.net/jon-oberheide/ppa/ubuntu/dists/jaunty/main/source/Sources.gz)  404  Not Found
Failed to fetch [http://ppa.launchpad.net/madman2k/ubuntu/dists/hardy/main/binary-i386/Packages.gz](http://ppa.launchpad.net/madman2k/ubuntu/dists/hardy/main/binary-i386/Packages.gz)  404  Not Found
Failed to fetch [http://ppa.launchpad.net/madman2k/ubuntu/dists/hardy/restricted/binary-i386/Packages.gz](http://ppa.launchpad.net/madman2k/ubuntu/dists/hardy/restricted/binary-i386/Packages.gz)  404  Not Found
Failed to fetch [http://ppa.launchpad.net/madman2k/ubuntu/dists/hardy/universe/binary-i386/Packages.gz](http://ppa.launchpad.net/madman2k/ubuntu/dists/hardy/universe/binary-i386/Packages.gz)  404  Not Found
Failed to fetch [http://ppa.launchpad.net/madman2k/ubuntu/dists/hardy/multiverse/binary-i386/Packages.gz](http://ppa.launchpad.net/madman2k/ubuntu/dists/hardy/multiverse/binary-i386/Packages.gz)  404  Not Found


I fixed this by just telling Update Manager no longer to look for updates from those sources. This is done by clicking on 'settings' in Update Manager and then going to the 'other software' tab and un-checking the relevant sources. 

I am able to now check for updates without returning any error messages. I'm still not confident that I can successfully get updates since it hasn't returned any needed updates yet. I'll wait to do a couple successful updates before I mark the thread as solved. 

Also, I'm still having a funny issue with running Update Manager. If I open it up by clicking on System > Administration > Update Manager, then whenever I click on something it just thinks and doesn't do anything. However, if I open it in a terminal by typing update-manager then it works fine. Any ideas on fixing this? If it continues to be a problem and I don't get any answers here I may post it as a new thread.

---

