---
title: "laptop shutdown halfway through upgrade to 13.10"
date: 2013-10-20
forum: Installation &amp; Upgrades
---

### Post by gertrude58 on 2013-10-20
I was doing upgrade to 13.10 when the plug was pulled by accident to my laptop. As it only works now if plugged into the mains,it promptly shut down.When plugged back in and restarted,the grub menu came up with ubuntu the top option to log in to,the other options were memory tests.So I chose ubuntu and this message came up:

Filesystem check or mount failed.
A maintenance shell will now be started.
CONTROL-D will terminate this shell and continue booting after re-trying filesystems.Any further errors will be ignored
root@richard-Satellite-L300:~

So what do I do now? I thought I could maybe burn a new dvd and reinstall on top of the mistake but when I try to boot from the dvd it just comes back to that grub menu again and wont use the dvd at all even though I chose it in the boot menu.
Any advice gratefully accepted.i am in big trouble as this laptop is now being used by hubby who is not amused!

---

### Post by mörgæs on 2013-10-20
How does a boot from USB work?

---

### Post by beenny on 2013-10-20
I had the same problem. i don't mind do a fresh install (but stupidly) didn't back up all files yet and when I try plugging in an external drive it isn't recognized in mount. is there a way I can atleast get certain files backed up and just do a fresh install?

fsck -f doesn't reveal any (obvious) problems

---

### Post by beenny on 2013-10-21
So I wasn't able to boot from a USB but I did find this thread to finish the installation:

[http://askubuntu.com/questions/38617/root-filesystem-check-fails-after-power-failure-during-installation](http://askubuntu.com/questions/38617/root-filesystem-check-fails-after-power-failure-during-installation)

still checking stuff but seems to be working so far. This is the second upgrade where it has failed in the middle. not sure if it's me or ubuntu but definitely worrisome...

---

### Post by mastablasta on 2013-10-21
> **gertrude58 said:**
> Any advice gratefully accepted.i am in big trouble as this laptop is now being used by hubby who is not amused!

mkae a fresh install of the system. don't format the disk during install but just install the os (i.e. overwrite the previous install).

---

