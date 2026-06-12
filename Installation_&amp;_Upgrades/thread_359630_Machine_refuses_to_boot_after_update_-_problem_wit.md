---
title: "Machine refuses to boot after update - problem with md devices??"
date: 2007-02-12
forum: Installation &amp; Upgrades
---

### Post by autom8on on 2007-02-12
All,

I've just set up a box running xubuntu 6.10 on an athlon 64 box. I used the alternate boot cd to install the machine - then updated the software using the normal tool.

My hardware setup is:

hda1 = /boot
hda2 = swap

sda1 and sdb1 = raid 1 = / partition.
sdc1 and sdd1 = raid 1 = /var partition.
sde1, sdf1 and sdg1 = raid 5 = /home.

After updating to kernel 2.6.17-11-generic - the machine just refuses to boot. 

Putting it into recovery mode - I'm seeing it identify all the devices correctly - but then it's just hanging after logging the following on the console:

md: raid1 personality registered for level 1
md: raid5 personality registered for level 5
md: raid4 personality registered for level 4

The machine is still responsive (i.e. if i hit ctrl-alt-delete it shuts down properly) - and it's sequentially accessing the drives (i can sit and watch the pretty lights flash in sequence).

Any ideas what has gone wrong, or how I can fix it?? I tried getting it to boot into single user mode - but it's still trying to load the md devices and hanging at that point...

*** UPDATE ***

I can boot off the ubuntu cd - at which point the machine is correctly identifying all the raid devices. I can mount them and browse the filesystem. /etc/mdadm/mdadm.conf looks right (although I'm not sure about the UUID entries - what happened to good old /dev/ stuff?).  Can't see any reference to RAID4 at all (so why it's hanging at that point is beyond me).

Still no idea how to fix it though... ;(

*** FURTHER UPDATE ***

After playing around with the partitions mounted from the boot CD - I decided to give it one last go booting from disk. I'm sure that it was hanging when booting from the previous kernel (2.6.17-10-generic) - but this time it seems to be working fine (apart from it having a fit when trying to fsck the drives 'cause I didn't unmount them cleanly)...

Oh no - wait a minute - rebooted after fscking the drives - selected the old kernel - and it's back to hanging at the "md: raid4 personality registered for level 4" again... WTF?!!?!!

*** SHEER MADNESS!!! ***

So - I can make the box boot. I just have to boot off CD. Go to a command prompt and manually mount the drives. Hit the reset switch so that the disks aren't cleanly unmounted. Then power the box back on (after removing the CD) - and it happily boots past the "md: raid4 personality registered for level 4" message and drops me at a command prompt where it wants me to manually fsck the disks.

There's obviously something screwy going on - 'cause the last things before the prompt are:

bash: no job control in this shell
bash: groups: command not found
bash: lesspipe: command not found
bash: dircolors: command not found

Other strangeness - when I fsck the filesystems - it tells me they are all clean already.

When I hit CTRL-D to kill the shell - it boots me into my normal graphical login prompt.

Does anyone have any idea what the fsck is going on?? This one has got me stumped...

---

