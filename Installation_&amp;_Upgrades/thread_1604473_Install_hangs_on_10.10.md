---
title: "Install hangs on 10.10"
date: 2010-10-24
forum: Installation &amp; Upgrades
---

### Post by Rowan_ on 2010-10-24
please help. I have already installed Maverick on my own machine and on my mother in law's PC. However my mothers machine will not accept it.

First off I tried the liveCD to do a full install and everything went smoothly until the progress bar would freeze/hang at around 3/4 full.  If i clicked details the last line of text would read:

Update-initramfs: Generating /boot/initrd.img-2.6.35.22-generic.

I tried this method several times - once disconnecting the LAN connection.  
 
I then decided to try a full install using the alternate installer which uses a text based setup... and lo and behold it worked... kind of.  The computer did boot into the fresh install, but when I tried to do an update with Update Manager it hung.  Once again the last line of text read as above.

Then I did a reboot and then ran update manager again and even tried #sudo apt-get install f-.  Each time the same result.

So now I figured that i would reinstall and not update to the newer kernal as that seemed to be the issue.  Problem is that when i tried to reinstall Ubuntu, a single line of text appears that reads:

create-_floppy_devices(227): Specified group 'floppy' unknown

A simular line appears with whatever option I choose:  install, repair system, or check disk.  The only option that works is the memory test.

In the morning I will try to reinstall Winblows, but thought I might try asking for help from the community before leaving my mother stranded with windows.

---

### Post by mörgæs on 2010-10-24
Please describe the hardware on which you are installing.

Can you run a live 10.04 session on the machine?

---

### Post by Rowan_ on 2010-10-24
> **mörgæs said:**
> Please describe the hardware on which you are installing.

Can you run a live 10.04 session on the machine?


Okay, I can run a live 10.10 session on the machine.  If I try to do a Hardware Test it hangs.  

Im wondering if my hard drive is dead after reformatting a half dozen times; could that be my cause?

Biostar P4TPT 
Intel Pentium 4 2.60 GHz 
748.8 MiB RAM
GEForce2 mx 400 64bit 64MB SDR
Maxtor Diamond Plus 80GB ATA/133 HDD
and a Lan card.

The System Monitor shows Processor 0 and Processor 1 with the same device listed afterwards.  I was under the impression that this is a single core machine not a dual core, but this seems to indicate otherwise.

---

### Post by Rowan_ on 2010-10-24
Now I have reinstalled window and tried to use the Ubuntu alternative install disk again.
This is what comes up after I select 'Install':


[CODE]create_floppy_devices[226]: specified group 'floppy' unknown


udevadm settle - timeout of 180 seconds reached, the event queue contains:
/sys/devices/pci0000:00/0000:00:1d.1/usb3/3-1/3-1:1.0 (990)
[  180.972283] Kernal panic -not syncing: Attemped to kill init!
[  180.972519] Pid: 1, comm: init Not tainted 2.6.35-22-generic #33-Ubuntu

---

### Post by mörgæs on 2010-10-24
There are many reports of problems with this graphics card under 10.10. I would try a clean install of 10.04 as a first step. 

Reformatting does not give any particular wear on the hard drive.

---

### Post by Rowan_ on 2010-10-24
> **mörgæs said:**
> There are many reports of problems with this graphics card under 10.10. I would try a clean install of 10.04 as a first step. 

Reformatting does not give any particular wear on the hard drive.


Alright then, thanks; I'll give it a shot.

---

### Post by mörgæs on 2010-10-24
By the way, if you want to find out about the one-or-two processor question, please post the output from 

```
hwinfo --cpu
```

when Ubuntu is installed.

---

### Post by Rowan_ on 2011-02-01
Solved by using livecd and gparted and reformatting hard drive; then cycling power; reboot livecd; and install.

---

