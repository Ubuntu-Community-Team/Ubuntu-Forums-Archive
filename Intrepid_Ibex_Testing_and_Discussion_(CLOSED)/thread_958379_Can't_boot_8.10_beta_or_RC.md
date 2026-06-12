---
title: "Can't boot 8.10 beta or RC"
date: 2008-10-25
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by showson1 on 2008-10-25
Hi all,
I tried 8.10 beta about a week or so ago and it wouldn't boot on my laptop.

It won't boot of the live CD and if I install it (through Windows) it won't load on reboot.

It shows the Ubuntu logo with the progress bar and almost immediately freezes.
The progress bar stops moving and there's nothing.

If I press keys on the keyboard the progress bar starts moving, but it never loads.

So far i've tried the i386 Beta version, i386 RC Desktop, amd64 RC Desktop and I'm about to try Alternate.. but would be willing to bet it won't work.

Any suggestions?

The laptop is a Compaq Presario f763nr.

Thanks.

---

### Post by mikewhatever on 2008-10-25
Post your computer specs - RAM, CPU, graphics.

---

### Post by cantormath on 2008-10-25
[SIZE=2]while booting, press alt+f2 and see what happens during boot.......

There is probably something you can add to the kernel boot param when booting up that will allow the disk to work.

for example, I had the issue below and use this fix to resolve it with hardy:

[/SIZE]                    [SIZE=2]_**The Issue**_
Live CD hangs when booting for install.  
[/SIZE][SIZE=2] Error when boot disk:
[/SIZE] [SIZE=2]busybox v1.1.3(debian 1:1.1.3-5ubuntu12) built in shell (ash)

_**Fix**_
[/SIZE]   [SIZE=2]Put CD in
boot to install menu
press F6
replace "[/SIZE][SIZE=2][I]splash quiet --"
[/I]with[/SIZE][SIZE=2]all_generic_ide pci=routeirq

**Note**: you may only need to replace [/SIZE][SIZE=2]"[/SIZE][SIZE=2]*splash quiet --" with *[/SIZE][SIZE=2]all_generic_ide
[/SIZE] [SIZE=2]
hit enter

After install:
you need to set "all_generic_ide" in your kernel parameter one more time on first boot after you install.

press esc 
press e
go down one row, press e, you are going to edit the kernel boot parameter...
[/SIZE][SIZE=2]replace "[/SIZE][SIZE=2]*splash quiet --" with *[/SIZE][SIZE=2]all_generic_ide, no quotes. 
press enter
press b

computer should boot up.

after boot up, go into /boot/grub/menu.lst and change the kernel boot option the same way.  Each time the updates include a kernel update, you will need to do this cause dell is a pain in th ***.

the end....[/SIZE]

---

### Post by showson1 on 2008-10-25
Thanks a lot for the info.
I tried the suggestions but it still locks.

There's really no error as far as I can see.
It stops when it's detecting the USB ports:

[3.612431] hub 4-0:1.0: 2 ports detected.

If I hit a key at this point it moves on, then stops at:

