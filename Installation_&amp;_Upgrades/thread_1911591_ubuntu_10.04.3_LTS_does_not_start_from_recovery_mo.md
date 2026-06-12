---
title: "ubuntu 10.04.3 LTS does not start from recovery mode"
date: 2012-01-19
forum: Installation &amp; Upgrades
---

### Post by moltoscarso on 2012-01-19
This thread is sent to forum’s gurus. 
   
  I installed latest lubuntu version on an old HP-Vectra but former ubuntu 10.04.3 LTS does not start from recovery mode correctly. Also has a 11.10 ubuntu version loaded on an additional HD connected to same pc.
   
  After lubuntu installation grub looks like this:
   
  GNU grub version 1.99 - 12ubuntu[FONT=&quot]

ubuntu con linux 3.0.0-14 generic
ubuntu con linux 3.0.0-14 generic (modalità ripristino)
Memory test (memtest 86+)
Memory test (memtest 86+, serial console 115200)
ubuntu with linux 3.0.0-12-generic(on dev/sda1)
ubuntu with linux 3.0.0-12-generic(on dev/sda1) (recovery mode)
ubuntu 10.04.3 LTS kernel 2.6.32-37-generic (on dev/sdb1)
ubuntu 10.04.3 LTS kernel 2.6.32-37-generic (on dev/sdb1) (recovery mode)
ubuntu 10.04.3 LTS kernel 2.6.32-36-generic (on dev/sdb1)
ubuntu 10.04.3 LTS kernel 2.6.32-36-generic (on dev/sdb1) (recovery mode)
ubuntu 10.04.3 LTS kernel 2.6.32-35-generic (on dev/sdb1)
ubuntu 10.04.3 LTS kernel 2.6.32-35-generic (on dev/sdb1) (recovery mode)
ubuntu 10.04.3 LTS kernel 2.6.32-23-generic (on dev/sdb1)
ubuntu 10.04.3 LTS kernel 2.6.32-23-generic (on dev/sdb1) (recovery mode)
ubuntu 10.04.3 LTS kernel 2.6.32-19-generic (on dev/sdb1)
ubuntu 10.04.3 LTS kernel 2.6.32-19-generic (on dev/sdb1) (recovery mode)
ubuntu 10.04.3 LTS memtest 86+ (on dev/sdb1)[/FONT]

 
 
  Whenever I try to let ubuntu 10.04 start from recovery mode with terminal command: [FONT=&quot]startx [/FONT]
  Get following error message:


  
(==) log file: "var/log/Xorg.0.log", Time *[FONT=&quot](current time)[/FONT]*[FONT=&quot]
(==) Using config file: "/etc/x11/xorg.conf"
(==) using config directory: "/usr/lib/x11/xorg.conf.d"
the KEYBOARD keymap compiler (xkb comp) report:
> Errors:      Cannot close "/tmp/file2gVvOB" properly (not enough space?)
[/FONT]>                  Output file "/tmp/file2gVvOB" removed[FONT=&quot]
Errors from xkbcomp are not fatal to the X server
(EE) Error compiling keymap (-)
(EE) XKB: could't compile keymap
keyboard initialization failed. This could be a missing or incorrect setup of x keyboard config.

fatal server error:
failed to activate core devices.
Please consult the The X.org Foundation support at  [http://wiki.x.org]("http://wiki.x.org/") for help
Please also check the log file at "/var/log/Xorg.0.log" for additional information

ddxSigGiveUp:   closing log
givin up.
Xinit: No such file or directory (errno 2): unable to connect to X server
Xinit: error in locking authority file /home/tizianocapecci/.Xauthority[/FONT]


Tryed meanwhile to check among several posts in the internet forums to get around problem, getting rip of same disk junk such as Trash or unused files but nothing happened.
   
  Anybody has an hint for me?

---

### Post by raja.genupula on 2012-01-19
i think your xorg.conf file was corrupted . please give a try . if you have live CD then copy that 
 config file: "/etc/x11/**xorg.conf**"
(==) using config directory: "**/usr/lib/x11/xorg.conf.d**"

files to those locations . get these files from your live cd and then place them at your filesystem's location .

Let me know what you got , all the best . 

one more point : before going to copy new files to that location get the old files as back up .

All the best.

---

### Post by snowpine on 2012-01-19
Running X in recovery mode is generally not advisable, can you give us some background on the project that requires for you to do this?

---

### Post by moltoscarso on 2012-01-20
Unfortunately I do not have the live CD; and even, since I'm not familiar with the ubuntu family I'm afraid I would not be able to copy and place file in my filsystem's location  :(  

Also I will give you soon some more closed details of what I got when I'm trying to run the apparently corrupted version of ubuntu 10.04.03 LTS from grub.

Will reply as soon as possible. Thank you 

ms

---

### Post by raja.genupula on 2012-01-20
make some bootable USB live cd .It's better to give us more details regarding what you wanna do .

---

### Post by snowpine on 2012-01-20
You are having trouble with startx in recovery mode... can you startx in regular (non-recovery) mode?

---

### Post by moltoscarso on 2012-01-20
No, I can't either. When I try the regular mode on the opening screen I'm asked to log in with my username (or other). In the same schreen i do get an installation error warning message which I cannot remeber by heart now because I'm not home. Still, the info says that some installation error has happen during loading lubuntu upon old resident ubuntu 10.04.03 - i can only guess that disk space was not sufficient of wrongly partitioned. I migh t be possible that unintentionally I manually set the disk partition wrong.

---

### Post by snowpine on 2012-01-20
If you can tell us the error message, that would be helpful.

If there is a problem with your partitions, you may be able to fix it using a Live CD and GParted partition editor. For example if your 10.04.03 partition is too small, you can resize it. :)

