---
title: "First Install...booting up hangs at &quot;mounting root file system&quot;"
date: 2006-08-25
forum: Installation &amp; Upgrades
---

### Post by skinrock on 2006-08-25
Right now I have XP Pro installed.  I did a disk cleanup and defrag, then booted up knoppix and ran qtparted to resize the partition down to 20 gb.

I proceeded to install ubuntu, wasn't sure what partition option to use, so I did a manual edit and made two new partitions, a 20 gb primary ext3, and a 1 gb primary linux-swap.

now I'm not saying I'm good with partitions, so I may have gotten those wrong.  all I know is the installation was a success, but when I rebooted (grub correctly recogonized ubuntu and xp pro), and booted into ubuntu, it hung at the "mounting root file system" message.  tried it twice, no luck.

any suggestions?  thanks.

edit: btw, here's my hardware -

ASUS A8N32-SLI Delux
AMD Athlon X2 64 4400+
2x512 MB Corsair XMS Ram
320 GB SATA 3.0 HDD
nVidia 7900GT
Lite-On DVD Burner
D-Link Wireless G Adapter

I doubt most of that doesn't matter, but figured I'd post it.

another edit: i used ubuntu live cd to delete the partitions, except my 20 gig windows one, and reinstalled using the "largest continuous space" option...and it still hangs...

---

### Post by Original Brownster on 2006-08-26
Hi, I suspect (though could be wrong) that the sata disk name has changed between installing via the live cd and now booting. Shouldn't happen but something we can check.
Let us know if you have more than one sata drive.
Confirm you have installed the entire linux in one partition (except swap)
if you can remember the partition letters from the installer plz let us know.

What we are looking for is an inconsistency in the drive letter recorded in the menu.lst file and that reported by 'find ...'

boot from the hard drive, when you get the grub menu press 'c' to go to the command line.

type:
*root*
and make a note of what it says hopefully something like '(sd0,2)'

next type:
*find /boot/grub/menu.lst*

with any luck it will come back with something like: (sd0,2)

compare the two outputs above

if there was a difference between the two above that will be the problem, as this specifys the root partition used and where grub found a grub menu file.

Another check, if the two outputs where different, change the root parameter by entering:
root (sdx,x) 
where x,x are the same as that reported by the find command above.

now type
cat /boot/grub/menu.lst

and page through until you find the first stanza to boot linux, something like:
title Ubuntu
          root (hd0,0)
          kernel /boot/vmlinuz root=/dev/sda1 vga=ext
          initrd /boot/initrd
          savedefault

the above is just an example, 
look at what yours says, check that the line starting 'root' has the correct parameter and importantly the line starting kernel at the end of which there will be another root bit like 'root=/dev/sda2' 

Now for the slightly confusing bit... grub counts drives and partitions from 0 not 1 , so if grub says (sd0,0) that translates to /dev/sda1
first drive = a, first partition = 1 counting from 0
another example, grub says (sd1,3) that translates to /dev/sdb4, 
2nd drive = b, fourth partition = 3 counting from 0

with that in mind check the root parameter is correct compared to what find reported earlier, you might find that the drive letter is incorrect.

Let us know all the outputs and the stanza bit from your menu.lst file 
then we can tell if it's right or not.

---

### Post by skinrock on 2006-08-27
Well, everything is saying "hd0,1".  And when I did cat on menu.lst, the part where it lists out the ubuntu info says "/dev/sda2" for the kernel line.

So from the sounds of it...everything is matching up.  btw, I only have one sata drive, and I'm pretty sure it only installed it on one partition.

---

### Post by randell6564 on 2006-08-27
Hi!  I know that you would rather me give you some working tips, but I found this link and it might help you to understand S-ATA raid devices and how Linux doesn't like them much.

[http://linuxmafia.com/faq/Hardware/sata.html](http://linuxmafia.com/faq/Hardware/sata.html)  Good Luck!

---

### Post by skinrock on 2006-08-27
well, i was reading in the other threads that usb devices might cause it to hang, and even though i didn't think any of mine should have interfered, i went ahead and removed all of them, and now it boots up fine.

so that might have been it.  thanks for the help...about to boot into my xgl session :)

---

### Post by Original Brownster on 2006-08-28
Hi, I'm glad you got it working, that's good news :-)

Incidentally when you plug in all the usb devices, do any get named /dev/sdx ? (where x is a drive letter)
Just wondering if this is the cause or not.

> **skinrock said:**
> well, i was reading in the other threads that usb devices might cause it to hang, and even though i didn't think any of mine should have interfered, i went ahead and removed all of them, and now it boots up fine.

so that might have been it.  thanks for the help...about to boot into my xgl session :)

---

