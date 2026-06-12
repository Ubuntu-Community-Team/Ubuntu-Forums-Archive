---
title: "Question regarding installation"
date: 2008-11-25
forum: Installation &amp; Upgrades
---

### Post by Aralhach on 2008-11-25
I am thinking of using Ubuntu or one of its variants on my PC.  However, the hard drive is full.  Therefore, I was thinking of buying another hard drive, and hooking it up to the computer.

Would it be possible to have 2 physical hard disks, with the new disk having a Ubuntu part and a Windows part?  I mean, the one I have now would be all Windows, and the new disk would be part-Windows part-Ubuntu.  Would the installer detect my Windows installation on the other hard drive and put it in the GRUB?

I'd appreciate your answers.

---

### Post by VastOne on 2008-11-25
Yes it will.

I am curious as to what you mean by the new drive being "part windows"...Do you mean shared space for shared files?

VastOne

> **Aralhach said:**
> I am thinking of using Ubuntu or one of its variants on my PC.  However, the hard drive is full.  Therefore, I was thinking of buying another hard drive, and hooking it up to the computer.

Would it be possible to have 2 physical hard disks, with the new disk having a Ubuntu part and a Windows part?  I mean, the one I have now would be all Windows, and the new disk would be part-Windows part-Ubuntu.  Would the installer detect my Windows installation on the other hard drive and put it in the GRUB?

I'd appreciate your answers.

---

### Post by caljohnsmith on 2008-11-25
Sure, you can install Ubuntu to your external drive. I would highly recommend installing Windows first on that drive, and then Ubuntu, to save potential hassle with reinstalling Grub (Ubuntu's boot loader). If you want you can use Ubuntu's partition editor gparted to set up your partitions prior to installing Windows/Ubuntu; if you boot your Live CD, the partition editor is under System > Admin > Partition Editor. You might also find this tutorial helpful:

[http://www.herman.linuxmaniac.net/p22.html](http://www.herman.linuxmaniac.net/p22.html)

Let us know how it goes or if you have more questions. :)

---

### Post by Aralhach on 2008-11-26
First of all, thanks for your answers!!

I was thinking of buying another internal hard drive (I think I have more than one HD port).  What kind of hassle would I have and why would I need to reinstall the GRUB?  Thanks for the tutorial! I'm reading it.

I was thinking of having 2 internal hard disks.  The one I have right now is 100% Windows (and quite full :) ) Now, I'd like to buy another hard drive, and partition that into 2 parts (or maybe more, but divide them into 2 groups).  One part of the hard drive I'd want to be NTFS (for Windows to use) and I'd want the rest to be ext3 for Ubuntu (including swap and all that).  I was also thinking of creating a FAT32 partition for data transfer from Linux to Windows (I heard that it's pretty risky to write in NTFS with Ubuntu).

Sorry for not being very clear.

Thanks again for answering!!

---

### Post by caljohnsmith on 2008-11-26
> **Aralhach said:**
> First of all, thanks for your answers!!

I was thinking of buying another internal hard drive (I think I have more than one HD port).  What kind of hassle would I have and why would I need to reinstall the GRUB?  Thanks for the tutorial! I'm reading it.

If you install Windows to a drive that has Grub installed as the boot loader, Windows by default (and by no other choice) will overwrite Grub so that you can only boot into Windows. So then you would have to boot your Live CD and reinstall Grub to the MBR (Master Boot Record) so you can boot Ubuntu again, and also add Windows to your Grub menu so you can boot Windows. It's not too big of a deal, it's just easier if you install Ubuntu after Windows so you don't have to reinstall Grub. :)
> **Aralhach said:**
> 
I was thinking of having 2 internet hard disks.  The one I have right now is 100% Windows (and quite full :) ) Now, I'd like to buy another hard drive, and partition that into 2 parts (or maybe more, but divide them into 2 groups).  One part of the hard drive I'd want to be NTFS (for Windows to use) and I'd want the rest to be ext3 for Ubuntu (including swap and all that).  I was also thinking of creating a FAT32 partition for data transfer from Linux to Windows (I heard that it's pretty risky to write in NTFS with Ubuntu).

Sorry for not being very clear.

Thanks again for answering!!
Linux in general doesn't have any problems reading and writing to NTFS partitions any more, so don't feel constrained to using a FAT32 partition. Anyway, keep us posted and let us know how it goes. :)

---

### Post by Aralhach on 2008-11-26
Well, I wasn't thinking of installing Windows to the new hard drive. I was thinking of letting Windows stay installed on the one I have now and install Linux in the new one and just partition NTFS space for Windows to use merely as storage space.

I'm getting the feeling that this won't be possible.  Would it be better to just migrate my data to the new HD and then install Linux on a partition in the old one (where Windows is already installed)??

Thanks again!!

---

