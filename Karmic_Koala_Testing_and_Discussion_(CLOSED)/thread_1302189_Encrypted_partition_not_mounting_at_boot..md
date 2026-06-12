---
title: "Encrypted partition not mounting at boot."
date: 2009-10-26
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by Nightmare JG on 2009-10-26
Hello there,
I updated to karmic RC a few days ago, and aside from xsplash not installing itself I ran into no problems. However a few days ago some update or another has caused me a problem.

I have Ubuntu Studio set up with full disk encryption. I have three different partition that linux all mounts at boot: home, root, and FILES. FILES has stopped mounting automatically. I went into grub2 (which I installed before this problem started) and removed splash from the boot command so I could get a look at the problem. It seems that after I type my password it mounts home and root and beings to run fsck on FILES, but the system continues booting anyway. The end result being that FILES is never mounted.

So, any idea why this is happening? I'd also like the command I can use the mount the disk manually, since I would like to be able to get at my stuff. Is the problem just with me or is it worth filing a bug report?

---

### Post by Nightmare JG on 2009-10-27
Okay, that was odd.

So I've just been using my laptop normally despite not being able to use my FILES drive. I'd noticed when I'd booted it up last that the icons for files and folders on my desktop where wrong, so I opened up the appearance dialog and tried to change them. They wouldn't, so I just assumed it was a different problem. Nope.

I just noticed that I FILES was mounted again. So after messing around I realized that nautilus was running as root somehow. I restated nautilus and my icons and theme came back along with a working FILES mount.

My guess would be that fsck kept running and managed to finish, cause FILE to mount properly. The system just didn't wait like it was supposed to.

EDIT: I figure I should file a bug report, but for what package?

---

### Post by biji on 2009-10-27
i'm having same problem.. after   trying all ecryptfs binary ^^ found this:

run ecryptfs-manager
eCryptfs key management menu
-------------------------------
	1. Add passphrase key to keyring
	2. Add public key to keyring
	3. Generate new public/private keypair
	4. Exit

choose 1

paste your passphrase at 1st time setup (not your login pass)

choose 4

then run ecryptfs-mount-private

mount


HTH

---

