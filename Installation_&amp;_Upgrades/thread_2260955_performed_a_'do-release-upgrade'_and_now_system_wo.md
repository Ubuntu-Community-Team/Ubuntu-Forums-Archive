---
title: "performed a 'do-release-upgrade' and now system won't boot after."
date: 2015-01-15
forum: Installation &amp; Upgrades
---

### Post by Paul_Adair on 2015-01-15
I performed a do-release-upgrade this morning now my system won't boot.  It was on  12.04 before this upgrade and it was a system that was working fine for about a year.  Whenever I would login to the system it told me to do the do-release-upgrade so I tried it.  It seemed to upgrade without any problems.  Only cautions I received were my proftpd.conf file was changed and my /etc/services were changed. I compared, just minor customizations so I continued.  At the end it said it need to reboot so I let it.  Now this is what I see...(attached).  The system is virtual running on ESXi 5.5.

The error seems to be around the "/dev/mapper/web3--vg-root" file.  My systems name is "web3".

Any help appreciated. This is a production web host system that is currently down.

[ATTACH=CONFIG]259255[/ATTACH]

---

### Post by oldos2er on 2015-01-15
Were you running 13.04 or 13.10?

---

### Post by Paul_Adair on 2015-01-15
On closer inspection it may of been 12.04.  Just looked at the ISO directory I build VM's from on my datastore and it has a file called "ubuntu-12.04.4-server-amd64.iso" so I assume I built it from that.  Would of been around a year ago.

---

### Post by Paul_Adair on 2015-01-15
The system was originally setup with the disk using LVM.  I'm sure this is an easy fix, I'm just not an expert on how to do grub/lvm patch work etc.  Anyone???

---

### Post by MAFoElffen on 2015-01-15
Got your PM... Happy to help.

First- Describe how you have things set up... In your words...
And-- If you have backup? If not do you need to get a backup before making changes? (Production or Personal?)

I see only one drive (sda) with 3 partitions (sda1, sda2 & sda5). I see mapper and a layout that implies LVM2, right? You didn't mention, so assuming no raid? Tell me if there was a physical drive that didn't show there. (for instance, if one dropped out)

So-- Boot from a LiveCD and post the results of:
```

sudo blkid
sudo fdisk -l /dev/sda
sudo pvdisplay -v
sudo pvscan -v
sudo vgs -a -v -o vg_all

```
I'm assuming Volume sd1 is most like the vg_boot? But the above will show that. Assuming MBR. If a GPT disk, instead of using fdisk, use gdisk
```

sudo apt-get install gdisk
sudo gdisk -l sda[1-5]

```
After you send the results back, we can see how it's laid out, the particulars of mounting those volumes to access the last syslog...

You mentioned it was server edition in transition from 12.04LTS to 14.04LTS?

---

### Post by Paul_Adair on 2015-01-15
[ATTACH=CONFIG]259283[/ATTACH]

attached is output from those commands. I booted from the install cd and went rescue mode. is that the same as livecd?  the sudo didn't work or the apt-get with the other commands.  the pic does show the output of the others though.

---

### Post by Paul_Adair on 2015-01-15
sorry.. your other questions.. the setup.. it is a VM on an ESXi host. Quite simple, 2 cpu, 2gb ram 40gb disk originally. I expanded it in esxi client to 100gb but never got it to expland in Linux.
I do have a backup, with unitrends enterprise free version.  I didn't know I had to do a bare metal cd create first to restore. :(  I was able to create a new vm and can restore things like my /var/www and /etc/apache2/sites-available and /var/lib/mysql/<databases> but the new vm I created with the latest 14.04 cd and I suspect the mysql and other app versions are different because while the data was there the webs or databases were not working. i'm sure I could get them working like that from restore but will be a huge lengthly timely process. I'd like to see if I can fix this boot issue first...

---

### Post by Paul_Adair on 2015-01-15
as for the raid question.... the raid is at the ESXi host level.

---

### Post by MAFoElffen on 2015-01-15
I don't do rescue mode of an an install cd as that may have made changes when it tries to access a filesystem. I usually want to do a standlaone LiveCD image boot so it is "looking" at a file system from the outside, without making changes... The diagnose what you need to do, before you make any changes.

By using a LiveCD, then you can diagnose, mount, then try to chroot into your installed system... using what it was configured as. (not what it tries to guess on). I'm hoping it did make any changes already... Is so...

