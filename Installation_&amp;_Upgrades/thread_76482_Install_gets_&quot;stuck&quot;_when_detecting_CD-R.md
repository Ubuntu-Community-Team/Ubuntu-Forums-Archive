---
title: "Install gets &quot;stuck&quot; when detecting CD-ROM"
date: 2005-10-15
forum: Installation &amp; Upgrades
---

### Post by phend-one on 2005-10-15
Fustration cannot even begin to describe what I'm experiencing.

Before I begin, please don't ask me to check the md5 sums or redownload the image or change my cd-rom or whatever. I've done it all. Burned at numerous speeds. slower/faster.

Everytime I pop the 5.10 install cd in, it goes to start setup, but it doesn't go through the nice bootsplash logo way. It goes through the all text based "ISOLINUX" way. Fine.

Choose Language, Locale, Keyboard. Begins "Detecting hardware to find CD-ROM drives" and freezes at 86%, "Loading module 'ide-cd' for Linux ATAPI CD-ROM..."

Everytime. All the time. No fail.

I've tried tinkering with the bios settings, entering the boot options: linux pci=noacpi etc etc.

I just can't get it to work! ARGH! And I don't even know why! That's what really bugs me! :???: 

AMD Athlon 1200MHz
1GB DDR Ram
ECS K7S5A (3.1) motherboard (VIA Chipset)
Maxtor 30GB HDD
nVidia GeForce 4 Ti 4200
and the integrated sound card, NIC and USB.

The hard drive has been wiped on my windows box, and has no partitions or anything. I just slammed it back in, and prayed that was the problem. SOL I guess.

Any input would be appreciated. Thanks :)

---

### Post by 5-HT on 2005-10-15
[QUOTE=phend-one]

Begins "Detecting hardware to find CD-ROM drives" and freezes at 86%, "Loading module 'ide-cd' for Linux ATAPI CD-ROM..."

Everytime. All the time. No fail.

[/QUOTE]

Having the exact same problem here, freezes at 86%. 

I checked the md5sums of the .iso, even checked the sums against those listed on the cd after burning.

Hoary installed with no problems...but Breezy just wont get through that step.

I have no idea how to get around this, and it looks like I may need to just install Hoary again, which is too bad.


Anyone have any ideas?
Thanks for any input.

---

### Post by phend-one on 2005-10-15
^What type of hardware do you have?

---

### Post by 5-HT on 2005-10-15
[QUOTE=phend-one]^What type of hardware do you have?[/QUOTE]

I'm trying to install on a notebook with a pentium III processor, and IDE hard disk and DVD ROM drives.

I'm giving one last go with a different image and see if that helps.

What I did was to simply do an dist-upgrade from hoary, but ran into irq error problems trying to boot with the 2.6.12-9-386 kernel. 

I managed to get past that by adding in an "irqpoll" as a boot option in grub, am wondering if using such an option is ok to do in the long run.

After a bunch of fooling around though, I've messed up my breezy install...so I'll try a clean install again with that different iso but if that doesn't work I may just stick with hoary as stability is of primary concern.

I'd love to use breezy, but it seems to be fighting me at every step unfortunately.

---

### Post by phend-one on 2005-10-15
Hmm maybe I should check if there are IRQ conflcts. 

What "other image" are you using?

---

### Post by 5-HT on 2005-10-15
[QUOTE=phend-one]Hmm maybe I should check if there are IRQ conflcts. 

What "other image" are you using?[/QUOTE]

Just the same i386 install .iso but from a different mirror (not that it should matter...but just in case ).

Md5sums checked out, and I'm about to burn it and see if it's still getting stuck at 86%.

---

### Post by leohart on 2005-10-15
After several times trying to find a solution. I left it on while helping a customer. AFTER a LONG time, I come back to find that it has moved on to the next step (DHCP). I was like: HOORAY.

So just chill out and go out to grab a cup of coffee at Starbuck (my fav is Venti Mint Mocha Chip)

---

### Post by 5-HT on 2005-10-15
[QUOTE=leohart] AFTER a LONG time, I come back to find that it has moved on to the next step (DHCP). I was like: HOORAY.

So just chill out and go out to grab a cup of coffee at Starbuck (my fav is Venti Mint Mocha Chip)[/QUOTE]

Leohart my hero!

So I'm guessing that in the end there were no issues with the install apart from that cd-mounting hiccup?

I did leave it while it was stuck on that step for a while, but was left with just the blue install screen and though it gave up.

I'll try again and just leave it, and hopefully meet the same results as you.

Thanks!

---

