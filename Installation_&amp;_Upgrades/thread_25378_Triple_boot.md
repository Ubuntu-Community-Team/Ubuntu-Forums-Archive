---
title: "Triple boot"
date: 2005-04-10
forum: Installation &amp; Upgrades
---

### Post by veritas366 on 2005-04-10
Hello,

I have XP on hda and fedora core 3 on hdb.  Currently they dual boot perfectly.  I was wondering if it is possible to "triple boot" with ubuntu.  Can I put Ubuntu on the same drive as Fedora? 


I suppose, for now, I can set up an entirely different file system...though I'd been thinking of putting my /home on a separate partition and then sharing between the two, if that's possible.

What I don't want is to have Ubuntu mess with my grub or mbr so that nothing works!  I had issues before, but I had burned my own iso's.  I'm hoping that with the free cd's (thanks!) I won't have the same debootstrap errors.  The problem was, once Ubuntu install had started it had messed with the MBR and I lost it...even attempts to fix the mbr didn't work.  (It did allow me to discover some fascinating security holes in XP, however.  Reset ALL passwords, anyone?)

IF there are two flavors of linux on one hard drive, will they fight or play nice?  Also, I assume that I would need a separate install of things like the Nvidia drivers.  Will such installs confuse the machine?  Is this a really stupid thing to try?

---

### Post by edubarr on 2005-04-10
I think that you won't have any problems as long as you keep the root partitions for both linux distributions separate. You can just edit your current version of grub to load the which ever kernel you want.

You can still have your /home mounted on a separate partition and have both distributions mount it. This will probably be a good idea if you want to have all your files accessible between the different systems.

---

### Post by jerome bettis on 2005-04-10
yeah you can do this.  i do it with ubuntu and gentoo.  i have a shared boot partition so both can use the same tweaked kernel, and a shared home partition so all my settings are the same everywhere.

lately i've been experimenting.  i boot into gentoo, mount my ubuntu partition, chroot into that and start gnome.  it's the best of both worlds.  all the good stuff of ubuntu running on a tweaked gentoo system.  plus i can run xfce4 and gnome at the same time.

i also have a windows partition which just collects dust, but it's there if i ever need it.

---

### Post by veritas366 on 2005-04-10
[QUOTE=jerome bettis]yeah you can do this.  i do it with ubuntu and gentoo.  i have a shared boot partition so both can use the same tweaked kernel, and a shared home partition so all my settings are the same everywhere.

lately i've been experimenting.  i boot into gentoo, mount my ubuntu partition, chroot into that and start gnome.  it's the best of both worlds.  all the good stuff of ubuntu running on a tweaked gentoo system.  plus i can run xfce4 and gnome at the same time.

i also have a windows partition which just collects dust, but it's there if i ever need it.[/QUOTE]
 First of all, thanks to Jerome Bettis for this information.  You are also one of my favorite running backs.  Are you coming back this year?  

Onto Linux.  I think I will not share the home directory.  You've had success but I saw some warnings that some distros like settings that one might find in /home different from other distros so sharing might be confusing.  No examples were given.  If I like Ubuntu better, I'll just move stuff over.

Some questions.

First, what, EXACTLY, does ubuntu do to the MBR of Windows?  I ask because I got half way through an install before, as I mentioned, and the MBR was gone...caused many headaches.  How can I be sure that if the install goes badly this time I won't have that problem...and are there any choices I need to make about Grub while installing ubuntu that I could get wrong???

Secondly, is there any advantage to sharing a boot partition if I haven't tweaked my kernel?  I don't even know how to tweak a kernel, so that's not an issue.  FC3 has two choices of kernel right now.  I stopped updating them because I had no interest in reinstalling Nvidia drivers every time, but I have two...any potential conflicts there?  

My primary interest is to see if certain things work better.  I"m having many multimedia issues in FC3 and I am just curious to see how Ubuntu handles.

And, as an added bonus, I see that my whole hdb is under a "logical volume manager" other than a little /boot partition.  I don't know how to mess with those.  I was too scared to try to install ubuntu as that LVM consists of pretty much the entire disk.  I don't really know what lvm is for or why fc3 uses that rather than just several partitions such as /swap and /  .  However, I don't know how to change it and safely free up space (of which I actually have plenty.)

---

