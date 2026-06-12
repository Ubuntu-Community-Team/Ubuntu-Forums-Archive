---
title: "Ubuntu installation issues..."
date: 2005-06-02
forum: Installation &amp; Upgrades
---

### Post by kona0197 on 2005-06-02
I am having some problems installing Ubuntu.

First of let me tell you this:

I have 2 Hard Drives. My Master HD is a 40 gig Maxtor. My Slave HD is a 4 gig Quantum. 

I have XP Pro set up on the Master 40 gig HD.

I set up Ubuntu on the little 4 gig HD.

My problem seems to be with GRUB. I choose to install GRUB on the 4 gig slave HD. 

I then set the BIOS to use the 4 gig slave drive as the first boot device.

Grub will not load either OS - either XP or Ubuntu.

What should I do? Can I fix GRUB or should I install GRUB on the main master 40 gig drive? I'm trying NOT to put anything Linux related on the 40 gig HD as it's a drive all for windows.

Forgive me if this is posted in the wrong section on the forum - maybe a admin can move it.

---

### Post by codejunkie on 2005-06-02
you should install grub on the 40gig maxtor if it is your master hard drive change back your bios settings to the way they were maxtor 40gig being the first drive in the boot order and install grub on the master hard disk. if you choose not to keep linux you can remove grub from the master harddisk by inserting your windows xp cd choosing recover console and typing fixmbr this will overwrite grub with the default windows bootloader. that is if you have an original windows cd, Recovery CD Sets from Compaq or Emachines won't work. i would'nt recommend installing  grub to the master hardisk if you are not sure about what your doing or don't have an original windows cd to remove it incase somthing goes wrong try using the live cd insted.

---

### Post by kona0197 on 2005-06-02
Well I reinstalled Ubuntu and put GRUB on the Master 40 gig and all is well. I'm very impressed with Ubuntu. Sleek and fast. 

My first question though: How do you get Ubuntu to play MP3 files?

---

### Post by mingus on 2005-06-02
here are the codecs . . . in the very handy starter guide, check it out

[http://www.ubuntuguide.org/#codecs](http://www.ubuntuguide.org/#codecs)

you'll want to take a look at the following it's related . . .

[http://www.ubuntulinux.org/wiki/RestrictedFormats](http://www.ubuntulinux.org/wiki/RestrictedFormats)

along with the guide it's useful to bookmark the following . . .

[http://www.ubuntulinux.org/wiki/UserDocumentation](http://www.ubuntulinux.org/wiki/UserDocumentation)

---

### Post by kona0197 on 2005-06-03
I have tried to follow the guide but when I try to install codecs I get this in terminal:

root@c-67-169-205-213:/home/terry # sudo apt-get install mplayer-386
Reading package lists... Done
Building dependency tree... Done
The following extra packages will be installed:
  libdirectfb-0.9-20 libfaad2-0 libggi2 libgii0 libgii0-target-x libglib1.2
  libgtk1.2 libgtk1.2-common libmad0 libsvga1 libungif4g libxvidcore4 xmms
Suggested packages:
  libggi-target-emu libggi-target-monotext libggimisc2 w32codecs libdvdcss
  mplayer-doc
Recommended packages:
  libggi-target-x libggi-target mplayer-fonts libmikmod2
The following NEW packages will be installed:
  libdirectfb-0.9-20 libfaad2-0 libggi2 libgii0 libgii0-target-x libglib1.2
  libgtk1.2 libgtk1.2-common libmad0 libsvga1 libungif4g libxvidcore4
  mplayer-386 xmms
0 upgraded, 14 newly installed, 0 to remove and 38 not upgraded.
Need to get 8252kB/8308kB of archives.
After unpacking 21.2MB of additional disk space will be used.
Do you want to continue [Y/n]? Y
**Abort.**
root@c-67-169-205-213:/home/terry #

What is going on?

---

### Post by bored2k on 2005-06-03
It is telling you "I am getting ready to install MPlayer, but there is a problem: it needs certain files you do not have. Luckily, I will get them for you, please press YES so I can eat your bandwith for the next couple of minutes :D".

---

