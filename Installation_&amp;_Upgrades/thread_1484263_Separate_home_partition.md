---
title: "Separate /home partition"
date: 2010-05-15
forum: Installation &amp; Upgrades
---

### Post by Cathhsmom on 2010-05-15
My Experience Level: dangerous and brave.   Question: I am planning on reformatting my hard drive on my laptop and having a partition dedicated as /home.   When I install Ubuntu, will it create another /home directory or is there a prompt or place that I can tell to use the separate /home partition.  And if my question is not clear, it is probably because I do not understand how to integrate this separate /home partition.  Thanks in advance for the help.

---

### Post by darkod on 2010-05-15
The guided methods in the installer create only root+swap system.
For separate /home you need to select Manual Partitioning (bottom option in step 4 I think). That will open a window showing your disk(s) and partitions.

You will need to create a minimum of 3 partitions, for /, /home and swap. Dedicate as much space as you want to either of them.
Few hints:
For swap 2GB is enough, or if you plan to use hibernate regularly make it 1.5 x memory size.
For / 10GB is more or less enough, because ubuntu is not very space demanding for software, and with separate /home you keep all your personal files like photos, videos, music on it. If you have hdd space to spare, give / 15GB.
The rest can go to /home.

When creating the partitions, for swap select swap area for filesystem (and no need for mount point for swap). For / select ext4 and mount point /. For the separate /home select ext4 and mount point /home.
That is how ubuntu will know to use your separate partition as Home, because you specify the mount point /home.

That should be it. Any questions, ask.

---

### Post by Cathhsmom on 2010-05-15
Thanks, I have printed out your notes.   

I am expecting a new external hard drive sometime next week.  And then, we will have fun redoing my computer.

---

