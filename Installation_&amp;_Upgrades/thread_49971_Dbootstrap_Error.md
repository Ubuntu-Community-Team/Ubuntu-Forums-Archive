---
title: "Dbootstrap Error"
date: 2005-07-18
forum: Installation &amp; Upgrades
---

### Post by Kiijo on 2005-07-18
Hello,
I'm having trouble installing ubuntu.  I have been able to boot from my burned cd and go through the beginning of the installation.  I get through the disk partition section and then get a Dbootstrap Error when I get to the "Install the base system" portion of the install.

I've matched the checksum on my download and burned 3 different cds.  The last one was burned at 2x as suggested by the Dbootstrap Error.

I have had the exact problem on 2 different systems (though they are both old P2 systems).

Any help is appreciated, thanks
Rob

---

### Post by amohanty on 2005-07-18
Can you post your partition table?

 ie how many partitions? 

What are they (/boot, /, /usr/...)?

What were their sizes? 

Basically the window that confirms partition changes before install.

AM

---

### Post by Kiijo on 2005-07-18
I created 3 partitions:

1 primary 98mb ext3 /boot
2 primary 5gb ext3  /
3 primary 296mb swap space

---

### Post by Kiijo on 2005-07-18
Thinking you might be on the right track I decided to change the partition infostructure:

1 primary 8gb ext3 /

and it works now...

Thanks for your help

---

### Post by h0bbe on 2005-07-31
I'm trying to install Ubuntu Hoary from the Shipit CD and have exactly the same problem: debootstrap error=couldn't retrieve bsdutils. I've tried with five different CD's and still have the same problem. The LiveCD works fine though, that's what I use now.

