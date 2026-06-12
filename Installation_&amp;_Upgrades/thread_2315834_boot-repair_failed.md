---
title: "boot-repair failed"
date: 2016-03-02
forum: Installation &amp; Upgrades
---

### Post by Steven_Geurts on 2016-03-02
Still hangs when rebooting. Tried boot-repair, but stays the same.
boot log:   [paste.ubuntu.com/15270395](paste.ubuntu.com/15270395)

any ideas?

---

### Post by grahammechanical on 2016-03-02
Boot Repair did not fail. It successfully re-install Grub into the MBR of the hard disk. Breakage between the boot menu loading Linux and the desktop environment cannot be fixed by boot repair.

You need to give us a better description of what "hangs when rebooting" means. Do you get dumped into Grub rescue? NO? Then the problem is nothing to do with Grub? Do you get to a login screen? Yes? What happens next? No? Are there any error messages on screen at the time that loading stops?

It is this kind of information that will be helpful to us.

Regards.

---

### Post by oldfred on 2016-03-03
You show an old nVidia card GeForce 6200, so need nomodeset.
Since you only have Ubuntu installed, you will not get grub menu, but have to hold shift key from BIOS until menu appears.
Did you install Ubuntu or Lubuntu?
Old systems may not work with Unity and need lighter weight gui that Lubuntu has.

       At grub menu you can use e for edit, scroll to linux line and replace quiet splash with nomodeset.
How to set NOMODESET and other kernel boot options in grub2 - both BIOS liveCD & grub first boot ( also UEFI with grub) 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)

---

### Post by Steven_Geurts on 2016-03-03
Thx, will try that. (home in an hour or so) I installed Ubuntu, previously had 12.04 running great.
It was  running my mediaserver and facebook/twitter system for the wife.
But last night i tried to get in the grub menu, but holding down shift didn't do the trick.
boot-repair ran flawless, but problem stayed the same.

Kind regards

---

### Post by Steven_Geurts on 2016-03-03
Now it says error, attemping to read / write outside hd0. Grub rescue...

---

### Post by oldfred on 2016-03-03
Is this the same 12.04 or new install?
If same you may be getting hard drive issues.

From live installer, use Disks or Disk Utility which have Smart Data, if your hard drive supports that.

---

### Post by Steven_Geurts on 2016-03-03
Was a new clean install with nomodeset from the f6 options, cannot get into Grub, going to do the boot-repair

---

