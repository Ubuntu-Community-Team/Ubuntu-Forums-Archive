---
title: "Help me with my installation :("
date: 2008-04-30
forum: Installation &amp; Upgrades
---

### Post by jorgecarrillo150990 on 2008-04-30
==THIS IS NOT THE IMPORTANT STUFF==
I have been an Ubuntu User for a year, happily dual-booting XP and Ubuntu.
A few months ago, I had to delete my WIndows partition for some problems it was causing, but now I am missing my games.
Hardy came and I saw an opportunity to install windows back, so I installed it and now I am trying to install Hardy.

==IMPORTANT STUFF STARTS HERE==
The problem is that I can't resize my XP partition.
When doing the installation I only get two option in the partitioning screen: Guided (using the full disk) and Manual.
It seems that in Manual I cannot create any new partitions.
So I went to Xp, fragmentized the disk and came back to Ubuntu, still I can't resize it.
I went to GParted and I can't resize my Windows partition.
I really want to dual-boot again, so can anyone help me?

---

### Post by jorgecarrillo150990 on 2008-04-30
Bump (I'm in a hurry)

---

### Post by Rallg on 2008-04-30
Try this: Download and burn the "System Rescue CD" iso (find it easily on the Internet). It is a Linux-based live CD including GParted. In the past, it has worked for me on occasions when other things did not work.

When you boot it, you will get terminal text. Eventually the text will stop and await further instructions. It does give you suggestions as to what to type. For me, "startx" (without the quotes) works and provides a GUI. If that does not work on your graphics card, there are safer alternatives.

When you finish, you exit the live desktop by going to its terminal, with
shutdown -r now
to reboot to your ordinary boot loader. If that doesn't work, try
sudo -s
shutdown -r now
to exit the live CD.

Important caution: Your Windows installation might use the Windows partition starting point as a means of determining whether or not your copy of Windows is authentic. Do not move the starting point of your Windows partition unless you are prepared to re-install Windows, or at least re-validate it!

---

