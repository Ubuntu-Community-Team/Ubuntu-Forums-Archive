---
title: "Floppy Drive Question"
date: 2010-06-16
forum: Installation &amp; Upgrades
---

### Post by bayouoldguy on 2010-06-16
I upgraded from Ubuntu 8.10 LTS to 10.04 LTS the other day. I cannot get the floppy drive to read , getting a " no media detected " message. I found a site " justanotherwebblog.worldpress.com "How To : Use Floppy in Ubuntu 8.10", stating that by default, the use of floppy drives is disabled in Ubuntu 8.10.
My question is if I updated to 10.04 LTS, as I have done, would the disabled floppy configuuration still apply ?. I can get a light on the floppy when I attempt to use it from the "Places- Floppy Drive" list, but cannot open the floppy to use the JPEG files.
A floppy is a neat way to move JPEG files to Ubuntu from Windows & use the great GIMP image editor.
Any ideas for a fix ??........George

---

### Post by FireFighter on 2010-06-16
I don't have an answer to your problem and am only posting to say that my ability to access my floppy drive quit working today after the latest updates for 10.04. Was working fine yesterday. Will follow your post and see what comes of it. I guess I am telling you that if you have an updated 10.04, that might be the reason for it not working. :confused:

---

### Post by psusi on 2010-06-16
If you still have one of these clunkers it should still work, but seriously... it's 30 year old technology that was obsolete more than 10 years ago and it has been at least 5 years now since OEMs finally stopped building systems with them.  They don't even hold 1.44 mb of data, which is about the size of a typical jpeg that you intend to transfer.  Why not get a usb flash memory stick instead?

---

### Post by plucky on 2010-06-17
The floppy on my test system running 10.04lts works.

Open a terminal and ```
mount /dev/fd0
``` with a floppy disk loaded.Post any errors.

Also from the terminal,input ```
lsmod
``` and see if the word **floppy** is in the list.If it is,the floppy driver is loaded.
Post output of ```
cat /etc/fstab
``` does it have a line for the floppy?

---

### Post by cascade9 on 2010-06-17
> **psusi said:**
> They don't even hold 1.44 mb of data, which is about the size of a typical jpeg that you intend to transfer.  Why not get a usb flash memory stick instead?

Cheap, easy, fast, USB flash drives are superiour in every way to floppies IMO. 

I havent had a floppy drive in any of my systems for over 7 years now.....

*edit- some systems I have still have the floppy in place, mainly because I dotn want a gaping hole into my case. They all have the power and data cables removed though.

---

### Post by bayouoldguy on 2010-06-17
Here it is ::: seems to list floppy....George
george@george-desktop:~$ mount /dev/fdo
mount: can't find /dev/fdo in /etc/fstab or /etc/mtab
george@george-desktop:~$ lsmod
Module                  Size  Used by
binfmt_misc             6587  1 
snd_emu10k1_synth       5156  0 
snd_emux_synth         31695  1 snd_emu10k1_synth
snd_seq_virmidi         4213  1 snd_emux_synth
snd_seq_midi_emul       5492  1 snd_emux_synth
fbcon                  35102  71 
tileblit                2031  1 fbcon
font                    7557  1 fbcon
bitblit                 4707  1 fbcon
softcursor              1189  1 bitblit
vga16fb                11385  1 
vgastate                8961  1 vga16fb
snd_emu10k1           130627  3 snd_emu10k1_synth
snd_ac97_codec        100646  1 snd_emu10k1
ac97_bus                1002  1 snd_ac97_codec
snd_pcm_oss            35308  0 
snd_mixer_oss          13746  1 snd_pcm_oss
snd_pcm                70662  3 snd_emu10k1,snd_ac97_codec,snd_pcm_oss
snd_page_alloc          7076  2 snd_emu10k1,snd_pcm
snd_util_mem            3106  2 snd_emux_synth,snd_emu10k1
snd_hwdep               5412  2 snd_emux_synth,snd_emu10k1
snd_seq_dummy           1338  0 
snd_seq_oss            26726  0 
snd_seq_midi            4557  0 
snd_rawmidi            19056  3 snd_seq_virmidi,snd_emu10k1,snd_seq_midi
snd_seq_midi_event      6003  3 snd_seq_virmidi,snd_seq_oss,snd_seq_midi
snd_seq                47263  9 snd_emux_synth,snd_seq_virmidi,snd_seq_midi_emul,snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
nouveau               467048  0 
snd_timer              19098  3 snd_emu10k1,snd_pcm,snd_seq
snd_seq_device          5700  8 snd_emu10k1_synth,snd_emux_synth,snd_emu10k1,snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
ttm                    49943  1 nouveau
drm_kms_helper         29297  1 nouveau
ppdev                   5259  0 
snd                    54148  17 snd_emux_synth,snd_seq_virmidi,snd_emu10k1,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_hwdep,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
sbp2                   19448  0 
joydev                  8708  0 
drm                   162471  3 nouveau,ttm,drm_kms_helper
psmouse                63245  0 
serio_raw               3978  0 
via686a                10986  0 
emu10k1_gp              1492  0 
i2c_algo_bit            5028  1 nouveau
amd_k7_agp              4892  1 
i2c_viapro              5573  0 
soundcore               6620  1 snd
parport_pc             25962  1 
gameport                9089  2 emu10k1_gp
agpgart                31724  3 ttm,drm,amd_k7_agp
shpchp                 28820  0 
lp                      7028  0 
parport                32635  3 ppdev,parport_pc,lp
hid_logitech            7388  0 
ff_memless              4093  1 hid_logitech
ohci1394               26950  0 
8139too                18545  0 
floppy                 53016  0 
pata_via                7272  2 
mii                     4381  1 8139too
ieee1394               81181  2 sbp2,ohci1394
usbhid                 36110  1 hid_logitech
hid                    67032  2 hid_logitech,usbhid
george@george-desktop:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda3
UUID=df0200e3-e6e9-439a-922f-100d92af0c58 /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda6
UUID=58b7db92-174a-463c-b372-99f8b01351a2 none            swap    sw              0       0
/dev/hdd        /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/hdc        /media/cdrom1   udf,iso9660 user,noauto,exec 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec 0       0
george@george-desktop:~$ ^C
george@george-desktop:~$

