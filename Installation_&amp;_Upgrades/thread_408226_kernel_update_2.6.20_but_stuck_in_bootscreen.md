---
title: "kernel update 2.6.20 but stuck in bootscreen"
date: 2007-04-13
forum: Installation &amp; Upgrades
---

### Post by graha on 2007-04-13
hi well the titles says it all. it was succesful update from here [http://ubuntuforums.org/showthread.php?t=311158&highlight=master+kernel]("http://ubuntuforums.org/showthread.php?t=311158&highlight=master+kernel")
can some one explain if i did wrong during the update ?

---

### Post by deeq on 2007-04-13
Same here. I ran autoupdate, restart and stuck in loadup screen.

---

### Post by glitchiron on 2007-04-13
I have the same problem.

---

### Post by deeq on 2007-04-13
> **kwagner said:**
> Same here!
Boot with the previous kernel, on your GRUB menu.

-Karl

[http://ubuntuforums.org/showthread.php?t=408225](http://ubuntuforums.org/showthread.php?t=408225)

---

### Post by graha on 2007-04-13
damn.i thought i was the only one with the same problem :(

---

### Post by Basz on 2007-04-13
Same here. Booting in older kernel is successful, yesterday's update broke something in 2.6.20-14 i guess?

When i switch to tty1 during boot, it just says 'loading... please wait'. Sometimes, but not every time, it mentions 'ata1.00: revalidation failed (errno=-19)' and then stops.
Recovery mode doesn't make any difference.

update: just tried booting without 'splash' and 'quiet'. ata_piix seems to report an enormous (incorrect) blockcount for my harddisk and thus fails to recover it...

---

### Post by sipior on 2007-04-13
My system is also experiencing this problem (ata1.00: revalidation failed (errno = -19)), after installing Feisty beta and then upgrading last night. Went to report the trouble on lauchpad.net, but the bug reporting mechanism is throwing up internal server errors atm (which I believe technically counts as irony). I'll have a go again later this afternoon.

Cheers,

Sipior

---

### Post by muncrief on 2007-04-13
Same here.  I was running Feisty AMD64 this morning but had to do a full clean reinstall because I corrupted it with some 32/64 bit compilation errors that resulted in library mix ups. I reinstalled from scratch, applied all the updates, and the system just froze at the boot screen. In recovery mode it just says there's been a hardware error and the kernel panics and dies.

It looks like the new kernel is remapping all the drives in a different order but the update doesn't configure correctly.

I used to have my DVD drive and CD-ROM drive mapped as /dev/hda and /dev/hdc, and my two SATA drives as /dev/sda and /dev/sdb.

I can see from the last few lines before the kernel panic that my sda drive is now considered to be scsi2 and my sdb drive is scsi3, so I'm assuming my DVD/CD drives have been mapped to scsi0 and scsi1.

However, after five hours of trying every combination under the sun in my boot and fstab configuration, I just can't get my system to boot with the new kernel. I have to use the old kernel, and I can see already that not all applications work with the old kernel after the update and I'm afraid of corrupting their configurations.

It looks like we're really stuck. I hope this gets fixed ASAP.

For reference, here's my hardware:

Gigabyte GA-K8N Pro-SLI Motherboard (Nvidia nForce 4 based)
Athlon 64 3000+
3GB Dual Channel PC3200 DRAM
Maxtor 6V200E0 Sata hard drive (sda, 120GB)
WDC WD1200JS-00MHB0 Sata hard drive (sdb, 200GB)
LITE-ON LH-18A1P DVD R/W drive
Sony CDU5221 CD-ROM drive
Nvidia 7800GT Video card
Hauppage WinTV-Go TV card

Here's my old drive partition map, I'm not sure what the new kernel is doing:

hda - DVD-RW
hdc - CD-ROM
sda1 - 20GB - Windows NTFS partition
sda2 - 2GB - Linux swap
sda3 - 20GB Linux ext3 / (this is the partition that was destroyed after the update)
sda4 - 70GB Linux ext3 /home
sdb1 - 95GB Linux ext3 /virtual (for virtual machines)
sdb2 - 95GB Linux ext3 /storage (data archive)

---

### Post by mhansen on 2007-04-13
> **muncrief said:**
> 

However, after five hours of trying every combination under the sun in my boot and fstab configuration, I just can't get my system to boot with the new kernel. I have to use the old kernel, and I can see already that not all applications work with the old kernel after the update and I'm afraid of corrupting their configurations.




Well, actually, you can still use the new kernel.  After 12 years of using Linux,  you'd think I'd keep at least one backup of an older kernel to use, but nope.

So, what I had to do was boot with the install disk, rename (i.e. mv) the initrd.img-2.6.20-14-generic.bak to initrd.img-2.6.20-14-generic and there you are, back to the pre-update kernel config.  Anyone who hasn't deleted all of their older kernel images doesn't have to boot with the install disk, of course...  Good game, Mike.  Good game.


Regards,
Mike

---

### Post by Basz on 2007-04-13
Too bad i already tried to re-install the kernel, thinking it was something i did wrong...

---

### Post by skopa on 2007-04-13
sorry for this :mad: :mad: :mad: :mad: :mad: :mad: :mad: :mad: (there were something like other 50 faces here but i cant get more than 8,too bad)
my pc is also stuck in bootscreen
AND THIS IS TOTALLY UNACCEPTABLE FOR A BETA RELEASE OF AN OS
I'M REALLY REALLY MAD FOR THIS
I HOPE THE DEVELOPER WHO UPLOADED THE KERNEL GOES FOR VACATION,PERMANENT
again,sorry for this
now,anybody,is there anyway getting past the bootscreen?

---

### Post by floke on 2007-04-13
Yeah it's pants.
Stuck right at the beginning of the orange bar.
Old kernel works fine though (AFAIK!)

---

### Post by Basz on 2007-04-13
> **skopa said:**
> sorry for this <smileyoverloadsnip> (there were something like other 50 faces here but i cant get more than 8,too bad)

And we're glad you couldn't. At least, I am. Must have taken you quite some time, putting in 50 smileys :twisted:.
> 
AND THIS IS TOTALLY UNACCEPTABLE FOR A BETA RELEASE OF AN OS

Please reread the definition of a beta release at [http://en.wikipedia.org/wiki/Beta_release#Beta]("http://en.wikipedia.org/wiki/Beta_release#Beta")
> 
I'M REALLY REALLY MAD FOR THIS

I can understand that. So am I. well... disappointed at least. But on the other hand I very much appreciate the loads of work the developers are putting into this great distro. Best so far, imho. And I'm sure they will fix this minor problem some time very soon.
> 
I HOPE THE DEVELOPER WHO UPLOADED THE KERNEL GOES FOR VACATION,PERMANENT

I'm guessing they would like that too very much, but they have a deadline to catch i'm afraid. Will find out bankaccount details for you, so you can donate something extra for their well earned holdiday.
> 
again,sorry for this

Better not do it again then, next time. :D 
> 
now,anybody,is there anyway getting past the bootscreen?

Ah, ontopic. Finally. Read the previous posts. At least 2 temporary solutions have been mentioned earlier on.
Having a rough day, aren't you? ;) Oh, and you have an error in your keyboard-config. Capslock seems to randomly come on sometimes... Please fill out bug-report. Thank you.

---

### Post by babuu on 2007-04-13
Same problem here, I knew I shouldn't have upgraded yet (BETA and it was my work computer =P), but I am always to curious.

I could boot the old kernel but then there was a version mismatch between Nvidia kernel module and the old kernel module. Don't want to mess that up, so I guess just have to wait for the kernel to be available with aptitude dist-upgrade. Luckily I have the laptop so I can do some work.

---

### Post by skopa on 2007-04-13
well basz i am mad for this because, apparently, this update was uploaded without any testing...
this i a beta version, meaning from my debian days, i guess it's a testing version? that has gone beyond the experimental phase? so it should work on most pcs and need something like just minor patches?? (and this doesn't seem to be the case)


> And we're glad you couldn't. At least, I am. Must have taken you quite some time, putting in 50 smileys .
it's quite easy to do 50 clicks, if you ever played any fps game that is(or strategy, or rpg, or ...), actually it took me more time to delete those smileys

---

### Post by Basz on 2007-04-13
> **skopa said:**
> well basz i am mad for this because, apparently, this update was uploaded without any testing...
this i a beta version, meaning from my debian days, i guess it's a testing version? that has gone beyond the experimental phase? so it should work on most pcs and need something like just minor patches?? (and this doesn't seem to be the case)



it's quite easy to do 50 clicks, if you ever played any fps game that is(or strategy, or rpg, or ...)

It doesn't seem the case to YOU, but only 1 topic containing about 15 posts about the issue isn't much of a 'major global problem' is it?

---

### Post by xxdd on 2007-04-13
> **babuu said:**
> Same problem here, I knew I shouldn't have upgraded yet (BETA and it was my work computer =P), but I am always to curious.

I could boot the old kernel but then there was a version mismatch between Nvidia kernel module and the old kernel module. Don't want to mess that up, so I guess just have to wait for the kernel to be available with aptitude dist-upgrade. Luckily I have the laptop so I can do some work.
you can select to use the open-source nv driver by hitting control-alt-f1 to get to a terminal, login, then run:
sudo dpkg-reconfigure -phigh xserver-xorg
then select nv instead of nvidia, select any resolutions you want to use.
Then run:
sudo /etc/init.d/gdm restart
to restart the x session.

---

### Post by skopa on 2007-04-13
> It doesn't seem the case to YOU, but only 1 topic containing about 15 posts about the issue isn't much of a 'major global problem' is it?

look around,you may see other posts, (and i guess some people couldn't really boot to another pc/os to even post? or maybe some people don't really bother posting on a forum)
oh and this does seem to be the case as the update was withdrawn...

---

### Post by mhansen on 2007-04-13
> **Basz said:**
> 
But on the other hand I very much appreciate the loads of work the developers are putting into this great distro. Best so far, imho. And I'm sure they will fix this minor problem some time very soon.




Same here.  As a (former) developer who worked on another distribution, I know the work that these people are putting in.  I also know that most of the time nobody even thinks of the word "developer" or what they're doing, until something goes wrong.

For every one time something goes wrong, there are hundreds(?) that go right, and these are never noticed by the majority of the community, unfortunately.  The only ones that are remembered are the ones with the "unintended features".  :)

So, for what it's worth, I'd like to thank the developers for all that they're doing.  If I had the time, I'd be there with ya guys (and gals).


Regards,
Mike

---

### Post by babuu on 2007-04-13
> **xxdd said:**
> you can select to use the open-source nv driver by hitting control-alt-f1 to get to a terminal, login, then run:
sudo dpkg-reconfigure -phigh xserver-xorg
then select nv instead of nvidia, select any resolutions you want to use.
Then run:
sudo /etc/init.d/gdm restart
to restart the x session.

Thanks a million! Works great! You made me really happy.

---

### Post by frodon on 2007-04-13
First for those who the device name changed from hdx to sdx it is normal because the IDE devices are now handled by the sata drivers, if you name your devices using UUID it shouldn't be a problem. CDROM/DVD drives are a special case because i beleive UUID can't be used with them but the issue is know and should be fixed already or will be soon.
For the others have a look to this bug report and try the test kernel posted by Ben Collins , it should solve the HPA support problems that some of you may have. The more you are to test and give feedback about this testing kernel the more chance we have to get it included in the feisty release :
[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/82314](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/82314)

Try this kernel and give feedback in the bug report, thank you for testing.

---

### Post by skopa on 2007-04-13
well,i'm back at my ubuntu system after a downgrade but something funny
it's friday the 13th...isn't it ironic?

---

### Post by neymac on 2007-04-13
The same here.
What did I?
Started Ubuntu with the kernel 2.6.20-13-generic (safe mode)
I got a black screen and I am root now:

cd /boot
ls

(see if you have the file initrd.img-2.6.20-14-generic.bak , it is the copy of the previous kernel image before the "bad" updade)

mv initrd.img-2.6.20-14-generic initrd.img-2.6.20-14-generic.broken
mv initrd.img-2.6.20-14-generic.bak initrd-2.6.20-14-generic

reboot

And all worked again with the previous kernel 2.6.20-14-generic, as I used to do before the bad update.

---

### Post by teddybairs1 on 2007-04-13
Huh. My Updater must like me or something then, because it refused to install the update after downloading it, saying that it would break other packages. I guess Adept knows better than I do.

---

### Post by Stingxgl on 2007-04-13
Wow I am very glad I found this forum. I installed Feisty Fawn for the first time last night and have had nothing but problems. I eventually got it installed and working, and thought the best thing to do would be the recommended upgrades. So I would do these upgrades and get the new kernel and then wouldn't be able to reboot without some kind of halt and Busybox prompt (just like everyone mentioned). 

Simply reverting to the .bak worked great. However what I tried was edditing the GRUB init line from  ...initrd.img-2.6.20.14-generic... to ...initrd.img-2.6.20.14-generic.BAK

Adding the ".bak" to it and hitting "b" to boot worked perfectly. You could still do it the other way of using a live CD to log and rename.. but I thought my way would be a little quicker. Of course the next time I boot it will die again cause it goes back to default but all I needed to do was sign in and rename the kernel file and I am good to go. 

To think I only tried reinstalling feisty 6 times in the last 8 hours to get it working.. when all it took as a file rename. If Windows was this fun I might consider using it. :D

UPDATE: The above worked great.. but now I cant see the splash screen... GRub shows that "splash" is in the command line but it just shows me all the loading text like I was in recovery or something. Anyone else having this issue? DId one of the other updates drop the splash? When I shut down or reboot I do see the splash "unloading" ubuntu.

---

### Post by floke on 2007-04-13
Just a big thanks to the devs for the new kernel 20-15.=D> =D>

---

### Post by teddybairs1 on 2007-04-13
My Wife keeps reminding me that Feisty is still in Beta stage and that I was rather foolish to install it yet. When I first attempted to upgrade from Edgy to the feisty beta, the updater hung and I lost everything. I had to recover my important files through my Windows partition and a program called ext2fs. Ironic though it is. I then reloaded it and did the update download and it worked fine for about a day, and then when I tried to change the mouse pointer to another theme, X crashed on me, and I had to do the whole reload thing again. Now it's been running ok for about the last four days. Adept seems to have caught the bad package and won't let me update to it, even though adept_updater keeps reminding me that it's there. I count this as the grace of God and Adept living up to its name.

We still have six days to go until the release date for feisty. Until then, all of us who were too curious for our own good are in for the roller coaster ride.

To be fair, I do like the improvements I've seen in feisty, and think Ubuntu's just getting better and better. But we all knew the risks we took by installing feisty before the release date.

---

### Post by Basz on 2007-04-13
> **Steve.K said:**
> Just a big thanks to the devs for the new kernel 20-15.=D> =D>

I second that. Great work! :D :D

---

### Post by teddybairs1 on 2007-04-13
Anyone know why kernel 20-15 won't show in my GRUB screen? It only displays 20-12 and 20-14.

---

### Post by skopa on 2007-04-13
> Just a big thanks to the devs for the new kernel 20-15. 

me 2

---

### Post by muncrief on 2007-04-13
Please see my mini Howto on how to update to the latest Feisty.

Aptitude is broken, but the kernel hard drive problem that brought down so many systems starting yesterday has been fixed. However, if you don't upgrade correctly you probably won't get the correct kernel at this time.

 I hope this helps. Here's the link:

[http://ubuntuforums.org/showthread.php?t=408860](http://ubuntuforums.org/showthread.php?t=408860)

---

### Post by teddybairs1 on 2007-04-13
20-15 does seem to be working smoothly so far. Great job to the coders for getting it out so quickly.

---

### Post by sirbats on 2007-04-14
> **neymac said:**
> The same here.
What did I?
Started Ubuntu with the kernel 2.6.20-13-generic (safe mode)
I got a black screen and I am root now:

cd /boot
ls

(see if you have the file initrd.img-2.6.20-14-generic.bak , it is the copy of the previous kernel image before the "bad" updade)

mv initrd.img-2.6.20-14-generic initrd.img-2.6.20-14-generic.broken
mv initrd.img-2.6.20-14-generic.bak initrd-2.6.20-14-generic

reboot

And all worked again with the previous kernel 2.6.20-14-generic, as I used to do before the bad update.

I lived in Indonesia; but I put japan repository considering japan provide better packages (than Indonesia). I tried to update my kernel 2.6.20-14-generic LAST NIGHT and repos said : FORBIDDEN. This morning  I know the reason that something happened on aptitude.

Thanks to Japan.

rgds

---

