---
title: "Ubuntu 9.10 karmic won't install on IBM Intellistation 185 PowerPC"
date: 2010-02-10
forum: Installation &amp; Upgrades
---

### Post by scprotz on 2010-02-10
Hi All,

Thanks for the time to read this.  So I'm a big convert on using Ubuntu on my x86/x64 machines.  I have a nice IBM Intellistation 185 Power PC (ppc) with dual 970 processors and 8gb of ram (and 3 SCSI 300 MB drives).

I tried to install Ubuntu 9.10 on it (the PPC distro) and it gets to the boot prompt, asks me how I want to install (I can choose "live" or "install", etc..).  No matter which option I choose (I've tried them all) it hangs after trying to start the kernel at "returning from prom_init".

Now...I've also tried other distros to see where that got me - Debian does the exact same thing as Ubuntu (which makes sense).  Yellow Dog Linux actually will install and run fine(I'm writing this from Firefox 3 in YDL).  

Since YDL works, I'd think that a version of Debian/Ubuntu should be able to work.

Any ideas on how to debug this and find out why Ubuntu won't install (or even run the Live CD?)

Thanks so much,

---

### Post by scprotz on 2010-02-24
Bump.  Anyone?

---

### Post by scprotz on 2010-03-21
So i've tested a number of OSes.  It seems the RedHat family of OSes works reasonably well (Yellow Dog Linux boots up with only one minor change - Enlightenment won't work -but I use Gnome anyway).

For some reason though, no Debian derivatives (including Ubuntu) will get past the "returning from prom_init".

Since this is something usually found in yaboot, I thought maybe it was a bootloader issue, so I used the YDL yaboot and booted the Ubuntu CD from yaboot command line - same issue.  So it still seems to me there is some type of kernel issue with the Debian/Ubuntu kernel.

If anyone has suggestions, I'm all ears (possibly an Ubuntu install with a custom kernel that works in my system? - I'd love to try it, but wouldn't know exactly how to do it - maybe install YDL and do a chroot?)

Thanks for any help

---

### Post by pabelanger on 2010-03-22
Having the same issue.  I'm trying to get qemu (running powerpc) to boot ubuntu-9.10-server-powerpc.iso, but no luck.

returning from prom_init

Will let you know what I find out.

---

### Post by scprotz on 2010-12-07
bump.  Any news on any Ubuntu working on the IBM Intellistation 185 (pSeries, PowerPC)?

I was able to get Fedora 12 running on it, but not my favorite distro.

Any help still?  I'll give 10.10 a try to see if any updates have been made.

---

### Post by droberts73543 on 2010-12-08
Hi
not sure if this is going to be a help to you powerpc ppl out here but I have an IBM Powerpc 7025 F50 and today after 3 months of working with it trying every distro out here, I got Ubuntu 10.04 Lucid Lynix loaded and so far it's running great. What I had to do was after installing go back in under rescue mode for me it was rescue-powerpc at boot promp...I went to /etc/yaboot.conf and used vi to omit the line that was /pci@fed00000 after doing that of cource wq then exit out and restart your machine. Now I found that when I installed the distro all it had was base os, I then went to /etc/apt now in apt directory I found sources.list, sources.list~, and sources.list.apt-setup, now the file we are wanting is sources.list but when I cat it had nothing, but sources.list.apt-setup did so I cp /etc/apt/sources.list.apt-setup /etc/apt/sources.list and rm /etc/apt/sources.list~. After I finished that I was able sudo apt-get update and all is good now after one head full of hair..hope this helps I'm no expert but am inquisitive and will figure things out. 
Thx and Good Luck or as my machine has on the display Have Fun!

---

### Post by scprotz on 2010-12-09
Thansk for the reply droberts73543,

I think the issue for some of us is the fact that we can't even get it to the install screen.  It appears that yaboot is hanging on the kernel.  I don't know if it is a faulty yaboot on Ubuntu for my particular PowerPC (mine is the Intellistation Power 185 with the Power970MP CPUs).  Fedora seemed to handle it just fine, but I'm just not good enough dealing with the yaboot boot loader.

I have been trying to debootstrap an ubuntu system onto it, but it always seems to be missing some file to keep it from completion.  The Fedora guys seem to have given up on PPC architecture as well ending at Fedora 12 (as of this note, the x86 family is at Fedora 14).

Worst case, i'll move to AIX 6.1, but since all my other machines are some version of Ubuntu,  I'd like to stay consistent.

---

