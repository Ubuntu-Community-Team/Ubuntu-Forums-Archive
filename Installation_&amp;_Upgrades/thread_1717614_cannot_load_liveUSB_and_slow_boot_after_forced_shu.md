---
title: "cannot load liveUSB and slow boot after forced shutdown"
date: 2011-03-30
forum: Installation &amp; Upgrades
---

### Post by calchal on 2011-03-30
Hi all,

I am new to this forum. I experienced what i perceive as the craziest thing during 2 years of using ubuntu. About some months ago, I have two ubuntu installed  on my HP-mini netbook: ubuntu 10.04 64 bit (CAElinux) and kubuntu 10.04, and run without problem. 

One day, the netbook's battery run out of charge and I forgot to plug it in. The ubuntu, as usual, went to hibernate, but without harddisk noise, so I forced it to shutdown by pressing power button (as i think it is not normal). What happened later was the partition of 10.04 was broken, it could not boot, it even affected another partition as the netbook couldn't boot kubuntu 10.04. 

I try to run liveUSB and CD of both distro and the liveCD/USB boot stopped on loading screen. So I try another linux distro: PCLinuxOS, which was able to boot but took very long time. The partition of ubuntu 10.04 could not be accessed. 

After installing PClinuxOS in replace of kubuntu, I scanned the ubuntu 10.04 partition and the partition was fixed, I could access the partition and could load to ubuntu 10.04, but it took very long time. Here how it loaded: first: blank screen with blinking cursor, then ubuntu load screen, then back to blank screen with blinking cursor, then it showed numbers and sentences, like some scanning works. It took long time before login screen appeared (about 10-15 minute, while the prevously normal boot time in my netbook was less than 1 minute), but once its done, the ubuntu worked normally. This also the case in the PClinuxOS and the reason it load very slowly.

After this, I try to boot the liveUSB of various linux distro, and found some could boot while the others not:

able to load with unusual slow boot time:
PClinuxOS (latest)
Ubuntu 8.04
Fedora (latest)
Linuxmint 8 (based on ubuntu 9)

can't load
ubuntu 10.04 and 10.10
kubuntu 10.04
latest linuxmint

The liveUSB boot could take 1 hour. I also try the latest Puppy, Gentoo and OpenSuse liveUSB but it couldn't boot, and it likely the liveUSB problem. I made the all the liveUSB with unetbootin. The ubuntu 10.04, 10.10, kubuntu and the latest linuxmint could not boot even after I scanned the ubuntu 10.04 partition. There was no problem with the liveUSB as it would load normally on another computer. I think it is just the variant of ubuntu 10 that is not being able to boot.
 
I was not content on this slow boot, so I try to format the two partition of ubuntu and PClinuxOS (there are another partitions though), and installed ubuntu 8. But it also happened to boot slowly as the previous ubuntu. Then I replaced it with linuxmint 8, and the same occurred. So I try to install windows on another partition, and it boot normally.

The question is, what is happening. Why do the forced-shutdown-of-ubuntu-10.04 affect another partition, to the boot of another distro? If my HD was broken, the Windows would load very slowly too right? Yes, in SMART Data (from disk utility) it showed "few bad sector", but i think this is not related to the slow boot. The ubuntu 10.04, 10.10, kubuntu and the latest linuxmint cannot boot until this moment. I am thinking there are some informations planted on my computer, that twist it to load some distro slowly, and prevent it to load some others. But where and what? (I almost arrived to the thought that this is supernatural!) ](*,)

Because of my long story up there (as I think it must be reported), the conclusion is: 
1. Ubuntu 10.04 on my netbook was forced shutdown (by me)
2. It caused the partition broken
3. After fixing the partition (by scan, but I forgot the command), it took very long time to boot, but the ubuntu itself run normally
4. It also affected the boot of another distro (slow down the boot time), but Ms.Windows boot time is normal
5. It also caused ubuntu 10 (and its variant) to not be able to boot from liveCD/USB
6. It also caused me going crazy

