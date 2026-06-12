---
title: "Getting GRUB error 17, can't load ubuntu because of it"
date: 2006-10-01
forum: Installation &amp; Upgrades
---

### Post by bomber991 on 2006-10-01
I'm not too sure how to go about fixing this problem, but I was wondering if there were different bootloaders I could just install and try instead.

I installed ubuntu on my eide slave drive.  Now when I turn on my PC, it shows the bios screen like usual, then it says:

"Grub loading....

Grub Error 17"

Then that's it.  I've already repaired my MBR with the windows disc, but I really want to try out ubuntu.

The way I have my system setup, is that I have two eide hd's, and one serial ata hd.  I installed ubuntu on the slave eide HD, and I have my windows installation on the master eide hd.

So uh, how can I go about fixing this?  Because right now I can't boot into the Ubuntu installation that I have on my hard-drive.

---

### Post by Herman on 2006-10-01
Get a [Super Grub Disk]("http://adrian15.raulete.net/grub/tiki-index.php"), you can boot with that for the time being.

When you feel like it, sometime when you are booting, rather than booting up by the menus, press 'c' to get into Super Grub's [Command Line Interface]("http://users.bigpond.net.au/hermanzone/p15.htm#cli")
(other versions of Grub have that too). 
Use the Command Line to investigate your computer, 
                                    How to get GRUB's Command Line to investigate a computer.........................................[GO]("http://users.bigpond.net.au/hermanzone/p15.htm#How_to_get_GRUBs_Command_Line_to_investigate_a_computer")

Boot Ubuntu up with the information you find out from the CLI mode Grub, taking notes while you are doing it. You can edit your menu.lst with the same information.

[Edit your /boot/grub/menu.lst file]("http://users.bigpond.net.au/hermanzone/p15.htm#orientation") with the correct details, 

and re-install Grub to MBR, with Super Grub Disk.

Regards, Herman :D

---

### Post by bomber991 on 2006-10-02
Well, I'm not quite sure what exactly I did, but I used that super grub program and it was still giving me error 17.  I eventually did something and it got fixed.  Now I have to figure out how to get grub to show up automatically everytime so that I don't have to insert the supergrub disc, but I will make a seperate thread for that issue if I can't figure it out on my own.

Thanks Herman, I don't know if this is one of those boards that lets me give +rep or +carma, but thanks man.

---

### Post by bomber991 on 2006-10-02
Alright, I really don't know what the hell I did, but now grub works just fine and I don't even have to insert the super grub disc.  So, thanks again Herman!

---

### Post by Herman on 2006-10-02
bomber991,
That's great, I'm glad you got it fixed. I guess it doesn't matter how, just as long as it's fixed. :D
Super Grub Disk is very fast!
Regards, Herman

---

### Post by unusednameihope on 2006-10-13
Sorry to reopen this tpic, but i am struglling with the grub error for two days now.
I tried all possible Super grub options but to no avail. I am new to Linux and it seems i will stay this way, because it's impossible to get a clean install on a fresh computer. 
I do not have a clue how to solve this problem. It seems i get more and more partitions during my repair activities.
Please advice.

---

### Post by Herman on 2006-10-13
Hello unusednameihope,
Are you installing Ubuntu with the Ubuntu Dapper 'Desktop' Live/Install CD? If you are, have you got any good instructions you can follow to guide you through all the steps of the installation so that you are sure you are doing everything correctly?
For the Ubuntu Dapper Desktop Live/Install CD, I use and recommend aysiu's web site, here is the link, [http://www.psychocats.net/ubuntu/windowstoubuntu.html](http://www.psychocats.net/ubuntu/windowstoubuntu.html)

If you already have too many partitions, I would delete them all and start again, following the guide in the above link.
if you still get a Grub error, then please tell me the error number and show me a copy of what you see when you type 'sudo fdisk -lu' into a terminal in the Live CD, ```
sudo fdisk -lu
``` Also, tell me a little bit more about what kind of computer you have. Is it old or new? One hard disk or two? IDE disks or Sata? How much RAM has it got, and anything else that might make a difference to the situation, please. :D

Regards, Herman :D

---

