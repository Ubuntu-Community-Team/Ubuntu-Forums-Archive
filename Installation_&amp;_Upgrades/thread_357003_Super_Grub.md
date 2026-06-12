---
title: "Super Grub"
date: 2007-02-09
forum: Installation &amp; Upgrades
---

### Post by H0SS on 2007-02-09
Okay, so I downloaded and put the floppy img on my floppy disk, the dl site was [http://forjamari.linex.org/frs/?group_id=61](http://forjamari.linex.org/frs/?group_id=61).  It boots from floppy, but I am left at the command prompt with a discription telling me that I can use Tab to view avialible commands in such.  Why didnt I get into the gui for this?  I though maybe I had the wrong image, but I download both floppy verisions.  Any help?

---

### Post by Herman on 2007-02-09
Hello H0SS,
Um, did you make your SuperGrub Disk according to the documentation?

Please click this link,[ How Make your Super Grub Floppy Disk]("http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html#How_Make_your_Super_Grub_Floppy_Disk")

Exactly which versions of SuperGrubDisk did you use? Mine's an older one, version sgd_0.9528, I could try with one of the same files you used to make sure it works for me if you tell me what numbers they were.

But they should work if you followed the documented procedure.

Regards, Herman :)

---

### Post by Herman on 2007-02-09
Okay, I'm having some problems too and I'm not sure why. 
It could be my floppy disks, I don't know, I'm getting an error message every time i try to format one.```
herman@testedgyeftbeta:~$ fdformat /dev/fd0
Double-sided, 80 tracks, 18 sec/track. Total capacity 1440 kB.
Formatting ... done
Verifying ... Read: : Input/output error
Problem reading cylinder 0, expected 18432, read -1
``` ```
herman@testedgyeftbeta:~$ dd if=super_grub_disk_floppy_english_0.9575.img of=/dev/fd0
dd: writing to `/dev/fd0': Input/output error
1+0 records in
0+0 records out
0 bytes (0 B) copied, 1.42886 seconds, 0.0 kB/s
```My old SuperGrubDisk floppy works fine, I tried it,  but with new SGD floppy disks I am getting, > Verifying DMI Pool Data ............
GRUB_ Is your error exactly the same as mine? Did you get an error when you formatted too?
I wonder if I left my floppy disks lying around too long, or if there's a bug in the floppy disk formatting program, or if I have a faulty floppy disk drive, or if there's a bug in SuperGrubDisk?

Regards, Herman :confused:

---

### Post by H0SS on 2007-02-09
Yeah, it sounds like a bad floppy to me.  

My problem is different.  Instead of booting to the Super Gurb menus, I am dumped to the grub prompt.  Almost as if you were to just type Grub in console, i.e.

grub>(with binling cursor here)

I then have access to all the grub commands, but all I want is to use the resore MBR option from in the menu.  Maybe I am using the wrong img file, but if you look that the download link that I showed you, there are only two to choose from, and I have tried both.

---

### Post by Herman on 2007-02-09
Three bad floppies in a row you mean?
Well I get days like this.   :roll:    

Okay then, I'll keep on trying, it's daylight again, the stores will be open so I can buy more floppies. Maybe I will try something different for an experiment, and make some other kinds of floppy disk just to see if those will work. 
If the problem is with SuperGrubDisk, I'll let adrian15 know and it will be corrected. Sorry for any inconvenience.

If you just want to restore Grub, you would have been able to do it very easily with the SuperGrubDisk if you could get into the menu part of it. I don't know why that part isn't working, but if you are interested, it isn't all that difficult to do the same thing manually from the command line.
Here is a link that explains as clearly as possible, step by step, how to do that. It's only about five steps, and you can skip the first one, ('sudo grub'), because you already have your grub command line, so it's only four steps...well, the last step is just quitting grub, so really it's only three steps.                                                  [Re-install Grub with a GRUB shell eg; with Live CD]("http://users.bigpond.net.au/hermanzone/p15.htm#Re-install_Grub_with_Live_CD")

 The only difference will be you'll have a black background with white print, where the Grub shell from terminal is white with black type. The commands will work the same. You can do it from any grub command line, so the one you have from the SuperGrubDisk will work fine. It will be installing you hard disk's installed Grub's first stage to MBR, not the floppy disk's SGD first stage.

Let me know if you still have problems.
Regards, Herman :)

---

### Post by H0SS on 2007-02-09
Nice link man.  I am good at the moment.  I just deleted the partitions that Ububtu was using and did a clean install.  I kinda botched up my Ubuntu anyways, so it was good that I re-installed.

Yeah, that is odd that 3 floppies in a row wouldnt take.  Maybe your disk drive is dirty or something?  I know that we have go to occationally clean out our tape drives in our servers because the dust will give read/write errors.

---

### Post by Herman on 2007-02-09
> Yeah, that is odd that 3 floppies in a row wouldnt take. Maybe your disk drive is dirty or something? I know that we have go to occasionally clean out our tape drives in our servers because the dust will give read/write errors. :idea: Yes, it could be dust in the floppy drive, and maybe on the floppy disks too. It is quite dusty here. Maybe I better do some vacuuuming and clean this room and then clean my old computer out. 
It's amazing the sort of problems we solve here in Ubuntu Web Forums isn't it? :lol:
(Herman)

---