### Post by brentoboy on 2005-10-15
the driver that is loaded at 86% is probing your hardware to see if it is a good match, and it is hanging durring the probe.  There is some possiblity that ubuntu (or debian) was nice enough to abort the probe after some extended timeout.

I could believe that it might recover.  If not, try installing hoarty instead, maybe the offensive driver isnt even in the hoarty installer.  Then, after you get hoarty installed (and liking it) switch to breezy via dist-upgrade.

---

### Post by phend-one on 2005-10-15
[QUOTE=leohart]After several times trying to find a solution. I left it on while helping a customer. AFTER a LONG time, I come back to find that it has moved on to the next step (DHCP). I was like: HOORAY.

So just chill out and go out to grab a cup of coffee at Starbuck (my fav is Venti Mint Mocha Chip)[/QUOTE]

How long is LONG? :D

Yeah, maybe I just need to relax a bit. I'll let it do its thing...

EDIT: I started it at 4:32 this morning and it's now 5:49pm... 13hours and still at that screen :(

---

### Post by 5-HT on 2005-10-15
Well I left it running at the detecting cd-rom prompt for over an hour, and got to the scanning cd-rom screen but that remained at 0% and wouldn't budge.

I tried installing using "install irqpoll" on a hunch that the problems may be related and while I did get passed the detecting cd-rom screen, I received an error message stating that the "release file" was not found.

If I try to skip a step, or even redo one I end up getting a mount error for the drive....

Looks like this isn't an isolate issue either: [http://ubuntuforums.org/showthread.php?t=65240](http://ubuntuforums.org/showthread.php?t=65240)

Oh well, sorry breezy but you just don't seem to like my setup.

---

### Post by phend-one on 2005-10-15
Yup! That post you linked to describes the solution. (At least now I can get further than that 86%)

For anyone else following the thread having similar issues, these may help your situation:
1) DISABLE PnP OS in the BIOS
2) On boot: linux irqpoll noapic nolapic


This helped greatly and I'm progressing through the install as we speak. *crosses fingers*

**EDIT: **[http://ubuntuforums.org/showthread.php?t=73367&highlight=irqpoll]("http://ubuntuforums.org/showthread.php?t=73367&highlight=irqpoll") was actually the link that helped me arrive at the solution.

Your post helped me address the irqpoll and PnP OS as potential problems to the install. Thanks ;)

---

