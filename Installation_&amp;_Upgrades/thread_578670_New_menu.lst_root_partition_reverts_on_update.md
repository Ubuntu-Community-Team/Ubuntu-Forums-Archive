---
title: "New menu.lst root partition reverts on update"
date: 2007-10-17
forum: Installation &amp; Upgrades
---

### Post by GeekCat on 2007-10-17
Hi,

I have skulked the Web and Forums and have almost found (but not quite) the answer to this question.
I recently added a Raid card to my computer and changed the root partition in Grub menu.lst to (Xen kernel):

module		/vmlinuz-2.6.22-13-xen root=/dev/mapper/RaidGroup-RootVol ro console=tty0

Everything worked great.  When I updated the kernel using update-manager, the root volume reverted to the original install root partition:

module		/vmlinuz-2.6.22-14-xen root=/dev/mapper/Stemp-TmpRootVol ro console=tty0

I had to edit menu.lst manually to go back to my new root.

There must be an update configuration file that I can't find to tell updater what root volume to put in menu.lst.  Can you help me find that file?

Thanks..

---

### Post by logos34 on 2007-10-17
you forgot to change the 'groot' line (~ line 74 i think)

---

### Post by GeekCat on 2007-10-18
I'll give it a try.

Thanks..

---

