---
title: "trouble installing ubuntu 5.10 on my laptop"
date: 2005-11-29
forum: Installation &amp; Upgrades
---

### Post by zwcp on 2005-11-29
Hi...

I'm new to this forum and linux in general, but none the less I hope someone can help me...

Im trying to install ubuntu version 5.10 on my old Toshiba Satellite Pro 4220 XCDT laptop. Its got an 6 GB harddrive, 192 ram and 450 Mhz cpu.

Im using the installation CD supplied and shipped by ubuntu. 

Heres the problem/s:

im using the basic setupmode and letting ubuntu guide me through the installation. 
the process works fine up until we get to the point where it starts to instal the additional packages, right after it has installed the basic system... 
After a while it comes up with af screen saying, that: "you havent got enough disk space for the installation, and would i like to continue anyways?". 
According to the info on the CD case, it only requires 1.8 GB of disk space to install, and ive got 6 GB, so why does it write this?

I then press "continue" and move on, hoping to fix the problem later. The program runs the rest of the setup, and then finaly prompts: "remove CD to make sure the computer boots up from the harddrive where you installed the programs".
It shuts down and reboots starting up with the ubuntu logo, and show af list of the stuff its attempting to start up... everything gets an "ok" and the screen now changes again to the same type of oldfashioned screen used during the initial instalment. 

The screens titel says: "installing packages", further down its says "preparing for installation" and theres a proces bar reading "0 %".... 

and then it stops... nothing else happens... Ive tried to shut down the computer and start it up again, but in allways ends up the same way, with the same screen saying "installing packages" and the proces bar reading "0 %"...


What am i doing wrong and can anyone help me...

Kind regards

Anders from Denmark

---

### Post by bwog on 2005-11-29
Strange, can you give information on the partitions that were made? You can see them with gparted (Live CD) or when you follow the install procedure to guided partition.

---

### Post by bwog on 2005-11-29
What you can try anyway is to make the partitions in guided partitioning: make a 5.5GB / (root) partition (bootable, ext3), and 0.5 GB /swap.

Do a default installation first, to see if it works.

Later, you can install again with xfce instead of Gnome, it is less demanding on the hardware. See: [http://ubuntuforums.org/showthread.php?t=75971&highlight=howto+xfce](http://ubuntuforums.org/showthread.php?t=75971&highlight=howto+xfce)

---

### Post by zwcp on 2005-11-29
[QUOTE=bwog]What you can try anyway is to make the partitions in guided partitioning: make a 5.5GB / (root) partition (bootable, ext3), and 0.5 GB /swap.

Do a default installation first, to see if it works.

Later, you can install again with xfce instead of Gnome, it is less demanding on the hardware. See: [http://ubuntuforums.org/showthread.php?t=75971&highlight=howto+xfce](http://ubuntuforums.org/showthread.php?t=75971&highlight=howto+xfce)[/QUOTE]

I realized to late that there was a section further down for linux newbies so i copy/paste'd my question into that section aswell... And, as in this section ive gotten the same answer....

I'm trying a new install right now, its taking a while. Im trying to do it via the guided setup version, and so far it seems to be working, but i'll let you guys know how it works out, asap...

Thanks :-)

---

### Post by zwcp on 2005-11-29
[QUOTE=zwcp]I realized to late that there was a section further down for linux newbies so i copy/paste'd my question into that section aswell... And, as in this section ive gotten the same answer....

I'm trying a new install right now, its taking a while. Im trying to do it via the guided setup version, and so far it seems to be working, but i'll let you guys know how it works out, asap...

Thanks :-)[/QUOTE]

It works :D

lets shut this question down... ive got another new question in in my other thread in the beginners forum... Same topic as this one, check it out

thanks for the replies...

---

### Post by atoponce on 2005-11-29
[quote=zwcp]It works :D

lets shut this question down... ive got another new question in in my other thread in the beginners forum... Same topic as this one, check it out

thanks for the replies...[/quote]

Please don't double-post.  Thanks.

---

