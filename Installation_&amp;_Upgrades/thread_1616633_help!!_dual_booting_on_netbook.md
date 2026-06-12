---
title: "help!! dual booting on netbook"
date: 2010-11-08
forum: Installation &amp; Upgrades
---

### Post by simelinux on 2010-11-08
i am trying to dual boot ubuntu netbook edition along with xp but i get stuck at setting up the partitions. at the installation i have the option of installing alongside xp however when they show the graph it looks like they want me to share ubuntu on C:/ drive so that xp gets 60Gb and ubuntu gets 20Gb. What i would like to do is keep xp on the C:/ drive and install ubuntu on the D:/ drive so that windows and ubuntu each get 80GB.

What i have done so far is go into gparted and delete the D:/ drive so i have now 80Gb of unallocated space. however when i start the installation process and choose "install alongside other OS" it still chooses to share it with my C:/ drive. i would like to be walked through the process of splitting the hard drive so i can install ubuntu on D drive. also i know i need to create a swap partition do i do that before the installation of after?

 I am a linux noob so please talk barney language to me. i really wanna ditch windows.
also it might help to say i have asus eee pc 1000.

---

### Post by sikander3786 on 2010-11-08
Hi and Welcome Ubuntu Linux and the forums :popcorn:

If you have deleted the D: drive and it is just an unallocated space, you need to choose the "Use the largest continuous space" option and that will automatically create all the necessary partitions and will install Ubuntu without touching your Windows drive.

If you choose the way I mentioned above, Swap partition will automatically be setup so you don't need to worry about that.

You can also go for the manual partitioning but it would be bit of an advanced setup.

Post back if you've got any doubts.

---

### Post by simelinux on 2010-11-08
thank you for responding. however i dont get an option "use largest continous space"
this is what i get:

once i choose the option to install along another OS i am brought to another window that asks me to chose entire disk or choose entire partition?

---

### Post by sikander3786 on 2010-11-08
Sorry I think that option got removed in 10.10 installer.

I am not 100% sure about that so you might wish to wait for some other experienced replies. I think it should have been renamed to choose entire partition but it would be risky to proceed without knowing what you are doing as I am not sure either.

I can help if you want to do manual partitioning. Or just wait and some other mate will jump in soon.

---

### Post by simelinux on 2010-11-08
thank you for your help

---

