---
title: "Keep hands off Swap Partitions"
date: 2005-06-23
forum: Installation &amp; Upgrades
---

### Post by Jim2 on 2005-06-23
I have several other distros on the same hard as I am trying to instal ubuntu. I have tried using the partitioner as well as Partition Magic to set up two partitions. An EXT2 and a Swap partition. In both cases the partitioner wants to format the other swap partitions from the other distros on the hard drive. Why?

 [-X

---

### Post by mingus on 2005-06-24
I can't say why, but I have observed the same thing installing many different distros.  It has always been harmless.

---

### Post by Jim2 on 2005-06-24
[QUOTE=mingus]I can't say why, but I have observed the same thing installing many different distros.  It has always been harmless.[/QUOTE]

So are you saying that allowing the ubuntu installer to format the other swap partitions are not boing to cause problems with the existing distros?

---

### Post by TravisNewman on 2005-06-24
[QUOTE=Jim2]So are you saying that allowing the ubuntu installer to format the other swap partitions are not boing to cause problems with the existing distros?[/QUOTE]
 You only need one swap partition. It's just a partition used as virtual memory, so when the ram is full it can use it. You only need one swap partition that can be shared by every distro on your system (linux distro, that is). It's totally fine that it wants to format it.

---

### Post by mingus on 2005-06-24
[QUOTE=Jim2]So are you saying that allowing the ubuntu installer to format the other swap partitions are not boing to cause problems with the existing distros?[/QUOTE]

panickedthumb is exactly correct . . . usually when a distro installs, it already sees an existing swap and doesn't try to add another.  While it doesn't hurt to have more than one, with today's RAM it is not necessary.  All distros can share the same swap partition.  And yes, reformatting swap is harmless - it's just raw disk space.

---

### Post by afonic on 2005-06-24
[QUOTE=Jim2]So are you saying that allowing the ubuntu installer to format the other swap partitions are not boing to cause problems with the existing distros?[/QUOTE]
 Exactly. The other distros only use this space as a temponary space when they are running.

However if you don't want to format it you can easily select it by making the partitions manually.

---

### Post by Jim2 on 2005-06-24
[QUOTE=afonic]Exactly. The other distros only use this space as a temponary space when they are running.

However if you don't want to format it you can easily select it by making the partitions manually.[/QUOTE]


Sorry but I already tried that using Partition Magic and using  and the Ubuntu's partitioner to assign the mount point but Ubuntu still forces one to format the existing Swap partitions.

---

