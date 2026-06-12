---
title: "Dapper can't mount CD"
date: 2006-06-02
forum: Installation &amp; Upgrades
---

### Post by seshomaru samma on 2006-06-02
(sorry I posted this in the general support section first,before I realised this section existed...)
I want to upgrade from breezy to dapper
I booted from the dapper CD, at first everything seemed fine
but after i put in my keyboard setting a notice appeared saying that ubuntu can't mount the CD and that perhaps the CD isn't there which is very strange because I was booting from that very CD...
I tried to mount it several times but failed so I cannot proceed with the installation...
Please help...

---

### Post by pellgarlic on 2006-06-07
you will need to provide more information before anyone can help - 

are you using the "final release" version of dapper, or a "release candidate"?

what kind of cd drive is it? (e.g: ide, scsi, usb?)

have you checked the md5 sum of the iso you downloaded to burn the cd, to make sure it has not been a flawed download?

can you quote the _exact_ error mesage you receive?

---

### Post by halfstep on 2006-06-20
I'm also having this problem.  I'm using an IDE DVR drive, and I've also tried it on my dvd rom drive.  Both times behaves as in the previous post.  It boots from the cd, asks for language and keyboard settings, then says it can't mount/find the disc.  

My system is relatively new, so I would assume my config would be supported, but just in case:
Asus Motherboard P5AD2-E
Intel Pentium 4 3.2Ghz
2 IDE 280 Gb Hard Drives (I'm planning on installing to the 2nd)
1 ASUS DRW-160BP
1 ASUS DVD-E616P3
4gb ram

I am using the final release of Drake, 6.0.6, i just downloaded it and burned it last night.  I also tried a 5.10 version that I had on disc from a text book, but that also errored in the same manner.

And yes I did check the md5sum, so I don't think the disc is the problem.

Thanks!

---

### Post by rcarring on 2006-06-20
Thinking laterally, can Dapper Drake support 4GB of Ram?

I think the problem you are having is due to the fact you have two cd/dvd drives attached to your system and Dapper may not be able to figure out which one it is running on. If you only have one cd/dvd drive then I am not sure what to suggest.

---

### Post by halfstep on 2006-06-20
So you suggest unplugging one of the cd drives and seeing what happens?  I'll try it when I get home tonight, but that seems kind of odd that Dapper wouldn't support systems with 2 drives.

---

### Post by pellgarlic on 2006-06-20
rcarring's suggestion sounds the best way to go.

[QUOTE=halfstep]that seems kind of odd that Dapper wouldn't support systems with 2 drives.[/QUOTE]

perhaps you'll only need to do this for the installation procedure - the "live cd" works differently than the actual installed version of dapper will. if it works, and you get dapper installed, you may have to manually edit your fstab file to include your second dvd drive.

[QUOTE=rcarring]Thinking laterally, can Dapper Drake support 4GB of Ram?[/QUOTE]

as far as i know, the default kernel has the HIMEM option enabled, so it should work with up to 4gb of RAM fine. any more than that, and i think you have to specify a different HIMEM option or something.

[Edit: couldn't find my source of information for the above claim, but found this: [https://launchpad.net/distros/ubuntu/+source/linux-source-2.6.15/+bug/8574](https://launchpad.net/distros/ubuntu/+source/linux-source-2.6.15/+bug/8574) which ends with statement that HIMEM support is included in breezy. HIMEM is required for anything over about 900mb of ram, so i'm guessing it's highly likely it is "on" by default in dapper]

---

### Post by halfstep on 2006-06-20
Well I tried it, and ran into the same error.  I copied the error that was on the screen:
hdb: cdrom_pc_intr: The drive appears confused (ireason = 0x01)(this is displayed about 50 times)
irq 185: nobody cared (try booting with the “irqpoll” option
handlers: [<c0252040>](id_intr+0x0/0x200)
[<f891b330>] )usb_hcd_irq+0x0/0x60[usbcore])
Disabling IRQ #185

It keeps cycling through that.  Its kind of Odd though that it says hdb:  I have 2 hard drives, so shouldnt Hd1 be hda and hd2 be hdb leaving c and d for the cd drives?

---

### Post by CaptainHowdy on 2006-06-21
[QUOTE=halfstep]Well I tried it, and ran into the same error.  I copied the error that was on the screen:
hdb: cdrom_pc_intr: The drive appears confused (ireason = 0x01)(this is displayed about 50 times)
irq 185: nobody cared (try booting with the “irqpoll” option
handlers: [<c0252040>](id_intr+0x0/0x200)
[<f891b330>] )usb_hcd_irq+0x0/0x60[usbcore])
Disabling IRQ #185

