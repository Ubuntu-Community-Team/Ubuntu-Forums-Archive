---
title: "fresh re-start: decide partition size"
date: 2006-09-16
forum: Installation &amp; Upgrades
---

### Post by lepre on 2006-09-16
Hi everyone!

i'm enjoying xubuntu 6.06 since june and now i feel a bit more adapted to the system, so i want to do more with it.
and the first thing i want to do, is reinstall it from scratch and have a better partitioning scheme because right now i'm having a bit of trouble with my old ntfs partitions and i have few space for the system.

right now my full / menus the /home takes up about 9GB.

now, since i have a WD raptor 74GB i tought about something like this:
- 100MB for /boot
- 20GB for /
- 1Gb for /swap (until now the top used was 17MB and usually is none...anyway...)
- rest for /home
- 15GB for other thing (testing new os/backup/archive, a new 250GB drive is coming in soon for my file server, so will be mainly for os test)

can i have problem with a separate boot partition? will i have to take care of something particular?

p.s.: i also wish to have a testing space for developing/trying new thing for my main installation, it's better to have a separate installation to be sure to not mess up mine?

thank you :KS

edit: another question is: can ubuntu installer full-format my disk? i mean this time i don't want the so called "fast format" but i want it to write all the disk to blank.

---

### Post by daxelrod on 2006-09-16
For a really, really in depth guide to partitioning, try the [Linux Partition HOWTO]("http://www.tldp.org/HOWTO/Partition/"). (I know, that doesn't specifically answer your question, sorry.)

GNU [shred]("http://www.gnu.org/software/coreutils/manual/html_node/coreutils_69.html"), already included in Ubuntu, will wipe your disk. I would recommend booting from the Ubuntu LiveCD to do this. Note that shred is designed to permanently overwrite a hard disk in a way that makes its contents impossible to recover, so be very, very **careful** with it.

If you don't care about forensic-quality wiping and just want to zero-out the disk, you would tell it to do no passes and give it the -z flag.

---

### Post by lepre on 2006-09-16
that's a good start :D

thank you ;)

---

