---
title: "[SOLVED] encrypted root partition not mounting"
date: 2008-11-01
forum: Installation &amp; Upgrades
---

### Post by astrophoenix on 2008-11-01
I ran aptitude dist-upgrade to upgrade from hardy to intrepid.

for some reason, that didn't update my kernel. so when I rebooted, I was still running 2.6.24. and X wouldn't run. (I have an nvidia card).

I went ahead and did an aptitude install linux-generic, and that got me the 2.6.27 kernel. so I installed the linux-restricted-modules-2.6.24-21-generic, and rebooted, thinking my trouble would be over.

but, my root partition is an encrypted lvm partition.

on booting the 2.6.27 intrepid kernel, it prompts me for the passphrase on the splash screen as usual. but then eventually I get this message:

```

Starting up ...
Loading, please wait...
usplash: Setting mode 1920x144 failed
usplash: Using mode 1600x1200
Setting up cryptographic volume hda5_crypt (based on /dev/disk/by-uuid/a8a4fb81-99b2-48bf-96b9-a8bb8a1e2ea3)
cryptsetup: failed to setup lvm device
  Reading all physical volumes.  This may take a while...

```

that last line about "Reading all physical volumes." then repeats forever.

apparently I should have run update-manager instead of aptitude dist-upgrade.

but what do I do now? 

thanks

---

### Post by astrophoenix on 2008-11-04
[solution in this post, just click]("http://ubuntuforums.org/showthread.php?p=6103307#post6103307")

---

### Post by merpattersonnet on 2009-01-14
> **astrophoenix said:**
> [solution in this post, just click]("http://ubuntuforums.org/showthread.php?p=6103307#post6103307")

That post seems to be about getting X running and does not address the problem the OP mentions.  I'm also having this problem.  I can boot just fine with my hardy kernel but with the intrepid kernel it never moves past the point described.

---

### Post by merpattersonnet on 2009-01-14
> **merpattersonnet said:**
> That post seems to be about getting X running and does not address the problem the OP mentions.  I'm also having this problem.  I can boot just fine with my hardy kernel but with the intrepid kernel it never moves past the point described.

I've filed a bug report at:

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/317334](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/317334)

If anyone has experienced this please go there and confirm the bug report and leave a comment.  Thanks!

---

### Post by merpattersonnet on 2009-01-18
> **merpattersonnet said:**
> I've filed a bug report at:

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/317334](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/317334)

If anyone has experienced this please go there and confirm the bug report and leave a comment.  Thanks!

I resolved this in my case.  From the bug:

"Turns out that my lvm2 package wasn't being upgraded to intrepid for some reason I was unable to determine. Upgrading lvm2 and reinstalling the kernel package (so the initrd was rebuilt) did the trick."

---