---

### Post by dabl on 2010-06-17
All modern Linux distributions omit loading of the floppy module by default, for efficiency.

Usually you can load the module and get the floppy drive working with

```
sudo modprobe floppy
```

---

### Post by bayouoldguy on 2010-06-17
Update to my edited post....I tried a 1.0 
gig flashdrive w/ JPEG's......it will open..guess I am good to go.
I still want to solve the floppy problem if I can....."G"

---

### Post by bayouoldguy on 2010-06-17
Hmmmm...here is results of that....G"
( where do I add these ?).
george@george-desktop:~$ sudo modprobe floppy
[sudo] password for george: 
WARNING: All config files need .conf: /etc/modprobe.d/blacklist-modem, it will be ignored in a future release.
WARNING: All config files need .conf: /etc/modprobe.d/bluez, it will be ignored in a future release.
WARNING: All config files need .conf: /etc/modprobe.d/alsa-base, it will be ignored in a future release.
george@george-desktop:~$

---

### Post by plucky on 2010-06-17
> floppy 53016 0 

Floppy module is already there,so no need to load it again.

> george@george-desktop:~$ mount /dev/fdo
mount: can't find /dev/fdo in /etc/fstab or /etc/mtab

That should be fd0 where 0=zero not a letter o.

> /dev/fd0 /media/floppy0 auto rw,user,noauto,exec 0 0


That is the correct line for your fstab file.

Try the correct mount command and see what happens.

Good Luck

---

### Post by bayouoldguy on 2010-06-17
> **plucky said:**
> Floppy module is already there,so no need to load it again.



That should be fd0 where 0=zero not a letter o.




That is the correct line for your fstab file.

Try the correct mount command and see what happens.

Good Luck

tried again...sorry for the first mistake....."G'
results:george@george-desktop:~$ mount/dev/fd0
bash: mount/dev/fd0: No such file or directory
george@george-desktop:~$

---

### Post by bayouoldguy on 2010-06-17
another attempt: george@george-desktop:~$ mount /dev/fd0
mount: /dev/fd0 is not a valid block device
george@george-desktop:~$

---

### Post by dabl on 2010-06-17
Is there a diskette in the floppy drive?

---

### Post by bayouoldguy on 2010-06-17
> **dabl said:**
> Is there a diskette in the floppy drive?
Re-ran this in xterm:
george@george-desktop:~$ sudo modprobe floppy
[sudo] password for george: 
WARNING: All config files need .conf: /etc/modprobe.d/blacklist-modem, it will be ignored in a future release.
WARNING: All config files need .conf: /etc/modprobe.d/bluez, it will be ignored in a future release.
WARNING: All config files need .conf: /etc/modprobe.d/alsa-base, it will be ignored in a future release.
george@george-desktop:~$ sudo mkdir /media/floppy
mkdir: cannot create directory `/media/floppy': File exists
george@george-desktop:~$ sudo mount /dev/fd0 /media/floppy
mount: /dev/fd0 is not a valid block device
placed floppy in drive...then :
george@george-desktop:~$ sudo mount /dev/fd0 /media/floppy
mount: block device /dev/fd0 is write-protected, mounting read-only
george@george-desktop:~$
..........no read data from JPEG's on clean floppy...still looking for an answer...."G' 
....Still showing "no media detected" using the Disk Utility in 10.04

---

### Post by bayouoldguy on 2010-06-17
And also readout of :
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda3
UUID=df0200e3-e6e9-439a-922f-100d92af0c58 /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda6
UUID=58b7db92-174a-463c-b372-99f8b01351a2 none            swap    sw              0       0
/dev/hdd        /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/hdc        /media/cdrom1   udf,iso9660 user,noauto,exec 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec 0       0
....any thoughts ????.."G"

---

### Post by dabl on 2010-06-17
> **bayouoldguy said:**
> 

george@george-desktop:~$ sudo mount /dev/fd0 /media/floppy



Try that as
```

