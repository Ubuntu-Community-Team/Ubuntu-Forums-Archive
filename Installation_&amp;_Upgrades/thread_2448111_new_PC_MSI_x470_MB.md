---
title: "new PC MSI x470 MB"
date: 2020-08-02
forum: Installation &amp; Upgrades
---

### Post by oneleded on 2020-08-02
i have to put an OS in, an i'm gonna stick with lubuntu. plus i have to put in the drivers. i cant seem to log onto the MSI site, of forum, which would be nice. first;
a list of what i got;
MSI x470 Gaming Plus Max
Be Quite mid-tower ATX case 600
Sabrent Rocket Q 1TB NVMe PCIe M.2 2880 SSD
AMD Ryzen 5 1600af
EVGA GeForce GT 1030 @GB Low Profile Video Card Gddr5
Crucial Ballistic 3200 MHz DDR4 DRAM 16GB(8GBx2)
EVGA supernova 650G3 gold power supply
250 HDD barracuda from before. i plan on using XFS file system, and having mutable drives, but not near as many as this could hold.
i might put in Windows 10, because some sites call for it. they cant handle Linux
Thats where i'm at now, formatting SSD, adding lubuntu, and drivers.

---

### Post by ActionParsnip on 2020-08-02
What messages do you see when you try to log into the forum? What browser(s) have you tried?

---

### Post by oneleded on 2020-08-02
i haven't loaded the SSD drive yet fist time i did OS from scratch.
i'm not sure if i want my HDD 1st, it has Lubuntu, and Puppy already on it.

---

### Post by oneleded on 2020-08-02
^bump^

---

### Post by oneleded on 2020-08-05
I read this [Installing and booting Windows 10 from a solid state drive], and it is related to my problem. installing Windows10. my 1st.drive is SSD. i read it doesnt like temp. files, so i gonna install a 2nd. drive HDD for temp, files. i think i now would be better off, installing my ubuntu/linux dristo's on the 1st. drive SSD, Windows 10, on the 2nd. drive HDD, and making space for temp. files there also.
Windows 10 responds to grub 2 win..  sooo, i should be able to do the same king of setup i got now. ubuntu and linux on the 1st. drive, windows XP on the 2nd. drive..

---

### Post by CelticWarrior on 2020-08-05
Any current solid state drive will last as much as if not more than traditional mechanical HDDs. The temporary files issue is a non-issue. The SSD will very likely outlive the computer itself.

And any OS installed in a HDD, regardless of how powerful the rest of the machine is, will suffer from a tremendous bottleneck effect, i.e., it'll be noticeably slow and very much so.

---

### Post by oneleded on 2020-08-05
> **CelticWarrior said:**
> Any current solid state drive will last as much as if not more than traditional mechanical HDDs. The temporary files issue is a non-issue. The SSD will very likely outlive the computer itself.

And any OS installed in a HDD, regardless of how powerful the rest of the machine is, will suffer from a tremendous bottleneck effect, i.e., it'll be noticeably slow and very much so.

i hate to here that. should i go ahead and in stall windows 10 on the ssd drive?, or since i will only use windows 10 on occasion, install it on the HDD drive?

---

### Post by CatKiller on 2020-08-05
CelticWarrior has correctly said that it's not something to worry about any more, but I'll also explain what the issue was.

It's not that any drive "doesn't like temp files," it's that drives have a finite lifetime.

Hard drives have mechanical parts, and all mechanical parts wear out eventually. Since people have been making hard drives for a very long time, hard drives now are able to have a long life before they eventually fail. Using them more heavily means that they'll wear out more quickly.

SSDs don't have any mechanical parts, so they don't wear out. However, the underlying technology - cells of flash memory - can only be written to a fixed number of times before it can't be written to any more. When SSDs were first introduced, this number was quite small, and, since they were expensive to make, putting more cells on would have made them unaffordable. Hence all the advice about avoiding putting temporary files on SSDs, to reduce the number of writes and extend the lifetime.

Now, though, flash cells last a lot longer and are much cheaper to make. Drives now have spare cells (called overprovisioning) so that if some cells can no longer be written to those cells can be mapped to the spare ones and the drive will just keep working.

We passed the point where the expected lifetime of an SSD is as long as the expected lifetime of a hard drive a couple of years ago.

You still might want to avoid unnecessary writes - not saving the last time a file was accessed (noatime) is still useful, for example - but drive lifetime isn't the overriding concern that it used to be.

---

