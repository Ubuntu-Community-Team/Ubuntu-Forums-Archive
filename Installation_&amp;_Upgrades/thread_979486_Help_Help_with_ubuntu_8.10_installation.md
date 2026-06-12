---
title: "Help Help with ubuntu 8.10 installation"
date: 2008-11-12
forum: Installation &amp; Upgrades
---

### Post by sonicgg on 2008-11-12
When i install ubuntu 8.10 on my new machine, I start it with live cd, then install, the installer hangs at the third step: scanning disks, the percentage is always 50%, and keyboard&mouse don't work, the whole system hangs. and i have no way to check the error log but reset the machine.

btw, I test ubuntu 7.10, the error is the same, but the percentage is 46%, not 50%.

I changed different setting in bios, change sata disk to ide disk, all don't work, all got the same errors.

could someone give me a hint of this? I googled "ubuntu scanning disk hang', someone had the same problems as me, but I can not find a workable solution yet.

My machine: 
intel E8500
asus p5ql
2G kingston
250G segate harddisk.


thank you very much in advance.

---

### Post by ubiubi on 2008-11-12
Hi
I have a similar problem, ABIT p35E, Intel e4300. It achieves 48% stage three, passes to stage 4 but the dialogue box that is supposed to show all partitions is grey with no disk image inside. I think it may be a partition table problem because windows is operating properly and all partitions ready for the linux install are shown in GParted. It's just that the live CD doesn't seem to recognise them!

I don't know if this gives you any ideas. Good luck!

---

### Post by sonicgg on 2008-11-12
it's slightly different, i even couldn't see the step 4, the whole system just hangs at step 3.
I google out a possible solution, are you using the 'install' link on desktop to install ubuntu? The link is actually the command: 
'gksudo ubiquity', someone said it works if execute 'sudo ubiquity' in terminal. 
I will test it when back home. Hopefully it helps... it really frustrated me a lot.

---

### Post by ubiubi on 2008-11-12
Hi
This might be clutching at straws, but it might me possible that ubuntu does not recognise your hard drive (if it is  a sata) see the thread below. It does seem to be describing my exact problem , so I'll give it a go tonight. Who knows, it might even help You.

Good luck and let me know

 	
[ubuntu] Ubuntu Installer Shows No Partitions (Multi-page thread 1 2)
mxcrowe 

This is a very, very recent thread!

---

### Post by sonicgg on 2008-11-12
still no luck:((((
i tried several method:
 1) enable ahci in bios for sata disk
 2) put all_generic_ide=1
ubiquity just hangs at the 3rd step, showing scanning disks forever....

btw, my motherboard is p43 chipset.

---

### Post by sonicgg on 2008-11-12
actually I can access the disk via gparted.
I also use gparted to delete my orginal partitions, create a new one....
but when ubiquity scanning disks, the whole systems crashed...

---

### Post by sonicgg on 2008-11-12
anyone could help? I am really really frustrated....

---

### Post by sonicgg on 2008-11-12
update:
I tried with a ubuntu 7.10 official disk.

founding is I still can not install on my machine, hang at 46% of scanning disks. 
Interesting thing is I can not use gparted neither, gparted with hang the whole system. But with 8.10, gpart works on the same machine.

So I GUESS it's a bug which already fixed in gparted from 7.10 to 8.10, but not fixed in ubiquity.....

still ask, anyone can help....

---

### Post by ubiubi on 2008-11-13
Hi again

I don't know if this is of any help but I suspect you need advice from a more experienced user!

 Good luck!


[http://forum.msi.com.tw/index.php?topic=120088.0;prev_next=prev](http://forum.msi.com.tw/index.php?topic=120088.0;prev_next=prev)

---

### Post by sonicgg on 2008-11-13
i made some progress..
I changed to alternative cd, it works well... seems it's definitely a bug in ubiquity...

but i met another problem...
when i installed with alternative cd, the installer hangs at confingurating apt.....

---

### Post by ubiubi on 2008-11-13
Well, I solvedmy problem, just had to choose a different sata port on my MB. If you post your motherboard name and model I'll see if I can find any useful threads on the net. Keep going!

---

