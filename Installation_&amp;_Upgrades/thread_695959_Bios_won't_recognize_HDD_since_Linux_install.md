---
title: "Bios won't recognize HDD since Linux install"
date: 2008-02-13
forum: Installation &amp; Upgrades
---

### Post by PlasticCup on 2008-02-13
A friend of mine was always very happy with Linux, so when I needed a Linux live cd to do some migration, I decided to go ahead and install Linux. Bad decision. Here's what happened.

Before: 2 x 320 GB hdd (Both WD Caviars, not bought at the same time), 1 Vista (boot) drive, 1 download drive. For sake of clearness, I will refer to the drives as "old" for the old Vista install drive (320 GB), "new" for my new 500 GB drive and "download" for the 320 GB download drive.

I got a new 500 GB hdd (also WD Caviar), and decided to migrate Vista to that disc, and make the other two into a joined download partition. I found a tutorial which involved a Linux live cd and the dd command, so I got the Ubuntu live cd, and used it to clone my Vista drive onto the new one. Everything looked fine, I could boot into it, no problem. 

Then I decided to use the Live CD to install Linux, to try it out. I booted into Linux Live and used Gparted to resize the Vista partition on the new hdd to all of the hdd - 2 GB (my friend told me Linux could be installed easily on a 1 GB partition, I made it 2 to be safe). I ran Install, which crashed at the end. I assume this was because of not enough space, so my friend told me to delete the Linux (ex3 and swap iirc) partitions, make 5 GB available and try again. So I did.

It worked fine, however it stopped working after I rebooted with only the new hdd with the other ones unplugged, to test before wiping the old ones (lucky I did that :/ ). Now it won't boot into GRUB at all, and neither the BIOS nor  Gparted even acknowledge the drive's existance.

Once I got lucky after having both the old and new hdds plugged in, but my relief turned to apprehension when I saw the information displayed in the BIOS. Suddenly the vendor of my new hdd had become "BzBzBzBzBzBzBzBzBzBzBzBzBzBzBzBzBzBzBzBzBzBz" and the size 571.0 GB instead of around 465. Now it won't be recognized anymore.

Is there any hope left?

---

### Post by ajgreeny on 2008-02-13
Unfortunately, I think you should have reduced the size of your Vista partition with Vista's own tools, as I'm aware some people have had problems when using gparted.  Whether that is the reason for your BIOS not seeing the partition/disk I really can't say.  Just for safety's sake I suggest you boot again into the live CD and see if you can at least get your Vista files backed up to an external USB drive or something similar.  Then even if things go totally to worms you will not have lost your valuable files.  This assumes, of course that your live CD will be able to read the disk that your BIOS seems unable to.  Having done that at least you would be able to reinstall both windows and Ubuntu if necessary.

Good luck, I hope it works out for you.

---

### Post by PlasticCup on 2008-02-13
Nope, Linux live won't recognize it either. Fortunately, the new hdd is merely a clone of the old one, with more space and an added linux partition, which I haven't done anything on cause it wouldn't boot. Unfortunately, I can't wipe it and reïnstall Vista/Linux, because it seems to be unaccessable.

---

### Post by RJARRRPCGP on 2008-02-13
> **PlasticCup said:**
> A friend of mine was always very happy with Linux, so when I needed a Linux live cd to do some migration, I decided to go ahead and install Linux. Bad decision. Here's what happened.

Before: 2 x 320 GB hdd (Both WD Caviars, not bought at the same time), 1 Vista (boot) drive, 1 download drive. For sake of clearness, I will refer to the drives as "old" for the old Vista install drive (320 GB), "new" for my new 500 GB drive and "download" for the 320 GB download drive.

I got a new 500 GB hdd (also WD Caviar), and decided to migrate Vista to that disc, and make the other two into a joined download partition. I found a tutorial which involved a Linux live cd and the dd command, so I got the Ubuntu live cd, and used it to clone my Vista drive onto the new one. Everything looked fine, I could boot into it, no problem. 

Then I decided to use the Live CD to install Linux, to try it out. I booted into Linux Live and used Gparted to resize the Vista partition on the new hdd to all of the hdd - 2 GB (my friend told me Linux could be installed easily on a 1 GB partition, I made it 2 to be safe). I ran Install, which crashed at the end. I assume this was because of not enough space, so my friend told me to delete the Linux (ex3 and swap iirc) partitions, make 5 GB available and try again. So I did.