There is a description of the problem on [https://bugzilla.ubuntu.com/show_bug.cgi?id=12790](https://bugzilla.ubuntu.com/show_bug.cgi?id=12790) but I don't understand what do do to it.

Is the partitioning table the cause of the problem? I want to clear my entire harddrive and set up a completely new system with Ubuntu. The partitions i want to create are:

1. 10 gb /
2. > 59 gb /home
3. 10 gb /extra (for a possible other OS in the future)
4. < 1 gb swap partition (size as suggested of the partition manager)

Is another partition table the solution to the debootstrap error?

I find it rather peculiar that the partition part of the installation is so fast. After the partitions are ready and the installer continous it just set up the partitions and I can't see anything about formatting. Shouldn't it take a while to format an 80 gb harddrive? After the partition set up the debootstrap error eventually occurs and the installation fails :-(

I really want to get Ubuntu going but are getting fed up on this and thinking about trying another distro. I'm a newbie to Linux so the solution maybe is really easy.

Hope anyone can help me!

---

### Post by amohanty on 2005-07-31
Ehm..err you are missing the '/' partition

you need this:
/
/home
/extra
4x<size of installed RAM> swap

I would suggest converting /root to /
/root is similar to /home/<username> but for the root user. Without / you cannot load anything.

HTH
AM

---

### Post by h0bbe on 2005-07-31
Sorry, I just wrote root. In my configuration it's only / (I've edited my previous post now), still I have the problem. Any suggestions?

---

### Post by amohanty on 2005-07-31
Ok heres something I tried a long time back, dunno if it will still work but something to try:

1. Download Win98SE boot disk from [www.bootdisk.de](www.bootdisk.de)
2. Boot into the box via boot floppy
3. use fdisk to create a primary parition of 10G which will be assigned C: (this will eventually become /extra)
4. reboot and boot from floppy.
5. format C: as a fat partition.
6. boot from Ubuntu install CD
7. During partitioning, leave the fat partition alone, assign 4xRAM as swap and the rest to /. If the FAT partition has a # (or some such character) in the format column in the confirm partition changes table instruct the installer to not format it
8. Continue with install and post the results if something goes wrong.

HTH
AM

---

### Post by h0bbe on 2005-08-04
Thanks for the suggestion but I solved it yesterday by skipping the base system installation part and continue with copying the packages to my harddrive (next step) from the cd. After that (or after rebooting, don't remeber) it succeded installing the base system and everything went on just fine. I'm finally a happy Ubuntu user :-)

I didn't check what went wrong though and are still wondering how many others who give up on Ubuntu because of this!? There are a whole lot of forum threads out there on this problem and the most common reply is "sounds like a bad CD!". I'm not sure that's the explanation and hope the Ubuntu team correct it for the next release.

---

### Post by ubunta on 2005-08-05
Hi!

I just have the same problem. I tried to do the amohanty sugestion but it didn't work. I have a laptop computer and i want to have a partition for winxp and another with ubunto.  ](*,)  

I wish to be a ubunto user  :roll:

---

### Post by ubunta on 2005-08-06
Hi!

I just find the solution. It was a problem with the partitions.

First i did 
     / ext 3
     swap
     fat 32

Now i am doing
     [COLOR=DarkRed]/ ext 2[/COLOR]
     swap
     fat 32

If anybody know how to explain this situation...
It seems to work. I hope this information can help somebody.

---

### Post by Cynos on 2005-08-11
If I may bump this thread - 

My system - 

20Gb HD
Partition 1 is NTFS and staying that way, 9.2Gb
Partition 2 is Swap, 764Mb
Partition 3 is ReiserFS, 9.9Gb

Installing off Ubuntu Shipit CD.

Using DEBCONF_DEBUG = 5, I've garnered the following information about the debootstrap errors during the copying of base system. 

[b]Missing ide-mod
Missing ide-probe-mod
Missing ide-detect
Missing ide-floppy[/b]

Hmm, this is during the loading of packages.

During the install base system process, the following is the latest error message - 

tar: write error: input/output error
tar .usr/share/man/js/malchsh.lgz *Exact filename may differ*

**/dev/ide/host[0]/bus[0]/lun[0]/part3** is mounted as **/target**

which has become read-only. I've had various different programmes (cp etc.) fail at different points, but all with the same problem, my partition has become read-only.

I'm told that Linux will do that on a read/write failure, so I'm wondering what's causing the read/write failure. 

Now, after this happens, the install partition manager can't see my partition table, nor can fdisk. 

Any advice welcomed, including RTFM (if there's a link to the appropriate page in the manual  ;-) ) because I quite want Ubuntu installed, but I'm an incredible Linux newbie. 


Oh, I've done a destructive badblocks read-write test of the 3rd partition, no bad blocks. I've also checksummed the ShipIt CD, and it's fine.
I'm now off to try the above ext2 partition advice, but I hear ReiserFS is the shiz, so I'd prefer to keep it.

---

### Post by BiggoCharley on 2005-10-08
[QUOTE=ubunta]Hi!

I just find the solution. It was a problem with the partitions.

First i did 
     / ext 3
     swap
     fat 32

Now i am doing
     [COLOR=DarkRed]/ ext 2[/COLOR]
     swap
     fat 32

If anybody know how to explain this situation...
It seems to work. I hope this information can help somebody.[/QUOTE]

I have the "dbootstrap" problem -tried the above but it didn't solve it. I have been trying to install Ubuntu 5.04 on an IBM Thinkpad 600x.  I have never been able to install any Linux dostro on this machine.  I have tried Ubuntu, Fedora Core 3 and Libranet all with no success.  I currently have Ubuntu installed on an HP Omnibook 4150. The installation went off without a hitch. I'm ready to throw up my hands and call it quits as far as the Thinkpad goes unless someone has some "magic formula" for me.

---

### Post by Cynos on 2005-10-09
> I have the "dbootstrap" problem -tried the above but it didn't solve it. I have been trying to install Ubuntu 5.04 on an IBM Thinkpad 600x. I have never been able to install any Linux dostro on this machine. I have tried Ubuntu, Fedora Core 3 and Libranet all with no success. I currently have Ubuntu installed on an HP Omnibook 4150. The installation went off without a hitch. I'm ready to throw up my hands and call it quits as far as the Thinkpad goes unless someone has some "magic formula" for me.


Hey - I forgot to post my resolution for this issue...

Jump into your BIOS, check what your primary master drive is. It really helps if it's your HD. I couldn't install because my HD was set as my primary slave...

---

### Post by Nanoda on 2005-10-12
I had this error (and another previously regarding initrd-tools).  I did manage to eventually install, but did two things at once, so try each and let me know.

-Firstly, I did a complete format and re-burned my install CDRW at 2x.
-Secondly (I think this was the real solution) I used "hdparm -E" to reset the speed of my cdrom drive.  Just go to another console with Ctrl-Alt-F2 and type "hdparm -E n /dev/hdx", where hdx is your cdrom, and n is a number representing n-times regular audio speed.  I used 8 on my 32x drive and it worked.  YMMV, so try 1 or 0 if it's really not working for you.

---

### Post by sinistermilk on 2005-10-12
thats the problem i had/still have
deebotstrap error return "something" 27
/target/var/log/bootstrap.log
or atleast something very close to that

so how do we fix this?

---

### Post by dickohead on 2005-10-14
I'm currently trying to install Breezy, i successfully installed hoary, and was running it for months, but after a kernel problem i decided to format and start again.
I am getting returned with this error in Breezy's base system installation:
```

Base System Installation error
The debootstrap program exited with an error (return value 1).
Check /target/var/log/bootstrap.log for details.

```

But the file bootstrap.log does not exist, i tried changing my root partitions file system from Reiser to Ext3 but have the same error, i will attempt to skip the base install and let you know how that goes, but if anyone knows a work-around it would be much appreciated.

---

### Post by Cynos on 2005-10-15
[QUOTE=dickohead]I'm currently trying to install Breezy, i successfully installed hoary, and was running it for months, but after a kernel problem i decided to format and start again.
I am getting returned with this error in Breezy's base system installation:
```

Base System Installation error
The debootstrap program exited with an error (return value 1).
Check /target/var/log/bootstrap.log for details.

```

But the file bootstrap.log does not exist, i tried changing my root partitions file system from Reiser to Ext3 but have the same error, i will attempt to skip the base install and let you know how that goes, but if anyone knows a work-around it would be much appreciated.[/QUOTE]
Have any of the fixes mentioned here worked for you?

Keep an eye on the other consoles - Ctrl+Alt+F2 to Ctrl+Alt+F4; that'll give a more precise error message or two.

---

