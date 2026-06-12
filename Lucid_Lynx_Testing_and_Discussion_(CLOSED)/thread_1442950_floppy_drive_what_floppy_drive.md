---
title: "floppy drive? what floppy drive?"
date: 2010-03-30
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by bigsmitty64 on 2010-03-30
In places/computer    shows a floppy drive. I HAVE no floppy drive. If I click it, it says:

 "opening floppy drive: you can stop this by hitting cancel" 

is this possibly just a bug in 10.04 beta 1?

---

### Post by psusi on 2010-03-30
No, you told your bios you have a floppy, and Linux believes it.  Go into your bios and tell it you do not have a floppy.

---

### Post by bigsmitty64 on 2010-03-30
actually, I turned off floppy seek at bootup a long time ago, this just happened since I installed 10.04 beta 1

---

### Post by new_tolinux on 2010-03-30
It's not only "floppy seek at bootup".
In most BIOS-es there is an option to specify that you have a floppy drive. Set it tot "none".
(mostl times that option is found where you also configure your hard-drives).

---

### Post by bigsmitty64 on 2010-03-30
The only other thing in my bios that say anything about a floppy is: Removable Device Priorities

There it shows "Floppy" but no option to disable it.

Again this JUST started happening and I haven't changed anything in bios for quite a while

---

### Post by coffeecat on 2010-03-30
No sign of a floppy drive in "Computer" on a newish laptop with fully updated Lucid. On my home-build desktop there is a floppy icon, but perhaps that's because it's fitted with a floppy drive. Works just fine in Lucid too.

I agree this sounds like a BIOS issue, but I would have thought the BIOS simply wouldn't report the presence of a floppy if there wasn't one. I don't remember seeing an option to set floppy=none in a BIOS, but then I probably wasn't looking very closely.

@bigsmitty64, you'll probably get more responses if this thread was in the Lucid subforum. I'll ask a mod to move it.

---

### Post by bigsmitty64 on 2010-03-30
@coffeecat 
Thanks man. 

The reason I think it's something to do with Lucid is because I JUST installed that yesterday.

---

### Post by psusi on 2010-03-30
Floppy manufacturers never bothered implementing the device detection commands so you always have to manually tell the bios what type you have.  Linux has to trust this setting too.  All bios have a setting to specify the type of floppy or none.  Seek just says to turn on the drive and move the head at boot.  It does not matter.

---

### Post by srs5694 on 2010-03-30
You may be able to get rid of the floppy by removing the floppy device driver. As an experiment, try typing "sudo rmmod floppy" at a command prompt. If you get an error, try "sudo rmmod -f floppy". If either of these commands succeeds in getting the icon to disappear, try adding it (minus the "sudo" part) to the /etc/rc.local file and see if it works when you reboot.

---

### Post by Omoronovo on 2010-03-30
> **bigsmitty64 said:**
> In places/computer    shows a floppy drive. I HAVE no floppy drive. If I click it, it says:

 "opening floppy drive: you can stop this by hitting cancel" 

is this possibly just a bug in 10.04 beta 1?

What motherboard do you have? We could probably tell you exactly how to disable the floppy device if we knew which motherboard and bios you use.

This is actually a major issue nowadays for many operating systems, Vista/Windows 7 delay their setup considerably if the bios has a floppy set but not one actually installed; presumably to check for additional sata/raid drivers.

---

### Post by bigsmitty64 on 2010-03-30
Mainboard is ECS  GeForce 6100PM-M2  V: 2.0

---

### Post by bigsmitty64 on 2010-03-30
No takers? :)

---

### Post by VMC on 2010-03-30
You went through your BIOS in detail looking for any referance to floppy and disabled it?

Also, I got tired of listening to my CDROM being detected of each boot, re-boot so I removed it, and use it through usb-ide connection. Also it boots faster.

Regarding floppy. As I remember, after I removed the floppy I never saw any message about floppy again. Maybe the power and connection needs to be removed. I figured, on the rare occasion I ever use a floppy I can plug it back in.

---

### Post by RJARRRPCGP on 2010-03-30
I know that with an Award BIOS, if the BIOS is configured to search for a floppy disk drive and you don't have a floppy disk drive, then the BIOS will bug you with :

Floppy disk(s) fail

Press F1 to continue. (or similar)

---

### Post by swoll1980 on 2010-03-30
Lucid thinks I have a floppy drive too. I'll have to check my BIOS out and see if I can convince it otherwise.

---

### Post by bigsmitty64 on 2010-03-30
> **VMC said:**
> 
Maybe the power and connection needs to be removed.

There is nothing hooked to my mother board floppy connection or the power connection. I removed it months ago.

