---
title: "Samba disk not connected with Karmic"
date: 2009-12-15
forum: Installation &amp; Upgrades
---

### Post by efmpsc on 2009-12-15
Hallo I am brand new of this forum.
I have an external disk I perfectly read with jaunty. I use with two partition, one for music named "varie", and the other one for backups named "disco_backup".
The fstab file is like this:
[I]#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda1 during installation
UUID=6d4205f3-f594-4343-9e5e-3d3a71027cd9 /       ext4    errors=remount-ro 0       1
# swap was on /dev/sda2 during installation
UUID=14e82894-825b-40a1-a8de-d70ce5720d05 none        swap    sw              0       0
/dev/sda3       /home  ext3  rw,defaults  0    0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
# Disco esterno
[B]//192.168.0.4/public /media/disco_backup cifs  credentials=/etc/samba/user,noexec  0 0
//192.168.0.4/varie /media/varie cifs  credentials=/etc/samba/user,noexec  0 0[/B]
#Telefonino Nokia 6234
obexfs#-u1 /media/Nokia fuse noauto,user,fsname=obexfs#-u1 0 0
#Installazione Guest Additions per VirtualBox
none /proc/bus/usb usbfs devgid=125,devmode=664 0 0[/I]

Moved to Karmic, same fstab: no way to see the disk.
I was forced to go back to jaunty and it's weeks I am trying karmic with VirtualBox but with no success. I am a little bit frustrated. Thanks for yr help.

---

### Post by efmpsc on 2009-12-19
Nobody can help me?

---

### Post by lmarmisa on 2009-12-19
Check the network configuration of your Karmic virtual machine in VirtualBox and switch from NAT to Bridge mode. If NAT mode is selected, you will have a lot of problems of communication with other machines of your LAN.

Best regards,

Luis

---

### Post by audiomick on 2009-12-19
Hi.
I think quite a few people had or are having problems with samba in karmic.

A good source for help with sambe is this thread:
[http://ubuntuforums.org/showthread.php?t=1169149](http://ubuntuforums.org/showthread.php?t=1169149)

---

### Post by efmpsc on 2009-12-24
Thank you for yr support. Unfortunately I did not fix the issue.
@Luis : I tried using Bridge mode setting in my VB Karmic; with "sudo mount -a" I receved back "Network unreacheable"; when set NAT, network is perfectly seen.

@Michael: I tried all the instructions of the link you added; by the way some of them were already in. Again no success.

I checked again all setting in my standard jaunty environment and in Karmic one and everything is the same (fstab, smb.conf, nsswitch.conf): in Jaunty run smoothly, in Karmic I can't see anything....

If somebody discovers something which solves pls help me, I will stay tuned!

Paolo

---

### Post by lmarmisa on 2009-12-24
Sorry, my previous post is wrong. It belongs to another thread.

---

### Post by lmarmisa on 2009-12-24
Hi Paolo,

Please, follow this steps in order to identify your problem.

First step: try checking the communications with the CIFS file server:

```

ping 192.168.0.4

```Second step: check if the two mounting points ***/media/disco_backup ***and ***/media/varie ***exist:
```

ls -l /media 

```Third step: verify (with Synaptic) that the smbfs package is installed.

Fourth step: try to access to the shared directories using the command smbclient

```

smbclient -U your_samba_user //192.168.0.4/public

```The command will ask for your passwd. If you get a prompt similar to **smb: \> **the test is good. Type **dir** and **quit** .

Repeat the test with the other directory:

```

smbclient -U your_samba_user //192.168.0.4/varie

```Fifth step: try to mount manually your directories:

```

sudo mount -t cifs //192.168.0.4/public /media/disco_backup -o username=your_username,password=your_passwd,iocharset=utf8,file_mode=0777,dir_mode=0777
sudo mount -t cifs //192.168.0.4/varie /media/varie -o username=your_username,password=your_passwd,iocharset=utf8,file_mode=0777,dir_mode=0777

```Last step: check if the file /etc/samba/user exists and if its content is good.

Follow theses steps until you get some kind of error and post the results.

Best regards and Merry Christmas,

Luis

---

### Post by efmpsc on 2009-12-24
Thank you Luis. I tried everything you posted, I cannot say it works but something interesting arose.


[LIST]
[*]ping: OK, I stopped the process after abt. 1000 chunks of 64 bytes correctly exchanged.
[/LIST]

[LIST]
[*]the two mounting points ***/media/disco_backup ***and ***/media/varie ***exist.
[*]smb: I can reach **smb: \> **prompt. One thing more: when I type "dir" I receive:
[/LIST]
[INDENT][COLOR=Red]smb: \> dir
  .                                   D        0  Wed Dec 31 23:59:59 1969
  ..                                  D        0  Wed Dec 31 23:59:59 1969
  Ciajvkoskij.pdf                     A    34625  Tue Dec 28 09:25:12 2010
  Musica                              D        0  Sun Nov 30 08:14:48 1986
  Film                                D        0  Wed Dec 31 23:59:59 1969
  Programmi                           D        0  Wed Dec 31 23:59:59 1969

        12151 blocks of size 16777216. 5561 blocks available
[/COLOR][/INDENT]           which is correct. When I type "dir Musica" I receive:
[INDENT][COLOR=Red]smb: \> dir Musica
  &#61660;&#452;&#16384;&#23854;&#61660;&#452;                      2663897088  Wed Dec 31 23:59:59 1969

        12151 blocks of size 16777216. 5561 blocks available
[/COLOR][/INDENT]           which shows that after the first level of directories I have problems.

[LIST]
[*]sudo mount: no error with them. Nevertheless I cannot see anything after the highest level.
[/LIST]
One interesting point: if I go in Netwrok with Nautilus I can see everything perfectly...

Cheers, and Merry Christmas to you as well!

---

### Post by lmarmisa on 2009-12-24
This seems an odd problem, but your last comment about Nautilus is a good signal :).

I would recommend you to modify  temporarily your **/etc/fstab** file in this way:

```

/192.168.0.4/public /media/disco_backup cifs username=yourusername,password=yourpassword  0  0
/192.168.0.4/varie /media/varie cifs username=yourusername,password=yourpassword  0  0

```Are the remote directories mounted with this change?.

---

