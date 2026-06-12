---
title: "Grub Rescue prompts after formatting"
date: 2011-08-17
forum: Installation &amp; Upgrades
---

### Post by Sir Andrew on 2011-08-17
Up until yesterday I had Ubuntu and Kubuntu installed to dual-boot using the GRUB loader installed by Kubuntu. I mistakenly formatted the Kununtu partition to NTFS in an attempt to install Windows XP in its place without updating grub to pull the files from my Ubuntu partition.

Now, when I go to boot the computer, I receive a the "error: unknown filesystem" and the grub rescue prompts for commands. I've attempted to boot from both a Ubuntu Live CD and a Secured Ubuntu CD with boot repair built into it, but receive the same message both times. I know this isn't an issue with my boot order (I've changed that), and my computer will boot into a Windows XP setup disc (which will not proceed for a different reason)

---

### Post by Sir Andrew on 2011-08-17
Fixed! Just follow the directions on the Grub 2 page on the Ubuntu wiki: [https://help.ubuntu.com/community/Grub2#Rescue](https://help.ubuntu.com/community/Grub2#Rescue) Mode (''grub rescue>'') Booting

---

