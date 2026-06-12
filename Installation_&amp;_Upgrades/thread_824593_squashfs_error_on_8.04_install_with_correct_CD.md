---
title: "squashfs error on 8.04 install with correct CD"
date: 2008-06-10
forum: Installation &amp; Upgrades
---

### Post by flntobi on 2008-06-10
Hi

I tried to install Ubuntu 8.04 Desktop on my Laptop. Before I had a dual boot with Windows xp and Ubuntu 7.x. 
Booting from the CD works fine and the Install-Gui lets me select my installation-properties: Manuel Partition to keep the dualboot.

But on "Copying files..." the Process stops at 62%, when I switch to another Console (Ctrl-Alt-F1), I See the following line running down:
squashfs error: unabled to read page, block xxxx

The CD is fine! I already installed 2 PCs with it.

Can anybody give some hints, where to look? I want Ubuntu back on my PC.

Cheers flntobi

---

### Post by mxg01 on 2008-06-10
The 'unable to read from squashfs' message usually means a corrupt CD. It might be that the drive on the PC you are using cannot read that CD even though other drives read it. The usual advice is to burn the CD at a slower speed. x4 or less. Give that a go and see if it makes a difference.

---

### Post by flntobi on 2008-06-10
I knew somebody would write that.  But thats not the reason, because today I managed to install it by using reiserfs instead of ext3 as filesystem.

So the reason for the proplem seems to be the filesystem on which ubuntu is installed. I would be nice if someone can confirm that who has similar problems.

rock on
:guitar:
flntobi

---

### Post by mxg01 on 2008-06-10
In that case I wonder if you had some errors on your existing ext3 filesystem. Reformatting it as ReiserFS would have cleared or marked these as bad. That may be why it worked when you changed the filesystem.

---

### Post by flntobi on 2008-06-10
Doesn't ext3 mark bad sectors? Because I tried several times with ext3, making new partitions.

---

### Post by mxg01 on 2008-06-10
ext3 does mark bad blocks but only when it knows about them. The fact that you created and formatted a new partition would have marked them as bad so it's not that. The error is in reading from the squash filesystem anyway. It must have been something to do with reading the CD that particular time.

Other than that I'm going to have to say I don't know.

---

### Post by alamuru420123 on 2008-08-20
I've had the same problem. I keep getting squashfs errors as soon as I try to boot from the CD. md5 checked out fine and I burnt 2 more CDs and still got the same error. While running check CD for defects, got 19 in the first and 21 in the second. 

When I got the same error in the 3rd CD, I pressed F6 at the initial screen and added the option 'all_generic_ide' without the quotes after 'splash' and before '--'. And it worked! Typing this from the Live CD right now. You could give it a shot and see if it works for you.

---

### Post by tekorei on 2008-08-23
I think it's a Hardware problem, I got the same SQUASHFS error during my installation, I swapt my DVD-DRIVE and it worked, good luck

---

### Post by fencer on 2008-08-23
> **alamuru420123 said:**
> I've had the same problem. I keep getting squashfs errors as soon as I try to boot from the CD. md5 checked out fine and I burnt 2 more CDs and still got the same error. While running check CD for defects, got 19 in the first and 21 in the second. 

When I got the same error in the 3rd CD, I pressed F6 at the initial screen and added the option 'all_generic_ide' without the quotes after 'splash' and before '--'. And it worked! Typing this from the Live CD right now. You could give it a shot and see if it works for you.

sry but didnt work for me :-( help plz](*,)](*,)

---

### Post by markovich on 2008-10-17
Had the same problem. After following mxg01's advice and burning the iso at 4X speed, I no longer received the SQUASHFS errors and successfully installed my first unbuntu box.

---

### Post by Indubitableness on 2008-11-16
Hey guys, I had this same problem, and it was only on a computer running IDE connection hard disks, one of which did, indeed, have damaged sectors (like a lot)

  After getting help from this exact forum, i found the noapci (or whatever) and other no* boot options that have helped a few of us are useless. I got the same errors.

 My hypothesis came to this, i needed to format the partition into a useful ext3 or other linux specific format before hand, i tried to do this with ultimate boot disk, but alas, it was corrupt.

 I gave up and installed OpenSUSE, which i did not like at all, BUT, the resulting partitions it made allowed me to boot Ubuntu 8.04!!!!

 Once i got ubuntu booted, i was able to simply format the openSuse partitions and install on top of it. BAM problem solved.

 I know some of you have already tried partitioning ahead of time, and you're still getting the same problem, in which case, this solution may not help you, but it worked for me, so i wanted to post it here. Good Luck

---

### Post by scl205 on 2009-05-15
After reading these posts I changed the CD drive in my box. The install went without a hitch after that

---

### Post by phanidee on 2009-07-18
Iam also having the same squashfs errors. I have gone through many of the posts relatted to these and many people were saying that, this is because of the sata drive. But still, i dont know the solution.

Waiting eagerly for the solution !!

---