sudo mount -t vfat /dev/fd0 /media/floppy
```

---

### Post by bayouoldguy on 2010-06-17
> **dabl said:**
> Try that as
```

sudo mount -t vfat /dev/fd0 /media/floppy
```
nope: results  :george@george-desktop:~$ sudo mount /dev/fd0 /media/floppy
george@george-desktop:~$ sudo mount -t vfat /dev/fd0 /media/floppy
mount: wrong fs type, bad option, bad superblock on /dev/fd0,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

george@george-desktop:~$ 
                            Thanks anyway  ..."G"

---

### Post by bayouoldguy on 2010-06-17
Point of information: floppy drive is functional in Windows ME, opens same floppy I am trying on the 10.04....I know I am being hard headed, but I think others want to salvage some data on floppys.

---

### Post by dabl on 2010-06-17
OK, I'm officially annoyed now.    :lolflag:

I'm about 2 hours from being able to test my rig, which is running both Kubuntu 10.04 and sidux.  I'll let you know ....

---

### Post by bayouoldguy on 2010-06-17
> **dabl said:**
> OK, I'm officially annoyed now.    :lolflag:

I'm about 2 hours from being able to test my rig, which is running both Kubuntu 10.04 and sidux.  I'll let you know ....
dabl...thanks for the effort, obviously something is left out for the floppy drive to mount in "read" & not be able to display the JPEG files.... I too will be away for a couple of hours....."G"

---

### Post by dabl on 2010-06-17
OK, so, I dunno what to say.

```
dabl@lucid:~$ uname -a
Linux lucid 2.6.32-22-generic #36-Ubuntu SMP Thu Jun 3 19:31:57 UTC 2010 x86_64 GNU/Linux
dabl@lucid:~$ sudo modprobe floppy
[sudo] password for dabl: 
dabl@lucid:~$ ls -la /dev/fd0
brw-rw---- 1 root floppy 2, 0 2010-06-17 15:52 /dev/fd0
dabl@lucid:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda1 during installation
UUID=8cd86caa-8f74-46d5-829a-32b92bb77c2c /               ext4    noatime,errors=remount-ro 0       1
# swap was on /dev/sdc2 during installation
UUID=8f03cf64-35dd-4d7f-b055-2d42aa291028 none            swap    sw              0       0
# /dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
UUID=bef7fc54-d120-4869-920c-edc64a214bae /mnt/DOCS             ext4    auto,users,rw,exec,noatime      0       2
UUID=2b7ce29a-4550-4c6f-9171-8406d9688da7 /mnt/DOCSPIXBAK       jfs     auto,users,rw,exec,noatime      0       2
UUID=1e908a65-7ddb-4a1f-9913-d5a82ddb3137 /mnt/MUSIC            ext4    auto,users,rw,exec,noatime      0       2
UUID=b69c6415-23e4-4e96-9f72-17d2d7736b93 /mnt/MUSICBAK         jfs     auto,users,rw,exec,noatime      0       2
UUID=dfd5d21c-b8d7-4dd7-8d44-ac3146008354 /mnt/SIDUX            jfs     auto,users,rw,exec,noatime      0       2
UUID=932854dc-d16b-4612-9bd7-37345d1def09 /mnt/VIDEOS           ext4    auto,users,rw,exec,noatime      0       2
UUID=86da0233-4b7e-4ff9-b9f1-0ca338922c37 /mnt/VIDEOSBAK        jfs     auto,users,rw,exec,noatime      0       2
UUID=a1934295-3ff7-4700-901a-637513a74cfa /mnt/WHATEVER         ext4    auto,users,rw,exec,noatime      0       2
/dev/cdrom       /media/cdrom             udf,iso9660     noauto,ro,users                            0      0
/dev/fd0         /media/fd0               auto            noauto,rw,users                            0      0
dabl@lucid:~$ cd /media
dabl@lucid:/media$ ls
fd0  floppy  floppy0  tmp
dabl@lucid:/media$ cd /floppy
dabl@lucid:/media/floppy$ sudo cp /home/dabl/ss3200.exe .
dabl@lucid:/media/floppy$ ls
ss3200.exe
dabl@lucid:/media/floppy$
```

So, the good news is, it does work. The other news is, despite what it says in /etc/fstab about the diskette being mounted at /media/fd0, it turns out to actually be located at /media/floppy.  And it is owned by root, so "sudo" is required to make use of it.

Whew, I thought I was losing (the rest of) my marbles there for a while!  :lolflag:

---

### Post by bayouoldguy on 2010-06-18
> **dabl said:**
> OK, so, I dunno what to say.

```
dabl@lucid:~$ uname -a
Linux lucid 2.6.32-22-generic #36-Ubuntu SMP Thu Jun 3 19:31:57 UTC 2010 x86_64 GNU/Linux
dabl@lucid:~$ sudo modprobe floppy
[sudo] password for dabl: 
dabl@lucid:~$ ls -la /dev/fd0
brw-rw---- 1 root floppy 2, 0 2010-06-17 15:52 /dev/fd0
dabl@lucid:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda1 during installation
UUID=8cd86caa-8f74-46d5-829a-32b92bb77c2c /               ext4    noatime,errors=remount-ro 0       1
# swap was on /dev/sdc2 during installation
UUID=8f03cf64-35dd-4d7f-b055-2d42aa291028 none            swap    sw              0       0
# /dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
UUID=bef7fc54-d120-4869-920c-edc64a214bae /mnt/DOCS             ext4    auto,users,rw,exec,noatime      0       2
UUID=2b7ce29a-4550-4c6f-9171-8406d9688da7 /mnt/DOCSPIXBAK       jfs     auto,users,rw,exec,noatime      0       2
UUID=1e908a65-7ddb-4a1f-9913-d5a82ddb3137 /mnt/MUSIC            ext4    auto,users,rw,exec,noatime      0       2
UUID=b69c6415-23e4-4e96-9f72-17d2d7736b93 /mnt/MUSICBAK         jfs     auto,users,rw,exec,noatime      0       2
UUID=dfd5d21c-b8d7-4dd7-8d44-ac3146008354 /mnt/SIDUX            jfs     auto,users,rw,exec,noatime      0       2
UUID=932854dc-d16b-4612-9bd7-37345d1def09 /mnt/VIDEOS           ext4    auto,users,rw,exec,noatime      0       2
UUID=86da0233-4b7e-4ff9-b9f1-0ca338922c37 /mnt/VIDEOSBAK        jfs     auto,users,rw,exec,noatime      0       2
UUID=a1934295-3ff7-4700-901a-637513a74cfa /mnt/WHATEVER         ext4    auto,users,rw,exec,noatime      0       2
/dev/cdrom       /media/cdrom             udf,iso9660     noauto,ro,users                            0      0
[COLOR="Blue"]/dev/fd0         /media/fd0               auto            noauto,rw,users                            0      0
dabl@lucid:~$ cd /media[/COLOR]
dabl@lucid:/media$ ls
fd0  floppy  floppy0  tmp
dabl@lucid:/media$ cd /floppy
dabl@lucid:/media/floppy$ sudo cp /home/dabl/ss3200.exe .
dabl@lucid:/media/floppy$ ls
ss3200.exe
dabl@lucid:/media/floppy$
```

So, the good news is, it does work. The other news is, despite what it says in /etc/fstab about the diskette being mounted at /media/fd0, it turns out to actually be located at /media/floppy.  And it is owned by root, so "sudo" is required to make use of it.

Whew, I thought I was losing (the rest of) my marbles there for a while!  :lolflag:

Thanks dabl....Here is a search for a file :
george@george-desktop:~$ cd /floppy
bash: cd: /floppy: No such file or directory
george@george-desktop:~$ 
could this be the problem ?...how do I fix it ?.  "G"
also :george@george-desktop:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda3
UUID=df0200e3-e6e9-439a-922f-100d92af0c58 /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda6
UUID=58b7db92-174a-463c-b372-99f8b01351a2 none            swap    sw              0       0
/dev/hdd        /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/hdc        /media/cdrom1   udf,iso9660 user,noauto,exec 0       0
[COLOR="Blue"]/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec 0       0[/COLOR]
george@george-desktop:~$ ^C
george@george-desktop:~$ cat/etc/mtab
bash: cat/etc/mtab: No such file or directory
george@george-desktop:~$

---

### Post by bayouoldguy on 2010-06-18
dabl...does the various colors in this list signify anything ?.
george@george-desktop:~$ cd /media
george@george-desktop:/media$ ls
[COLOR="YellowGreen"]cdrom[/COLOR] [COLOR="RoyalBlue"] cdrom0  cdrom1  fd0[/COLOR] [/COLOR] [COLOR="YellowGreen"]floppy[/COLOR]  [COLOR="RoyalBlue"]floppy0[/COLOR]
 the "cdrom" & "floppy" are in a light green, the others are in a light blue !.
...just trying to find a solution...."G"

---

### Post by dabl on 2010-06-18
Yes, the colors do signify something -- but what?  You'll have to study up on the Ubuntu conventions for the terminal.

I'm presently booted in sidux, and on this OS (a pure Debian), the floppy diskette drive /dev/fd0 is mounted to /media/fd0.  No multi-color like Kubuntu. But, it is still working on my rig.

Have you confirmed that your diskette drive is set in BIOS?  Just a thought ....

---

### Post by plucky on 2010-06-19
> does the various colors in this list signify anything ?.


They are just folder/file types.e.g all the same colour are all the same type of file.(txt,pdf,dir etc)

> I upgraded from Ubuntu 8.10 LTS to 10.04 LTS the other day

I think this could be the problem as I did a clean install of 10.04 and my floppy drive works perfectly even without sudo.

Something to consider.

Good Luck

p.s It is broken again in Meerkat (Dual boot Lucid and Meerkat)

---

### Post by dabl on 2010-06-19
> **plucky said:**
> 

I think this could be the problem as I did a clean install of 10.04 and my floppy drive works perfectly even without sudo.


You could test this with a 10.04 Live CD.   :wink:

---

### Post by bayouoldguy on 2010-06-20
> **dabl said:**
> Yes, the colors do signify something -- but what?  You'll have to study up on the Ubuntu conventions for the terminal.

I'm presently booted in sidux, and on this OS (a pure Debian), the floppy diskette drive /dev/fd0 is mounted to /media/fd0.  No multi-color like Kubuntu. But, it is still working on my rig.

Have you confirmed that your diskette drive is set in BIOS?  Just a thought ....

dabl....diskette drive functions in the Windows ME partition. I have dual OS
to play with...don't use the Windows except for some programs of "old" that won't work in later Windows..... BIOS must be OK....."G"

---

### Post by bayouoldguy on 2010-06-22
I guess we all will wait for a "fix". I have been searching threads & found MANY Problems with 10.04 installs either trying to mount a floppy where none exists, & a good many with the same request that I have, Not any good solutions so far. I will check back from time-to-time & see if anyone has found the solution......"G":confused:

---

### Post by lubigor on 2010-06-27
I have the same problem after updating my ubuntu 10.04 before that floppy worked perfectly,now i can only open it with LiveCD:confused::confused: i tried all kind of tutorial and how-to guides but nothing worked.

If someone find solution please Reply

---

### Post by Brian Vaughan on 2010-06-27
I've been having similar trouble. My floppy drive works in Windows 7. In Ubuntu 10.04, it doesn't.

As for why this matters: I've got stacks of old floppy disks around, with content I'd like to access. I'm sure I'm not the only one. Also, I understand that many old devices other than personal computers still use floppy disks -- there was a discussion of this on Slashdot recently. While it's understandable that, given the obsolescence of floppy disks, that they would no longer be enabled by default, there are still cases where it's useful to be able to access them.

---

### Post by Brian Vaughan on 2010-06-27
Some additional things I've found, with a test floppy disk in the drive:

These disk formatting commands appear to work:
```
sudo mformat -f 1440 A:
sudo fdformat /dev/fd0
```

```
sudo fdlist
```
produces this output:
```
NAME   TYPE  STATUS
 fd0  1440K  not mounted