### Post by caljohnsmith on 2008-11-26
> **Aralhach said:**
> Well, I wasn't thinking of installing Windows to the new hard drive. I was thinking of letting Windows stay installed on the one I have now and install Linux in the new one and just partition NTFS space for Windows to use merely as storage space.

I'm getting the feeling that this won't be possible.  Would it be better to just migrate my data to the new HD and then install Linux on a partition in the old one (where Windows is already installed)??

Thanks again!!
It's definitely possible to install Ubuntu to the new hard drive and get it booting just fine; many, many linux users have exactly that type of setup. :) One thing you should know though is that when you install Ubuntu, Grub will by default be installed to the MBR (Master Boot Record) of (hd0), also known as /dev/sda, which will be your Windows internal drive. The advantage of this is you don't have to do anything special to get the Grub menu on start up after you reboot, if all goes well. The big disadvantage is that your drives are dependent on each other for booting, so if anything happens to either of them (including simply disconnecting the Ubuntu drive), you will not be able to boot either Windows or Ubuntu.

Personally I would recommend installing Grub to the MBR of your Ubuntu drive, leaving your Windows drive untouched, and then set your BIOS to boot the Ubuntu drive on start up instead of the Windows drive. And of course you can add an entry in your Grub menu to boot your Windows drive. This has the advantage that if anything happens to either drive, you can still boot the other one; the drives are entirely independent of each other. If you want to do it this way, then when you get to the last stage of the Ubuntu installation, click the "advanced" button, and tell Grub to install to /dev/sdb or whichever is the new drive you are installing Ubuntu to. That's all there is to it.

Let me know if you run into any problems or have more questions. :)

---

### Post by Aralhach on 2008-11-26
Thanks a lot for your time!! It was an excellent explanation!

I haven't purchased a new HD yet, but will do so soon (with a RAM upgrade ;) )  I will post if I run into anything or get some other doubt...  Thanks a lot!!!!!

---

### Post by VastOne on 2008-11-27
Caljohn, 

great response...I am curious about this quote...

> **caljohnsmith said:**
>  One thing you should know though is that when you install Ubuntu, Grub will by default be installed to the MBR (Master Boot Record) of (hd0), also known as /dev/sda, which will be your Windows internal drive. 


I have 2 SATA drives and every time i install to the 2nd sata ( a new drive as you described) I get a new grub installed to that drive even though it is the 2nd disk..

Is this a natural thing with SATA drives or do you have another thought on it?

VastOne

---

### Post by caljohnsmith on 2008-11-27
> **VastOne said:**
> 
I have 2 SATA drives and every time i install to the 2nd sata ( a new drive as you described) I get a new grub installed to that drive even though it is the 2nd disk..

Is this a natural thing with SATA drives or do you have another thought on it?

VastOne
Well actually Grub lives in two places; Grub has its necessary boot files in some partition (usually either a /boot partition if you make one or the main Ubuntu partition), and then Grub also can be in the MBR of a drive so that drive will boot Grub on start up. But for Grub to boot on start up, it needs its necessary boot files (the Grub stage2 file and menu.lst) that are located in the /boot partition or main Ubuntu partition. So unless you tell the Ubuntu installer not to install Grub at all, then you will get Grub installed along with Ubuntu on your 2nd SATA drive, or in other words, you'll get a /boot/grub folder (or just /grub folder if it is a /boot partition) with all of Grub's boot files. The key is where you install the "other part" of Grub via the "advanced" button in the installer that I mentioned before; if you install Grub to the MBR of the same drive that has Grub's boot files, then that drive is independent and you can boot it directly. But if you let Grub install to the MBR of another drive (like your 1st SATA drive for example), then when you boot the 1st SATA drive (i.e. boot Grub in the MBR), Grub depends on the 2nd SATA drive for its boot files. Thus the drives depend on each other for booting. Does that hopefully answer your question or did I just make it more convoluted? :)

---

### Post by VastOne on 2008-11-27
Makes perfect sense...

It is easy to reinstall/reset grub to the first sata (part2) and copy over the settings from menulst of the 2nd install.

Tis a wonderful way of learning....

Thank you CalJohn

> **caljohnsmith said:**
> Well actually Grub lives in two places; Grub has its necessary boot files in some partition (usually either a /boot partition if you make one or the main Ubuntu partition), and then Grub also can be in the MBR of a drive so that drive will boot Grub on start up. But for Grub to boot on start up, it needs its necessary boot files (the Grub stage2 file and menu.lst) that are located in the /boot partition or main Ubuntu partition. So unless you tell the Ubuntu installer not to install Grub at all, then you will get Grub installed along with Ubuntu on your 2nd SATA drive, or in other words, you'll get a /boot/grub folder (or just /grub folder if it is a /boot partition) with all of Grub's boot files. The key is where you install the "other part" of Grub via the "advanced" button in the installer that I mentioned before; if you install Grub to the MBR of the same drive that has Grub's boot files, then that drive is independent and you can boot it directly. But if you let Grub install to the MBR of another drive (like your 1st SATA drive for example), then when you boot the 1st SATA drive (i.e. boot Grub in the MBR), Grub depends on the 2nd SATA drive for its boot files. Thus the drives depend on each other for booting. Does that hopefully answer your question or did I just make it more convoluted? :)