### Post by CatKiller on 2020-08-05
> **oneleded said:**
> i hate to here that. should i go ahead and in stall windows 10 on the ssd drive?, or since i will only use windows 10 on occasion, install it on the HDD drive?

We can't tell you what you *should* do. If you install Windows 10 on a hard drive it will be a lot slower than if it was installed on an SSD. How much that will bother you is something that only you can decide. Similarly, how separate you want your OSes to be, and how much you want to play with partitioning, is entirely up to you.

---

### Post by oneleded on 2020-08-06
i dont expect ya to tell me what to do. is there any advantage, to keeping a (Windows 10) in this case, or a temp file system, on a separate drive. 1 TB SSD should outlast me. [i got gray/bald in my old age. still got some hair left on the sides/;~}] other than that, i might need ta know how big ta format the partition on some occasions i need a windows OS. as long as it doesnt bottleneck the SSD, i have no problem. putting it on another drive. for that matter, i also dont have a problem putting it on the SSD drive. I should have a lot of extra space on the SSD to spare, even at 1TB. IDK

---

### Post by CatKiller on 2020-08-07
Were it my computer, and if I hadn't stopped using Windows 15 years ago, I'd put both OSes on the SSD and use the HDD for data, like media files and regular backups. I understand that Windows 10 struggles to apply updates if it has less than 64 GB to play with, so I'd make its install partition at least that big.

Data that needed to be accessed from Windows I'd use a Windows-native filesystem for, since Windows is bad at accessing anything else but Linux can access them, but I wouldn't use that for anything I didn't have to since Windows-native filesystems are kinda crap and can only be prevented from eating themselves from within Windows.

YMMV.

---

### Post by oneleded on 2020-08-07
at least what im trying to build. is 64 bits., i didnt upgrade windows since XP. i couldnt, and didnt want to understand past XP.,... a different operating system, that ya pay for, that exploit's ya. well, everyone is entitled to there own views. if this dont belong here, please edit. i had intentions of making the windows 10 file, NTFS, or whatever it use's now.  only because i need it to access some medical sites. other than that, i dont need Windows10 at all. nor care. maybe i can get by with internet explorer. it's weird too. ed

---

### Post by oneleded on 2020-08-07
administrators and moderators are welcome to correct me, anytime they want. i expect it. come to think of it., if someone, needs me to be correct, they are welcome as well. i can only be so correct., but, i will try my best. ed

---

### Post by CatKiller on 2020-08-07
> **oneleded said:**
> only because i need it to access some medical sites. other than that, i dont need Windows10 at all. nor care.

You might be able to just spoof the browser's user agent string so that it thinks you're on Windows. Otherwise, if it's just one or two applications that you'd use Windows for, using a Virtual Machine would probably be more manageable than having Windows installed directly.

---

### Post by oneleded on 2020-08-08
i've been thinking about that since it was first mentioned to me. 2016, or 2017. cant remember who said it. i did look up hard drives, an tried to find quite ones. i cant believe how inexpensive they are. [old horse]. most the junk i got is pretty obsolete. tis a wonder it lasted this long. i'll look up my old threads. it was a while back, but i remember it. anyway the loudest thing i got on the old Dell[2002], is the fan in the power supply. the other one is super slow. a drop of turbine oil, might get it going again. still runs cold. ZOOM SPOUT. I think its about $5 dollars U.S. with shipping, an comes in 4 oz. saved many a power supply fan. even the one's from radio shack. i still got 3.98 OZs left. stuff last.
Didn't mean to ramble on so., i can get HDD for under $50.oo, in the terabytes. 5-16TB or higher. an i dont have that much stuff, i want to remember. ;~}

---

### Post by oneleded on 2020-08-08
it took a bit, Cmcanuity, was the 1st. i believe to tell me about vertial box. Nov/03/2018. ;~}

---

### Post by oneleded on 2020-08-11
it's taken a while to get me this far. if not for this forum, i would have never got here. :-), i dont want to state the obvious, but it is so. i still have questions,
 hope i always do. anyway, just ta show you some picts. been a while since i posted pictures. i might still have it. ;~}
should run cool, 4 fans. an its in the basement, sometimes it gets below 58F, in the winter. i leave windows open in the summer. if i didn't, it wouldnt get above 64F.
cold for me. just a thing.

---