It worked fine, however it stopped working after I rebooted with only the new hdd with the other ones unplugged, to test before wiping the old ones (lucky I did that :/ ). Now it won't boot into GRUB at all, and neither the BIOS nor  Gparted even acknowledge the drive's existance.

Once I got lucky after having both the old and new hdds plugged in, but my relief turned to apprehension when I saw the information displayed in the BIOS. Suddenly the vendor of my new hdd had become "BzBzBzBzBzBzBzBzBzBzBzBzBzBzBzBzBzBzBzBzBzBz" and the size 571.0 GB instead of around 465. Now it won't be recognized anymore.

Is there any hope left?

It appears that the HDD has failed. Looks like a bad HDD.

And more bad news, even the folks at HDD Guru probably will pronounce the HDD bad. 

([http://hddguru.com](http://hddguru.com))

---

### Post by jpbelauskas on 2008-02-13
i had the same issue dual booting winxp and ubuntu.  what ended up happening with me was that the partition manager placed grub on a completely different hard drive.  i set my bios to boot from that hard drive and grub came up.

---

### Post by Herman on 2008-02-13
[TestDisk Page]("http://www.users.bigpond.net.au/hermanzone/p21.html") 
TestDisk is a the best software I know of for fixing bad partition tables. You should do some reading first, but it's quite simple to use once you get the idea of it.

Regards, Herman :)

---

### Post by PlasticCup on 2008-02-14
@ JPbelauskas: Thing is, the one time I did manage to boot from it, GRUB worked fine (choosing the 500 GB new hdd as boot device), so it's unlikely it was placed on another disc. Plus, I have the hdds plugged in to the same sata ports as when it did work, but now it doesn't.

@ Herman, I haven't done that much reading, but when I do "CREATE" and then in the list of drives, the new one doesn't show up, that probably means it isn't detected, right?

---

### Post by Herman on 2008-02-14
> @ Herman, I haven't done that much reading, but when I do "CREATE" and then in the list of drives, the new one doesn't show up, that probably means it isn't detected, right?:( No, don't bother reading too much.  After reading your original most more carefully and thinking about it some more I think I agree with RJARRRPCGP. 
It appears as if you have some hardware or firmware problem in the hard drive's controller card probably. 
>  when I do "CREATE" and then in the list of drives, the new one doesn't show up, that probably means it isn't detected, right?
Yes, if it's not even detected there's probably nothing TestDisk can do in this situation, sorry for wasting your time.
Regards, Herman

---

### Post by PlasticCup on 2008-02-14
Don't be sorry for wasting my time, I came here because I thought "It's probably dead, but maybe soemone else knows hdd-cpr". Turns out cpr won't help, doesn't matter. It was worth a try.

---

### Post by Herman on 2008-02-14
Is it new enough to still be covered by any warranty?

---

### Post by PlasticCup on 2008-02-14
> **Herman said:**
> Is it new enough to still be covered by any warranty?

It is a week old. I only had time to connect it, migrate Vista, install Linux, and then it just stopped working.

---

### Post by Herman on 2008-02-14
I would imagine the hard drive manufacturer's quality control people would like to have that one back for examination. it wouild be more than worth  it for a reputable company to  exchanges one like that for another new one.
Try returning it to your computer store and see what they say. You might need to be prepared to fill in some forms.

If you want, you can take a look at it with Smartmontools first, which is a program you can temporarily intsall in the Ubuntu LiveCD, or use a Knoppix or System Rescue CD. it might be interesting to take a look, I would be extremely curious myself, smartmontools will take a look in the hard disk controller cards.s memory and see what errors have been recorded there, (if your hard drive supports S.M.A.R.T.). Or maybe you won't get any sense out of it due to the nature of the failure, you said earlier that your hard drive is reporting the wrong information to your BIOS and that seems to be integral with the issue. [Check On Your Hard Disks With Smartmontools]("http://users.bigpond.net.au/hermanzone/p20.html#Check_On_Your_Hard_Disks_With").

Regards, Herman :)

---

