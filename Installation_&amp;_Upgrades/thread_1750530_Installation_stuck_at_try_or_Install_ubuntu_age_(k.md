---
title: "Installation stuck at try or Install ubuntu age (kinda long)"
date: 2011-05-05
forum: Installation &amp; Upgrades
---

### Post by afs97209 on 2011-05-05
Tried Ubuntu 11.04 dual boot install w/ Win7 Friday

Dual boot installation failed. Only booted for Ubuntu.

Was fairly angry :mad: until I found my Windows7 files available for me to remove my old files to new back-up drive. Moved all my files there, and decided after being forced to use the new Ubuntu Unity desktop all day moving files to the new back-up, I really liked using it.:) Decided to keep unity. That's a pretty big win for Unity, 'cause I had not been a happy camper about the dual boot issue.

So...Ubuntu was stuck on a standard fairly small 20 Gig partition standard for dual boots.

Finished moving files and decided to install ubuntu on the whole hard disk.

Now the Ubuntu install won't advance beyond the page of install you choose to try the live disk or install ubuntu. Tried several times yesterday. Just sits there and sits there.](*,)

Tried using GParted to alter partitions. Could not move mount point off small Ext 4 partition. Nogo.

Decided to try to use Debian online installer to see if it could get any better luck getting further along in install process.

Debian installs perfectly. I now have a solid Debian 6 install with healthy hard drives and big single ext3 partition. I'm using ?iceweasel? to post this.

It's not what I want. I like the new Unity desktop.

It still will not install. Can't get the same page where you choose to try or install with the 2 check boxes.

---

### Post by afs97209 on 2011-05-05
Hello?

---

### Post by afs97209 on 2011-05-05
I was told on the #ubuntu chat channel to try the Ubuntu alternate text installer. I hadn't thought of that, probably because I've got 7 gigs of RAM. 

The text installer worked like a charm. Just some odd bug that got the graphic installer hung up, but not the alternate text installer.

Happily now\\:D/ using Unity to do all the post install stuff.

Thanks for the help.

---

### Post by Quackers on 2011-05-05
Well done :-)  Happy Ubuntuing!
I suspect that your original problem would have been fixed by running sudo update-grub in a terminal. Did you try that?

---

