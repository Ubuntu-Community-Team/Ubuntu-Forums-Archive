---
title: "GRUB problem--XP won't boot"
date: 2005-11-16
forum: Installation &amp; Upgrades
---

### Post by joseftu on 2005-11-16
I am a complete newbie. Let me say that right away.  I did a lot of reading, and tried to work with the Live disk, but my experience level is very low!

So here's the problem I had yesterday, that I'm hoping to avoid when I try again.

I have an IBM Thinkpad T43p, and I wanted to install Ubuntu and dual boot with Windows XP.  The Thinkpad has two partitions as it comes from the factory, one for XP, and one for the IBM Rescue and Recovery.

From various places, but particularly this page [http://www.columbia.edu/~em36/ubuntuhoarythinkpadt42.html](http://www.columbia.edu/~em36/ubuntuhoarythinkpadt42.html) , I learned that the way to keep the ability to use the "Access IBM" button during boot was to say "**NO**" to installing GRUB to the MBR--instead it was better to install it to " the first partition of the disk on which you install Ubuntu."

So I did that (after making a partition for Linux, and another for the Swap file).  I installed Grub to the partition where I had Windows XP. Everything seemed to go swimmingly, and Ubuntu installed and booted from Grub's dualboot menu with no problem.  

But when I tried to use the Grub menu to boot XP, it just went right back into the Grub menu.  I tried editing /boot/grub/menu.lst , with no luck.  

In frustration, I even tried to fixmbr (using the XP Recovery console).  But the machine still went right to grub, and still would not boot XP.  That grub would not go away!

In deepest frustration, I ended up just putting the whole system back to factory condition--reformatting and reinstalling Windows using the IBM recovery disks.

So now I've got my XP system back, but I still want to ultimately be able to Dual boot with Ubuntu.  This should be possible, right?  

Was my mistake just in saying "no" to installing grub to the MBR?  Should I try again and say "yes" this time, and everything will be fine?

I'm willing to take any suggestions anyone has!  I would like to figure this out--it's all part of my learning process.

Thanks

---

### Post by leezer3 on 2005-11-16
Hiya,
Quite typically, the IBM recovery is a joke, using some sort of custom bootloader as opposed to a BIOS hook. This means that by overwriting your MBR, you will loose access to the restore functions.
My apologies, but I'm not totally familiar with your model. If there is an option to burn recovery CDs somewhere in Windows, you should do this- This will allow you to install Ubuntu to the MBR, and still be able to restore Windows if necessary.
However, I don't think this is your problem. Other than going back to the menu, did Grub give you any error messages? Without knowing about any errors etc, my best suggestion would be to make the restore CDs, put Gub to the MBR, and have a look in the BIOS, and turn on LBA.
It might also be an idea to use something other than the Ubutu partitioner to resize the Windows partition, as it is not perfect yet and could have caused these problems.

Cheers

-Leezer-

---

### Post by jwd45244 on 2005-11-16
You said you installed GRUB on the first hard disk where you had Ubuntu installed. If Windows is in the rist partion and Ubuntu is in a later, I suspect you have not overwritten the MBR but overwritten Windows boot code that is in that first partition.

I am not exctly sure how to fix this.

---

### Post by joseftu on 2005-11-16
[QUOTE=leezer3]However, I don't think this is your problem. Other than going back to the menu, did Grub give you any error messages? [/quote]
No, no error messages at all. It just circled right back to the menu (in between it flashed, very briefly, a screen with what looked like the lines for Windows XP from menu.lst--but it was too fast to really read, and then right back to the menu.

[QUOTE=jwd45244]You said you installed GRUB on the first hard disk where you had Ubuntu installed. If Windows is in the rist partion and Ubuntu is in a later, I suspect you have not overwritten the MBR but overwritten Windows boot code that is in that first partition.

I am not exctly sure how to fix this.[/QUOTE]
That sounds very likely...so in that case the solution would be to just go ahead and put GRUB on the MBR as leezer3 suggests?

Thanks a lot, guys...this is giving me some helpful ideas.

---

### Post by leezer3 on 2005-11-16
Hiya,
DO NOT put Grub on the MBR unless you have another means of recovery other than that at startup!! If you have burnt recovery CDs or similar, then put Grub on the MBR, but the recovery will stop working.

Installing Grub on the first partion will not have done anything to the Windows boot files- It installs on the first Linux (ext3 etc.) partition that it finds, not Windows partitions.

Cheers

-Leezer-

---

### Post by joseftu on 2005-11-16
[QUOTE=leezer3]Hiya,
DO NOT put Grub on the MBR unless you have another means of recovery other than that at startup!! If you have burnt recovery CDs or similar, then put Grub on the MBR, but the recovery will stop working.

Installing Grub on the first partion will not have done anything to the Windows boot files- It installs on the first Linux (ext3 etc.) partition that it finds, not Windows partitions.

Cheers

-Leezer-[/QUOTE]
Oh ho. This is interesting. I think I told it to install specifically on sda1 (the first partition, if I figured right) which is where Windows was--not Linux.  If it automatically goes to the first Linux partition, why does it ask where it should go? 

And let me clarify about the recovery.  I do have a set of recovery CD's that I burned when I first got the laptop--if I put GRUB on the MBR, I can still boot from CD and recover that way, right? Just can't use the builtin recovery. 

Now, IBM has a separate, hidden, partition where they put recovery info--that's what you access (I think) by pushing the blue button at boot.  So if GRUB is on the MBR, I can't do that?  Then I could just wipe out that partition and use the CD's?

Thanks for the help very much--this is really a stretch for me, and I want to understand what I'm doing so I can understand what can go wrong (thought I understood that the first time...but clearly didn't!)

---

### Post by leezer3 on 2005-11-17
Sorry, I should have been clearer :rolleyes: 
If you tell it to put Grub on the first available partition, it will automatically skip the Windows partitions and use the first Linux partition. However, as you found, you can also specify precisely where you want it to go- Useful if you have multiple Linux installs.

By putting Grub on the MBR, you are effectively disabling your chance to push the blue button at boot and use system restore, and would have to use the recovery CDs you have burned instead. This would then allow you to wipe out the partition and use the space, but unless you are short on space I would tend to leave it- The function can be recovered by running the IBM MBR recovery disk that you linked to earlier, and I'm not sure if it will do this if you totally reinstall from the CDs. You also want to bear in mind that CDs can be lost or damaged, and if you can't use the IBM recovery in this case you could be in trouble.

Cheers

-Leezer-

---

### Post by jwd45244 on 2005-11-17
OK,  There seems to be some confusion as to how XP boots.

1) The MBR (or exctly 446 bytes of the mbr) "boot" and that code normally boots NTLDR.SYS

