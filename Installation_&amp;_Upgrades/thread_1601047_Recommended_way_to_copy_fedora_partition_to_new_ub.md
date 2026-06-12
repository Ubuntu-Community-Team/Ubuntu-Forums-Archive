---
title: "Recommended way to copy fedora partition to new ubuntu"
date: 2010-10-19
forum: Installation &amp; Upgrades
---

### Post by mancocapac on 2010-10-19
Hi Folks,

I have just switched from Fedora to Ubuntu, while not a complete newbie I am a novice linux user.

I want to copy from my old Fedora drive to my Ubuntu drive, specifically my /opt and and svn repos among
other(s).

From: [http://www.linuxquestions.org/questions/fedora-35/how-can-i-mount-lvm-partition-in-ubuntu-569507/](http://www.linuxquestions.org/questions/fedora-35/how-can-i-mount-lvm-partition-in-ubuntu-569507/)
I have managed to mount the drive via the following: 
```

237  sudo modprobe dm-mod
  238  sudo vgscan
  239  man vgchange
  240  sudo lvs
  243  sudo fdisk -l
  244  sudo vgchange -ay VolGroup00
  245  sudo lvs
  246    sudo mkdir /mnt/fcroot
  247  sudo mount /dev/VolGroup00/LogVol00 /mnt/fcroot -o ro,user
  248  cd /mnt/fcroot/
  260  sudo ls -al root
  261  df
  262  vgchange -a y
  263  sudo vgchange -a y
  265  sudo mount /dev/sdb3 /mnt/fcroot/opt -o ro,user

```My new drive is configured with 3 Volume Groups and several LVs each, 
e.g. /dev/mapper/VGSYS-optLV
                      19529128     32840  19496288   1% /opt 
and is using resierfs
/dev/mapper/VGSYS-optLV /opt            reiserfs defaults        0       2

while my Fedora drive is
```

/dev/VolGroup00/LogVol00 /                       ext3    defaults        1 1
UUID=f35429f9-bfdb-4aeb-851f-f16ade27bae5 /tmp                    ext3    defaults        1 2
UUID=861a7328-a3ec-4747-b530-574852dc3a42 /usr                    ext3    defaults        1 2
UUID=5fa4614d-8cb9-4ac9-8862-4a7e7e354ec1 /var                    ext3    defaults        1 2
UUID=4293f2d3-d806-4ba7-90ba-189d8408ac1f /usr/local              ext3    defaults        1 2
UUID=7b5283e1-655a-4245-a6a8-465013371982 /opt                    ext3    defaults        1 2
UUID=dfc9c73b-9d49-4845-ac98-1a6026625127 /home                   ext3    defaults        1 2
UUID=92bd6083-4300-4469-bb92-34a3743f3b40 /boot                   ext3    defaults        1 2

df
Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/mapper/VolGroup00-LogVol00
                      50379460   7130980  40689300  15% /
/dev/sda8             20161172    183852  18953180   1% /tmp
/dev/sda7             30233896   5917840  22780244  21% /usr
/dev/sda6             40313964    852168  37413912   3% /var
/dev/sda5             40313964    183040  38083040   1% /usr/local
/dev/sda3             60476068  13823604  43580436  25% /opt
/dev/sda2            100790036   4457608  91212516   5% /home
/dev/sda1               194442     28132    156271  16% /boot
tmpfs                  1032228      2484   1029744   1% /dev/shm


```my fedora /opt has lots of 3rd party sw with softlinks to my active version:
lrwxrwxrwx  1 root root    55 2009-04-10 12:08 eclipse -> eclipse_depo/ganymede-SR2-linux-gtk-JBossTools/eclipse/
drwxrwxr-x 12 root dev   4096 2009-04-10 13:54 eclipse_depo

Question: is there are recommended best way to copy all of this data? 

Thanks!
Tim

---

### Post by lemming465 on 2010-10-21
You may need to do more mount commands to pick up some of those fedora partitions.  I'd mount them where Fedora would, e.g. the Fedora /usr on /mnt/fcroot/usr, and so on.
To copy lots of files try something of the form *cp -a FROM1 FROM2 ... TO* or use a tar pipeline, such as *tar cf - THING1 THING2 ... | (cd /your/destination; tar -xf -)*

---

### Post by mancocapac on 2010-10-25
lemming465,

THanks for the info. I mounted the dirs as you suggested and went the *cp -a FROM1 FROM2 *route*. *The only issue I had was the group and user Ids were different between Fedora
and Ubuntu.So post copy I was left with Id's in the 500 range vs the 1000s that Ubuntu
uses. Not such a big deal but I had to reboot using my old drive to match the Ids to the 
actual names. For the next guy I suggest finding out the mapping of group & User names
to Ids before you do the copy and avoid having to go back. 

Thanks,
Tim

---