---

### Post by cariboo on 2010-03-30
Have a look at the screen shot. The setting to disable the floppy is on the Standard CMOS Features page in the BIOS.

---

### Post by zacbarton on 2010-03-31
Try removing it from /etc/fstab. 

It worked for me and I dont have a floppy drive either even though it was listed in fstab.

---

### Post by bigsmitty64 on 2010-03-31
> **cariboo907 said:**
> Have a look at the screen shot. The setting to disable the floppy is on the Standard CMOS Features page in the BIOS.

O.K. You got me excited for a minute. I found it under the cmos settings. Disabled it.... It's still there in the file browser.

---

### Post by bigsmitty64 on 2010-03-31
> **zacbarton said:**
> Try removing it from /etc/fstab. 

It worked for me and I dont have a floppy drive either even though it was listed in fstab.


Remove this line?

```
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
```

---

### Post by LinuxTAd on 2010-03-31
In fstab I changed this

```
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
```

to this:

```
# /dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
```
That worked for me, thank you :)

---

### Post by andrewabc on 2010-03-31
> **LinuxTAd said:**
> In fstab I changed this

```
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
```

to this:

```
# /dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
```
That worked for me, thank you :)

Yep, don't need to delete in fstab, can just comment out (put a # in front of text) in case you want it later for some reason.

---

### Post by bigsmitty64 on 2010-03-31
Thanks LinuxTAd that did the trick.  I appreciate everyones help !

But........I'm still wondering why this floppy drive appeared out of nowhere all of a sudden?

---

### Post by psusi on 2010-03-31
Because you flashed your bios or something else to cause it to decide you had a floppy, then when you installed lucid it set up your fstab to mount it.

---

### Post by Omoronovo on 2010-03-31
> **bigsmitty64 said:**
> Thanks LinuxTAd that did the trick.  I appreciate everyones help !

But........I'm still wondering why this floppy drive appeared out of nowhere all of a sudden?

It's a combination of both factors: After you installed Linux with the floppy drive enabled in the Bios - even if one doesn't exist - linux has to make an entry in fstab. After you removed the device from Bios, you then still had to remove the entry from fstab.

In future, as long as you do not re-enable this option in the bios, you will never get a new entry in fstab to deal with - even if you reinstall linux.

---

### Post by bigsmitty64 on 2010-04-01
Cool beans, thanks for everyones input here!

---

### Post by coffeecat on 2010-04-01
> **bigsmitty64 said:**
> Mainboard is ECS  GeForce 6100PM-M2  V: 2.0

That's interesting. I've got one those.

I had a look in the BIOS, and I *think* the setting you need to change is:

Go to "Standard CMOS feature" (the first option from the main BIOS page). Scroll down to "Drive A" and change the setting to 'none'. I haven't tested this because I have a floppy fitted and don't want to disable it, but it might be worth trying. - or at least having a look at whatever setting yours is showing.

I hope you're still following this thread because I have a question and a cautionary tale.

Ever since I bought this board, I haven't been able to use RAM in the second slot. I've tried matched pairs and a known working RAM in the second slot only, but whatever I do, if there's a stick in the second slot, the system simply freezes and won't even show the POST screen. This is probably a hardware fault rather than a BIOS setting problem, but I haven't explored the latter possibility much - the DRAM configuration settings are incomprehensible to me. Have you tried two sticks? If so, with what result?

The moral of the cautionary tale is to think twice before attempting a BIOS upgrade with this board. In the misguided hope that a BIOS upgrade would fix the memory problem, I downloaded the latest version and flashed this. Fortunately, I used the Windows GUI utility that the manufacturer also offered for download and, just as fortunately, I had the presence of mind to use a feature in the utility that let me save the old BIOS. When I tried booting into the new BIOS, Windows was just fine, but none of the several Linux distros I had setup as a multiboot would boot up. I can't remember whether there were any error messages or whether they just froze, but I couldn't get much past grub.