---

### Post by Aralhach on 2008-12-08
OK. I just got back from buying the new HD.  It's a 250GB SATA HD.  Now, first of all, I recall someone telling me about setting the HDs up as master, slave, etc.  I don't really know about this, so I'd really appreciate some information on this.

I have a 160 GB drive, which is all Windows, and almost full.
I just bought the 250GB one and I'd like it to have a Windows partition and an Ubuntu partition.  The Windows system files are on the 160 GB HD.  I understood why the drives would be interdependent for booting, but could you explain a little more specifically what option to modify to put the GRUB on the new HD (I would like them to be independant).

Thanks for your answers!!

---

### Post by caljohnsmith on 2008-12-08
> **Aralhach said:**
> OK. I just got back from buying the new HD.  It's a 250GB SATA HD.  Now, first of all, I recall someone telling me about setting the HDs up as master, slave, etc.  I don't really know about this, so I'd really appreciate some information on this.

As I understand it, master/slave setups are not relevant to SATA drives, only IDE/PATA drives, because each SATA drive gets its own channel; thus I don't think you'll need to worry about a master/slave setup. :)
> **Aralhach said:**
> 
I have a 160 GB drive, which is all Windows, and almost full.
I just bought the 250GB one and I'd like it to have a Windows partition and an Ubuntu partition.  The Windows system files are on the 160 GB HD.  I understood why the drives would be interdependent for booting, but could you explain a little more specifically what option to modify to put the GRUB on the new HD (I would like them to be independant).

Thanks for your answers!!
When you go through the Ubuntu installer, make a mental note of which drive you are installing to, i.e. whether it is sda, sdb, etc. Then when you get to the final stage of installation, click the "advanced" button, and then specify to have Grub installed to /dev/sdb or whichever is the drive you are installing Ubuntu to. That should be all there is to it as far as the installation goes. Once it completes successfully, reboot, set your BIOS to boot the new Ubuntu drive, and you should be all set. If not, let me know what problems you run into. :)

---

### Post by Aralhach on 2008-12-08
Thanks a lot!!  That was very straightforward.  Now, this might be a not so good question, but should I install Hardy or Intrepid?? :)  Which would you recommend?

---

### Post by caljohnsmith on 2008-12-08
> **Aralhach said:**
> Thanks a lot!!  That was very straightforward.  Now, this might be a not so good question, but should I install Hardy or Intrepid?? :)  Which would you recommend?
I would try booting the Intrepid Live CD and try it out first; if it looks like basically everything is working OK, I would go ahead and install Intrepid. If for some reason you have any problems booting the Intrepid Live CD or have problems once you boot into Intrepid, then you could go ahead and try Hardy instead. But I would definitely go with Intrepid if it works. :)

---

### Post by Aralhach on 2008-12-09
OK. I've got one last question before the installation. :)  Should I put the Windows partition first or the Linux partition first?

I'm thinking that I should probably put the ext3 partition first, but I'm not sure, and where should I put the swap?

---

### Post by caljohnsmith on 2008-12-09
> **Aralhach said:**
> OK. I've got one last question before the installation. :)  Should I put the Windows partition first or the Linux partition first?

I'm thinking that I should probably put the ext3 partition first, but I'm not sure, and where should I put the swap?
I guess I would go ahead and put the linux partition first, because there is always a possibility you might have an older BIOS that can't access anything on the HDD past either 8.4 GB or 137 GB, depending on how old the BIOS is. If your BIOS has that limitation, and if your linux boot files are outside of that range, then you won't be able to boot Ubuntu; you'll instead get a Grub error 18. Thus is if you install Ubuntu at the front of the drive, you have less risk of the boot files being outside of that range; it may not be necessary as we don't know if you BIOS has that limitation, but its better not to find out the hard way if you can prevent it I think. Also, be sure to give Windows a primary partition, not a logical one. I think I would set up your drive as follows:
```
1st primary partition = Ubuntu
2nd primary partition = Windows
3rd primary partition = swap
4th extended partition
   5th logical partition = personal files
```
That's just an idea, because there are lots of ways of doing it. Good luck and let me know how it goes. :)

---

### Post by Aralhach on 2008-12-13
Well, I finished installing a couple hours ago, and then ran the update thing (took a while :)  Anyway, the installation went smoothly.  I found that my Windows hard drive was detected as /dev/sdb and my new Linux HD was /dev/sda, so that went well.  Everything else looks great, and now I'm just setting everything up the way I like it and enjoying Ubuntu!

Thanks a lot for your help!!

---

### Post by caljohnsmith on 2008-12-13
I'm really glad to hear your installation went smoothly; cheers and have fun with Ubuntu. :)

---

