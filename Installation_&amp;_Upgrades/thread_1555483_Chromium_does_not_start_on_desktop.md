---
title: "Chromium does not start on desktop"
date: 2010-08-18
forum: Installation &amp; Upgrades
---

### Post by Arnoldijzermans on 2010-08-18
All

A problem I have read more about, but for now haven't find the solution.

On my desktop (10.04) I installed chromium using synaptic. It doesn't start, so I tried to start it from the terminal.
I then saw an error telling me that there was a shared memory problem and that a certain file couldn't be created in /dev/shm.
The solution was to try *sudo chmod 777 /de/shm*.
Of course tried it, but that resulted in the notification that the directory is read only ....

I also have a netbook running the 10.04 netbook edition. Installed it and it works absolutely flawless in one time.

The only difference is, that the netbook is a clean install and the deskop an upgrade from Karmic.

Is there anyone who can give me information in order to solve this problem. I want to use chromium on my desktop as well.

All help very very welcome.

regards

---

### Post by Arnoldijzermans on 2010-08-19
solved.

tmpfs was mounted as ro. Edit fstab and unmount and remount the drive.

---

### Post by mörgæs on 2010-08-19
Good. Please mark the thread 'solved'.

---

