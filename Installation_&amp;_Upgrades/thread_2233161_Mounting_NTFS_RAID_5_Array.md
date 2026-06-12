---
title: "Mounting NTFS RAID 5 Array"
date: 2014-07-06
forum: Installation &amp; Upgrades
---

### Post by fossilman on 2014-07-06
Hello all,

I am a former MS windows user and very recently switched to Ubuntu 14.04 LTS, my hard drive configuration consisted of a single 500Gb HDD and 4 1Tb drives in an Intel BIOS RAID 5 and formatted withing Windows 7 with NTFS.

I made a fresh new installation with a new hard drive (former main drive just went smoke) I had to define my new drive as the installation and carrier of Linux, since by default the RAID was chosen as first HDD, then the main HDD finished like this:

```
sde1 / 25Gb
sde5 /home 450Gb
sde6 /swap 25 Gb
```

Now, I have been trying to make Ubuntu to recognize my RAID drives without success, after reading a lot about it I tried

```
fossilman@pangea:~$ sudo dmraid -s
*** Group superset isw_fhhecaiej
--> Subset
name   : isw_fhhecaiej_Oerth
size   : 5860561920
stride : 128
type   : raid5_la
status : ok
subsets: 0
devs   : 4
spares : 0
```

After that I used:

```
fossilman@pangea:~$ sudo dmraid -r
/dev/sdd: isw, "isw_fhhecaiej", GROUP, ok, 1953525166 sectors, data@ 0
/dev/sdc: isw, "isw_fhhecaiej", GROUP, ok, 1953525166 sectors, data@ 0
/dev/sdb: isw, "isw_fhhecaiej", GROUP, ok, 1953525166 sectors, data@ 0
/dev/sda: isw, "isw_fhhecaiej", GROUP, ok, 1953525166 sectors, data@ 0
```

Apparently everything was alright, then I used:

EDIT:
I gave up and then made a new installation again, this time I am using Kubuntu 14.04 LTS, the previous commands were the same, now when using the following command it says the RAID is already installed:

```
fossilman@pangea:~$ sudo dmraid -ay
[sudo] password for fossilman: 
ERROR: isw: seeking device "/dev/dm-1" to 18446744073709517312
RAID set "isw_fhhecaiej_Oerth" already active
```

Then I tried the mounting command:

```
fossilman@pangea:~$ sudo mount -t ntfs-3g -o /dev/sda /mnt/raid
```

And It keeps displaying the mount help. Please, let me know what I must do to finish this task. AND please, assume that I am a complete idiot with your answers, I really need the step by step Linux for Dummies approach.

---

