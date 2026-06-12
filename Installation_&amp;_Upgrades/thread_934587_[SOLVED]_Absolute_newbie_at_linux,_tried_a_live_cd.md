---
title: "[SOLVED] Absolute newbie at linux, tried a live cd and now can't access my files"
date: 2008-09-30
forum: Installation &amp; Upgrades
---

### Post by The_Girl on 2008-09-30
Hello
Sorry if anyone posted about this before, I used the search function on the forums and couldn't find anything useful yet.

I tried the Kubuntu and Ubuntu live cds on my computer, a quad 6600 with 4gb RAM, Nvidia 8800GT, 500gb hard drive. 

My hard drive had windows XP pro installed and working all right.I recently had a smitfraud infection which I think I got rid of. 

After trying the live cds,and without having changed anything else on my system (no updates, no installations, nothing at all), windows started to freeze on startup. I tried to start in safe mode, but it won't work either.

The only setting that I've been changing was the boot device order, setting the cd drive as primary, and reversing it to hard drive after having used the ubuntu live cd.

I have been advised to reboot from the windows xp cd, restore the system and do a FIXMBR, but it didn't work either.

I have also tried to access my data via ubuntu live or kubuntu live but it says "$logfile indicates unclean shutdown" and says something on the line that the ntfs disc is in use right now. I am not allowed to mount it. I don't know how to force mount the drive, since I'm a total newbie at linux.

I am more than willing to format and reinstall afterwards, but I really need to recover a couple files. Is there any way to recover my files?
What happened?

Thanks for any help you can provide. 

Sorry about the English mistakes, it's not my mother tongue.

---

### Post by Pumalite on 2008-09-30
Try a Knoppix Live CD:
[http://www.knopper.net/knoppix/index-en.html](http://www.knopper.net/knoppix/index-en.html)
It mounts all drives/partitions automatically at boot
(I doubt an Ubuntu Live CD had anything to do with your problems. It loads in RAM)

---

### Post by Sef on 2008-09-30
>  Sorry about the English mistakes, it's not my mother tongue.     Your english is fine.

> My hard drive had windows XP pro installed and working all right.I recently had a smitfraud infection which I think I got rid of. 

After trying the live cds,and without having changed anything else on my system (no updates, no installations, nothing at all), windows started to freeze on startup. I tried to start in safe mode, but it won't work either.

The only setting that I've been changing was the boot device order, setting the cd drive as primary, and reversing it to hard drive after having used the ubuntu live cd.Maybe one of your ram sticks is bad.   To check it, I would download the latest version of [memtest86]("http://memtest86.com"), and run it overnight.  (It is also on the Live CD, but an older version.)

Last, if anyone says anything inappropriate, or in any other way violates the [Ubuntu Code of Conduct]("http://ubuntuforums.org/index.php?page=policy"), please click on the report button on the bottom left.  Thank you.

---

### Post by Crafty Kisses on 2008-09-30
Sure. Paste this code into the terminal:
```
sudo fdisk -l
```
Look for the drive in question. Let's just say, for the sake of this example, that it's /dev/hda1 and NTFS (if it's something else, post it back here, and I or someone else will help you modify the appropriate command). Then paste these commands into the terminal:
```
sudo mkdir /media/windows
sudo mount -t ntfs /dev/hda1 /media/windows -o nls=utf8,umask=0222

```
Launch up the file browser and browse the /media/windows directory, and you should see all your files. There is probably a GUI way to do this, too, but it depends greatly on what version of Ubuntu you're using... or if you're using Kubuntu or Xubuntu.

---

### Post by The_Girl on 2008-10-02
Hello. Thank you everybody for your help. The situation today is as follows:
I am currently downloading knoppix on a different computer. I've already tested the Ram memory and it is working all right.
On my previous post, I forgot to mention that my hard drive is a SATA2 hard drive. I don't know if this makes any difference to ubuntu.
I've tried the sudo fdisk -l command and what the terminal says is this:

ubuntu@ubuntu:~$ sudo fdisk -l

Disco /dev/sda: 500.1 GB, 500107862016 bytes
255 cabezas, 63 sectores/pista, 60801 cilindros
Unidades = cilindros de 16065 * 512 = 8225280 bytes
Identificador de disco: 0xe533e533

Disposit. Inicio    Comienzo      Fin      Bloques  Id  Sistema
/dev/sda1   *           1       60800   488375968+   7  HPFS/NTFS
ubuntu@ubuntu:~$ 
Translation: ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/tracks, 60801 cilinders
Units = cilinders of 16065 * 512 = 8225280 bytes
Disc ID: 0xe533e533

Device. Start    Begining      End      Blocks   Id  system
/dev/sda1   *           1       60800   488375968+   7  HPFS/NTFS
ubuntu@ubuntu:~$ 

I am going to try with knoppix later when it has finished downloading. I'll probably post my results tomorrow. If it doesn't work, should I try with the other terminal commands that have been posted in this forums?

Thanks for your time and patience.

---

### Post by Pumalite on 2008-10-02
Take a look with the Knoppix. Later you could try to boot your Windows with Super Grub:
[http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html)
Look in 'Search' for meierfra. He has a good thread on how to fix XP
I suspect that all that happened is that you didn't shutdown Windows properly

---

### Post by caljohnsmith on 2008-10-02
> **The_Girl said:**
> 
I have also tried to access my data via ubuntu live or kubuntu live but it says "$logfile indicates unclean shutdown" and says something on the line that the ntfs disc is in use right now. I am not allowed to mount it. I don't know how to force mount the drive, since I'm a total newbie at linux.

I am more than willing to format and reinstall afterwards, but I really need to recover a couple files. Is there any way to recover my files?
What happened?

There is a great program in linux called "ntfsfix" that will fix most problems with Windows partitions (NTFS file systems) that have been "uncleanly shutdown." To use it, boot your Ubuntu Live CD, open a terminal, and do:
```
sudo apt-get install ntfsprogs
sudo ntfsfix /dev/sda1
```
If that says it worked, you can then mount your Windows partition with:
```

sudo mkdir /media/Windows
sudo mount /dev/sda1 /media/Windows
```
Then you can open up a file browser (see the "Places" menu on the Ubuntu desktop) and access all your Windows files in the /media/Windows directory. Let me know how it goes, or if you run into problems.

---

### Post by The_Girl on 2008-10-06
Sorry about the delay, I had some unexpected university assignments. Thank you everybody for your help. Knoppix worked and now I'm backing up my important files. 

I'll try to make XP work later by using the various advices which you have given me and I'll post if I could fix the problem or not, but just for informative purposes. If it doesn't, I'll format and start again (see where I went wrong and learn!)

Let me thank you all again, I've been using windows for years, but have just ventured into linux and it's good to find such kind and helpful people. Cheers!

---

### Post by The_Girl on 2008-12-30
Ok, thank you everybody, I'd forgotten where I'd posted this, but now it's solved. I formatted with ubuntu and everything is working all right with that computer. Thanks everyone!

---