```

```
sudo fdmount
```
produces this output:
```
fdmount (/dev/fd0): Can't access /fd0: No such file or directory
```

It looks to me like things fail at the point of mounting the disk. I'm not sure how to proceed.

---

### Post by lubigor on 2010-06-28
I reinstaled my ubuntu 10.04 ,before update floppy worked fine but when i press update ([COLOR=#000000]Approximately 200MB) again i have error                 

 -Unable to mount floppy No media in drive- 

so problem is in update 100%,but what ?
[/COLOR]

---

### Post by Brian Vaughan on 2010-06-28
There's considerably more information here:
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/441835?comments=all](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/441835?comments=all)

In short, the Ubuntu team is aware of the problem, but it's not an easy bug to fix.

---

### Post by RiP13 on 2010-06-28
Hi all, 

this solution is working for my Xubuntu 10.04: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/441835/comments/227](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/441835/comments/227)

---

### Post by lubigor on 2010-06-29
YES This work 

For all others you nead to down grade you udisks with synaptic

i change from udisks (1.0.1-1build1) lucid update
to udisks (1.0.1-1build1) lucid 

):P):P):P

---

### Post by plucky on 2010-06-29
> **lubigor said:**
> yes this work 

for all others you nead to down grade you udisks with synaptic

i change from udisks (1.0.1-1build1) lucid update
to udisks (1.0.1-1build1) lucid 

):p):p):p

+1 for me too

---

### Post by bayouoldguy on 2010-06-29
lubigor & plucky....thanks for the fix !. Was able to mount the floppy  & read (open ) two floppy disks & review the data.
For those who may ask...go to synaptic, open it, & type in "udisks". The result will show you probably "udisks(1.0.1-1ubuntu1)". Select properties & go to versions header, select the "1build1" package & go back to package header & select "force version" option....proceed as usual & it will install. Go to places & click on the floppy & it should mount!
I don't know if the floppy will have to be re-mounted each use or not, but it will be a "work-around", hope it won't be lost with upgrades...but may have to be vigilant.....Thanks guys......"G"):P

---

### Post by bayouoldguy on 2010-06-29
** Lets give credit to RiP13** ! The re-boot un-mounts the floppy, & you need to have a floppy in the drive to mount it...." Places...floppy disk" At least its a working solution to those who want to view old data..."G"

---

### Post by bayouoldguy on 2010-07-01
**To all interested floppy users !**....Ubuntu Update Manager will attempt to update udisks package....if you permit, it will revert to (1.0.1-1ubuntu1) , revised in a boot correction version.
You will need to **"lock in"** the version in your Synaptic Package Manager to prevent any updates to your "downgraded version , (1.0.1-1build1).
....never a "dull" moment in computers !!!!......."G"](*,)

---

### Post by chris1379 on 2010-07-04
> **lubigor said:**
> YES This work 

For all others you nead to down grade you udisks with synaptic

i change from udisks (1.0.1-1build1) lucid update
to udisks (1.0.1-1build1) lucid 

):P):P):P

But doesn't this bring back the original problem of trying to mount a nonexistent floppy? I'm sure most of you are thinking that you either have a floppy drive and downgrade udisks or don't have a floppy drive and leave it alone. My problem is sometimes I have a floppy drive and sometimes I don't. It's a laptop and the drive is removable. I admit I don't use it much but I needed to make a BIOS update disk yesterday and guess what I had to do. Yep, I had to use Windows. I get the message,"[COLOR=#000000]Unable to mount floppy No media in drive" when I try to mount a floppy. [/COLOR]

---

### Post by Michl on 2010-07-25
> **bayouoldguy said:**
> lubigor & plucky....thanks for the fix !. Was able to mount the floppy  & read (open ) two floppy disks & review the data.
For those who may ask...go to synaptic, open it, & type in "udisks". The result will show you probably "udisks(1.0.1-1ubuntu1)". Select properties & go to versions header, select the "1build1" package & go back to package header & select "force version" option....proceed as usual & it will install. Go to places & click on the floppy & it should mount!
I don't know if the floppy will have to be re-mounted each use or not, but it will be a "work-around", hope it won't be lost with upgrades...but may have to be vigilant.....Thanks guys......"G"):P

Thank you thank you...this works and no need to remount.  Just go to places and there is a nice floppy icon, click and all
those old files and folders appear.

---

### Post by neil33 on 2010-07-27
> **bayouoldguy said:**
> lubigor & plucky....thanks for the fix !. Was able to mount the floppy  & read (open ) two floppy disks & review the data.
For those who may ask...go to synaptic, open it, & type in "udisks". The result will show you probably "udisks(1.0.1-1ubuntu1)". Select properties & go to versions header, select the "1build1" package & go back to package header & select "force version" option....proceed as usual & it will install. Go to places & click on the floppy & it should mount!
I don't know if the floppy will have to be re-mounted each use or not, but it will be a "work-around", hope it won't be lost with upgrades...but may have to be vigilant.....Thanks guys......"G"):P

This technique solved the problem. The floppy drive  works now. Thanks so much!

Linux Rocks!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!

Neil in Edmonton

---

### Post by murphyac on 2010-07-28
> **bayouoldguy said:**
> lubigor & plucky....thanks for the fix !. Was able to mount the floppy  & read (open ) two floppy disks & review the data.
For those who may ask...go to synaptic, open it, & type in "udisks". The result will show you probably "udisks(1.0.1-1ubuntu1)". Select properties & go to versions header, select the "1build1" package & go back to package header & select "force version" option....proceed as usual & it will install. Go to places & click on the floppy & it should mount!
I don't know if the floppy will have to be re-mounted each use or not, but it will be a "work-around", hope it won't be lost with upgrades...but may have to be vigilant.....Thanks guys......"G"):P

This worked beautifully for me until today's (7/28/2010)  update to Lucid.  The previous updates didn't break anything.  After today's update, if I click on floppy drive, the motor starts and the light comes on, but that is all.  I'll try to unpin the "1build1" udisks package and install the update version, but I'm not very hopeful.  I'll report back with my findings.
Angela C. Murphy

---

### Post by murphyac on 2010-07-29
Well, installing the upgrade did not help at all.  Then I went back to udisks 1.0.1-1build1 using "force version", and did it also for udisks-doc, then locked them both.  Somehow it worked, I have my floppy drive back.  I need that drive.  I'm working with a couple of old computers - preUSB - and many files get transported via floppy.  
Hope this helps.
Angela C. Murphy

---

### Post by bayouoldguy on 2010-07-29
Reminder.......
 
To all interested floppy users !....Ubuntu Update Manager will attempt to update udisks package....if you permit, it will revert to (1.0.1-1ubuntu1) .
You will need to "lock in" the udisks downgrade version in your Synaptic Package Manager to prevent any updates to your "downgraded version , (1.0.1-1build1).
....never a "dull" moment in computers !!!!......."G"
__________________  Thanks to all who posted this problem..... "G":D

---

### Post by chris1379 on 2010-07-29
It's still broken for removable floppy drives. If I want the occasional use of the floppy drive, I have to use udisks 1.0.1-1build1 and disable the floppy drive in BIOS when it is removed. BTW, is it normal for the files on a floppy created in Windows to show as being owned by root? I can't write to the disk unless I use ```
sudo nautilus
```

---

### Post by kpoole on 2010-08-04
> **bayouoldguy said:**
> Reminder.......
 
To all interested floppy users !....Ubuntu Update Manager will attempt to update udisks package....if you permit, it will revert to (1.0.1-1ubuntu1) .
You will need to "lock in" the udisks downgrade version in your Synaptic Package Manager to prevent any updates to your "downgraded version , (1.0.1-1build1).
....never a "dull" moment in computers !!!!......."G"
__________________  Thanks to all who posted this problem..... "G":D

From one cranky old curmudgeon to, possibly, another, many thanks for bringing this to us.  I still have a few old floppies around that need to be preserved and finding Lucid not recognizing the floppy drive properly was becoming a bit of a show stopper for changing over my main workstation.

I've seen a few threads about this and the most ridiculous response was from one fellow who said the obvious solution was to switch to USB thumbdrives.  Of course, that didn't help get the data off the floppies and a few people told him so.  (should have checked, that might even have been near the beginning  of this thread.  ;-)

So, thanks to Bayouoldguy and his source for this solution.

---

### Post by joseielpi on 2010-08-06
I had the same problem Downgrading udisk makes access to floppy disk files finally posible. THANKS A LOT.

---

### Post by bayouoldguy on 2010-08-11
> **kpoole said:**
> From one cranky old curmudgeon to, possibly, another, many thanks for bringing this to us.  I still have a few old floppies around that need to be preserved and finding Lucid not recognizing the floppy drive properly was becoming a bit of a show stopper for changing over my main workstation.

I've seen a few threads about this and the most ridiculous response was from one fellow who said the obvious solution was to switch to USB thumbdrives.  Of course, that didn't help get the data off the floppies and a few people told him so.  (should have checked, that might even have been near the beginning  of this thread.  ;-)

So, thanks to Bayouoldguy and his source for this solution.

Actually....thanks to lubigor & plucky for their initial inputs, I just helped get the ball rolling with the "lock in" directions. You got to love ubuntu & the "forum" for finding stuff !....Also I like ubuntu more & more every revision, & am trying to find funds for an older laptop to install ubuntu to show off to "non-believers"..."G":D

---

### Post by mela on 2010-08-21
Thanks to ALL who contributed to this post! To those who found the solution, and especially to those successful users who wrote of their results which encouraged me to try this myself. 

Actually, it was easy and the process was painless, even for a beginner. My floppy lives again because of this regression fix. Viva Ubuntu!

---

### Post by kininja on 2010-12-30
Thank you for posting this solution! Worked perfectly!

---

### Post by Handssolow on 2011-01-02
With Lucid udisks 1build1 is available as an alternative version which I've installed and locked. I can reads floppy discs again.
With Maverick I added the Lucid packages to obtain 1build1 but I am still unable to use the floppy drive, getting this message-
mount: /dev/fd0 is not a valid block device

Edit: Comments I read in Launchpad suggest that Ubuntu's support of the floppy drive is becoming history. My attempts to get a floppy drive working with Maverick 10.10 ended with it halting on reboot with a /media/fd0 error. So I've removed the fd0 entry in fstab and /etc/modules that I'd put there and it boots normally again. At least I've got a Lucid machine that can read floppies.

---

### Post by csacpt on 2011-01-11
Worked for me as well, but truly disappointed that there are still those who seem to decide for others what we are permitted to use. Looks as though I will be using Lucid(patched) no matter what else may be considered "newer and better." Pity that in this instance even Windows is better. Thanks for the help anyway, at least the people here still understand.


Update: Well, seems I spoke too soon. The fix only sort of works. Floppy is OK  but several applications are broken, Brasero and Rhythmbox that I have  found so far. I am not going to spend any more time on something that  should be simple. Windows will let me use my hardware without hassle so I  will use that to access data on that drive. Thanks anyway.

---

### Post by psusi on 2011-01-12
> **csacpt said:**
> Worked for me as well, but truly disappointed that there are still those who seem to decide for others what we are permitted to use. Looks as though I will be using Lucid(patched) no matter what else may be considered "newer and better." Pity that in this instance even Windows is better. Thanks for the help anyway, at least the people here still understand.

Nobody decided what you are permitted to use.  The driver just isn't included by default any more because it is not useful to 99% of Ubuntu users.

There is a large difference between me choosing not to hand you the keys to a new car, and telling you that you can never drive.

---

### Post by wkulecz on 2011-01-12
> I reinstaled my ubuntu 10.04 ,before update floppy worked fine but when i press update (Approximately 200MB) again i have error

For an LTS release the QA/QC on updates seems to be lacking  I've had several previously perfectly working systems broken after updates.

---

### Post by csacpt on 2011-01-12
?

---

### Post by csacpt on 2011-01-12
.

---

### Post by csacpt on 2011-01-12
.

---

### Post by csacpt on 2011-01-12
.

---

### Post by RogerDavis on 2011-05-22
How can this be marked "SOLVED" when there is no solution !?!

---

### Post by warfie on 2011-07-05
> **lubigor said:**
> YES This work 

For all others you nead to down grade you udisks with synaptic

i change from udisks (1.0.1-1build1) lucid update
to udisks (1.0.1-1build1) lucid 

):P):P):P

After hours of F&*^%#G around, this worked!

Thanks dude! I owe you one!

---

### Post by RogerDavis on 2011-07-06
This is encouraging, but I don't understand how to accomplish what 
-----
"For all others you nead to down grade you udisks with synaptic

i change from udisks (1.0.1-1build1) lucid update
to udisks (1.0.1-1build1) lucid "
-----
says to do.

I have uttered the prerequisite penguin chants, but I have not sacrificed the proverbial bird upon my keyboard so that it will automatically do what is said above.  I just can't do that...

Can someone translate this into regulartalk, so I don't have to do the sacrifice?

---

### Post by confused57 on 2011-07-06
Open synaptic package manager, enter udisks in
Quick Search, click on udisks so that it is highlighted, then Package---> Force Version.
Here you change the currently installed & force the other version(click on Apply).  Once you do this, you'll need to lock the version, so that Update doesn't reinstall the newest version.

---

### Post by createdcreature on 2011-07-06
Use the command 'udisks --mount /dev/fd0'.;)

---

### Post by RogerDavis on 2011-07-06
Now I understand, I hope clearly.

This does prompt the questions below:
1) Does this only degrade that particular module, or the entire system?
2) What does this mean in terms of lost functions, safety, etc.?
3) Will any upgrades at all be possible in the future, to this module or the system (see #1) after locking?  If so, what might be lost then?
4) You reference this version as "other", implying alternate but equal, and reference what we are blocking as the newest version, implying that what will end up in use is an older version.  Is it actually alternate, or older?
Thanks!

---

### Post by confused57 on 2011-07-06
> **RogerDavis said:**
> Now I understand, I hope clearly.

This does prompt the questions below:
1) Does this only degrade that particular module, or the entire system?
2) What does this mean in terms of lost functions, safety, etc.?
3) Will any upgrades at all be possible in the future, to this module or the system (see #1) after locking?  If so, what might be lost then?
4) You reference this version as "other", implying alternate but equal, and reference what we are blocking as the newest version, implying that what will end up in use is an older version.  Is it actually alternate, or older?
Thanks!

I wasn't sure if it was a security issue or not, but found this on launchpad:
[https://bugs.launchpad.net/ubuntu/+source/udisks/+bug/539515](https://bugs.launchpad.net/ubuntu/+source/udisks/+bug/539515)

It may be that "udisks (1.0.1-1build1) lucid update" is a fix for the bug mentioned on launchpad.

---

### Post by RogerDavis on 2011-07-11
This prompts the questions below:
1) Does this only degrade that particular module, or the entire system?
2) What does this mean in terms of lost functions, safety, etc.?
3) Will any upgrades at all be possible in the future, to this module or the system (see #1) after locking? If so, what might be lost then?
4) You reference this version as "other", implying alternate but equal, and reference what we are blocking as the newest version, implying that what will end up in use is an older version. Is it actually alternate, or older?
Thanks!

---

### Post by lubigor on 2011-08-19
> **RogerDavis said:**
> This prompts the questions below:
1) Does this only degrade that particular module, or the entire system?
2) What does this mean in terms of lost functions, safety, etc.?
3) Will any upgrades at all be possible in the future, to this module or the system (see #1) after locking? If so, what might be lost then?
4) You reference this version as "other", implying alternate but equal, and reference what we are blocking as the newest version, implying that what will end up in use is an older version. Is it actually alternate, or older?
Thanks!

LOL this topic is still alive.

I am not using ubuntu now (i'm on XP :( because old radeon graphic )

but as far as I can remember only reason they launch (1.0.1-1build1) lucid update (NEW) instead of udisks (1.0.1-1build1) lucid (OLD) is that some new laptops and PCs have  problem because ubuntu(or something like that) is looking for floppy on boot and OS can't start, so quick fix was to delete floppy support . 

I don't think you will have any security problem.

 Does someone use floppy on  11.04  version:confused:

---

### Post by thewarlock on 2011-08-21
udisks --mount /dev/fd0   worked for me.

udisks 1.0.2-ubuntu1  is what's installed in 11.04 here.

automounting is NOT working, but I didn't have the FD installed when I put 11.04 in.

will see if I can get automounting working.

edit:  files show up in a terminal, yet do NOT show up on the desktop/file manager.

sigh.


> **lubigor said:**
> LOL this topic is still alive.

I am not using ubuntu now (i'm on XP :( because old radeon graphic )

but as far as I can remember only reason they launch (1.0.1-1build1) lucid update (NEW) instead of udisks (1.0.1-1build1) lucid (OLD) is that some new laptops and PCs have  problem because ubuntu(or something like that) is looking for floppy on boot and OS can't start, so quick fix was to delete floppy support . 

I don't think you will have any security problem.

 Does someone use floppy on  11.04  version:confused:

---

### Post by RogerDavis on 2011-08-25
I can use  udisks --mount /dev/fd0  to get the floppy to show up in file manager and gnome commander.   However, no operations can be done with it.  

It seemed to work for a short time, then quit.

Are there any further developments?

I repeated, and now it seems to continue working.  Did anyone find a way to auto mount it?

After further working on it, it sometimes works, sometimes not.  Also, I can't format a floppy, it says "Device or Resource Busy".

---

### Post by Gerard08 on 2011-08-29
Great this worked for me too! I am looking for some old documents that may be on floppies. Perhaps me or someone could type up this fix and post it under "tutorials"? I spent about 4 hours trying to locate the problem

Thanks a bunch!

ger:P

---

