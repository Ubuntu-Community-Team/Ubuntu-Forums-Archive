---
title: "install from scratch keeping my home partition"
date: 2005-10-15
forum: Installation &amp; Upgrades
---

### Post by jnoreiko on 2005-10-15
upgrading broke my hoary installation (in another thread on this board...)

I think the only thing to do now is install breezy from scratch.

I have root and home on two different partitions.
How do I tell the installer to use an existing partition as users' home folders and not change anything on it?

---

### Post by Pluk on 2005-10-15
At the partition part in the installer choose to manually partition.
In there you can choose you root and swap partition to format and select your home partition to keep its current data and mount it as /home.

---

### Post by jnoreiko on 2005-10-15
that's what I thought, wanted to make sure.
thanks! :)

---

### Post by jnoreiko on 2005-10-16
does the same apply to the /boot partition?
I've got grub set up to dual boot windows.

---

### Post by mikeyman on 2005-10-16
I wouldn't sweat /boot. The installer will most times find your windows partition and add the corresponidng entry in GRUB. You can even configure it to be mounted on boot up.

---

### Post by jdawdy on 2005-10-17
I too had /home on a seperate parition, however I did not specify this at installation.  Is there any way I can link the  /home directory on the seperate partition to  my /home diretory on the root (linux install) partition?


Jim

---

### Post by jnoreiko on 2005-10-17
mounting a partition on /home automatically hides whatever was already on /home before, so just altering your list of volumes to mount should do it.

you'll be left with an inaccessible /home on your main partition though. I'm not sure what the best way to get rid of that is.

---

### Post by jdawdy on 2005-10-20
I modified fstab to mount hda5 on /home and it works well.

I now realize that using the option of creating /home on a seperate partition has an added advantage for upgrading Ubuntu.  If you choose to go with a fresh install (as I did), or even if your upgrade doesnt go well and you need to do a fresh install,  you don't have to worry about losing all your files, or backing them up (major PITA). 

Yes, I know.  Duh.  But coming from windows thats not intuitive.

---

### Post by jnoreiko on 2005-10-20
You can sort of do the same with windows, and keep all your documents on another partition, but you'll still lose all your personal settings that are in the registry :(

---

### Post by jvalatka on 2005-11-02
I too would like to keep my home partition and install breezy system files from scratch.  However, when I get to the part where I can alter the partitions, I don't get a list of existing partitions, but instead:

???    ???

And selecting "Go Back" or "Continue" doesn't get me anywhere, but the same partitioning window with:

???    ???

And I would see a list of errors flash when I try to escape from this pit, something like multiple lines of "E: unsupported action".

What's the deal?
:(

---