---

### Post by moltoscarso on 2012-01-20
when I'm opening grub I get:

GNU grub version 1.99 - 12ubuntu

ubuntu con linux 3.0.0-14 generic
ubuntu con linux 3.0.0-14 generic (modalità ripristino)
Memory test (memtest 86+)
Memory test (memtest 86+, serial console 115200)
ubuntu with linux 3.0.0-12-generic(on dev/sda1)
ubuntu with linux 3.0.0-12-generic(on dev/sda1) (recovery mode)
ubuntu 10.04.3 LTS kernel 2.6.32-37-generic (on dev/sdb1)
ubuntu 10.04.3 LTS kernel 2.6.32-37-generic (on dev/sdb1) (recovery mode)
ubuntu 10.04.3 LTS kernel 2.6.32-36-generic (on dev/sdb1)
ubuntu 10.04.3 LTS kernel 2.6.32-36-generic (on dev/sdb1) (recovery mode)
ubuntu 10.04.3 LTS kernel 2.6.32-35-generic (on dev/sdb1)
ubuntu 10.04.3 LTS kernel 2.6.32-35-generic (on dev/sdb1) (recovery mode)
ubuntu 10.04.3 LTS kernel 2.6.32-23-generic (on dev/sdb1)
ubuntu 10.04.3 LTS kernel 2.6.32-23-generic (on dev/sdb1) (recovery mode)
ubuntu 10.04.3 LTS kernel 2.6.32-19-generic (on dev/sdb1)
ubuntu 10.04.3 LTS kernel 2.6.32-19-generic (on dev/sdb1) (recovery mode)
ubuntu 10.04.3 LTS memtest 86+ (on dev/sdb1)


Whenever I try with > startx get following error message:

(==) log file: "var/log/Xorg.0.log", Time *current time*
(==) Using config file: "/etc/x11/xorg.conf"
(==) using config directory: "/usr/lib/x11/xorg.conf.d"
the KEYBOARD keymap compiler (xkb comp) report:
> Errors:      Cannot close "/tmp/file2gVvOB" properly (not enough space?)
>                  Output file "/tmp/file2gVvOB" removed
Errors from xkbcomp are not fatal to the X server
(EE) Error compiling keymap (-)
(EE) XKB: could't compile keymap
keyboard initialization failed. This could be a missing or incorrect setup of x keyboard config.

