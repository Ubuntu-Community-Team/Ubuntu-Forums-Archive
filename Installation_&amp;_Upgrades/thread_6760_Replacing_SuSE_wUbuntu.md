---
title: "Replacing SuSE w/Ubuntu"
date: 2004-12-01
forum: Installation &amp; Upgrades
---

### Post by usasma on 2004-12-01
First off, hello to all!  I'm a newbie who's a bit visually handicapped.  I'd installed Mandrake back in 1998, and just installed SuSE on my system about a month ago. 

What I'm looking for is to see if someone can point me to an in-depth set of instructions on how to replace my SuSE with Ubuntu.  I've got the Grub boot loader and have partitioned my C:\ drive (it's a SATA drive) for Linux.

When I remove the SuSE distro according to their instructions, the Grub refuses to load and I have to reinstall SuSE to get it working again (I'm dual booting with Windows XP Pro).

Because of my vision problems, I can't spend a long time researching things on the net (like I used to do).  So, I apologize in advance for taking up your time with this question.

FWIW - my vision problems are from scarring caused by Toxic Epidermal Necrolysis.  My eyes don't make hardly any tears, and the tears that are made are not healthy for my eyes. 

Thanks again!

---

### Post by TravisNewman on 2004-12-01
First off, I'm sorry to hear about your condition. My dad is legally blind and I know how hard it is for him.

To get to the point, if you want to replace SuSE with Ubuntu, all you really need to do is boot off of the Ubuntu CD, and when asked about partitions tell it to use the partition previously used for SuSE. It will install it's own grub version, and automatically pick up your Windows XP partition as well.

---

### Post by HiddenWolf on 2004-12-01
The question is, would it be possible to save the /home partition without too much problems?

---

### Post by jdodson on 2004-12-01
[QUOTE=HiddenWolf]The question is, would it be possible to save the /home partition without too much problems?[/QUOTE]

i would just tar the home directories, if you have another computer you can transfer the files to you can just tar/bzip2 the home directory and transfer it to another machine:

```
tar -cvf ./home.tar ./
bzip2 ./home.tar

``` 

make sure you are your home directory.  

if you want to tar all the home directories:

```
sudo -cvf ./homes.tar /home/
sudo bzip2 ./homes.tar
```

then you can install ubuntu and then untar the directories.

---

### Post by usasma on 2004-12-01
Thanks folks!  I was hoping that that was the solution.  Do you know if there'll be remnants of the SuSE left that I'll have to delete manually?  I'm not too worried about anything on the Linux partitions, but don't want to screw it up so bad that I've gotta reinstall SuSE.  

Thanks for the codes also!  I'll be able to use it to backup my stuff later on!

---

