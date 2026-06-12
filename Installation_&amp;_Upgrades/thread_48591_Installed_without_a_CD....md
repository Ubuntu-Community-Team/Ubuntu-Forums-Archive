---
title: "Installed without a CD..."
date: 2005-07-13
forum: Installation &amp; Upgrades
---

### Post by Jeviar on 2005-07-13
Hi all!

Am using a Pentium 4 Datamini computer. Was previously on Windows XP when I decided to switch to ubuntu. I tried to install by booting from the install disc but it gave me an error saying 'Boot Failed'.

Then, I decided to check if it was my CD-Rom drive that was spoiled. No go. It managed to detect all my other CDs. So then following the advice of some threads, I decided to do a network install. Everything seemed to be going well until I was asked to reboot.

So then I rebooted the com and everything still seemed to start out well until it said 'Starting Enterprise Volume Management System'. It would hang for 5mins before outputting this error message: Buffer I/O error on device dm-2, logical block 0. and then it will just continue on giving me the same error message with a higher logical block number.

Decided to try the recovery thing. (There was an option on boot to press esc, then there were 3 things to load. one was the original ubuntu, one was the recover or maybe safe version and the last was a memtest thingy. the memtest was fine.)

The recovery thing now gave me this output: 

ide: fail opcode was: unknown
end_request: I/O error, dev hdb, sector 24595525
Buffer I/O error on device dm-2, logical block (some number)
hdb: dma_intr: status=0x51 {DriveReady SeekComplete Error }
hdb: dma_intr: error=0x40 {UncorrectableError }, LBA Sect= (some number), sector=(some number)


Now I don't know what is wrong and I have no idea how to get things back up. Appreciate any help.

---

### Post by downtheciv on 2005-07-13
have you got your hd a or b flagged/writen as primary?
seems that your cd and or second partition maybe in a logical format instead of primary  :-k

---

### Post by Jeviar on 2005-07-13
I'm not exactly sure what is the configuration inside. However, what I do know is that I have 2 drives, C drive (my primary drive) and my D drive. Before I attempted to install ubuntu, my D drive was partitioned into 2.

Actually, I think i made a mistake while doing the net install. I followed [this](http://ubuntuforums.org/showthread.php?t=28948&page=1&pp=10)  guide. But as I didn't want to do a dual boot, I decided to format my C drive totally...

---

### Post by Jeviar on 2005-07-13
Managed to fix my installation. What I did was used a friend's Win XP boot disk, delete all partitions and repartitioned everything all over. Basically reinstalled Win XP and then dual boot. Heh. 

Hope this time things will go great! *crosses fingers*

---