It keeps cycling through that.  Its kind of Odd though that it says hdb:  I have 2 hard drives, so shouldnt Hd1 be hda and hd2 be hdb leaving c and d for the cd drives?[/QUOTE]


Well yes, i have the same problem and i have it with other linux distributions as well, and i havent found the solution to the problem.. I disconnect drives but it still seems to have the same problem!

---

### Post by pellgarlic on 2006-06-21
[QUOTE=halfstep]Well I tried it, and ran into the same error.  I copied the error that was on the screen:
hdb: cdrom_pc_intr: The drive appears confused (ireason = 0x01)(this is displayed about 50 times)
irq 185: nobody cared **(try booting with the “irqpoll” option**
handlers: [<c0252040>](id_intr+0x0/0x200)
[<f891b330>] )usb_hcd_irq+0x0/0x60[usbcore])
Disabling IRQ #185[/QUOTE]

read that bold part - perhaps that hints at a solution? i'm pretty sure there is no option to add "irqpoll" when booting from the "live/install" cd, but perhaps there is with the "alternate" cd - you could try downloading the iso for that (from the same place as you got the "live/install" iso).

when booting from it, you should be able to enter "command-line" options - try typing "linux irqpoll" or something (not sure of the correct syntax - hints should be provided if i remember correctly). although, the only documentation i can find regarding "irqpoll" is for adding it to grub's menu.lst, so i don't know if it will work...

it seems, from what i've been reading, that the problem stems from the way the kernel handles IRQs, and certain combinations of IDE controllers and dvd drives  - which means if the irqpoll thing doesn't work it's probably gonna be quite hard to sort this :( 

perhaps you could borrow a different model of cd/dvd drive, and switch it with your own drive, in order to perform the installation, then add the "irqpoll" option to the menu.lst (it goes at the end of the "kernel /boot/vmlinuz-2.6.15...... root=/dev/...." line), and then reinstall your own dvd drive?

---

### Post by halfstep on 2006-06-21
The irqpoll seems to fix the cdrom issue, or at least get me further.  It read the cd, and then asked me to name the computer on th network and succesfully configured all that.  Then I got a message saying its detecting my hard discs.  It hangs there for a really long time.  If i hit ctrl-c, it brings up a partitioning menu, but as soon as I it any option it goes back to the hanging screen.  If i push ctrl-c it goes to the partition menu again.  Any ideas here?

Thanks

---

### Post by pellgarlic on 2006-06-22
ok, try this:

linux irqpoll ide=nodma

---

### Post by CaptainHowdy on 2006-06-23
Does anybody know the source of this problem???  ](*,) 

Is it possible that the installation of the disks (master - secondary) setup
confuses the setup???

---

### Post by CaptainHowdy on 2006-06-23
[QUOTE=rcarring]Thinking laterally, can Dapper Drake support 4GB of Ram?

I think the problem you are having is due to the fact you have two cd/dvd drives attached to your system and Dapper may not be able to figure out which one it is running on. If you only have one cd/dvd drive then I am not sure what to suggest.[/QUOTE]


Well i have almost the same configuration and i disconnected the one cdrom
drive but i still had the same problem...

I ll try the irqpoll ide=nodma option and i will let you know..

---

### Post by pellgarlic on 2006-06-23
[QUOTE=CaptainHowdy]Does anybody know the source of this problem??? [/QUOTE]

i'm not 100% sure, but it seems to have something to do with the specific ide controller on your motherboard, and the way that linux communicates with it, either that or the actual cd/dvd drive itself. but if the problems seem to extend to the hard drive(s) as well, the ide controller is the more likely culprit. some people have this problem, but most don't.

---

### Post by CaptainHowdy on 2006-06-24
Probably, i dont know, maybe my MoBo has the problem..

Anyway the 'linux irqpoll ide=nodma' option does not work.. It halts the 
whole system (CTRL+ALT+DEL doesnot work) when it get to the point
of installing the base system (up to there i have no problems).. It always
halts at 6%.

---

### Post by halfstep on 2006-06-24
That didn't change anything.  I also tried the options noapic and nolapic.  Any other ideas?

---

### Post by an-thome on 2006-06-25
Hi!

I have the same problem, and I have the very same motherboard as you.

I havent tested any other distros on this motherboard... Have you? and if so... did you get the same problem?

I'm gonna try searching for a general linux solution for this one... (Google :-))

Regards
Anders

---

