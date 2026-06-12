---
title: "Buffer I/O Error on Device sr0"
date: 2008-05-19
forum: Installation &amp; Upgrades
---

### Post by tonofclay on 2008-05-19
So I've run into in an error that occurs on boot up, very shortly into the loading process. I get repeated messages saying "Buffer I/O Error on Device sr0, followed by the logical block which increases by 1 with each error output. 

I've done a lot of googling and haven't found any solution to my problem yet. I first experienced this problem with Linux Mint 4.0, where I saw the error. Since then I've tried an 8.04 beta install, and more recently (yesterday) the final 8.04 release. Both of the ubuntu's get to the stage of loading hardware drivers and cannot get any further...I assume the same problem is occurring that I had with Linux Mint. I tried various flags like noapci but none seemed to do the trick. I made sure to burn the discs at the slowest speed, and have seen them work on other computers. I tried cleaning the disc drive lens as I saw that was a possible solution, but this did not work either.

I recently encountered a problem with my dell and the intel storage matrix which prevented me from using AHCI, and I was needing to change the bios to RAID/ATA in order to boot windows at all. I finally got the AHCI driver installed again though with a custom Windows install cd made with nlite. I was hoping this would be the solution to my Linux problem as well but unfortunately nothing has changed.

I'm at the end of my rope here...I've been using Windows for a month or two now and I can't take it much longer. Any suggestions would be greatly appreciated!

---

### Post by dstew on 2008-05-19
Probably the Linux kernel in the Live CD is having trouble interacting with your sr0 device, which is probably a CD or DVD drive. If could be the CD or DVD is bad, or the drive is bad, or a cable is bad etc. Do other data CD/DVD's work in the same drive OK?

If the drive has an IDE connector, try the kernel parameter **ide=nodma**. You can also try **libata.dma=1** which allows DMA only on your hard drives, and turns it off on your ATAPI (CD-ROM) drive.

---

### Post by tonofclay on 2008-05-19
Thanks, I'll try those out and see if one of them does the trick. I saw that it might be a bad CD or DVD drive, but I tried in both my DVD and CD drive and get the same problem, and I haven't had any problems with any other cds, so I'm pretty sure the drives are ok.

---

### Post by tonofclay on 2008-05-19
Argh, no luck with either of those params. Guess I'll need to go back to browsing page after page of google...maybe something will turn up eventually.

---

