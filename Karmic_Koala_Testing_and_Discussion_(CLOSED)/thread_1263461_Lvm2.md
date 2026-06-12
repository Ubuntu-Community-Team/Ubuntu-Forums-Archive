---
title: "Lvm2"
date: 2009-09-11
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by FunkyRes on 2009-09-11
This is definitely too late for karmic - I looked at the brainstorming area and maybe this belongs there, I do not know.

I have been a CentOS user for several years, a Fedora user before that (since Fedora Core 2) and a Red Hat user before that.

I admin several systems running CentOS and will continue to do so. The systems I admin pretty much run stock CentOS + EPEL and I do not like installing and 3rd party stuff (other than updated php RPMs that I maintain) because you don't want repository conflicts on servers and you don't want to replace vendor packages on servers.

However, after playing with Ubuntu for a about a week now, I am seriously considering making Ubuntu my home desktop install - I have to keep CentOS around (might run it in xen) but I'm really starting to like Ubuntu as a desktop distro.

My biggest complaint with ubuntu is the lack of LVM2 on install disk.
I saw there are ways to do it, namely booting into live CD and installing, but I think it really needs to be an option (even if just as an advanced option) on the install CD.

What makes LVM2 so nice is that you can make your partitions and then easily resize if later on you found out you made some too small and others too large. This is particularly useful for /home and /srv - so that you can do clean installs and upgrades w/o needing to restore your personal data and databases etc. - but you can adjust the size as necessary, or even add another drive to an LVM.

Red Hat has a very good GUI LVM manager that is open source and (if it hasn't been already) could be built for Ubuntu.

I understand that LVM is a little more complicated than fixed partition sizes on install, and would need modification to the installer, but I do think it would benefit many, and should be doable by choosing install off of the media w/o needing to boot into live environment.

---

### Post by lithorus on 2009-09-11
Aren't lvm2 on the server edition install disc?

---

### Post by FunkyRes on 2009-09-11
Are they?

I grabbed the desktop install.
Would it then be on the DVD version?
If so, sorry for the noise.

I know LVM2 is often thought of as server tech but I have found it extremely useful on Desktop installs.

---

### Post by erkiha on 2009-09-11
> **FunkyRes said:**
> Are they?

I grabbed the desktop install.
Would it then be on the DVD version?
If so, sorry for the noise.

I know LVM2 is often thought of as server tech but I have found it extremely useful on Desktop installs.

with ubuntu server install you can install the same desktop system only without graphical installer and livecd. Just install ubuntu-desktop package. And you can use LVM and software raid.

---

### Post by Quikee on 2009-09-11
You could also download Ubuntu "alternative installer" installation disk which has lvm2 support and md raid support in its disk partitioner.

---

