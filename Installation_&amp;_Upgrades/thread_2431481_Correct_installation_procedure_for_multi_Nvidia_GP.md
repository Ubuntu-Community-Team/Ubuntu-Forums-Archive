---
title: "Correct installation procedure for multi Nvidia GPUs?"
date: 2019-11-17
forum: Installation &amp; Upgrades
---

### Post by ProDigit on 2019-11-17
Hello everyone,

I have found that the installation of the deb file (the nvidia-driver included in the repositories), works for 1 GPU, but gives desktop errors on multi GPU systems.
Up until 18.10, I could just exit the GUI (CTRL + ALT + F2), and sudo init 3.
I was recommended to stop service sddm or lddm or lightdm as well.
A procedure I found from an Arch Linux forum.

Then install the nvidia run files (which the run file has to be set to executable first).
On Lubuntu 16.04, 16.10, 18.04 and 18.10, this procedure worked flawlessly.

Now, with Lubuntu 19.04 / 19.10, I notice that this procedure no longer works. I think a conflict with the nouveau drivers that remain remnant even after sudo init 3?
I even tried installing the same procedure, via grub >> ubuntu recovery mode >> drop to root shell, and from there install the drivers.
But without success.

Can anyone enlighten me on the correct procedures to make multi GPUs work on Lubuntu please?

---

