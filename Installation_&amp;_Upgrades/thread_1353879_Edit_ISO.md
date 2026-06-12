---
title: "Edit ISO"
date: 2009-12-13
forum: Installation &amp; Upgrades
---

### Post by neojames on 2009-12-13
I've downloaded the latest ubuntu 64bit ISO for use on my new computer. I was wondering if there was a way to change the default software packages to include my most commanly used reposatorys and programs like wine or songbird (all programs I'd want to use have debs.)

Thank You,
Neojames;)

---

### Post by CharlesA on 2009-12-13
Add them after you install. Use Synaptic or apt-get.

---

### Post by neojames on 2009-12-14
I know that but I wanted to write it to the iso so if I want/have to reinstall in the future then I would like to have my most commonly used software installed with ubuntu, as it usually takes houres to find all the software I want!

---

### Post by JoeSolo on 2009-12-14
I don't know about auto-installing all the software as part of a standard build.  I've heard that its far too complicated for us mere mortals to attempt.

What you could try is:

1. Make a backup copy of the original iso
2. Mount the backup copy of the iso
3. Create a folder named Custom on the mounted image
4. Copy all your DEB files into the Custom folder
5. Write a bash script to
   a) Copy the DEB files to /var/cache/apt/archives
   b) Run an apt-get install for each package you want to install
6. Unmount the back copy and write it to disc
7. Test!

Then, once you've completed a new install, you just open a terminal and execute the bash script.

The problems with this:
1. Its not fully automatic, but its better than having to remember everything you want to install
2. I'm not sure whether or not the edited ISO will still be bootable

---

### Post by neojames on 2009-12-14
Ok thank you would I need anything special in the SH script (usually I would have to run as root would this still be the case) also could I use the software in a repo to reduce the size of the end ISO.

---

### Post by SecretCode on 2009-12-14
I haven't tried it, but I've heard that **remastersys **is the solution to this.

---

### Post by neojames on 2009-12-16
I already use this for my backup any idea on how to use this on an image I haven't installed?

---

