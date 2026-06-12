---
title: "IDE log errors after upgrade to feisty 7.04"
date: 2007-05-01
forum: Installation &amp; Upgrades
---

### Post by qstel on 2007-05-01
I recently did an ugrade from Dapper Drake to Feisty. I have a 64-bit Athlon system with one SATA disk, one SATA DVD-rw and one IDE DVD. After upgraded to feisty and changed my kernel from 2.6.17-10  to 2.6.20-15 I get the usual "new medium detected"  KDE deamon popup only I dont have a disk in the drive and the popup does not specify the device it deteted. Furthermore if I leave my pc unattendent the same daemon keeps comming up until I have about 30-40 popup windows requesting the same thing.

Upon examining my system log files I found out that every few minutes or so my drive produces the following error:

Syslog:
> 
May  1 11:32:47 Sparowhawk kernel: [126133.624000] ide: failed opcode was: unknown
May  1 11:32:47 Sparowhawk kernel: [126133.624000] hdb: drive not ready for command
May  1 11:32:47 Sparowhawk kernel: [126133.624000] hdb: status error: status=0x58 { DriveReady SeekComplete DataRequest }
May  1 11:32:47 Sparowhawk kernel: [126133.624000] ide: failed opcode was: unknown
May  1 11:32:47 Sparowhawk kernel: [126133.624000] hdb: drive not ready for command
May  1 11:32:47 Sparowhawk kernel: [126133.624000] hdb: status error: status=0x58 { DriveReady SeekComplete DataRequest }


kern.log:
>   
May  1 11:32:47 Sparowhawk kernel: [126133.624000] ide: failed opcode was: unknown
May  1 11:32:47 Sparowhawk kernel: [126133.624000] hdb: drive not ready for command
May  1 11:32:47 Sparowhawk kernel: [126133.624000] hdb: status error: status=0x58 { DriveReady SeekComplete DataRequest }


dmesg:
> 
[126149.676000] hdb: drive not ready for command
[126149.676000] hdb: status error: status=0x58 { DriveReady SeekComplete DataRequest }
[126149.676000] ide: failed opcode was: unknown


I also get this from time to time:
> 
May  1 11:37:27 Sparowhawk NetworkManager: <debug info>^I[1178008647.413028] nm_hal_device_removed (): Device removed (hal udi is '/org/freedesktop/Hal/devices/volume_part_1_size_0').


Any ideas?

---

### Post by 4tro on 2007-05-05
> **qstel said:**
> I recently did an ugrade from Dapper Drake to Feisty. I have a 64-bit Athlon system with one SATA disk, one SATA DVD-rw and one IDE DVD. After upgraded to feisty and changed my kernel from 2.6.17-10 to 2.6.20-15 I get the usual "new medium detected" KDE deamon popup only I dont have a disk in the drive and the popup does not specify the device it deteted. Furthermore if I leave my pc unattendent the same daemon keeps comming up until I have about 30-40 popup windows requesting the same thing.

Upon examining my system log files I found out that every few minutes or so my drive produces the following error:

Syslog:
 	Quote:
 	 	 		 			 				May  1 11:32:47 Sparowhawk kernel: [126133.624000] ide: failed opcode was: unknown
May  1 11:32:47 Sparowhawk kernel: [126133.624000] hdb: drive not ready for command
May  1 11:32:47 Sparowhawk kernel: [126133.624000] hdb: status error: status=0x58 { DriveReady SeekComplete DataRequest }
May  1 11:32:47 Sparowhawk kernel: [126133.624000] ide: failed opcode was: unknown
May  1 11:32:47 Sparowhawk kernel: [126133.624000] hdb: drive not ready for command
May  1 11:32:47 Sparowhawk kernel: [126133.624000] hdb: status error: status=0x58 { DriveReady SeekComplete DataRequest } 			 		 	 	 
kern.log:
 	Quote:
 	 	 		 			 				May  1 11:32:47 Sparowhawk kernel: [126133.624000] ide: failed opcode was: unknown
May  1 11:32:47 Sparowhawk kernel: [126133.624000] hdb: drive not ready for command
May  1 11:32:47 Sparowhawk kernel: [126133.624000] hdb: status error: status=0x58 { DriveReady SeekComplete DataRequest } 			 		 	 	 
dmesg:
 	Quote:
 	 	 		 			 				[126149.676000] hdb: drive not ready for command
[126149.676000] hdb: status error: status=0x58 { DriveReady SeekComplete DataRequest }
[126149.676000] ide: failed opcode was: unknown 			 		 	 	 
I also get this from time to time:
 	Quote:
 	 	 		 May 1 11:37:27 Sparowhawk NetworkManager: <debug info>^I[1178008647.413028] nm_hal_device_removed (): Device removed (hal udi is '/org/freedesktop/Hal/devices/volume_part_1_size_0').  	 	 
Any ideas?

I can confirm this behaviour, i have this in my system as well.
Similar bugs were in dapper and edgy and other distro's.

I have found several topics relating to this bug, but nowhere any developers or "experts" in the form of hal developers.
Workarounds are there, but they never solve this bug.

hope this helps

---

### Post by samjam on 2007-07-18
Here's my automatic fix.

Put this script in /usr/local/sbin:

```
#! /bin/bash
# /usr/local/sbin/fixhdc
# by Sam Liddicott http://www.liddicott.com/~sam/?p=79
# Monitor kernel messages to see if the cdrom is jiggered
# If so do an atapi reset
# First add this line to /etc/syslog.conf
# kern.* /var/log/kern.fifo
# Then run this script from /etc/rc.local with:
# setsid /usr/local/sbin/fixhdc &

KERNFIFO=/var/log/kern.fifo
CDROM=hdc

CDROM_NODE="/dev/$CDROM"

daemon() {
  while read logline
  do
    case "$logline" in
      *"$CDROM: status timeout: status=0xd0 { Busy }"*)
        hdparm -w "$CDROM_NODE"
        logger -t 'kern.crit' -- "$0 reset $CDROM"
      ;;
      *) echo "Ignore $logline";;
    esac
  done
}

while :
do
  if test -p "$KERNFIFO" || mkfifo "$KERNFIFO"
  then daemon < "$KERNFIFO" &
       # restart syslog now we have the pipe open
       /etc/init.d/sysklogd reload
       # it probably won't finish till syslog does
       wait
       logger -- "Restarting $0"
  else echo "Can't make fifo $KERNFIFO"
       exit 1
  fi
done

```

---

### Post by magabriel on 2007-07-28
I have an HP 6510b and can confirm that this works like a charm. 

Thank you, man!!!

---

### Post by labinnsw on 2008-05-15
What name should I give the code?

I am using Hardy Heron. Should I do anything different?

---

### Post by labinnsw on 2008-05-19
Looks like it works in Hardy but had to be placed in usr/bin as fixhdg. (hdg being my CDROM designation) I have monitored for 52 minutes so far and is continuing to monitor. If the problem persists, I will advise as soon as I become aware. So far, looks like this works for Hardy.

Thanks Samjam

---

### Post by labinnsw on 2008-05-20
Spoke too early. Absolutely nothing has changed. This thing is bugging the living daylights out of me. I am a bit of an obsessive compulsive and I am determined that Ubuntu is the OS I want to use. I am not trying to convince anyone else, but for reasons I don't have time to get into the details of, I think It is the single best operating system. Whatever happens, Ubuntu is my OS. Now, that said, I need to have this problem fixed urgently or I will find it very difficult to sit at my computer to do anything. Just knowing that my OS is logging a single error is enough to drive me up the wall. Please someone help me before I go completely buzzirk!

---

