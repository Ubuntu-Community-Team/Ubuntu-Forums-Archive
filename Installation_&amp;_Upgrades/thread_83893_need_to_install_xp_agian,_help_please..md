---
title: "need to install xp agian, help please."
date: 2005-10-29
forum: Installation &amp; Upgrades
---

### Post by generalstoner on 2005-10-29
Installed Ubuntu and loved it but my xp get erased in the procces, when I boot up with the xp cd it goes to the hit enter to install screen and when I hit enter it says I cant find a harddisk to write too, I really need some help here getting this back asap. thanks in advance. I plan on using linux full time but for right now I really need xp back.

---

### Post by darth_vector on 2005-10-29
hmm, sounds like you have a SCSI or SATA hard disk. is this right?

if so, winXP doesnt have drivers for them (at least not before service pack 2). you will have to download these drivers and put them in a floppy. when the winXP install begins it will say "press F6 to install SCSI or third party drivers" or words to that effect. press F6, put your floppy disk in and after a little wait it will ask you which driver to install. select the driver from the disk (it should be the only thing in the list) and press ok. from then on things are pretty easy.

hope that helps, post back if you still have problems

---

### Post by generalstoner on 2005-10-29
thanks dude, Im going to go try that right now, I will post my results later

---

### Post by generalstoner on 2005-10-29
next problem, when I go to open the floppy drive or extract to it, it says"Unable to mount the selected volume.Error: given UDI is not a mountable volume" please help some more

---

### Post by bootlinux on 2005-10-29
Sounds like you formatted the whole drive when you installed Ubuntu which wiped out windows.
Windows can't recognize linux partitions. That's why the install CD doesn't know the hard drive is there. You'll have to re-fomat the hard drive with a bootable cd or disk to ntfs or fat32, then the CD will install windows. I did this once and had to use a bootable partition program like baby boot or partition magic as the windows boot disk would not work. You can install Ubuntu along side windows but it has to be on it's own partition which is a duel boot. Someone may have a better solution for you then I do as I'm not that experienced.

---

### Post by generalstoner on 2005-10-29
ok, first can someone help me with my floppy problem. then if you could tell me how to reformate or something along the lines of what bootlinux said because Im an absolute noob to linux.

---

### Post by generalstoner on 2005-10-29
can someone walk me through on how to reformatt my harddrive so I can get XP back, I installed linux on the whole drive so now I cant reinstall windows XP.

---

### Post by Xian on 2005-10-29
You can use the Ubuntu InstallCD to reformat the entire HD in any file system you choose (and as a single partition if that is what you want), then just restart your box with the WindowsCD in the tray and start from scratch.

---

### Post by super on 2005-10-29
windows should format for you. what you need to do is partition your disk so that you have a partition big enough for windows.

---

### Post by generalstoner on 2005-10-29
I no longer have windows which is why I need to reformatt, I also have a problem with my floppies, It says "Unable to mount the selected volume.Error: given UDI is not a mountable volume" I need my floppy since I have a SATA harddrive for the drivers If I could get some help there aswell.

---

### Post by aysiu on 2005-10-29
[quote=generalstoner]I installed linux on the whole drive so now I cant reinstall windows XP.[/quote] [QUOTE=generalstoner]I no longer have windows which is why I need to reformatt[/QUOTE] These two statements seem to contradict each other. How can you reinstall XP if you no longer have Windows...? If I'm misreading your post and you really mean you don't have a Windows *installation* but you do have a Windows *installer disc*, then you can follow [Microsoft's instructions for removing Linux and installing XP](http://support.microsoft.com/default.aspx?scid=kb;en-us;314458)

---

### Post by generalstoner on 2005-10-29
for the part about me saying I dont have windows anymore referrs to it being completely removed, as for the link you provided, I dont know were to do any of thoose things nor do I have an fdisk.

---

### Post by aysiu on 2005-10-29
[QUOTE=generalstoner]for the part about me saying I dont have windows anymore referrs to it being completely removed, as for the link you provided, I dont know were to do any of thoose things nor do I have an fdisk.[/QUOTE] Do you have a Linux installation CD or live CD or anything? Do you have any kind of Linux CD?

---

### Post by generalstoner on 2005-10-29
I have the linux install cd. The one off the site wich I burned then installed

---

### Post by aysiu on 2005-10-29
[QUOTE=generalstoner]I have the linux install cd. The one off the site wich I burned then installed[/QUOTE] Hold on. I'm trying to figure out how you might do it with the installer (as opposed to the Live) CD.

---

### Post by darth_vector on 2005-10-29
[QUOTE=generalstoner]next problem, when I go to open the floppy drive or extract to it, it says"Unable to mount the selected volume.Error: given UDI is not a mountable volume" please help some more[/QUOTE]

is this when inserting the floppy in an ubuntu machine? odd. first thing would be to try another floppy. 

do you have a friend/neighbour with windows and an internet connection? maybe you can get the driver from the internet through their computer. you shoudnt have to do this though.

---

### Post by generalstoner on 2005-10-29
ok cool, if its not to much trouble could you also see what is going on with my floppies, that is also what is keeping me from reformatting as I need to put SATA drivers on them before I can start to install xp as well

---

### Post by generalstoner on 2005-10-29
posted this on the wrong website...

---

### Post by aysiu on 2005-10-29
[QUOTE=generalstoner]I have the linux install cd. The one off the site wich I burned then installed[/QUOTE] Okay. I have an idea. I don't if it'll work. You can go through the regular Ubuntu installation process. When you get to the part where it says *Erase entire hard drive* or *Manually edit partition tables*, choose to manually edit it. See if you can delete your partitions and then create one NTFS partition (or at least a FAT32--Windows installer will recognize this).

Otherwise, maybe you need to get another CD (I'd recommend the Knoppix live CD or the first Mandriva installer CD). The problem is that your Ubuntu installation has the *fdisk* command, but it can't erase the entire Ubuntu installation and recreate a Windows-compatible partition while the command itself is being executed from Ubuntu.

---

### Post by generalstoner on 2005-10-29
Ok, im going to try it out, I hope it works

---

### Post by generalstoner on 2005-10-30
it didnt work, my next step would be to try knoppix, I need a dvd burner program though and FULL instructions on how to install and use it.

---

### Post by aysiu on 2005-10-30
[QUOTE=generalstoner]it didnt work, my next step would be to try knoppix, I need a dvd burner program though and FULL instructions on how to install and use it.[/QUOTE] Download the Knoppix CD--it'll be a lot faster! There should be both Knoppix CDs *and* DVDs available for download. And you don't install Knoppix--it's a live CD, meaning that it runs entirely off the CD and RAM. That's why it can repartition your entire hard drive, because it's not using the hard drive to run.

---

### Post by generalstoner on 2005-10-30
I mean intructions on installing the dvd burner program, I cant find one in the install apps menu.

---

### Post by aysiu on 2005-10-30
[QUOTE=generalstoner]I mean intructions on installing the dvd burner program, I cant find one in the install apps menu.[/QUOTE] Thanks for the clarification, but what you should be looking for is a CD burner program--that's my point--as the CD for Knoppix will take a lot less time to download than the DVD of it. Though, I guess most CD-burning programs also burn DVDs.

There's one built into Nautilus already. Just right-click on the ISO image and select "Write to disc." Otherwise, here are a couple of CD-writing programs worth installing through Synaptic (see second link of my sig for more details on Synaptic): K3B, Graveman, Gnomebaker.

---

