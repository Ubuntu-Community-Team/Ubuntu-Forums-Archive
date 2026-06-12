---
title: "ubuntu with a seperate boot partition"
date: 2006-07-17
forum: Installation &amp; Upgrades
---

### Post by dolby on 2006-07-17
i changed my partition scheme to the following one

```


dev/hda1 /boot
dev/hda2 swap
dev/hda3 /


```

but when logged in & updated the kernel boot was reassigned to / .

only thread on the forums that helped a bit was [this](http://www.ubuntuforums.org/showthread.php?t=119512&highlight=boot+partition)

suggesting changing # kopt=root=/ & # groot= but that can be done only after the reassigning of the mount point. how do i  prevent this from happening again before i update the kernel?

---

### Post by dolby on 2006-07-18
doesnt anyone know?

---

### Post by notepad on 2008-05-16
i know this post is 2 years old now but im curious. were you saying that the system wouldnt boot at all and thats why you couldnt change your grub/menu.lst?

i trust you worked out to run from a livecd and sudo -i to get access to your /mnt/hda1 so that you could make the necessary changes?

---

