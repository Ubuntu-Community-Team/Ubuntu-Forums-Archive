---
title: "Desperate for help. I installed linux, moved partitions, and windows doesn't boot"
date: 2015-10-10
forum: MINT
---

### Post by dustin23 on 2015-10-10
I updated my Dell 3531 from windows 8.1 to 10, got sick of it and installed linux per a youtube video that had me download mint cinnamon to a usb with unetbootin. The install went great and I had the option when starting the machine to either use windows 10 or linux. I used gparted to make the linux partitions. 

After doing this there were several small unallocated spaces that I wanted to combine. I used GParted for this also. I was unable to move the linux partitions I had created since I was running off of them but did move some of the windows ones. Now windows will not work. I get a Process1_initialization_failed error. One of the changes I made was moving the OS and shrinking it so that it only had a small amount of open space left. I am guessing that they need to be in an order that I changed.

I am not sure if this is the place to go, but I am feeling overwhelmed here about what to do.

Any help is greatly appreciated.

D

---

### Post by yancek on 2015-10-10
Are you using UEFI with both windows and Mint?  Were you initially able to boot into both?  If you moved the partition with the boot files, they will not be in the location they previously were and they won't be found.  I'd suggest you do an online search for the error you posted.  You might first try booting Ubuntu and running sudo update-grub to see if you get any output for windows.

---

### Post by dustin23 on 2015-10-10
I don't know if I am using UEFI. When I followed the steps in the video, I was able to boot into both without an issue. After I got linux working, I went into GParted again and saw that my hard drive had many small unallocated pieces. I did not want this and decided to try to move them to combine them. I also shrank the other windows partitions to almost as small as possible. It was during one of these steps that I did something wrong.

It doesn't appear that I can move the order of the partitions, but only change their size and unallocated amounts between them, so I am thinking the order of them is OK, I also added back the amounts to each one that I had removed, but am still getting the initialization error.

thanks for the response

---

### Post by oldos2er on 2015-10-10
Moved to MINT. Linux Mint's own forums are here: [http://forums.linuxmint.com/](http://forums.linuxmint.com/)

---

### Post by oldfred on 2015-10-10
Did you delete some essential Windows partitions that in gparted show as errors as they are unformatted?

 Microsoft suggested partitions including reserved partition for gpt & UEFI:
[http://technet.microsoft.com/en-us/library/dd744301%28WS.10%29.aspx](http://technet.microsoft.com/en-us/library/dd744301%28WS.10%29.aspx)
Order on drive is important: msftres
[http://en.wikipedia.org/wiki/Microsoft_Reserved_Partition](http://en.wikipedia.org/wiki/Microsoft_Reserved_Partition)

      
 Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)

---

