---
title: "Gave up on Wubi, planning traditional installation"
date: 2008-07-22
forum: Installation &amp; Upgrades
---

### Post by ebolaRETURNS on 2008-07-22
Hi all.
So Wubi isn't really working for me.  It looks like I may want to make a dedicated partition and just install normally.  SO, then the questions/issues:
1.  What I need to do is take a blank portion of an existing windows partition, devoting it to a new and blank Linux partition.  I am working under severe space limitations.  The linux partition will be 8 gigs.
--How difficult is this?  Where should I look find info on how?
--How risky is this?  Should I do a FULL back-up and be prepared to do a fresh format on everything?
2.  I need to install Ubuntu and set up the menu for dual boot.
[same dashed questions.}
3.  Then I need to get Ubuntu to "see" my windows partitions, so I can just store shared media files on those...and maybe to toy with windows emulators and WINE.
--again, looking for difficulty and how-tos.

thanks!

---

### Post by Partyboi2 on 2008-07-22
[[COLOR=Blue]Here[/COLOR]]("http://apcmag.com/the_definitive_dualbooting_guide_linux_vista_and_xp_stepbystep.htm") is howto if you are going to dual boot xp and ubuntu
[[COLOR=Blue]Here[/COLOR]]("http://apcmag.com/how_to_dualboot_vista_with_linux_vista_installed_first.htm") is one for vista and ubuntu
Always a good practice to backup your important data before working on partitions.
After you have installed ubuntu you should be able to read/write to your windows partition.
Wine is in the ubuntu repos you can install it by going to Applications>Add/Remove and searching wine and then install it by clicking on the "apply" button
or you can install it from the terminal (Applications>Accessories>Terminal)
```
sudo apt-get install wine
```

---

### Post by ebolaRETURNS on 2008-07-22
Thanks!

---

