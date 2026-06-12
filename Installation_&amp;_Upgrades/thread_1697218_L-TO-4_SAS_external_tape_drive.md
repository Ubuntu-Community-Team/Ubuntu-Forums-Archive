---
title: "L-TO-4 SAS external tape drive"
date: 2011-02-28
forum: Installation &amp; Upgrades
---

### Post by cormu7 on 2011-02-28
Hello,

I am running Ubuntu 10.04, and i recently purchased an tandberg LTO-4 SAS tape drive. I want to access it and backup data on it.

Do I simply just connect plug it into the server,and I should be able to backup/transfer data to the tape drive? Or are there intermediate steps before I can do that.

Here are some results from commands that I have typed:

> ls /dev/tape/
by-id
 


> ls -lt /dev/tape/by-id/
total 0
lrwxrwxrwx 1 root root  9 2011-02-25 14:54 scsi-3500110a00145553e -> ../../st0
lrwxrwxrwx 1 root root 10 2011-02-25 14:54 scsi-3500110a00145553e-nst -> ../../nst0



> lsmod
Module                  Size  Used by
binfmt_misc             7960  1 
ppdev                   6375  0 
osst                   55350  0 
st                     39570  0 
ipt_MASQUERADE          1863  0 
iptable_nat             5219  0 
nf_nat                 19501  2 ipt_MASQUERADE,iptable_nat
nf_conntrack_ipv4      12980  3 iptable_nat,nf_nat
nf_defrag_ipv4          1481  1 nf_conntrack_ipv4
xt_state                1490  0 
nf_conntrack           73966  5 ipt_MASQUERADE,iptable_nat,nf_nat,nf_conntrack_ipv4,xt_state
ipt_REJECT              2384  0 
xt_tcpudp               2667  0 
iptable_filter          2791  0 
ip_tables              18358  2 iptable_nat,iptable_filter
x_tables               22461  6 ipt_MASQUERADE,iptable_nat,xt_state,ipt_REJECT,xt_tcpudp,ip_tables
bridge                 53216  0 
stp                     2171  1 bridge
fbcon                  39270  71 
tileblit                2487  1 fbcon
font                    8053  1 fbcon
bitblit                 5811  1 fbcon
softcursor              1565  1 bitblit
vga16fb                12757  1 
bnx2                   72874  0 
psmouse                64576  0 
serio_raw               4950  0 
vgastate                9857  1 vga16fb
dell_wmi                2177  0 
lp                      9336  0 
parport                37160  2 ppdev,lp
power_meter             9473  0 
joydev                 11008  0 
dcdbas                  6886  0 
usbhid                 41116  0 
hid                    83504  1 usbhid
ses                     6683  0 
enclosure               8649  1 ses
mpt2sas               115081  0 
scsi_transport_sas     33021  1 mpt2sas
megaraid_sas           38618  8 




Any thoughts?

cor

---

### Post by Hedgehog1 on 2011-02-28
I went to their website.

I found this page:

[http://www.tandbergdata.com/us/index.cfm/products/tape-drives/lto-drives/lto-4-hh/]("http://www.tandbergdata.com/us/index.cfm/products/tape-drives/lto-drives/lto-4-hh/")

If you click on 'downloads', you will see that there is a TDTool download for Linux (and others for Windows and OSX).  

Next to each download is another link for a document describing it usage.

:KS

---

### Post by cormu7 on 2011-03-01
Hedge,

thanks for the response. yes, i've downloaded from the website and ran the tool kit. 

now, i'm new at this when it comes to external tape drives and linux. so i guess my question isn't about tandberg devices specifically, but more along the lines of external tape drive usage and backup in general.

i just want to backup files on the tape drive.

i'm confused as to what actual folder i should move the files to for backup.

should it be "/dev/tape" or "/dev/st0", and what useful commands should i use to do this? do i use the "mv" and "cp" commands like i would for moving and placing files in folders?

thanks,

cor

---

### Post by Hedgehog1 on 2011-03-01
Since all my tape backup experience is pre-Linux (giant reel-to-reel units like you see in the old movies, running non-UNIX OSes), I had to dig around a bit.

I have taken the key text from this Web page:

[http://www.cyberciti.biz/faq/linux-tape-backup-with-mt-and-tar-command-howto/]("http://www.cyberciti.biz/faq/linux-tape-backup-with-mt-and-tar-command-howto/")

And created the summarized post below.

***The Hedge***

:KS

---

### Post by Hedgehog1 on 2011-03-01
[I]I thought it might be worth capturing some of the key text from the above web site so it will show up in future searches:
[/I]
**[SIZE="3"]Operating Tape Drives from Linux[/SIZE]**

[SIZE="2"]**SCSI tape device names:**[/SIZE]

The st driver provides the interface to a variety of SCSI tape devices under Linux.

* First (auto rewind) SCSI tape device name: /dev/st0
* Second (auto rewind) SCSI tape device name: /dev/st1

* First the non-rewind SCSI tape devices: /dev/nst0
* Second the non-rewind SCSI tape devices: /dev/nst1

[SIZE="2"]**IDE tape device names:**[/SIZE]

The ht driver provides the interface to a variety of IDE tape devices under Linux.

* First (auto rewind) IDE tape device name: /dev/ht0
* Second (auto rewind) IDE tape device name: /dev/ht1

* First the non-rewind IDE tape devices: /dev/nht0
* Second the non-rewind IDE tape devices: /dev/nht

[SIZE="2"]**Examples** [/SIZE](Please replace ***/dev/st0*** with your tape drive name):

Rewind tape drive:
```
mt -f /dev/st0 rewind
```
Backup directory /www and /home with tar command (z – compressed):
```
tar -czf /dev/st0 /www /home
```
Find out what block you are at with mt command:
```
mt -f /dev/st0 tell
```
Display list of files on tape drive:
```
tar -tzf /dev/st0
```
Restore /www directory:
```
cd /
mt -f /dev/st0 rewind
tar -xzf /dev/st0 www
```
Unload the tape:
```
mt -f /dev/st0 offline
```
Display status information about the tape unit:
```
mt -f /dev/st0 status
```
Erase the tape:
```
mt -f /dev/st0 erase
```

**[SIZE="2"]The 'big' tar examples:[/SIZE]**

To backup to multiple tape use the following command (backup /home file system):
```
tar -clpMzvf /dev/st0 /home
```
To compare tape backup, enter:
```
tar -dlpMzvf /dev/st0 /home
```
To restore tape in case of data loss or hard disk failure:
```
tar -xlpMzvf /dev/st0 /home
```

[SIZE="2"]**tar** options are:
* **d**: find differences between archive and file system
* **x**: extract files from an archive
* **l**: list the contents of an archive (Lower case 'L'
* **p**: ignore umask when extracting files
* **M**: create/list/extract multi-volume archive (multiple tapes)
* **z**: Compress backup using gzip
* **v**: verbosely list files processed
* **f */dev/st0***: Tape device name (replace ***/dev/st0*** with your tape device name)[/SIZE]

---

