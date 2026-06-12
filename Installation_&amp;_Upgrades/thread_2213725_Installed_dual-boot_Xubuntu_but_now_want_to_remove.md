---
title: "Installed dual-boot Xubuntu but now want to remove Windows XP"
date: 2014-03-28
forum: Installation &amp; Upgrades
---

### Post by Xubuntist on 2014-03-28
Hello

I am becoming more and more linux-savvy and I have installed Xubuntu 13.10 dual-boot on an old Lenovo PC and it's working like a dream. But now I want to remove the Windows XP partition and the last and previous times I did this I simply ran Gparted from the LiveCD (a bit laborious) and deleted the Windows partition but having done this a few times now on different computers this has caused me various problems, primarily:
[LIST]
[*]Can't boot any more because grub got deleted or corrupted 
[*]The grub menu keeps returning even though there is now just one OS on the pc 
[/LIST]
So, would it be possible for somebody to tell me the correct procedure to
[LIST]
[*]Remove the now unneeded Windows XP 
[*]Re-allocate all the freed-up space to Xubuntu 
[/LIST]
 Many thanks in advance for your patience and persistence with my noob questions.

---

### Post by fantab on 2014-03-28
Lets see your partitions. Post the output of:
```
sudo parted -l
sudo fdisk -l
```

---

### Post by Xubuntist on 2014-03-28
I'm sorry that it's in French, I hope this doesn't cause you a problem.

PARTED

```
Modèle: ATA WDC WD1600AAJS-0 (scsi)
Disque /dev/sda : 160GB
Taille des secteurs (logiques/physiques): 512B/512B
Table de partitions : msdos

Numéro  Début   Fin    Taille  Type      Système de fichiers  Fanions
 1      32,3kB  107GB  107GB   primary   ntfs                 démarrage
 3      107GB   155GB  48,3GB  extended
 5      107GB   154GB  47,4GB  logical   ext4
 6      154GB   155GB  937MB   logical   linux-swap(v1)
 2      155GB   160GB  4861MB  primary   fat32                diag
```


FDSIK

```
Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 têtes, 63 secteurs/piste, 19457 cylindres, total 312581808 secteurs
Unités = secteurs de 1 * 512 = 512 octets
Taille de secteur (logique / physique) : 512 octets / 512 octets
taille d'E/S (minimale / optimale) : 512 octets / 512 octets
Identifiant de disque : 0x75adc3f6

Périphérique Amorçage  Début         Fin      Blocs    Id. Système
/dev/sda1   *          63   208693825   104346881+   7  HPFS/NTFS/exFAT
/dev/sda2       303082290   312576704     4747207+  12  Compaq diagnostics
/dev/sda3       208695294   303081471    47193089    5  Étendue
/dev/sda5       208695296   301248511    46276608   83  Linux
/dev/sda6       301250560   303081471      915456   82  partition d'échange Linux / Solaris

Les entrées de la table de partitions ne sont pas dans l'ordre du disque
```

---

### Post by Bucky Ball on 2014-03-28
I would personally delete sda1, expand sda2 into the free space and run Boot Repair from a live install disk or USB to reinstall grub. 

