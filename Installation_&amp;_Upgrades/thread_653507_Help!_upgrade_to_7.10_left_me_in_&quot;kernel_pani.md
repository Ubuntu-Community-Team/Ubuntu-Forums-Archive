---
title: "Help! upgrade to 7.10 left me in &quot;kernel panic&quot;!"
date: 2007-12-30
forum: Installation &amp; Upgrades
---

### Post by familyman83616 on 2007-12-30
I had a problem during the upgrade and foolishly rebooted.  Now I'm left with a system that won't boot.

I burned the 7.10 ISO, booted to the CD, and pulled important stuff to my USB drive.  (Booting from CD was SO impressive!  This is a great distro!)  Some files were flagged as me not having rights to access them.  The install is asking me to come up with a boot partition.

I have three questions:
[LIST=1]
[*]How do I log in to gain access to my remaining files? (I sort of doubt there is any way.)
[*]Is there anyway I can use the current boot partition and, in effect, resume the upgrade?
[*]Would there be any reason to create a small boot partition instead of a full format?
[/LIST]

Thanks, in advance, for your help with this.

- mark

---

### Post by taurus on 2007-12-30
If you want to access your files on your harddrive, open a terminal, Applications -> Accessories -> Terminal, from the LiveCD and run

```
gksudo nautilus
```
Now, you can browse to wherever you want to be.

---

### Post by familyman83616 on 2007-12-30
Thanks for the prompt reply.  "gksudo nautilus" let me navigate the CD image but wouldn't let me look at the "36.6 GB Volume: disk".  I'm still locked out of some of my files.

I think I'm hosed because I need a way to enter credentials that only exist on my drive that won't boot.

---

### Post by taurus on 2007-12-30
Have you mounted your harddrive?  You need to mount it before you can access it.  Post the output of this command from a terminal.

```
sudo fdisk -l
```
That is a lower case letter L.

---

### Post by familyman83616 on 2007-12-30
I bet you don't sleep much.  :)

The CD boot must have found and mounted the drive.  Since the target machine is not on the wired network, I will have to type in the info ...
```
/dev/hda1 * (boot) 1 to 4783 38m blocks id 83 Linux
/dev/hda2 4784 to 4864 65k block id 5 Extended
/dev/hda5 4784 to 4864 65k blocks id 82 Linux swap / Solaris
```

Did I miss anything important?

---

### Post by taurus on 2007-12-30
```
sudo mkdir /media/ubuntu
sudo mount -t ext3 /dev/hda1 /media/ubuntu
ls -la /media/ubuntu/home/*username*
```
Where *username* is your login name on your machine.  Now, all your personal files on the harddrive should be in /media/ubuntu/home/*username*.

p.s.  It's about 0122, Sunday here.

---

### Post by familyman83616 on 2007-12-30
The commands went in without a problem.  Now I have my files under /media/ubuntu/home/mark/Desktop/WhitBap.  The problem is that I still have access problems with some of my files.  For example, when I click on one of the doc files, OpenOffice shows me "Access to /media/ubuntu/... was denied."  Each of the problem files has an orange "x" on the document icon.

I think I will be OK with not having these files.  Could you help me with questions two and three of my original post?  I'd like to know if there is anyway to save my configurations or if I should start from scratch.

Thanks.

---

### Post by taurus on 2007-12-30
Access those files/directories with

```
gksudo nautilus
```

2.  Not sure when you stopped the upgrade process so it's hard to say.

3.  Whether it's a good idea to have a small /boot partition, it all depends on who you ask.

When you first turn on your machine, how many kernels are there on the GRUB menu?

---

### Post by familyman83616 on 2007-12-30
I understand the whole having to mount now!  Thank you.

But now I'm really confused.  The red "x"s on the icons are gone and I can open each file.  However, when I drag them to the USB drive, ubuntu says "error while copying. /media/ubun... cannot be copied because you do not have permissions to read it."  

I figured out a way to copy those locked files to the USB drive.  I think I'm in good shape now as far as backing everything up.  I guess the only thing I'm resisting now is having to reconfigure my wireless (it was a pain under earlier Ubuntu), installing mapping software, setting up my desktop, etc.  

I know, I know.  I should just suck it up and start from scratch.

BTW: The upgrade process went for quite a while.  Is there a log I can view?

---

