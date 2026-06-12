---
title: "Beta 1 crashes hard randomly"
date: 2010-03-20
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by cheapsaket on 2010-03-20
I installed Beta 1 (amd64) yesterday and have updated it today.

My laptop (Dell Studio 1735 4G Ram ATI 3650 Radeon) crashes randomly.

The screen goes blank and the keyboard does not respond.

REISUB does not work, I have to press the power button for 10 seconds to reboot.

Can someone help me figure out what is happening

---

### Post by yiit on 2010-03-20
same here, it's because of the radeon driver. you can try radeonhd if you want to stick to open source, or the new fglrx build from ati.

both of them solves this problem.

---

### Post by cheapsaket on 2010-03-20
> **yiit said:**
> same here, it's because of the radeon driver. you can try radeonhd if you want to stick to open source, or the new fglrx build from ati.

both of them solves this problem.

Hi, where can I get the new fglrx build?

---

### Post by yiit on 2010-03-20
> **cheapsaket said:**
> Hi, where can I get the new fglrx build?
i386:
[https://launchpad.net/ubuntu/+source/fglrx-installer/2:8.721-0ubuntu3/+build/1570406](https://launchpad.net/ubuntu/+source/fglrx-installer/2:8.721-0ubuntu3/+build/1570406)

amd64:
[https://launchpad.net/ubuntu/+source/fglrx-installer/2:8.721-0ubuntu3/+build/1570405](https://launchpad.net/ubuntu/+source/fglrx-installer/2:8.721-0ubuntu3/+build/1570405)

---

### Post by cheapsaket on 2010-03-20
I'm not understanding how to download from these links that you gave, could you please give a few details

---

### Post by yiit on 2010-03-20
there are .deb packages near the bottom of the page. 

for i386:

fglrx_8.721-0ubuntu3_i386.deb (17.3 MiB)
fglrx-amdcccle_8.721-0ubuntu3_i386.deb (4.9 MiB)
fglrx-dev_8.721-0ubuntu3_i386.deb (63.3 KiB)
fglrx-modaliases_8.721-0ubuntu3_i386.deb (13.4 KiB)

download these files, and install by running them. install the fglrx_8.721-0ubuntu3_i386.deb first, then the others. after installing them, run "sudo aticonfig --initial" in the terminal.

and also if you are using the radeonhd driver, you need to uninstall it before installing those packages.

---

### Post by cheapsaket on 2010-03-20
> **cheapsaket said:**
> I'm not understanding how to download from these links that you gave, could you please give a few details

ok downloaded and installed the deb files, lets see what happens

thanks

---

### Post by yiit on 2010-03-20
you also need to reboot your computer, of course.

---

### Post by cheapsaket on 2010-03-20
ok rebooted. now I am suffering from the slow maximize/restore issue with ati :sad:

---

### Post by cheapsaket on 2010-03-20
I resolved the slow maximize/resize/restore issue by following this post: [https://bugs.launchpad.net/ubuntu/+source/fglrx-installer/+bug/351186/comments/256](https://bugs.launchpad.net/ubuntu/+source/fglrx-installer/+bug/351186/comments/256)

Hope it helps someone

---

### Post by Reiger on 2010-03-20
I guess disabling KMS might also work. Your problems seem to be somewhat exact copy of mine when I use KMS. However passing radeon.modeset=0 on boot fixes everything. On the other hand, my crashes are very much not *random* but occur predictably *whenever I [s]use[/s] try KMS*.

From a default installation; on first boot try to get a tty using Ctrl,Alt <key> where <key> is a function key (e.g. F2).

Next, edit /etc/default/grub (for instance using sudo nano /etc/default/grub); and edit the GRUB_CMDLINE_LINUX_DEFAULT to include radeon.modeset=0.
Mine is this:
```

GRUB_CMDLINE_LINUX_DEFAULT="radeon.modeset=0 quiet splash"

```

Save (in nano Ctrl+O) and quite (in nano Ctrl+X). Then run sudo update-grub to make these changes propagate to your boot configuration (so all the old entries are updated with the radeon.modeset parameter) and reboot. (sudo reboot.)

---

### Post by yiit on 2010-03-21
> **cheapsaket said:**
> I resolved the slow maximize/resize/restore issue by following this post: [https://bugs.launchpad.net/ubuntu/+source/fglrx-installer/+bug/351186/comments/256](https://bugs.launchpad.net/ubuntu/+source/fglrx-installer/+bug/351186/comments/256)

Hope it helps someone

this patch is for xserver-xorg 1.6.3 package, which lucid uses 1.7.5 

are there any problems with it?

---

### Post by cheapsaket on 2010-03-22
> **yiit said:**
> this patch is for xserver-xorg 1.6.3 package, which lucid uses 1.7.5 

are there any problems with it?

The steps given will generate a deb for 1.7.5 or the version you have installed and then you can use it without issue.

I was able to follow this step by step and it generated 2 deb files for my 1.7.5.
It took around 30 minutes to download and build.

---

### Post by cheapsaket on 2010-03-22
To clarify, when you get to this step:

```
cd xorg-server-1.6.3
```

type in 

```
cd xorg-server-
```

and press TAB to autocomplete and choose 1.7.5 or the version you have.

Rest of the steps remain the same.

It might give a warning or error in the end (mine did) but its for gpg/pgp signing of the package generated which I did not have.

The package is still generated and I was able to dpkg --install

---

### Post by svaens on 2010-03-23
> **yiit said:**
> same here, it's because of the radeon driver. you can try radeonhd if you want to stick to open source, or the new fglrx build from ati.

both of them solves this problem.

Uhmm.... huh? 

I thought there were only two drivers ? radeonhd and fglrx? 

Or? What is the difference between the 'radeon driver' and the 'radeonhd' ?
and, how do I know what I am running at the moment ? 

Does the radeonhd (if i'm using radeon at the moment) provide 3D as well ?

I ask all this, because i've noticed this annoying blank/black unrecoverable random freeze as well.

---

### Post by zika on 2010-03-23
> **svaens said:**
> Uhmm.... huh? 

I thought there were only two drivers ? radeonhd and fglrx? 

Or? What is the difference between the 'radeon driver' and the 'radeonhd' ?
and, how do I know what I am running at the moment ? 

Does the radeonhd (if i'm using radeon at the moment) provide 3D as well ?

I ask all this, because i've noticed this annoying blank/black unrecoverable random freeze as well.

I've been searching for solution for quite some time now. Fglrx is not a solution for me. [http://ubuntuforums.org/showthread.php?t=1347430](http://ubuntuforums.org/showthread.php?t=1347430) [http://www.phoronix.com/forums/showthread.php?t=22002](http://www.phoronix.com/forums/showthread.php?t=22002)

---

