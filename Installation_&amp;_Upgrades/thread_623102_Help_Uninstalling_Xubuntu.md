---
title: "Help Uninstalling Xubuntu"
date: 2007-11-25
forum: Installation &amp; Upgrades
---

### Post by Unlockitall on 2007-11-25
I have an old computer that ran windows 98, and just to try to learn more about computers, i installed xubuntu because it was a small linux distro and my computer teacher recommended it. now i find that it is not working for me very well. im thinking about puttin a UNIX distro on it instead. I was wondering if anyone could tell me how to completly unistall Xubuntu and still leave windows intact(my dad says something about he has important files). any help is greatly appreciatted

---

### Post by LaRoza on 2007-11-25
Restore the Windows MBR, use the Windows disk or use the Super Grub Disk.

Restart the computer, Windows should load normally, use the Windows tools for deleting the Xubuntu and swap partitions.

That computer sounds a little old, you can try Zenwalk, which may be better resource wise.

Look in the "Other OS Talk" section for the sticky on distros for old computers, it is the most informative post on this subject.

---

### Post by Unlockitall on 2007-11-25
im sorry...im not sure what the mbr is and i dont know what the super grub disk is. i also do not have the windows disk:(sorry

---

### Post by LaRoza on 2007-11-25
> **Unlockitall said:**
> im sorry...im not sure what the mbr is and i dont know what the super grub disk is. i also do not have the windows disk:(sorry

See the link in my sig, download the Super Grub Disk and burn it as an iso (like Xubunu).

Boot from it, and restore the MBR (Master Boot Record) to Windows (the option will be there, the SGD is all text, but it is straight forward, read it, you won't have to do anything other than select the option)

Reboot the computer, and Windows should load with no option to boot Ubuntu (no Grub).

---

### Post by Unlockitall on 2007-11-25
thank you very much. just to double check this will completly unistall xubuntu?

---

### Post by LaRoza on 2007-11-25
> **Unlockitall said:**
> thank you very much. just to double check this will completly unistall xubuntu?

Well, restoring the MBR with the SGD will make it safe to delete the Xubuntu partitions and reformat them or extend the Windows partition to fill the space.

---

### Post by Unlockitall on 2007-11-25
if i want to install FreeBSD and have it take up the same space as Xubuntu, how would I  delete it first?

---

### Post by LaRoza on 2007-11-25
> **Unlockitall said:**
> if i want to install FreeBSD and have it take up the same space as Xubuntu, how would I  delete it first?

Use the existing partitions then, the FreeBSD installation will format it for you.

---

