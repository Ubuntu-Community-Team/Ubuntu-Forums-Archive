---
title: "How to install alongside another Linux (GRUB issue)"
date: 2006-11-05
forum: Installation &amp; Upgrades
---

### Post by gzunk on 2006-11-05
I'm thinking about switching distro's, so I've downloaded the Ubuntu live cd and gone through the installation questions until it said that it was going to install grub on (hd0).

I already have grub installed on (hd0) and don't want Ubuntu to overwrite this, in case it screws up my existing distro and Windows installation. I'll edit the grub configuration myself so that I can boot Ubuntu (as long as I know where the kernel is going to go and what options it needs). How can I do this?

Well I've just attempted the alternate install CD with the text based installer and it refused to go past the partition selection stage saying that one of the two ext2 partitions that I have have an unsupported feature - Except of course that I had specifically told Ubuntu that I didn't want the existing partitions mounted so it shouldn't have mattered.

Isn't Ubuntu supposed to be easier than the alternatives?

---

### Post by ingo on 2006-11-06
to your first question: i recently installed Kubuntu on my desktop (alongside Suse and Debian) using the graphical install interface. I was able to state where I wanted to put GRUB, which I put in (hd0,6) I think.

to your second comment: mounted or not, they still get checked. once installed, you can of course edit your fstab as you see fit

to your third comment: yes, and it probably is for the normal user. your setup, however, is not 'normal'.

hth

---

### Post by rpkehoe on 2006-11-06
I had no problems when installing Ubuntu along side XP and mandrake, even with letting grub reinstall.  As I recall, Ubuntu picked up all OS's with no problem.  I would only suggest backing up your grub conf file, as depending on your other distro, it may use a different naming scheme.  You can always combine your conf files manually after install.

---