### Post by pellgarlic on 2006-06-26
those of you having this problem could try the "knoppix" live cd - it's reputed to have excellent harware detection. if it works with that cd, you can be optimistic about finding a solution. if not, i would be sceptical about getting it to work. to be honest though, this seems beyond my knowledge and capabilities. sorry, don't think i have any more help for you. :( maybe someone else with more experince and knowledge will pick this up...

---

### Post by CaptainHowdy on 2006-06-26
Well i guess i should try to change my MoBo since it's a little bit old
Thanx anyway!

---

### Post by pellgarlic on 2006-06-26
it might be worthwhile trying a different cd/dvd drive first - it seems to be the combination of motherboard and optical drive that does it, and a new drive would be cheaper and a lot less hassle to replace than the motherboard...

maybe you have a friend who can load you one to try it out? (if it's a different make from your current one).

if you do go the "new mobo" route, i would first check the compatibility - i think there are some chipsets that are happier with linux than others. i seem to recall something about via chipsets being in the latter group, although i could be wrong.

---

### Post by CaptainHowdy on 2006-06-26
Well i always wanted to change my mobo since it has low
capabilities and now its a good chance to do so..

I ll see to it and i ll let u know.

---

### Post by danpos on 2006-06-27
@ALL

Hi there! First time in this forum. I've got the same issue than others 'Dapper's users: I've got 2 IDE DVD-Recorders (1 Samsung DVD+-RW / 1 LG DVDRAM) and this time I did install from LiveCD. Follows what I got with 'dmesg | tail':

> [17182117.560000] end_request: I/O error, dev hdd, sector 64
[17182117.560000] Buffer I/O error on device hdd, logical block 8
[17182118.304000] hdd: tray open
[17182118.304000] end_request: I/O error, dev hdd, sector 64
[17182118.304000] Buffer I/O error on device hdd, logical block 8
[17182787.428000] hdd: command error: status=0x7f { DriveReady DeviceFault SeekC omplete DataRequest CorrectedError Index Error }
[17182787.428000] hdd: command error: error=0x7f { IllegalLengthIndication EndOf Media AbortedCommand MediaChangeRequested LastFailedSense=0x07 }
[17182787.428000] ide: failed opcode was: unknown
[17182787.428000] end_request: I/O error, dev hdd, sector 64
[17182787.428000] isofs_fill_super: bread failed, dev=hdd, iso_blknum=16, block= 16

So must I've to compile a customized kernel or so what? I don't do this for ages, since early versions of Debian and already missing something about this ... 

Any advises?

Regards,

---

### Post by pellgarlic on 2006-06-28
seems like it's a problem with your second (slave) dvd drive. are you able to use it? (i.e. - can you read discs, copy from discs, write discs etc.)

it may be that the drive is faulty - can you check it another computer? you could also make sure that the drive is detected in the bios properly.

could you also post the contents of your /etc/fstab file?

---

### Post by halfstep on 2006-06-30
You are right its not the CD drives themselves, its got to be the MOBO's IDE controller.  When I installed Windows for the first time I had to use the drivers from a disc because windows didn't immediately recognize the controller.  Is there something similar I can do in this case?  Because obviously Ubuntu...or any linux for that matter doesn't like it.  Strange thing though, I used to be able to install an old version of Ubuntu.  Did they drop some driver support?  My mobo isn't old, its only a year old.  And I would think ASUS would be well supported.  Any Ideas?

---

### Post by kwicky21 on 2006-07-06
I'm having the same problem, couldn't mount the CD-ROM and check if it's in the drive. But the thing is, I've installed Ubuntu 6.06 LTS using this same CD on another computer and it worked fine. I've also installed Ubuntu Dapper Flight 7 on this machine that it isn't installing now. So maybe the problem is with the final release of Dapper?

:(

---

### Post by madmanwashere on 2006-07-11
OK, I am having the same problem, IRQ 185 issues, I have an asus p4c mobo and some other interesting things (host adapters and whatnot) and I'm trying to get Debian 'testing' to install.  I read this forum and it gave me some ideas and lo and behold I got this to install, but... :-k could just be luck :p 
I've spent a couple days trying to get this to work, now that I finally got it to install, here's what I did.  the command line:
**linux noapic irqpoll isapnp_reserve_irq=18**
breakdown: linux is the kernel to boot for Debian install, irqpoll definately helps the system find the CD again after booting from it , noapic to disable buggy apic, and finally I did boot the system with a knoppix live cd and noticed it had the same errors... and it disabled irq 18 and continued to boot, so looking through command line linux boot params, I found isapnp_reserve_irq=18 and this seems to have made the installer ignore irq 18. Final "workaround" if all of that gets you to where the system is installing and freezes at 6%, i noticed it was doing some stuff but not increasing the % counter so I switched to terminal 2 ( <alt>+F2 ) and looked at what processes were doing what ( ps ) and while I was on this screen it didn't get stuck, it continued to install :D , so i don't know if that last part is neede or not but after two days of trying to get linux to install ( Debian, ubuntu, gentoo ) I now want to get working on it. and now that it boots, the real fun starts!

---