### Post by oneleded on 2020-08-11
> **CatKiller said:**
> You might be able to just spoof the browser's user agent string so that it thinks you're on Windows. Otherwise, if it's just one or two applications that you'd use Windows for, using a Virtual Machine would probably be more manageable than having Windows installed directly.
i think i like this. 
the more i learn about modern HDD's, the less i know. right now, i'd say, the loudest noise i got, is the power supply, in a 2002 Dell. at least thats the sound i think i hear. surely it cant be the drive, can it? like the DVD or the RW drive? right now, the 2002 Dell is making noise, the fan in the power supply is not running like it should, nor the fan, that draws heat off the MB. only the processor fan.

---

### Post by CatKiller on 2020-08-11
> **oneleded said:**
> anyway, just ta show you some picts.

Looking good!

> **oneleded said:**
> right now, i'd say, the loudest noise i got, is the power supply, in a 2002 Dell. at least thats the sound i think i hear. surely it cant be the drive, can it? like the DVD or the RW drive?

Optical drives are really noisy.

If you've got a noise that you can't locate the source of, the quick-and-easy method is to stick a bendy straw in your ear. Not all the way, obviously. That makes your hearing much more directional, and then you wave the other end near the likely sources to see which is loudest.

> right now, the 2002 Dell is making noise, the fan in the power supply is not running like it should, nor the fan, that draws heat off the MB. only the processor fan.

You'll probably (different motherboards expose different settings) have settings in the UEFI to control the fan curve profile: how fast each fan should be going for a given temperature. The Wraith cooler in my other half's computer was fairly loud by default.

Also, if that machine's been running since 2002, some squirts of compressed air to get the dust out is overdue.

---

### Post by oneleded on 2020-08-16
sometimes the stuff you guys teach me sinks in. it might take me a while, but it does. i appreciate the effort.   ;~}

---

### Post by oneleded on 2020-08-29
on the boot, how big should i make the partition? it seems to double every so often.. some sites recommend, 100-200 Mib, others more. it wont be too long it's gonna get bigger.  i was thinking 1 or 2 GB should last a while. on the ssd drive. Got 1TB, on the ssd drive. 
just a funny' i didn't know that 5.25 drives, arent made anymore, til the other day.
the PC see's both the SSD, and sda/HDD.
/dev/nvme0n1 for the SSD 
/dev/sda for the HDD
not much advice out there, course, i dont ask the right questions.
ubuntu / linux, should be just fine, on the SSD. i may have to get 2 more memory cards, to match the ones i got, while they still make them.

---

### Post by CatKiller on 2020-08-30
I think I went for 500 MB for the EFI System Partition on my last install, on the grounds that I didn't want it to be too small (one of the Ubuntu releases, maybe 14.04, had quite a small ESP but also didn't autoremove old kernels, so everyone ran out of space) and, like you, I have plenty of space to spare. I think each kernel only needs tens of MB in the ESP.

---

### Post by oneleded on 2020-09-04
2x500 MB =1GB least i understand, it dont hurt to plan ahead. i just wonder if's its enough. course, i started with a small 1TB SSD drive.
after the KY Derby, i'l work on it, [dont want to have the system down]. information is growing so fast. its hard to keep up. always has been. i dont know if exponential covers it.

---

### Post by oneleded on 2020-09-09
Well; the Derby is over. i lost the $6.oo i bet on the trifecta. now to business. the Sabrent Q i bought dont support linux, or ubuntu. so i contacted the company, got a response the next day., using just email. i was told as long as linux works, it should be OK to use XFS.
[i left out the part where ext4 is supported, an some earlier versions, ext2].
mostly Sabrent is Windows10, 64 based. they will have to get used to that, [gotta start somewhere], but, i think they will come around., at least they list what you will need, in my case, xsfprogs, xsfdump..  then the other file systems, that are listed also. i found that out by using GParted/ view/ file system report. there is much to learn. also
i did learn my HDD, drive with 32 bit XP, will no longer work, on 64 bits, plus, its gotta lot of heat, to throw out in that 5.25 hdd drive.

---

### Post by oneleded on 2020-09-16
i got the lubuntu 20.04 amd64.iso some time ago and put it on disk. now i'm trying to use the checksum, and i have some problems. the iso, is on the desktop, but its a zip file. i un-zipped to the desktop, so i might be able to write a path for this, md5sum.txt. 
the other, SHA256sums, i can find it online, i just cant copy and paste. somehow, i dont have permission, to create a folder anymore.

---

### Post by CatKiller on 2020-09-16
> **oneleded said:**
> the iso, is on the desktop, but its a zip file.  

Are you sure, or is it that the program that can open zip files can also open iso files? 

> somehow, i dont have permission, to create a folder anymore.

Iso files, being an image of a read-only filesystem, are read-only. That also translates to iso images burned onto a thumb drive, although some burning programs will choose to ignore that and still allow the resulting filesystem to be writable.

