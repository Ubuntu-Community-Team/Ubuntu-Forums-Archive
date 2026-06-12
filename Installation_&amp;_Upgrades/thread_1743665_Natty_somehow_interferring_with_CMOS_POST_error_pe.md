---
title: "Natty somehow interferring with CMOS POST/ error persisting past reboot"
date: 2011-04-29
forum: Installation &amp; Upgrades
---

### Post by asdlfkjdw202011 on 2011-04-29
I must admit this little problem is quite a fascinating one, since I wasn't aware that anything persisted past a shutdown/reboot (though this is without a full power cycle.)

Natty itself works absolutly fine, this seems to be about how it impacts the rest of the system.

Basically my problem can be neatly summed up as the problem described at both [here]("http://kubuntuforums.net/forums/index.php?action=printpage;topic=3115863.0") and [here.]("http://fossplanet.com/f10/%5Bbug-768480%5D-%5Bnew%5D-natty-causes-interruption-cmos-post-checks-130927/") I can only presume it's a rather uncommon problem to do with a particular hardware setup since I can't find any widespread bug reports of it, but it is (on my system at least) highly replicable. 

I can reboot my system from Natty and it either one of two scenarios. It can reboot the system (as first asked) then reboot again in the middle of POST and splurge an error about interrupting POST at me (and keep giving me this error every reboot till I go into the bios and resave some settings). 

Alternatively, it can get all the way into grub, where I can dual boot into Windows, windows will get some arbritary point in (usually the login screen give or take 10 seconds) and then reboot at random. It's not even a windows crash since I've disabled auto-reboot.

I'm not sure what's causing it but I can only presume it's something at the kernel level, since I'm not sure anything else would have the kind of power needed to interfere with the system at an 'outside the OS' level. As such I wouldn't have any idea how to go about fixing it, but I can hope that someone here may be able to point me in the direction of potential settings I can change (probably BIOS I guess) that might aleviate the issue till a fix is found.

A full power down and resart of the machine clears the issue (but I'd be incredibly surprised if it didn't.)

Edit: This is an alternate CD install of the 64 bit version.

Many thanks. :)

---

### Post by asdlfkjdw202011 on 2011-04-30
Small bump.

---

### Post by dino99 on 2011-04-30
have some trouble too with my hardware: reboot never work due to a bad state while shuting down

as i've an intel cpu i've installed: intel-microcode & microcode.ctl to get the latest bug fixes from intel

updating your bios is an other way

and reporting bug too: ubuntu-bug linux

but the problem is still there even with the latest kernel (kernel-ppa)

so wait & see

note: still not tested with reformating the partition (ext4 on my end) with latest gparted or partedmagic, in case of a formatting issue

---

### Post by asdlfkjdw202011 on 2011-05-16
A little bump to see if anyone as any further suggestions on this issues, since no updates appear to have fixed it yet.

Further googling finds [this thread]("http://ubuntuforums.org/showthread.php?t=1734517") and [this thread]("http://ubuntuforums.org/showthread.php?t=1759080") which appear to describe the exact same problem. It doesn't appear common, but it is rather severe for anyone who wants to dual boot with this issue.

---