Get Boot Repair:
[http://sourceforge.net/projects/boot-repair/?source=directory](http://sourceforge.net/projects/boot-repair/?source=directory)

Use BR:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

Yannbuntu's thread:
[http://ubuntuforums.org/showthread.php?t=1769482](http://ubuntuforums.org/showthread.php?t=1769482)

---

### Post by Xubuntist on 2014-03-28
Thank you very much for the reply.

The problem is that I've run Yannbuntu's Boot Repair on two PCs where I had this problem, and on both (one was a Windows Vista partition and the other was a Windows XP partition) it was unable to repair grub and on both machines I was forced to reinstall Xubuntu - which is clealy not the ideal solution. I am now scared of willy-nilly deleting partitions like that.

 This is why I am asking if there is a recognised "correct" way to deal with this.

---

### Post by Bucky Ball on 2014-03-28
Did you use the 'Advanced Options' and tell it where you wanted to reinstall grub, or did you hit 'Recommended Repair' to try and repair the existing one?

There's some pics of what I mean here: [http://www.howopensource.com/2012/05/reinstall-recover-grub-from-ubuntu-12-04-live-cd-usb/](http://www.howopensource.com/2012/05/reinstall-recover-grub-from-ubuntu-12-04-live-cd-usb/)

---

### Post by Xubuntist on 2014-03-28
I always used "Recommended Repair".

---

### Post by Bucky Ball on 2014-03-28
There's some pics of what I mean here: [http://www.howopensource.com/2012/05...4-live-cd-usb/](http://www.howopensource.com/2012/05...4-live-cd-usb/)

Reinstalling grub is the go. You can also do that from the Live CD (or install Boot Repair if you can get online). 

[http://howtoubuntu.org/how-to-repair-restore-reinstall-grub-2-with-a-ubuntu-live-cd](http://howtoubuntu.org/how-to-repair-restore-reinstall-grub-2-with-a-ubuntu-live-cd)

---

### Post by Xubuntist on 2014-03-28
I will try that and get back to you!

Thank you!

---

### Post by fantab on 2014-03-28
Don't delete the XP partition, just format it as ext4 and use it as a data parittion. Do this from xubuntu and use Gparted. If its not available then install it.
After formatting the said partition:

```
sudo dpkg-reconfigure grub-pc
```
and install Grub to the HDD ie, /dev/sda.

Reboot.

If xubuntu does not boot then:
Boot with xubuntu dvd/usb- try xubuntu without installing
and follow the instructions [HERE]("http://howtoubuntu.org/how-to-repair-restore-reinstall-grub-2-with-a-ubuntu-live-cd").

---

### Post by Xubuntist on 2014-03-28
OK, I will try that and get back to you! It seems safer than just deleting it.

Thank you!

---

### Post by Xubuntist on 2014-03-28
> **fantab said:**
> Don't delete the XP partition, just format it as ext4 and use it as a data parittion. Do this from xubuntu and use Gparted. If its not available then install it.
After formatting the said partition:

```
sudo dpkg-reconfigure grub-pc
```
and install Grub to the HDD ie, /dev/sda.

Reboot.

If xubuntu does not boot...

Oh, but deep joy, it **did** reboot, but it first came up with the grub menu with the option to load Win XP which, of course, we don't want. Is there a way I can edit the grub menu to get it load Xubuntu automatically and just remove all other entries?

---

### Post by fantab on 2014-03-28
Run:
```
sudo update-grub
```

It shouldn't find Windows anymore... let us know.

If xp is still present in the menu then edit /etc/default/grub and edit the file to disable OS_Prober:

```
gksudo gedit /etc/default/grub
GRUB_DISABLE_OS_PROBER=true
```

Again run 'update-grub'

---

### Post by Xubuntist on 2014-03-28
Bad news then...```
$ sudo update-grub
[sudo] password for darees: 
Création de grub.cfg…
Image Linux trouvée : /boot/vmlinuz-3.11.0-18-generic
Image mémoire initiale trouvée : /boot/initrd.img-3.11.0-18-generic
Image Linux trouvée : /boot/vmlinuz-3.11.0-12-generic
Image mémoire initiale trouvée : /boot/initrd.img-3.11.0-12-generic
Found memtest86+ image: /boot/memtest86+.bin
Windows NT/2000/XP trouvé sur /dev/sda2
fait


```

---

### Post by Xubuntist on 2014-03-28
PARTED

```
$ sudo parted -l
Modèle: ATA WDC WD1600AAJS-0 (scsi)
Disque /dev/sda : 160GB
Taille des secteurs (logiques/physiques): 512B/512B
Table de partitions : msdos

Numéro  Début   Fin    Taille  Type      Système de fichiers  Fanions
 1      32,3kB  107GB  107GB   primary   ext4                 démarrage
 3      107GB   155GB  48,3GB  extended
 5      107GB   154GB  47,4GB  logical   ext4
 6      154GB   155GB  937MB   logical   linux-swap(v1)
 2      155GB   160GB  4861MB  primary   fat32                diag


```

FDISK

```
$ sudo fdisk -l

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 têtes, 63 secteurs/piste, 19457 cylindres, total 312581808 secteurs
Unités = secteurs de 1 * 512 = 512 octets
Taille de secteur (logique / physique) : 512 octets / 512 octets
taille d'E/S (minimale / optimale) : 512 octets / 512 octets
Identifiant de disque : 0x75adc3f6

Périphérique Amorçage  Début         Fin      Blocs    Id. Système
/dev/sda1   *          63   208693825   104346881+  83  Linux
/dev/sda2       303082290   312576704     4747207+  12  Compaq diagnostics
/dev/sda3       208695294   303081471    47193089    5  Étendue
/dev/sda5       208695296   301248511    46276608   83  Linux
/dev/sda6       301250560   303081471      915456   82  partition d'échange Linux / Solaris

Les entrées de la table de partitions ne sont pas dans l'ordre du disque
```

---

### Post by fantab on 2014-03-28
Did you edit /etc/default/grub?
Post the output of:
```
cat /etc/default/grub
```

---

### Post by frank18 on 2014-03-29
Wouldn't be easier to reinstall from scratch? and you should install xubuntu14.04 that is running like a champ on my PC that is low on resources P4

---

### Post by fantab on 2014-03-29
Its your choice.

But do you really want to re-install a bootable and working Xubuntu just because you have an 'unwanted' entry in the GRUB menu?
A new version, Xubuntu 14.04 will release in a few weeks, you might want to wait until then. When installing 14.04 you can set it up the way you want.

---

### Post by Xubuntist on 2014-03-29
> **fantab said:**
> But do you really want to re-install a bootable and working Xubuntu just because you have an 'unwanted' entry in the GRUB menu?

Yes, that's exactly my point. It's running like a dream on a crappy Lenovo A88 6449. All peripherals have been installed with working drivers. I have Skype with webcam working, Teamviewer autoloads to the system tray, printer, scanner, and all required software, plus icons, themes and wallpapers, it's all working. I don't want to **have** to go through that again for no ***real ***reason.

```
cat /etc/default/grub
# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.
# For full documentation of the options in this file, see:
#   info -f grub -n 'Simple configuration'

GRUB_DEFAULT=0
#GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""

# Uncomment to enable BadRAM filtering, modify to suit your needs
# This works with Linux (no patch required) and with any kernel that obtains
# the memory map information from GRUB (GNU Mach, kernel of FreeBSD ...)
#GRUB_BADRAM="0x01234567,0xfefefefe,0x89abcdef,0xefefefef"

# Uncomment to disable graphical terminal (grub-pc only)
#GRUB_TERMINAL=console

# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
#GRUB_GFXMODE=640x480

# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID=true

# Uncomment to disable generation of recovery mode menu entries
#GRUB_DISABLE_RECOVERY="true"

# Uncomment to get a beep at grub start
#GRUB_INIT_TUNE="480 440 1"

```

---

### Post by Xubuntist on 2014-03-29
> **fantab said:**
> Did you edit /etc/default/grub?

No, I haven't touched grub.

---

### Post by fantab on 2014-03-29
What detects other OS is 'os-prober'. Since you have only Xubuntu booting on that machine we can safely disable the os-prober. To disable it
```
gksudo gedit /etc/default/grub

***add the following Line to at the end of the file:
GRUB_DISABLE_OS_PROBER=true
```

See my [earlier post]("http://GRUB_DISABLE_OS_PROBER=true").

Save the file.

Run:
```
sudo update-grub
```

Reboot.

EDIT: while you are editing /etc/default/grub you can uncomment (ie remove '#' in front of the line):
**#**GRUB_HIDDEN_TIMEOUT=0 change this to
GRUB_HIDDEN_TIMEOUT=0

(Whenever we edit /etc/default/grub we run 'sudo update-grub' to write the changes.)

Now the OS will boot directly without displaying grub.

More info on GRUB: [https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)

---

### Post by Xubuntist on 2014-03-29
You, sir, are the man! 

(I know you already knew this but recognition is an absolute requirement and I doff my cap to you sir)

I have created a text file with everything I have learnt and, if the occasion presents itself, I will pass this on to those in need.

By the way, I've been studying [this file to understand more about GRUB and how it works]("http://www.dedoimedo.com/computers/grub.html"). Fascinating and very instructive.

---

### Post by Xubuntist on 2014-03-29
OK, just to update, I am now doing the most perilous part of the operation (judging by previous experience). I have deleted the old Windows and the Lenovo factory restore partitions. I have run the Live CD and I am expanding the Xubuntu partition to the full hard drive capacity plus increasing the linux-swap to 5Gb. This is taking about 25 minutes and I'll report back shortly.

---

### Post by fantab on 2014-03-29
I am glad you got everything under control.
If you think the thread issue is resolved then please mark the Thread as 'Solved'.

What you are reading about is GRUB LEGACY, we don't use that anymore, we use GRUB2: [http://www.dedoimedo.com/computers/grub-2.html](http://www.dedoimedo.com/computers/grub-2.html)
Ubuntu customizes GRUB2 somewhat. So reading Ubuntu WIKI, the link to which I posted earlier is a good bet.

---

### Post by Xubuntist on 2014-03-29
> **fantab said:**
> please mark the Thread as 'Solved'.
We're not there yet ;)

Reading your link now, thank you!

---

### Post by Xubuntist on 2014-03-29
OK, I'm fairly stunned that nothing went wrong! Having followed all of the advice in other posts I've found I did the following (and noted it down for future reference, having a lousy memory):

Run the Xubuntu LiveCD and open GParted
  Turn swap OFF on the linux-swap partition and unmount ALL partitions
  Remove or reformat the Windows partition as EXT4 as required (deleted Windows and the Lenovo factory restore partitions in this case)
  Resize the Xubuntu and linux-swap partitions as required (this will take time : 25 minutes in this case, so not exactly long)
  Switch swap back ON on the linux-swap
  Reboot

The PC booted up straight into my Xubuntu install. I'm absolutely delighted and this is due directly to the help received in this and other threads **and** the confidence that I have gained by being so aided. Every disaster that I have created by my own lack of knowledge has been repaired/averted because of these forums and I am, without a shadow of a doubt, a (X)Ubuntu convert.

Marked as solved and extremely grateful to everybody that it is!

---

