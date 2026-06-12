---
title: "Edgy power manager problem"
date: 2006-10-27
forum: Installation &amp; Upgrades
---

### Post by Totonno on 2006-10-27
Hello fellows!
I have a Sony Vaio VGN-FJ3S. Today I installed Ubuntu Edgy Eft 6.10 final release but I can't make the power management to work. Everything seems fine, but when I plug out the power the screen doesn't lowdown, and probably also the CPU scaling is off. At first I thought it was a problem of the Beta release, but the problem's still here. The weird thing is that in Dapper everything used to work fine "out of the box". What can I try before experimenting my first kernel recompiling? Or you have any suggestion about settings i should check in recompiling?
Thanks a lot!

P.S. - sorry for my bad english 

Totonno

---

### Post by stenka on 2006-10-27
Hi,

I have exactly the same issue with my Vaio, thought it worked very well with Dapper.

I submitted this bug, please confirm it :
[https://launchpad.net/distros/ubuntu/+source/gnome-power-manager/+bug/68617](https://launchpad.net/distros/ubuntu/+source/gnome-power-manager/+bug/68617)

---

### Post by stenka on 2006-10-28
A nice guy gave me there a workaround :

cd /bin
sudo mv sh sh.original
sudo ln -s /bin/bash /bin/sh

And then try to use gnome-power-manager to change the brightness.

He found that the scripts in hal uses "let" that is not implemented in
"dash".

---

### Post by Drife on 2006-10-28
Hi!
I've got an Acer laptop and the power-manager worked fine in dapper but know when I run on battery the manager is reporting the power in steps of 25%.. so it says 100% until it all of a sudden says 75%. Very annoying and very strange.. Anyone else experience this? Or even got a solution? I have already replaced sh with bash since it's necessery to compile the ATI-drivers.. pretty bad with an ugly work around. Thumbs down Edgy!

---

### Post by Totonno on 2006-10-28
Thanksalot Stenka! Hope it works...

---

### Post by Totonno on 2006-10-28
Yes! It works...very helpful, thanks for taking time to help! Cheers
Totonno

---

