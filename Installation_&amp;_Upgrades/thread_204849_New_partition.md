---
title: "New partition"
date: 2006-06-27
forum: Installation &amp; Upgrades
---

### Post by Albi on 2006-06-27
Hello,
I recently installed Ubuntu on a 10GB Partition, but now I'm deciding to make a new 15gb partition with PartitionMagic (or another method if better), increasing the overall size to 25gb.
My only question before I go on with this is, is it possible to make this partition automatically mount itself at startup, and if so, what would be the best way to go about doing something like this?

---

### Post by bruce89 on 2006-06-27
Partition magic is useless for ext3 et al(AFAIK).  Use the [Gparted CD]("http://gparted.sourceforge.net/livecd.php"), which is only 30MiB.  It seems as if you want to make a partition larger, just enlarge it from in Gparted.  It will mount (if it is the same partition).  I would backup anything you want to keep on the partiton you are changing, just in case.

---

### Post by Culuntu on 2006-06-27
i don't think there is partition magic for ubuntu!

---

### Post by Albi on 2006-06-27
[QUOTE=bruce89]Partition magic is useless for ext3 et al(AFAIK).  Use the [Gparted CD]("http://gparted.sourceforge.net/livecd.php"), which is only 30MiB.  It seems as if you want to make a partition larger, just enlarge it from in Gparted.  It will mount (if it is the same partition).  I would backup anything you want to keep on the partiton you are changing, just in case.[/QUOTE]
From what I know, there's no way to make a partition larger, only smaller, unless you re-format it, which is not what I'm willing to do>

And I dual boot with Windows XP

edit: could I not just run gparted from ubuntu?

---

### Post by bruce89 on 2006-06-27
[QUOTE=Albi]From what I know, there's no way to make a partition larger, only smaller, unless you re-format it, which is not what I'm willing to do>
[/QUOTE]
I'm sure that ext3 can be resized up or down.  The only thing that can't be done is its front end moved.  This is the typical capabilities:
[IMG]http://gparted.sourceforge.net/screens/gparted_10_big.jpg[/IMG]
[QUOTE=Albi]edit: could I not just run gparted from ubuntu?[/QUOTE]
You could, but you'd have to unmount every partition you want to edit, which is impossible if it is the root directory.

---

### Post by Culuntu on 2006-06-27
plz may someone help me with this : ?

[http://www.ubuntuforums.org/showthread.php?t=204848]("http://www.ubuntuforums.org/showthread.php?t=204848")

---

### Post by bruce89 on 2006-06-27
[QUOTE=Culuntu]plz may someone help me with this : ?

[http://www.ubuntuforums.org/showthread.php?t=204848]("http://www.ubuntuforums.org/showthread.php?t=204848")[/QUOTE]
What has that to do with this thread?  I'm sorry, but I can't help you, somebody else will be able to.

---

### Post by Albi on 2006-06-27
[QUOTE=bruce89]I'm sure that ext3 can be resized up or down.  The only thing that can't be done is its front end moved.  This is the typical capabilities:
[IMG]http://gparted.sourceforge.net/screens/gparted_10_big.jpg[/IMG]

You could, but you'd have to unmount every partition you want to edit, which is impossible if it is the root directory.[/QUOTE]
Well I ran gparted from the Ubuntu LiveCD, and like PartitionMagic, it won't let me resize it to make it bigger, only smaller.

---