A bug in ACPI? I don't know and didn't care to waste my life trying to find out. I simply restored the old version of the BIOS and now I can run Linux on that board - but with one RAM stick only. :(

Beware!

---

### Post by cascade9 on 2010-04-01
@ coffeecat- I've seen that happen before. Sometimes is that the system would only take single sided RAM (that shouldnt be a problem with DDR2 *shrugs*). I've also seen dead RAM slots- have you tried just using slot2 with no memory in slot1? (I'm guess you have and it just freezes). 

> **cariboo907 said:**
> Have a look at the screen shot. The setting to disable the floppy is on the Standard CMOS Features page in the BIOS.

Nice. There is another settings for the floppy (page 41 on the same manual that the screenshot was from), manual here- 

[http://www.ecs.com.tw/ECSWebSite/Downloads/DownloadFile.aspx?catid=1&driverid=3990&areaid=1&LanID=0](http://www.ecs.com.tw/ECSWebSite/Downloads/DownloadFile.aspx?catid=1&driverid=3990&areaid=1&LanID=0)

Go to  "Intergrated Perepherials-> SuperIO Device-> OnbaordFDC controller". Set that to 'disabled'. 

Disabling the controller might make the floppy disappear, as removing the floppy from the standard CMOS features doesnt turn off the controller, it just makes the BIOS not look for the floppy drive.

---

### Post by coffeecat on 2010-04-01
> **cascade9 said:**
> @ coffeecat- I've seen that happen before. Sometimes is that the system would only take single sided RAM (that shouldnt be a problem with DDR2 *shrugs*). I've also seen dead RAM slots- have you tried just using slot2 with no memory in slot1? (I'm guess you have and it just freezes). 

Yes, it is DDR2 and slot 1 sees all the RAM on a double-sided stick. And, yes, I have tried one (good) stick in slot 2 with slot 1 empty. No go. A dead slot is the most likely explanation I fear. Still, it is an ECS board which is at the - ahem - 'budget' end of the quality range. :wink:

---

### Post by VMC on 2010-04-01
> **roldannarag said:**
> Please Help me..I have a lot of files in my Ubuntu..

I Just Mark all Upgrade in my Synaptic package..after restarting my laptop..Login appears but when i log in olny mouse cursor with black screen appears..

please help..


Im using lenovo with ATI video Card..

thanks...

You need to start a new topic and don't use the "please help" as a title. Be more specific.

---

### Post by bigsmitty64 on 2010-04-01
> **coffeecat said:**
> That's interesting. I've got one those.

I had a look in the BIOS, and I *think* the setting you need to change is:

Go to "Standard CMOS feature" (the first option from the main BIOS page). Scroll down to "Drive A" and change the setting to 'none'.


Ever since I bought this board, I haven't been able to use RAM in the second slot.



Wow!  I have only one stick also, I will try sticking it in the other slot and report back here momentarily.

I DID get the floppy issue straightened out doing just what you said. I found it yesterday!

---

### Post by bigsmitty64 on 2010-04-01
@ coffeecat
O.K. I'm back and I moved the 2 gig stick and all seems well here. System monitor reporting all 2 gig.

I wish I had another stick to throw in there but I do not.  My ram is, as follows:


Model:  KVR667D2/2GR 
- Type:  240-Pin DDR2 SDRAM 
- Capacity: 2GB 
- Speed: DDR2 667 (PC2 5300) 

Good luck

---

### Post by coffeecat on 2010-04-01
> **bigsmitty64 said:**
> @ coffeecat
O.K. I'm back and I moved the 2 gig stick and all seems well here. System monitor reporting all 2 gig.

I wish I had another stick to throw in there but I do not.  My ram is, as follows:


Model:  KVR667D2/2GR 
- Type:  240-Pin DDR2 SDRAM 
- Capacity: 2GB 
- Speed: DDR2 667 (PC2 5300) 

Good luck

Thanks for that. I think it confirms what I suspected - that slot 2 is faulty on my board. At the moment I have a 1GB stick in it and limit myself to 32-bit installs and use it as a secondary machine. My original intention was to get a matched pair of 2GB sticks so that I could run 64-bit comfortably, but I abandoned that idea when I discovered the problem when I fitted 2 x 1GB sticks.

But, tbh, 32 bit Ubuntu works just fine in 1GB. I even do some video rendering and I haven't run out of memory yet - it just takes a bit longer.

---

### Post by bigsmitty64 on 2010-04-01
Ya, that sounds like the problem.
 I also do a lot of video editing and pic editing. I haven't had many ram issues with 2 gig, but **some** lag here and there when doing video editing like you said.

---

### Post by cascade9 on 2010-04-01
> **coffeecat said:**
> Yes, it is DDR2 and slot 1 sees all the RAM on a double-sided stick. And, yes, I have tried one (good) stick in slot 2 with slot 1 empty. No go. A dead slot is the most likely explanation I fear. Still, it is an ECS board which is at the - ahem - 'budget' end of the quality range. :wink:

LOL, yeah, I'm not fond of ECS, I've got a K7S5A that is always being troublesome. 

I agree, dead slot. 

BTW, I'd try the 64bit version anyway if your doing video rendering- I've played with 32bit and 64bit, and despite what I've seen soem people say, 64bit doesnt seem to use any more RAM than 32bit. YMMV though ;)

---

