---
title: "Dual Boot Help (Solved)"
date: 2005-10-17
forum: Installation &amp; Upgrades
---

### Post by New_Tux on 2005-10-17
I am trying to install Ubuntu on my computer without trying to install it over windows; I want a dual boot system.  I don't know how to make partitions or anything like.  I want to create a 7 GB partition for Unbuntu and keep the other 13GB for Windows. (20 GB total) Could someone please me!

---

### Post by aysiu on 2005-10-17
This is the best guide I've seen:

[http://users.bigpond.net.au/hermanzone/](http://users.bigpond.net.au/hermanzone/)

---

### Post by New_Tux on 2005-10-17
Thanks:p

---

### Post by GizzardBoy on 2005-10-17
This site does appear to be an excellent guide for many.  However, things did not turn out so rosy for me and now I'm stuck.  I had FC3 + WindozeXP in a dual boot config. on a single HDD, but each OS in it's own 30 GB partition on my wife's laptop.  Another 500 MB was configured as swap.  After several months, FC3 went flaky and died.  I decided to replace it with Ubuntu.  I tried the 5.04Live CD and it looked great.  I installed the 5.04version and now my wife's laptop says "Hard disk boot sector invalid".  I originally allowed Grub to install and then tried manually installing it on the Ubuntu partition when the automatic install failed.  Same result either way.

I now remember that the head IT guy at my wife's company had a simiilar problem when FC# was installed.  He installed Symantec boot loader to solve.  Can I use grub?  How can I at least get Windows to boot again?  I'd love to have Linux and Windows going, but it's late and I'm in big trouble in the morning if I don't get Windows running.

Thanks in advance for any help one can offer.

GB

---

### Post by Herman on 2005-10-17
[http://www.ubuntuforums.org/showthread.php?t=76652&highlight=install+grub+floppy+disk](http://www.ubuntuforums.org/showthread.php?t=76652&highlight=install+grub+floppy+disk)

 Here's some things you can try, (above link). This should give you pretty good instructions on how to restore GRUB, and even if you are still not able to do that, maybe you can try to install GRUB to a floppy disk and use it off the floppy disk. The instructions for that are there too. I haven't gotten around to trying that trick out myself yet, but I will soon. Good luck (from Herman.)

---

### Post by Herman on 2005-10-18
I made myself a GRUB boot floppy by following the instructions from the link given above to prove it works.  This was easier to do on my old reliable Hoary CD than it was with a Breezy CD though. I couldn't get the Breezy CD to do anything without actually formatting. 
The files on the floppy are invisible, so I had to try it out, don't just look on the floppy and give up when you don't see anything. And of course, to do this, you'll remember to set your first boot device to floppy in your BIOS.
 With the Hoary CD, which the instructions in the link were written for, you will get some pretty scary red warning screens, so it's a real nail-biter for newbies!
It might almost be simpler to just format the new installation and re-install it again, since in your case, (GizzardBoy), you won't have any files in it yet to care about losing.
 You could try again to see if GRUB can be installed to your MBR, (you might be luckier the second time), or choose 'No', and have it installed to a floppy this time. The advantage of having it on a floppy is if you have an older computer with 'Dynamic Drive Overlay' software (or some other software) in the MBR already (to enable an older BIOS to cope with a larger GB hard disk), that can get in the way of the GRUB boot loader and stop it from working from the MBR. So by having it on the floppy you get around that problem. That might not be your exact problem, but it's one example of a problem some people can have.  [http://www.pcguide.com/ref/hdd/bios/overDDO-c.html](http://www.pcguide.com/ref/hdd/bios/overDDO-c.html)
  Another neat thing about having you GRUB on a floppy is you can have improved security. Only those who know they need the floppy will be able to boot, and you can have a 'secret partition' that way!
Anyway, don't ever give up, and I know you will succeed as long as you keep on trying. (Herman).

---

### Post by GizzardBoy on 2005-10-18
Thanks for the responses.  I can see that I left out a critical piece of information.  This laptop does not have a floppy drive and it is fairly new (Pentium P4M with 1 GB RAM& 60 MB Toshiba HDD).

How do I even tell if I have an MBR anymore?  It never showed up as a separate partition during the two attempts at installation.  Please help.  I only have about an hour left before my wife wakes up and I am toast.

GB

---

### Post by GizzardBoy on 2005-10-18
A few more details that may help...
The laptop used to dual boot fine with a Symantec boot loader.  Grub is not working.

There are postings on the Fedora forums describing a similar problem that arose with FC2.  Is this the problem with Ubuntu as well- the difference in how some new Linux dists. vs. XP read drive geometry?

Thx,

GB

---

### Post by Herman on 2005-10-18
GB, I think you will need to think of a plan to divert your wife and avoid trying to do anything to any computer in a hurry and under stress. It's a recipe for disaster for sure. Always be calm and relaxed and never hurry when doing computer work.
 I think you'll be best off trying again to install GRUB to your MBR again either by trying the method on that link  or by re-installing Ubuntu if you haven't done so already. Re-installing just the new Ubuntu installation shouldn't take you very long on a fast new computer like that. Maybe you'll have better luck with GRUB the second time. I've had things go wrong with installing and simply done it again and everything went okay the second time. I don't know why, maybe a little dust on the CD maybe or something. 
Sorry but I don't know any instant cures. It's surprising how clever some of the others around here can be, but they often take a while to respond. 
Regards, Herman.

---

### Post by Herman on 2005-10-18
Or try your symantec boot loader then, I don't know anything about those, but if it'll get you out of trouble, the by all means!

---

### Post by Herman on 2005-10-18
GB I'm sorry I'm so slow, but I am working on your problem and I've done volumes of reading for you already to try to help get you out of the doghouse.
I _might_ have found something worth sharing at last:
[http://www.cyberwalker.net/columns/sep98/090398.html](http://www.cyberwalker.net/columns/sep98/090398.html)
You'll need a Windows 98 Boot Disk, my favourite is 'boot98c_seoem.exe' (without the inverted commas), you can find that on the internet and download one for free. It's a self extracting thing that installs itself automatically to a floppy disk when you double-click on it. You'll need to use a machine with a floppy drive for that. (Borrow one or ask a freind?), then copy the floppy to a CD maybe, since you don't have a floppy drive. In this way, hopefully you will get to use 'FDISK', which is one of the programs on the Win98 boot disk. From there you can follow the instructions on the link and at least (with luck and a little skill), get Windows booting again on your wife's laptop.
I don't like telling anyone to do anything I can't try myself to make sure it works, but I can't do that all the time. Please let us all know if this works as it might help others with similar problems.
At least it might get you part of the way to getting everything running again, you'll probably still need to re-install GRUB though, if you want Ubuntu, I'd imagine. Keep smiling!:D

---

### Post by Björn on 2005-10-19
now i don't know if the problem is solved but.. 
you said you tryed too install it on your ubuntu partition, but i think (as everything i say, i am not sure, just might be a hint in the right direction... hopefully=) )you have to install it on the first partition, which, if you installed windows first, should be that partition. Second, if you (for now) just wanted windows to work, have you tryed to restore the original windows MBR?

[http://www.microsoft.com/resources/documentation/Windows/XP/all/reskit/en-us/Default.asp?url=/resources/documentation/Windows/XP/all/reskit/en-us/prkd_tro_ldau.asp]("http://www.microsoft.com/resources/documentation/Windows/XP/all/reskit/en-us/Default.asp?url=/resources/documentation/Windows/XP/all/reskit/en-us/prkd_tro_ldau.asp")

i hope i am not talkin too much bullshit, which I might be because i neither have tryed it... ... or i simply got everything wrong from the beginning :P


/Björn
________________________________________________________________

Don't worry, nor sleep next to a kid who ate 5 cheeseburgers :P

---

### Post by Herman on 2005-10-19
That's an excellent link you posted on the subject, Bjorn. It should help some people. I think New_Tux was the one who added 'problem solved' in the title. GizzardBoy has not been responding, maybe he's just busy for a while or having a rest.
I'm still studying and practicing things to help him or others in his type of situation for the future. I'm trying to make GRUB copy to a CD and have been able to do this, but I get 'Error 6: mismatched or corrupt version of stage1/stage2' when I try to boot from the new CD. So I am working on that, but also have other things to do first before I get back to it. 
Can anyone offer some suggestions to get a GRUB CD that works? Has anyone been successful already in making one?
I have tried two ways: [http://www.gnu.org/software/grub/manual/html_node/Making-a-GRUB-bootable-CD_002dROM.html](http://www.gnu.org/software/grub/manual/html_node/Making-a-GRUB-bootable-CD_002dROM.html)
and:            [http://www.linuxquestions.org/questions/history/336446](http://www.linuxquestions.org/questions/history/336446)
                                       (Herman)

---

### Post by Emerzen on 2005-10-27
I don't know if this thread is still active, but I saw Gizzardboy had cross-posted for help.  I would boot up a LiveCD and at prompt type:

**sudo fdisk -l**

figure out which drive is the drive that your computer's BIOS is set to boot from, most likely /dev/hda or /dev/sda.  (your 1st drive).  Also, know what partition you have Ubuntu installed on in the /dev/sdx# format.

Pop in the install CD and reboot.  At prompt type '**rescue**'.  It will ask what partition you want to mount...mount the partition that has Ubuntu installed on it (should be ext3), your root partition that is.  When prompt comes up, type:

**grub-install /dev/whatever is your first drive** (do not specify a partition #).

For example, 'grub-install /dev/hda'

Then reboot...you may need to readd Windows to your grub menu, sometimes it picks it up automatically.  If this doesn't work, your MBR is messed up and you'll need to search on 'fixmbr'.

---