### Post by PlasticCup on 2008-02-18
I've been trying to boot into knoppix to use smartmontools, but it won't boot. It partially boots but then gives an error message along the lines of "Can't find KNOPPIX filesystem, dropping you to a limited shell." What should I do?

---

### Post by Herman on 2008-02-18
It sounds to me as if there might be a problem somewhere else then, maybe in your BIOS or in your motherboard or with your cables and sockets or . . . 

You might be able to plug the questionable hard disk into another computer to see if it's okay in another computer, or even just a different SATA socket in your motherboard and see if that makes a difference.

If you are a do-it yourself kind of person, (like me), you'll probably want to keep on trouble shooting by running tests and trying to boot, and unplugging or swapping various computer parts to try to determine exactly which part is faulty.

Or if you aren't the type of person who likes playing around with computer parts, I guess you'll need to take it to a computer repair shop and get someone to do it for you. 

Regards, Herman :)

---

### Post by PlasticCup on 2008-02-18
I built this PC myself, so I'd consider myself as the "do-it-myselfer" :D

Anyway, I've already done that before posting here, all configurations possible, none worked for the 500 GB hdd. The others both work, no matter what port they're plugged into. I also checked if the mobo had a problem with sata 1 OR 2 used (1 of them empty) and 3/4 both sata dvd-drives, so I unplugged the dvd drives, but that didn't help either. Something to note: the last time it worked the 500 GB hdd was in an extra sata slot between the pci-slots (a JMicron controller I believe). Maybe that had to do with something. 

Also, I read somewhere that a sata dvd drive wouldnt boot knoppix (just 1 site tho, w/o a solution, but I thought I'd mention it anyways)

---

### Post by Herman on 2008-02-18
Knoppix should boot even without any hard drive at all in the computer, it runs from CD, Knoppix is completely independant of hard drives, I have done it before.

---

### Post by PlasticCup on 2008-02-18
Yes I know, but I'm talking about a sata DVD drive, the one I put my Knoppix disc in. I read somewhere that the Knoppix live cd/dvd (I've tried both) won't boot from a SATA DVD drive. Is this true? If not, what can I do to make it work?

---

### Post by Herman on 2008-02-18
:) Knoppix was not made to be installed to hard disk, it's a LiveCD/DVD operating system based on Debian. Although, you can install Knoppix to hard disk if you really want to for some reason.
If you want to install Knoppix to hard disk, you will find it a lot easier to just install Debian instead, which is a distribution that was made for installing to hard disk, and should work well and be easier to install. When Knoppix is installed to hard disk it becomes Debian in any case, so why not do it the easy way?
You can install the same if not more software in Debian as you can in Knoppix, and choose either the KDE or Gnome Destop, and possibly other Desktops too.
Or you can choose Ubuntu, Kubuntu, Xubuntu, or any other *buntu, Ubuntu is also based on Debian, and you can install much of the same software as Debian. Ubunu works well from hard disks.

I hope you can find out somehow what's wrong with your computer and fix it easily, whatever you do.
I built one of my computers myself too and I think it's a great idea for those of us who can.  

Regards, Herman :)

---

### Post by PlasticCup on 2008-02-19
I'm not trying to boot from HDD, neither am I trying to install to HDD. I'm trying to boot from a sata **[SIZE="7"]DVD[/SIZE]** drive. IT WON'T WORK. I NEED HELP BOOTING THE CD/DVD FROM A DVD DRIVE. I DO NOT NEED TO INSTALL IT IN ANY WAY.

Sorry for capitalisation, but you just didn't seem to get the point.

---

### Post by trickytrickytricky on 2008-02-19
Just a thought, I had a similar problem pre linux days. You could try putting the hd into a caddy with a usb connection and try reading it from another pc as an ext hd. Don't forget to change the jumper though. If you don't want to go to the hassle of messing with a caddy you can buy a device that just plugs the hd into a usb connector (and then to the pc). Good for quick testing hd's.

---

### Post by Herman on 2008-02-20
>  Sorry for capitalisation, but you just didn't seem to get the point. Sorry for the misunderstanding, PlasticCup, now I see where I went wrong, I have never seen or heard of a Sata DVD drive before, so I misinterpreted your post completely. Please accept my humble appologies.
I have never seen or used a sata DVD drive, this is the first time I have known that such a thing exists, although now that I'm thinking about it. it sounds like quite a reasonable thing to imagine.
I don't know the answer to your question, sorry. 

