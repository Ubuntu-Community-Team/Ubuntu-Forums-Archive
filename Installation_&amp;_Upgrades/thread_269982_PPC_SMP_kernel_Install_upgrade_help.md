---
title: "PPC SMP kernel Install upgrade help"
date: 2006-10-02
forum: Installation &amp; Upgrades
---

### Post by moof on 2006-10-02
Hello all-

I'm fairly new to Ubuntu, and after looking aorund the forums a bit, I figured out how to get the PPC-SMP kernel for my Mac G4 dual from Synaptic.  After download/install, it asked for a reboot, which I did, but now when I check in the System Monitor, I see that it's still only showing one processor instead of two.

I figure that I'm missing some other step here, so could anyone clue me in on  how to get the kernel switched?  I notied that the SMP kernel is now located in the /boot dir, so it's there, just not being loaded or pointed to.

Thanks for any help in advance!

---

### Post by moof on 2006-10-03
Okay, so to answer my own question, it just requires a bit of gumption and persistence to get the kernel booting in Yaboot.  I'm going to post a thumbnail here for people as a reference if someone else runs into the same problem.

FIRST, you should check out the Yaboot documentation.  You should actually have this regardless, it's extremely handy to have:
[http://penguinppc.org/bootloaders/yaboot/doc/yaboot-howto.shtml/index.en.shtml]("http://penguinppc.org/bootloaders/yaboot/doc/yaboot-howto.shtml/index.en.shtml")

Especially pertinent to this problem is chapter 6, specifically section 6.5.

NEXT. all you really need to do is install the kernel you desire using Synaptic.  After that's done, you can do a list of your /boot directory and see the kernel files there.  There's actually two files that are symlinks: 'vmlinux' and 'initrd.img'  that each link to the current kernel files.  You can edit /etc/yaboot.conf and add your desired kernel in the top-most spot in the image section.  This wil make it the default image loaded at the boot: menu.

So essentially, you can put in:
```
image=/boot/vmlinux-2.6.15-27-powerpc-smp
        label=Ubuntu-27-dual
        read-only
        initrd=/boot/initrd.img-2.6.15-27-powerpc-smp
        append="quiet splash"
```

I would recommend leaving the current kernel section untouched, as it can be a fallback in case anything goes wrong.  This is actually a precompiled kernel from Ubuntu, so it's nothing too fancy.

After rebooting, check the System Monitor under System:Administration and hey presto, you should see two CPUs at work.

I'm slow, but I get there in the end... :-?

---

