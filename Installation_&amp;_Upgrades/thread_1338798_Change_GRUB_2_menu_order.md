---
title: "Change GRUB 2 menu order"
date: 2009-11-26
forum: Installation &amp; Upgrades
---

### Post by Fuzzy Toaster on 2009-11-26
I've just installed Ubuntu 9.10, dual booting with Windows 7. I understand that GRUB 2 doesn't have a menu.lst anymore, and I know about /etc/default/grub. What I want to know is, how do you change the order of the boot options when GRUB 2 starts up? Currently it's:

ubuntu9.10
ubuntu recovery
ubuntu memtest
windows

But I obviously want to boot windows more than run a memory test, so I want windows to be the second entry.

Appreciate any help.

---

### Post by oldfred on 2009-11-27
You really could not do what you ask in old grub's menu.lst as the Ubuntu entries were within the automagic area and were rewritten with every update to a kernel. So a windows entry could not be in between the Ubuntu entries.

Files are processed in the number order of the entires in /etc/grub.d You can reorder if you must or copy all manual entries into 40_custom and run just that with everything else turned off. I am sure most of this would not be recommended.

[http://members.iinet.net/~herman546/p20/GRUB2%20Edit%20Mode.html]("http://members.iinet.net/%7Eherman546/p20/GRUB2%20Edit%20Mode.html") 
[https://wiki.ubuntu.com/Grub2#Adding%20Entries%20to%20Grub%202](https://wiki.ubuntu.com/Grub2#Adding%20Entries%20to%20Grub%202) 
[http://members.iinet.net/~herman546/p20/GRUB2%20Configuration%20File%20Commands.html]("http://members.iinet.net/%7Eherman546/p20/GRUB2%20Configuration%20File%20Commands.html")

For total customization install your own grub partition and use it
Page down about 2 pages in this link.
[http://members.iinet.net/~herman546/p20/GRUB2%20Bash%20Commands.html#grub-install](http://members.iinet.net/~herman546/p20/GRUB2%20Bash%20Commands.html#grub-install)

---