Now im gonna format the whole HD in hope of ubuntu 10.04 (and later) could boot again, but shall it fix the problem? (as formatting the previously ubuntu 10.04 partition did not solve the problem). Or should I buy another HD (or even computer) to install natty!!!???? :-( :-( :-(

I hope this problem would be fixed in the next release.[-o<

Thank you :(
ichal

---

### Post by mikewhatever on 2011-03-30
I would test if the hdd is the problem. Disconnect it's cables, and then try booting from a live cd/usb.

---

### Post by calchal on 2011-03-30
hmmm, it would be difficult for me to unplug the HDD in my netbook, but if it is the HDD, why does the ms.winblows boot normally? Does my mistake (forcing shutdown the ubuntu) affect the performance of HDD on ext format (and not on NTFS)? my problem is just with boot time (except for ubuntu 10 liveUSB), if it succeed boot to login screen, the OS will work normally

---

### Post by mikewhatever on 2011-03-30
That's an odd problem. Obviously, you can't remove the hdd, I must have missed the netbook part, sorry.

---

### Post by calchal on 2011-03-31
that's ok, its a long story though, im just confused why formatting the drive doesnt solve the problem and its just ubuntu 10, it is a crazy thing, whats happening with the boot process

---

### Post by mörgæs on 2011-03-31
This is a strange one. You could try erasing the disk completely with Killdisk to be sure that every trace of the old installation(s) is gone. After that, try a sole installation of Ubuntu 10.04 or 10.10 (without Windows) for testing.

[http://www.killdisk.com/](http://www.killdisk.com/)

---

### Post by mikewhatever on 2011-03-31
You could try looking at the dmesg log:
```
dmesg > ~/Desktop/dmesg.txt
```

That will produce a text file with the log on your desktop, and you can post is as attachment here.

---

### Post by calchal on 2011-04-01
> **mikewhatever said:**
> You could try looking at the dmesg log:
```
dmesg > ~/Desktop/dmesg.txt
```

That will produce a text file with the log on your desktop, and you can post is as attachment here.
This command produces what i mentioned above (the boot runs with some "scanning work"--i dont know). Thanks mike, i didnt know how to save the log during booting :D. Boot in my netbook ends with:

[  533.180212]  domain 0: span 0-1 level SIBLING
[  533.180219]   groups: 1 0

but in normal computer it would be:

[    2.658259] md: raid10 personality registered for level 10
[    2.835670] EXT4-fs (sda7): mounted filesystem with ordered data mode

It seems my netbook takes too many this "attempt" or "level" or whatever that is signed with number [  533.xxxx], normal computer just takes it 2, mine does it until 533, what does this actually means???

---

### Post by calchal on 2011-04-01
> **mörgæs said:**
> This is a strange one. You could try erasing the disk completely with Killdisk to be sure that every trace of the old installation(s) is gone. After that, try a sole installation of Ubuntu 10.04 or 10.10 (without Windows) for testing.

[http://www.killdisk.com/](http://www.killdisk.com/)
Thanks mörgæs, i'll try it, but does this kind of program has linux equivalent?

---

### Post by calchal on 2011-04-01
> **mikewhatever said:**
> You could try looking at the dmesg log:
```
dmesg > ~/Desktop/dmesg.txt
```

That will produce a text file with the log on your desktop, and you can post is as attachment here.

I forgot to attach the file, sorry :)
its too big for text file attachment so I compressed it

---

### Post by mörgæs on 2011-04-01
> **calchal said:**
> Thanks mörgæs, i'll try it, but does this kind of program has linux equivalent?

Please read the web site.

---

### Post by calchal on 2011-04-04
Hi,
I just found that ubuntu 10.04 liveUSB is actually capable to boot in my netbook, but it took very looooooooooooooooooooooooooong time, that it seemed fail to boot. And in installation process, it took unusual long time after selecting time zone and keyboard type. 

I am curious of the actual nature of this problem, is it such a big mistake to forcing shutdown the ubuntu? What's going on? :confused: :confused:

p.s. I am not yet formatting the whole harddisk using killdisk

---

### Post by calchal on 2011-04-05
I have solved this probleeeeeeeeeeeeeeeeeeeeeeeeeeeeeeeeeeeeeeeeeem!!!!!

I booted Natty beta liveUSB, and deleted the entire HD with Gparted, and then went to Disk Utility --> Format Drive --> MBR ---> ok. What happen next was the installation process (of Ubuntu Natty beta) went smoothly like dream, and the installed Natty booted very fast like a pig run, 10 s approximately!!!!!! (I will count it later, but it is what the Natty intro video told).:P I post this with Natty beta :grin:
I think the problem is the MBR, maybe it is the last that have to be formatted.

Now Im happy again, at last after nearly two months I can feel completely the beauty of ubuntu again, and reach the eternal spiritual tranquillity. 
 
Thank you very much Mike and Mörgæs for all your suggestion.:popcorn:

---

