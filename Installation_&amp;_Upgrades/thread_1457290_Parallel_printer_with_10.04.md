---
title: "Parallel printer with 10.04"
date: 2010-04-18
forum: Installation &amp; Upgrades
---

### Post by PaulHuffman on 2010-04-18
I like the way 10.04 lts is running on my old PC, except I can't seem to install my HP 895C.  This printer worked on previous releases on Ubuntu.  The printer is local and cabled to the PC's parallel port.  But "Add" under printing doesn't show any parallel printers under local printers. Only shows serial port, other, and network printers. Is this because 10.04 is beta? "Troubleshooting printers" doesn't have a list of printers, and wasn't much help.  Is the lpt1 in PC speak /dev/lp0 in Linux? Should that be the printer URI?

---

### Post by Sef on 2010-04-18
> Only shows serial port, other, and network printers. Is this because  10.04 is beta?

Could be.  One the 22 April, it goes into RC (release candidate) status, so if it is, it will most likely be working by then.  Also check launchpad for bug reports.

---

### Post by Detonate on 2010-04-18
One of the common causes is the permissions are set wrong on /dev/lp0.

Change the permissions to allow user to read and write.

---

### Post by PaulHuffman on 2010-04-24
Hey, WTF, there is no /dev/lp0!  Now what?

---

### Post by Detonate on 2010-04-25
Check to make sure it is enabled in your bios.

---

### Post by chui101 on 2010-04-25
> **PaulHuffman said:**
> Hey, WTF, there is no /dev/lp0!  Now what?

There is, you just have to have root permissions to view it.
In terminal, do 
```
sudo su -
```
(with the dash), then you should be able to see it.

What I did didn't work though - I did
```
sudo chmod o+rw /dev/lp0
```

But I am still unable to access lp0 to print; I am running into the same issue with setting up my oldie but goodie HP LaserJet 5L. 

Is there a reason why udev permissions were changed? This really should be fixed in the default configuration,

---

### Post by PaulHuffman on 2010-04-25
sudo ls doesn't see any lp*. 

[FONT="Fixedsys"]paul@paul-desktop:/dev$ sudo ls -lt l*
brw-rw---- 1 root disk 7, 6 2010-04-24 22:57 loop6
brw-rw---- 1 root disk 7, 3 2010-04-24 22:57 loop3
brw-rw---- 1 root disk 7, 2 2010-04-24 22:57 loop2
brw-rw---- 1 root disk 7, 7 2010-04-24 22:57 loop7
brw-rw---- 1 root disk 7, 5 2010-04-24 22:57 loop5
brw-rw---- 1 root disk 7, 1 2010-04-24 22:57 loop1
brw-rw---- 1 root disk 7, 4 2010-04-24 22:57 loop4
brw-rw---- 1 root disk 7, 0 2010-04-24 22:57 loop0
srw-rw-rw- 1 root root    0 2010-04-24 22:57 log[/FONT]

I also updated 10.04 with all available packages last night.

I also booted with a couple other iso CDs last night.  

9.04 and 9.10 Add Printer didn't show any Parallel Printers. Also, there were no lp* s in /dev

8.04 Add Printer showed Parallel Printers as LPT1.  Detected my printer, found a driver, and printed a test page.

Did Ubuntu drop parallel printer support starting with 9.*?

---

### Post by Detonate on 2010-04-25
Run lsmod and see if "parport" is running.

---

### Post by avtolle on 2010-04-25
Wondering, but don't know, if the two posting with problems (as they have HP printers) could not set up the printers using hplip, assuming parport is running.

---

### Post by quadproc on 2010-04-25
> **PaulHuffman said:**
> sudo ls doesn't see any lp*. 
...
Did Ubuntu drop parallel printer support starting with 9.*?
I vaguely recall having seen an old posting relating to a problem where the parallel printer had been omitted from some development version of Ubuntu.  Perhaps this omission has occurred again?

Some of us, myself included, still use parallel printers.

quadproc

---

### Post by PaulHuffman on 2010-04-25
It looks like parport is running:

