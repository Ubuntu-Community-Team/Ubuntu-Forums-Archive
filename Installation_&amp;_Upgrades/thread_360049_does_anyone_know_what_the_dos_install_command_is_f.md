---
title: "does anyone know what the dos install command is for ubuntu?"
date: 2007-02-12
forum: Installation &amp; Upgrades
---

### Post by como on 2007-02-12
well?

---

### Post by phiphedog on 2007-02-12
Huh? This question is a little strange and not very descriptive. What are you trying to do?

---

### Post by finer recliner on 2007-02-12
...its a bootable disc, no need for DOS. im confused with your question too.

---

### Post by Logical Dream on 2008-04-08
Hi all . I wanted to post new topic but I saw this thread . I have maybe  similar problam, As I want to install Ubuntu for my brother as burned ubuntu 7.10 as bootable disk . When I boot It Im getting on Caldera Dr-Dos point and I have A:\> as my drive . Can not chnage it and I need to start installation from that point . 
I try to burn new CD but didnt find option to have stupid normal Auto Run for installation when I boot it .

uf 

If someone can suggest how to start installation from here , will be apritiated . 

p.s. Machine is prety OK as it has 512 mb RAM ,160 GB HD , Radeon GC etc...

---

### Post by Partyboi2 on 2008-04-08
After you have downloaded the ubuntu iso check the [md5sum]("https://help.ubuntu.com/community/HowToMD5SUM") that it matches, then burn it to disk as a iso not as data and at about x4 or less then enter into your bios and change the boot order so that your cdrom is the first to boot. When you have got to the ubuntu main menu screen choose "Check cd for defects" If this passes then install ubuntu.

---

### Post by Logical Dream on 2008-04-08
tnx for tip . but in break I found some solution  :

```

If again this doesn' work, as happened with me, then you will need to do the following (this requires a floppy disk drive and a blank floppy disk.
 Find the file 'sbm.bin' under the /install folder on the Ubuntu CD. If you can't find it you can download it from this link, 
and click on 'sbm.img' to begin the download. Then you will need to download a program called RawWrite, 'Extract' it and install it.
 First insert the floppy disk and then format it. Open a command prompt (Start / Run / "cmd") if this doesn't work search for an application 
called 'dos prompt' or similar. It will be a black box with white writing) and type: 'format a:' and then press enter.
 It may ask you to name the drive but simply pressing enter when this option comes up will leave it with the name it has. 
When this has stopped doing something then type: 'rawrite 'f sbm.bin', and press enter (this is a rawrite command). 
When this is finished close the box and the floppy disk will be complete. note: the floppy disk will appear to have nothing on it as it is a hidden system file.
 Label the floppy disk to avoid confusion.

Now reboot the computer with both the floppy disk and the Ubuntu CD in and watch carefully as it loads up. 
There will be an option similar to 'Press F2 to enter set-up'. When this appears press the specified key as before, 
and in the same way that you selected to boot from the CD-ROM drive select to boot from drive 'a:' 
Then Select the option to reboot your computer and, providing the rest has been done correctly then a screen 
will load with the title 'Smart Boot Manager'. Use the arrow keys to scroll down to the option that says 'Boot from CD-ROM' or similar. 
This will then load the Ubuntu start-up page as shown before.
```  ---> Originaly posted by "stooshbunutu" member  [LINK]("http://ubuntuforums.org/showthread.php?t=737168&highlight=DOS")

I will try this solution as I delted my image when I burned CD

---

