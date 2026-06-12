---
title: "initramfs + busybox trouble installing"
date: 2008-04-24
forum: Installation &amp; Upgrades
---

### Post by wconstantine on 2008-04-24
I'm stuck at initramfs after trying to launch the livecd/install ubuntu. I've tried safe graphics mode and several boot parameters such as: noirqdebug irqpoll noapic nolapic nomsi

It loads the linux kernel, then the loading bar shows up. It loads and then it just pops up initramfs.

My system specs are E6600, 8800GT, MSI P965 Neo, 2GB 667MHz.

---

### Post by matl1984 on 2008-04-24
i got the same message.

i turned the "sata mode" in bios from "ahci" to "raid" and then it works

my motherboard is asrock 775 twins hdtv r2.0.
my hard disks are seagate Barracuda 7200.10 320GB 16MB
i have 2 sata disks and only dvds are at primary ide master and secondary ide master

my messages - not exactly:

```
BusyBox 1.1.3...
initramfs
[time..] ata1: COMRESET failed (errno:-16)
[time..] ata1: COMRESET failed (errno:-16)
[time..] ata1: COMRESET failed (errno:-16)
[time..] ata1: COMRESET failed (errno:-16)
[time..] ata1: reset failed. giving up
[time..] ata2: COMRESET failed (errno:-16)
[time..] ata2: COMRESET failed (errno:-16)
[time..] ata2: COMRESET failed (errno:-16)
[time..] ata2: COMRESET failed (errno:-16)
[time..] ata2: reset failed. giving up
```

---

### Post by Daveoc64 on 2008-04-24
Thank you!

That fixed my installation, so I don't need to reinstall!

---

### Post by wconstantine on 2008-04-24
> **matl1984 said:**
> i got the same message.

i turned the "sata mode" in bios from "ahci" to "raid" and then it works

my motherboard is asrock 775 twins hdtv r2.0.
my hard disks are seagate Barracuda 7200.10 320GB 16MB
i have 2 sata disks and only dvds are at primary ide master and secondary ide master

my messages - not exactly:

```
BusyBox 1.1.3...
initramfs
[time..] ata1: COMRESET failed (errno:-16)
[time..] ata1: COMRESET failed (errno:-16)
[time..] ata1: COMRESET failed (errno:-16)
[time..] ata1: COMRESET failed (errno:-16)
[time..] ata1: reset failed. giving up
[time..] ata2: COMRESET failed (errno:-16)
[time..] ata2: COMRESET failed (errno:-16)
[time..] ata2: COMRESET failed (errno:-16)
[time..] ata2: COMRESET failed (errno:-16)
[time..] ata2: reset failed. giving up
```

Do you have raid? Because I don't. Dunno why that should do the trick. Will try tho.

Edit: Didn't work.

I've located the problem to be with the wonderful JMicron that my motherboard has. It's a major pain in the ***. Any ideas that could help me?

---

### Post by garyc_onbuntu on 2008-04-24
I had a similar problem on a Dell Vostro 200 - attempts to install or check the CD (8.04 i386 desktop) just resulted in being dumped to the BusyBox screen with (initramfs) showing.

Eventually it would show [111.485885] ata 1.00: revalidation failed.

I went into the BIOS and change the SATA mode from 'IDE' to 'RAID', rebooted and its now installing as I write.

What does this actually do? I have one SATA HDD and a SATA DVD-RW. The machine was a new machine reject due to case damage and the disk had been reformatted with FAT32 if that makes any difference.

Anyway, I'm up and running so thanks alot for the tip.

---

### Post by painaxl on 2008-04-24
I had this same issue and it was resolved by switching from IDE to RAID in the BIOS.

HOWEVER...  I was trying to set up a dual boot with Vista using easybcd.  I got into Ubuntu fine, but when I tried to reboot into Vista, it wouldn't even get to the splash screen before it rebooted the system.  I did the entire rebuild of the bootloader as written on the excellent tutorials on the easybcd site and nothing changed.  So I went back into the BIOS and changed the SATA setting back to IDE.  That did it and Vista booted fine.

What does that setting do and why does Vista only accept the IDE setting and Ubuntu the RAID setting?  I've got a SATA HDD and a SATA DVD-RW, like Gary C, in a Dell Inspiron 530.  Any ideas on why this is necessary and what's happening?

---

### Post by azurehi on 2008-04-25
I get the same initramfs + busybox message.  I have no idea how to access bios and can't understand why, after using ubuntu successfully since 6.06, I cannot install 8.04.  I have downloaded the image X3 and also the alternate install image and get the same error.  I am stymied.  Help please - thank you.

---

### Post by matl1984 on 2008-04-25
my vista ultimate x64 starts normally even if i switch from ahci to  raid mode.

vista supports my 2 modes: AHCI / RAID
ubuntu 8.04 can start only successful with the RAID mode.

i have no raid configured yet (previously i had one configured).

the raid mode is also a bit slower as the AHCI mode during system boot (the grub boot loader comes later)

as you can see here AHCI is a published standard from Intel and requires a license from them. so maybe no one from ubuntu/linux has implemented it now???
[http://de.wikipedia.org/wiki/Advanced_Host_Controller_Interface](http://de.wikipedia.org/wiki/Advanced_Host_Controller_Interface)

---

### Post by jedimasterk on 2008-04-25
> **matl1984 said:**
> my vista ultimate x64 starts normally even if i switch from ahci to  raid mode.

vista supports my 2 modes: AHCI / RAID
ubuntu 8.04 can start only successful with the RAID mode.

i have no raid configured yet (previously i had one configured).

the raid mode is also a bit slower as the AHCI mode during system boot (the grub boot loader comes later)

as you can see here AHCI is an published standard from Intel and requires a license from them. so maybe no one from ubuntu/linux has implemented it now???
[http://de.wikipedia.org/wiki/Advanced_Host_Controller_Interface](http://de.wikipedia.org/wiki/Advanced_Host_Controller_Interface)

This is ridiculous!. What if we don't have RAID and use a SATA drive. Never was a problem with 7.10. This version needs to be pulled of the mirrors and fixed, before it is an LTS!!!.

---

### Post by jedimasterk on 2008-04-25
How are "NEWBEES" to Linux going to know how to go into a BIOS!!. Give me a break!!.

---

### Post by logicslayer on 2008-04-25
Enter the CMOS/BIOS by pressing one of the below five keys during the boot. Usually it's one of the first three.

    * F1
    * F2
    * DEL
    * ESC
    * F10

A user will know when to press this key when they see a message similar to the below example as the computer is booting. Some older computers may also display a flashing block to indicate when to press the F1 or F2 keys.

Press <F2> to enter BIOS setup

Tip: If your computer is a new computer and you are unsure of what key to press when the computer is booting, try pressing and holding one or more keys the keyboard. This will cause a stuck key error, which may allow you to enter the BIOS setup.

---

### Post by matl1984 on 2008-04-25
here's a screenshot from the bios setting from my motherboard manual. maybe this helps someone.

---

### Post by jedimasterk on 2008-04-25
I've never had to change anything in the bios to get Ubuntu running except the boot order.

---

### Post by kdnewton on 2008-04-25
I'm in the same boat.

320GB SATA2 hard-drive split 260GB to WinXP and 50+ to Ubuntu 7.10 currently.

I can confirm that both the AMD64 and i386 Live-CD versions dead-end at the busybox / initramfs / ash thinger. I've tried playing with my bios and I can't find a configuration that works. I tried all of "Check CD for Defects", "Try without changing" and "Install" and they *all* lead to the busybox interface.

I did burn the images at 20x write to Sony 700MB CDs. The 8.04 i386 CD installs fine to my old HP Pavilion laptop, but busybox me on my desktop.

I'm now burning the Alternate i386 at the slowest write speed and am going to try that.

Canonical you and I know know you don't owe me anything. I'm just one person. However, I have to say that this sucks that the possible configuration of my computer is going to "busybox" me and the hundreds of other people out there who don't feel the need to post their cares to the forums.

My iso-burn is done. Back in a few.

---

### Post by aliasbind on 2008-04-25
changing from AHCI/IDE to SATA doesn't solve the problem. when the screen with the ubuntu logo and orange bar moving left-right appears, the OS seems to search "desperately" for a disk in the floppy and if i put one in it, it gives an error and then continues loading perfectly.

i have 2 HDs (1x SATA, 1x IDE). ubuntu can't detect the SATA HD, but, amazingly, it detects the IDE as SATA. this is getting creepy!

---

### Post by kdnewton on 2008-04-25
I'd read what jedimasterk wrote in another thread, that to the alternate CD is to loathe and we shouldn't have to resort to it.

I agree, but it seems to be doing the trick for me.

After burning it and booting into it, I started up the install right away. The install hung up for quite a while and didn't seem to be doing anything. I CTRL-C`d it and saw that it appeared to be in an infinite loop, something to do about not finding a database.

A quick search on the f0s here and I find that someone recommended pressing F6 from the alternate boot menu and adding "pci=nomsi" to the boot arguments. That seemed to do the trick.

Now I'm already over 50% done the last stage of the installation process (select and install software).

---

### Post by kdnewton on 2008-04-25
Just a follow up. I'm now swimming happily through the Hardy Heron i386 desktop, thanks to the alternate CD and pci=nomsi argument.

---

### Post by wconstantine on 2008-04-25
Seems like we have unveiled a major problem with 8.04. Although, none of you are experiencing this due to same reason as I. :mad:

---

### Post by ig72 on 2008-04-25
I also have this problem on a machine I built myself using an Asus A8-VM CSM motherboard. 

It has a single 300Gb sata drive and an IDE DVD writer. 

On any option in the install menu, Normal/safe mode check CD etc 
as the ubuntu logo appears I see it access the HDD for a second (and I hear the drive seeking) then the CD is accessed for a second, this repeats approx 10 times, after this it then dumps me to the Busybox console with no error messages.

I have tried enabling raid in the BIOS but this makes no difference whatsoever.

I will try the above mentioned "pci=nomsi" in alternate boot options later on today and report if it works.

---

### Post by amosbr on 2008-04-25
I have the same problem. I try to install in any of the different modes and at first i get the ubuntu loading screen for about 2 minutes and then the busybox thingy. The problem i have is i can't seem to find that SATA option in my CMOS. Also, how do I get to "alternate boot options" in order to try the pci=nomsi method?
Thanks.

---

### Post by amosbr on 2008-04-25
sorry admins accidentally posted twice please delete

---

### Post by dishayu on 2008-04-25
same motherbaord, same problem...

BUT
it did run once on mine, i guess the second time i tried, but then i recalled i had to backup some stuff prom my previous 64 bit install (moving to 32 bit now).. and when i backed up the data and tried again...

BAM!!
it just won't work... tried 2 CDs burnt at 16x and both lead to the same screen...

---

### Post by wconstantine on 2008-04-25
> **amosbr said:**
> I have the same problem. I try to install in any of the different modes and at first i get the ubuntu loading screen for about 2 minutes and then the busybox thingy. The problem i have is i can't seem to find that SATA option in my CMOS. Also, how do I get to "alternate boot options" in order to try the pci=nomsi method?
Thanks.

You press F6 in the menu in order to edit. Just write after the --. :)

---

### Post by azurehi on 2008-04-25
1.  changing BIOS from IDE to RAID accomplished Nothing -- still reach initramfs screen and cannot install ubuntu 8.04

2.  from F6 adding "pci=nomsi" did nothing -- still reach initramfs screen and cannot install ubuntu 8.04

Would installing 7.10 and then updating to 8.04 seem a viable solution.  Any suggestions much appreciated.

---

### Post by amosbr on 2008-04-25
> **wconstantine said:**
> You press F6 in the menu in order to edit. Just write after the --. :)
sorry for noobness, but what menu are you referring to?

---

### Post by dishayu on 2008-04-25
> **amosbr said:**
> sorry for noobness, but what menu are you referring to?

the menu you are shown when you boot from the cd...

use your eyes, it's written on the bottom of that screen..


PS : so what's the conclusion? does using a msi p965 neo imply that i'm not going to run hardy on my pc??

---

### Post by avenger3000 on 2008-04-25
same problem here mates.. i have an asus p5w dh deluxe mobo, two sata hd drives and one ide drive, when i try to boot hardy i get the Busybox message. right now i'm at work but i will give the -- pci-msi parameter a try.. whats more frustrating is the fact that 7.10 starts up normally and i can install it flawlessly.

---

### Post by dishayu on 2008-04-25
okay... everyone on a msi p965 neo IDE cd drive and SATA hard drive... I figured out a solution to work the way around this issue and i shalt give it to you if you all bow down to me... hehe now, jokes apart...

your harddisk most probably is connected to ich8 sata port, plug it into the jmicron sata port (the only one which stands out) and launch the setup, works flawlessly for me... other motherboards with jmicron bios should also 
work similarly, although i'm just guessing here...


ENJOY...

PS : drop in an appreciation e-mail to [email]dishayu@gmail.com[/email] if this works for you.. i almost never visit the forums..

---

### Post by wconstantine on 2008-04-25
> **dishayu said:**
> okay... everyone on a msi p965 neo IDE cd drive and SATA hard drive... I figured out a solution to work the way around this issue and i shalt give it to you if you all bow down to me... hehe now, jokes apart...

your harddisk most probably is connected to ich8 sata port, plug it into the jmicron sata port (the only one which stands out) and launch the setup, works flawlessly for me... other motherboards with jmicron bios should also 
work similarly, although i'm just guessing here...


ENJOY...

PS : drop in an appreciation e-mail to [email]dishayu@gmail.com[/email] if this works for you.. i almost never visit the forums..

My SATA HDD is connected to that very port. Although I have several harddrives.. Could that be the problem?

By the "one that stands out", do you mean sata 1? Here's an image of the mobo sata ports.
[IMG]http://www.hardwarezone.com.sg/img/data/articles/2006/1987/P965Neo_SATA.jpg[/IMG]

---

### Post by dr_john_doe on 2008-04-25
> **aliasbind said:**
> changing from AHCI/IDE to SATA doesn't solve the problem. when the screen with the ubuntu logo and orange bar moving left-right appears, the OS seems to search "desperately" for a disk in the floppy and if i put one in it, it gives an error and then continues loading perfectly.

i have 2 HDs (1x SATA, 1x IDE). ubuntu can't detect the SATA HD, but, amazingly, it detects the IDE as SATA. this is getting creepy!
Aliasbind's hint was right: I noticed the system trying to get a floppy. I inserted one, then ubuntu read the floppy for some time and finally continued to boot from CD. No error message or anything, just reading the floppy. While I'm writing this posting I still use ubuntu 8.04 in Live-CD mode.

And I have a ASUS P5B-Deluxe mainboard with this f****g JMicron controller stuck on it! This one gave me trouble eversince I bought the board some 18 months ago using Windows or different Linux distributions. Now it's definitly time to buy some SATA DVD-Writer and disable this controller. Perhaps it interferes here as well as some other users mention it as part of their system, too.

---

### Post by dr_john_doe on 2008-04-25
> **aliasbind said:**
> (...) when the screen with the ubuntu logo and orange bar moving left-right appears, the OS seems to search "desperately" for a disk in the floppy and if i put one in it, it gives an error and then continues loading perfectly.

Aliasbind's hint was right: I noticed the system trying to get a floppy. I inserted one, then ubuntu read the floppy for some time and finally continued to boot from CD. No error message or anything, just reading the floppy. While I'm writing this posting I still use ubuntu 8.04 in Live-CD mode.

And I have a ASUS P5B-Deluxe mainboard with this f****g JMicron controller stuck on it! This one gave me trouble eversince I bought the board some 18 months ago using Windows or different Linux distributions. Now it's definitly time to buy some SATA DVD-Writer and disable this controller. Perhaps it interferes here as well as some other users mention it as part of their system, too.

---

### Post by dishayu on 2008-04-25
> **wconstantine said:**
> My SATA HDD is connected to that very port. Although I have several harddrives.. Could that be the problem?

By the "one that stands out", do you mean sata 1? Here's an image of the mobo sata ports.
[IMG]http://www.hardwarezone.com.sg/img/data/articles/2006/1987/P965Neo_SATA.jpg[/IMG]

and yes, i do mean SATA 1, the one next to the IDE port... the darker coloured one...
try using just 1 harddisk while installation, it worked in one go for me...

---

### Post by azurehi on 2008-04-25
I guess I have to give up on ubuntu 8.04...still reach initramfs no matter what I do.  I get this also with kubuntu 8.04.

---

### Post by azurehi on 2008-04-25
I guess I have to give up on ubuntu 8.04...still reach initramfs no matter what I do.  I get this also with kubuntu 8.04.

---

### Post by jedimasterk on 2008-04-25
> **dr_john_doe said:**
> Aliasbind's hint was right: I noticed the system trying to get a floppy. I inserted one, then ubuntu read the floppy for some time and finally continued to boot from CD. No error message or anything, just reading the floppy. While I'm writing this posting I still use ubuntu 8.04 in Live-CD mode.

And I have a ASUS P5B-Deluxe mainboard with this f****g JMicron controller stuck on it! This one gave me trouble eversince I bought the board some 18 months ago using Windows or different Linux distributions. Now it's definitly time to buy some SATA DVD-Writer and disable this controller. Perhaps it interferes here as well as some other users mention it as part of their system, too.

You know I remember my floppy drive constantly turning on and off as well, when booting from 8.04 Live cd than I get the bars than (initramfs)_ prompt. Didn't try inserting a floppy. But oh well, sticking with 7.10. It works!.

---

### Post by jedimasterk on 2008-04-25
I think Caninical should release a new Live CD, that fixes the floppy detection issue. This may be the problem!. 8.04.1 canonical. Before the Shipit cds are sent.

---

### Post by HDave on 2008-04-25
This is not just a floppy detection issue.  I have a Dell XPS M1210 laptop with no floppy drive at all and I am getting the same issue:  boot into busybox.

I tried the pci=nomsi workaround and it didn't work.

I can't believe that simply upgrading to Hardy has bricked my PC.  The only thing that works is the Windows XP side of the dual boot....arrggghhh.

---

### Post by HDave on 2008-04-25
FIXED!

The hard drive UUID in my GRUB menu.lst was wrong.  I had swapped out my hard drive when my machine was running Gutsy.  I had fixed the UUID in /etc/fstab (you have to or you can't login).  However I never changed the UUID in /boot/grub/menu.lst and when I upgraded to Hardy I used the new "merge" capability to get my new menu.lst file.

Apparently Gutsy didn't care the UUID was wrong, but Hardy does.  I booted into windows, copied the UUID from fstab and pasted it into menu.lst I now I am swimming in 8.04 goodness.

---

### Post by mat.wojcik on 2008-04-25
I don't have any SATA devices in my PC and I have the same bug! The option pci=nomsi doesn't work. I'm afraid of doing dist-upgrade, cause it might be the same error but on my installed system...

---

### Post by avenger3000 on 2008-04-26
the pci=nomsi trick didn't work for me either... i have installed 7.10 on my ide drive and then upgrade it to 8.04. everything went fine. the problem is that when i try to boot windows i get the following error "error 21: selected disk does not exist" if i set as first boot device my windows disk it boots normally but i loose grub since its located on my ide drive.

---

### Post by om1n[A]e on 2008-04-26
i also have the problem with initramfs;

hardware:
MSI P965 Neo-F
250GB SATA HD (connected to ICH8)
DVDRW SATA (connected to Jmicron)

i also noticed that the system tries to read from floppy, so I'll try this recommendation tomorrow. however, i also think that canonical should fix this issue with a new live-cd

---

### Post by Maqz447 on 2008-04-26
Hi folks, I updated from 7.10 to 8.04 using the Update Manager, and now I have the same problem. The Ubuntu splash screen hangs for a while trying to mount the root file system, then I'm dumbed into Busy Box and get the initframs error message repeatedly in some kind of infinite loop. The strange thing is that 2 times I did get Hardy up and running without doing anything different, and everything seemed to work fine, but when I restart it just hangs again!

I tried to change the "SATA mode" setting in my BIOS from "IDE" to "RAID" (my HD is a SATA, I have a Dell Inspiron 530), and that did do the trick insofar as I got Hardy to mount the drive, however it was extremely unresponsive to mouse and keyboard input for some reason, so much that it was practically unusable. And, I was then unable to get into Windows (I dual-boot with Vista). So now I've reset it to IDE, and I can't boot Hardy. 

8.04 seems to have a major problem with SATA drives... I'll be following this thread to see if any solutions come up, I would deeply appreciate any suggestions anyone might have.

---

### Post by mat.wojcik on 2008-04-26
I do not have SATA drive, I tried to remove 'quiet splash' from boot options in Live CD and I got these errors before Busybox:

> Add. Sense: Logical unit communication CRC Error (Ultra-DMA/32)
end request: I/O error, dev sr1, sector 1384512
Sense key: Hardware Error [current]
SQUASHES error: sb-brod failed reading block 0xa8789
SQUASHES error: unable to read uid/gid table

Can you help me with that?

---

### Post by Jong on 2008-04-26
Enabling floppy drive in BIOS even though I don't have one, made the "busybox initramfs" message disappear.

Now I'm stucked with the "buffer i/o error on device fd0" message. As described by other users, it just loops infinite...

I haven't tried changing the interface from "IDE" to "RAID" though.

Hardware:
AMD64 3700+
ASUS A8N-E mb
2 Samsung SP250 SATA-II hd

Edit: Tried installing from the alternate cd, but it can't even detect/mount my cd drive during installation. Very disappointing :(

---

### Post by Aearenda on 2008-04-26
Maqz447, try the all_generic_ide boot option mentioned in [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/153702](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/153702) - this works on my 530 with Hardy, but then so does the RAID setting in the BIOS, for me!

---

### Post by Maqz447 on 2008-04-26
Thanks for the link Aerenada, that's very interesting. Now, pardon my noobness, but I'm not entirely sure how to add the boot option "all_generic_ide" to GRUB. Can I do this from GRUB itself, or do I have to edit /boot/grub/menu.lst, or something else?

---

### Post by wconstantine on 2008-04-26
I enabled a floppy in the bios as well, though I don't have one. Now I just loads a really long time and then it drops me a black screen. After a few seconds this message appears with random digits in fron of them. Repeatedly.

```
Buffer I/O error on device fd0, logical block 0
``` :popcorn:

---

### Post by Maqz447 on 2008-04-26
Ok, so I appended "all_generic_ide" to the "kernel" line in GRUB. That did nothing, however. It still hangs when it's trying to mount the root file system. I changed the SATA setting to RAID in my BIOS again, and edited the same line in /boot/grub/menu.lst (typing s l o w l y because Ubuntu was so unresponsive to keyboard input, just like last time I changed this setting to RAID), but that still doesn't help when I switch the BIOS setting back to IDE.

Using the RAID setting is no option for me, as I sometimes need to use Windows, and Ubuntu becomes more or less unusable even though it does boot.

---

### Post by tofuconfetti on 2008-04-26
Okay after a lot of searching, I found a far simpler fix, and the only one that worked for me.  I am running an Intel motherboard with an e6600 quadcore chipset.  It has a Marvell 88SE61xx SATA controller.  I got the same freeze with the same busybox message. So I did more searching in the bugs list and found [this link that explains a possible workaround]("https://wiki.ubuntu.com/WubiGuide#head-9fe000fa2e31a632fdcf384438b2aee35076c623").  Interestingly, when I booted into the graphical boot menu and hit 'esc' to go into the non-graphical menu and tried to hand edit the boot options, I got a "kernel not found" message.  It dawned on me that the drives weren't being recognized by the kernel. 

I could NOT use the directions listed in that workaround, so I experimented and found how how I could make it work.  Try this:

1] Boot the Live CD and select your language.

2] When you are in the graphical menu, hit <F6> for "other options" and when you do you'll see the actual kernel boot line and at the end you'll see a ' -- ' and the cursor will be placed just after the end of the line just after the ' -- '. 

3] At the cursor type:  'irqpoll'  (obviously without the quotes).

4] Hit enter to start the boot process.

Worked like a charm and I booted into the Live CD.

Now I haven't tested this with an actual install, BUT if it hangs on a fresh install, boot into the live CD as above, mount the system partition, and edit the /boot/grub/menu.lst file and add 'irqpoll' to the kernel boot line.  That is what I am going to try if it hangs on install.

I'm currently typing this from the Live CD, so haven't tried that yet.

---

### Post by Maqz447 on 2008-04-26
Thanks for the tip on irqpoll! I added 'irqpoll' to the kernel line in GRUB, and am now typing this at full speed from Hardy Heron! There's only one small problem so far: CPU scaling isn't working, so that my 1.86 GHz Core 2 Duo is always running at 1.86 GHz, whereas it used to idle at 1.60 most of the time. Other than that, seems to be working fine.

---

### Post by tofuconfetti on 2008-04-26
It seems that the kernel that made it into the distribution doesn't have this same problem.  Once I installed, it booted right up. The problem seems to be with the differing bios' method of SATA drive assignment.  I'll leave it up to the kernel whizkids to figure out exactly why.

So I did not need to modify the /boot/grub/menu.lst kernel boot options.  If the problem persists after boot, you may have to do that.

For the record, I have two other AMD 64 AM2 based motherboard computers neither of which had this problem.  It only happened with the Intel board using the quad-core chip.  

Mazq447, I'll know more about the scaling once I monitor the system for a while.  Glad the workaround worked for you.

---

### Post by Caligatio on 2008-04-26
I'm going to bump this as there's a lot of 1 post threads that I think are duplicates of this.

I'm running a ABIT IP-35 board... my boot problem is intermittent.   It won't work for like 5 attempts.. I go into Vista to look at posts.. try again and it works.

There's a few launchpad posts about this.. apparently it may be a problem with the kernel version.

---

### Post by sorta90 on 2008-04-26
> **matl1984 said:**
> i got the same message.

i turned the "sata mode" in bios from "ahci" to "raid" and then it works

my motherboard is asrock 775 twins hdtv r2.0.
my hard disks are seagate Barracuda 7200.10 320GB 16MB
i have 2 sata disks and only dvds are at primary ide master and secondary ide master

my messages - not exactly:

```
BusyBox 1.1.3...
initramfs
[time..] ata1: COMRESET failed (errno:-16)
[time..] ata1: COMRESET failed (errno:-16)
[time..] ata1: COMRESET failed (errno:-16)
[time..] ata1: COMRESET failed (errno:-16)
[time..] ata1: reset failed. giving up
[time..] ata2: COMRESET failed (errno:-16)
[time..] ata2: COMRESET failed (errno:-16)
[time..] ata2: COMRESET failed (errno:-16)
[time..] ata2: COMRESET failed (errno:-16)
[time..] ata2: reset failed. giving up
```
will this bios thing on raid work with my windows xp media center edition ( im relatively new to this)

---

### Post by tofuconfetti on 2008-04-26
Did you try adding 'irqpoll' at the end of the boot string from the graphical boot up menu?  Rather than change a working bios with a Windows install, changing your boot options is less intrusive on the system and less apt to mess up your working Windows install.

Also, if you are new, I'd highly recommend putting Ubuntu on a second drive.  Careful "moving" or "resizing" partitions unless you know what you're doing.

---

### Post by felipe de la muerte on 2008-04-26
hello,

i have a similar problem with hardy.
after a simple upgrade some things did not work anymore (fglrx....), so i decided to do a clean install, since my home folder is on a different partition anyway.
but after the upgrade i got some problems with my cd writer, the system would freeze every time i wanted to burn the cd. i was getting some strange messages on tty1, like

[   time...] hdb: drive not ready for command
[   time...] hdb: timeout verifying DMA

these come up again and again, and the system freezes, so i had to burn the cd in winxp. never seen things like this before. 
the live cd brings up busybox and also some weird messages like

[   time...] ata4.01: cmd a0/01:00:00:80:00/00:00:00:00:00/b0 tag 0 dma 128 in
[   time...] ata4.01: status { DRDY }
[   time...] exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x2 frozen

again and again every 40-50 units in "time" (seconds? :D).

i'll try the bios thing now.

but seriously: wtf?

UPDATE:
neither the adding irqpoll nor all_generic_ide to the boot string of the live cd helped. my single sata-disk is already managed as raid by the bios, because winxp needed it for some reason.
well, i don't really know what else to try.

---

### Post by strumluff on 2008-04-26
Hi All,

I also got this issue on my laptop (worked fine on my desktop) when trying to boot with the Live CD. I haven't made any changes to my hardware and I dont even have a SATA hard drive in it...seems that this is happening to multiple users but for different reasons.

I couldn't fix it so I tried a dist-upgrade from Gutsy and it worked fine, I guess that will have to do, even though I wanted a clean install...

---

### Post by Aearenda on 2008-04-26
mazq447: Sorry for not supplying the details, it was night time here :-)

I'm glad it is working for you now!

---