parport                32635  2 ppdev,lp

---

### Post by PaulHuffman on 2010-04-26
Back at my home office, I have a newer PC running 9.10 (10.04 now, since 5/14).  Add Printer shows lpt #1 and all the serial ports.  /dev/lp0 is present.

Is the bios on my old PC too old so Ubuntu > 8.04 can't detect parallel ports properly? I see a warning about the bios too old scroll by at startup.

---

### Post by chui101 on 2010-04-28
I too, have parport running. 
```
chui@matrix:~$ lsmod|grep parport
parport_pc             25962  1 
parport                32635  3 ppdev,parport_pc,lp
```I was able to add it just fine under 9.10, so for me it's something that has changed since that release. I don't have 9.10 installed anymore as I did a clean install of 10.04 RC.

I'm running it on a Thinkpad T42. It's the only computer I have around that still has a parallel port, unfortunately. I do see it when i sudo, though :
```
chui@matrix:~$ sudo ls -l /dev/lp*
crw-rw---- 1 root lp 6, 0 2010-04-26 01:01 /dev/lp0
```

---

### Post by Detonate on 2010-04-28
If parport and parport_pc are running, I can't be of any more help because I don't have a clue why you don't see /dev/lp0.  I just upgraded my computer to a new motherboard and I now no longer have a parallel port, and this is the only machine I have that is running 10.04 so I can't experiment and see if I can figure it out.  I hope someone more knowledgeable jumps in.

---

### Post by PaulHuffman on 2010-04-28
At my home office, I tried booting my newer PC on a 10.04 iso CD just now, and lp0 was there. Didn't need to sudo to list it.  And Printers>New showed LPT #1.

Must be that my old PC is just too old to run unbuntu > 8.04. I got it back in late 99 right after my house fire. I tried to install XP on it and it ran too slow for XP. Ubuntu gave it new life and extended its usefulness. I can easily roll back to 8.04 on that old girl and be able to print again. What added features will I miss between 8.04 and 10.04?

Is there a linux way to get a report on what bios this old girl is running? biosdecode?

---

### Post by nss0000 on 2010-04-28
> **PaulHuffman said:**
> I like the way 10.04 lts is running on my old PC, except I can't seem to install my HP 895C.  This printer worked on previous releases on Ubuntu.  The printer is local and cabled to the PC's parallel port.  But "Add" under printing doesn't show any parallel printers under local printers. Only shows serial port, other, and network printers. Is this because 10.04 is beta? "Troubleshooting printers" doesn't have a list of printers, and wasn't much help.  Is the lpt1 in PC speak /dev/lp0 in Linux? Should that be the printer URI?

I've had similar issues ... with printers vanishing. Try this:

0) un-plug **vanished** printer from computer
1) turn off both computer and printer.
2) re-plug printer. turn on printer
3) turn on & boot computer

4) ,,, mebby the printer now re.appears when you reference the printer config dialog. Or mebby it just automagically appears & works .

---

### Post by PaulHuffman on 2010-04-30
Nss0000 - Sounds like a long shot since I don't know how a system restart will make /dev/lpt0 reappear, but I'll give it a try next time I'm in that office.

---

### Post by PaulHuffman on 2010-05-08
Yeah, Ns000, that didn't work. Any other ideas?  I'm rolling back to 8.04.

---

### Post by PaulHuffman on 2010-05-17
Clutch the pearls! >>There's a bug reported on this [https://bugs.edge.launchpad.net/ubuntu/+source/linux/+bug/369850]("https://bugs.edge.launchpad.net/ubuntu/+source/linux/+bug/369850")

I'll have to try the fix next time I'm at the location.

---

### Post by PaulHuffman on 2010-05-23
The fix worked.

First I reinstalled 10.04.

Just type in [FONT="Fixedsys"]sudo modrobe parport_pc[/FONT] 

Then Add printer showed not only the parallel port but found my HP 985C. Installed the driver, and started printing test pages.

Not sure yet if adding the modprobe line to /etc/modules makes the printer work after reboot.

---

