---
title: "lost my vista"
date: 2008-11-29
forum: Installation &amp; Upgrades
---

### Post by 3adijidan on 2008-11-29
Hey,
i just installed ubuntu for the 1st time on my laptop. I wanted to dual boot vista with ubuntu but now i found out that i lost, or think i lost, my vista. can u help me?

  Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       18705   150247881   83  Linux
/dev/sda2           18706       19457     6040440    5  Extended
/dev/sda5           18706       19457     6040408+  82  Linux swap / Solaris

does that mean i lost it completely?

---

### Post by doas777 on 2008-11-29
it's my understanding that you should see the windows partition in 'fdisk -l'. as you have shown, it isn't there. you might want to confirm with gparted though.

good luck,
franklin

---

### Post by linuxguymarshall on 2008-11-29
I am a realist so I'm not going to sugar coat it. You are what in the technical world call "Totally and irreversibly, screwed." Pull out those reinstall CD's. You have along day ahead of you.

---

### Post by davidbilla on 2008-11-29
How did you partition your disk when installing Ubuntu? Did you let Ubuntu do it, or did you do manual partitioning? If you had let Ubuntu do it, then sure as surity you've removed your vista. Or if you are sure that you'd left your vista intact while installing Ubuntu, go to Places->Removable Media-> and see whether your other hard disks or partitions are listed there.

If anything is listed there, then just click on it to mount it and check whether your vista is intact. If it is, then all you may have to do is to just edit '/boot/grub/menu.lst' which we'll come to later once you've verified the presence of vista.

---

