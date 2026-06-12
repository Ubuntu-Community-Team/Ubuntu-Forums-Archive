---
title: "dual booting w/ xp"
date: 2006-04-20
forum: Installation &amp; Upgrades
---

### Post by darklemming54 on 2006-04-20
i am planing on dual booting with xp so i made 3 partions 
nfts
ext2
swap
before installing i wanted to go to xp, so i exited installer and get "insert system disk" when i boot.  how do i get to xp before installing ubuntu?

---

### Post by Derek Djons on 2006-04-20
I'm afraid you might have overwritten Microsoft's Windows MBR (Master Boot Record).

You can use the Microsoft Windows XP disc and boot up the installer utility. Instead of choosing a new installation you can choose 'R' (Rescue). It will start a CLI in which you can execute the command 'fixmbr' This command gives you the option to write a new standard MBR for Windows XP. Use -help to see the commands options.

After that you should be able to boot your current installation.

---

