---
title: "Some questions before first installation"
date: 2011-04-01
forum: Installation &amp; Upgrades
---

### Post by guysh on 2011-04-01
Hello all
I want to install Ubunto netbook on my compaq mini 730, but I want to keep my windows xp OS as well and have the dual boot option. 
At the moment I have the hard drive partitioned to C and D. 
My question is - what is the best way to install ubuntu and keep windows ? 
Should I create a separate partition for it ? if yes what size ? 
Can Ubunto install itself on C next to windows automatically ? 

Thanks in advanced :)

---

### Post by Sean Moran on 2011-04-01
> **guysh said:**
> Hello all
I want to install Ubunto netbook on my compaq mini 730, but I want to keep my windows xp OS as well and have the dual boot option. 
At the moment I have the hard drive partitioned to C and D. 
My question is - what is the best way to install ubuntu and keep windows ? 
Should I create a separate partition for it ? if yes what size ? 
Can Ubunto install itself on C next to windows automatically ? 

Thanks in advanced :)
First off, copy as much as you can from your Windows My Documents folder to the D:, and do what you can to remove as much of the unnecessary data from the Windows C: to to the D: or some things maybe onto a DVD as backup.

It's good to have EVERYTHING backed up somewhere, just in case, as well as a WinXP installation CD, just in case.

When you've scaled down the amount of data on the C:, it mught be down to under 8Gb if you're lucky as I am, but do the best you can.  As small as you can get it, and add 20% or so for expansion with less fragmentation.

That's the second part.  Run the Disk Defragmenter to realign all the files on C: at the front end of the partition.  It's something to do while you're having dinner because it does tend to take a while.

The next part is to boot into the Live-CD and use GParted to downsize (resize/move) the C: /dev/sda1 and the D: - assumedly /dev/sda5 to make room for the new partitions and effect the dual boot for Windows and Ubuntu.

If you downsize C: so that there's 20% extra free space or so, and reduce D: to whatever size suits the needs you envisage in the future.  eg, you might make it as small as possible so that you can copy most of the archived data across to the new partitions.

Now you should have room enough to create a new 8Gb partition as /dev/sda2, and a whole lot of room on the extended partition, where the D: resides as a logical partition /dev/sda5.  You'll also need to create a small 2-4Gb SWAP partition, which can go somewhere on the extended as a logical, or you might want to reduce the extended partition by a few GB and set your SWAP up as /dev/sda4.  That would cover all four possibilities for primary partitions, with /dev/sda1 & 2 for Windows and Linux, /dev/sda3 as the extended, and /dev/sda4 for a little SWAP at the back end, like the caboose on a steam train in a John Wayne western.

The remaining free space within the extended partition can be used for /home or a range of partitions for archiving data, or other purposes, depending on what you want to do.

.

---

### Post by guysh on 2011-04-02
Oh my.... I'm starting to remember why I didn't install ubuntu in the past. Does it have to be so complicated ? there is no auto mode ?

---

### Post by guysh on 2011-04-02
O.k I did some reading. 
Is it better in my case to install regular Ubunto. Will it support my Netbook model - Compaq mini 730 ej ?

---

### Post by Z80A on 2011-04-02
Wouldn't it be an idea just to start out using the WUBI method? I sense that you are in  an *experimenting phase* and maybe not really ready to let go of Windows? For a long time I was using a WUBI based installation "within" Windows - but configured to start up Ubuntu as default OS. Worked quite well (no performance issues) and installation was a no-brainer through Windows.

[http://www.ubuntu.com/desktop/get-ubuntu/windows-installer](http://www.ubuntu.com/desktop/get-ubuntu/windows-installer)

[https://wiki.ubuntu.com/WubiGuide](https://wiki.ubuntu.com/WubiGuide)

...and should you get tired of Ubuntu (don't see that to be likely), you can remove it through the Windows Control Panel and your Windows XP will appear untouched! ;)

Z80A

---

### Post by guysh on 2011-04-02
Now that seems like a great idea ! 
Thanks allot, I'll do just that.

---

### Post by Z80A on 2011-04-02
Great! Again trying out this, it is still a good idea to consolidate as much of you data in one common place (e.g. drive D:) and do a proper back-up.

Not really familiar with your netbook hardware, but you will need to make sure you have sufficient space for two OS's (hardly a problem though)...

Z80A

---

### Post by guysh on 2011-04-02
I did just that and Installation was a breeze. 
Had some problems with installing the updates but it seemed to solve it self. Also installed Opera and dropbox

Thanks for the help

---