2) NTLR.SYS read C:\boot.ini (a hidden system file).  Thay has a line that tells NTLDR.SYS where the XP Chainloader code is (normally the first partion of the first hard drive).

It sounds as if you have written the GRUB boot code into the XP chainloader spot. So the MBR boots, fires up ntldr.sys it reads c:\boot.in which say run Windows and find the intialization code at partion 1, your Grub is ther so you see the GRUB menu. ad infinitum.

Should Grub be allowed to overwrite your XP chainloder code?  Probably not, but it can if you tell it to.

In my dual boot systems, I always creat a 10-20 gb FAT32 partition (so I can share files more easily.  I put grub in that partitions and then use dd to copy those 446 bytes to a file on that partion called something like linux.run or somesuch.  The in XP, I attrib -r -s -h c:\boot.ini and if XP sees my FAT partion as D: I add a line into c:\boot.ini that reads: 
d:\linux.run='Ubuntu Linux'

---

### Post by joseftu on 2005-11-17
Thank you, guys.  This is looking a lot clearer now.  I think you've hit exactly on what I did wrong, and (after a little more research--and an image of the restored machine so I don't have to reinstall everything one more time if I screw up again) I want to give it another try...maybe even this weekend (it beats writing the two articles and six course descriptions I'm supposed to have done by Monday!).
:)

---

### Post by leezer3 on 2005-11-18
[QUOTE=jwd45244]OK,  There seems to be some confusion as to how XP boots.

1) The MBR (or exctly 446 bytes of the mbr) "boot" and that code normally boots NTLDR.SYS

2) NTLR.SYS read C:\boot.ini (a hidden system file).  Thay has a line that tells NTLDR.SYS where the XP Chainloader code is (normally the first partion of the first hard drive).

It sounds as if you have written the GRUB boot code into the XP chainloader spot. So the MBR boots, fires up ntldr.sys it reads c:\boot.in which say run Windows and find the intialization code at partion 1, your Grub is ther so you see the GRUB menu. ad infinitum.

Should Grub be allowed to overwrite your XP chainloder code?  Probably not, but it can if you tell it to.

In my dual boot systems, I always creat a 10-20 gb FAT32 partition (so I can share files more easily.  I put grub in that partitions and then use dd to copy those 446 bytes to a file on that partion called something like linux.run or somesuch.  The in XP, I attrib -r -s -h c:\boot.ini and if XP sees my FAT partion as D: I add a line into c:\boot.ini that reads: 
d:\linux.run='Ubuntu Linux'[/QUOTE]

Precisely, but you haven't seen the whole picture- IBM installs a custom MBR & Windows loader to allow it to run its system restore functions. Ubuntu shouldn't have been able to overwrite the XP chainleoader code, as it will only normally install to Linux partitions, and should automatically skip Windows ones.

Also, I would not reccomend attempting to use the MS bootloader to run Linux from- It causes more trouble than it's worth.

Cheers

-Leezer-

---

### Post by gilbartdon on 2005-11-19
So, after reading the above How do you install Ubuntu to the other hard drive if XP is on the first hard drive??? So Leezer says not to use MS boot loader!

---

### Post by leezer3 on 2005-11-21
[QUOTE=gilbartdon]So, after reading the above How do you install Ubuntu to the other hard drive if XP is on the first hard drive??? So Leezer says not to use MS boot loader![/QUOTE]
Hang on, you're confusing everyone, please don't hijack someone elses thread :)
To answer your question, you would need to install Grub on your first HDD, or switch them around, so that the Linux HDD is the primary. To install Grub on the first HDD, you would need to create a separate partition to hold Grub as it won't install on windows partitions.
Or are you referring to two different partitions (One disk)- This is different.

Cheers

-Leezer-

---

### Post by joseftu on 2005-11-23
Well, it all worked perfectly! Thanks again.

I've got a dual boot system, with grub *not* in the MBR, and everything strong and successful, both ubuntu and xp booting as needed.

Now I've got some (more) ubuntu learning to do!

---

### Post by ikki_72 on 2005-11-23
it's weird that when i installed grub on mbr it displayed both my xp n ubuntu, but not with lilo. um...lilo is the gui boot chooser right?:cool:

---