fatal server error:
failed to activate core devices.
Please consult the The X.org Foundation support at  [http://wiki.x.org]("http://wiki.x.org/") for help
Please also check the log file at "/var/log/Xorg.0.log" for additional information

ddxSigGiveUp:   closing log
givin up.
Xinit: No such file or directory (errno 2): unable to connect to X server
Xinit: error in locking authority file /home/tizianocapecci/.Xauthority

Somebody in a local ubuntu forum suggested to give following command:

> E2fsck and I got following:

E2fsck.ext2: nessun file o directory durante l'apertura di /dev/sda* (* numero partizione)
Il superblocco e' illeggibile, o non descrive un corretto filesystem ext2 
Se  il dev/a e' valido e contiene realmente un filesystem ext2 (e non swap,  ufs o altro), allora il superblocco e' corrotto e si potrebbe provare  ad eseguire e2fsck con un superblocco alternativo
E2fsck -b 8193 (device)

[FONT=Verdana]sorry for italian text. Nevertheless, the contents sounds like this:


[/FONT]E2fsck.ext2: no file or directory during opening of /dev/sda* (* partition number)
superblock is not readable, or it doesn't describe a correct filesystem ext2
If dev/a is valid and really contains a filesystem ext2 (not swap, ufs or other), then superblock is corrupt and you might try to execute e2fsck with an alternate superblock
E2fsck -b 8193 (device)

[FONT=Verdana]Hope this is understandable for you.  Thank you anyhow for trying to help me [/FONT]

---

### Post by oldfred on 2012-01-20
I do not think e2fsck will resolve this issue but it should not hurt. You should always run e2fsck from liveCD or USB so partitions are unmounted. And you have to specify which partition which must be a ext2, ext3 or ext4 format.

#From liveCD so everything is unmounted,swap off if necessary, change sdb1 to your partition(s)
#e2fsck is used to check the ext2/ext3/ext4 family of file systems.
sudo e2fsck -C0 -p -f -v /dev/sdb1
#if errors:
sudo e2fsck -f -y -v /dev/sdb1

Do you get same errors on lubuntu boot?

I also think issue is as raja.genupula suggested on xorg.conf. Did you manually modify keyboard to Italian as it seems like some error on keymap.

---

### Post by moltoscarso on 2012-01-20
I did use the liveCD as suggested by you. with first command
```
sudo e2fsck -C0 -p -f -v /dev/sdb1
```
it went ok but, after rebooting nothing changed; i.e. start from regular mode got same error as before. I'm being asked to login with my user name and get an error message saying something like:
> installation problem
predefined values for the configuration of GNOME supply provider are installed not correctly
contact system administrator

lubuntu boot, on the other hand, no problems

I'm also thinking raja was right. 
with the keyboard did not change anything. please be aware that system from the very beginning has been installed for italy use, so in italian language and with italian keyboard. I'm definitely located in italy.

---

### Post by moltoscarso on 2012-01-21
Die try sito liveCD got following reply (When disconnected 2nd ATA MAXTOR hd connected  to pc - it's tue one Where ubuntu 11 is loaded)

> E2fsck: no such file or directory while try ing. To open /dev/sdb1

The superblock cold not be' read or dose not describe a correct ext2 filesystem. If the device is valid and it rally contains an est2 filesystem (and not a swap or ufs or something else) tien the superblock is corrupt, and you might try running e2fsck Winehouse an alternate superblock: 
E2fsck -b 8193 (device)

---

### Post by oldfred on 2012-01-21
The example I posted of sdb1 assumes that a ext2,3, or 4 partition is at sdb1. You have to use your partition(s) that are ext formated.

this will tell you, your partitions and which are Linux.
```

sudo fdisk -lu
```

and this gives UUID & formats

```
sudo blkid
```

---

### Post by moltoscarso on 2012-01-22
oldfred thank you for clarifying, unfotunately I'm not that good in getting along with linux altogether.  Still, your information were useful and good to me. situation now is clearer. Partition of both hard disks (ATA MAXTOR) now is known. I solved meanwhile my problems installing anew ubuntu 10.04.3 in some left space of both hard disks. Got all the pictures I was missing from corrupted ubuntu version via F-Spot. Thus finally no need to set back that faulty version. Honestly speaking I would like to find out how to come out of this 'engpass'. I'm courious to see if problem can be solved via terminal, as I presumed. I think raja.genupula was right in detecting Xorg corruption so I followed his(her?) indications but, could not find the file in the given directory. Did not find it in the liveCD directories. This sounds strange to me. I don't know where I'm mistaking.  Any suggestion Raja?

---

### Post by oldfred on 2012-01-22
If you are in your liveCD or other install, you can mount the old install and browse it. You can do it from Naulitus file browser but may have to use gksudo Nautilus from command line to edit. Be careful with a root Nautilus as you can accidentally damage other things.

Or from command line you can mount the old install. If old install  was sda5

sudo mount /dev/sda5 /mnt
Backup old copy just in case:
sudo cp /mnt/etc/x11/xorg.conf /mnt/etc/x11/xorg.conf.backup

gksu gedit /mnt/etc/x11/xorg.conf

or command line editor with sudo:
sudo nano /mnt/etc/x11/xorg.conf

---

### Post by moltoscarso on 2012-01-23
ok, done as you suggested. I guess it shall be a missing xorg file problem cause after first command from command line, when I try to backup, got following error message

> tiziano@tiziano-desktop:~$ sudo cp /mnt/etc/x11/xorg.conf /mnt/etc/x11/xorg.conf.backup
cp: impossibile eseguire stat di "/mnt/etc/x11/xorg.conf": Nessun file o directory
tiziano@tiziano-desktop:~$ 
it says: cp: impossible to execute stat of ""/mnt/etc/x11/xorg.conf": no file or directory

---

### Post by oldfred on 2012-01-23
First did it mount your install correctly to /mnt? If not then it would not be found anyway.

---

### Post by moltoscarso on 2012-01-27
A final and sharp cut to a long story. Very easy indeed; disk was full, no space left. Logged in with my username in the recovery mode terminal and made some simple clean-up of my home directory, taking away some heavy stuff like movies and pictures and that was.
After rebooting anything worked again perfectly.

---

