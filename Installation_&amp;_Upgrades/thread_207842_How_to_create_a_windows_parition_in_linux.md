---
title: "How to create a windows parition in linux?"
date: 2006-07-02
forum: Installation &amp; Upgrades
---

### Post by w1z4rd on 2006-07-02
Whats the safest way to do this? I love Kubuntu as my desktop, and I have no intention of changing, however until I can actually game propley on linux, I am going to have to use a dual boot alternative.

Please dont try to tell me about things like Cedega and wine, I have purchased Cedega, and tried wine. The bottem line is until the linux devs find a better way for X to communicate with the hardware (TCP/IP is a stupid solution), linux will never beat microsoft in the desktop war, and people will not use it until that solution is found.

I hate MS, and it burns me up, that I am forced to install a windows parition to be able to competivly game on a PUNK BUSTER ENABLED RANKED SERVER. Even if I could play BF2 on a ranked server with the lower FPS, I would, but currently (with no solution in sight), I am forced to install gawd dam windows.

Now, back to the post, and an end to my rant. What would be the safest way to create a 10GB parition on my linux ext3 parition (currently 500GB). I have spent to much time customizing kde to be as eye candy as possible, so I do not wish to loose any data.

I did some searches, but the only results i found were how to safely make a linux parition on NTFS... not how to safely make a NTFS patition on an exisiting ext3 parition without loosing data.

Any help in this would be appretiated.

---

### Post by Ctrl+Alt+Del on 2006-07-02
You cannot create a partition within a partition, you will have to shrink your existing ext3 partiton and create a new ntfs drive. 
Depending on your current parititioning layout this might become a very ugly task, but you will have to provide some detailed info to estimate how ugly this will get.

---

### Post by DJ Scribblinni on 2006-07-02
Even though your best bet would be install windows first... 
Windows overwrites the MBR/bootloader
Do a search for installing a boot loader in windows before attempting anything...heres a possibility...

Split the hard drive using a program such as QTparted, which does what Ctr+Alt+Del says, it will shrink your ext by that amount, you may want to format it has FAT or something as such.  Boot up the comp with the dreaded Windows CD, do the install on that particular empty partition.  Windows will recognize the entire hard drive, and should see the 2 different partitions.  The Linux partition will be known as Unknown.  If windows only sees one partition, you had better stop there because it will overwrite anything and everything.  Assuming the install went flawlessly, you need to find a way to install Grub, or whatever boot loader you like to use. Windows will overwrite it without even telling you.  It is best to search this before even starting this.  Without it, you'll never get back into Linux.  Here's one how-to  

[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows]("https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows")

Good luck finding a good how to on installing Grub in windows, I haven't found a decent how-to, but if you do, post one up here!

---

### Post by Tomosaur on 2006-07-03
I couldn't get my NTFS partition to resize - it just doesn't seem designed to do it, so I wiped my hard drive and made a linux partition, a swap partition, then let windows make it's own NTFS partition. It overwrites the MBR so Grub won't work, but I'm about go and fix that problem right now (just been waiting for SP2 to finish installing :rolleyes: )

---

