---
title: "SOS:error after installation from windows-no main file system chosen!"
date: 2010-05-23
forum: Installation &amp; Upgrades
---

### Post by geosofie on 2010-05-23
Hello,

I just completed the ubuntu 10.04 installation using the windows' installer.
After the installation, the system reboot. I chose "ubuntu" from the OS selection screen.
A message appeared that the system would verify the installation parameters.

Suddently, a message was shown:
"no main file system chosen. Please solve this error from the partition menu."
And it wouldn't continue!!!!!!!!!!!!!!

Please help me...how can I find the partition menu and set the file system for the ubuntu?????

An idea would be to enter the installation cd for windows (as if I would wanted to format the pc)...wouldn't then the partition menu appear?????

---

### Post by dino99 on 2010-05-23
are you talking about wubi ?

mini howto: [http://ubuntuforums.org/showpost.php?p=9216264&postcount=14](http://ubuntuforums.org/showpost.php?p=9216264&postcount=14)

---

### Post by geosofie on 2010-05-23
well, the problem is, that I have already run the Ubuntu installation from windows.
So, if I run "partedmagic", can I just find the partition with the ubuntu and change the filesystem (I guess change it to ext3, right??) ???? Is this safe for the data already stored in  my disk????????????

---

### Post by dino99 on 2010-05-23
> **geosofie said:**
> well, the problem is, that I have already run the Ubuntu installation from windows.
So, if I run "partedmagic", can I just find the partition with the ubuntu and change the filesystem (I guess change it to ext3, right??) ???? Is this safe for the data already stored in  my disk????????????

if your data are mixed with the system partition, you will lost them, that why a /home is highly requested to keep your own work safe. Of course you only use partitioning tools on non active disk, so install partedmagic on a cd or usb stick and boot on it.

---

### Post by darkod on 2010-05-23
Yes, the OP is probably using wubi. So that link wouldn't apply and he shouldn't just start handling partition as if full ubuntu is installed.

Dino, I don't mean any disrespect, but I've seen you posting that same link in a lot of threads where it's not really related to the problem. So it can additionally confuse someone depending how much experience they have with linux.

Can you please not post the same link regardless what the problem is? In that link you are giving some procedure to prepare partitions in advance (which is not really needed but that's another subject) and how to install with the alternate cd. For most situations where someone has a problem with already installed ubuntu, there is nothing helpful in there.

@geosofie
It seems the wubi install went wrong somewhere. You could try booting windows and removing wubi (ubuntu) from Programs. After that try to install it again if you want.

But installing a proper dual boot ubuntu is much better than wubi, so you might consider that option too. Wubi is just for a quick try, it's not meant to be a long term install. And you can do the quick try with the cd in live mode too.

---

