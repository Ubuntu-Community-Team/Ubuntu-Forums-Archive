---
title: "Get out of dual boot."
date: 2008-01-26
forum: Installation &amp; Upgrades
---

### Post by travist120 on 2008-01-26
Hey, I've had Ubuntu Gutsy installed on my laptop some time now. I've found that I haven't had any problems any more, even after running ubuntu on it for 5 months. I just want to know, is there anything I have to do before I completely delete my windows vista partition? Under gparted, it shows up that it has the boot flag. I don't know if this has anything to do with Grub, or if it is nonessential. I would also like to know how I can use the new space and make my ubuntu partition MUCH bigger. Thanks for your help!

---

### Post by forestpixie on 2008-01-26
I'd be inclined towards using to using gparted to reformat the partition to ext3 and using it as a seperate partition and mounting it in fstab - you might need to reinstall grub - either with supergrub or the livecd

---

### Post by travist120 on 2008-01-26
shouldnt there be a simpler way of doing that? I dont have the live cd anymore, or supergrrub. I'd rather not destroy my ubuntu by trying to give it some more space.

---

### Post by Pumalite on 2008-01-26
They gave you good advice. Follow it.

---

### Post by shad0w_walker on 2008-01-26
Why don't you have the livecd anymore? It's a good thing to have around and when something goes wrong (And it will, either by faulty hardware, iffy update or just by user error) your best way to fix it is most likely the livecd. Get another copy and keep the thing around.

---

### Post by Partyboi2 on 2008-01-26
Just to add my 2 cents :) When you do partition work you need to have the partition unmounted to work on it. So livecd is the best way to go.

---

### Post by travist120 on 2008-01-27
Yes I understand this. I just thought there would be an easier way. Now how would I go about doing this with a live cd? I know I need to partition, but how would I get grub onto my ext3 partition instead of my ntfs partition? IS there a specific command I could type into terminal?

---

### Post by forestpixie on 2008-01-27
boot with the cd - go to partition editor in system>admin - assuming that the partition isn't mounted delete the ntfs partition and format to ext3 or whatever you want, if it is you'll need to unmount it first

this page should help with restoring grub
[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

once you've done that and rebooted you'll need to dela with mounting the partition and getting it in your fstab so it mounts at boot time
[http://www.psychocats.net/ubuntu/mountlinux](http://www.psychocats.net/ubuntu/mountlinux)

---

