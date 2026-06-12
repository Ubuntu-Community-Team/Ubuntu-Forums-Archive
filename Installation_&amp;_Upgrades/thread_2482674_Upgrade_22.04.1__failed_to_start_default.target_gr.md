---
title: "Upgrade 22.04.1  failed to start default.target graphical.target"
date: 2023-01-07
forum: Installation &amp; Upgrades
---

### Post by pspi098 on 2023-01-07
Hello, 

I have decided to upgrade from 21.XX LTS Ubuntu to 22.04.1LTS. After the installation, the laptop rebooted but it went straight into recovery mode and getting the following error: 
[B]1) When booting: 
[/B]    Integrity: Problem  loading X.509 certificate -65
    1st disk: /dev/nvme0n1p2: recovering journal 
                   /dev/nvme0n1p2: clean.....

    2nd disk: /dev/nvme1n1p2: unrecognized mount point default or missing. 

**2) Boot Log**: 
     **1)**Failed to mount /mnt/disk2
          systemctl status mnt-disk2.mount : 
             -error mount:  /mnt/disk2: wrong fs type, bad option , bad superblock on /dev/nvme1n1p2, missing code page  or helper program, or other
                      /lib/recovery-mode/recovery-menu" line80:etc/default/rcS: no such file or direcotory
                      systemd: mnt-disk2.mount: MOunt processexite, code=exited, status =32/n/a
                      systemd: mnt-disk2.mount: Failed  with result "exit-code".
                      systemd: Failed to mount /mnt/disk2
      **2)** Dependency failed for local file system

      **3) **after exit from recovery mode following error: 
             Failed to start default target. Transaction for graphical.target/start  is destructive (emergency target has 'start' job queued , but 'stop is included in transaction:

         
    I also attached pictures taken. 

   I came across googling of a solution which involves fsck /dev/nvme1n1p2  but it came back clean. 
   
My  theory is that during the update somehow it mounted the wrong file system,  but it does not make sense to me. 

Any idea what could be the issue and how this can be solved? 
If someone requires further info I am more than happy to provide.

Thank you for your help and assistance

---

### Post by MAFoElffen on 2023-01-07
First off 21.xx... Anything starting with 21.anything was not "LTS". LTS versions were 20.04 and 22.04. But that does not matter.

You can try to do fschk, but you need to start it externally, via a LiveCD USB to do it. If the drive is the root drive, it cannot do a fschk on any drive that is mounted. See the problem there? 

Before attempting a rescue... Booting off a LiveCD USB will also give you the ability to copy data and configurations off your drive before any changes are made yet. Because if this fails further, you may lose what is there. Understood? Now is the time to do something like that.

Next, when you get to the point where it says that it cannot start the graphical target, if you press the keys <Cntrl><Alt><F4> at the same time, does it take you to TTY4, where you can long in to a console prompt?

---

### Post by pspi098 on 2023-01-08
Thanks for your quick response. 
Cntrl+alt+f4 goes to black screen and a ticker on the upper left. It is blinking but does not accept any key input, just blinking. 
I will do as you suggested. 


Thank you again.

---

### Post by MAFoElffen on 2023-01-08
Did you try doing an fschk from a LiveCD USB? Were you able to rescue any data off your old installation?

EDIT: Honestly... If that doesn't work, I'm afraid to tell you that you are facing a migration to a fresh, new install. Please try to rescue any data that you can now by using a LiveCD USB.

Reason... You do not have a system booting the Kernel 'completely'. It's not just the Graphics Layer. I can recommend a few things to try, but the outlook isn't looking hopeful at the moment.

If there were more details, then I could see where it is failing... There might be... But I'm not seeing where it is failing.

I don't even think that running the 'system-info' script from a LiveCd is going to give a clear picture of what is going on.

Lease try to explain what is on /dev/nvme1n1p2??? You added that into your fstab right? What happens if you comment that line out in your /etc/fstab and try to boot it? (Then we could try to deal with that separately.)

---

### Post by pspi on 2023-01-10
GNE,  yes, I was able to rescue data with the live USB, copied everything what is needed. 
The /dev/nvme1n1p2 disk is my secondary disk. 
After a thorough back up, I thought to myself that I should try to comment out that disk from the fstab before I proceed with the fresh install as you recommended and to my dismay the system has booted up without issue. 
So now it is running smooth. 

Thank you very much for your time and effort.

---

### Post by MAFoElffen on 2023-01-10
Good that booting is fixed, now for the next steps...

While offline (not mounted), can you fschk that volume (partition) to see if it had a data error in the filesystem?

Can you mount that volume "manually"?

---

### Post by pspi on 2023-01-15
I run the fsck command and result came back as clean - disk was unmounted. 
After I mounted disk manually, then I rebooted, the issue returned. 

I wonder, if the issue is that it is booting for some reason from the secondary disk ?  

May be I should just create a backup from the disk and format it?

---