Regards, Herman

---

### Post by froy02 on 2008-02-20
What's your motherboard, does it have Intel chipset?

---

### Post by PlasticCup on 2008-02-20
It's an Asus P5K (Intel P35 chipset iirc). I didn't, however, plug it into one of the 4 "regular" sata sockets, but in a 5th JMicron sata connection. This should not make a difference, but I thought I'd post it just to be sure.

---

### Post by whazooo on 2008-02-20
I have a sata dvd drive and it boots the gutsy live cd just fine.
I'll download a koppix iso and try it on the sata drive and let you know...

---

### Post by whazooo on 2008-02-20
Wont boot from knoppix cd on sata dvd

---

### Post by froy02 on 2008-02-20
> **PlasticCup said:**
> It's an Asus P5K (Intel P35 chipset iirc). I didn't, however, plug it into one of the 4 "regular" sata sockets, but in a 5th JMicron sata connection. This should not make a difference, but I thought I'd post it just to be sure.

Sure, it makes a difference...

---

### Post by PlasticCup on 2008-02-20
@ Whahzoo: hmm, okay. So no Knoppix for me. Ah well, I'll just send it in, too much hassle.

@ Froy: It does? What difference does it make exactly? Note: I plugged in the hdd we're discussing atm, not sure if that came across.

---

### Post by goofydawg on 2008-02-20
I had a similar problem with two HDD s ..  I did have three and then two and then swapped the last two from one ide channel to the other.... don't ask why...   anyway.   the bios no longer recognized the drives... after i went back into the bios and reset all the drives to autodetect it started working.    it seems like when one was unplugged  during some setups the bios got confused   ??   .   anyway... resetting the bios for each drive location to autodetect fixed the problem..

jim

---

### Post by froy02 on 2008-02-23
> **PlasticCup said:**
> @ Whahzoo: hmm, okay. So no Knoppix for me. Ah well, I'll just send it in, too much hassle.

@ Froy: It does? What difference does it make exactly? Note: I plugged in the hdd we're discussing atm, not sure if that came across.

I have a gigabyte DS3L-P35 motherboard with Intel chipset. For the bios to list the hard drives and CD-DVD drives, I had to disable the 'AHCI' function in the bios.  I then press f10 to save settings then when the boot menu comes out again I press 'delete' again to check that all the drives are listed in the bios.  I then again save the settings and let the computer boot. 
If I enable the 'AHCI' function, Windows XP SP1 does not see the CD-DVD drive at all but the computer would boot from the hard drive.  I could not test it with XP SP2 because that OS is installed in my other computer (ECS MB) thus I could not update to SP2 from Micro$oft for my gigabyte MB.
I am not even sure what the AHCI function does and I e-mailed gigabyte about it but I haven't received a reply yet.

Hope it helps you.

---

### Post by PlasticCup on 2008-02-27
I fixed it :D

Turns out my sata cable was faulty. I changed the port it was in etc. etc., but forgot to switch the sata cables. Turns out that was the problem, and the hdd was 100 % fine :D

---

### Post by netuser1234 on 2008-05-20
> **Herman said:**
> [TestDisk Page]("http://www.users.bigpond.net.au/hermanzone/p21.html") 
TestDisk is a the best software I know of for fixing bad partition tables. You should do some reading first, but it's quite simple to use once you get the idea of it.

Regards, Herman :)

--
Hi, everyone,
I have the same problems after I tried to install DSE Knoppix 3.4, which caused my hard disk completely disppeared. My hard disk became unstable after I tried and failed to install other Linux (Fedora Core 4) to a partition that created by resizing the Windows XP partition, which caused the Bios won't recognise the whole disk. Moreover, the Installation tools in SC Works 4.0 (from recent APC journal) were unable to fix the MBR and partition problems. Eventually, I used the Knoppix 3.4, which was able to boot from DVD drive and able to recognise the partition that Fedora failed to install in, but when I attempted to install Knoppix 3.4 in this partition, the system was done and the Knoppix unable to read that partition any more. 

I would be grateful if any one with your experties, able to advise my how to fix and reuse this hard disk.

Cheers.

Frank

---

