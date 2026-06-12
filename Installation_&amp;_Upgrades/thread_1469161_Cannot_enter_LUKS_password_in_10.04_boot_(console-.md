---
title: "Cannot enter LUKS password in 10.04 boot (console-setup issue)"
date: 2010-05-01
forum: Installation &amp; Upgrades
---

### Post by onyxrev on 2010-05-01
I've just upgraded from 9.10 on a system that has an encrypted root partition encrypted using the following guide:

[https://help.ubuntu.com/community/EncryptedFilesystemOnIntrepid](https://help.ubuntu.com/community/EncryptedFilesystemOnIntrepid)

On boot, prior to the LUKS password prompt, I see the error:
```
cannot open file /etc/console-setup/boottime.kmap.gz
```

The consequence is that the keyboard does not respond, the password cannot be entered, and the root partition cannot be unlocked.

This behavior occurs on all 2.6.32.x kernels but falling back to my previous kernel, 2.6.31.9-rt works just fine.

This is on a production system and is not running in a virtual machine, so the issue is not:

[https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/548891](https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/548891)

I have tried running sudo dpkg-reconfigure console-setup, which does regenerate the initram-fs for the desire kernel, but it does not solve the problem.

The guide's initram hook includes the lines:

```
mkdir -p ${DESTDIR}/etc/console-setup
cp /etc/console-setup/boottime.kmap.gz ${DESTDIR}/etc/console
```

... but my understanding of the initram stages of the boot process are hazy and I am unclear what the intent is behind the lines.

Any help would be greatly appreciated.

---

### Post by onyxrev on 2010-05-02
Hmmm... it looks to me like the second line that copies the file in question should be copying to console-setup, not straight-up console:

```
mkdir -p ${DESTDIR}/etc/console-setup
cp /etc/console-setup/boottime.kmap.gz ${DESTDIR}/etc/console-setup
```

... but I dunno how it ever worked previously.  Going to try regenerating initram-fs with that change.

---

### Post by onyxrev on 2010-05-02
As I feared, the error about console-setup is gone but the keyboard still does not respond for any kernel.  Kinda dead in the water, now.

---

### Post by onyxrev on 2010-05-02
Well, going to have to roll back to my 9.10 image for now as I use this machine for work on a daily basis.  But I will first save the 10.04 drive to an image I can reload if anyone has any ideas.

---

### Post by onyxrev on 2010-05-02
Hey... wait a sec.

So the second script in that guide tries to load the console-setup file at the console location, not console-setup:

```
/bin/loadkeys /etc/console/boottime.kmap.gz
```

I bet that needs to be /etc/console-setup now.  I've gotta chroot into this thing and change that.

---

### Post by onyxrev on 2010-05-02
Well that certainly was wrong but didn't solve the problem.  Adding the splash option back to the grub menu entry demonstrated that the keyboard was in fact working but didn't 'connect' to the password entry prompt.

I'm out of ideas.  I got limping along by mashing the keyboard until the LUKS prompt times out, unlocking the drive at the initramfs prompt, and hitting 'continue'.  Gross.

---

### Post by onyxrev on 2010-05-03
Well, I never got it working and I have no idea why.  I did a fresh 10.04 install using the alternate disc's full-disk encryption and then hooked in my encrypted home directory using crypttab.  The LUKS prompts with 10.04 splash screen are really slick!

---

### Post by rennerc on 2010-05-18
I had the same issue, this is how I (sort of) fixed it:
[LIST]
[*]boot and wait till password prompt is being displayed
[*]press alt-f1
[*]enter password
[*]press alt-f7 to see whether it worked
[/LIST]
Any ideas why the keyboard only works on the first virtual terminal?

Cheers,
Chrigi

---

### Post by koba101 on 2010-06-02
rennerc, thanks for your input, i can now finally see the prompt and whether or not i've entered the correct password,
but I also agree this is no solution, in my case if i disable splash i can't enter anything, yet if i enable it i can't see the luks password entry screen....i need to research this further

---

