---
title: "forced shutdown - boot record !=backup"
date: 2007-04-29
forum: Installation &amp; Upgrades
---

### Post by scradock on 2007-04-29
I'm trying to install Edgy on my wife's desktop machine - eMachines T1840. Had install troubles, then GRUB troubles. Had to use fixmbr to get Windows back working. Then I used GRUB from the LiveCD to setup GRUB in the mbr again. Then it had trouble finding the right partition - long story

Now the 2.6.17-10 version boots from the hd. I tried to update to 2.6.17-11, but it won't boot that kernel - kernel panic almost immediately. I'll try the update again, when I fix the other problem.

The reason I'm writing is to ask why the 2.6.17-10 version shuts down the machine after 5 minutes or so, complaining that the boot record does not match the latest backup. Which boot record would that be? - the mbr? How do I make sure it has a correct backup, or how can i stop it comparing the new correct mbr with an incorrect backup?

Any help much appreciated - we want out of Windows!
sc

---

### Post by Herman on 2007-04-30
Hello scradock,
Are you sure the error message isn't "there are differences between the bootsector and its backup" ?

That error message normally is received during boot-up. Your computer will be booting and you'll see your Ubuntu Splash screen with the progress bar showing Ubuntu loading but it pauses at about 25%.
Then you see a black page with white text as Ubuntu performs filesystem checks during boot -up. If your Windows fat32 partition has differences between the bootsector and its backup you will be given this error message. You should be able to press 'Ctlr'+'D' to continue booting anyway.
I have never heard of that causing Ubuntu to shut down after 5 minutes or so once Ubuntu is bootied though, that part is something I don't understand. Maybe your error is somthing different from the one I'm thinking of.

If this sounds like the same error you are talking about, it can either be caused by a virus in Windows writing to Windows bootsector, or someone installing Grub to Windows boot sector instead of to the hard disk's MBR. If that happened you would not be able to boot Windows, but selecting Windows from your Grub menu would loop you back to your Grub menu again. 
One way to fix that, (if that's the one you mean), would be to run 'FIXBOOT' from a Windows [recovery console]("http://www.kellys-korner-xp.com/win_xp_rec.htm"). 'FIXBOOT' fixes the Windows bootsector, it doesn't do anything to the hard disk's  MBR.

Or maybe you mean something different, not all of the symptoms match up, so maybe I'm guessing wrong. Here's a link anyway, 
         [                      When the bootsector is not the same as its backup]("http://users.bigpond.net.au/hermanzone/p10.htm#differences_between_the_bootsector_and_its_backup")

Regards, Herman :)

---

### Post by scradock on 2007-05-04
Thanks for the suggestions, Herman.

I checked a bit more and realised that the bootsector problem was not causing the shutdown - it was showing up because the shutdown returned me momentarily to the boot messages before closing completely.

The real problem is overheating. I believe the cpu is overheating and that BIOS or linux is very sensibly shutting down to avoid damage.

The clue is that a slightly noisy fan (probably the cpu cooling fan itself) seems to be running all the time, in Windows and during boot into linux, until a couple of seconds into the boot process. Then it stops, and I never hear it come on again. A few minutes later - maybe ten, maybe thirty - the system shuts down.

I suspect an ACPI failure - it's an old machine. (5yrs, eMachines T1840). Running "acpi -t" in a terminal gives only a temperature reading, which is clearly erroneous - huge number with 10 or 12 digits "C".

I've tried booting with "acpi=off" on the boot line. The fan stays on, which is encouraging, but the Window Manager (Nautilus) doesn't start after login. Booting with "noacpi" instead I get the original behavior - fan goes out, and never starts up.

Any ideas - do I need a BIOS update? or a kernel patch? I have the latest Edgy with all available updates - presumably including the latest acpi modules.

Help, anyone?

---

### Post by Herman on 2007-05-04
```
herman@work:~$ acpi -t
     Thermal 1: ok, 53.0 degrees C
``` Hey, neat command! Thanks, scradock, that's one I didn't know about, I like it! :)

Here's a link to my [BIOS Page]("http://www.users.bigpond.net.au/hermanzone/p1.htm")

What type of BIOS do you have, can you go into CMOS and check in '[product information]("http://www.users.bigpond.net.au/hermanzone/p1.htm#Navigating_in_CMOS")' or the equivalent? Then if you go to your motherboard or BIOS manufacturer's website is there a newer version available for your machine?

Has your computer's BIOS got a '[PC health status]("http://www.users.bigpond.net.au/hermanzone/p1.htm#System_Health_Check")' feature? If it does you might be able to see if the temperature reported there is probably correct or if it seems to be erronous as well. Maybe you can just leave your computer running for a time like half an hour or so and watch in 'PC Health Status' to see what happens.  You should be able to watch your temperatures there, and see the fan speeds (rpm), voltages from your power supply and all that sort of thing. Not all BIOSes have a way for the user to see all these displayed.
Maybe that will help you a little. 

Does this problem only occur in Ubuntu or when running other OSes too? What about when running the LiveCD? 

Always begin troubleshooting by thinking of the simplest (don't overlook the blindingly obvious) and cheapest things first and proceed leaving the more expensive and more tricky things last.

How far from the wall is your computer case? Plenty of room around your air intakes for lots of cool air to enter and outlet vents for hot air to exhaust unobstructed?

How long since your computer has been serviced inside? Does it have any kind of air filter that might need cleaning, or do you just clean the case and CPU fans and fins every once and a while? (Like most PCs).
Sometimes with older computers it helps to unplug everything, including the CPU and the RAM modules, clean everything including the slots and reseat everything again. You may need a service technician to do these things if you aren't confident with doing them yourself. 

What about the thermal paste between your CPU and heatsink? Has that ever been disturbed? The thermocouple temperature sensor that reports the CPU temperature to your motherboard might be damaged or not making proper contact. It may be glued in the thermal paste in some older CPUs.

I hope something here will help you, the intention is there anyway,
Regards, Herman :)

---

### Post by scradock on 2007-05-04
Thanks again, Herman. Lots of good suggestions there.

At the moment I'm staying with the tell-tale fan noise - which just cuts out when ubuntu starts booting. I've checked with Phoenix/Award for a BIOS update - the date is August 2002, so it's ACPI version 1.0. I'm waiting for a call-back on what's available.

I've run Mepis and Knoppix on this machine in the past without problems, so I don't think it's generic to linux - just ubuntu Edgy. With all the fuss about problems upgrading to Feisty I'm not keen to go that way yet. I'll see how the BIOS upgrade turns out.

There has to be a way to turn on a cpu fan, doesn't there? Does anyone know how to do it? I really wouldn't mind if it stayed on all the time - I've read some very old posts suggesting that turning off acpi, and even adm as well, leaves the fan going all the time. That should take care of the overheating. But the system doesn't come all the way up - stalls at loading Nautilus or gdm - with "acpi=off" on the boot line.

Can anyone enlighten me about the difference btw "acpi=off" and "noacpi" as boot parameters? The first seems to be fatal, the second ineffective in my experience! [I've tried both on my other machine, an HP laptop that does Edgy very well indeed.....]

scradock

---