### Post by 5-HT on 2005-10-15
Nice! You're geting through it, and I think that I am too though I'm using a different method.
```

noapic or nolapic
``` 
didn't work for me but
```
 acpi=off no acpi 
```
looks promising (thanks to this thread: [http://ubuntuforums.org/showthread.php?p=415302](http://ubuntuforums.org/showthread.php?p=415302))

Though I'm pretty that I will (not sure about you or anyone else) have to edit grub to add  ```
irqpoll
``` to the kernel boot path in order to boot up everytime as that was what was needed for my  up quasi-completed mess of an upgrade.

---

### Post by James Keating on 2005-10-16
I had success by going into the BIOS on boot and changing the drive type from (auto) to CD-ROM. This was on a Compaq Presario laptop. The install later got stuck on installing the kernel (the third option worked, whatever that was), and GRUB. On trying again, it would hang on the CD detection again, but not every time. Eventually all three decided to not stick during the same run, and the install finished. 

My other problems on installing Hoary (if the CD problem remains in Breezy, this may still be relevant as well):

There was nothing for an ADSL connection. I had to go to an Internet cafe, stick the Roaring Penguin rp-pppoe on a floppy and compile it. This is still what I use. 

My laptop wouldn't sleep on pressing the power button briefly. 
Following instructions elsewhere, I edited the boot config file:
sudo pico /boot/grub/menu.lst
and changed the kernel line to add acpi=off noacpi (must be all on one line):
kernel	/boot/vmlinuz-2.6.10-5-386 root=/dev/hda1 ro quiet splash acpi=off noacpi
and to make sure it stays in kernel upgrades, also added that to the default lines:
# nonaltoptions=quiet splash acpi=off noacpi
I saved the file, then ran:
sudo update-grub
I still can only put it to sleep if I switch to a blank terminal first (control-alt-F6), otherwise it freezes.

My system clock was screwy as well, failing to read the hardware clock on booting but then writing its wrong system time to the hardware clock on shutdown. I took out all the automatic clock-setting packages. I then set /etc/crontab to run the hourly files every ten minutes:

SHELL=/bin/sh
PATH=/usr/local/sbin:/usr/local/bin:/sbin:/bin:/usr/sbin:/usr/bin
# min hour date month weekday (0 or 7 is Sunday) user	command
*/10 * * * *	root    nice -n 19 run-parts  /etc/cron.hourly
00 23 * * *	root	nice -n 19 run-parts  /etc/cron.daily
10 23 * * 2	root	nice -n 19 run-parts  /etc/cron.weekly
20 23 1 * *	root	nice -n 19 run-parts  /etc/cron.monthly

and made an executable file called setclock in /etc/cron.hourly to set the system time from the hardware clock:
#!/bin/sh
hwclock --hctosys 

I suspect that all or most of these problems are the fault of Compaq making the BIOS in some nonstandard way.

These problems all ate up a lot of time, but I have already saved that much and more by having switched away from an RPM-based distribution.

---

### Post by lupo on 2005-10-17
Hi there,
I had this problem once I wanted to install Hoary. I burnt the iso-image again, changed the cd-rom drive, tried different boot-parameters but without sucess...
Finally I found the cause of the problem: It has nothing to do with the cd-rom drive!! It was my 4 in 1 usb-cardreader I plugged  in! After removing this device the setup ran without any problems.
Greets
 Lupo

---

### Post by Jason_25 on 2005-10-17
[QUOTE=lupo]Hi there,
I had this problem once I wanted to install Hoary. I burnt the iso-image again, changed the cd-rom drive, tried different boot-parameters but without sucess...
Finally I found the cause of the problem: It has nothing to do with the cd-rom drive!! It was my 4 in 1 usb-cardreader I plugged  in! After removing this device the setup ran without any problems.
Greets
 Lupo[/QUOTE]
Thanks for that.  That would have drove me nuts.  My boot was getting stuck right after the drive initialization on an old PII gateway desktop.

---

### Post by Teroedni on 2005-10-17
[QUOTE=phend-one]Fustration cannot even begin to describe what I'm experiencing.

Before I begin, please don't ask me to check the md5 sums or redownload the image or change my cd-rom or whatever. I've done it all. Burned at numerous speeds. slower/faster.

Everytime I pop the 5.10 install cd in, it goes to start setup, but it doesn't go through the nice bootsplash logo way. It goes through the all text based "ISOLINUX" way. Fine.

Choose Language, Locale, Keyboard. Begins "Detecting hardware to find CD-ROM drives" and freezes at 86%, "Loading module 'ide-cd' for Linux ATAPI CD-ROM..."

Everytime. All the time. No fail.

I've tried tinkering with the bios settings, entering the boot options: linux pci=noacpi etc etc.

I just can't get it to work! ARGH! And I don't even know why! That's what really bugs me! :???: 

AMD Athlon 1200MHz
1GB DDR Ram
ECS K7S5A (3.1) motherboard (VIA Chipset)
Maxtor 30GB HDD
nVidia GeForce 4 Ti 4200
and the integrated sound card, NIC and USB.

The hard drive has been wiped on my windows box, and has no partitions or anything. I just slammed it back in, and prayed that was the problem. SOL I guess.

Any input would be appreciated. Thanks :)[/QUOTE]


Do you got Serial Ata or Paralell
If parralell how is it set up?
Do you got harddrive and cd on one cabel and which one is master and slave?.
You may also consider underclocking your cpu(bus)
It may be that it will help the install.It shouldnt be a problem as you can clock it back after succesfull install.
set pnp=no
And disable all your paralell and serial ports if  you dont need them
It may be that they are making irq problems with addoncards and such.
Do you use dual ram ?
do you have different speed on them?
maybe you only need to move the ram
It can be all sort of things

---

### Post by Teroedni on 2005-10-17
But lets begin with the hardrive first.
Tell me what type of hardrive you have and what config u use

We should be able to fix this problem. It may just take some time to find out whats stopping the install. you just need some patience and good will.

Regards 
Teroedni

---

### Post by lupo on 2005-10-17
As I mentioned before, ensure that you disconnect all devices which would be detected as volume but aren't actually "real" volumes, such as card-reader, digi-cam, usb-stick etc.

---

### Post by phend-one on 2005-10-17
[QUOTE=Teroedni]But lets begin with the hardrive first.
Tell me what type of hardrive you have and what config u use

We should be able to fix this problem. It may just take some time to find out whats stopping the install. you just need some patience and good will.

Regards 
Teroedni[/QUOTE]

Sorry, but I already solved the problem. Thanks though! :KS

---

### Post by Teroedni on 2005-10-17
Okey thats nice:)
Can you tell me what the problem was
I am just a litlle curios;)

---

### Post by phend-one on 2005-10-18
Scroll up, we have all posted different solutions.

---

### Post by Benchrest on 2005-10-30
I am having this problem installing Breezy and none of the suggestions work or my bios doesn't allow. I get the 'detecting hardware to find cd-rom drives message' and am stuck at 'loading module IDE-CD for LINUX ATAPI CD-ROM' message where it sticks for 25 minutes. If I pull my Linksys ethernet card it only sticks there for 5 minutes. The next screen I get is a 'BLUE SCREEN' for 20 minutes. After that I get 'Scanning CD-ROM  0%  scanning /CDROM/pool/main/a....' and it hangs at the zero percent for 15 plus minutes when I power off.  Like the others, I had no problem installing Hoary. I have disabled both serial and parrellel ports and have nothing physcally attached. My computer is in my signature. I would apprciate any ideas.

---

### Post by Benchrest on 2005-10-31
I have used my Breezy CD to  install to a desktop, so I feel confident the CD is ok. The screens I hang on for so long process in less than a minute on my desktop. By the way, I don't remember those screens existing on Hoary install. This is a show stopper for me if I can't install Breezy so I can get to the newer Open Office that has the database function.

---

### Post by Teroedni on 2005-11-01
TRy to set plug and play to no and try
if that fail
Try plug and play to yes and try

---

### Post by Benchrest on 2005-11-01
Thanks for your reply. I do not have PnP as an option on this old laptop's BIOS. I am retrying it now, but letting it sit in the third screen mentioned, 'Scanning CD-ROM 0% scanning /CDROM/pool/main/a....' to see if it will eventually finish. It has been over 20 minutes so far. I have another option to 'UPGRADE' instead of 'FRESH INSTALL"? but I was hoping to avoid that.

---

### Post by Benchrest on 2005-11-01
Its been a couple of hours now and it's not stuck! But terribly slow. It's now showing 'Scanning CD-ROM 8% scanning /CDROM/pool/main/e....' Should be done in another 24 hours or so on this step. Maybe I'll have it installed before DD comes out;) . Hopefully it will break loose at some point.

---

### Post by Benchrest on 2005-11-01
Now at 22%, not getting any quicker. This seems like a problem I should report through bugzilla, but I doubt if they would make a change to the distribution until Daper Drake at the earliest. A fix in the repro's would do me no good. If it doesn't speed up in the next hour I will need to kill it. Makes me wish I had tested the prerelease version of BB so maybe it would have gotten fixed on the final release.

---

### Post by Benchrest on 2005-11-02
At startup I pressed F2 when I saw the Ubuntu logo and entered: linux acpi=off noapic nolapic as I read in another post. It smoked right by the screeens that had been so slow and is installing! Now I need to research what those parameters mean and see if I really needed them all or if they may cause other problems.

---

### Post by papasan on 2005-11-27
this worked for me on my old IBM thinkpad...
```
linux pci=noapic
```

---

### Post by 5-HT on 2005-12-02
[QUOTE=Benchrest]At startup I pressed F2 when I saw the Ubuntu logo and entered: linux acpi=off noapic nolapic as I read in another post. It smoked right by the screens that had been so slow and is installing! Now I need to research what those parameters mean and see if I really needed them all or if they may cause other problems.[/QUOTE]

Glad you got it to run, sorry I wasn't able to be of some help. 
In terms of consequences, while I'm by no means any expert in the area I believe the noapic and nolapic options repercussions would mostly affect only multi processor setups (though I could be wrong). With acpi turned off, you'd loose some of the advanced power management and diagnostic capabilities available through acpi (while useful in certain circumstances...their lack does beat being able to install, in my opinion).

---

### Post by renegado on 2006-01-29
how you solved the problem?:-k

---

### Post by renegado on 2006-01-29
> 
Quote:
Originally Posted by Teroedni
But lets begin with the hardrive first.
Tell me what type of hardrive you have and what config u use

We should be able to fix this problem. It may just take some time to find out whats stopping the install. you just need some patience and good will.

Regards
Teroedni

Sorry, but I already solved the problem. Thanks though! 


please, how you solved the problem?

---

### Post by saschaz on 2006-02-23
I had the same problem with my ACER Travelmate 529 TXV.

Look in this thread for my solution:

[http://ubuntuforums.org/showthread.php?t=128987](http://ubuntuforums.org/showthread.php?t=128987)

---

### Post by MediaHound on 2006-06-24
Same problem.. first posted about it in this thread:
[http://www.ubuntuforums.org/showthread.php?t=167518](http://www.ubuntuforums.org/showthread.php?t=167518)

Left it overnight, that didn't help; it's still stuck. 

I'll now try the acpi=off then the pci=noacpi. 

Hope to see this fixed in future versions!

](*,)

---

