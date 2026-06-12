---
title: "Unable to update or upgrade"
date: 2010-12-24
forum: Installation &amp; Upgrades
---

### Post by Ninjin25 on 2010-12-24
Hello,

Trying to upgrade my Ubuntu server to 10.10, however it is giving me grief.

I first tried 

Sudo apt-get upgrade, but I get the output

E: Could not open lock file /var/lib/dpkg/lock - open (1: Operation not permitted)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?

So then I did sudo su and tried again still getting the same error.

Any ideas would be much appreciated.

FYI sudo apt-get update gives me the same error.

Thanks in advance

---

### Post by Rubi1200 on 2010-12-24
Hi and welcome to the forums :)

Did you by chance have more than one package manager open at the time?

This type of error is often seen if you are running, for example, apt-get and also have aptitude open etc.

Try closing all instances and then start again.

---

### Post by Ninjin25 on 2010-12-24
Thanks for the quick reply.

I apologize, I'm not 100% to sure on how to check on instances that are running(Still learning). 

Correct me if I'm wrong, but I can check for running instances by using ps -e?

If so I'm not seeing any other package manager that I recognize. Here is a copy of the output if it helps
> 
  PID TTY          TIME CMD
    1 ?        00:00:00 init
    2 ?        00:00:00 kthreadd
    3 ?        00:00:00 migration/0
    4 ?        00:00:00 ksoftirqd/0
    5 ?        00:00:00 watchdog/0
    6 ?        00:00:00 events/0
    7 ?        00:00:00 cpuset
    8 ?        00:00:00 khelper
    9 ?        00:00:00 netns
   10 ?        00:00:00 async/mgr
   11 ?        00:00:00 pm
   12 ?        00:00:00 sync_supers
   13 ?        00:00:00 bdi-default
   14 ?        00:00:00 kintegrityd/0
   15 ?        00:00:00 kblockd/0
   16 ?        00:00:00 kacpid
   17 ?        00:00:00 kacpi_notify
   18 ?        00:00:00 kacpi_hotplug
   19 ?        00:00:00 ata/0
   20 ?        00:00:00 ata_aux
   21 ?        00:00:00 ksuspend_usbd
   22 ?        00:00:00 khubd
   23 ?        00:00:00 kseriod
   24 ?        00:00:00 kmmcd
   27 ?        00:00:00 khungtaskd
   28 ?        00:00:00 kswapd0
   29 ?        00:00:00 ksmd
   30 ?        00:00:00 aio/0
   31 ?        00:00:00 ecryptfs-kthrea
   32 ?        00:00:00 crypto/0
   36 ?        00:00:00 kstriped
   37 ?        00:00:00 kmpathd/0
   38 ?        00:00:00 kmpath_handlerd
   39 ?        00:00:00 ksnapd
   40 ?        00:00:00 kondemand/0
   41 ?        00:00:00 kconservative/0
  175 ?        00:00:00 scsi_eh_0
  176 ?        00:00:00 scsi_eh_1
  179 ?        00:00:00 scsi_eh_2
  180 ?        00:00:00 usb-storage
  221 ?        00:00:00 jbd2/sda1-8
  222 ?        00:00:00 ext4-dio-unwrit
  267 ?        00:00:00 upstart-udev-br
  269 ?        00:00:00 udevd
  400 ?        00:00:00 udevd
  401 ?        00:00:00 udevd
  421 ?        00:00:00 kgameportd
  556 ?        00:00:00 portmap
  579 ?        00:00:00 rpciod/0
  669 ?        00:00:00 jbd2/sda6-8
  670 ?        00:00:00 ext4-dio-unwrit
  675 ?        00:00:00 jbd2/sda5-8
  676 ?        00:00:00 ext4-dio-unwrit
  709 ?        00:00:00 rsyslogd
  719 ?        00:00:00 nfsiod
  721 ?        00:00:00 sshd
  730 ?        00:00:00 rpc.idmapd
  761 tty4     00:00:00 getty
  765 tty5     00:00:00 getty
  777 tty2     00:00:00 getty
  779 tty3     00:00:00 getty
  783 tty6     00:00:00 getty
  787 ?        00:00:00 cron
  788 ?        00:00:00 atd
  824 ?        00:00:00 mdadm
  859 tty1     00:00:00 getty
  860 ?        00:00:00 sshd
  928 ?        00:00:00 sshd
  929 pts/0    00:00:00 bash
 1013 ?        00:00:00 flush-8:0
 1016 pts/0    00:00:00 ps

---

### Post by Rubi1200 on 2010-12-24
What does the output of ```
cat /etc/*release
``` show?

Also post if there are errors with this command:
```
sudo dpkg --configure -a
```

---

### Post by Ninjin25 on 2010-12-24
Doing cat /etc/*release gave me the following

> 
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=10.04
DISTRIB_CODENAME=lucid
DISTRIB_DESCRIPTION="Ubuntu 10.04.1 LTS" sudo dpkg --configure -a error

> 
dpkg: you do not have permission to lock the dpkg status database

 xc
EDIT: I should mention that several weeks ago I was messing with the chattr command. From what I was reading generally speaking chattr +a is a favorable attribute for /var, so I did this. However, since then I have done chattr -a and -i (just in case I did use the chattr +i) to remove those attribute from that directory

---

### Post by Rubi1200 on 2010-12-24
I know this sounds silly, but did you use the command exactly as you originally posted?
> Sudo apt-get upgrade

If so, you need to use lowercase = sudo not Sudo.

I am looking for solutions, but haven't found anything yet.

---

### Post by Ninjin25 on 2010-12-24
Sorry, the capital "S" on my initial inquiry was by habit.

Exact syntax is

sudo apt-get upgrade


I'm not sure if you got to review my edit on my last post prior to posting so I will quote it 

> EDIT: I should mention that several weeks ago I was messing with the chattr command. From what I was reading generally speaking chattr +a is a favorable attribute for /var, so I did this. However, since then I have done chattr -a and -i (just in case I did use the chattr +i) to remove those attribute from that directory

---

### Post by Rubi1200 on 2010-12-24
I think you may need to check the status of your permissions:
[http://manpages.ubuntu.com/manpages/lucid/en/man1/chattr.1.html](http://manpages.ubuntu.com/manpages/lucid/en/man1/chattr.1.html)

---

### Post by Ninjin25 on 2010-12-24
Well I  cross checked my permissions and attributes with a working Ubuntu box , and everything appears to be correct. However, I'm not 100% positive on what I should be looking for or what commands need to be ran.

Ultimately I'm just going to reinstall, this is just a play/learning system with anything important backed up. Thanks again for all your help. If you can think of something within the next 48 hours(I won't be reinstalling for another day or more) I'm more than willing to look into it.

---

### Post by Ninjin25 on 2010-12-26
Well, since reinstalling isn't currently an option I'm going to continue working on this and got it working.

What I found was that the /var directory did have the append attribute, which I already suspected from the very beginning. Any time I would try to remove the attribute with>  sudo chattr -a /var, then do lsattr on that directory the append attribute would still be present. Today it came to me while taking a nap at work, I realized a serious problem in what I was trying to do! I was trying remove this attribute from the parent directory.Stupid me trying to apply an attribute to a parent directory with out using the -V option. 

After running > sudo chattr -V -a /var I was able to successfully upgrade my system.

Thank you very much for all your assistance with this matter, all that''s left is trying to get my local hostname back.

You may close this thread :D

---

