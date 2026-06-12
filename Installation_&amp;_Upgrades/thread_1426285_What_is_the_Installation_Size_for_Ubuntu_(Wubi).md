---
title: "What is the Installation Size for Ubuntu (Wubi)?"
date: 2010-03-10
forum: Installation &amp; Upgrades
---

### Post by dreamstone007 on 2010-03-10
[FONT=&quot]Hi friends,[/FONT]

[FONT=&quot]I need to install Ubuntu inside of Windows XP, but the installer ask me to enter an (installation size) that should vary between 3 to 30GBs. I have an internal hard disk of 60GBs with 30GBs free. My question is if I allocated 30GBs for Ubuntu, would I be able to use this space in both Windows and Ubuntu? The only reason that I'm using the Wubi method is because I don't wand to lose space from portioning the hard drive.[/FONT]

---

### Post by Fafler on 2010-03-10
No. You could, however, make a smaller filesystem for Ubuntu and use the rest of the Windows filesystem from inside Ubuntu. I wouldn't go much lower than 10 gb.

---

### Post by Mark Phelps on 2010-03-10
> **dreamstone007 said:**
> ...The only reason that I'm using the Wubi method is because I don't wand to lose space from portioning the hard drive.[/FONT]

Bad reason ... because you will "lose space".  The Ubuntu installation will be implemented as a single file on your hard drive. So basically, that space will be used up by Ubuntu.

If that's your "only reason", I strong suggest that you consider doing a traditional dual-boot -- with Ubuntu in its own, separate, partitions.  You'll benefit from that in the long run and you can decide you much space to "lose" when you do the partitioning.

---

### Post by NonaMannequin on 2010-04-30
Follow the on-screen instructions to install Ubuntu. If you are  installing alongside an existing operating system and you do not want to  destroy it and all your data, be sure you select the option to resize  existing partitions and install side by side. Changes made after this  point are generally irreversable. Once you have given the installer all  necessary information and options, it will install Ubuntu on your  system. Depending on your hardware, this can take up to 30 minutes, but  most modern systems should install fairly quickly.

---