### Post by Gentleman83301 on 2008-04-27
I am having this exact same problem as well.  I was able to install 8.04 clean onto a Dell precision workstation 4300 without any issues. When I try to toss it onto my desktop I reach the same result as everyone else above.  Tried the switches, tried the floppy trick,  bios etc.  Been scouring the forums/google for work-arounds and so far the only one that really works is to not use 8.04 :(

---

### Post by Fury161 on 2008-04-27
Same problem here. 

Can anybody help me?

2 SATA Hard Drives.
2 IDE DVD-ROM/RW

Bios:

Both (SATA/PATA) => Ubuntu 8.04 Initramfs + Busybox trouble installing and entering

Just SATA => Everything works except DVD-ROM/RW (So I can't either install it through live CD nor use my DVD-ROM devices in my ubuntu updated from feisty)

Thanks a lot everyone

---

### Post by Tarmael on 2008-04-27
I can report that 8.04 is working now after using the pci=nomsi workaround after trying the AHCI to RAID (or any other variant for that matter) and the irqpoll workaround.

Also, I'd like to note that I installed the 8.04 RC Desktop version (as it's the only one I have and I don't have the internet connected to that computer.)

Thank you all. Good luck.

Basil.

---

### Post by Jong on 2008-04-27
OMG, I'm up running with Hardy now :lol:
No IDE to RAID switch, nor enabling the floppy drive (I disabled it again).

Using the desktop live cd, what did the trick for me was adding ```
all_generic_ide floppy=off irqpoll
``` to the boot options when pressing F6. I can't tell if you really need all three options. I'm just happy to be up running :D

Hope this may help someone - good luck to everyone.

---

### Post by felipe de la muerte on 2008-04-27
ok my hardy heron seems to work now, too!

all the bootoptions did not help. what i did was that i put my cd-writer from primary slave to secondary slave, and everything worked fine. i really don't know why. maybe this can help someone.

no i've got my dvd-rom on primary master and the cd-writer on secondary slave (i have to change the jumpers to get it on master), and my harddisk on the s-ata port. maybe the dvd-rom and cd-writer interfered somehow.

---

### Post by Fenris_rising on 2008-04-27
hi all

ive been trying for days to get HH on my PC. i have an ASUS A8V-VM with a SATA drive as primary with XP pro. i installed HH within windows and rebooted. got the fd0 error and eneded up at initramfs. i went into bios and disabled the floppy which isnt connected anyway. reboot and select ubuntu and hit esc for menu and then 'e' to edit. to the second line of the 3 presented i added pci=nomsi enter then b to boot. HH then did its install yayyyyyyyyyyyy it rebooted...........initramfs boooooooo!!!!
so i reboot and go into the menu again and once more i enter the pci=nomsi. boot and good god!!! its in and on!!!!! now i must stress im a novice and its only reading in this forum thats helped plus a bit of lucky guess work. i didnt really know where to type the pci=nomsi for sure and until i reboot the PC i dont know if ill need to do it again. anyone know?? glad to say the wireless internet access has worked within seconds of HH coming on. BTW last night i cocked it right up and trashed my HDD so i was up till3 oclock this morning reinstalling XP and all the drivers and software. so fingers crossed i have a dual boot system. 
all being well ive got a bit of a steep learning curve ahead.
good luck to all dont give up, if a numpty like me can get this far theres hope for us all.........poor bill gates mwahahahaha!

regards

Fenris

---

### Post by Tom_R on 2008-04-27
I had the busybox thing come up on me too. I could switch screens and the boot stuff told me a UUID could not be found. I tried some of the things posted here and nothing helped. I booted a live cd to see what was up and it told me the drive I tried to install to had a bad superblock. I was using 7.10 with that drive no problems, but it's an older IDE 60gb drive.

I solved my problem by installing on a 320gb SATA drive where windows xp used to be. I figured I haven't used it in months and if I need it I'll try to install it on the other disk.

---

### Post by om1n[A]e on 2008-04-27
works for me now, only thing needed was irqpoll...

---

### Post by Neo0351 on 2008-04-27
i think it is the something wrong with the kernel.  i updated from gutsy and i got the same thing as the live cd, busy box.  the alt. cd didnt work either cause it coudnt find my either HDD.  i seem to remember this problem with i think it was 7.04 also.  anyways, so the 2.6.24 kernel didnt boot right, but i can boot just fine with the old 2.6.22 kernel.  go figure.

---

### Post by blindd0t on 2008-04-27
Jong:

Thanks so much!  Your suggestion did the trick.  I did need all three since I also got the Ultra-DMA I/O error as mat.wojcik on post #43 in this discussion.  I did an install using those options to boot the LiveCD, and I did *not* need to edit my menu.lst file after installation to boot from the hard drive.  Also, I am using an Asus A8N-8X Deluxe motherboard with an Athlon 64 (I installed the x64 version of Hardy) with only one SATA drive.

-d0t

---

### Post by Gentleman83301 on 2008-04-27
> **Jong said:**
> OMG, I'm up running with Hardy now :lol:
No IDE to RAID switch, nor enabling the floppy drive (I disabled it again).

Using the desktop live cd, what did the trick for me was adding ```
all_generic_ide floppy=off irqpoll
``` to the boot options when pressing F6. I can't tell if you really need all three options. I'm just happy to be up running :D

Hope this may help someone - good luck to everyone.

Thanks Jong,  I believe I tried them switchs stand-alone and got no where.  However I tried all 3 in the same order you did and am 61% into the install now.  Wish me luck,  I'll update more after I verify a good reboot or three.

by the way my floppy is enabled in bios, (I did no bios changes)  I may go back and see if I can narrow down or shorten it,  but im smiling now!

---

### Post by Ubangi on 2008-04-27
Me too, I have written to beginners forum but all I got was advice to reburn the CD for the third time....

---

### Post by Ubangi on 2008-04-27
All hail the powerful wizard Jong for his secret knowledge of the incantation: "F6, all_generic_ide floppy=off irqpoll" to pass through the locked gates of UBUNTU installation!

---

### Post by ScottBla on 2008-04-27
No such luck for me...when I try to boot into the live CD Ubuntu on the 8.04 desktop ISO, I'm ending up with an apparent infinite loop with messages something like this:

SQUASHFS error: unable to read fragment cache block...
SQUASHFS error: unable to read page, block 2224bb3d, size 8404
SQUASHFS error: sb_bread failed reading block 0x8893b

Guess I'll try the re-download & re-burn sequence (again) to see where that gets me...

This is installing on a Dell Vostro 200 that is currently dual booting the original Dell Windows XP (that I shrunk down) and Ubuntu 7.10.  I'm attempting to do a fresh install of 8.04 on top of the existing (just recently installed) 7.10 install.  No luck so far :(

Any other suggestions would be appreciated!

---

### Post by Tritonio on 2008-04-27
Had the same problem. **I used the all_generic_ide boot option and it worked.**
My mobo is Gigabyte K8 Triton series, GA-K8NF-9 (nForce4-4x chipset).

This is a really serious problem. In fact it's more than one problem because different users find different workarounds working for them.

---

### Post by louyo on 2008-04-27
Alas, the "fixes" don't work for all. I have a Dell 690 with Quad Core and NVIDIA video. I get the dreaded busybox halt with a: "ata_id [2884 *number varies*] main:HDIO_GET_IDENDITY failed for /dev.tmp-8-32" jumping up about 30 seconds later. Actually 2 such messages. I have tried all the incantations I can find on here, unplugged/disabled everything I can think of in BIOS except for the CDROM and one hard drive (SATA or SCSI). All to no avail. Both Ubuntu and Kubuntu, CD's pass test and both install in a Virtual Machine in VMWare (running on Linux host). System is already running openSUSE 10.3 which installs fine. Guess I will have to stay with it unless another version of the image is released. I have officially given up.
This is a great forum, so I will keep an eye open to see if something else in the way of a work around shows up. Keep up the good work. 

-- 
Lou
I don't know how I got over the hill without ever getting to the top.

---

### Post by Fury161 on 2008-04-27
Please help :(

If I use the "all_generic_ide floppy=off irqpoll" option with the live CD it will work and install Hardy but after that the brand new installation won't work, will it?

To make my updated Feisty to Hardy work I have to change in Bios "Both" (SATA/PATA) to "SATA" in the Onboard SATA devices. But the problem is that way I can't use my IDE DVD-ROM devices.

Any idea? Please help :(

---

### Post by jbr6700 on 2008-04-27
Have similar issue here, but looks like a network card is jamming things up. I have tried a upgrade from within Gutsy as well as a clean install but the end result is always being dumped to a busybox screen. Message is as follows:   **(initramfs) [ 139.175210] 8139cp 0000:05:09.0: This (id 10ec:8139 rev 10) is not an 8139C+ compatible chip [ 139.175276] 8139cp 0000:05:09.0: Try the "8139too" driver instead. **    This setup works pretty well in Gutsy with mimimal tweaking, but Hardy refuses to do anything from a Live CD except Memtest86+. Any other choice results in the error. System specs are Asus A8V-VM / Athlon 64 3500+ / Nvidia 6600GT based GPU / 1GB DDR 400 / Hitachi 80 GB HDD / Lite On DVD ROM CD +/- Burner combo. Any suggestions would be welcomed here.

---

### Post by dvord on 2008-04-27
I had this problem when I installed 7.10.  This ugliness appeared again and irqpoll saved the day.

Now can we get 5 button mouse support?  PLZ!?

---

### Post by HDave on 2008-04-27
For those of you still having problems -- can you verify that the UUID in the grub /bppt/grub/menu.lst matches your /etc/fstab and is actually the right value for your hard drive?

They were different in my case...and I got dumped into busybox too.

---

### Post by azurehi on 2008-04-27
Thank you Jong!  I was able to install HH 8.04 from the Live CD.  From Live CD, Install, F6 I entered:

all_generic_ide floppy=off irqpoll  

and the image booted from cd-rom to desktop and the installation proceeded without apparent problem.  I tried all the other suggestions, without success and this did the job.

---

### Post by matl1984 on 2008-04-28
> **sorta90 said:**
> will this bios thing on raid work with my windows xp media center edition ( im relatively new to this)
on my vista ultimate x64 it works with both modes (AHCI, RAID).
maybe you need drivers from your sata controller (on the motherboard cd?)
i don't know - the drivers for my board are integrated into vista or i don't need special one.

additional infos to my config:
my floppy controller is disabled in bios (manually - because i have no floppy)

i think i should also try the options posted her without change sata mode to raid.
```
all_generic_ide floppy=off irqpoll
```
if the options are the correct solution this should be autodetected and built in if possible in future iso files.

off topic:
compiz fusion is so cool! The effects are running very fast (ati radeon express 200 onboard with 256mb shared ram). everytime i move a window i have to smile :) these effects are all better than the vista effects. maybe i'll buy a hp all-in-one printer instead of my lexmark all-in-one p4350 and then kill my vista!

---

### Post by wconstantine on 2008-04-28
It seems like all_generic_ide floppy=off irqpoll is the solution for those with an Asus board with JMicron? Not for MSI. I can't get it working.

---

### Post by transisco on 2008-04-28
I can verify that this works on my ASUS AMD X2 4200+ with 8600GT when using all_generic_ide floppy=off irqpoll. After that I don't need to do anything else once Ubuntu is installed.

---

### Post by matthewhunt on 2008-04-28
Well I had the same probems last night trying to install 8.04. Got dumped to the busy box every time. I'll try the command line tags suggested above. 

It's a pity there's such a widespread problem with this distriution as it may be enough to put off a less technically savvy person from trying Linux. I'm pissed off with windows sapping my computers resources and I really don't like vista so i'm prepared to put the work in to get linux going.

I do have a copy of 7.10 that i haven't used yet so i could try that and upgrade.

---

### Post by avenger3000 on 2008-04-28
After lot of tests i managed to install HH on an 120gb ide hdd and it works flawlessly. the thing is that i can't get into my windows xp installation. if i choose "Windows XP Professional" from the GRUB menu i get a message like "selected disk can not be found". ubuntu starts from sd (0,0) hdd, how can i get grub to load windows as well? the hard disk (sata) where windows are installed is sdc1. what do i have to add on menu.lst. any ideas?

---

### Post by millenium.dare on 2008-04-28
Thanks Jong!

I was able to boot the LiveCD and install Hardy 8.04 on my machine with the help of those kernel parameters. For reference, my specs are:

Asus P5NSLI
Intel E6600
2 Seagate SATA HDD
Nvidia 8800GTS

---

### Post by wconstantine on 2008-04-28
> **avenger3000 said:**
> After lot of tests i managed to install HH on an 120gb ide hdd and it works flawlessly. the thing is that i can't get into my windows xp installation. if i choose "Windows XP Professional" from the GRUB menu i get a message like "selected disk can not be found". ubuntu starts from sd (0,0) hdd, how can i get grub to load windows as well? the hard disk (sata) where windows are installed is sdc1. what do i have to add on menu.lst. any ideas?

I suggest you create a new thread for that issue as it's quite off topic here.

---

### Post by vlgligor on 2008-04-29
The "all_generic_ide floppy=off irqpoll" options does not work for me, all the time I end up in the initramfs + busybox.

I tried also changing the IDE/AHCI -> RAID, but it doesn't work.

My configuration:
Intel C2Duo 6300
MB MSI P965 Platinum
HDD SATA
DVD-WR Primary IDE.

---

### Post by matl1984 on 2008-04-29
i tried some combinations of ```
all_generic_ide floppy=off irqpoll
``` but it doesn't work for my system. **currently the only solution for me is to switch sata mode in bios/IDE Config from AHCI to RAID.**
i tested the following:
with live cd:
all_generic_ide floppy=off irqpoll
floppy=off
all_generic_ide floppy=off
irqpoll

i also removed my dvd burner from the primary ide master and my dvd drive from the secondary ide master and tried to boot the previously installed ubuntu (installed with sata raid mode) with ahci mode with no success.

my system as previously mentioned:
asrock 775 twins hdtv r2.0 with bios 2.10 (floppy disabled), 
intel pentium d 805, 2x1GB DDR2 667 RAM, 2 x sata seagate barracuda 7200.10 320 GB 16MB on SATA1 und SATA2.

---

### Post by MinoltaLuvR on 2008-04-29
i havent or cant recall posting on this forum for a long time.
but i gotta chime in now and say, i've been very disappointed in the last two releases of ubuntu. i never had to jump through hoops to get ubuntu installed like i have with 7x and now 8x. its just sad.

that being said.. i just got the live cd to boot finally after using a great many of the start up commands suggested in this and other threads.
what ultimately worked for me was adding:
nolapic acpi=off irqpoll 
after hitting F6 i hit the END key, i delete the quiet splash -- and put the above commands in its place.

which iirc was the exact string i had to use to install 7x on my box.

my specs are a Xeon 3220 @3.2ghz on an ip35 pro with 4 gigs of OCZ ram.

hope this helps someone out there.. cheers.

---

### Post by matthewhunt on 2008-04-29
I haven't managed to get Hardy to run on my desktop pc. The live CD however runs on my works laptop and everything works as far as i could see from a quick test this morning. 

I have a different issue with 7.10 where the live cd runs ok on my desktop pc, but my keyboard doesn't work but i'll discuss that problem somewhere else.

---

### Post by devliljohn on 2008-04-29
im having this same issue with my asus z96j laptop it has a 32bit core duo processor, radeon x1600 graphics card and 1 gig of ram. i haven't tried any workarounds from this thread yet but i will when i get home tonight and i will post my results

---

### Post by paziek on 2008-04-29
> all_generic_ide floppy=off irqpoll
did the trick on MSI KT4AV board.
\thanks.

---

### Post by Sonny Boy on 2008-04-29
> **all_generic_ide floppy=off irqpoll **
worked like a charm on my Acer 5050(after trying all the other with no success)

---

### Post by PhilB on 2008-04-29
Very familiar with this problem as I had it last year with 7.10 on a new machine I built and I have spent the last two days getting very frustrated having encountered it again.
Basically the Hardy upgrade failed for me-no nvidia enabled. Turned out to be booting 7.10 still, and when I edited grub to 8.04 I trashed the machine.
I tried installing 7.10 again and got the initramfs/busybox problem, and all research indicated that the problem lay with Seagate drives, so knowing that I had successfully installed openSuse on a Hitatchi drive tried with this one-same thing.
Only just realized after the last two days why I had for the last six months been using a very old slow Toshiba cd drive instead of my very fast LG dvd burner (which I decided on Sunday I ought to put back in the computer, being a "better" drive).

If you cannot install, and if none of the suggestions for editing the boot script via F6 dont work, I strongly suggest you try a different cd/dvd drive.

---

### Post by silbar on 2008-04-29
> **azurehi said:**
> I get the same initramfs + busybox message.  I have no idea how to access bios and can't understand why, after using ubuntu successfully since 6.06, I cannot install 8.04.  I have downloaded the image X3 and also the alternate install image and get the same error.  I am stymied.  Help please - thank you.
For my BIOS (on a Dell Inspiron 530) I have to hit <F2> to go into the BIOS setup and from there into Integrated Peripherals to eventually find the SATA mode options.

Dick Silbar

---

### Post by wib on 2008-04-30
I read the thread...all of it.  Could never get a string response. Using older Asus mobo, A7A133 w/ 1.2G RAM and a Deathstar IBM HD.

Nominal installs during HH beta, but when I was installing LTR the Verbatim 52x CD-RW died or stopped being recognized. I replaced it with an LG CED8080B and then could never get past the BusyBox. 

As suggested, replacing the IDE device worked instead of using the all_generic_ide command.  Since this whole system is built from a pile of pulled parts it was simply a matter of finding the right combination. In this case it was a Sony CRX 140E CD-RW.

I'm all grubbed up and now can hopefully solve [Bug #218508. ]("https://bugs.launchpad.net/ubuntu/+bug/218508") Maybe that's why my network connection and the CD-RW failed: there may be a general problem of Ubuntu not having enough testing on specific drivers for the enormous permutations of installed hardware. I'm on my second HD, third CD-RW, and now headed for a third network card. Keep trying, folks.

---

### Post by louyo on 2008-04-30
:KSDecided to give another go and downloaded the alternate CD image. That one installed. I still see the same messages when booting up the new install but it boots up and runs OK (actually switched over to Kubuntu now). I will try to locate another CDROM drive to see if that makes a difference. Also have to look through the logs. I never did get the liveCD to boot. 
Thanks to all the folks who are hanging out here and helping.

---

### Post by kav on 2008-04-30
I don't know if it helps to find the clue or even makes it more complicated, but my story is the following:

Toshiba portege 3505, 512 ram, 60gb IDE, Pentium III, ACPI 1.40, trying to install 8.04

Live CD or installation drops me to Busybox, none of the tricks mentioned in this thread worked for me.
What I did was to remove my HDD and put it in another laptop, where I installed ubuntu without any problems. 

I put my disk back to my laptop and... get the busybox thing!
In recovery mode what I get is the following:

[http://img230.imageshack.us/img230/7559/ubuntupn4.gif](http://img230.imageshack.us/img230/7559/ubuntupn4.gif)

sda4 is the linux partition so it definitely exists.

In normal mode after removing 'quiet' it stops after

```
Mounting root file system
Running /scripts/casper-premount -- ok
```

...and then drops me to busybox.

---

### Post by tofuconfetti on 2008-04-30
After all this, I decided on that particular computer to revert back to 7.10.  It did the same thing.  I hadn't remembered that, but it finally dawned on me that previously I had disabled the "USB legacy support" in the BIOS of that motherboard.  I did that again and had absolutely no problems booting up.  Then I remembered that was required of another Intel based ASUS motherboard.

So I closed down the 7.10 Live CD and tried the 8.04 CD with the legacy USB disabled.  It worked like a charm with no parameters passed to the kernel line.

The only downside to this is that you can't select the options in the boot menu IF you are using a USB keyboard.  You can, of course, solve this with a PS2 connected keyboard just for the setup (I always keep one around).

Add that as another one to try on your list of possible solutions.

The hardware I had success on was:

Intel D975XBX2 motherboard
e6600 quadcore chip
4 Gb of RAM
Nvidia 8800 GTX video
WD 500 Gb SATA drive on SATA1
SATA DVD+/-RW on SATA5
No floppy as registered as such in the BIOS
USB Keyboard/Mouse

---

### Post by Brendt2 on 2008-05-01
I just wanted to thank everyone for there input into this matter.

I have a Vostro Desktop 200 that hit this crazy issue, and irqpoll solved everything for me.  I am now functional again!

I love the ubuntu forums!

---

### Post by tofuconfetti on 2008-05-02
What would be nice to know is exactly where the bug is that's giving everyone these errors.  They are obviously widespread. There is something strange in the kernel that's causing drives not to be recognized.

---

### Post by hal8000 on 2008-05-02
> **tofuconfetti said:**
> What would be nice to know is exactly where the bug is that's giving everyone these errors.  They are obviously widespread. There is something strange in the kernel that's causing drives not to be recognized.


I have had the same problems booting Ubuntu since 6.10 (the last Ubuntu that installed from the CD without problems).

My solution was to compile my own kernel, this works, but its not the most elegant solution and outside the scope of a newbies. I have a feeling that its somehow tied in with the libata library as this is when my problems started.

I hope someone can provide an answer.

---

### Post by wconstantine on 2008-05-02
Would indeed be nice to have some attention over here from the developers of Ubuntu. I've had problems with installing Ubuntu with my JMicron system for as long as I can remember. First time I tried was 6.10 if I remember it correctly. 7.04 (or 7.10) was the first distrobution I succeeded in installing. I think it was due to a kernel fix that existed in the new kernel 7.04 used. Has that fix been stripped away due to this LTS stuff? 

I'm going to try to download 7.04 again and try installing it and then doing a dist-upgrade. I've already tried with 7.10 and it didn't work. So I have little hope for 7.04.

This is one of Linux's issues folks. The average joe will need a working OS. Not some shell dropped before their eyes.

---

### Post by hal8000 on 2008-05-02
> **HDave said:**
> For those of you still having problems -- can you verify that the UUID in the grub /bppt/grub/menu.lst matches your /etc/fstab and is actually the right value for your hard drive?

They were different in my case...and I got dumped into busybox too.

Hi, can you elaborate on this please? Are you saying that you modified your grub/menu.lst file and can now load Ubuntu 8.04 without problems.

I am multi booting, but using an alternative (PCLinuxOS) grub to control booting, however I still cannot boot Ubuntu without using a non ubuntu kernel. So far changing BIOS settings to non pata, sata, and adding generic_ide_devices irqpoll have all failed for me... however the live CD boots ok, but not the permanent install.

I will load the live CD, copy the kernel and modules into my installed 8.04 system  and see if that cures my initramfs problems.

---

### Post by wconstantine on 2008-05-02
> **hal8000 said:**
> Hi, can you elaborate on this please? Are you saying that you modified your grub/menu.lst file and can now load Ubuntu 8.04 without problems.

I am multi booting, but using an alternative (PCLinuxOS) grub to control booting, however I still cannot boot Ubuntu without using a non ubuntu kernel. So far changing BIOS settings to non pata, sata, and adding generic_ide_devices irqpoll have all failed for me... however the live CD boots ok, but not the permanent install.

I will load the live CD, copy the kernel and modules into my installed 8.04 system  and see if that cures my initramfs problems.

The boot parameters you have described there are wrong. :)

"all_generic_ide" is the right one. Anyways, I guess you have added the boot parameters in the /boot/grub/menu.lst file? If not, do it and it'll should work for you.

Adding the boot parameters when launching the live-cd is not enough. It doesn't remember the parameters given when launched so you need to add it yourself in the right line in the meny.lst file.

If you already have done so, sorry. Your reply is not quite so detailed, just wanted to make sure. :)

---

### Post by tofuconfetti on 2008-05-02
> **hal8000 said:**
> Hi, can you elaborate on this please? Are you saying that you modified your grub/menu.lst file and can now load Ubuntu 8.04 without problems.
When you get booted into the 8.04 installed system (not the Live CD), then you can hand edit the /boot/grub/menu.lst file.  It will have a line that passes parameters to the kernel as it boots up.  The line will look something like this ...

```
kernel  /vmlinuz-2.6.22-14-generic boot=UUID=349b7b5f-a9af-4f81-abb3-56bb54a72a70 ro quiet splash
```

At the END of that line add whatever parameters you want to pass at boot up.  If you really get stuck and can't pass parameters from the graphical grub menu, you can actually boot into the Live CD, mount the system partition (or the partition with /boot on it, I put it on it's own paritition - an old habit from the Gentoo days) by loading up the terminal and typing ...

```

sudo mkdir /mnt/system
sudo mount /dev/sda1 /mnt/system
nano /boot/grub/menu.lst

```

NOTE: you will need to change the /dev/sda1 to whatever partition your /boot/grub/menu.lst is on.

Then add the parameters to that line, and SAVE it before you close it.  Then shut down the Live CD, reboot into 8.04 and the parameters will be passed.

For the record, I did NOT have to add "all_generic_ide" to mine.  I either had to set the USB Legacy settings to "off" in the BIOS, or had to pass "irqpoll" to the kernel.  I don't know WHY this works, it just does.  Until we have a firm answer, you may have to try them individually to see which one works for you.

> **hal8000 said:**
> I am multi booting, but using an alternative (PCLinuxOS) grub to control booting, however I still cannot boot Ubuntu without using a non ubuntu kernel.
Then boot into the PCLinuxOS and edit the Ubuntu boot line passing the parameter.  That's even easier.  Just edit /boot/grub/menu.lst and add it to the UBUNTU line (not the PCLinuxOS line.

> **hal8000 said:**
> So far changing BIOS settings to non pata, sata, and adding generic_ide_devices irqpoll have all failed for me... however the live CD boots ok, but not the permanent install.
Did you say you were using a non-Ubuntu kernel??  That's not good.  Install 8.04 fresh using their kernel.  That should work IF the Live CD works okay.

> **hal8000 said:**
> I will load the live CD, copy the kernel and modules into my installed 8.04 system  and see if that cures my initramfs problems.
I wouldn't do that.  Let the installer do it.

Maybe some of that will help you.

---

### Post by hal8000 on 2008-05-03
> **tofuconfetti said:**
> When you get booted into the 8.04 installed system (not the Live CD), then you can hand edit the /boot/grub/menu.lst file.  It will have a line that passes parameters to the kernel as it boots up.  The line will look something like this ...

```
kernel  /vmlinuz-2.6.22-14-generic boot=UUID=349b7b5f-a9af-4f81-abb3-56bb54a72a70 ro quiet splash
```


Maybe some of that will help you.

Hi, thanks for all your help.

Looking back through my own notebook, I have had trouble booting Ubuntu since 6.04, think this is when the Ubuntu kernel used the libata library.

Looks like I may have passed the wrong kernel parameter.
Looking back I to 6.04 a kernel module was missing.
I used the livd CD chroot'ed into my ubuntu system and added piix to /etc/initramfs-tools/modules and created a new initramfs

I have just added piix to the modules in Hardy Heron and updated the initramfs-  for a brief second I thought this was going to boot, but after a few lines of text I get a black monitor screen (no text or graphic displayed) then drops to initramfs

One thing I notice between live install and hard drive install is that the boot splash screen changes. The live install gives the familiar Ubuntu logo, after a live install I see what looks like a TV test card, which hangs on waiting for root filesystem then drops to initramfs.



I am still convinced that libata is the problem, in Suse you can disable libata by appending hwprobe=-modules.pata to grub/menu.lst

This only works in Suse as it is parsed by Suse central config file /etc/sysctrl (I think,from memory).
If anyones knows a way to disable libata support from grub/menu.lst I'll give this a try.

I am going to go through your suggestions and all posts in this thread again. My hardware:
Asus P4P800-E motherboard
Intel P4 2.8G
Nvidia 7600GS
1G Ram
Maxtor UDMA100 HD (IDE not sata)

---

### Post by silviutp on 2008-05-03
> **Jong said:**
> OMG, I'm up running with Hardy now :lol:
No IDE to RAID switch, nor enabling the floppy drive (I disabled it again).

Using the desktop live cd, what did the trick for me was adding ```
all_generic_ide floppy=off irqpoll
``` to the boot options when pressing F6. I can't tell if you really need all three options. I'm just happy to be up running :D

Hope this may help someone - good luck to everyone.

Thanks for help. This did it for me too.

---

### Post by wconstantine on 2008-05-03
THIS DRIVES ME CRAZY.

Has ANYONE succeeded in even launching the live-cd for 8.04 with MSI P965 Neo?!

I have 2 sata drives and one IDE cd-rom. I've tried with Wubi, A LOT OF BOOT PARAMETERS on the live-cd and I've also tried 7.04/7.10 which I've successfully run before. But none of them works anymore. I'm not dropped into busybox with 7.04/7.10 but the computer locks up and the pc speaker beeps constantly.

In 8.04, you can't even hear the cd is being read. It just loads a little and then drops into busybox. So damn annoying.

Boot parameters I've tried:

```
irqpoll noirqdebug all_generic_ide noapic nolapic floppy=off pci=nomsi nomsi
``` 

LET ME TASTE THAT UBUNTU GOODNES, I CAN'T STAND WINDOWS ANY MORE.

---

### Post by dartdog on 2008-05-03
FWIW I did a wubi install, went through the entire install and reboot sequence with a Dell opti.. was happily in Ubuntu, went back to win xp for a while... had a thunderstorm shut down power and used the opportunity to go back into Ubuntu after the power came back...
 Got the mysterious initramfs + busybox prompt...
rebooted , same thing... went to these forums after getting win XP back...read this thread and others.. was about to figure out how to apply some of the suggestions... but... when rebooting all went well and I'm writing this in Ubuntu... I guess running XP reset some bios? or cleared some hardware states that were not cleared with a powerdown...??? As I said.. Probably won't help anyone else but you never know>>>!

---

### Post by herdivet on 2008-05-04
Add this to the FWIW column.  I have a dual boot system I put 8.04 beta on, and applied updates.  Eventually I got the busybox, but if I chose an earlier version, it came up fine.  I just did that for a while, until another update occurred and suddenly everything was fine.

On my 'working' system, I upgraded from 7.1 to 8.04.  Yikes.  It looked great immediately after the upgrade, but then I ran the 'updates' and it's been stuck with busybox everytime, unless I pick an older version from the grub menu.  It actually has four versions (not counting recovery modes) on the grub menu, with linux-version-2.6.24.17 linux-version-2.6.24.16 linux-version-2.6.22.14 and linux-version2.6.20.16.  The 2.2.24.17 ALWAYS busyboxed until I put the recommended all-generic-ide on the loader.  That allowed it to boot -thanks for the help.

However - it boots with graphics set to 640x480 and only offers 320x240 as the other option (reminds me of the old PC XT with mode80 and mode40!)  The card is an nvidia GeForce 6150LE but the driver, when I get it to load, still only offers 640x480.  By booting to the 2.6.22 version, I can get 800x600 w/out the nvidia driver, but I sure miss Ubuntu 7.1 with 1024x768 and booting without having to drop back a few versions.

It appears some of these problems are with the Linux kernel, based on how it gets worse with 2.6.24.  I'  hoping to hang on with 800x600 for a while and hope an upgrade shows up soon to fix this.

Just FWIW and thanks for all the help.  This has been the most informative thread on this topic I've seen.  At least it gave a solution that got the system to boot.  Thanks again!

---

### Post by jbr6700 on 2008-05-04
Well after messing around and trying all else I finally edited grub boot options using what seems to be the Silver Bullet for most people trying to get HH 8.04 running. Here is what my grub list reads now: 
[B]title		Ubuntu 8.04, kernel 2.6.24-16-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=2a123592-7e9f-4dc2-980c-683f994c2e26 ro quiet splash all_generic_ide floppy=off irqpoll
initrd		/boot/initrd.img-2.6.24-16-generic
quiet[/B]

I'm not sure which addition solved the issue but at present all looks well here. Running the Nvidia restricted drivers as well as Compiz Fusion went flawlessly, no issues with sound like I had in Gutsy either. Playback of encrypted DVD's took a different approach than what is posted in Community Documentation. AWN runs great as well. I am seeing some issues with Firefox occasionally when I move the mouse it occasionally backs up to the prior window!? That one might require waiting till Firefox is out of Beta to see if it continues. Thanks to Jong for their fix.

---

### Post by Rogerbeep on 2008-05-04
BIOS is a function of any motherboard regardless of the operating system. It is a small set of instuctions that tell the hardware setup how to turn themselves on and at what basic settings. It is accessed in various ways depending on the motherboard. Many require pressing the delete key during the boot process. After you press the power key you should hear a beep from within you case. This is the motherboard's PC Speaker. Directly after you hear this beep you must press the appropriate key to enter BIOS. Try the delete key. If this is not the corrrect key for your motherboard and you cannot find the correct key in your motherboard's documentation then try the insert key or the F8 key. One of these should work. Also, pay attention to your initial boot screen. It goes by fast but you can hit the pause key to stop the progress. It should tell you what key needs to be pressed to get into BIOS.
 Once you access BIOS there are many settings that cane be changed but please be careful what you change and I suggest changing one setting at a time unless you are well versed in BIOS settings. This way if you machine will not boot properly you will be able to go back and reverse the change. If you get stuck and have it all completely botched up there is a way to physically reset the BIOS back to it's original default settings. It requires moving a jumper on the motherboard. You must have the proper documentation specific to your motherboard to do this but it is s simple procedure. If all else fails you can shut down your machine. Pull the A/C plug out and then remove the motherboard's battery (a small shiny silver disk like the battery in a car's remote door unlock)for a couple of hours. this will force it to revert to the factory defaults.
 Good luck, I hope this helps....

---

### Post by tofuconfetti on 2008-05-04
> **wconstantine said:**
> 
Boot parameters I've tried:

```
irqpoll noirqdebug all_generic_ide noapic nolapic floppy=off pci=nomsi nomsi
``` 


Wconstantine,

I don't know if you caught that one post I made regarding using a USB keyboard that prevented me from booting on an Intel system.  What is your hardware setup?  List an inclusive list down to the keyboard.  On my Intel motherboard with the quad-core processor I had to disable legacy USB support in the BIOS when using a USB keyboard.  I understand your frustration.  Try plugging in a PS2 keyboard and see if THAT works.  That is one thing that worked for me, hopefully it'll help you.

The problem here is that I see no pattern to why any of this works.  I have several MSI motherbords and none of them was a bit of trouble.  It's just the Intel motherboards I've tried that give me a hassle.

---

### Post by hal8000 on 2008-05-04
I've still not got Ubuntu 8.04 booting on my system Asus P4P800 E motherboard, Intel 865PE chipset and UDMA hard drives.

In my case the Live CD works and boots fine, but an installed system will not boot, taking me to an initramfs shell.


I can boot Ubuntu if I use a Debian 2.6.24 kernel proving that the problem is the configuration of the Ubuntu kernel. I am convinced the answer lies in disabling libATA and just found the following on the libata site:

[http://linux-ata.org/faq.html](http://linux-ata.org/faq.html)

    * Recommended (where BIOS permits): Change BIOS IDE mode from "legacy" or "combined" mode to "AHCI" (recommended), "RAID" or "native".
    * Boot with the kernel commandline parameter "combined_mode=libata" or "combined_mode=ide" to allow the specified driver to claim all IDE ports.
    * Disable libata (CONFIG_ATA) entirely, and enable CONFIG_BLK_DEV_IDE_SATA.
    * (newer choice, with less field testing) Disable CONFIG_IDE, and permit libata to run all your IDE and SATA ports.


Adding the parameters 
combined_mode=libata  or combined_mode=ide may work as suggested above, but as the Ubuntu kernel config has CONFIG_ATA set to y this may be the only way to disable libATA. This solution isnt quick as it would require
booting from the LiveCD (for those that can) chroot'ing into the installed Ubuntu system, downloading the kernel source and then recompiling the kernel.
This would work (in my case) as my alternative kernels (Debian have ConFIG_ATA disabled).
If an alternative kernel was available from synaptic this may be an alternative solution.

---

### Post by wconstantine on 2008-05-05
> **tofuconfetti said:**
> Wconstantine,

I don't know if you caught that one post I made regarding using a USB keyboard that prevented me from booting on an Intel system.  What is your hardware setup?  List an inclusive list down to the keyboard.  On my Intel motherboard with the quad-core processor I had to disable legacy USB support in the BIOS when using a USB keyboard.  I understand your frustration.  Try plugging in a PS2 keyboard and see if THAT works.  That is one thing that worked for me, hopefully it'll help you.

The problem here is that I see no pattern to why any of this works.  I have several MSI motherbords and none of them was a bit of trouble.  It's just the Intel motherboards I've tried that give me a hassle.

I've got both an USB keyboard and mouse. I'll try changing those when installing to give it a try. Thing is, I've just changed my keyboard from PS2 to USB, so you might be right. Gonna eat, then I'll try it out.

Edit: Didn't work. Tried disabling USB controller completly in the bios as well.

---

### Post by revoltism on 2008-05-06
> **wconstantine said:**
> It seems like all_generic_ide floppy=off irqpoll is the solution for those with an Asus board with JMicron? Not for MSI. I can't get it working.

Yes, but in my case i used the alternate cd and installed from my dvd-rw-rom instead of my dvd-rom. to get it to work.. but i still got the slow boot

EDIT: After adding "all_generic_ide floppy=off irqpoll" to menu.lst i booted within 10 seconds...

---

### Post by wconstantine on 2008-05-07
> **revoltism said:**
> Yes, but in my case i used the alternate cd and installed from my dvd-rw-rom instead of my dvd-rom. to get it to work.. but i still got the slow boot

EDIT: After adding "all_generic_ide floppy=off irqpoll" to menu.lst i booted within 10 seconds...

You got it working with a P965 Neo and the alternate cd?

Edit: I'VE GOT IT WORKING! AT LAST!

Used the alternative 8.04 cd and the boot options as seen: all_generic_ide floppy=off irqpoll

---

### Post by Toddish on 2008-05-09
hey guys

im still stuck :(

I got busybox too (im on an Abit AB9, E6600, 2gb Ram, 1 500Gb SATA, 1 250Gb SATA), and all_generic_ide floppy=off irqpoll actually got ubuntu to load, but now it suddenly freezes.

just locks up, stops loading, and I can't move my mouse (PS2, as is the keyboard).  reckon its part of the same problem, or should I make a new thread about it?

---

### Post by ludefork on 2008-05-10
For Dell Ubuntu users: I've had the same problems described here. An Ubuntu tech support person at Dell told me to "flash the BIOS" on my system, i.e. upgrade the BIOS. He gave me a link for instructions on how to flash the BIOS. This is the link:

[http://linux.dell.com/wiki/index.php/Repository/firmware](http://linux.dell.com/wiki/index.php/Repository/firmware)

After flashing the BIOS correctly, I still had the same problems booting up - with "intramfs" and "busybox" being displayed on the screen. But changing IDE to RAID in peripherals during bootup fixed my problem completely! I can now run Hardy and it works fine (prior to flashing the BIOS, changing IDE to RAID did not fix the problem). My system is Dell Inspiron 530 Desktop, PCO, E2160 (1.8 GHZ), 4 gig memory.

---

### Post by epidemiks on 2008-05-11
Hi guys,

My problem seems similar.. I have managed to get the update installed, but when i try to boot to the -17 kernels i get:

```
ata1.01: exception Emask 0x0 SAct 0x0 SErr 0x0 acion 0x2 frozen
ata1.01: cmd C8/00.08.00.../fo tag 0 dma 4096 in
Buffer I/O error on device sdb, logical block 0
```
and then get the busy box prompt.

but the -14 kernel boots ok, says it's 8.04 and runs well..

would the above errors relate to this sata/bios fix? I don't run any sata drives and i'd imagine XP on the second ide wouldn't like being told it's sata.. or am i wrong?

also, its hard enough for me to understand whats going on in this page, so apologies if I've missed solution in the preceding 11 pages.. :)

---

### Post by hal8000 on 2008-05-11
> **epidemiks said:**
> Hi guys,

My problem seems similar.. I have managed to get the update installed, but when i try to boot to the -17 kernels i get:

```
ata1.01: exception Emask 0x0 SAct 0x0 SErr 0x0 acion 0x2 frozen
ata1.01: cmd C8/00.08.00.../fo tag 0 dma 4096 in
Buffer I/O error on device sdb, logical block 0
```
and then get the busy box prompt.

but the -14 kernel boots ok, says it's 8.04 and runs well..

would the above errors relate to this sata/bios fix? I don't run any sata drives and i'd imagine XP on the second ide wouldn't like being told it's sata.. or am i wrong?

also, its hard enough for me to understand whats going on in this page, so apologies if I've missed solution in the preceding 11 pages.. :)


Any messages that start ata..  (like the ones you pasted) are from libATA emulation. There are clear and present problems like this for at least 10,000 users so why havent the ubuntu team compiled a different kernel that does not use libATA emulation?
I havent had time to recompile the ubuntu kernel yet, but as a non libATA compiled kernel boots my 8.04 system I'm certain this is the 'root' cause of the problem ~(no pun intended).

The thread is long but some solutions (though they dont work for everyone)
including appending comments to the boot line, or changing settings in BIOS. Hope that helps

---

### Post by mptpro on 2008-05-12
Hi Dick,

I have the same computer - Dell 530.  Have you gotten it to install 8.04?  I have not.

thanks,
Michael

---

### Post by epidemiks on 2008-05-12
I've tried clearing the bios, irqpoll, enabled sata, still getting buffer i/o error on device sdb, logical block 0
still nothing

---

### Post by macr0s on 2008-05-14
Sup

I ran into this problem install 8.04 desktop cd on my old p4 system.

None of those boot paramaters worked for me but this did:

1. Put the hdd and cdrom drive on different ide channels, both master.
2. left a single stick of ram in there (im paranoid about ram errors). Alternatevely run a ram check if you are patient.

good luck

edit: the pc i had this problem on was actually an athlon xp 1400, ASUS mobo - A7A133 with ALI chipset

---

### Post by eleybourn on 2008-05-15
> **felipe de la muerte said:**
> ok my hardy heron seems to work now, too!

all the bootoptions did not help. what i did was that i put my cd-writer from primary slave to secondary slave, and everything worked fine. i really don't know why. maybe this can help someone.

no i've got my dvd-rom on primary master and the cd-writer on secondary slave (i have to change the jumpers to get it on master), and my harddisk on the s-ata port. maybe the dvd-rom and cd-writer interfered somehow.
I don't know why or how, but unplugging my IDE DVD Burner also worked. I have tried everything listed in all the forums, ide_generic_all, pci=nomsi, irqpoll, floppy=off etc.

I will go and buy a new IDE cable so I can plug it into the secondary IDE slot (I have a HDD on the first cable)

---

### Post by 52rockwell on 2008-05-17
I had this problem on my Dell 530 Inspiron. The computer I bought because dell was offering Ubuntu preinstalled. 
The Bios switch to RAID worked for me.
  I just googled busybox+ubuntu.   Wow..
This is really a big problem

---

### Post by gmilne on 2008-05-19
How DO I get into BIOS?

Since you guys seem informed can anyone tell me how to install Ubuntu to Drive E:\?
I have XP on bootable F:
C and D are storage disks 
I think Ubuntu keeps trying to install itself on C:

Any help much appreciated.

---

### Post by herdivet on 2008-05-19
To get in to the BIOS you press a key, usually <F2> <DEL> <F1> <F10> - the screen may put up a very quick message saying which to press to enter BIOS Setup.  You can usually press one after the other until it says it's entering setup.

During the installation process the default is to install Ubuntu on the first HDD.  If you're comfortable with it, you can unplug all drives except the one you want Linux on.  If not, you can choose Manual and then pick the drive you want to put Linux on.  The drive descriptions will be HDA SDA etc. so you will have to look closely to ensure you pick the one you want!

---

### Post by gmilne on 2008-05-19
Problem with that is my two 80G drives  - 1 with XP and the other blank have the same number affixed to them. My two 400G also have identical numbers. Is there a workaround?

If I do get to the blank drive and install Ubuntu on it will Ubuntu put a boot manager on the drive so that I can get back to XP if need be.?

I think I can change the boot order with Disk Manager in Windows. But then how do I get back to XP (and boot manager after the Ubuntu install?

---

### Post by herdivet on 2008-05-19
Yes, Linux will add the GRand Universal Boot loader (GRUB) to the first drive so you'll have a menu with XP as an option.  If you cancel the install as soon as it starts, then run SYSTEM | ADMINISTRATION | SYSTEM MONITOR and click on the File Systems tab it will show the drives, with designation, file system (NTFS/ext3, etc.) and free space.  That should make it easy to pick the empty one.  Note which one it is and then double click the Installation folder on the desktop to restart the install.

Hope that helps.

---

### Post by gmilne on 2008-05-19
Thank you so much. Installation seemed to go well, however when I get the boot manager menu and pick Ubuntu I eventually get the initranfs message again. Can you give me an idea of what is wrong here?

I made a 
Root partition of 15G
Swap File 10G
Home 55G

I was unable to import Docs and Settings but imagine I can do that later.
Cheers,
/graham

---

### Post by gmilne on 2008-05-20
Install seemed to work fine, but this time get just initranfs. 
When I type man intro it returns
/bin/sh: man: not found

Any ideas.

I can boot to XP fine but Ubuntu (7.01) just sits there like my last wife and gives me the silent treatment. 

Should I be changing the boot order of disks in the BIOS or anything?
Any help appreciated.

---

### Post by gmilne on 2008-05-20
*I found this but because it's for Dell I hesitate to use it. Any idea if it works?*

This worked with "Made for Ubuntu" Dell 530N. If your machine is hanging here and not booting then it's worth a shot for you too surely?

Press "Esc" before/during Grub "Countdown". Press "e". Find the line "kernel-blah-blah" (it doesn't really say blah but you are following right?) Go to the end of the line type: irqpoll Press then "b" to boot.

Once Ubuntu/Gnome has booted open a terminal...

sudo gedit /boot/grub/menu.lst

Search for "# defoptions=quiet splash"

Change to "# defoptions=quiet splash irqpoll"

Save and exit your editor. Type:

sudo update-grub

Reboot. This should now boot into Ubuntu/Gnome without hanging at busybox/initramfs

---

### Post by nikolay.dimitrov on 2008-05-21
Hello, I have ASUS A7N8X-VM/400 (nVidia nForce 2) with AMD Sempron, 1 PATA HDD, 2 DVD-ROM and USB wireless Keyboard and mouse. I have the same problem with the installation - with BusyBox initramfs. I solve the problem with 'ide_generic_all irqpoll floppy=off' at the end of the command line (F6 at startup). I write the commands before '--'. After the installation I have no more problems. Thanks all for help.

---

### Post by hannah187 on 2008-05-21
I am here with same problem. Please look into this post of mine a week back.
[http://ubuntuforums.org/showthread.php?t=791518](http://ubuntuforums.org/showthread.php?t=791518)

I have installed 8.04 with alternate CD however cannot boot and get initramfs + busybox

Disabled USB Legacy support in BIOS
Change BIOS IDE mode from "compatibility" mode to "AHCI" 

Have tried following parameters

all_generic_ide floppy=off irqpoll
combined_mode=libata
irqpoll noirqdebug all_generic_ide noapic nolapic floppy=off pci=nomsi nomsi

still no success

My Notebook is
Toshiba Satellite Pro L300 PSLB1A  (IN Australia) same as 
Toshiba Satellite Pro L300 PSLB1E  (In Europe)

You can see some more details and pics of GPARTED in this thread


[http://ubuntuforums.org/showthread.php?t=791518](http://ubuntuforums.org/showthread.php?t=791518)

Many thanks for the help

---

### Post by shoeheight on 2008-05-21
I'm having the same problem.  I am using Wubi for a dual boot with XP and can't boot Ubuntu anymore.  I had been running it fine for the past few weeks but suddenly...I get this (initramfs) screen.  

I've been reading this thread but I'm a little worried about changing the bios on my office computer.  If I change the boot like <gmilne> has so clearly written, could it affect my XP boot?  (I backed up all my info on the Ubuntu boot so I don't mind loosing it)

Sorry, maybe this is more of a beginner question.
:confused:

---

### Post by sprightlyone on 2008-05-21
hi 
  i was getting same error messages as everyone else ihave 2 burns with different distro`s neither would work 
 fix for my install was visit bios &turn on sata controller  now i can install all my disks 
  i `m trying to setup on a VIA  MM3500 m?board with smll IDEdrive 
 this may be of use to someone 
  thanks for this post  
  the answer may still lie in tweaking BIOS if your board has SATA ports 
lyle

---

### Post by hal8000 on 2008-05-23
I've solved my Ubuntu loading problems, but this solution is possibly not going to work for everyone.

In my case I reverted back to Edgy (6.06) which worked without problems. I upgraded to Feisty but needed to append irqpoll to the grub parameters.
Although Feisty worked, checking dmesg revealed many messages relating to my cdrom drive.
I had a DVD drive and a CDROM sharing the same IDE cable and two IDE drives sharing the same IDE cable. IRQ sharing should not be a problem these days, but did affect my install. Only when I removed a device from each cable did the system boot without errors, and using libATA emualtion (IDE hdx drives now seen as sdx drives).

The cost of a 160G SATA drive is now under £30, at this price its a good buy. On my Asus P4P800E motherboard Intel 965 chipset and ICH5 hardware, the performance is excellent:

sudo hdparm -tT /dev/sdb

/dev/sdb:
 Timing cached reads:   2038 MB in  2.00 seconds = 1019.29 MB/sec
 Timing buffered disk reads:  226 MB in  3.02 seconds =  74.81 MB/sec

The above is a Native Hitachi Deskstar SATA2 drive, my IDE drive is slightly slower:

 sudo hdparm -tT /dev/sda

/dev/sda:
 Timing cached reads:   1968 MB in  2.00 seconds = 983.49 MB/sec
 Timing buffered disk reads:  168 MB in  3.02 seconds =  55.54 MB/sec

The solution may not work for everyone but for my computer, shifting IDE connectors ( a single device on each IDE controller and no shared interrupts has worked for me).

---

### Post by beyboo on 2008-05-25
> **Caligatio said:**
> I'm going to bump this as there's a lot of 1 post threads that I think are duplicates of this.

I'm running a ABIT IP-35 board... my boot problem is intermittent.   It won't work for like 5 attempts.. I go into Vista to look at posts.. try again and it works.

There's a few launchpad posts about this.. apparently it may be a problem with the kernel version.

DITTO ! 

I came in to search for support of my Abit IP35-E mobo. Since Gutsy I've had problems installing the OS. The mobo has 6 SATA ports on the mobo out of which # 1,2,5,6 are enabled. 3 and 4 are disabled as part of the mobo hardware spec. I have Seagate and WD SATA disks installed on ports 2,5 and 6. For some reason whenever I boot from the Hardy live CD, I always get the ATA4 revalidation error when I boot. 

In Gutsy I managed to install the OS after removing the disks in ports 1 and 2. AFter that I installed the latest Kernel back then 2.4.26 from kernel.org and it worked. However it boots only 50% of the time. Most other times it just hangs at "Waiting for Root File System" and has to be reset a couple of times. USually entering the bios screen and saving (no changes made) works and the system boots ok. On some occassions I just reboot in to Windows XP and then restart and its sorted out. 

I havent been able to boot the Hardy disk as well on this machine. Though I am not in a hurry, I got an ACER 5920 laptop and Hardy works on it like a breeze.

---

### Post by jward3010 on 2008-05-25
I'll put in my tuppence happeny worth.

I have a Sony Vaio VGN-A397XP which uses a 100GB S-ATA drive but has a hopelessly optionless BIOS with no options for AHCI and RAID modes and hence I'm having this problem with "initramfs / busybox" etc.

This I have to say is pretty bad for Canonical, I assume that before it's released officially that the installation is tested on hundreds of different configurations in terms of different laptops, PC's, motheboards, drive configurations etc. How this was missed is hard to understand. Anyway I suppose where they should be praised is the fact that this cost me nothing and it's a genuinely good work in progress with this being a bit of a balls-up.

I've included a picture of what exactly comes up. It will be good for reference and I haven't seen one yet that shows the exact error.

---

### Post by hal8000 on 2008-05-25
> **beyboo said:**
> DITTO ! 

I came in to search for support of my Abit IP35-E mobo. Since Gutsy I've had problems installing the OS. The mobo has 6 SATA ports on the mobo out of which # 1,2,5,6 are enabled. 3 and 4 are disabled as part of the mobo hardware spec. I have Seagate and WD SATA disks installed on ports 2,5 and 6. For some reason whenever I boot from the Hardy live CD, I always get the ATA4 revalidation error when I boot. 

In Gutsy I managed to install the OS after removing the disks in ports 1 and 2. AFter that I installed the latest Kernel back then 2.4.26 from kernel.org and it worked. However it boots only 50% of the time. Most other times it just hangs at "Waiting for Root File System" and has to be reset a couple of times. USually entering the bios screen and saving (no changes made) works and the system boots ok. On some occassions I just reboot in to Windows XP and then restart and its sorted out. 

I havent been able to boot the Hardy disk as well on this machine. Though I am not in a hurry, I got an ACER 5920 laptop and Hardy works on it like a breeze.

Have you by chance got 2 optical drives on an IDE connector sharing the same interrupt? This was my manin problem and now having a different device on a different connector works a treat. You could try removing the connector and see if that helps.

---

### Post by batmanjohnson on 2008-05-27
> **'om1n[A]e said:**
> works for me now, only thing needed was irqpoll...

worked for me, too. (dual boot via wubi). edited via regular boot sequence, not live cd. selected ubuntu, 'e' to edit, etc...... nice. this problem just started occurring, i had been using 8.04 successfully for days......strange.

---

### Post by wdl71 on 2008-05-29
I AM a newbie to Ubuntu and get stuck at busybox with a "try 8139too driver" message and am clueless.  Also have an SATA drive.  I'll try the AHCI method but beyond that don't know.  Hopefully they will come out with a version of Ubuntu for clueless people like myself that will do everything for us called Nuubuntu or Buubuntu.

---

### Post by bgreenaway on 2008-05-30
Just to add my tuppence worth as I have just (hopefully) solved this:

My hardware setup is a HP Media Center m7160n with a single Maxtor 250 GB SATA drive. Did not have the SATA option in BIOS to change to RAID (as suggested in earlier posts).

This problem was resolved for me by adding the **all_generic_ide floppy=off irqpoll** to the install option. So far, installation of 8.04 running smoothly. Will see what happens upon completion, however.

---

### Post by Li1t on 2008-06-01
> **bgreenaway said:**
> This problem was resolved for me by adding the **all_generic_ide floppy=off irqpoll** to the install option. So far, installation of 8.04 running smoothly. Will see what happens upon completion, however.

I was having a similar problem, except that the CD worked the first time I tried it. I reset as it used an auto-detected resolution which was too high (1600x1200, which worked but wasn't ideal as my old monitor displays part of it off the screen), and teh next time I ran it up it dumped me into busybox. Strangely, it got past that stage the first time for both Ubuntu and Kubuntu KDE4, but I reset from the installer both times opting to instead install from the live CD where I could change the resolution. I had exactly the same problem with both versions, it worked the first time but not subsequent ones.

That exact set of options, "**all_generic_ide floppy=off irqpoll**" in that order if it matters, worked for me too on my Asus A7N8X-E Deluxe with ATI9700 Pro and IDE HD.

Note, someone a page or so back mistyped ide_generic_all instead of all_generic_ide. The correct option is the one with all at the start, so: **all_generic_ide**

---

### Post by bgreenaway on 2008-06-02
> **bgreenaway said:**
> Just to add my tuppence worth as I have just (hopefully) solved this:

My hardware setup is a HP Media Center m7160n with a single Maxtor 250 GB SATA drive. Did not have the SATA option in BIOS to change to RAID (as suggested in earlier posts).

This problem was resolved for me by adding the **all_generic_ide floppy=off irqpoll** to the install option. So far, installation of 8.04 running smoothly. Will see what happens upon completion, however.

Just to conclude that the 8.04 installation completed successfully and everything is running sweet.

---

### Post by robtjr30 on 2008-06-04
After I update Ubuntu 8.04 I and install all add-ons I reboot Ubuntu and I get the BusyBox V1.1.1.3(Debien 1:1 1.3-5 Ubuntu 12)Built-in Shell (ash)
Enter 'help' for a list of built in commands.
(initrants)
I do not know how to get back into Ubuntu I tried the Restore option through another Reboot and still the samething 
What do I do?
I am running Windows XP Pro along with Ubuntu.

---

### Post by Kujen on 2008-06-05
Posting this from a Dell Inspiron 530. The "all_generic_ide floppy=off irqpoll" fixed the busybox crap for me. Thanks to whoever figured that out.

You would think they would test the Dells that are selling their damn OS before releasing.

---

### Post by hannah187 on 2008-06-05
> **bgreenaway said:**
> Just to add my tuppence worth as I have just (hopefully) solved this:

My hardware setup is a HP Media Center m7160n with a single Maxtor 250 GB SATA drive. Did not have the SATA option in BIOS to change to RAID (as suggested in earlier posts).

This problem was resolved for me by adding the **all_generic_ide floppy=off irqpoll** to the install option. So far, installation of 8.04 running smoothly. Will see what happens upon completion, however.

I have reinstalled Hardy Heron from my Alternate CD 8.04 with **all_generic_ide floppy=off irqpoll** to the install option and it [COLOR="Red"]**did not**[/COLOR] solve my initramfs + busybox error. My laptop is Toshiba Satellite Pro L300 (PSLB1A).

Still searching for a solution.

---

### Post by Dave2k6 on 2008-06-05
When you get to the GRUB menu, press e, then go down one line and press e again.

Now add this to end of boot line, after the -- ,

```
all_generic_ide floppy=off irqpoll
```

If it works, you will need to edit you menu.lst file to include those boot parameters.

At a terminal screen type

```
gksudo gedit /boot/grub/menu.lst
```

Enter your password when askede.

Then look for a line similar to below

```
title		Ubuntu 8.04, kernel 2.6.24-17-generic
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.24-17-generic root=UUID=e61ff7b5-df4b-46c5-b95f-39de2857387a ro quiet splash
initrd		/boot/initrd.img-2.6.24-17-generic
quiet
```

and add a space after the word splash then type 

```
all_generic_ide floppy=off irqpoll
``` (do NOT change the root=UUID bit as yours will be different from above (as it's the drive's id))

then save the file.

---

### Post by hannah187 on 2008-06-05
> **Dave2k6 said:**
> When you get to the GRUB menu, press e, then go down one line and press e again.

Now add this to end of boot line, after the -- ,

```
all_generic_ide floppy=off irqpoll
```

.

I am just looking at my Grub Menu..I do not have --

this is what is have:

kernel /boot/vmlinuz-2.6.24-16-generic root=UUID=XXXX ro quiet splash

have added all_generic_ide floppy=off irqpoll at the end of splash and then enter and "b" to boot...
the Ubuntu Splash Screen appears and then after a while drops to  busybox + intramfs shell..

still no solution for me..

IS there anyone installed HARDY on this Toshiba Satellite Pro L300 (PSLB1A)

---

### Post by ExemplarUbuntu on 2008-06-05
With a floppy in the drive and muttering the incantaion (extra boot parameters) I have managed to get a Dell PowerEdge 2600 to boot the LiveCD to the Ubuntu desktop.

Next step is to try an install to see if it will recover the wreckage of so many failed installs.

Give me FreeMiNT-XaAES any day.

---

### Post by paul cooke on 2008-06-05
I am really really not happy... I waited a few weeks and then tried to update my laptop from gutsy to the new 8.04LTS...

No dice...

this as far as I'm concerned is a showstopper... a biggy and should never have made it out of the gate...

I have tried some of these boot options no dice... all I get is the logo bar moving back and forth for what seems like ages and then get dumped into the busybox shell...

ALT -F1 gives me the normal terminal screen for the boot process and I see the following in the error message:

```
starting up ...
Loading, please wait...
         Check root= bootarg proc/cmdline
         or missing modules, devices:cat /proc/modules ls /dev
ALERT!/dev/disk/by-uuid/ff7922cab-081d-464d-8ee9-9b6341edc685 does not exist. Dr
opping to a shell!
```

what maroon introduced these uuids for booting???????

basically I have a completely borked laptop... and no obvious way to fix it...

good job it wasn't my primary machine... then I'd really be unhappy...

---

### Post by Mithrandir13 on 2008-06-06
Hi folks,

I've got XP and Vista both running together like a charm. But i need to install Kubuntu now as a third os. Tried it with wubi, but got the same problem after rebboting and selecting kubuntu to boot. Now i want to install it from the boot-cd, but as i read about these problems here, i am afraid, that afterwards, my two windows systems wont work anymore.

Is there a final solution?

---

### Post by kroutal on 2008-06-07
Hello
I had the same problem with the Toshiba L300 12k.
I've finally managed to boot with the new kernel that's in the updates.

---

### Post by pascalc on 2008-06-08
>IS there anyone installed HARDY on this Toshiba Satellite Pro L300 (PSLB1A)

Yes, the trick for me was to deactivate the LAN support in the BIOS (F2), this way I no longer have the error on the install CD boot and I could install Hardy. The problem is that I have to leave the LAN deactivated for Ubuntu to accept to boot and the Wifi is not recognized so I can't connect to the internet to get updates.

I read on a forum that some recent updates to the kernel would have fixed it but since I can't connect to the repositories, I can't apply them :(

---

### Post by hannah187 on 2008-06-08
> **pascalc said:**
> >IS there anyone installed HARDY on this Toshiba Satellite Pro L300 (PSLB1A)

Yes, the trick for me was to deactivate the LAN support in the BIOS (F2), this way I no longer have the error on the install CD boot and I could install Hardy. The problem is that I have to leave the LAN deactivated for Ubuntu to accept to boot and the Wifi is not recognized so I can't connect to the internet to get updates.

I read on a forum that some recent updates to the kernel would have fixed it but since I can't connect to the repositories, I can't apply them :(

This is exactly my machine.. ok I will try this way. By the way: which CD have you tried to install. Live or Alternate..

As with ALTERNATE CD (8.04) I can install however after booting I get the error. 

What is your experience in regards to get on the internet after installing 8.04. Were you able to?

Cheers

---

### Post by hannah187 on 2008-06-09
ok I have changed the bios to disable the LAN and with live CD 8.04 (and not Alternate CD) istalls with out a hitch. Now one can log into Hardy however no internet.

Then I have enabled LAN support in BIOS, and boot my laptop, intramfs+busy box returns. Note that 7.10 works without a problem.

---

### Post by kroutal on 2008-06-11
You have to install this linux image :[here]("http://security.ubuntu.com/ubuntu/pool/main/l/linux/linux-image-2.6.24-19-generic_2.6.24-19.33_i386.deb") and the message should disapear.

---

### Post by Skerit on 2008-06-14
Is there any progress on getting the WiFi to work on this machine? (Well, on a L350-107 more specifically!)

The kernel updates made the LAN problem go away, but I still don't know how to repair the wifi

---

### Post by Spudgun79 on 2008-06-17
Right, after a lot of messing about I've managed to get a Hardy Heron/Vista dual-boot (its a necessity) working.

I too started off with a Busy Box error, mainly preceded by the fd0 error, even though it worked fine with Gutsy. :confused:

My setup consists of a MSI K9A Platinum V1.0 motherboard with 2 Western Digital 320GB SATA II HDs.  After reading this thread and seeing all the MSI issues I wasn't holding out much hope.  For my mobo at least there are four SATA settings in the BIOS: Native IDE, AHCI, Legacy IDE & RAID. I finally managed to get Hardy to install and be able to use it by changing this setting to 'Legacy IDE' from 'Native IDE'. RAID was a no-go as then Vista would not work.

The problem with 'Legacy IDE' is it made Vista hideously slow so I really wanted to use 'Native IDE'.  After trying everything I had found (all_generic_ide, irqpoll, noirqpoll etc..) for the boot options **I tried "pci=nomsi" and everything now works like a charm!**

Whether that would have worked straight from the live CD and allowed you to install without messing about with the BIOS I don't know, but I suspect it may well do.

I hope my experience will have the chance to help others.  Its very frustrating and stuff like this really needs to be sorted out if Linux is going to go mainstream in the Desktop market.  I persevered because I like using Ubuntu.

Can anyone tell me what "pci=nomsi" actually does?  I did a quick google, but didn't really come up with much.

---

### Post by mmbspa on 2008-06-17
I have the same problem. 100 gig hard ide drive, 64 amd processor and a cd/dvd drive and thats it. I just jet the initramfs and busy box and when typing help get nowhere.
why cannot the distro writers fix this. 
Help????

---

### Post by mnec20 on 2008-06-18
I tried to install Ubuntu 8.04 LTS around a month ago and had the same problem as everybody else here. I ended up giving up on Ubuntu since nothing described in this topic helped at all, including the commands on start up and bios tweaking.
I tried agian a few minutes ago using the pci=nomsi argument and strangely enough it worked!! Ubuntu is being installed on my desktop as I write this on my laptop. Problem is: this "busybox" stuff is NOT SOLVED. I'm afraid it may happen again sometime soon since I've done nothing different than what I tried the other time. I'm obviously new to Linux so I'd like to ask special attention from the power users and developers about this matter so future releases won't be so troublesome.

---

### Post by paul cooke on 2008-06-18
I'm extremely unhappy with this problem. :mad:

1) I have a borked laptop which won't boot after upgrade from gutsy to hardy. It dumps me in the busybox with the ridiculously long can't find UUID error... ](*,)

2) I have my primary machine still back on Dapper and Firefox 3 doesn't run on it... and there don't appears to be support for it now either... :(

I'm stuck with a dead laptop and I'm too scared to attempt the upgrade from Dapper to Hardy on my other boxes. I've had my fingers burnt too often before on rpm based systems with apparently easy upgrades that fell over completely.

This dumping people into busybox is, as far as I'm concerned, a serious showstopper and will really give a sour taste for both newcomers and experienced hands. :sad:

My laptop isn't anything special... just an old Sony VAIO with a good old fashioned IDE drive, none of this fancy SATA stuff...

---

### Post by herdivet on 2008-06-18
Okay, here's a fix I used that worked for me.  I was going to link to it, but I cannot find it on the forums now.  it was originally posted by PriceChild.

REPAiRING YOUR BROKEN HARDY INSTALL

If you can, it is preferable to just boot using a backup kernel or into recovery mode and update from there.  If you can't:

*Boot up a live cd, or separate Linux install
*Mount your Hardy drive somewhere (replace **** with name of drive, e.g. hda1 or sda2 etc)

code:
[I]sudo mkdir /media/hardy
sudo mount /dev/**** /media/hardy
[/I]
* chroot into your hardy drive

code:
[I]sudo chroot /media/hardy
su[/I]

*Update your system via apt as normal (sudo not required)

code:
[I]apt-get update
apt-get upgrade
apt-get dist-upgrade[/I]

*Ctrl+d or type "exit" to exit the chroot, then reboot the computer and you should be able to get back in to Hardy.


That's what was in the post.  I have multiple Hardy's, one I have to use the all_generic_ide irqpoll at all times, the other will fall in to busybox on occasion and until I do this process it won't come out.  

Hope this helps.  Hate to see anyone giving up because of this.

---

### Post by mmbspa on 2008-06-18
Some of us newbees have not done command line work in a while so be a litter nicer. Grow up.

---

### Post by cobraspyguy on 2008-06-18
So does previous versions work? I was hoping to get away from Vista and not go back to XP but this seems like deja vu. Have to use an older version of buntu to get it to work. I guess microsoft isnt so bad after all.

---

### Post by paul cooke on 2008-06-19
> **herdivet said:**
> Okay, here's a fix I used that worked for me.  I was going to link to it, but I cannot find it on the forums now.  it was originally posted by PriceChild.

REPAiRING YOUR BROKEN HARDY INSTALL

If you can, it is preferable to just boot using a backup kernel or into recovery mode and update from there.  [...]

Hope this helps.  Hate to see anyone giving up because of this.

thanks, I managed to get in via an old kernel that was in the grub menu...

busy installing some 305 mb of updates right now... will get back with yey or ney when it's all finished.

---

### Post by paul cooke on 2008-06-19
> **paul cooke said:**
> thanks, I managed to get in via an old kernel that was in the grub menu...

busy installing some 305 mb of updates right now... will get back with yey or ney when it's all finished.


it's a yey...

laptop rebooted fine

---

### Post by joele on 2008-06-20
Tried all the suggestions in this thread, wasted most of the night.. got nowhere.. Back to Vista (it installs fine).. 

If I wanted to screw around this much I would use Gentoo again...

---

### Post by Ubangi on 2008-06-22
Like many other people, I eventually managed to install with:
all_generic_ide floppy=off

However, I find now that some benchmarks run at only half their expected speed on my amd64.

I wonder if anyone else noticed this problem and if it might be connected with the screwed up installation?

---

### Post by hadley on 2008-06-22
Hi everyone,

I finally succeeded in installing 8.04 after experiencing the same initramfs+busybox issue. Jong's ([http://ohioloco.ubuntuforums.org/showpost.php?p=4809508&postcount=61](http://ohioloco.ubuntuforums.org/showpost.php?p=4809508&postcount=61)) solution worked in my case (using the live CD). Many thanks! 

If it helps, or anyone's interested I'm running an Asus A8N-E, with one SATA and ATA drive (master and slave respectively). 

As a bit of an aside, from 6.06 to 7.10 I've had no problems what so ever on any of my machines. A bit annoying, but great 8.04 is running!

---

### Post by hannah187 on 2008-06-23
I have a Toshiba Satellite Pro L300 (PSLB1A) on which normal 8.04installation will stall at initramfs + busybox.

One needs to disable LAN in BIOS and then install 8.04 from Live CD (Not Alternate CD).

Then have this kernel update (suggested by Kroutal) offline ready in your Flash Drive or in any other form. Apply this update and when you then restart the comp, under Ubuntu 8.04 grub menu, one should see another option for 2.6.24-19 Kernel. 

Now enable LAN in BIOS.

Restart the computer with 2.6.24-19 Kernel option. You should be able to access Internet.

However my sound card now stopped working. Should be a small problem to fix.


Mega thanks to Kroutal for his advice.

> **kroutal said:**
> You have to install this linux image :[here]("http://security.ubuntu.com/ubuntu/pool/main/l/linux/linux-image-2.6.24-19-generic_2.6.24-19.33_i386.deb") and the message should disapear.

---

### Post by Gafard on 2008-06-24
OMG, I tried this and that and it still doesn't work for me. I tried all the mentioned options in menu.lst and it didn't work.

I have no live cd. Could anyone tell me PLEASE what I could do to get rid of this annoying bug? I'm quite new to Linux and I'm obviously overstrained...

What kind of data do you need to help me?

---

### Post by hannah187 on 2008-06-24
> **Gafard said:**
> OMG, I tried this and that and it still doesn't work for me. I tried all the mentioned options in menu.lst and it didn't work.

I have no live cd. Could anyone tell me PLEASE what I could do to get rid of this annoying bug? I'm quite new to Linux and I'm obviously overstrained...

What kind of data do you need to help me?


Tell us make and model of your computer and which Cd you use to install. Alternate CD does not work at least in my machine. I had to use the Live CD to install Hardy.

---

### Post by I'd_rather_be_____'ing. on 2008-06-26
Read through almost all of this thread and finally came to a solution for me, although I haven't actually installed yet.

I tried all the bootloader commands and all combinations - no good.

In the BIOS I:  disabled legacy USB support, changed the SATA mode from 'AHCI' to 'compatibility' (only options), and finally, disabled internal LAN.  That's what did it.  I went back and undid everything else, leaving only the LAN disabled, and the LiveCD still loads and appears willing to install.  It's too late/early for me to try now...

The hardware is a Toshiba Equium L-300 laptop, and the culprit LAN is a Realtek RTL8102E.  At least it's the one that disappears from Vista's device manager when it's disabled.

Now I have but two questions:
Should I leave the SATA mode as 'AHCI'?  Is this generally a better choice?
Will my LAN work in the future?  The link posted by *hannah187* is 404.

Thanks to everyone who slugged this out before my arrival here a few days ago!  I'll sign in under Ubuntu next time.

A.

---

### Post by tofuconfetti on 2008-06-26
For me it's always been the legacy USB setting.  Get things installed, then change the other settings back AFTER you install and I'll bet you'll be fine.

---

### Post by confused57 on 2008-06-26
Found this on the Phoronix website which may help some with LAN problems:
> Onto the Linux and Solaris compatibility for the Gigabyte 965P-DS3. This board's predecessor had a few issues with the JMicron controller that was integrated to the board, but luckily we did not have any major issues with the P35! However, we did have one issue with the Realtek RTL8111/8168B Gigabit Ethernet controller. Ubuntu was unable to turn on the controller after Windows set it to disabled state instead of Wake on LAN state (don't worry; we just used Windows for the BIOS flashing). The fix is to unplug your computer, press the power button to drain the power, and then boot it back. Then enable Wake on LAN in the Windows Device Manager and it should boot fine. Enabling LAN boot ROM in the BIOS might also help for some people. Those of you who will be planning to use this board (or any board with this controller) on a dual boot Windows machine will most likely have this issue; but those who simply plan to run Linux will not have an issue.

---

### Post by dennisn on 2008-06-29
I'm a little short on details, but basically, I'm pretty this is caused by the installation kernel not having the sata module required to use the hard drive (in my Acer 3680 cheap laptop). After much frustration, I ended up downloading the newer "intrepid" (8.10) iso image, and installing it via the hd-media installation images (as opposed to cdrom or netboot, hd-media's initrd automatically searches for iso images on your USB stick, etc, to install from). Intrepid's kernel/initrd is able to find my sata drive. (There is nice information on USB installation here: [https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick) )

So yeah -- the default 8.04 is a horrible release -- I'm pretty sure previous releases of ubuntu didn't have this problem (7.10, etc).

In particular, the Acer 3680 is poorly supported. Aside from not even being able to install AT ALL using 8.04 (dropped to busybox), sound doesn't work out of the box (a small configuration change has to be made), nor does wifi. ( [http://ubuntuforums.org/showthread.php?t=429182](http://ubuntuforums.org/showthread.php?t=429182) ). Maybe these things could be fixed in upcoming releases? (I'm not exactly sure if/how ubuntu deals with quirky hardware, but this seems to me what the distro is primarily meant to do. The "beauty" of ubuntu was NOT to force the user to tinker with "ugly" internals. In fairness, my first install of ubuntu on a friend's (older) computer was absolutely effortless and flawless, so I know this great potential is there.)

---

### Post by Gafard on 2008-06-30
> **hannah187 said:**
> Tell us make and model of your computer and which Cd you use to install. Alternate CD does not work at least in my machine. I had to use the Live CD to install Hardy.

I do not use a live CD, I use a synaptec for upgrade. 

My system:
-Computer-
Processor		: 2x AMD Processor model unknown
Memory		: 2063MB (776MB used)
Operating System		: Ubuntu 8.04
Date/Time		: Mo 30 Jun 2008 12:44:25 CEST
-Display-
Resolution		: 1680x1050 pixels
OpenGL Renderer		: Unknown
X11 Vendor		: The X.Org Foundation
-Multimedia-
Audio Adapter		: HDA-Intel - HDA ATI SB
-Input Devices-
 Macintosh mouse button emulation
 AT Translated Set 2 keyboard
 Logitech Logitech Dual Action
 PC Speaker
 PS/2 Logitech Mouse
 Power Button (FF)
 Power Button (CM)
-Printers (CUPS)-
PDF
-IDE Disks-
TSSTcorpCD/DVDW SH-S182M
-SCSI Disks-
ATA MAXTOR STM325031

What can I do to get a new kernel to work?

---

### Post by kewlito on 2008-06-30
Thanks Jong

---

### Post by Neo0351 on 2008-06-30
so today i finally put my theory to the test that this was indeed caused buy a missing module.  following this thread, [http://ubuntuforums.org/showthread.php?t=311158&highlight=ahci](http://ubuntuforums.org/showthread.php?t=311158&highlight=ahci)
i spent all day trying different things.  finally i found this
[http://www.ussg.iu.edu/hypermail/linux/kernel/0707.3/3840.html](http://www.ussg.iu.edu/hypermail/linux/kernel/0707.3/3840.html)
it said to disable the CONFIG_PCI_MSI module and sure enough now my computer boots properly without having to enter boot parameters.  im using an abit an52 motherboard (nvidia 520 chipset).  here's my ispic output for anyone interested
```
neo@neo-desktop:~$ lspci
00:00.0 RAM memory: nVidia Corporation MCP65 Memory Controller (rev a1)
00:01.0 ISA bridge: nVidia Corporation MCP65 LPC Bridge (rev a2)
00:01.1 SMBus: nVidia Corporation MCP65 SMBus (rev a1)
00:01.2 RAM memory: nVidia Corporation MCP65 Memory Controller (rev a1)
00:02.0 USB Controller: nVidia Corporation MCP65 USB Controller (rev a1)
00:02.1 USB Controller: nVidia Corporation MCP65 USB Controller (rev a1)
00:07.0 Audio device: nVidia Corporation MCP65 High Definition Audio (rev a1)
00:08.0 PCI bridge: nVidia Corporation MCP65 PCI bridge (rev a1)
00:09.0 IDE interface: nVidia Corporation MCP65 IDE (rev a1)
00:0a.0 IDE interface: nVidia Corporation MCP65 SATA Controller (rev a1)
00:0b.0 PCI bridge: nVidia Corporation Unknown device 045b (rev a1)
00:0c.0 PCI bridge: nVidia Corporation MCP65 PCI Express bridge (rev a1)
00:0d.0 PCI bridge: nVidia Corporation MCP65 PCI Express bridge (rev a1)
00:0e.0 PCI bridge: nVidia Corporation MCP65 PCI Express bridge (rev a1)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
02:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8056 PCI-E Gigabit Ethernet Controller (rev 13)
04:00.0 VGA compatible controller: nVidia Corporation Geforce 9600 GT 512mb (rev a1)

```

---

### Post by hannah187 on 2008-06-30
> **I'd_rather_be_____'ing. said:**
> 

In the BIOS I:  disabled legacy USB support, changed the SATA mode from 'AHCI' to 'compatibility' (only options), and finally, disabled internal LAN.  That's what did it.  I went back and undid everything else, leaving only the LAN disabled, and the LiveCD still loads and appears willing to install.  It's too late/early for me to try now...

Now I have but two questions:
Should I leave the SATA mode as 'AHCI'?  Is this generally a better choice?
Will my LAN work in the future?  The link posted by *hannah187* is 404.

A.


Right..I also run XP in my laptop hence I need to leave it on Compatibility mode otherwise my XP won't boot. If AHCI works for Vista, then try it and see what happens. 

You will find that if  you enable the LAN in BIOS, Ubuntu will not boot and drops to busybox. Hence you need to upgrade the kernel as suggested in the previous post. Since you cannot connect to internet, you need to download the latest kernel offline and then load it offline as well. After that you can enable LAN in BIOS and it should work.

You may find that the sound driver will not work. The solution is to load the latest kernel again through Synaptic (now that you can go online).

Cheers

---

### Post by hannah187 on 2008-07-01
> **Gafard said:**
> I do not use a live CD, I use a synaptec for upgrade. 


Can you please tell us the kernel version?

---

### Post by Gafard on 2008-07-02
> **hannah187 said:**
> Can you please tell us the kernel version?

Currently the last one that works is 2.6.22.14. Everything with 2.6.24 doesn't work. 

Did you mean this?

---

### Post by hannah187 on 2008-07-02
> **Gafard said:**
> Currently the last one that works is 2.6.22.14. Everything with 2.6.24 doesn't work. 

Did you mean this?

ok I understand.

Try one of these:  You need copy this in your flashdrive and load in your laptop off-line. 

[http://security.ubuntu.com/ubuntu/pool/main/l/linux/linux-image-2.6.24-19-generic_2.6.24-19.34_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/l/linux/linux-image-2.6.24-19-generic_2.6.24-19.34_i386.deb)


or even later:

[http://security.ubuntu.com/ubuntu/pool/main/l/linux/linux-image-2.6.26-2-generic_2.6.26-2.6_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/l/linux/linux-image-2.6.26-2-generic_2.6.26-2.6_i386.deb)

I am assuming that you have got an Intel 32bit machine.

---

### Post by kvmapr on 2008-07-08
"i turned the "sata mode" in bios from "ahci" to "raid" and then it works"

Same problem here, and the same solution worked for me as well. In my bios (Dell 530n) the SATA line item has two modes, IDE and RAID. It was defaulting to IDE. After setting it to RAID and saving my settings, it booted wonderfully.

Now I just have to get my wireless working with the new 2.6.18 kernel.

kvmapr

---

### Post by onelife151 on 2008-07-10
I do seriously apologize if this has already been answered. I am going to try the achi to raid bios option when i reboot. I just wanted to see if you guys could help me out with this. I have a compaq sr1630nx. good will tell you my system specs. the only addons i have added is more memory and an extra harddrive. I downloaded the ubuntu 8.04.1 iso via torrent and then verified the iso image via the md5sums. when i boot using the pci=nomsi option or any options it freezes trying to load my external which i inturn had to unplugg and then freeze a bit on my card reader finally stalls at the initramfs prompt but through out the loading process i get this error over and over again. 

hdc: status error: error 0x00 {}
ide: failed opcode was: unknown
hdc: drive not ready for command
hdc: status error: status=0x59 { DriveReady SeekComplete DataReset error }

if you need me to post for information about my specs or what i am doing please let me know. I really want to get ubuntu on this computer.

---

### Post by Gafard on 2008-07-14
> **hannah187 said:**
> ok I understand.

Try one of these:  You need copy this in your flashdrive and load in your laptop off-line. 

[http://security.ubuntu.com/ubuntu/pool/main/l/linux/linux-image-2.6.24-19-generic_2.6.24-19.34_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/l/linux/linux-image-2.6.24-19-generic_2.6.24-19.34_i386.deb)


or even later:

[http://security.ubuntu.com/ubuntu/pool/main/l/linux/linux-image-2.6.26-2-generic_2.6.26-2.6_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/l/linux/linux-image-2.6.26-2-generic_2.6.26-2.6_i386.deb)

I am assuming that you have got an Intel 32bit machine.

I have 64bit, but I already installed these versions. And they all do not work.  :confused:

Isn't there any single option or file that is responsible for this mess?

---

### Post by Tom55 on 2008-07-14
I have discovered a solution that worked for me.  My setup is 

ASUS MN2 MX SE-Plus motherboard
AMD Sempron LE-1200
2GB RAM
500GB SATA HDD
Pioneer DVD D/L burner
AMIBIOS V 0503 build date 26 Mar 08

When I attempted to use the Ubuntu Hardy Heron live CD I received the Busybox message.
After googling for ideas I selected the F6 option at the boot screen and added the parameters noapci nolapic acpi=off pci=noapci
I was able to avoid the Busybox screen but the system then froze at the Initramfs screen.
Thinking that there was a problem with the live CD I burned 3 more HH live CD’s from different sources but had the same problem with each disk.
I then burned a Gutsy Gibbon live CD but still couldn’t get the disk to work.
Next I went into the MB bios to the power option and disabled the ACPI Version Features and the ACPI APCI support option.  

This resulted in the Gutsy Gibbon live CD successfully booting.  However the HH CD (all of them) would not boot.
I then noticed when HH was attempting to load the monitor was showing some lines of text with SR0 and CDROM block error messages.  I’m a newbie with Linux and have the Thomas Edison approach to problem solving (just keep trying anything until you find a solution).  So I disconnected the Pioneer DVD player and replaced it with a Liteon CD player.

The HH live CD (all 3 of them) then worked.

So was the problem the Pioneer DVD drive.  I then removed the CD driver and replaced it with an LG DVD player.  The HH live CD would boot from the LG DVD drive.

In summary 
To get Hardy Heron to boot from the live CD I’ve deactivated ACPI support in the bios and replaced the Pioneer DVD burner.

The Pioneer model is DVD-RW  DVR-106D

---

### Post by raydude on 2008-07-20
For 8.04.1 Boot CD (either 32 or 64 bit) I had to use all_generic_ide at the boot menu, and then (and this is the important bit) it took a full minute to start booting after the kernel good message came up.

Why the delay? I do not know. I'm just glad I came back to the forum to read some more before I rebooted. It started up while I was reading more posts.

Raydude

---

### Post by raydude on 2008-07-20
Well, I can't log in to edit the post but I can log in to post so: its an Acer ASPIRE 5050 that I had this problem with, its not even SATA and its a laptop without a floppy.

Raydude

---

### Post by n7cee on 2008-07-20
I had the same problem after upgrading Kubuntu 8.04 to 8.04-1. The old kernel, 2.6.24-16-generic, would boot OK, but not the new 2.6.24-16-generic. In checking that the UUID in the /boot/grub/menu.lst kernel line was correct for the new kernel, I discovered that a newline had been inserted in the middle of the UUID. Deleting the newline so the UUID was all on one line fixed thr problem.

---

### Post by irlandes on 2008-07-22
> **paul cooke said:**
> I am really really not happy... I waited a few weeks and then tried to update my laptop from gutsy to the new 8.04LTS...

No dice...

this as far as I'm concerned is a showstopper... a biggy and should never have made it out of the gate...

I have tried some of these boot options no dice... all I get is the logo bar moving back and forth for what seems like ages and then get dumped into the busybox shell...

ALT -F1 gives me the normal terminal screen for the boot process and I see the following in the error message:

```
starting up ...
Loading, please wait...
         Check root= bootarg proc/cmdline
         or missing modules, devices:cat /proc/modules ls /dev
ALERT!/dev/disk/by-uuid/ff7922cab-081d-464d-8ee9-9b6341edc685 does not exist. Dr
opping to a shell!
```

what maroon introduced these uuids for booting???????

basically I have a completely borked laptop... and no obvious way to fix it...

good job it wasn't my primary machine... then I'd really be unhappy...

Don't know if you got this fixed or not, much time has passed.

However, the whole thing, 

/dev/disk/by-uuid/ff7922cab-081d-464d-8ee9-9b6341edc685

Should not be appearing in a boot error message.

The UUID that goes into grub menu.lst should only say:

ff7922cab-081d-464d-8ee9-9b6341edc685

For example:

root=UUID=ff7922cab-081d-464d-8ee9-9b6341edc685

I have no idea why you put the whole /dev/disk/by-uuid/ path in front. But, I can tell you that is why it didn't work based on your error message.

---

### Post by paul cooke on 2008-07-24
my laptop booting issue is fixed. I used an earlier kernel in the boot list and gained acces and was then able to finish the upgrade properly...

---

### Post by epidemiks on 2008-08-13
Oh wow.. After sitting on my hands since May, I figured I'd give this another go.. And IT WORKS!!

My troubles seem to stem from the Hard Disk I had Gutsy on..

Samsung SV1022D Rev A 2000.02

With that out of the system, and all_generic_ide floppy=off irqpoll in the boot options, the damn thing just worked!


If you will excuse me, I got some bandwidth to burn..:guitar:

---

### Post by melodis on 2008-08-16
I've been working for months now trying to get Linux installed on my main machine. The only way I've been successful is to install an old ATA133 hard drive. Ubuntu, and more than likely, the GRUB manager seems to have a serious flaw, or compatibility issue with SATA connections.

I have both the SB600 SATA Controller and a JMicron JMB363 controller and the 8.04 live disc can't find any of my hard drives including a RAID 0 on the JMB363 or two seperate hard drives on the SB600 controller running in IDE Mode. 

Strangely enough, I found this on the Wikipedia entry for JMicron:

> JMicron SATA/IDE controllers are often incompatible with some boot loaders. In particular, those using GRUB, such as Ubuntu, cannot boot in some conditions[5]. The most recent Linux kernel and the most recent JMicron controller BIOS [6] solve these incompatibilities but may not be present in existing products, requiring a flash of the motherboard BIOS if the newer version contains the JMicron BIOS update. Other bootloaders such as EXTLINUX and the Windows boot loader work fine. 

I've tried almost every recommendation in this thread, including:

all_generic_ide
irqpoll
nolapic
noapic
deleted quiet splash
floppy=off

Nothing seems to work or improve the situation. Granted, some of these commands change the errors I receive, or the point at which my machine locks up on boot, but in general, I still can't install 8.04. 

My motherboard is nearly 3 years old (ECS KA3 MVP) so I would think at this point the Linux community would have addressed an issue with GRUB that has these types of issues with SATA controllers.

Does anyone know what kind of attention this issue is getting?

---

### Post by paul cooke on 2008-08-17
> **melodis said:**
> 
My motherboard is nearly 3 years old (ECS KA3 MVP) so I would think at this point the Linux community would have addressed an issue with GRUB that has these types of issues with SATA controllers.

Does anyone know what kind of attention this issue is getting?

Well, the subset of ECS mobo users of that particular motherboard who actually use Linux is probably very small, so you are quite likely in a very small number of Linux users who are having problem... The issue here is that the problem is really yours to manage, not that of the community. You can't expect somebody else who isn't having a problem to know about the problem until they are actually made aware of the problem...

so has it actually been reported to the GRUB developers? If not, you'll have to do it yourself. If it already exists as a GRUB bug, then add extra details to the bug report.

Be prepared to help testing any patch as they are extremely unlikely to have the hardware you have.

---

### Post by euthymos on 2008-08-18
Got the same problem on my system (mobo: ASUS P5K-E with JMicron controller, video card: nvidia 8800gt).
Tried all the workarounds but none worked.

I'm reverting back to windows: I've not so much time to waste.

---

### Post by azurehi on 2008-08-18
The work around all_generic_ide has worked for me with all of the 8.04 "buntus" and must also be used in my case with all other 8.04 based distributions,e.g., linux Mint.  As Intrepid approaches, I wonder whether this or similar issues will exist, whether, once again, workarounds will be necessary.  I had no difficulty with any of the unbuntu distros prior to Hardy.  I do not have the expertise to understand why 8.04 has been so difficult and exasperating to install and and I certainly cannot upgrade ot purchase a new computer.

If ubuntu is ever to become mainstream, i.e., easy to install with everything working, the developers are going to have to pay more attention to the user with older equipment, I would think.  I have never heard on Any official ubuntu acknowledgment that the problem discussed in this topic since Hardy's release exists.  Perhaps, I should not expect to.  I can well understand the frustration of poster euthymos.  I use ubuntu extensively but still use xp if I want to share pictures/cam in yahoo messenger, for example.  When, if ever, can I do that with pidgin in ubuntu.

Sorry if my frustration is showing.

---

### Post by melodis on 2008-08-18
> **paul cooke said:**
> Well, the subset of ECS mobo users of that particular motherboard who actually use Linux is probably very small, so you are quite likely in a very small number of Linux users who are having problem... The issue here is that the problem is really yours to manage, not that of the community. You can't expect somebody else who isn't having a problem to know about the problem until they are actually made aware of the problem...

so has it actually been reported to the GRUB developers? If not, you'll have to do it yourself. If it already exists as a GRUB bug, then add extra details to the bug report.

Be prepared to help testing any patch as they are extremely unlikely to have the hardware you have.

From the number of posts in this thread alone it's a very poor conclusion of yours to assume it's my ECS board. This isn't an ECS issue, but more like a GRUB/Linux issue with SATA controllers in general. Many people in this thread have a different manufactured mainboard with a JMicron controller on it that's having the same problem. 

I don't know if this is a GRUB issue, or a Linux Kernal issue, or something else. I'm not a coder, programmer, debugger, or a driver designer. I'm just a Linux user. 

As another user said later in this thread, if Linux is to become more mainstream, bugs like this have got to be resolved quicker than 2 years. After I've googled this problem, it dates back at least 2 years that I've found.

---

### Post by Enki0611 on 2008-08-19
Like many other people, I have a **JMicron **controller for my SATA drives. For me, the solution was to set the JMicron Controller Mode to **RAID **in the BIOS. **Windows XP still launches **with this setting.

I installed Ubuntu by installing the **network installer **on an USB stick through UNetBootIn (get it at: [http://unetbootin.sourceforge.net/]("http://unetbootin.sourceforge.net/")). I installed it without the RAID mode, but then that worked only once from the 10ish times I tried.

For the statistics, I have an Asus P5W DH Deluxe with a Intel quadcore Q6600. I am installing to a 300gb samsung sata disk. I have an Ami Bios version 2503 from 12/26/07.

If your computer uses JMicron and you can not set this option in your BIOS, perhaps you need to update your BIOS. According to JMicron, JMB bios 1.06.53 and above supports linux & grub as can be read [here]("http://www.jmicron.com/Support_FAQ.html"). I have a different bios, but I think I might update my bios anyway to see if I can get it working without setting the controller mode to RAID

---

### Post by Oortism on 2008-08-19
Ok Guys,
    For the past week I have been unable to get Mythbuntu to install on my new made up system that I put together.  I have read alot of this threads and have had to same problems as a lot of you.  It was always, no matter what I tried,:

Busybox v1.1.3 (Debian 1:1.1.3-5ubuntu12) Built-in Sheull (ash)
Enter 'help' for a list of built-in commands.

(initramfs)

So finally, success!!!

These are my specs:

 Xpci- ATI HD 2600 Pro Super
PCI - Broadlogic 2030 card
PCI - Vision Plus 1020a Digital Satellite TV card
PCI - Firewire / USB card and
USB - Genpix board

Motherboard: Asus A8V-XE

Memory: Rosewill DDR400 512mb model: RW 400/512 (4 x 512 = 2 gigs)

Hard Drive:

80 gig-7200rpm Western Digital #WDC WD800JD-(This drive has got Windows xp and want to erase and install fresh'Mythbuntu' system)

500 gig-7200rpm Western Digital #WDC WD5000KS (New)

Video Card: Palit Radeon HD 2600 Pro Super

DVD/CD: Samsung DVD Writer (BG68-01353A Rev. 02)
Artec DVD Writer (Vom-12E48X)Motherboard: Asus A8V-XE
Memory: 2 gigs
Hard Drive:

This is what I had to do:

Installed Ubuntu 7.10 as it saw everything with no problem.  Next, I rebooted and inserted the, Ubuntu 8.04.1 (AMD 64) and whe it goes to the graphical menu, hit <F6> for "other options" and you'll see the kernel boot line and at the end you'll see a ' -- ' and the cursor will be placed just after the end of the line just after the ' -- ', just add 'all_generic_ide', without the quotes, and press the 'Enter' button on the keyboard. 

It went to install Ubuntu 8.04.1 and after installation, reboot and insert the Mythbuntu 8.04.1 and it will install that.

I know it is a very long rout to get to install Mythbuntu but it worked for me.  I am very happy after going 1 week on a daily basis trying and trying that to install this.

I give credit to whomever posted about the 'all_generic_ide'.  That did for me.

Hope it works for someone else---Oortism

---

### Post by AlanPo on 2008-08-23
thanks to gmilne post #133

I needed only irqpoll option. and no more initramfs!!
just needed time to realize that after editing a line need to press b not ESC:)

I have Intel dual core system , 8.041 hardy, and this unfortunate SATA.

---

### Post by Miroku on 2008-08-23
very discouraged when i learned of this issue, how am i suppose to brag about this LTS when the first thing that pops up to those who i recommend ubuntu to is an error. i guess i am sticking with 7.10 for now. and i was so excited as well.

well its time to start plowing thru these posts to get the livecd to 'just work'. i appreciate all the hard work and yes this was a completely useless post. i just felt a strong need to say something.

---

### Post by manthony121 on 2008-08-24
Adding my experience:

My current seup: Intel D975XBX2 Mobo, (has a Marvell SATA controller), 2 SATA HDDs, 1 SATA DVD-R/W drive.  Dual-booting XP / Ubuntu 7.04 64 bit (though I can't remember the last time I booted XP).  Put in the 8.04 i386 CD to begin upgrade....BusyBox/initramfs comes up.  Added "irqpoll" to the boot options --> boots OK.

I'm not sure what "irqpoll" is telling it to do; it sounds like an oxymoron: irqs are a way of getting the CPU's attention *without* polling.

It's little things like this that make Linux so  lovable.  You expect something to go a certain way.  When it doesn't, you dig around the Internet and the forums, learn a bunch of stuff that you never knew before, try things you didn't even know were there to be tried, and when it works, you feel a wave of relief wash over you.

---

### Post by cmat on 2008-08-24
This seems to be a problem with BusyBox when it cannot find a floppy drive on certain systems. Getting the latest Ubuntu LiveCD ISO solved this problem for many people.

---

### Post by mkoonstra on 2008-08-25
Did not see that this topic was active at the time I posted mine, maybe somebody can help me here.

You can view my topic here: [http://ubuntuforums.org/showthread.php?t=899341](http://ubuntuforums.org/showthread.php?t=899341)

Does somebody have an idea what to do?

---

### Post by ferral-cat on 2008-08-25
I was finally able to install Xubuntu 8.04 (Hardy Heron) on my Dell Vostro 200 tower PC.  These instructions should also work on Kubuntu 8.04 and Ubuntu 8.04

I did NOT go into the BIOS to change the Sata to RAID. The best thing is "restore default settings" in the BIOS.  

Then when you get to the screen to install Xubuntu press F6 key so you can edit the special arguments boot line.  

add the following to the end of the line after the --  

all_generic_ide floppy=off

This worked for me and after the install I did not have to edit menu.lst at all

Good Luck.  And this distro rocks!  

After sucessful install then install the package "ubuntu restricted" and you will have flash, java, mp3 and so on working.

---

### Post by sn0rlaxx on 2008-08-26
Just thought I'd contribute my success story, using the all_generic_ide floppy=off irqpoll command my install worked on a rig with Asus A8N-E mobo, SATA hdd.
Great job ubuntuforums, you guys are my heroes :)

---

### Post by mkoonstra on 2008-08-26
My succes was with "floppy=off pci=nomsi".

---

### Post by Kipposaurus on 2008-08-27
I'm trying to install Ubuntu so I can dual boot it alongside XP.

Getting the Initramfs error, putting me into the console but unable to type at all.

A lot of conflicting information in this thread, I know that my Windows won't boot in RAID mode though, so that fix isn't an option.

How can I do this "pci=nomsi" thing. Where is the option for the setting?

---

### Post by Michel347 on 2008-08-29
I'm a newbie at this since it is my first experience to load a Linux distro (past experience of re-installing Windows 98, Windows 2000 and XP because the kids would mess up the PCs and change some hardware as well). 

I have a 2004 Gateway 500:
Processor: Intel Pentium 4 Processor 2.6GHz with hyper-threading technology and 800MHz FSB 
Memory: 768MB 333MHz DDR SDRAM 
Hard Drive: 120GB 7200 RPM Ultra ATA 100 
Network Adapter: Integrated 10/100 Ethernet adapter 
Controller: Integrated Ultra ATA Controller 
Graphics: Integrated Intel® Extreme Graphics 2 with dynamic video memory 
Audio: Integrated Intel
Chipset: Intel® 865G, Intel® BIOS 
USB Ports: 8 Version 2.0 USB ports (2 in front, 6 in back).
DVD+RW/CD-RW combination drive

Ubuntu 8.04.1 -desktop-i386, with Wubi installation would not install after the first boot, I was getting that busybox (initramfs) each time after seeing it attempting to do something with the DVD+RW/CD-RW combination drive.

I tried everything found in that long post, nothing worked, untill when trying it again and again I decided to play with the open door of the DVD when it was doing something with it, it did the trick !!! So I was able to complete the installation, and my Ubuntu HH is now working perfectly with the exception that I have now to figure out why there is no sound.

---

### Post by RealG187 on 2008-08-31
My friend has a Toshiba Satellite notebook and this happened, so he is staying with Vista...

UPDATE: Looks like the new Ubuntu 8.04 ISO works:

[http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download)

---

### Post by JYoungest1 on 2008-09-01
I am fairly new at this whole linux game, but I think I might know part of the issue with the busybox start. 

I was having the same problem and continued to reset it over and over. The only way I got it working again was to start into Vista, and when I did there were updates to be installed, and I had also shut down windows a little messy the time before. When I let the updates install and shut down correctly it worked.

---

### Post by GaryLog on 2008-09-02
I have been reading alot about this initramfs + busybox trouble installing.
I wanted to thank this forum in helping me resolve this issue.
I wanted to give you my results to solve the installation of Ubuntu:

in reguards to AHCI to Raid, below is how I have to load Vista and Ubuntu in the bios:
IDE = Vista but not Ubuntu
ACHI = Ubuntu but not Vista
Raid = neither no boot to Vista or Ubuntu

This is a real pain in the ***, but it works, if anybody has a betterway to boot this please let me know. 
My system has my two harddrives in the raid on the motherboard and not IDE but the only way it will but is in the IDE mode.

---

### Post by cmat on 2008-09-02
> **RealG187 said:**
> My friend has a Toshiba Satellite notebook and this happened, so he is staying with Vista...

UPDATE: Looks like the new Ubuntu 8.04 ISO works:

[http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download)

Getting the new ISO worked for me. Also has this bug been reported to launchpad? Or are we just running in circles with our arms in the air?

---

### Post by RealG187 on 2008-09-02
I wonder does this happen if you boot the old Kubuntu (or Xubuntu) CD?

---

### Post by molochi on 2008-09-03
I was running into this sort of problem a week ago installing Ubuntu 8.04.1. SATA is running as IDE on a P43 motherboard (GA-EP43-DS3L). I'm downloading intrepid-desktop-amd64 (Alpha4)now for a clean install, but it'll be a few hours before the dl finishes. Lots of newer hardware and chips on this system, should be interesting to see what works. I'll update later.

---

### Post by 50words on 2008-09-04
I tried switching from IDE to RAID on my new Inspiron 530, but now I cannot get into the setup menu. Pressing F12 gets me the boot menu, but pressing F2 doesn't get me anything but the regular boot process.

---

### Post by 50words on 2008-09-04
I just pulled the cord and battery and reset the BIOS. Now, of course, I can't boot into Ubuntu. If I change the SATA from IDE to RAID, I can't access the BIOS. It's a no-win, it seems.

---

### Post by RealG187 on 2008-09-04
> **50words said:**
> I tried switching from IDE to RAID on my new Inspiron 530, but now I cannot get into the setup menu. Pressing F12 gets me the boot menu, but pressing F2 doesn't get me anything but the regular boot process.

My friend and I have similar BIOSES, ours are F12 for boot menu and F2 for setup, and when I press F2 it looks the same, the only difference is when you first turn it on, the splash for mine says acer and his says Toshiba.

I recall that if you get to the boot menu (F12) you can access setup from there, I think it's the last option.

---

### Post by molochi on 2008-09-04
Ubuntu 8.10A4-amd64 up and running, no busybox, no change in bios, so windows works too. Of course 8.10A5 is supposed to drop today, but I didn't know that when I DLed. I just did a regular clean install

Got a blank white screen after login (ATi4850) but I fixed that (get rid of Compiz). Now I just need to get wireless, azailea hd sound, and access to the NTFS partition going.

---

### Post by GaryLog on 2008-09-06
[QUOTE=GaryLog;5711814]I have been reading alot about this initramfs + busybox trouble installing.
I wanted to thank this forum in helping me resolve this issue.
I wanted to give you my results to solve the installation of Ubuntu:

in reguards to AHCI to Raid, below is how I have to load Vista and Ubuntu in the bios:
IDE = Vista but not Ubuntu
ACHI = Ubuntu but not Vista
Raid = neither no boot to Vista or Ubuntu

This is a real pain in the ***, but it works, if anybody has a betterway to boot this please let me know. 
My system has my two harddrives in the raid on the motherboard and not IDE but the only way it will but is in the IDE mode.

[I forgot to say that I used the Wubi download for the installation of Ubuntu.) 
[http://wubi-installer.org/](http://wubi-installer.org/)

---

### Post by grashdur on 2008-09-16
My patience is at an end with this thing! I was using Ubuntu HH with Wubi and it seemed mostly fine. I just wanted to make things a bit more secure by switching to a normal ubuntu partition. I wanted to use LVPM to make the transfer, but needed partitions, and the Partition Manager refused to run on my hdd. I tried all kinds of things, and decided to just do a fresh reinstall. I ran into this initramfs problem and finally concluded unintelligently that it must be caused by the boot menu situation for Wubi, so I uninstalled Wubi. But I still had the same problem. Now it looks like I have no choice but to return to Wubi, and do a whole round of installing and configuring for nothing!! 

Maybe Itchy Ibex will solve this problem???

---

### Post by jm1508 on 2008-09-16
I was having the same problem, i have windows and ubuntu installed side by side. I know this isn't a permanent fix but it got me in. when the screen comes up to select OS i clicked ubuntu then a screen comes up saying press "esc (or something else) to go to menu" or something like that with a timer, i went to it and some options pop up
ubutu 8.07
ubuntu 8.07 recovery mode
something else

and windows

i clicked on the recovery mode and let it load then clicked on start ubuntu normally, and the login window popped up. I wouldn't suggest using this every time but it'll get you in to change the files the other user metioned.

hope this was helpful.

---

### Post by bsprecher on 2008-09-20
I have been trying to completely replace the OS on my old Dell Dimension 4600 with Ubuntu. I also encountered the issue described here and tried everything mentioned (such as adding 'all_generic_ide floppy=off irqpoll' after hitting F6 on the boot menu, changing boot order in the BIOS; trying to turn on RAID - which wasn't even an option; etc.), all to no avail.

In desperation, I was sitting here, staring at the forum on my other computer as the machine went through yet another reboot, and I guess I let the system wait long enough that it automatically selected the English language and continued to boot into the Live mode! From within the Live mode, I ran the installer (on the Hardy Heron desktop), and that seems to be running now (knock on wood).

So, if you can't get the installer to load, try running the Live mode. In case it matters to anyone, here is some info about my machine:

Dell Dimension 4600
2.4GHz Pentium 4
1.5 GB RAM
2 ATA hard disks - 80 GB and 160 GB
2 CD/DVD drives (also ATA)
No Floppy

I suspect all the pain has something to do with the 2 hard drives I have set up, but I have no idea.

Good luck everyone!

---

### Post by earlyjazz on 2008-09-25
For everyone's info, I am having the same problems trying to install mandriva (one) 2008.1 from a live disk on a brand new Dell 530n which is also loaded with winXP.  Don't shoot me, I need Quicken and TaxCut. I'm about to try some of the suggestions from this forum and will report back.  Might help to isolate problem ie. kernel, computer, distro.
BTW, I tried to reinstall Ubuntu from disk Dell sent w/computer and it also had same problem!

---

### Post by odeley on 2008-09-28
I have the same problem. I've installed Ubutu with Wubi, then I rebooted the computer and that initramfs thing appeared. I have Windows XP as my primry os, so I don't want to make any changes on the bios and also I don't want to make a partition. Soo what can I do?:confused:

---

### Post by spoier on 2008-09-30
I had the same problem, turned out to be the Seagate FreeAgent USB hard drive, it was trying to mount it on /dev/hdc or something.  Just disconnected all non-essential USB devices and then it booted fine.  I have IDE drives, a 3ware PCI RAID controller, and disabled the onboard SATA since I wasn't using it.

Skye

---

### Post by warnec on 2008-09-30
I've experienced similar issues to yours guys. I think I might have found a possible  solution. 

(look here: [http://ubuntuforums.org/showthread.php?t=934302](http://ubuntuforums.org/showthread.php?t=934302))


PS My mobo is Foxconn MARS, also with Jmicron SATA controller. I have one SATA HDD and one SATA DVD burner, that's all.

---

### Post by cspizz on 2008-09-30
There are many different issues and errors that have been discussed (and resolved) in this thread.  Mine was (thankfully [-o<) more stereotypical.  What's below isn't anything new--I may have found all my answers in this thread--but it pulls together a few of the most common errors and their common solutions in one spot.  Doubt anyone will even find this post on page 24(?) of this ~6 month-old thread, but I spent hours figuring it out so thought I'd share.  :popcorn:

I couldn't install HH 8.04.1, boot to the live desktop, or get through a disk check.  They all resulted in the same thing: an endless loop of "[**##.####] Buffer I/O error on device fd0, logical block 0.**" (and some other errors I'll get back to).  I quickly found that fd0 was reference to the floppy disk drive (FDD).  The kernel was looking for a FDD for some reason, and I don't have one.  (Why it didn't just move on, I can't say. :confused:)  **This was an easy fix for me (as it appears to have been for many others): I disabled the floppy drive in my BIOS and removed it from the boot order.**

That stopped the 'fd0 error' loop, but now brought me to the **BusyBox and initramfs deadend**.  Again, this was an easy fix for me (as it appears to have been for many others): **I hit F6 at the install menu, removed the last two parameters from the boot line ("silent" and "quiet" I think) and added "irqpoll".**

Once I did that, I was able to boot to the live CD.  After booting live, I could see everything was generally working fine, so I installed to a new partition and set up a dual boot with EasyBCD.  *Here's my cautionary tale*: I logged out before changing the boot line parameters inside the newly installed OS, so HH wouldn't boot after I logged out. #-o I had to reboot into the live CD to edit the boot line.  **SO, before you log out after having gone through all you've gone through, DON'T FORGET TO EDIT THE BOOT LINE TO ADD WHATEVER PARAMETERS GOT YOU IN IN THE FIRST PLACE!!!**  To do that inside the newly installed OS, open up a terminal window and type:

```
gksudo gedit /boot/grub/menu.lst
```

That will open up a document.  Scroll down to the bottom (about 3/4 down) to find the boot command line (I identified the right line by finding the 2 parameters I needed to replace--"silent" and "quiet" I think--and make your changes.

If you're a dunce like me #-oand logged out before making the changes, you'll probably need to add a few more directories to your command:

```
gksudo gedit /*disk*/*folder*/boot/grub/menu.lst
```

These errors have apparently been common since this thread started in April 2008 when HH 8.04 was the latest.  Since then, 8.04.1 was released (the version I installed), but these issues haven't been fixed.  :-k

That's it, I think.  If anyone finds this and has any question, feel free to PM me.  Keep in mind what I just wrote is the sum of my linux knowledge to date.

---

### Post by iamah on 2008-10-11
I'm in awe and shock in front of the revelation I had this morning: my computer world is collapsing. 

I had an old computer, very supported by all distros. Couldn't run new games, though...

Now I have a new computer, but couldn't run Ubuntu cause of busybox, and windows xp new games keeps crashing with Nvidia infinite loop problem.

It's hell! :guitar:

Whats in the future for us? :confused:

I'll try Vista for Nvidia driver support, but since Vista has problems of its own, I'll end up with a triple boot Vista + XP + Ubuntu...

---

### Post by bobwyajnr on 2008-10-14
> **Jong said:**
> OMG, I'm up running with Hardy now :lol:
No IDE to RAID switch, nor enabling the floppy drive (I disabled it again).

Using the desktop live cd, what did the trick for me was adding ```
all_generic_ide floppy=off irqpoll
``` to the boot options when pressing F6. ...

Hope this may help someone - good luck to everyone.


Thanks Jong!! I have been tearing my hair out trying to get Ubuntu to install on my system!! Those switches did the trick!! The question this begs then is why haven't these installer woes been sorted out in the 8.04.1 release!! :confused:

I have a system build around a Tyan K8SE board (Nvidia nForce 4 professional 2200 chipset), dual AMD Opterons, lots of SCSI and SATA controllers (I actually boot from a U320 15K SCSI drive), no floppy drive present (floppy controller disabled)!! But I have been using an IDE DVD rewriter drive to boot Ubuntu from (secondary channel, master)!! However the boot process drops out prematurely to the Busybox command prompt. This happens with Ubuntu and Kubuntu discs versions 8.04 and 8.04.1 (x86 and AMD64 variants).

The Linux kernel is still booting when the Ubuntu CD drops out to the Busybox prompt (without Jong's magic solution). There is a race condition happening where Ubuntu is looking for the install CD before the kernel has even located the IDE DVD drive!! So the Caspter log file shows that Ubuntu has quickly whipped through all the possible drive devices and decided it can't find the install CD - dropping out to the Busybox prompt very early on. However with "priority=low" switch set, the non-graphical installer, I can see that the kernel does not finish detecting hardware till much later on in the boot process!! BTW there are no errors in the dmesg log (so it is simply a timing issue - unlike some other folks experience).

This is a very poor show as the actual OS itself runs very well... If you can get the bugger to install itself!! :lolflag:

Bob

---

### Post by iamah on 2008-10-14
> **Jong said:**
> OMG, I'm up running with Hardy now :lol:
No IDE to RAID switch, nor enabling the floppy drive (I disabled it again).

Using the desktop live cd, what did the trick for me was adding ```
all_generic_ide floppy=off irqpoll
``` to the boot options when pressing F6. I can't tell if you really need all three options. I'm just happy to be up running :D

Hope this may help someone - good luck to everyone.

Thanks, I could run the cd and install, but when running from hd i got busybox again... 

any suggestions are appreciated

---

### Post by cspizz on 2008-10-14
> **iamah said:**
> Thanks, I could run the cd and install, but when running from hd i got busybox again... 

any suggestions are appreciated

> **cspizz said:**
> [...]I was able to boot to the live CD.  After booting live, I could see everything was generally working fine, so I installed to a new partition and set up a dual boot with EasyBCD.  *Here's my cautionary tale*: I logged out before changing the boot line parameters inside the newly installed OS, so HH wouldn't boot after I logged out. #-o I had to reboot into the live CD to edit the boot line.  **SO, before you log out after having gone through all you've gone through, DON'T FORGET TO EDIT THE BOOT LINE TO ADD WHATEVER PARAMETERS GOT YOU IN IN THE FIRST PLACE!!!**  To do that inside the newly installed OS, open up a terminal window and type:

```
gksudo gedit /boot/grub/menu.lst
```

That will open up a document.  Scroll down to the bottom (about 3/4 down) to find the boot command line (I identified the right line by finding the 2 parameters I needed to replace--"silent" and "quiet" I think) and make your changes.

If you're a dunce like me #-oand logged out before making the changes, you'll probably need to add a few more directories to your command:

```
gksudo gedit /*disk*/*folder*/boot/grub/menu.lst
```


iamah - Because booting from the HD doesn't bring up the boot menu, you have no opportunity to change the boot parameters as you did when successfully booting from the live CD.  Your install is stuck trying to boot from the same bad parameters.  You need to boot into the live CD then edit the boot parameters for your install.  Open a terminal window and type:

```
gksudo gedit /**disk**/**folder**/boot/grub/menu.lst
```

**NOTE**: You must replace **disk** and **folder** in the code above according to your configuration.  You need these to find the boot parameters of your HD install.

PM me if you need clarification or more help on this.

---

### Post by craigcrawford114 on 2008-10-17
Hi,

I am experiencing the same problem. I am trying to install Ubuntu 8.04 (I've also tried 8.10) on a RocketRaid 2320 controller in a RAID 5 array.

I've tried all the suggestions in this thread with no luck. It gets up to the Ubuntu loading screen and then throws me back into the "initramfs + busybox" screen.

I know I probably wont get any responses to this message (I haven't in any other thread I've created here), especially due to the fact that not many people would be trying to install on a RAID 5 array.

But are there _ANY_ parameters I can try?

---

### Post by Pxtl on 2008-10-17
Hey, installing on a brand-new Dell box, had the same problem... irqpoll dodged that one problem and it seems to get further, but instead, it freezes up after ath_pci, on 
"ACPI: PCI Interrupt 0000:02:01[A] -> GSI 16 (level, low) IRQ 16"

dunno where to go from there.

---

### Post by iamah on 2008-10-18
i followed cspizz suggestion, but my menu.lst already had the options i used at live-cd boot... nice, but it didn't work when booting from hd, it hangs at some USB HiD stuff... man I'm missing my Ubuntu:confused:

---

### Post by snake_in_a_box on 2008-10-21
I've been having quite a problem with this installation. Tried to install Hardy Heron but I got busybox'd. Tried many of the solutions here but none worked. So, out of desperation, I popped in a Gutsy Gibbon disk. Lo and behold, it works. I then install Gutsy on my comp and upgrade to Hardy. I restart my computer and Busybox rears its ugly head. I need to get Hardy on this computer for school. Specs are below. I'm trying to install on the SATA HD.

AMD Athlon 64 X2 5200+
Nvidia Geforce 8800GT
ASUS M2R32-MVP Mobo
one 320 Gb SATA HD
one 80 Gb IDE hd

---

### Post by Matthew Good on 2008-10-23
> **snake_in_a_box said:**
> I've been having quite a problem with this installation. Tried to install Hardy Heron but I got busybox'd. Tried many of the solutions here but none worked. So, out of desperation, I popped in a Gutsy Gibbon disk. Lo and behold, it works. I then install Gutsy on my comp and upgrade to Hardy. I restart my computer and Busybox rears its ugly head. I need to get Hardy on this computer for school. Specs are below. I'm trying to install on the SATA HD.

AMD Athlon 64 X2 5200+
Nvidia Geforce 8800GT
ASUS M2R32-MVP Mobo
one 320 Gb SATA HD
one 80 Gb IDE hd

Your setup is very similar to mine.  To get hardy to install when your at the options menu press F6 and add pci=nomsi.  That should get you thru or at least it did for me.  To bad it doesn't work on the new Intrepid which I am still trying to figure out how to get that one installed.

---

### Post by iamah on 2008-10-26
will try the 8.10 or other distro someday, for now I'm using windows

---

### Post by matis_keynell on 2008-10-27
i had the same issue with wubi 8.04 & 8.10 live cd
'all_generic_ide irqpoll' fixed it the initramfs issue, but now installation stucks at
'usb hid core driver'
some mentioned adding a line: /sbin/udevsettle --timeout 10
to udev (in /scripts/init-premount) but i don't know how to do that since no command listed with 'help' can edit text files, and i can't do this under another os since it's a wubi installation
how to pass around that, any idea?

---

### Post by bep on 2008-10-27
I updated from 7.04 -> 7.10 -> 8.04, then got the busybox.

Could only boot from a fairly old kernel. Here is what fixed my problem:

First I removed splash/quiet from the boot options in /boot/grub/menu.lst. Then it was clear that Ubuntu for some reason now identifies my IDE disk as a SCSI device or something.

So I changed the menu.lst-item to this (/dev/hdc3 -> /dev/sda3 (my Ubuntu is on the fourth partition)):

```
kernel		/boot/vmlinuz-2.6.24-21-386 root=/dev/sda3 ro 
```

I also edited /boot/grub/device.map:

```

(hd0)	/dev/hdc
(hd0)	/dev/sda

```

(Do not know if the last step is necessary.

And viola!

---

### Post by the_darkside_986 on 2008-11-01
I am still getting BusyBox on 8.10 on a cheap Compaq Presario that has been able to run Windows XP, Windows Vista, and even older versions of Ubuntu without any issues. This happens before AND after replacing the IDE drive with an extra SATA I had. The BIOS doesn't support changing many options and Windows XP SP3 installed on the same machine without any issues, so the BIOS clearly isn't at fault. I should probably just give up and format the whole drive for NTFS anyway if it is a kernel problem until someone makes a distro containing an old stable kernel that Just Works (TM) suitable for desktop usage while running all of the latest free software.

---

### Post by Cha-cha on 2008-11-02
Here is how I fixed my initramfs and busybox problem.
First I noticed from my bios that my hard-drive was being detected as a secondary hard-drive (not primary). Many of the info here suggested that the initramfs issue has to do with the drives (hard, floppy, CD). I opened my computer, checked out the hard-drive and CD connection to the IDE. It turned out, just as the bios indicated, the hard-drive is connected as secondary IDE device. The cable I have has 3 connector--black (top) , grey (middle), blue (end). The label on my hard-drive says the grey connector is for secondary IDE devices. The original setup has the hard-drive connected to the the grey connector, while the CD-ROM is connected to the black connector and the black connector is connected to the IDE slot on the mother board.

I reconnected my devices as follows: black connector was connected to the hard-drive, the grey connector was connected to the CD-ROM and the blue connector was connected to the mother board.

The installation went very smoothly after the reconfiguration.

Note: my box had XP and I was able to boot with it, so initially, I didn't suspect I have a hardware issue.

---

### Post by the_darkside_986 on 2008-11-02
I've already tried two different SATA slots but I'll try the remaining later. But still, if Ubuntu 8.04 and earlier can find the drive, there is no reason the newest shouldn't be able to. They should quit introducing fatal bugs into the OS for no good reason.

---

### Post by bibloks on 2008-11-05
> **Oortism said:**
> Ok Guys,
    For the past week I have been unable to get Mythbuntu to install on my new made up system that I put together.  I have read alot of this threads and have had to same problems as a lot of you.  It was always, no matter what I tried,:

Busybox v1.1.3 (Debian 1:1.1.3-5ubuntu12) Built-in Sheull (ash)
Enter 'help' for a list of built-in commands.

(initramfs)

So finally, success!!!

These are my specs:

 Xpci- ATI HD 2600 Pro Super
PCI - Broadlogic 2030 card
PCI - Vision Plus 1020a Digital Satellite TV card
PCI - Firewire / USB card and
USB - Genpix board

Motherboard: Asus A8V-XE

Memory: Rosewill DDR400 512mb model: RW 400/512 (4 x 512 = 2 gigs)

Hard Drive:

80 gig-7200rpm Western Digital #WDC WD800JD-(This drive has got Windows xp and want to erase and install fresh'Mythbuntu' system)

500 gig-7200rpm Western Digital #WDC WD5000KS (New)

Video Card: Palit Radeon HD 2600 Pro Super

DVD/CD: Samsung DVD Writer (BG68-01353A Rev. 02)
Artec DVD Writer (Vom-12E48X)Motherboard: Asus A8V-XE
Memory: 2 gigs
Hard Drive:

This is what I had to do:

Installed Ubuntu 7.10 as it saw everything with no problem.  Next, I rebooted and inserted the, Ubuntu 8.04.1 (AMD 64) and whe it goes to the graphical menu, hit <F6> for "other options" and you'll see the kernel boot line and at the end you'll see a ' -- ' and the cursor will be placed just after the end of the line just after the ' -- ', just add 'all_generic_ide', without the quotes, and press the 'Enter' button on the keyboard. 

It went to install Ubuntu 8.04.1 and after installation, reboot and insert the Mythbuntu 8.04.1 and it will install that.

I know it is a very long rout to get to install Mythbuntu but it worked for me.  I am very happy after going 1 week on a daily basis trying and trying that to install this.

I give credit to whomever posted about the 'all_generic_ide'.  That did for me.

Hope it works for someone else---Oortism

Please mate how did you manage to instal PCI - Broadlogic 2030 card?  
I am trying to get this card to install and read in the net bunch of articles but I cannot find driver anywhere, the one I found are old and are for redhat!

I have installed mythbuntu 8.10, still did not configured anything in mythtv as I want to have DVB initially installed. 

PCI - Broadlogic 2030 card is visible by the system as netowrk card when i lounch hardware testing but its not dvb.  

Can you guys help me on this, need to know is this old card still can be runned with mythbuntu 8.10

Thanks

---

### Post by Gralgrathor on 2008-11-06
I have a similar problem with installing the 8.10 32-bit livecd.

I have a simple machine, 32 bit architecture mainboard, dual core Intel cpu, 4 sata channels, 2 IDE, to which I added an additional 4 IDE channels using a PCI IDE controller. The machine came with a Samsung 500G SATA drive (ch. 1/4), and I added 2 WD 1T SATA drives (ch. 2 and 4/4), and 2 older WD 500G IDE drives (those last two I plugged into the PCI controller, both as master).

The base install works like a charm. I just enter through the program, sacrifice my entire (hd0) 500G SATA drive to the "guided partitioning" process, remove the CD, hit enter - and -

End of story. The thing won't boot no matter what I do. The machine just stopped dead right after the POST check.

So here's what I did: I re-installed Debian, my previous installation, using the same harddrive, and told the installation program to tweak the MBR and /boot partition (why doesn't the ubuntu install livecd have nifty options like that? sure, the installer is easy to use - unless it doesn't work!). Then I re-installed ubuntu, again using (hd0).

Now, at boot, at least I got the grub menu. But keying enter got me in the BusyBox. The UUID its trying to boot from is wrong. So I rebooted and got myself into a grub commandline, to try some stuff. I couldn't get it to boot no matter what "root (hd#,#); setup (hd#)" or what UUID I entered.

I did discover one thing though:

Debian assigns a completely different range of drive numbers to my drives than ubuntu.

My machine has 3 SATA drives, and 2 IDE drives on a plugged in PCI IDE card. It also has a combination card reader internally on USB. It's starting to look like with ubuntu, the cardreader or USB devices are numbered as the first 4 SCSI devices, while the SATA and IDE drives are given drive designations higher than those. I want to install ubuntu to the same disk Debian was first on: the first sata drive - but apparently my BIOS, Debian and Ubuntu *all* have different ideas as to which drive is which.

Haven't tried switching BIOS to RAID yet - and I don't see why an off-the-shelf install CD should require somebody to radically alter their system hardware config anyway. Besides, I would like to make try and the machine a dual-boot, so I cannot willy nilly change system parameters, or something else will not boot.

I will try to add the "noapic" option to the kernel parameters at my next install attempt. I have tried the "all_generic_ide" option, but that just got me loads of "Input/output-errors."

I'll add another post if my attempts at installing this thing succeed. The machine's been offline for 3 days now. If I don't get the server to run within another day or so, I'll probably revert to Debian permanently, and to hell with the TV-card.

Yo!

G.

Addendum I:

Users have reported slower than normal detection of SATA hard drives on systems with Intel D945 motherboards in Ubuntu 8.10. This may cause the system to drop to a busybox initramfs shell on boot with a "Gave up waiting for root device." error. Wait a minute or two and then exit the initramfs shell by typing 'exit'. Booting should proceed normally. If it doesn't, wait a bit longer and try again. Once the system boots, edit /boot/grub/menu.lst and add rootdelay=90 to the kernel stanza for your current kernel. (Bug 290153: [https://launchpad.net/bugs/290153](https://launchpad.net/bugs/290153)). 

I'll try this as well: might be that the UUID is not wrong, but that my mainboard has an unsupported chipset, even though it is an MSI mainboard. At some installation attempts I got the message "... doesn't exist" and in some just timeouts, so it's worth a shot.

G.

---

### Post by iamah on 2008-11-06
I believe I'm getting this wrong UUID error because my sata disk is at a secondary slot, due to my VGA being too big I can't use Sata primary slot.

---

### Post by quoderat on 2008-11-06
I can't believe this is still a problem. Getting this in 8.10. Also, Intrepid erased the partition tables of two of my drives completely (not the two I was installing on) in two different installs.

This should be pulled until these problems are corrected.

---

### Post by grashdur on 2008-11-09
What's worse is that I didn't have this problem with Hardy Heron, as long as I installed with Wubi. I was hoping to use the installation disk for Intrepid to finally set up a separate partition for Ubuntu, and the installation disk did at least run. But on the first attempt I ruined both Windows and Ubuntu when trying to resize partitions, and on the second attempt I was not allowed to resize partitions. I then tried Wubi again, but I keep having various problems almost every time I try to start Ubuntu.

Now I'm about to try one more time to install. Then I might have to go back and do a new install of Hardy Heron with Wubi!!! So much work for nothing.

Edit: I had absolutely no problem managing partions and installing II on my laptop. It seems that Ubuntu is simply not compatible with my desktop computer hard drive.

---

### Post by NotoriousMOK on 2008-11-11
I have a laptop that my company provided (Sony Vaio VGN-NS135E) which has a SATA drive.  I have unsuccessfully tried different mixes of the following options;

pci=nomsi
all_generic_ide
irqpoll
floppy=off

My BIOS does not allow me to change the SATA mode.

I have been attempting to install 8.04 Desktop i386.

My preference is to use 8.04LTS, with 7.10 being a second choice, and 8.10 being the last choice.  If anybody has had success with a similar Sony notebook, I'd appreciate your solution.  Otherwise, kindly add me to the "PLEASE HELP" list.


Thanks!

---

### Post by daviebasite on 2008-11-12
I have quadcore system based on P5K-E wifi mobo
I had ubuntu 8.04 installed together with windows(dual boot, for learning purposes) the ubuntu was installed on the second hard disk which is connected to J-micron ide controller PATA. Windows is on the first hard drive which is SATA.
After alot of digging I decided to delete this distro and to wait for the new release because there where a problems with remembering the network settings. Then I fixed the windows mbr with the recovery console and windows for itself worked fine. One week after that the new ubuntu was released and then I faced a big problem with trying to install both 8.04 or 8.10. The installations every time finished in BusyBox (I read all the posts about and tried all command line options (irqpoll and all others in any combinations with the bios settings "raid-ahchi-ide)).
I'm wondering how I installed 8.04 the first time? That's weird because the hardware is still the same without any changes (only that mbr fixing stuff is the difference between the first installation and the current tryouts).
Anyway to avoid this now I'm using usb memory stick to install from. And voila - the installation processed as expected :)
But the new installation doesn't show grub at a boot time and windows is starting directly like nothing was made. wtf?

Just want to note that in my opinion the problem I have with the busybox on install is not releated to this controller, because the first installation of ubuntu was passed as a charm and it was working for around a month until I deleted it. Now with the same install cd on the same hardware there is a busybox!?

---

### Post by iamah on 2008-11-12
What worked for me was "all_generic_ide floppy=off irqpoll pci=nomsi" added to grub, plus SATA Raid option enabled at BIOS.

Still, you have to remember, once at Ubuntu, edit /boot/grub/menu.lst and add the same options at the ubuntu boot line. 

If you forgot to do that, press "e" during boot menu to edit the selected option, add the options to be able to boot into Ubuntu again. Then edit the file mentioned before.

---

### Post by NotoriousMOK on 2008-11-12
Follow-up:  Okay, I was able to get installed.  While I've still got display and a couple other small issues to work out, I'm pretty much running.  I used a 1G thumbdrive to install 7.10 (standard i386 desktop), but no wifi, so I plugged in for access and (via update mgr) upgraded to 8.04.  Once in 8.04 still no wireless, so I upgraded again to 8.10 and now I'm running with wifi, but have to still deal with 800x600 resolution (another topic).

While this was likely a long path around, it got me running.  BTW, I did not need to use any F6 options when installing 7.10


Thanks and good luck!




> **NotoriousMOK said:**
> I have a laptop that my company provided (Sony Vaio VGN-NS135E) which has a SATA drive.  I have unsuccessfully tried different mixes of the following options;

pci=nomsi
all_generic_ide
irqpoll
floppy=off

My BIOS does not allow me to change the SATA mode.

I have been attempting to install 8.04 Desktop i386.

My preference is to use 8.04LTS, with 7.10 being a second choice, and 8.10 being the last choice.  If anybody has had success with a similar Sony notebook, I'd appreciate your solution.  Otherwise, kindly add me to the "PLEASE HELP" list.


Thanks!

---

### Post by espressoguy on 2008-11-15
I'm seeing this problem too and just wasted alot of time with it!!

Twenty-six pages of people reporting this problem and still:
1. It is still in the latest release
2. It isn't even mentioned in the release notes

This does not speak well for the people responsible for Ubuntu !!

---

### Post by grashdur on 2008-11-16
I've had the same problem on my Gateway computer (with a SATA drive): The installation disk for Hardy Heron just would not run. I was able to install Itchy Ibex, but then I always had various major problems trying to boot into Ubuntu. (Though Ibex runs quite well on my Sony laptop.)

Ultimately I could only find one solution that would work and that wouldn't require learning to reprogram the whole OS: Just install Hardy Heron again from Windows, with Wubi. Certainly I'd prefer a real Ubuntu partition, but I seem to have no choice. :(  It's working just fine, and Ubuntu updates now have my DVD drive working most of the time. I just have to store some of my files in the Windows filesystem.

---

### Post by daviebasite on 2008-11-16
Hi guys,
A lot weeks of trying and reading, even buying a new pci ide controller didn't solve this "intramfs" console.
Every time I used a DVD-R burned at the lowest speed! Today I went to the shop and get one CD-R and burned it at 8x speed and now the installation goes smoothly into GUI and so on...!

P.S. "I'm using a CD-R for a first time from around 5 years :) "

---

### Post by JohnWP on 2008-11-17
I have just joined the forum and spent a happy (not) hour or so reading a lot of these posts. I was hoping that there would be a simple, definitive answer to the problem. 

I have been trying, of and on, for over three months to install 8.04. I have tried both the 32 bit and the 64 bit versions and keep running into the initramfs / busybox thing. I can make the live CD work by adding "generic.all_generic_ide=1" to the boot parameters - the boot process reports this as "unknown boot option - ignoring" but the live CD 32 bit and 64 bit both work. Install goes ahead apparently OK but when I try and actually switch the PC on and boot into Hardy all I see is the "bouncing bar" which goes on for ages - possibly forever.

I tried re-installing 7.10 and then upgrading to 8.04 via the package manager. Re-boot is even worse because after some minutes of the bouncing bar I see the intramfs / busybox thing again.

The only sure solution as someone else sadi is "don't use 8.04"

Does nobody from Canonical actually realise there is a problem here.

Being the number one distribution in the world only works when you make sure the software still works.

I am going to install Mandriva. 

But many thanks to all you fine people who have been trying to do Canonical's job for them.

---

### Post by one_time_poster on 2008-11-20
I went through the trouble of registering/activating on this forum so that I can voice my opinion right now.  Keep in mind this is my first (and probably only) post.

I've heard the buzz about ubuntu. I thought..."let's give it a try and see what all the hype is about"

I used wubi to install 8.10. Downloaded (took forever) and finally installed! Yay! It told me to restart my system.

<RESTART>

"WTF is initramfs??" I thought. Gave it 10 minutes. Nothing happened. I gave up. I see here that the problem still isn't resolved since April (!). Sorry Ubuntu, I gave it a try and you lost me for life.

Ubuntu 'just works'?? yea...right :roll:


BTW system setup:
AMD Phenom quad core 2550
SATA RAID 0 (4 disks)
4GB Memory (400 MHz--i think)
Biostar TF8200 A2+ Ver 5.x Motherboard
Dual Boot with Windows xp 64-bit
dual monitor

---

### Post by want2bdifferent on 2008-11-20
> **one_time_poster said:**
> I went through the trouble of registering/activating on this forum so that I can voice my opinion right now.  Keep in mind this is my first (and probably only) post.

I've heard the buzz about ubuntu. I thought..."let's give it a try and see what all the hype is about"

I used wubi to install 8.10. Downloaded (took forever) and finally installed! Yay! It told me to restart my system.

<RESTART>

"WTF is initramfs??" I thought. Gave it 10 minutes. Nothing happened. I gave up. I see here that the problem still isn't resolved since April (!). Sorry Ubuntu, I gave it a try and you lost me for life.

Ubuntu 'just works'?? yea...right :roll:


BTW system setup:
AMD Phenom quad core 2550
SATA RAID 0 (4 disks)
4GB Memory (400 MHz--i think)
Biostar TF8200 A2+ Ver 5.x Motherboard
Dual Boot with Windows xp 64-bit
dual monitor
exact problem i am having.

I am using an MSI wind U90

---

### Post by vs8 on 2008-11-25
I've posted this on Launchpad, I hope someone does something because this affects more people than we think.

I have an Acer Aspire 5050-5410. Everything started with Hardy, now six months later we still have the same problem. The only difference now is that now you type exit in the Busybox prompt and it boots.

Since I reported this bug to Launch pad I've been playing with some other distros in the same laptop:

Fedora 10 Preview- Compiz runs out of the box (you got to enable special effects) but it makes the whole system slow.

openSUSE 11.1 Beta 5 - The most beautiful distro in my opinion, works great on this laptop and boots way faster than Ubuntu. The only problem is that never got the drivers working.

Arch Linux - Never finished the installation because it's too "advanced".

Debian Lenny - Not my stuff, but it works. The installer took hours.

PCLinuxOS - Meh. But it had the best boot times. Outdated packages because of feature freeze.

Mandriva - Meh, really slow package manager.

Simply Mepis 8 Beta 5 - Man, people say that Ubuntu is ugly and stuff, but wait until you see this! Ubuntu will look like heaven compared to this weird thing! I ran away from it because it was so ugly, but it seems it works.

Linux Mint 6 Felicia RC - It has all the stuff Ubuntu should have out of the box. This is the distro I'm currently playing with. It has the same problems as Ubuntu but all_generic_ide works but it's too slow it's faster to type "exit" every time busybox appears.

The most interesting part is that none of these distros had problems booting, only Ubuntu and Mint (because it's still Ubuntu).

---

### Post by DilbertBusybox on 2008-11-25
I am looking for help with installing ubunt 8.10, use Wubi to install ubunt.  I am using vista 64 bit. Vista is installed on a sata hard drive that uses controller in MB.  I have a abit IP 35 pro with 8g of ram.  I have a raid 0 setup to run some programs, I installed ubunt to the raid 0.  When I reboot vista, I get a dual boot screen, when I select ubunt I get the progress bar then into busybox shell.  I should add my raid is a third party dual channel raid card.

Any ideas -

thanks
Rene

---

### Post by OriginalGrumpyOldMan on 2008-11-25
Coming over from [this thread]("http://ubuntuforums.org/showthread.php?t=968424") which is NOT solved.

I waited a couple of weeks, booted into Intrepid, loaded all the updates: still as broken as ever. Previously I tried most of the things proposed to solve this issue in the above thread.

I have a bog-standard (i.e. old) system that does not require any proprietary drivers, and has worked without much trouble through all recent iterations of Ubuntu.

Basically, -unless- my add-on SATA controller is -fully- populated, Intrepid is not able to boot, neither from my IDE DVD-RW or my internal IDE HDs.

For all practical purposes, that makes Intrepid U-N-U-S-A-B-L-E, not a word that I use lightly: If even a -single- one of the SATA drives fails, I am no longer able to (re)boot Intrepid EVEN THOUGH IT RESIDES ON A COMPLETELY SEPARATE DRIVE ON A COMPLETELY SEPARATE CONTROLLER. I have to open my PC and physically remove the SATA card to get back in... which is pointless on my server because now I can longer access the SATA drives containing the actual data!!!

Why in the world is my SATA add-on prioritized over my internal IDE drives (hda & hdb)? Why does it fail if not -every single- connection is used? Why does the ^#&$*@ boot manager then simply IGNORE the built-in IDE drives and FAIL? It is beyond me how that could have passed QA. Any discussion of the improvements of Intrepid (*) becomes moot if it already fails at boot... when no previous version ever had this problem in the first place!?

(*) and there are quite a few as I found in the short time I actually booted into it, esp. compared to Feisty.

I don't rant a lot since it usually isn't constructive but in this case I had to get it of my chest. Apologies to those who thought this is a waste of time. Back to Feisty, and next time I'll attempt an upgrade, I guess I'll look for another distro, as much as I like Ubuntu.

---

### Post by L0cky on 2008-11-27
I'm having the same problem.

I have both an IDE and SATA controller.  Disabling one or the other with mint installed on an enabled drive will work, however as soon as the other controller is enabled it will drop to busybox.

Installation also becomes extremely tedious as the liveCD (in my case booted from a USB flashdrive) will randomly assign the hard drives in an inconsistent fashion.

After installation I usually have to manually edit menu.lst to assign the correct drives just to get grub working.

I've tried all_generic_ide without success; later I'll try referencing the UUID instead of 'boot=/dev/sda1/' option and post back my results.

---

### Post by want2bdifferent on 2008-11-28
i have tried 8.04.1 and 8.10 and it worked all good on mine

---

### Post by vs8 on 2008-11-29
Try other distros, it only happens with Ubuntu and it's derrivatives like Mint etc. After getting tired of typing "exit" every time I turned the laptop on, or waiting for the "all-generic_ide" super delay I got mad at Canonical and changed to openSUSE 11.0 which is not as good as Ubuntu, but it's good and doesn't feature the BusyBox-screen-of-death.

I'll stick with SUSE until Canonical does something about this issue.

------
SUSE let me down too. Driver support is awfull. I'm gonna keep trying with Ubuntu.

---

### Post by cc247 on 2008-12-01
As the One_Time_Poster stated above: I went through the trouble of registering/activating on this forum so that I can voice my opinion right now. Keep in mind this is my first (and probably only) post.

I've heard the buzz about ubuntu. I thought..."let's give it a try and see what all the hype is about"

I used wubi to install 8.10. Downloaded (took forever) and finally installed! Yay! It told me to restart my system.

<RESTART>

"WTF is initramfs??" I thought. Gave it 10 minutes. Nothing happened. I gave up. I see here that the problem still isn't resolved since April (!). Sorry Ubuntu, I gave it a try and you lost me for life.

Ubuntu 'just works'?? yea...right

I have done the same thing. Tried Ubuntu and had the same problem. Deleting it and will wait for Ubuntu to fix the problem (if they ever do).I don't believe I should have to 'repair' my computer to accommodate Ubuntu.

Good Luck. Windows! I will return to..........

---

### Post by azurehi on 2008-12-01
I experienced great frustration with Ubuntu 8.04 and it's derivatives because of the initramfs/busybox issue.  I was "rescued" by the poster who suggested adding all_generic_ide.  With 8.10, I have had no problem installing and did Not need to add all_generic_ide.  Why the difference?  Why is 8.04, with it's many difficulties, the LTS, long term support, release?

I still use windows xp for one reason:  I enjoy using voip chat and cam in yahoo messenger.  So far I have not found this to be available in linux.

If Ubuntu or any linux distro is ever to challenge windows, it Must install easily and offer everything that windows does - my humble opinion.  I will continue to use Ubuntu and other distros because I enjoy most aspects of them and hope that, someday, they are "complete" from the standpoint of the casual computer user.

---

### Post by cc247 on 2008-12-01
azurehi, 
Nice post. Do you think Ubuntu is listening?
How does one add: all_generic_ide?

Thanks,
Charles:confused:

---

### Post by granny6989 on 2008-12-03
I can't imagine why this post is shown as SOLVED.,....,..

I have had the same problem mostly mentioned in this post and others since trying to install 8.10 (Ibex). 8.04(Hardy) has worked fine for me, as far as drives are concerned. Basic low down is this:

ASUS M2N-SLI board, AMD 64 with built in IDE and SATA controller.
2 IDE hard drives. 1 IDE CD drive. 1 SATA DVD drive.

When I use the live CD, or attempt an upgrade, etc.... to Ibex, i get:  ((xx.xxx) = misc numbers)


(xx.xxx) ata 5: COMRESET failed (errno=-16)
(xx.xxx) ata 5: COMRESET failed (errno=-16)
(xx.xxx) ata 5: COMRESET failed (errno=-16)
(xx.xxx) ata 5: COMRESET failed (errno=-16)
ata 5: reset failed, giving up
initramfs


This always happens after some little blurb about Busybox. I tried enabling the RAID option in BIOS for the SATA drive. No luck. For fun(?), last night I tried enabling RAID for all SATA drives, even though I have only one. Live CD finally booted up ok, got to the demo. Today I booted the CD, and installed. Seemed to go ok, so first thing I tried to enable Nvidia drivers. Machine tried to reboot, and then fell back to evil death loop of initramfs, etc, etc errors, blank screens, lockups, blank screens, etc, etc. login prompts... Finally hard booted and reloaded Hardy.

At this point, the RAID enabling option seems to be a faulty patch at best. It only worked for me after enabling several drives that didn't exist, and even then the system was unstable. After reading a lot of posts and pieces here and there, it looks to be an issue if you have mixed IDE/SATA setups. But that is only a guess on my part. I am going to keep Hardy until Ubuntu can prove that some fix has been made on this, Ibex so far will not work on my machine. I'd like to think that each version will get better, and perhaps it has in some respects, but this is ridiculous, if you expect a new user to grab a disk and install it, and then say 'well, you just have to go into BIOS and lie to your PC that it has RAID drives..'. It really is a bit much for a lot of people who just want to try something different or new. I don't know enough about programming and configuration to fix it or add anything else right now.

I am going to launchpad to post a bug to them in hopes of seeing some fix in the near future. Linux is still better than, well,...., you know.

S*

---

### Post by azurehi on 2008-12-04
cc247, I am not skilled enough to clearly explain how to add "all_generic_ide" other than to say that with All 8.04 variants (Mint, etc.), when the .iso, burned to cd or dvd, loads and language is chosen, I press F6 and the "e" to edit, adding all_generic_ide at the end of the "line" (don't know even what to call it") and then choosing "b" to boot with that addition...mainly trial and error.  I'm sure other readers here migh better help you.  I do not need to do this with 8.10.

---

### Post by knightrider37876 on 2008-12-08
I was able to boot from the LIVE CD to check things out on Ubuntu, but it hosed up on me... When I rebooted I was getting the initramfs, busybox deal... Thinking about trying Linux Mint now... Would have liked Ubuntu If I could have gotten into it...

---

### Post by 50words on 2008-12-08
Fixing the problem on my Dell 530 turned out to be incredibly easy. Based on what someone else here said, I peeked inside the box. The wire that connects the hard drives to the motherboard has two plugs on it, and the hard drive was plugged into the plug in the middle of the wire, not the plug at the end of the wire.

On my other desktop, where I do not have this problem, the hard drive is plugged into the end of the wire. I switched the plug on my Dell so that the hard drive was plugged into the end of the wire, and no more initramfs problem.

Edit: Actually, now I am getting a "diskette drive 0 seek failure" error. Any ideas?

---

### Post by danheeks on 2008-12-08
This worked for me on my Dell Inspiron 530.
I changed the SATA setting from IDE to RAID.
I am a Linux Newbie, but fortunately I know what a BIOS is.
Even so, I was thinking of asking for my money back at one point.

---

### Post by dymaxion on 2008-12-09
For the record... I'm having the same problems as everyone else with 8.10

I'm trying to run/install on Sony VAIO TT, and end up at the BusyBox shell.  Tried all different permutations of the command line boot options, nothing seems to work.

Can't believe they can release a new version with so many install problems for so many people!

Hope they fix it soon, otherwise I'll be stuck with evil Vista for the forseeable future on this laptop.

---

### Post by knightrider37876 on 2008-12-09
Tried Kubuntu... Thought maybe some chance it would work, but get the same problem as Ubuntu...

---

### Post by knightrider37876 on 2008-12-09
> **dymaxion said:**
> For the record... I'm having the same problems as everyone else with 8.10

I'm trying to run/install on Sony VAIO TT, and end up at the BusyBox shell.  Tried all different permutations of the command line boot options, nothing seems to work.

Can't believe they can release a new version with so many install problems for so many people!

**Hope they fix it soon, otherwise I'll be stuck with evil Vista for the forseeable future on this laptop.**

Have you thought about trying Fedora 10?

---

### Post by vs8 on 2008-12-09
Yeah, try other distros for the moment. Fedora is pretty good but not recommended for newbies there is also openSUSE and lots and lots of other distros.

---

### Post by dymaxion on 2008-12-10
Maybe I'll give Fedora a whirl, given that we use RHEL 5 at work, maybe this will be a better fit :-)   Shame Ubuntu is broken eh...

Anyone got any recommendations of Fedora over Suse? Given that I have a VAIO TT and worried about running into driver issues given how new my hardware is....

---

### Post by vs8 on 2008-12-10
Fedora plays a bit nicer with drivers and in some cases you don't need proprietary drivers to enable desktop effects. They have a very nice repo called rpmfusion, it's very good. Fedora has some nice features and the login screen after you install it is the best ever.

Overall its fine.

---

### Post by knightrider37876 on 2008-12-12
Any word of a fix for Ubuntu yet? I'm wanting to put it on my wife's laptop as right now it has Vista... blah!

---

### Post by jdeal on 2008-12-13
I just want to add myself to the people having the problems listed here.

System: Vostro 200, 3 GB RAM, 320 GB disk dualboot with Vista purchased August 2008

I first installed 8.04.1 (64-bit) in August and it worked fine.  Starting in November I started getting the ata1.00: Revaluation Failed errno=5 errors after an update.  I actually got then once or twice before but a reboot always worked.  Now it fails all the time.  The interesting part is the CD I used to install also fails as well as a 8.04.1 32-bit and a 6.06 LTS CD.  However Vista boots every time as does my Fedora F10 (alpha) Live CD and Fedora F9 DVD.

I purchased this system specifically to work on the Ubuntu version of an open-source project (Kompozer).  I have spent days, off and on, during the last month trying to resolve this.  It just seems so arbitrary when it works and when it doesn't.  I did try the solutions mentioned in this and other threads but no luck.  Like a previous post, mine also seemed to be a warmup issue so I would run Vista for an hour or so then reboot to Ubuntu.  Sometime that worked.  Now that does not work either.

Being an old embedded software engineer, this kind of behavior usually pointed to some kind of initialization and/or timing issue or missed interrupt.  Very fustrating.

I am mostly a Fedora person but I was really getting to like Ubuntu.  I have recently installed almost 100 Ubuntu 8.04 systems and except for some HP Xeon processor systems really did not have any problems.   I have it on my laptop and it works great (however, after reading about the bad update experience of others with 8.04.1 I have not applied any updates).

As far as my Vostro 200, I am throwing in the towel.  I am moving it to Fedora 10 since it seems that Ubuntu 8.10 does not fix this either.  Bummer!

---

### Post by Zehuti on 2008-12-14
Well, this issue rather annoyed me, and after reading through 15 pages of this thread, I finally decided to try my other disk drive (it's slower, so I didn't want to use it). But sure enough, it fixed it.. Thanks for all of the help, I love this community :)

- This is with Ubuntu 8.10, ABIT AW9D-MAX

---

### Post by RJARRRPCGP on 2008-12-15
> **HDave said:**
> FIXED!

The hard drive UUID in my GRUB menu.lst was wrong.  I had swapped out my hard drive when my machine was running Gutsy.  I had fixed the UUID in /etc/fstab (you have to or you can't login).  However I never changed the UUID in /boot/grub/menu.lst and when I upgraded to Hardy I used the new "merge" capability to get my new menu.lst file.

Apparently Gutsy didn't care the UUID was wrong, but Hardy does.  I booted into windows, copied the UUID from fstab and pasted it into menu.lst I now I am swimming in 8.04 goodness.

Oh, the fstab! -> That's after the kernel loads. Oops.

It looks like a failure of detecting the IDE controller (includes SATA) or the IDE controller (includes SATA) being unsupported.

---

### Post by 21Jerry on 2008-12-18
OK guys, I've tried everything in the past 29 pages.  I am pretty sure the motherboard is a P400E Asus.  

The problem varies by drive.  At first I couldn't get the install to finish after the boot post wubi.  I moved to a different drive and the install finished after trying about 50 times and then the initramfs prompt came-up on boot.

I played with the raid controller on the mo-board and I can make the symptoms change but can't get past the initramfs.  I have 4 dirves on the system plus an IDE CDrom.  I can't get the install finished on the two drive attached to the IDE connectors but it will install on the two on the raid controller.  Once installed on the raid connected drives, I get the initramfs prompt on normal boot.  go figure.

I am using 8.04 for EMC2 and the CD boots, I can run but can't instal.

Jerry

---

### Post by 21Jerry on 2008-12-18
solved my problem.  Since I had installed under XP, I had to ensure XP was shutdown properly.  Without a proper XP shutdown, I get the initramfs fall-out.

Thanks anyway,


Jerry

---

### Post by Kopachris on 2008-12-18
Okay, I'm adding myself to the list of people with this problem, although the nature of the problem is a bit different in my case.

I built a LiveDVD from my Intrepid Installation.  Well, one of them, anyway.  The one that I'm using as a base DustbunnyOS installation, hence the creation of the LiveDVD.  I've tried everything in the first 10 pages that apply to my situation.  I have no SATA or RAID, and I use and ASUS mobo.  The floppy thing might have applied to me (so I tried it) because I had to plug the floppy power cable into my new video card to get it to work.  So now my floppy drive has now power, but the ribbon cable is still plugged into the mobo.

I'll be looking through the various configuration files in the work directory to see if I can figure it out.  In the mean time, my main Intrepid installation still works perfectly.
Let me know if someone figures this whole BusyBox fiasco out, and I'll let you know if I figure it out!

---

### Post by celtic_hackr on 2008-12-20
Just going to add my $0.02 here. When is Ubuntu going to fix this bug?

Here's another system affected: Acer Aspire 4730z. Intel dual core T3250 (iirc) + Atheros, 2GHz, 2GB, 14.1". This drops to a busybox initramfs console. This is to be a xmas gift for a nontechie, barely pc literate user. I could make this work for Ubuntu (actually Mint + KDE), but then since Ubuntu doesn't care to ever fix this bug it'll be a maintenance nag for me. So when is Ubuntu going to fix this? Oh well, I guess I'll install some other debian based distro. Or maybe fedora 10. Since it worked out-of-the-box, I may leave it.

UPDATE: The Linux Mint release Felicia Main Release, which is based on Ubuntu Intrepid Ibex 8.10 works fine with the aforementioned computer. However, this is a default Gnome desktop. I'm a KDE guy, but this Gnome looks actually usable for the first time ever. Although, I'm sure there's plenty of annoyances down the road if I leave it like this. ;)    
So the long and short of it seems to be that Ubuntu Intrepid Ibex 8.10 should've been tried by me before posting this and maybe this will help others. :/

---

### Post by bertolo on 2008-12-21
hi all. in my university this bug is the number one bug of them all.
it got nothing to do about the system just about the disc. i switched computer with the same hd and i got the same problem.

IMPORTANT NOTE: THE PROBLEM IS IN THE HD

---

### Post by Kopachris on 2008-12-21
> **Kopachris said:**
> Okay, I'm adding myself to the list of people with this problem, although the nature of the problem is a bit different in my case.

I built a LiveDVD from my Intrepid Installation.  Well, one of them, anyway.  The one that I'm using as a base DustbunnyOS installation, hence the creation of the LiveDVD.  I've tried everything in the first 10 pages that apply to my situation.  I have no SATA or RAID, and I use and ASUS mobo.  The floppy thing might have applied to me (so I tried it) because I had to plug the floppy power cable into my new video card to get it to work.  So now my floppy drive has now power, but the ribbon cable is still plugged into the mobo.

I'll be looking through the various configuration files in the work directory to see if I can figure it out.  In the mean time, my main Intrepid installation still works perfectly.
Let me know if someone figures this whole BusyBox fiasco out, and I'll let you know if I figure it out!

Okay, my problem was completely unrelated.  It spawned because it couldn't find /sbin/init on the LiveDVD for some reason.  I'm guessing it's because I messed up while making the squashfs.

---

### Post by bertolo on 2008-12-22
I solved the problem. I unpluged my hard drive and boot pc without any hd in it. it worked. then , because i want ubuntu installed, i had to get a hd that don't give that anoying bug, so i used 2 very old hds 15GB + 1.7GB. Installed ubuntu perfectly.

so like i said the problem is just with some HD.

---

### Post by superklaus on 2008-12-29
Hi,

I agree, it seems to be a problem depending on the HD.
I have an Asus A8N-E with nforce4 chipset. If I connect an old Samsung SP1614C Sata HD with 1.5 Gbps, everything works fine.
But if I connect the newer Samsung SAMSUNG HD502IJ with 3.0 Gbps, the system hangs with the described error.
Please notify that the problem occurs also if I boot from DVD, e.g. Kubuntu 8.10., this means that any boot-process with an 8.10 Ubuntu hangs if this drive is connected!
With 8.04, I hadn't any problems. The only workaround I know is to disconnect the power from the HD when it hangs and then reconnecting it. After this, the system boots correctly without any further HD-related probs.

Does anybody know a better workaround? What HD-drives do the others have?

Greetings

Klaus

---

### Post by sweetcheese on 2008-12-30
Just thought I'd pop in and thow my noobish 2c into this. Excuse my lack of technical skills, I'm a person that takes computers into some guy and pays him 60 bucks an hour to download a driver. 

I was getting kicked into BusyBox, getting the same error messages as others. After trying many different CDs and versions and other hints, I eventually choose one of the other options listed after inserting the CD while in XP, which are a little different then the ones that show up when I boot off the CD. It worked. I have a duel boot now, which is annoying but acceptable.

The reason I wanted to mention it was I was going to give up with the idea that maybe I had a hardware conflict or some setup issue that is beyond my limited skills to fix...but it worked. I'm curious, what's the difference? Same hardware, same CD...maybe installing it within XP adds something?

Sorry if this is completely off base, just hoping a little more info helps solve this for people.

BTW, what a neat operating system.

---

### Post by mrbandersnatch on 2008-12-31
I have this issue on a brand new I7 920 system with a Gigabyte ex58-ud5 and .... 4 x Samsung Spinpoint HD103UJ drives *sigh*.

Now from past experience the problem with the busybox problem is that it doesnt give enough information to diagnose the error (I've had this on a variety of systems in the past and almost every time its been something different required to fix it).

I'll report back when I get it fixed for this set-up...others have installed on this board without issue, but the main point is :

**THERE IS NO SINGLE-CAUSE FOR THIS ERROR APART FROM THE FACT THAT BUSYBOX AND CASPER LOGS DONT PROVIDE ENOUGH INFORMATION TO DIAGNOSE THE PROBLEM FULLY.**

Amazing that about 3 years since I first hit on this problem it still isnt fixed.

EDIT : SOLVED. For this board, if even a single drive (hard...might not be an issue with the dvd hanging off here) is attached to the gigabyte sata2 controller the install routine drops into busybox. Its *possible* that one might be able to get around this by waiting about 10 minutes before typing exit at the busybox prompt (the drives are eventually detected) but I opted to just hang everything off the ICH10R.

---

### Post by csbrudy on 2009-01-01
I've read all these posts and can't believe the community hasn't come up with a solution....  I'm going to try 7.10, then I'll try the alternative iso.bittorrent for 8.1, 8.04, then 7.10.  If none of them works, I'll try Debian....

Finally, if I have to, I'll buy XP, and hate myself.

Somebody said this has been going on for three years?  Unreal.

---

### Post by tomthumb99 on 2009-01-03
I am new to Linux, but with PCs for 17+ yrs, found the thread that mentioned about installing an IDE drive that got me moving forward (Grub on IDE now). Took me three weeks to get Grub and 8.10 setup. Tried 8.04 three months ago (NG), must have installed it 20x. Lost all partitions on three separate drives (2-SATA 1-IDE) during this experience:)

The setup program (live CD) does not cover these tech setup details with any justice. How many new 'folks' are being pushed back to MS due to these issues (ie:50%-60%).  All new PCs have SATA drives, the software must work with it.  I would be nice to see a reduction in some low value deb upgrade files (SA X-fonts!), fix critical problems (ie: OS setup & stability).  Also Grub has to go, assembler programming died 20 years ago.

---

### Post by andre805 on 2009-01-04
Same problem here.  Initially, I successfully used "try without installing" to format my Seagate ST3500461NS for dual-boot.  After I installed Vista Ultimate 64-bit I attempted to come back and install Ubuntu 8.04, which is when I received the busybox issue.  

Just thought I'd contribute with my experience...

---

### Post by natrbro on 2009-01-04
This problem could be caused by different reasons for different people, but the splash screen hides all of the details.  Go to the more options thing by pressing F6 and delete the word "splash."  Continue in booting up and tell us what appears.  In my case, I get a series of Buffer I/O errors on my primary drive.

---

### Post by Kopachris on 2009-01-04
> **natrbro said:**
> This problem could be caused by different reasons for different people, but the splash screen hides all of the details.  Go to the more options thing by pressing F6 and delete the word "splash."  Continue in booting up and tell us what appears.  In my case, I get a series of Buffer I/O errors on my primary drive.
Hmm.  Even though I don't get the initramfs + busybox problem, my hard drive squeals with the activity LED on constantly every now and then while I'm in the LiveCD.  When I shut down the computer (which fixes it) it mentions buffer I/O errors on my primary drive.

---

### Post by andre805 on 2009-01-04
I deleted the word splash after pressing 'F6'.  All I got after doing so was "Loading, Please Wait..." then it went back to the busybox prompt.

---

### Post by BlackCat13 on 2009-01-06
> **andre805 said:**
> I deleted the word splash after pressing 'F6'.  All I got after doing so was "Loading, Please Wait..." then it went back to the busybox prompt.

Also take out "quiet"... should do the job

---

### Post by csbrudy on 2009-01-06
I'll give it a shot.  It seems to load fine atop XP, but then, who would need it, right?

I tried "FreeDos", and attempted to load 8.1 atop it, but no dice.

I've picked up a utilities disk that will format the drive, and I'll give that a try if the "splash" and "quiet" deletions don't help.

---

### Post by BlackCat13 on 2009-01-06
Taking out splash will simply remove the splash screen... taking out quiet will allow you to see the verbose print out of what is happening... won't fix any problem but will tell you where the problem is... because the system will show you where it is hanging before dropping to busybox... :)

---

### Post by csbrudy on 2009-01-07
I'll take out "quiet" first.  Thanks

---

### Post by csbrudy on 2009-01-11
Long weekend.  I checked the jumper on my CDROM and moved it to the master position.   Presto, the "run from disk" version loaded up.

Now, I've got disk formating problems, so I'll be back to describe them.....

---

### Post by jml66 on 2009-01-17
I was running kubuntu 8.04 on an old desktop (Duron 950mhz) with a maxtor 20GB hard drive to which I added a 250GB Seagate internal drive. All was going well until I messed everything up trying to convince Xorg to use a 1024x768 screen resolution instead of 640x480 with which I got stuck after changing monitor (previous was 800x600).
I installed Kubuntu 8.1 on the Seagate 250 GB drive and got to initramfs + busybox. I tried a couple of edits as found on previous messages in this thread but nothing worked. Worse yet after installing flawlessly (up to rebooting) I could not boot from cd anymore even though it was set in the bios. I opened the box,switched master/slave settings and reinstalled Kubuntu 8.1 on the Maxtor drive, and same thing happened. Now I am really stuck with two unusable systems and no clue as to what to do to get rid of them (maybe set the cd drive as primary master ...). Any idea anyone?

---

### Post by jml66 on 2009-01-18
Next day: I switched ide cable plugs on mainboard rebooted and still stuck for good now. Cannot boot from cd and still the busybox+initramfs bug. So contrary to what is said in previous posts the problem has nothing to do with drive type. Hope someone can tell me how to get the boot from cd back.

---

### Post by csbrudy on 2009-01-18
Iam66,

You are way ahead of me.  I had 8.04 running on a 500Mhz Duran with a 40G hard drive, but got turned on to a better machine with a valid copy of XP on it, which I later screwed up.

So I hooked up the old Duran machine, but somehow the 8.04 had gotten corrupted.  so I threw the 8.04 iso disk in, and presto, I got the busybox crap.  I tried 7.04, 6.10, and finally 8.10, but it was busybox all the way.  I changed the jumpers up and got 8.10 to format and partition the drive, but as soon as it began loading, the busybox set in.

I'm wondering if someone from microsoft is a mole.....

You know, if Ubuntu would load right up, and made it easy to add new programs and hardware, then Windows would crash and burn...

Anyway, I'm tired of messing with it......

---

### Post by jml66 on 2009-01-18
Hi csbrudy,
Would you please elaborate a little more on your jumper settings. What do you mean by "Presto, the "run from disk" version loaded up."? Did the cd drive  boot or the internal hard drive?

---

### Post by vs8 on 2009-01-18
Hahaha a mole from Microsoft! That's clever... but who knows!

Try a different distro, maybe Fedora or openSUSE maybe they'll work for you and those distros don't feature the busybox screen of death. That's an Ubuntu exclusive!

---

### Post by csbrudy on 2009-01-18
How about Debian?

---

### Post by vs8 on 2009-01-18
Yes Debian is a good option, in fact PCLinux too, but I'm more familiar with Fedora and openSUSE, that's why I recommended those.

---

### Post by csbrudy on 2009-01-18
Thanks for the tips.  I had a Win 98 disk and it formatted the old drive, then hung.   I managed to burn an iso of "FreeDos", which actually loaded.  I tried all the Ubuntus and the 98, and nothing worked.  I'll try Fedora and openSUSE... That is, while I wait for the OEM XP I ordered from Newegg.

Why go through it?  Why pay?  Because I'm recording music, and everytime I install a new application that uses the sound board, the Linux Ubuntu had troubles....  I used the ALSA mixer, and it had to be tweaked for Limewire, Goldwave and Audacity, which overwhelmed the OS.   So, Frak it, I'll bow to Bill Gates and enjoy the universal sound experience....  I've got a cheap sound blaster card, but it works OK, on XP....

---

### Post by csbrudy on 2009-01-18
I thought you might have seen it on the thread, I didn't realize you couldn't.....   There are two ribbon cables with two plugs each.  One ribbon goes to the hard drives, and the other to the CDROMs.   
The "jumpers" on the back of all the drives have several positions, but two of them that are important are the master and the slave.  The letters are a little different with different manufacturers, I think, but you should be able to tell which is which.  use tweezers or a little needle nose to move the jumper from position to position.  One of each type of drive is the master and the other the slave.

What I found new was that the "master", of both of the types of drives must be plugged in at the END of the cable, and the slave on the other one, closer to the motherboard.

I managed to get a few steps further before the Ubuntu went to the "busybox" screen...

Hope I'm not too late.

---

### Post by jml66 on 2009-01-19
Thanks for replies.
Both drives were set to 'cable select'; I changed jumpers to master and slave (off) and could boot from cd again. I downloaded and installed Fedora 10 which gave me a default 1024x768 screen res straight out of the box: great!
The yum package installer is not so great though but monitor resolution was my main problem and I had been fiddling with it for a damn long time.
EDIT/ Screen res is fine allright, the rest of the dist is not so great. I do not know if it comes from Fedora core or from KDE4 but many problems: very poor plug and play support (usb hard drive and usb dvd writer), a lot of errors and freezes: definitely not for the usual windows user like me.

---

### Post by Zjonn on 2009-01-19
I haven't gone through the whole of this posting (all 32 pages that is), only the first couple and the last couple, trying to see if anyone has come up with a solution to the original problem quoted here.
In my case, after installing Ubuntu, using Wubi, I was prompted to allow a restart to facilitate finalizing the installation of Ubuntu 8.1.
I booted up to Ubuntu, it showed an initial splash screen indicating Ubuntu was firing up, and after a short while I also got the "Busy Box V1.10.2 message followed by "Initramfs".
Than over the next few minutes it started to show a number of USB 2.2 errors (-32) three times, followed by (-110) four times.
I then noticed that my router went off line (though still in synch). Nothing after that, I left it alone for about ten minutes in case is was actually doing something, but nothing.
Some of the earlier posts suggested setting the SATA mode to Raid, I have a RAID system using 2*80 GB serial disks as one 160 GB disk, so it was configured as RAID, that's not a fix, at least not for me.
To give you an idea of my system's configuration;
Vista Ultimate (should have been sold as ultimate disaster)
Mother Board = A7N8X-E Deluxe (ASUS)
AMD Athlon XP3000+
Radeon X1650 graphics card.
I get the thought that Ubuntu is not seeing the RAID configuration and that it is unable to see my Internet connection. If anyone has any ideas as to how to remedy this situation, I would be most grateful.

---

### Post by csbrudy on 2009-01-19
I can't believe something I passed along actually helped someone. jml66.  I can't fathom Zjonn's problems because I'm using medieval hardware.   see you all..

---

### Post by vs8 on 2009-01-19
> **Zjonn said:**
> I haven't gone through the whole of this posting (all 32 pages that is), only the first couple and the last couple, trying to see if anyone has come up with a solution to the original problem quoted here.
In my case, after installing Ubuntu, using Wubi, I was prompted to allow a restart to facilitate finalizing the installation of Ubuntu 8.1.
I booted up to Ubuntu, it showed an initial splash screen indicating Ubuntu was firing up, and after a short while I also got the "Busy Box V1.10.2 message followed by "Initramfs".
Than over the next few minutes it started to show a number of USB 2.2 errors (-32) three times, followed by (-110) four times.
I then noticed that my router went off line (though still in synch). Nothing after that, I left it alone for about ten minutes in case is was actually doing something, but nothing.
Some of the earlier posts suggested setting the SATA mode to Raid, I have a RAID system using 2*80 GB serial disks as one 160 GB disk, so it was configured as RAID, that's not a fix, at least not for me.
To give you an idea of my system's configuration;
Vista Ultimate (should have been sold as ultimate disaster)
Mother Board = A7N8X-E Deluxe (ASUS)
AMD Athlon XP3000+
Radeon X1650 graphics card.
I get the thought that Ubuntu is not seeing the RAID configuration and that it is unable to see my Internet connection. If anyone has any ideas as to how to remedy this situation, I would be most grateful.

Have you tried typing "exit" when the intramfs appears? In my case it works. Another thing that works is setting the kernel parameters to all_generic_ide.

---

### Post by laserbastu on 2009-01-19
Hello, I'm another one with this problem. Other distros (except Linux Mint, also haven't tried Debian) seems to work.

'exit' doesn't work for me, just takes me instantly back to busybox.

I have no idea how to check or alter your jumpers nor what I'm supposed to look for when it comes to alter them (sorry if it's stated in one of the earlier posts, I really don't feel like reading through 32 pages of posts).

---

### Post by laserbastu on 2009-01-19
> **vs8 said:**
> Have you tried typing "exit" when the intramfs appears? In my case it works. **Another thing that works is setting the kernel parameters to all_generic_ide.**

That actually made the trick!! After all this searching this somehow made me boot into Ubuntu, and fast too!

Thank you!

Edit: I'll add some instructions for people who're lost (sorry I don't know all the proper names for everything, but hopefully you will understand what I mean)

1. Let the computer start and enter the grub menu.
2. Press 'e' on your keyboard to edit the boot config
3. Press the down arrow key to reach the 'kernel' boot parameter and press 'e' another time
4. At the end of the line add "all_generic_ide" so that your line looks something like this:
```
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=43206294-74ef-434d-aca2-db74b4257590 ro quiet splash all_generic_ide
```
5. Press enter
6. Press 'b' (without exiting the grub config)

This should make your system boot (if you had the same problem as me that is, if this didn't work for you you'll have no use in reading further), but this is just a temporary solution that you will have to repeat every time you boot your computer. To make this permanent you have to edit your "/boot/grub/menu.lst":

1. Make sure Ubuntu has booted properly.
2. Start a terminal and enter: ```
gksu gedit /boot/grub/menu.lst
```
3. Scroll down and you will find a similar line to the one you edited before in the grub boot config, it will look something like this: ```
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=43206294-74ef-434d-aca2-db74b4257590 ro quiet splash
```
4. Add all_generic_ide at the end of the line, like this (do NOT copy paste this line, your UUID number WILL be different from mine, if you copy paste you will just give yourself more problems):```
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=43206294-74ef-434d-aca2-db74b4257590 ro quiet splash all_generic_ide
```
5. Save the document and close gedit.

That's it!

By the way, if you update your linux kernel through a system update you might get a question if you want to keep your old menu.lst or copy it over with a new one. I recommend copying it over and adding the "all_generic_ide" to your boot options in your new menu.lst afterwards.

---

### Post by Zjonn on 2009-01-20
> **vs8 said:**
> Have you tried typing "exit" when the intramfs appears? In my case it works. Another thing that works is setting the kernel parameters to all_generic_ide.

Yes I have tried exit and the result is not pretty, suffice it to say that after a whole lot of i/o errors,it finishes up with;
"line 231:cannot open /root/dev/console, no such file
Followed by
[120.152828] kennel panic not synching attempting to kill init
than nothing
As I stated earlier, I don't think Ubuntu is seeing the Raid configuration and it appears nor does it appear to see the BIOS.
As far as re-setting the kernel parameters, no I haven't. I don't know where to find the kernel or how to edit it.

---

### Post by superklaus on 2009-01-20
Hi,
finally, the all_generic_ide kernel parameter helped :D
Here is my hardware:
- Asus A8N-E with nforce4 chipset
- Samsung SAMSUNG HD502IJ
In 95% when I tried to boot, I got the above mentioned COMRESET failed (errno:-16).
Then, I tried to boot with an old PCI Sata Card with Sil3112-Chipset and.... everything works fine. 
After that, I tried the all_generic_ide parameter with the build-in controller (nforce4) and it works too!
So here's my conclusion about this problem:
The sata_nv-driver used bei kernel 2.6.27-11 has definetly a problem with some hd-drives like mine.

Greetings

Klaus

---

### Post by Zjonn on 2009-01-20
Sad to say, so far none of the advice given above has actually worked for my system including the exit and edit information.
For edit, there are three lines available to edit, the bottom one when edited only has the following in it;
grub edit> initrd/ubuntu/install/boot/initrd.gz
I tried adding the "all_generic_ide" tag to that to no avail. I am missing something, are there any special drivers that anyone knows about which I need to put somewhere (remember, my system is a RAID 0 configuration, two serial disks as one), do I need a different LAN driver to facilitate the Internet through Ubuntu, any clues anyone?

---

### Post by vs8 on 2009-01-20
> **Zjonn said:**
> Sad to say, so far none of the advice given above has actually worked for my system including the exit and edit information.
For edit, there are three lines available to edit, the bottom one when edited only has the following in it;
grub edit> initrd/ubuntu/install/boot/initrd.gz
I tried adding the "all_generic_ide" tag to that to no avail. I am missing something, are there any special drivers that anyone knows about which I need to put somewhere (remember, my system is a RAID 0 configuration, two serial disks as one), do I need a different LAN driver to facilitate the Internet through Ubuntu, any clues anyone?

It's in the line that starts with "kernel". I think it's the second line. Try once more and report back.

Good Luck.

Oh and sometimes you need to type exit 2 times, it happened to me once.

---

### Post by Zjonn on 2009-01-21
> **vs8 said:**
> It's in the line that starts with "kernel". I think it's the second line. Try once more and report back.

Good Luck.

Oh and sometimes you need to type exit 2 times, it happened to me once.

I gave it a go, unfortunately no joy, just a lot of i/o errors..
Any other suggestions?, I still think that it needs drivers for the RAID and LAN. I have posted with ASUS's forum, re- my MB and UBUNTU asking the question and I will post any result here if useful, other than that, I hope someone else knows on this forum as to what the culprit might be.

---

### Post by jx3000 on 2009-01-21
Has this been fixed yet?

I can't boot ubuntu 8.10

---

### Post by vs8 on 2009-01-22
Look at this article!

When is this going to be fixed?

[http://www.computerworld.com/action/article.do?command=viewArticleBasic&taxonomyName=&articleId=9126042&taxonomyId=&intsrc=kc_feat](http://www.computerworld.com/action/article.do?command=viewArticleBasic&taxonomyName=&articleId=9126042&taxonomyId=&intsrc=kc_feat)

This guy is very lucky! I wish my PC booted normally after only 2 Busyboxes!

---

### Post by jx3000 on 2009-01-22
Imagine this was an LTS.

My install was with a LiveCD, has anyone tried the alternate CD method? Would that fix it.

---

### Post by Unitas on 2009-01-22
I've been following this thread and thought I'd share my experiences.

I had this error first on my desktop. (8.10/WinXP wubi install) This was after I installed ubuntu. After shutting down and restarting a few times it fixed itself. (My mobo has strange shutdown issues anyway)

I then did a wubi installation to my laptop from a live persistent usb drive. After installation I got the error again. I tried shutting down and restarting several times and that did not help. I tried editing the kernel boot options as others have done (irqpoll, floppy=off, all_generic_ide, etc.) with no luck. Selecting hibernate on accident from the windows installation screwed my mbr (wouldn't load anything), had to go into windows recovery to get it back to windows/ubuntu.

I then booted into windows, uninstalled the wubi installation of ubuntu, and then reinstalled with wubi from the main drive, letting it download the image itself, not running wubi nor installing the image from the usb. 

That worked. Unfortunately for those doing a complete installation having problems even booting the CD, I can't help.

Some details that might/might not matter: 

The usb installation was the 32-bit version, whereas installing from wubi on the local hd installed the 64-bit version automatically. (I have a core 2 duo in the lappy)

Booting ubuntu off the usb worked. I only had the initramfs error after installation.

I hope this helps some folks.

---

### Post by vs8 on 2009-01-22
That's the worst part, the problem lies after the installation. If wasn't so bad if the live disc didn't boot and your pc doesn't loose anything.

Lets say you want to get rid of XP or Vista in an older PC. You pop in the disc and it works (at least you think so) you like it and decide to get XP/Vista out for good. When you finish your installation and reboot... boom! Busybox!!!

You are going nowhere baby!

Like someone said, this could be some Microsoft's mole work!

I'll just wait for the developers to do something about this:popcorn:!

---

### Post by Zjonn on 2009-01-23
Not being one to give up, I decided to check out RAID as pertaining to Ubuntu and came up with this link; 
[https://help.ubuntu.com/community/FakeRaidHowto](https://help.ubuntu.com/community/FakeRaidHowto)
which explains about fake RAID, or software driven RAID which is what is supported by my MB.
I will be giving this a try and will dutifully report back when I have finished doing what is suggested in this posting.

---

### Post by nux_man777 on 2009-01-23
Hi all I  have seen a lot of different scenarios with this issue for version 8.10 and 8.04..The reality is after testing three different machines with certain cds that I bought online, I was getting to that initranfs prompt which frustrated me for days.I downloaded  v8.01 and burned my own cds at 4x and 8 x using free iso software burners and same scenario...I messed around with the hardware and bios and same thing kept happening
Like Alice in wonderland  I asked why will version 7.01 install on these sytems with the same hardware and bios settings and version 8.04 and 8.10 will not work..Then it dawned on me!!!

The hardware will seem or  appear to be the issue with these builds  because the media most people with issues are having is that the cds aren't burnt porperly  which leads to corrupt files.These files try to make an association with the harddrive and media devices and the builds crap out..

I have resolved my situation on all three systems and installed  version 8.10 on all three flawlessly.The solution is  very simple ...use a good iso burner like ROXIO and burn cd at 10x

Please note that there may be other exceptions and scenarios, but I will start here first before ripping down your systems
hope this helps someone

---

### Post by vs8 on 2009-01-24
The CD recording process has nothing to do with this all of the time. My Ubuntu Live Disc come directly from Canonical and they work perfectly in other PCs. The one I always download is the x86_64 version the day of the Ubuntu release and those Cds work perfectly too.

The problem is an Ubuntu installation bug it doesn't have anything to do with the hardware (at least in my case) because other distros work without a hassle and boot perfectly after instalation.

---

### Post by cspizz on 2009-01-24
I agree with vs8.  For myself, I use [imgburn ]("http://www.imgburn.com/")(stellar software) to burn the iso on to [Taiyo Yuden]("http://en.wikipedia.org/wiki/Taiyo_Yuden") DVD+Rs (stellar media).

Many people resolve this issue by editing their boot parameters.  That wouldn't seem to indicate a corrupt image.

---

### Post by Zjonn on 2009-01-27
Well, I finally am fully back on the air and have both operating systems (Vista and Ubuntu) working on my system. One HD, partitioned, one partition for Windows and the other two for Ubuntu. Yes I did end up downloading the Ubuntu 8.1 alternative install CD image, copied it to a CD and have had no major problems with the process.
Just to go back and re-acquaint you with my setup, a RAID 0 configuration consisting of two 80gb drives run as one.
I backed up all of Windows
Split the Raid drive in to one partition (about 60%) for windows and left the other for later as unused or unallocated.
Re-installed Windows and got it back to business as normal.
Re-booted the system with the Ubuntu 8.1 Alternative CD
followed the prompts which are totally intuitive, no hard questions at all.
When the installer got to the part of the Raid drive I left it to the software to determine how best to configure the remaining 40% of unallocated space for the two disk areas required which it did without any problems.
At the end it came up with the prompt to change the boot file to facilitate Windows as well as Ubuntu, which you obviously confirm.
I should also mention that the link provides various files and a great number of mirror image links across the world so be sure to look down the page to find the best link for the file which you want to download.
The whole procedure takes about an hour, maybe a bit less and at the end of the day, it ended up being relatively painless.
In case you have trouble finding it, the alternative file is available from this link:
[http://www.ubuntu.com/getubuntu/downloadmirrors#alternate](http://www.ubuntu.com/getubuntu/downloadmirrors#alternate)
So now we see what all the fuss is about!

---

### Post by karthik448 on 2009-02-02
Guys,

I'm having this same problem with Ubuntu 8.10. I can't even boot into the Live CD. The same thing works w/o hassles on my friend's laptop :( .

I have tried all of the suggestions listed in the prev 34 pages, editing the boot menu does no good for me and my MoBo has no options for editing the SATA modes.

I never knew trying out a distro was this hard. I'm back to Windows for now. But looking for any option to get Ubuntu to work for me.. cheers.

---

### Post by jrusidoff on 2009-02-05
I have to laugh at myself....I really thought "how hard can this be?" and tried to install 8.1 (my first Ubuntu).  I have now laboriously worked through most all of the suggestions in this gigantic thread and am still in Busy Box hell.  Can't run Ubuntu on my chosen project computer in any form or fashion!  Back to XP for me....pity.

---

### Post by 85stang on 2009-02-05
I have the busybox problem also.  Dell XPS 720. changing the bios to raid, all the boot options, none of them help.  It is installed on the hard drive, but it takes sometimes up to 6 or 7 boots to get past it, sometimes on the first try.  its real pain and wish it would get fixed.  no luck with 8.10 either, the live CD boots to a terminal and says there is no display to start X!

---

### Post by FranklinSt on 2009-02-08
I have the "COMRESET failed (errno:-16)" problem also. But I've tried to install Mandriva 2009, Kubuntu 8.10, Ubuntu 8.10 and Fedora 10 with the same result for all distros. It's not just an Ubuntu problem. Seems to me we've got a kernel problem with SATA drives.

---

### Post by csbrudy on 2009-02-08
I tried everything, even an old 98 version, and got the same problem.  It's before SATA drives, I think it has trouble with all drives.

The only thing i could get to work on any of the hard drives, after attempting every Ubuntu or Windows flavor, excepting Vista,
was "FreeDos".

It will let you mess with the partitions a bit, but one still needs to reformat for Ubuntu, and none of the installation sets, either live or the archived, can prep any hard drive.

You would think it would be basic.  The question could be, "use the entire drive?", a person would click OK and half an hour later that person would be downloading video.

But it would be the end of Microsoft, so I would be surprised if people WERE NOT being paid to sabotage the program.

---

### Post by tristar on 2009-02-09
Hi I'm a newbie to Ubuntu and here were some of my findings hope this helps you out. I was able to install Ubuntu 7.04 & 7.10 and the installation went smooth but i got the Initramfs error for 8.10 and tried out all the solution steps given ( not knowing for sure what I was doing) but nothing seemed to get me past that screen & all these attempts were made on a 4GB Flash drive and not a SATA HDD at all.

Installed 7.04 without a problem but really got pissed when I couldn't update it so thought of going to 8.10 and that stopped at the initramfs screen tried all the steps given but nothing seems to happen. I then downloaded 7.10 and installed and it works like a charm.

If this is a SATA issue why would previous versions install on my 4GB flash drive not 8.10 ???? my guess could be more of a SCSI Device issue rather than a SATA HDD issue as am unable to install it on my flash drive... while previous versions seem to work cool...

Did not test 8.04 however because 7.10 seems to be pretty stable from my Flash drive.....

---

### Post by FranklinSt on 2009-02-10
Thanks, Tristar. Would everybody agree we know the problem is distro independent, happens on newer kernels but not older ones and apparently occurs with all storage other than IDE hard drives?

---

### Post by tristar on 2009-02-10
OK!!!!!! here's another update.... 8.10 installs like a charm on IDE drives... booted straight up... Reinstalled as an external drive through a converter and it does not load ????? even IDE through a USB converter messes up.... revert back to 7.10 on the drive Internal & external & on a 4GB flash drive its amazingly good!!!!

---

### Post by FranklinSt on 2009-02-11
Well, we've narrowed it down...who do we communicate this to?

---

### Post by booksbuggy on 2009-02-12
People if you get this problem right after you installed a new drive go in and check if the wiring is secured because I had the same problem until I went and secured the wiring for the hard drives.

---

### Post by duwan on 2009-02-12
I've just completed a dual boot, 8.04 / xp. everything seemed fine.I can boot windows fine but 8.04 goes to  initramfs + busybox. The installation  is on separate harddrives and installed independent,(have to go to boot menu to select system. Can boot 8.04 if xp hd is unpluged, but plug it back in and get. initramfs + busybox when booting 8.04 HELP THANKS

---

### Post by tristar on 2009-02-13
OK !!!!! Another new Update..... Tried installing 8.04 in 4GB Flash Drive no go... Initramfs...

WTF.... So again tried installing it in IDE drive with an external converter for USB again it SPAT the INITRAMFS Error on my face....

But installs like a charm on the IDE drive directly connected...
 
The 8.XX Series seem to mess up when being installed in any other type of drive apart from the IDE drive....

HOPE THIS HELPS !!!! And rings a bell to someone who can fix it !!!!!

**[COLOR="Red"]booksbuggy : Please read the above posts the installation fails even on a Flash Drive Appreciate you trying but it's not helping us......[/COLOR]**

---

### Post by Alamaxia on 2009-02-18
Hello all,

I have browsed through every page on here, tried adding all suggestions to the boot options, but to no avail.  I still get the intramfs + busybox.  When I took off the quiet splash, i noticed it kept looping on:

ACPI: Unable to turn cooling device [db011f18] 'on'

It loops on that for about two minutes then it gives me the intramfs/busybox screen.  Any ideas?

---

### Post by tristar on 2009-02-19
Hey !!!!! Join the Bandwagon dewd... Been here for a long time trying to figure this out....

Now are any Mods actually looking at these posts beats me...

What is the one Final solution for this ???????

---

### Post by vs8 on 2009-02-20
I've been testing Jaunty fo a while in my Acer Aspire 5050 Laptop and it works perfectly. I boots without busybox problems but it stays in "Starting Up..." status for a couple of seconds, then the uSplash appears and the boot process starts.

---

### Post by FranklinSt on 2009-02-21
I even tried to work around the problem by first installing 8.04 (it works like a charm) and then doing a distro-upgrade to 8.10....same problem again!!!! %^&*((*%&$U^%&*(^

---

### Post by vs8 on 2009-02-21
> **FranklinSt said:**
> I even tried to work around the problem by first installing 8.04 (it works like a charm) and then doing a distro-upgrade to 8.10....same problem again!!!! %^&*((*%&$U^%&*(^

I stayed with 8.04, it runs faster on my PC, try staying with it or try using Jaunty, It's very usable even on alpha state.

---

### Post by tristar on 2009-02-22
Additional Updates... Tried to Update from 7.10 to 8.04 using the Internal Upgrade...

Back to a huge mess...

8.04 is supposed to be LTS ?????

Why no fix has been provided for the same...

If its a kernel problem why has it not been updated or fixed...

I am a newbie and this gives me a very negative Opinion on Ubuntu think of moving to Fedora or Deb....

---

### Post by FranklinSt on 2009-02-23
It's not a distro specific problem. I've tried to install the latest versions of Mandriva, Fedora, Kubuntu and Ubuntu....same results.

I've decided to stick with Kubuntu and/or Ubuntu 8.04. They run great, they're VERY stable and they're fast.

---

### Post by bertolo on 2009-02-23
this is the worst ubuntu bug.

---

### Post by FranklinSt on 2009-02-24
The problem is not new.....[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/129817]("https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/129817")

WHY CAN'T THEY FIX IT!???

---

### Post by 3mpire on 2009-02-24
Just adding my voice to the chorus of people who have had this issue.

I am a junior .NET developer looking to broaden my horizons and get rolling with Ubuntu and Ruby on Rails.

I'm building a Ubuntu box but am stuck in the busybox loop everyone here has described.

here is my hardware profile:

ASUS P5KPL-AM/PS LGA 775 Intel G31 Micro ATX Intel Motherboard
Intel Pentium E5300 2.6GHz LGA 775 65W Dual-Core Processor Model BX80571E5300
Western Digital Caviar RE WD2500YD 250GB 7200 RPM SATA 3.0Gb/s Hard Drive

Tried all of the boot parameters in various permutations, created several disks with iso files from different sources, etc. but still no luck.

I will try an older IDE HDD, try using the alternate cd, etc.  Hopefully that will work, if not, I'll try openSUSE.

---

### Post by tristar on 2009-02-25
Well **[COLOR="Red"]3MPIRE[/COLOR]** Dewd i would suggest you to roll back to Dist 7.04/7.10....

7.04 Feisty Installs and works great but you would not be able to download all the updates as they are not even fully available in old-releases.ubuntu.com/releases/..... or in archive.ubuntu.com/releases/....

But try 7.10 its working great... Donno what the pro's would say but i am sitting here typing this out from just a Flash Drive with Gutsy...7.10...

Its as smooth as a feather...and all the updates install nice and easy...
 
The OS itself is great but again such a huge flaw for a newbie like me makes me think twice.....

---

### Post by 3mpire on 2009-02-25
Quick update for everyone: I swapped out the IDE optical drive I originally planned to use with a newer SATA drive and I was able to boot off the CD and install no problem.  Downloaded all necessary updates and didn't have any issues with video or wifi right out of the box.

So chalk my issue up to some kind of conflict with an IDE optical drive and a SATA hard drive.

I have to say coming from my perspective, once I got past this hiccup, the process has been pretty easy.

Cheers.

---

### Post by akashexe on 2009-02-26
> **3mpire said:**
> Quick update for everyone: I swapped out the IDE optical drive I originally planned to use with a newer SATA drive and I was able to boot off the CD and install no problem.  Downloaded all necessary updates and didn't have any issues with video or wifi right out of the box.

So chalk my issue up to some kind of conflict with an IDE optical drive and a SATA hard drive.

I have to say coming from my perspective, once I got past this hiccup, the process has been pretty easy.

Cheers.

what did u actually do?

---

### Post by tristar on 2009-02-27
Well 3MPIRE dewd.... You have given a whole new dimension to this....

Need to see if this may be a fix.... But i am using a SATA Drive for Both the Optical and HDD....

And the installation is being done on a Flash Drive so whats the takeaway for that ?????

Any info, would really appreciate it....

---

### Post by 3mpire on 2009-02-28
> **akashexe said:**
> what did u actually do?

Originally, my DVD optical drive was IDE, and my hard drive is SATA.  With that combo I was experiencing the error that brought me to this thread.

My next attempt was to replace the SATA hard drive with an older IDE hard drive but that still didn't work.

I then went out and got a new SATA DVD optical drive and then put the original SATA hard drive back in.

After I did that was able to boot just fine (off a Live CD) without error.

If you're trying to install off the flash drive, but you have the optical drive, just burn the ISO to physical media and try that.  It seems that this error has to do with the install not finding certain drives (right?).

---

### Post by buckner on 2009-03-01
I have a motherboard so old it doesn't even have sata ports, but i still get to the busybox (initramfs) page when i try to boot the ubuntu 8.10 live cd.
My specs are
Primary IDE Master: 500 gig Hitachi HDP725050G
Primary IDE Slave: ATAPI COMBO 48XMA
Seconday IDE Master: HL-DT-STDVD-RAM GH

With this setup, I could only install ubuntu 8.10 if i put the disk in the secondary ide master dvd drive, but, when it installed, it didn't recognize my other cd/dvd-r drive, the primary slave. I switched the specs so that the ATAPI combo was the secondary IDE master and the HL-DT-STDVD  was the Primary ide slave, but now it only works if i put it in the ATAPI combo drive, and won't recognize the other drive. If i try to install the livecd in the other drive, I get to the busybox (initramfs) page, (hence why i'm here), I don't have sata ports on my motherboard so i can't change the AHCI setting in the bios to RAID, Has anyone else ever come across this problem?

The weirdest thing about this is that I have an older version of Ubuntu (7.10) installed on my computer right now, and it installed no problem, and recognized both of the dvd drives. What's different in the hardware detection between 7.10 and 8.10?

---

### Post by beofres on 2009-03-02
I gave up reading through all 37 pages, and stopped at page 11.

I too am experiencing this problem trying to install 8.10 (and then 8.04) Ubuntu Server.  Here are my specs:

ECS NF650iSLIT-A version 1.0
2 Western Digital 40GB IDE drives on the primary IDE channel
1 older 48x IDE CD-ROM on the secondary IDE channel
3 Western Digital 500GB SATA drives connected to the onboard sata ports, BIOS set to use the nVidia RAID stuff.

I'm installing onto one of the 40GB drives, the install goes smoothly (and detects everything) however grub fails to load and dumps out "Error 26".  I reinstall in expert mode, redo the partitions, install onto the same drive, only install LILO, and restart.  I'm able to get past the boot loader however the system locks up and drops to the busybox crap right after it detects my IDE CD-ROM (see pic below).  Ok, so it's probably the CD-ROM, right?  I remove that, and I get the same message at the last SATA drive in my array (sde) complaining about sda1 not being found (like the error in the picture).  I sequentially remove each sata drive, and then the system boots!  The hell?  Maybe Ubuntu doesn't like nvidia soft-raid, strange since 7.10 did.  Ok, let me disable nvidia's raid and try again.  Go into BIOS and disable the RAID-5 option, restart, and the drives detect as second and third master/slave drives.  The system still locks up at the same message.

[IMG]http://xanaduwapiti.net/ubunturz/IMAGE_004.jpg[/IMG]

My BIOS doesn't give me the option to force my SATA connections into any particular speed.  It just occured to me that since on my machine ubuntu doesn't really tell the difference between nvidia's soft-raid and the drives as just plain drives, that maybe it's because the motherboard treats them as 'fake' IDE drives (the third primary / third secondary and fourth primary fourth secondary) could be causing issues?  My board doesn't have any option to change the detection scheme (read as: no way for me to enable "sata compatability mode" or disable it; the only options I have are to enable SATA, enable the SATA RAID in a different screen, or disable the first two or second two SATA ports.  Am I the only one having issues on first boot after install?

Aside from that, Canonical has really dropped the ball on Hardy, since it seems like a lot of people are having quirky issues with SATA and/or IDE.  7.10 didn't have this issue, and Windows didn't either...just sayin.

---

### Post by tristar on 2009-03-03
Hey 3MPIRE dewd...... I have installed 7.10 directly on the 4 GB Flash drive and this thing is rocketing been using it for quite some time now... Its only with 8.04/8.10.....

But I think this Installation for 8.10 is messed up & Guess what Jaunty does the same even though its still in Alpha stage....

WTF..... They can at least fix this in 9.04... even in the test phase the Dewd does not want to see my drives without an Initramfs....

Guess Ubuntu loves me to stick to 7.10.....I really want to try out the 8.10 but the Raid thing does not seem to work....I tried it one of the Base systems in our Dell Lab an XPS 730 with Raid - 5 no go...

Tried one of the Inspirons and the Studios but it doesn't seem to work....

Looks like I need to live with 7.10... I kinda like it anyway...

---

### Post by gooyboy on 2009-03-03
Hello All, 
Just an FYI. I had this initramfs issue on my system while trying to boot from a cd with ubuntu-8.04.2-desktop-amd64.iso. Tried all the BIOS stuff recommended on the first 10 pages of this tread and nothing worked.  **What did work **was a cd boot from the latest version of ubuntu-8.10-desktop-amd64.iso(downloaded 3/3/09.

Asus A8N-SLI Deluxe/AMD dual core Operon/2GB mem/No Sata drives for now/IDE primary has a WinXP drive and CD/IDE secondary has Ubuntu OS/Nvidia9800GTX

later

---

### Post by vancouver on 2009-03-04
Hello everybody

I've been stuck in busybox+initramfs for 4 days now. Is there any way out. 
I went through most of the pages on this thread to no avail.

---

### Post by salemboot on 2009-03-06
ide=nodma

I've got three boxes that won't boot 810.  

The sad part is it's the libata driver that is the problem.

If you were to disable that in the kernel you get different behavior.  

Debinites should re-evaluate their commitment to this new unification.

Ubuntu developers just need to include a special kernel on the dvd/cdr to boot without libata.  

But they won't because there is a push for the unification.

I never saw nothing wrong with /dev/sda  /dev/hda  because I could tell which was ide, sata/scsi.

---

### Post by tristar on 2009-03-07
Sorry Salemboot with all due respect...

I was not able to understand the post... I am more from a windows background so dunno much about the stuff you said...

Could you translate that into simpler terms....

---

### Post by superklaus on 2009-03-07
Hello,

I'm using Interpid with kernel 2.6.27-13-generic. After installing this kernel, the busybox-problem is solved. :D
I am actually using intrepid-proposed and intrepid-backports.
Greetings

Klaus

---

### Post by 0ra1suicid3 on 2009-03-09
how do i make it work on a usb external hd? i tryed most of the suggestion in post
i have a mac with i want to dual boot
i get busy box then keep saying ata3: device not ready
the when i replase silent thing to debug and all_generic=ide irqpoll it goes on and reconise my 750G external hd but it say: link to slow but it usb 2.0? wtf
eny help

---

### Post by bpmelo on 2009-03-12
having the same problem here under 8.10, this is the output i'm getting on dmesg :
```

[   11.066553] ata3: SATA link down (SStatus 0 SControl 310)
[   16.424014] ata4: link is slow to respond, please be patient (ready=0)
[   21.072009] ata4: COMRESET failed (errno=-16)
[   26.432018] ata4: link is slow to respond, please be patient (ready=0)
[   31.080009] ata4: COMRESET failed (errno=-16)
[   36.440009] ata4: link is slow to respond, please be patient (ready=0)
[   66.120008] ata4: COMRESET failed (errno=-16)
[   71.144006] ata4: COMRESET failed (errno=-16)
[   71.144064] ata4: reset failed, giving up
[   71.311055] sata_via 0000:00:0f.0: PCI INT B -> GSI 20 (level, low) -> IRQ 20
[   71.311094] sata_via 0000:00:0f.0: routed to hard irq line 5
[   71.311160] scsi5 : sata_via
[   71.311585] scsi6 : sata_via

$ uname -r
2.6.27-11-generic

```

I tried the latest **kernel 2.6.28.7** and no success.

This is a PCI SATA Controller card running on the **VIA VT6420 chipset**, attached to it is a Seagate Barracuda 200G - Model ST3200822AS.

Both the card and HD are working 100%, tested it under Windows and works flawlessly.

This is what I tried so far without success :

passing **"nodmraid all_generic_ide ide=nodma"** to the kernel at boot time.

Tried adding the **pata_via** and **pata_acpi** under the blacklisted modules, no go also, they keep loading at boot.

I always get BusyBox when booting with the HD attached to the PCI card, after **"ata4: reset failed, giving up"** I can boot calling **"exit"** under busybox.

From **[https://bugs.launchpad.net/debian/+source/linux/+bug/256637/comments/15](https://bugs.launchpad.net/debian/+source/linux/+bug/256637/comments/15)** post, a user was able to sort it out booting under **kernel 2.6.27-4-generic**, have anyone tried this already ?

This problem also appears when trying to boot the installation disk for Ubuntu 8.10.

Also when I boot I can't see or access the HD attached to PCI card.

---

### Post by Whitewater001 on 2009-03-12
wow. I feel like a new person after getting the workaround to go... spent 3 days trying every setting combo known to man to get this going... and here i am, working from boot from an all sata pc. yay.
Specs: amd5200+, Gigabyte GA590SLI S5, 2gig ram, x1950pro, 5 sata Hdds, one sata Dvd drive.

I had the same problems trying to install / use the live cd no matter what settings i had my sata/ ide to (i get three options: treat sata as ide, sata in achi mode, and treat sata + ide as raid (this third option wasnt the fix, but was the only one that allowed me to get it going in the end). 

To get the live cd going i pulled an old ide dvd burner from my old pc, that allowed me to run the live disk (if sata + ide was set to raid mode), but i couldnt install from the disk in this manner. BUT... this method of getting the live cd going worked one in 4 times... very very very frustrating... so you just need to try a few times from restarts and hard power offs... if that makes sense (am noob).

Once i got into the live cd thing, i managed to work out (after several tries) what disk my xp boot was on and where i was to install ubuntu... i had to watch out as my sata locations were changing every time i turned the pc on after modifying where things were plugged in or how the settings were (SCSI5 would become SCSI7 or SCSI11). I ran the install thing to a new drive, then hit ok to reset... No boot. same problem.

The system would get to the boot option screen, xp would be fine, but none of the ubuntu options were working, just got the SRST failed (er 16) thing. 

To fix, i added 'all_generic_ide floppy=off irqpoll' to the end of the boot option. i had no idea what i was doing and was desperate. 

But here i am, first thing i did in my new ubuntu install is come here and post about how helpful reading 20x pages of this thread was.

Cheers guys... made my week!



Specs that got it working: Raid mode (not sata = ide, or achi).
putting 'all_generic_ide floppy=off irqpoll' after the boot option thing.

Good luck to anyone else who tries, and thanks once again to those who worked this out.

---

### Post by Robo1 on 2009-03-23
:(I have a ATA, burned CD at 2x but same problems

---

### Post by vs8 on 2009-03-23
Jaunty seems to fix these problems. At least it works well on my laptop and it boots super fast. Intrepid has been a horrible experience for me in my two PCs.

Jaunty is not super stable, but for an alpha 6 stage it's very usable. Try using it and report your experiences.

---

### Post by salemboot on 2009-03-24
That somehow scares me.

Try version X to fix problem Y.:)

:KS

---

### Post by vs8 on 2009-03-24
It should not scare you. This problem seems to be a kernel bug or something. So a newer kernel means bug fixes, more drivers, support for many hardware etc. That's why I recommend using Jaunty to get past this problem. It worked on my laptop (Acer Aspire 5050-5410) and now it's working like a charm, it even boots as fast as a desktop pc, that wasn't possible with openSUSE or Fedora which never dropped me to the busybox screen but were extremely slow to boot, Ubuntu was worse because I had to type "exit" in the busybox screen in order to boot andthe whole process took the pc like 1 min 30secs.

Some times using older versions work too. Intrepid Ibex is unusable in my desktop pc but Hardy works perfectly. 

I've been testing Jaunty and it also works perfectly, even better than Hardy! Jaunty's final release will kick major ***, because alpha 6 freaking rocks!

---

### Post by vs8 on 2009-03-25
Hi guys, I think I found a solution to the BusyBox Screen of Death. I asked the guy to post it here but if he doesn't post it here I'll paste the link to the site I found it just in case.

[http://blogs.computerworld.com/a_newbie_turns_to_linux#comment-134491](http://blogs.computerworld.com/a_newbie_turns_to_linux#comment-134491) 

The title is: Ubuntu is looking for partition, not a disk

I don't have this problem any more since I'm using Jaunty but for those of you who want to use more stable versions of Ubuntu try it and report back.

---

### Post by ExampleDotCom on 2009-03-25
I had the initramfs problem booting the LiveUSB on eee and this fixed it:

On the menu screen, I pressed f6 to configure the kernel mode line and removed splash, quiet, persistent, and the one about using cdrom/usb.

Not sure which one fixed it, but it booted up fine after that.

---

### Post by salemboot on 2009-03-30
I have fixed one of my machines' problems.

DVD: Ubuntu 8.10

Booting the text installer yielded a inability to find a cdrom drive.  Although, it booted from the dvd.

The configuration of the hardware:

Ata0
Master : IDE Harddrive
Slave: NONE

Ata1
Master : NONE
Slave: IDE ATAPI DVD/RW drive

I switched the DVD-RW drive to master and the problems ceased.

I non-longer got the drop to the initramfs whatever...


So if your set up isn't normal you may experience problems.

My final problem is no keyboard.  This may be a bios setting but I was happy to finally get the thing to boot the livecd/dvd

later

---

### Post by linux_maya on 2009-04-04
Hi All,
I tried adding the PCI=nomsi and also IRQPOLL...but nothing seems to work. This was my first shot in my life ever installing the Ubuntu(or anyother distro's). Unfortunately it didnt go well with me. After reading ample of posts (from past 1day), I dont know what to do. All I get is a blank screen after the orange moves back and forth for a minute....
Thanks in advance!

---

### Post by jcm1107 on 2009-04-05
> **linux_maya said:**
> Hi All,
I tried adding the PCI=nomsi and also IRQPOLL...but nothing seems to work. This was my first shot in my life ever installing the Ubuntu(or anyother distro's). Unfortunately it didnt go well with me. After reading ample of posts (from past 1day), I dont know what to do. All I get is a blank screen after the orange moves back and forth for a minute....
Thanks in advance!

next time start a new thread instead of replying to an old one. But I had the same problem and I couldn't fix it with anything just as you mentioned, but then I found I COULD install 7.1 gutsy gibson after the install you can upgrade to Ubuntu 8.04 or 8.1 try downloading from here 

[http://releases.ubuntu.com/7.10/](http://releases.ubuntu.com/7.10/) 

install this and post back here with any problems or let us know if it works please!!

---

### Post by psychnaut on 2009-04-24
> **granny6989 said:**
> I can't imagine why this post is shown as SOLVED.,....,..

I have had the same problem mostly mentioned in this post and others since trying to install 8.10 (Ibex). 8.04(Hardy) has worked fine for me, as far as drives are concerned. Basic low down is this:

ASUS M2N-SLI board, AMD 64 with built in IDE and SATA controller.
2 IDE hard drives. 1 IDE CD drive. 1 SATA DVD drive.

When I use the live CD, or attempt an upgrade, etc.... to Ibex, i get:  ((xx.xxx) = misc numbers)


(xx.xxx) ata 5: COMRESET failed (errno=-16)
(xx.xxx) ata 5: COMRESET failed (errno=-16)
(xx.xxx) ata 5: COMRESET failed (errno=-16)
(xx.xxx) ata 5: COMRESET failed (errno=-16)
ata 5: reset failed, giving up
initramfs


This always happens after some little blurb about Busybox. I tried enabling the RAID option in BIOS for the SATA drive. No luck. For fun(?), last night I tried enabling RAID for all SATA drives, even though I have only one. Live CD finally booted up ok, got to the demo. Today I booted the CD, and installed. Seemed to go ok, so first thing I tried to enable Nvidia drivers. Machine tried to reboot, and then fell back to evil death loop of initramfs, etc, etc errors, blank screens, lockups, blank screens, etc, etc. login prompts... Finally hard booted and reloaded Hardy.

At this point, the RAID enabling option seems to be a faulty patch at best. It only worked for me after enabling several drives that didn't exist, and even then the system was unstable. After reading a lot of posts and pieces here and there, it looks to be an issue if you have mixed IDE/SATA setups. But that is only a guess on my part. I am going to keep Hardy until Ubuntu can prove that some fix has been made on this, Ibex so far will not work on my machine. I'd like to think that each version will get better, and perhaps it has in some respects, but this is ridiculous, if you expect a new user to grab a disk and install it, and then say 'well, you just have to go into BIOS and lie to your PC that it has RAID drives..'. It really is a bit much for a lot of people who just want to try something different or new. I don't know enough about programming and configuration to fix it or add anything else right now.

I am going to launchpad to post a bug to them in hopes of seeing some fix in the near future. Linux is still better than, well,...., you know.

S*



I'm having the same problem here where is the cure in this form?

---

### Post by DaveAU on 2009-04-25
I believe this bug report (open since dapper) is relevant:
  [https://bugs.launchpad.net/ubuntu/+source/initramfs-tools/+bug/47768](https://bugs.launchpad.net/ubuntu/+source/initramfs-tools/+bug/47768)

It was pretty dormant until last month when someone assigned it to the canonical kernel team and marked it critical.  Looking at this thread I don't know how many people would have just walked away from Ubuntu in the meantime, so I'm glad it's become a priority.

So let them know what fails and what fixes don't work and hopefully before too long this problem will finally be put to rest.

---

### Post by starfry on 2009-04-26
Hello, I thought I'd add my findings here for the benefit of others rather than the hope of a solution (if 39 pages of posts don't convince Canonical there is a problem then I don't know what will ;))

I have just taken delivery of a core i7 machine based on the ASUS P6T-Deluxe motherboard. It only has SATA devices connected.

I can successfully install Jaunty from the alternate CD without issue. However, I have dependencies (OpenVZ) that require Hardy.

I can not get the Hardy alternate CD to work beyond detecting the CD-ROM (no common cd-rom drive found). Adding all_generic_ide made no difference.

However, I have successfully installed the from Hardy Desktop CD by using the all_generic_ide (it did not work without it). I had to make no changes to Grub - it booted successfully first time.

My BIOS is set to IDE mode. I had even less success with AHCI mode.

So, not all CDs are created equal: for me the desktop CD worked but the internal CD did not.

I really would prefer to use the alternate CD because I want to build upwards from a clean "command line system" with only the components I need - so I am still very interested in a solution to this problem :)

---

### Post by velja27 on 2009-04-26
I managed to fix my busybox problem by installing an CD/DVD-ROM from LiteOn and its very noisy but gets the job done.Its plugged in same place as my other CD/DVD-ROM but does the magic i want it to do.
Just so you know.

---

### Post by Infoteksec on 2009-05-13
Hmmm - if the problem is fixed i'd like to know where to find the fixed version.

I downloaded the USB image of Ubuntu+netbook remix, copied it to a 2Gb stick using Win32DiskImager and booted it on my AAO.

I'm stuck at the (initramfs) prompt too. I would of have thought an AAO would have been one of the first machines the image was tried on - not, apparently, the last.

Since I'm fresh out of RAID support on my AAO what have others tinkered with to make this work?

Peter

---

### Post by Chiapo on 2009-05-15
I have an Acer Aspire One ZG5 with Windows XP installed from the factory.
I really want to get online using Ubuntu, but have had no luck getting the Ubuntu Network Manager to recognize the 3G modem.
I've installed UNR 9.04 (beta) alongside WinXP.
I downloaded UNR daily build (karmic koala) last night, used Ubuntu ImageWriter to install the IMG to my bootable USB flash drive.
I tried to boot from the USB, and got as far as the busybox + initramfs prompt.
What now?
I was hoping that the latest daily build would fix my connectivity issue.
Thank you.

---

### Post by dbatero on 2009-06-05
Great it works well to me. Thanks!

---

### Post by ctimko on 2009-06-10
I am having this problem with 9.04. This was working with 8.10 until I updated. Tried alot of things posted in here and so far nothing is working. Thoughts other than going back to 8.10?

---

### Post by johnnyg2008 on 2009-06-10
Backport from r23074 from upstream to fix; go to:
launchpad.net/ubuntu/jaunty/+source/busybox/1:1.10.2-2ubuntu7
I encountered this bug upgrading my desktop from 8.10 > 9.04 and it's at the initramfs line,
could I download these fixes directly to its HDD using the commandline?

---

### Post by mark bower on 2009-09-09
My hat is off to velja27, post #388 in this series which pointed to the CD reader as the problem.

I have two internal CD units:  Memorex DVD multi-recorder with lightscribe and Memorex CD recorder 52x24x52.  XP installed using the DVD unit, but ubuntu 9.04 (CD from shipit.ubuntu.com) would not install and gave the cited Busy Box (initramfs) error message.  

I switched the IDE cable to the CD 52x24x52 and 9.04 installed with no problem.  I repeated the process of trying to install by switching the cable between the two units and verified the install problem relates to the hardware used for the installation.

However, since XP installs on either the DVD or CD unit, this shows a weakness in the 9.04 CD. Developers please take notice of this.

---

### Post by ovu on 2009-09-24
hi 
i ve got a the same problem,
ive got a 120 gb sata drive connected to my laptop with 64bit vista installed, i also have a 500gb usb external hard drive. i have a fat32 partition on the external drive and have left 20 gb of free space unformatted on this drive.

i have installed 64bit ubuntu on the free 20gb on the usb hard drive
/dev/sdb5
and i noticed that the boot loader was installed on hd0.

o.k the funny thing is when i boot my system up i only get grub if i have the usb cable connected otherwise i get a "grub 27" error

my major source of frustacion is when i choose to boot ubuntu 9.04. the splash screen with orange bar moving left to right appers but after 30 seconds or so i get an initramfs and busybox. as shown in the pic below



[IMG]http://i35.tinypic.com/30jp8c0.jpg[/IMG]

i really hope some one can help me resolve this problem as i really need ubuntu!!!!!

---

### Post by ovu on 2009-09-24
ooohhh

i think the problem may be because ubantu is trying to boot from (hd1,4) as shown in the top left of the screenshot/photo sorry about the mega proportions.
but i think it shoud be looking in (sdb,5) that would fix my problem

can some one direct me on how to accomplish this,


n.b i think this is why some peoples systems wont boot untill the bios is set to raid!!!!! 
(my primary drive is numbered hd0 and the usb/ubantu device is called sdb)

---

### Post by Lukios on 2009-09-25
My problem was my ide cable was bad

---

### Post by kannedheat on 2009-10-07
Hi all!

I also am having trouble with initramfs and busybox.  I haven't been able to get on Kubuntu 9.04 through GUI for about two weeks.  I am able to exit initramfs to go to boot, but my GUI display dosen't get displayed leaving me with only a terminal access.  This is very frustrating.

---

### Post by FranklinSt on 2009-10-27
I've had this issue since 8.04. I've tried lots of other distros like Mandriva, Suse, Knoppix and Redhat. ALL HAVE THE SAME ISSUE. It's a kernel problem that's been going on for years now and nobody has addressed it.

Like a previous poster said, how many people have walked away from Linux because of this??????

---

### Post by jenaniston on 2010-02-09
> **kannedheat said:**
> Hi all!
 
 I also am having trouble with initramfs and busybox. I haven't been able to get on Kubuntu 9.04 through GUI for about two weeks. I am able to exit initramfs to go to boot, but my GUI display dosen't get displayed leaving me with only a terminal access. This is very frustrating.
 
> **FranklinSt said:**
> I've had this issue since 8.04. I've tried lots of other distros like Mandriva, Suse, Knoppix and Redhat. ALL HAVE THE SAME ISSUE. It's a kernel problem that's been going on for years now and nobody has addressed it.
  
  Like a previous poster said, how many people have walked away from Linux because of this??????
  
I accept the below as true (from post **#291** page **30**) . . .

> **bertolo said:**
> hi all. in my university this bug is the number one bug of them all.
it got nothing to do about the system just about the disc. i switched computer with the same hd and i got the same problem.

**IMPORTANT NOTE: THE PROBLEM IS IN THE HD**

While I am still working and wondering what can be done with this SATA hard drive /dev/sda to 
get***  any*** live version of Fedora or Debian linux to boot . . .
at least this Live Xubuntu 9.10 x86_64 on a USB has worked the best of all - and gets me this far on a sick laptop  . . .

```
(initramfs) help
```with this I can get a list of commands available with (initramfs) prompt  . . . like pwd, ifconfig, uname, and some other commands for now . . .

and*** now*** I'll try this  (from post **#302 & 305 **page **31**) . . .
> **andre805 said:**
> I deleted the word splash after pressing 'F6'. All I got after doing so was "Loading, Please Wait..." then it went back to the busybox prompt.
> **BlackCat13 said:**
> Taking out splash will simply remove the splash screen... taking out quiet will allow you to see the verbose print out of what is happening... won't fix any problem but will tell you where the problem is... because the system will show you where it is hanging before dropping to busybox... :)

---

### Post by Lamonster on 2010-04-21
Okay guys, what are your thoughts?  I am totally new to Linux/Ubuntu and a BSOD on my Dell Vista computer is what brought me to trying Ubuntu so I can save the data on my C: drive before reinstalling Windows.
 
How can I successfully boot Ubuntu when every time I try **Install Ubuntu** or **Try Ubuntu without any change to your computer,** I'm getting this Busybox stuff every time:

 
[IMG]http://farm5.static.flickr.com/4007/4542448696_ec543b6876.jpg[/IMG]

---

### Post by 2hot6ft2 on 2010-04-21
So have you done what it tells you to do?
Run
```
chkdsk /f
```
on windows
and reboot windows twice
and shut windows down properly.

And welcome to the forum

---

### Post by Lamonster on 2010-04-21
> **2hot6ft2 said:**
> So have you done what it tells you to do?
Run
```
chksdk /f
```
on windows
and reboot windows twice
and shut windows down properly.
 
And welcome to the forum
I can try running that in the command prompt but can't shut down properly because Windows won't even load, getting the black screen with a mouse pointer and nothing else.

---

### Post by 2hot6ft2 on 2010-04-21
> **Lamonster said:**
> I can try running that in the command prompt but can't shut down properly because Windows won't even load, getting the black screen with a mouse pointer and nothing else.
It's a windows command and it's
```
chkdsk /f
```
I had a typo.
What version of windows? xp, vista, 7

---

### Post by 2hot6ft2 on 2010-04-21
you can download a free recovery cd here for windows that may fix your windows booting problem.
[http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/](http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/)

Burn the cd and boot up with it in the cd drive and and try to repair windows.

Once you get it to boot go to Start > Run
and run the command.

From memory  I think it was
Or open My Computer and right click on C: drive > Properties > Tools > check disk for errors with the fix option checked.

Or right click on My Computer > Manage > Disk Management > select the windows partition. Right click and select check for errors.

It will have to be restarted to actually run chkdsk.
Then you can get your stuff off of it and re-install it.

---

### Post by Lamonster on 2010-04-21
> **2hot6ft2 said:**
> It's a windows command and it's
```
chkdsk /f
```
I had a typo.
What version of windows? xp, vista, 7
Vista.  So I ran chkdsk /f and restarted twice and finally shut down using the shutdown command in the command prompt.
Still, I try to start Ubuntu and it goes into the loading symbol, followed by a blank black screen, then I press Spacebar and see the same BusyBox text as before.
 
> **2hot6ft2 said:**
> you can download a free recovery cd here for windows that may fix your windows booting problem.
[http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/](http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/)
 
Burn the cd and boot up with it in the cd drive and and try to repair windows.
 
Once you get it to boot go to Start > Run
and run the command.
 
From memory I think it was
Or open My Computer and right click on C: drive > Properties > Tools > check disk for errors with the fix option checked.
 
Or right click on My Computer > Manage > Disk Management > select the windows partition. Right click and select check for errors.
 
It will have to be restarted to actually run chkdsk.
Then you can get your stuff off of it and re-install it.
Thank you, it is downloading now.  I'm also downloading Ubuntu v7.10 because I heard there were issues with the later versions and DELL computers.

---

### Post by Lamonster on 2010-04-22
Vista recovery disc didn't work.  The only thing left to try is Ubuntu 7.10 but I am not confident it will be any different.  Any more ideas or suggestions?

---

### Post by Chame_Wizard on 2010-04-26
> **Lamonster said:**
> Vista recovery disc didn't work.  The only thing left to try is Ubuntu 7.10 but I am not confident it will be any different.  Any more ideas or suggestions?

7.10?That's not supported since last year.

Download Karmic koala and create a Live USB.


Can someone tell me why I getting emask errors on a IDE HDD when using the CLI? :(

---

### Post by RamseyT on 2010-06-18
The saga continues.

I need to run EMC2 and I believe this is the only Ubuntu version available for it.

Toshiba 225cds Laptop intel P133, 32768KB installed memory, 1.4G HDD,
No floppy
No SATA/RAID options just "Enhanced IDE (Normal)" and "Standard IDE"
Booting from the CD
Burned CD "ubuntu-8.04-desktop-emc2-aj13-i386.iso"
Selected "English"
Selected "Install Ubuntu"
F4 selected "Normal"
Tried all of the boot line suggestions in the preceding 41 pages.
Screen with "Quiet" removed.

All help will be appreciated

{edit}
I typed "Exit" and got this second screen shot...
If I remove the CD it still boots fine back to Windows.

Before arriving at the "iinitramfs" prompt and with Quiet off, the Ubuntu splash screen shows and several items in orange text get an "OK" alongside.

The third item on this growing list is "Mounting Root File System" but it does not get an "OK"
The fourth item is "mounting scripts/casper" and it gets an "OK".

"The Mounting Root File System" not getting an OK, may explain why the second screen shot mention the missing root drive system.
{/edit}

Ramsey

---

### Post by robrg1836 on 2011-09-03
This was very informative.  Great thread...

---

### Post by ionplay on 2012-02-06
> **azurehi said:**
> Thank you Jong!  I was able to install HH 8.04 from the Live CD.  From Live CD, Install, F6 I entered:

all_generic_ide floppy=off irqpoll  

and the image booted from cd-rom to desktop and the installation proceeded without apparent problem.  I tried all the other suggestions, without success and this did the job.

did everyone move on already???

I have some legacy machines locked into 8.0.4 LTS at the moment
and did a fresh install on new hardware
Hardy Heron has been very stable for us since 2006, and I fully intend to upgrade everything in my network to 10.0.4 or maybe 12.0.4 at the rate I am going

question is - I have new OCZ SSD drives 
at first I was not able to install HH, then I used the "all_generic_ide floppy=off irqpoll" on the install

that went fine - and everything installed

but now when I boot HH - it just reverts back to initramfs prompt again


did I just pick a dead thread???
yes I am going to upgrade - but still have to deal with legacy software that runs great on HH 8.0.4

---

### Post by ionplay on 2012-02-06
> **tristar said:**
> OK !!!!! Another new Update..... Tried installing 8.04 in 4GB Flash Drive no go... Initramfs...

WTF.... So again tried installing it in IDE drive with an external converter for USB again it SPAT the INITRAMFS Error on my face....

But installs like a charm on the IDE drive directly connected...
 
The 8.XX Series seem to mess up when being installed in any other type of drive apart from the IDE drive....

HOPE THIS HELPS !!!! And rings a bell to someone who can fix it !!!!!

**[COLOR="Red"]booksbuggy : Please read the above posts the installation fails even on a Flash Drive Appreciate you trying but it's not helping us......[/COLOR]**

SATA drives were working
trying to find example of someone using SSD harddrive - 10.0.4 works great on SSD's
but not HH 8.0.4 - anyone have a quickfix????

---

### Post by ionplay on 2012-02-06
my HH 8.0.4 was booting straight to initramfs after a fresh install

I had to use the F6 boot option to get the install done
added 
all_generic_ide floppy=off irqpoll

problem is the new SSD drive

once installed it would still boot to initramfs - thought after the install everything would be wonderful

had to edit the /boot/grub/menu.1st and manually add the boot option there

now everything is peachy

---