---

### Post by oneleded on 2020-09-17
hey; when you right click, a page shows the .iso files, an you have to option to extract them.
when i right click, on the desk top to make a new folder, i dont have permission. i was trying to copy and paste  SHA256sums to a new folder, which i cant create any more.
i'll look online and in this forum to see if i can find something.
i should ask ''How to make a new folder on the desk top, when i dont have permission too'', that is where it belongs. or ''why dont i have permission to create a new folder on the desk top?'', give me a couple of days or so, on this one.

---

### Post by oneleded on 2020-10-25
i got the "lubuntu 20.04 amd64.iso" some time ago. i installed it on the SSD. 
before this, i was using lubuntu 18.04 32 bit, on HDD drive.
here's my problem, i cant access the HDD drive. i need a module. 20.04 says so, i dont know what i need, per say. i'd still like access to the HDD.
anyway, 20.04 is working well so far. i wish i had installed it months ago. 
i ran into verification problem's as far as the iso. finally figured it out, to my satisfaction.

i want to put fassapup on one of the partitions, a frugal install, but i havn't figured out how yet. it sorta was easier to verify the iso. the install is complicated to me. puppy
grew up.
supposedly, it runs 10 time faster with a frugal install. who am i to doubt this.

---

### Post by oneleded on 2020-10-31
i have lubuntu 20.04 on the SSD drive at last. grub wont let me access my HDD drive.
Grub 2.04 says i have to; load kernel first. it says more than that, but i didnt write it down. not enough time. i didnt have my camera ready.
next time i boot i'll be ready. lubuntu 20.04 is on /dev/nvme0n1p4

---

### Post by oldfred on 2020-10-31
Looks like you have mixed the now 40 year old BIOS/MBR configuration with the now 8 year old UEFI/gpt configuration. 
Windows has required vendors to install in UEFI boot mode to gpt partitioned drives since Windows 8 released in 2012. So all new hardware is UEFI. 
Some early UEFI had issues, most are resolved.

Even if new system, have you updated UEFI and updated SSD firmware? 

But your SSD is UEFI and does not show an extended partition so gpt.
But your HDD shows an extended partition and not ESP - efi system partition so BIOS/MBR. Or maybe UEFI boot thru gpt drive and only BIOS on HDD?
Best with new systems to only use gpt.

I started converting drives to gpt in 2010.
GPT Advantages (older 2010 but still valid)  see post#2 by srs5694:
[http://ubuntuforums.org/showthread.php?t=1457901](http://ubuntuforums.org/showthread.php?t=1457901) & 
[https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT](https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT)
[http://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface](http://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface)

You should always be booting in UEFI boot mode. The setting on booting in UEFI/BIOS is only for installed systems.
You have to select UEFI or BIOS each time you boot USB flash drive installer. And some tools that create installer make it only UEFI or only BIOS.
My system shows UEFI: PMAP or PMAP where PMAP is name/label of flash drive and one that is just PMAP is BIOS boot.

More info on UEFI in link below.

---

### Post by oneleded on 2020-10-31
theres no harm in taking out the SSD, is there? just wanted to double check.  i have to change lubuntu 18.04 to 64bits anyway, an the main thing i want to save is the bookmarks, and i got to copy my passwords.

---

### Post by oldfred on 2020-10-31
UEFI typically forgets boot entries for deleted drives, or converts them to something else, but not a valid boot entry.
You usually can boot the fallback entry which is a hard drive entry, not Ubuntu or Windows.
Many UEFI seem to find Windows UEFI entries, but not anything else. 
So you have to use efibootmgr to add correct entry or reinstall/repair boot loader.

Always have Ubuntu live installer or Windows repair disk available.

---

### Post by oneleded on 2020-11-06
i changed the HDD, to the same as the SSD drive, ESP/EFI.  [however, the motherboard has boot options i think that helped the most. and is new to me.( <thats not true)
never run across ten boot options before. my other pc only had 4. anyway, i ran into UEFI, near the bottom of the list, an decided to click on it for once,. it took me into bios, an the boot order, i went from there.
i took out the SSD drive some days ago, so i could use the HDD drive, as i was stuck. after 4 or 5 days i put it back in. it still works as it did, that was a surprise. now to update grub and see if it is in the order of my distros. i might still have things to do. if i didnt have things to do, that would be a surprise also.
vvvv

---

### Post by oneleded on 2020-11-10
i dont know why i change the boot order, i know better. boot order has nothing to do with it.

---

