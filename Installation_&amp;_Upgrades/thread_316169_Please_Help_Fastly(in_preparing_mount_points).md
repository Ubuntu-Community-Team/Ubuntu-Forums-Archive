---
title: "Please Help Fastly(in preparing mount points)"
date: 2006-12-10
forum: Installation &amp; Upgrades
---

### Post by Khaled-F on 2006-12-10
hi all ..
im khaled
i like open sources and i decided to use linux
i choosed ubuntu 6.30 cauz it's the best ..:) 
here's the prob
i installed
ubuntu 6.10 desktop
from the windows
and burned it on a cd
then i created a partition ex3 4 linux(6 GB) and created a swap partition(700 M.B) and puted the cd and went into the install operation
now everything is fine until i reached the prepare mount point operation
i choosed the swap and puted "right" in reformat
like this
[IMG]http://www.elmsry.com/prob.png[/IMG]
now i want to choose
/media/hdc6 (6 GB)
to install linux inside it
but every time i press forward
it can't go forward and it's a error
NO Root file system
what shoud i do
plz help me quickly:confused
best wishes
khaled

---

### Post by Khaled-F on 2006-12-10
Please i needs u fastly ...
:( :???:

---

### Post by Peter76 on 2006-12-10
/media/hdc6 is the actual mountpoint of your sixth partition ( as seen by the installer ) If this is where you want to install ubuntu, change /media/hda6 into / . It should work then. Good luck

---

### Post by wpshooter on 2006-12-10
I don't think you need all of that.

Just do:

/ for root
/home for home
/swap for linux swap

That should be all you need initially.

---

### Post by kibo on 2006-12-21
I have the same problem.
Message "No root file system" after selecting sdb5 as root file system (/)
and sda6 as swap.
Look at the attachment.

---

