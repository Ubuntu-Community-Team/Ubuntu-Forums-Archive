---
title: "Will Hoary installer resize a ntfs partition?"
date: 2005-04-08
forum: Installation &amp; Upgrades
---

### Post by zcox on 2005-04-08
I wrote a couple [tutorials](http://ca.geocities.com/zachandloricox@rogers.com/ubuntu/ubuntu.html)   on how to install Ubuntu on an existing Win98/WinXP install a while back for the Warty release.  I'd like to do the same for the Hoary release.

The Warty installer would not resize a ntfs partition, but I was told that the Hoary installer would be able to resize a ntfs partition.  So is it true?  Can the Hoary installer resize an ntfs parition?

---

### Post by jdodson on 2005-04-08
[QUOTE=zcox]I wrote a couple [tutorials](http://ca.geocities.com/zachandloricox@rogers.com/ubuntu/ubuntu.html)   on how to install Ubuntu on an existing Win98/WinXP install a while back for the Warty release.  I'd like to do the same for the Hoary release.

The Warty installer would not resize a ntfs partition, but I was told that the Hoary installer would be able to resize a ntfs partition.  So is it true?  Can the Hoary installer resize an ntfs parition?[/QUOTE]

to my knowledge the hoary installer can not resize an ntfs parition.

---

### Post by jdong on 2005-04-08
I think I read somewhere, too, that the Hoary installer can resize NTFS.

---

### Post by az on 2005-04-08
Yes it can.

The debian installer on which the ubuntu installer is based began being able to resize ntfs about two weeks too late for it to be included as the Warty installer.  Debian RC2 has been able to resize ntfs for many many moons.  That is what Hoary is based on.

---

### Post by zcox on 2005-04-08
[QUOTE=azz]Yes it can.[/QUOTE]

 :grin: Sweet!!!

Another question: Can I resize an existing ntfs partition, create a fat32 partition, and create partitions for Ubuntu using the Hoary installer?

---

### Post by b_west on 2005-05-02
zcox-

I don't know if you're still looking for an answer here, but, yes, the Hoary installer can do just that. I know because I'm writing this on a machine where I performed just such an operation this morning.

I shrunk the default 60 GB NTFS partition that shipped with my laptop to about 30 GB, added a 20 GB FAT32 partition, then had then finished with an automated EXT3 format of the remaining 10 GB for Hoary.

The installer worked great and without a hitch. The only other action I had to take was to manually format the FAT32 within WinXP so Windows would read/write to it. After that, I've got a great share area for my files between the two OSs.

I know this thread is a little old, but good luck to ya!

---

### Post by prara on 2005-07-25
@ b_west: how did you do that? How can I resize the ntfs partition? (using Ubuntu 5.04)

---

### Post by az on 2005-07-25
[QUOTE=prara]@ b_west: how did you do that? How can I resize the ntfs partition? (using Ubuntu 5.04)[/QUOTE]

[https://wiki.ubuntu.com/forum/installation/Partitioning](https://wiki.ubuntu.com/forum/installation/Partitioning)

---

### Post by pierlo on 2005-08-27
[QUOTE=azz][https://wiki.ubuntu.com/forum/installation/Partitioning](https://wiki.ubuntu.com/forum/installation/Partitioning)[/QUOTE]

hum, am i missing something? 
the guide says: "Select the partition that you want to resize. Hit enter. Select the size. Enter a smaller size and hit enter." but i can't enter the new size on the size-row itself! How do i do that? 
Pressing enter goes to the next screen, and i can't change the size! Any ideas? 
 ](*,) 
thanks

---

### Post by blackburnrovers on 2005-10-23
[QUOTE=pierlo]hum, am i missing something? 
the guide says: "Select the partition that you want to resize. Hit enter. Select the size. Enter a smaller size and hit enter." but i can't enter the new size on the size-row itself! How do i do that? 
Pressing enter goes to the next screen, and i can't change the size! Any ideas? 
 ](*,) 
thanks[/QUOTE]

same problem here. i am using 5.10. i can highlight the current size of the partition, but then can't figure out how to change it. if i press enter, it continues on to the next step before i can give the new size.

---

### Post by az on 2005-10-23
Depending on how your partition table was made, (like if you use some proprietary software to partition before using the installer) you may have a wierd partition table that the installer will not be able to use.  It will just refuse to touch it.  


if you use fdisk (CTRL-ALT-F2) from the installer, what does it show when you list the partitions?

---

### Post by aysiu on 2005-10-23
Here's how to resize your NTFS partition with the Hoary installer (complete with screenshots):

[http://www3.telus.net/linux4u/ubuntu.html](http://www3.telus.net/linux4u/ubuntu.html)

---

### Post by Herman on 2005-10-23
zcox, your install example web site is great! When I made mine I wasn't aware that you else had already beaten me to it or I might have chosen to make mine on a different subject. I would love to see your new site, and offer every encouragement to you! Mine is definitely deficient where it come to the subject of creating a FAT32 partition for transferring files, and there may be other points as well that can be improved on. Please do!
    I think also that if we can offer more than one point of view or method, by the time people see something explained a couple of different ways they will really be able to understand what to do, and can decide whatever is best for them! All the best, (Herman)   :D

---

### Post by 2tim3_16 on 2005-10-24
I'm entirely new at this myself, having just installed Hoary about 5 days ago.

I currently have WinXP installed on my master drive (40 GB), and Hoary installed on my slave drive (200 GB). I have the slave drive formatted with 4 partitions, a 32MB boot partition (to fool the BIOS so it boots to the large drive); a 20GB root partition for Hoary; a 2GB swap partition; and the rest is formatted as NTFS. How do I get Hoary to recognize the NTFS partition, or to reformat it as FAT32? I would like to share it between WinXP and Hoary if possible.

I tried going to [https://wiki.ubuntu.com/forum/installation/Partitioning](https://wiki.ubuntu.com/forum/installation/Partitioning), but I'm just getting a message telling me that FireFox is unable to verify the identity of wiki.ubuntu.com as a trusted site, and it won;t let me accept the certificate.

---

### Post by Herman on 2005-10-25
:oops: , I didn't look at the date for zcox's original posts.

But meanwhile, someone else sent me a private message asking about how I made my 'screencaps' in my signature link. I would like to help and encourage others to do similar websites to show a trick or proceedure they can share with the rest of us.
Well, most of them aren't real screencaps, although many are immitations of real screencaps. Some are completely my own simulations of what I actually see on my screen. ( I use more than one computer for this). I cheated by using microsoft 'paint', as I (of course), have a dual boot computer. No other software is needed, just lots of time and patience. GIMP alone will work too, I made my locos with GIMP only, but 'paint's' simpler and quicker for some jobs.
I made grey rectangles, 600 pixels wide by whatever height was required, and typed the text into them with the 'paint' text tool. I did most of the other things in them with 'paint' too. GIMP's the best for fancy work. 'Paint's' okay for plain work.
For the non-animated ones, I mounted my Windows file system in Ubuntu, opened the bitmap image file in GIMP, and 'saved it as' .gif format. This is to save upload cost, as .gifs are very 'light'. Another good format would have been .png, but my website software wasn't able to use it. I had .jpg's earlier on, they were poor quality. Bitmaps are too 'heavy' (KB upload cost).
For how to make animated images, see: [http://www.ubuntuforums.org/showthread.php?t=80493&highlight=Herman](http://www.ubuntuforums.org/showthread.php?t=80493&highlight=Herman)
The animated images are all .gif 's too, by making say ten or so copies of the same bitmap image, changing each one just a little bit and copying each one to a new layer in GIMP. It's a handy tip to save each bitmap by naming it a name starting with a sequential number. For example '1filename' and the next one '2filename', '3filename', and so on, so they'll automatically fall into the correct sequence for you.
Also, if it saves time, anyone is welcome to copy images off my website, I don't mind sharing them.
I would like it if others can make similar websites. I would especially like it if someone would be interested in taking over the NTFS part of mine and improving on it. (making the FAT32 partition during the initial install). I will get around to that after a while if no-one else does though. I'd rather do something else, like work on GRUB re-installing, and/or GAG/Lilo boot loader, for 'part two' of my website, and just keep the Windows FAT32/Ubuntu Dual boot part one. 
If I can help anyone, please ask, and I'll give all the help I can.

---

### Post by 2tim3_16 on 2005-10-27
I found what I was looking for. I've now mounted my Windows partition, and reformated the rest of me drive space to FAT32 so that I can share it between Ubuntu and Windows.

---

### Post by climhazzard85 on 2005-12-12
Positive, unfortunately.

---