sense key: medium error
Unrecovered Read error
end_request: I/O error, dev sr0, sector 1429200
Buffer I/O error on device sr0, logical block 178650
[sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK

I've tried different disks, thinking it was a bad CD, but no dice.


Thanks for any suggestions!

---

### Post by NiklasV on 2008-10-25
Have you tried verifying the CD?
Even if there's nothing wrong with the CD, there could be a problem with your CD-drive..

Also, when you burn the CD, make sure you do so at the lowest available speed.

---

### Post by Robertjm on 2008-10-25
Were you using the SAME download when you tried the different pieces of media? If so, try downloading a new .iso file. I had a problem with a distro once and it turned out that my downloaded was funky. After redownloading it, it worked fine.

> **showson1 said:**
> Thanks a lot for the info.
....
I've tried different disks, thinking it was a bad CD, but no dice.
....

---

### Post by showson1 on 2008-10-25
Thanks all,
I've tried different media with different downloads.
I've tried the i386 and AMD64 desktop isos as well as the AMD64 Alternate.
I've never had a problem with any disks (CD or DVD) on this machine before and I'm able to load 8.04 just fine on there.

Even when I installed it through Windows and tried to boot into Ubuntu I get the same results.

Is there maybe an issue with the SATA drivers in this distribution or something?

I'll try burning again at lowest speed and see what happens..

---

### Post by showson1 on 2008-10-25
I think the error is related to the hard drive, before that last error message I can hear it hitting the drive.

I've run a diagnostic on the drive and it comes up clean..

---

### Post by showson1 on 2008-10-25
Ok, I downloaded again, burned on another machine with different media and still got same issues.

Thanks for the help all, but I'm going back to my Mac.

This is the exact type of thing that made me move away from Linux, it's just not ready for prime time yet and I don't want to waste hours trying to get it to work like I have in the past.

Thanks again to all for the help!

---

### Post by josedb on 2008-10-25
i have the same problem, even after installing the OS, when loading or shutting off i have to have a key pressed so the system can load correctly.


HP dv6736nr 
Turion 64 tl60
2gb ram DDR2
250gb sata hard drive
dvd Rw
Richo Card reader
nvidia 7150


All hardware works perfectly, even the wifi card (with madwifi compiled)

---

### Post by Naddiseo on 2008-10-25
> **showson1 said:**
> 
This is the exact type of thing that made me move away from Linux, it's just not ready for prime time yet and I don't want to waste hours trying to get it to work like I have in the past.



Perhaps you shouldn't be trying beta/RC releases, and should wait for the final release?

---

### Post by jerrylamos on 2008-10-25
> **Naddiseo said:**
> Perhaps you shouldn't be trying beta/RC releases, and should wait for the final release?

If all of us who have trouble wait for the final release, the final release will be full of bugs.

I've been battling "won't boot" since August 12 on my IBM Thinkpad R31 laptop.  Following hints from comments on the Intrepid forum, I chased it down to compiz.  Compiz plays "fancy tricks" to get "eye candy"  (my words) which don't work with some combinations of graphics hardware & drivers.

My workaround, see Launchpad bug 27344, is:
boot in recovery mode
at the selection pop-up: 
select root prompt
sudo apt-get remove compiz
sudo apt-get remove compiz-core
exit 
resume normal boot

Another workaround is to use Xubuntu, which uses Xfce desktop instead of the buggy Gnome/compiz desktop, or if Xfce is a bit plain use Kubuntu which has the fanciest "eye candy" and doesn't seem to use compiz, or at least not the way Gnome does.

The ONLY reason the Alpha's and Beta's and Release Candidate are put out is to test the water to see if people are running O.K. and if not work on some fixes before it is too late.

In any case always try CD Live before upgrading.  If CD Live doesn't work, install won't.  And yes compiz can be removed from CD Live by watching for X windows to start, Ctrl-Alt-F1, sudo apt-get remove compiz, sudo apt-get remove compiz-core, Ctrl Alt F7.

Jerry

---

### Post by Naddiseo on 2008-10-25
> If all of us who have trouble wait for the final release, the final release will be full of bugs.

That's not what I was suggesting. I'm saying that you shouldn't be complaining that linux/ubuntu isn't ready if you are using an unfinished product. I've been trying to get RC working all morning, but the liveCD/USB dumps me to busybox. Of course it's not ready for "prime-time" but I'm not complaining about it because I know it'll get fixed.

---

### Post by showson1 on 2008-10-25
> **Naddiseo said:**
> I'm saying that you shouldn't be complaining that linux/ubuntu isn't ready if you are using an unfinished product.

It seems you missed my point and it's interesting you interpreted my statement as a complaint.

I was saying Linux in general wasn't ready for prime time because of problems similar to this, not specifically this version of Ubuntu.

I'm not putting down Linux, it's a fantastic OS, but for me I don't have the time to put in to getting it to work on my machines for a desktop OS.

For a server, which I do use it for, it rocks though! :)

---

