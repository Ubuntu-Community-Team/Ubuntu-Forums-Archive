---
title: "resize partition question"
date: 2009-11-20
forum: Installation &amp; Upgrades
---

### Post by proevofanatik on 2009-11-20
i have vista dual booted with kubuntu 9.10. is it possible to delete vista and keep kubuntu installed and resize the kubuntu partition to the full size of the hard drive? if yes. how is it done?

---

### Post by emigrant on 2009-11-20
you can do this using gparted:
system>administration>disk partitioner

---

### Post by SuperSonic4 on 2009-11-20
> **emigrant said:**
> you can do this using gparted:
system>administration>disk partitioner

I wish people would actually read the question when relating to **Kubuntu**

You can run the partitionmanager as root ```
kdesu partitionmanager
```

---

### Post by proevofanatik on 2009-11-20
~$ kdesu partitionmanager
kdesu: command not found


thats whats happening when i run that in terminal

---

### Post by proevofanatik on 2009-11-20
i have just instlled partition manager in packagekit. what do i do on here? i dont want to delete anything im not supposed to

---

### Post by darkod on 2009-11-20
I don't know how exactly it looks, but usually you click on the wanted partition, and either with right-click or in some menu called Partition there should be Resize or Shrink/Expand option.

You can shrink windows partitions from your Kubuntu running but for expanding the / partition you will have to boot with Kubuntu live CD because then it's running from the CD and make sure / is not mounted.
No partition manager could expand it while mounted and if you are booting the regular Kubuntu installation / will be mounted.

---

### Post by proevofanatik on 2009-11-20
heres my partition manager here

i want vista to dissapear from grub and have just kubunu left with the rest of the hard drive. what linux partition will i have to resize after i delete the windows partition?

[[IMG]http://img340.imageshack.us/img340/4058/snapshot1p.png[/IMG]](http://img340.imageshack.us/i/snapshot1p.png/)

---

### Post by darkod on 2009-11-20
With that setup if you want vista completely gone I think it's best to reinstall Kubuntu on the whole drive. When you delete vista partition (/dev/sda1) then only your extended partition will remain. You could probably expand it (never tried) but it would be a very strange setup on the disk with no primary partitions and just extended one.
Plus your kubuntu partition /dev/sda2 will become /dev/sda1 after deleting vista partition and most probably grub will not be able to find your kubuntu installation anyway.
If you can consider reinstalling kubuntu, it would save you lot of work and produce immediate result. Otherwise you might spend hours troubleshooting.

---

### Post by proevofanatik on 2009-11-20
i thought that too m8. ill reinstall when i get my new graphics card.

thanks for the help

---

### Post by n3140f on 2009-11-25
so - let be all retarded - I istqalled windows because I anticipate buying and audio interface for using a software synth.

Unfortunately after installin windows, ubuntu installed on a 2 meg partition.  Now I can't get a partition editor into windows or ubuntu.

What a waste of time - now how do I change the size of that ubunmtu partition?

Why did this peice of junk install on a 2 meg partition.

I have the gnome partition editor on a live cd and it won't install on windows.

You guys can talk up ubuntu all you want - but the audio has been in litigation for years.

You need a server - you are fine - you need an audio workstation - you can go shoot yourself in the head.

Why can't I ihnstall gnome partition editor in windows to solve this rediculous problem?


The problem is = after installing windows = Ubuntu installed on a 2 meg partition.

Alsa is great - but until it actually works and the lawyers go away = it is usleless to me.

Buying the interface with the windows software and runnning f-ing windows to make sound - and that is really sad.

---

### Post by Mark Phelps on 2009-11-25
n3140f:

Yours is a different problem than the one posted here.  This problem is specific to partition management in Kubuntu -- yours is not.

Please don't hijack this thread for your problem but start a new thread instead.

Thanks

---