I'm saying that, because not I do not see sda2, /dev/mapper/, the PV web3 or the VG vg-root. I am hoping it doesn't see that, just because it tried to boot it and... because it still had problems, tried to start with the vg-root (dropped.

Try that all again with a LiveCD

---

### Post by Paul_Adair on 2015-01-15
quickest way to get a livecd?

---

### Post by MAFoElffen on 2015-01-15
Download and setup a LiveUSD... Burn a LiveCD... I keep many spares around that go out with on calls. So, we know if it is still 12.04 or did it make it far enough to think it's 14.04? Cause you want to boot it from a similar version...

---

### Post by Paul_Adair on 2015-01-15
ive googled 'Ubuntu livecd download' and it all points to the same downloads I already have?!?!? where can I get a 14.04 livecd iso?

---

### Post by MAFoElffen on 2015-01-15
Here is the release page:
[http://releases.ubuntu.com/14.04.1/](http://releases.ubuntu.com/14.04.1/)

---

### Post by MAFoElffen on 2015-01-15
Once you get terminal open, from the prompt, retype those commands again... 

Start up Firefox from the same place. Will be an Icon at the left on that app panel. Go to this thread...

Copy paste the output of them within [code] tags (advance Post menu > '#" icon at top... That will keep the output of that organized and take less room when posted.

---

### Post by MAFoElffen on 2015-01-15
Since I now know this is a VM... Create another Virutal disk and add it to that virtual machine... we can always use that as needed for a backup or a pvmove, if needed... make it bigger than you original... We can always delete that later if we don't need it.

---

### Post by Paul_Adair on 2015-01-15
ok.. this is from the firefox on the live cd.  here is the output you ask for.

ubuntu@ubuntu:~$ sudo blkid
/dev/loop0: TYPE="squashfs" 
/dev/sr0: LABEL="Ubuntu 14.04.1 LTS amd64" TYPE="iso9660" 
/dev/sda1: UUID="ac990ff2-1435-4e53-91c8-481959f11694" TYPE="ext2" 
ubuntu@ubuntu:~$ sudo fdisk -l /dev/sda

Disk /dev/sda: 107.4 GB, 107374182400 bytes
255 heads, 63 sectors/track, 13054 cylinders, total 209715200 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000c60bb

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048      499711      248832   83  Linux
/dev/sda2          501758    83884031    41691137    5  Extended
/dev/sda5          501821    83884031    41691105+  8e  Linux LVM
ubuntu@ubuntu:~$ pvdisplay -v
  /dev/mapper/control: open failed: Permission denied
  Failure to communicate with kernel device-mapper driver.
  WARNING: Running as a non-root user. Functionality may be unavailable.
    Scanning for physical volume names


ubuntu@ubuntu:/dev$ sudo pvdisplay -v
    Scanning for physical volume names
ubuntu@ubuntu:/dev$ sudo pvscan -v
    Wiping cache of LVM-capable devices
    Wiping internal VG cache
    Walking through all physical volumes
  No matching physical volumes found
ubuntu@ubuntu:/dev$ vgs -a -v -o vg_all
  /dev/mapper/control: open failed: Permission denied
  Failure to communicate with kernel device-mapper driver.
  WARNING: Running as a non-root user. Functionality may be unavailable.
    Finding all volume groups
  No volume groups found
ubuntu@ubuntu:/dev$ sudo gdisk -l sda[1-5]
GPT fdisk (gdisk) version 0.8.8

Usage: gdisk [-l] device_file

---

### Post by MAFoElffen on 2015-01-15
That is not looking that good.

sda1 is your boot.
sda5 is your root.

So if your PV Name is web3, and did a default install when you installed, then the defualt vg names would be "vg-root" and "vg-boot".

So lets try to mount it anyways, just for a test
```

sudo mkdir /mnt/root
sudo mount /dev/mapper/web3--vg-root /mnt/root

```
That will be the tell on that... That will tell us if the "recover" made changes on it.

You porbably should have taken a snapshot of the vm before you did the do-release-upgrade... then you could have rolled back... (I know. That afterthought too late now).

---

### Post by Paul_Adair on 2015-01-15
ubuntu@ubuntu:~$ sudo mkdir /mnt/root
ubuntu@ubuntu:~$ sudo mount /dev/mapper/web3--vg-root /mnt/root
mount: special device /dev/mapper/web3--vg-root does not exist
ubuntu@ubuntu:~$ 

???

---

### Post by MAFoElffen on 2015-01-15
The last mention of /dev/mapper/web3--vg-root is in your screen shot in Post #1. I thinking if now, you jsust try to use the file manager in the LiveCD and mounted sda5, you could see if anytrhing is there.

I don't think there is hope. it is looking for /dev/mapper/web3--vg-root because that is what it said it was in the fstab...

Wait, one last try-- a reach, but worth a try... Remove the iso from the virt CD... Boot and catch the Grub boot menu. Use the other kernels menu and boot from an earlier kernel... The intramfs inmage might work, because it had what is was before the upgrade...

Try that... (Crossing fingers for you!)

But since it is not seeing any pv's or vg's, I'm thinking they are now corrupted somehow... (How do you corrupt an LVM of 1 PV and no extents?)

EDIT-- I'm starting one of my consoles to start one of my KVM VM's to show you what that output should have brought back and showed...

---

### Post by Paul_Adair on 2015-01-15
I think I am going to give up on this.  Not that I don't want the system back, but in the background I have been trying other things.
I built a new Ubuntu 12.04 (pretty sure this is what I had before) and set it up as a simple LAMP/email system.  At the completion of that I installed the unitrends Linux agent and set it up in my backup software.
From my file level backups of my broken system I went thru the tree and selected to restore just key stuff I knew that was custom.  I did /etc/network, /etc/apache2, /etc/postfix, /etc/proftpd and all of /var (which would include /var/www and /var/lib/mysql).
Once that was done I rebooted the system and it came up using all the proper IP's that the broken system used.  99% of the websites work including ones that go to mysql databases.  I have several WordPress sites as well as SugerCRM.  They all work fine now.  Only thing I can't get to come back (so far...) is my own Observium system.  The mysql database looks ok, just must be something in the Observium/html config that may require custom permissions or something.

Long story short, I think I am going to be ok.  Only major item that is stumping me now is I can't get sshd to run.  I tried apt-get remove openssh-server and then apt-get install openssh-server with no luck.  

Any ideas on how to repair the sshd?

---

### Post by MAFoElffen on 2015-01-15
This is for example of what it might have returned if something was there:
```

Welcome to Ubuntu Vivid Vervet (development branch) (GNU/Linux 3.16.0-28-generic x86_64)

 * Documentation:  [https://help.ubuntu.com/](https://help.ubuntu.com/)

  System information as of Thu Jan 15 19:50:59 PST 2015

  System load:  0.01              Processes:           91
  Usage of /:   38.8% of 6.50GB   Users logged in:     1
  Memory usage: 9%                IP address for eth0: 192.168.2.14
  Swap usage:   0%

  Graph this data and manage this system at:
    [https://landscape.canonical.com/](https://landscape.canonical.com/)

Last login: Thu Jan 15 19:47:04 2015
root@vivid01:/home/mafoelffen# blkid
/dev/vda1: UUID="ccad8250-017b-4ed1-92bf-6320724ea420" TYPE="ext2" PARTUUID="000061eb-01"
/dev/vda5: UUID="hAVSpz-nfPK-waOd-MfmR-idKn-ifjQ-EXuk7V" TYPE="LVM2_member" PARTUUID="000061eb-05"
/dev/mapper/Template14--vg-root: UUID="06a4f478-27c4-4b78-bac9-15c99fc9b6f5" TYPE="ext4"
/dev/mapper/Template14--vg-swap_1: UUID="a37625a8-3a4b-4914-a92d-1d28c65e0982" TYPE="swap"
root@vivid01:/home/mafoelffen# fdisk -l

Disk /dev/vda: 8 GiB, 8590045184 bytes, 16777432 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0x000061eb

Device     Boot  Start      End  Sectors  Size Id Type
/dev/vda1  *      2048   499711   497664  243M 83 Linux
/dev/vda2       501758 16775167 16273410  7.8G  5 Extended
/dev/vda5       501760 16775167 16273408  7.8G 8e Linux LVM

Disk /dev/mapper/Template14--vg-root: 6.7 GiB, 7226785792 bytes, 14114816 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk /dev/mapper/Template14--vg-swap_1: 1020 MiB, 1069547520 bytes, 2088960 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
root@vivid01:/home/mafoelffen# fdisk -l

Disk /dev/vda: 8 GiB, 8590045184 bytes, 16777432 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0x000061eb

Device     Boot  Start      End  Sectors  Size Id Type
/dev/vda1  *      2048   499711   497664  243M 83 Linux
/dev/vda2       501758 16775167 16273410  7.8G  5 Extended
/dev/vda5       501760 16775167 16273408  7.8G 8e Linux LVM

Disk /dev/mapper/Template14--vg-root: 6.7 GiB, 7226785792 bytes, 14114816 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk /dev/mapper/Template14--vg-swap_1: 1020 MiB, 1069547520 bytes, 2088960 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
root@vivid01:/home/mafoelffen# pvdisplay -v
    DEGRADED MODE. Incomplete RAID LVs will be processed.
    Scanning for physical volume names
  --- Physical volume ---
  PV Name               /dev/vda5
  VG Name               Template14-vg
  PV Size               7.76 GiB / not usable 2.00 MiB
  Allocatable           yes 
  PE Size               4.00 MiB
  Total PE              1986
  Free PE               8
  Allocated PE          1978
  PV UUID               hAVSpz-nfPK-waOd-MfmR-idKn-ifjQ-EXuk7V
   
root@vivid01:/home/mafoelffen# pvscan -v
    DEGRADED MODE. Incomplete RAID LVs will be processed.
    Wiping cache of LVM-capable devices
    Wiping internal VG cache
    Walking through all physical volumes
  PV /dev/vda5   VG Template14-vg   lvm2 [7.76 GiB / 32.00 MiB free]
  Total: 1 [7.76 GiB] / in use: 1 [7.76 GiB] / in no VG: 0 [0   ]
root@vivid01:/home/mafoelffen# vgs -a -v -o vg_all
    DEGRADED MODE. Incomplete RAID LVs will be processed.
    Finding all volume groups
    Finding volume group "Template14-vg"
  Fmt  VG UUID                                VG            Attr   VPerms     Extendable Exported   Partial    AllocPol   Clustered  VSize VFree  SYS ID Ext   #Ext Free MaxLV MaxPV #PV #LV #SN Seq VG Tags VProfile #VMda #VMdaUse VMdaFree  VMdaSize  #VMdaCps 
  lvm2 hRFEU3-IFtI-Vhva-3CMc-gKDC-Jpa7-t0F5Az Template14-vg wz--n- writeable  extendable                       normal                7.76g 32.00m        4.00m 1986    8     0     0   1   2   0   3                      1        1   508.00k  1020.00k unmanaged

```
So you are right... on yours, it's gone. If it can't see the outside container, no chance of seeing inside something that doesn't exit.

---

### Post by Paul_Adair on 2015-01-15
ok, thanks for all your help. I've fixed the ssh issue now as well.
so other than my own Observium snmp monitoring website.. everything seems to have come back.
what is funning though, is even though is I am being nagged again at boot to "do-release-upgrade". lol. 
I am going to take a snapshot of the vm in VMware and THEN try that command again. lol.  If it don't work. roll back the snapshot.

cheers!

---

### Post by MAFoElffen on 2015-01-15
This is 15.04, which is the Server I'm testing at the moment, but should be the same apckage (different version of)
```

root@vivid01:/home/mafoelffen# dpkg -l | grep ssh
ii  openssh-client                      1:6.7p1-3                    amd64        secure shell (SSH) client, for secure access to remote machines
ii  openssh-server                      1:6.7p1-3                    amd64        secure shell (SSH) server, for secure access from remote machines
ii  openssh-sftp-server                 1:6.7p1-3                    amd64        secure shell (SSH) sftp server module, for SFTP access from remote machines
ii  ssh-import-id                       3.21-0ubuntu1                all          securely retrieve an SSH public key and install it locally

```
You did the right command. If you purged and reinstalled? I do that one from tasksel, the same menu as from the install disk (in the sys)
```

sido apt-get remove --purge  openssh-server
sudo tasksel

```

---

### Post by MAFoElffen on 2015-01-16
All mine are up on 14.04 LTS, except for my test servers, But...

There's a buzz going around saying this-- the 12.04 is LTS, but there was something going on with the kernel... so even if you stay, there was someting about running 12.04 w/ a 14.04 kernel... The message people were getting said something about the old kernel not going to be supported any longer. For something to come out like that, they must have found a vulnerability that they needed to step away from.

But a few days ago when that started hitting people boxes, some people were having challenges with that... People are still collecting info on what is the problems going on with that.

Yes, you are on the right track now. What i would do if it were me... snapshot and clone (2 chances to fall back on)... Then do a (complete) do-release-upgrade.

Honestly, I didn't have any troubles on mine and they do run better. I don't like to wait 5 years and try to upgrade releases at the last minute. Every two years is fine with me.

---

