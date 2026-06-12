---
title: "Restarts When i press enter???"
date: 2005-04-16
forum: Installation &amp; Upgrades
---

### Post by Diddy1 on 2005-04-16
Every time i boot with the installation cd in the tray it shows the start screen. Then i press enter for a normal configuration, and my pc just restarts??

Anyone know what is wrong?

Thanx In Advance.

---

### Post by arctic on 2005-04-16
hi there.

first of all: which system are you trying to install? 5.04 hoary or 4.10 warty?
then we would need some information on your hardware (graphics etc.). and have you done any partitioning? please give us a rough idea of the partition structure of your system.

but you might have luck with the following approach:
when the cd starts to boot, go to the advanced boot settings (hit f1) and try to start your system with the following options:

linux noapic nolapic

maybe that helps. good luck anyways. :)

---

### Post by dcahrakos on 2005-04-16
im having the same problem, except mine gets to uncompressing linux, Ok.....booting the kernel, then it restarts...

specs:
Intel Celeron 2.8ghz
786MB ram
Radeon 9250 128MB video card.

...hopefully someone can help both of us.
edit: I tried the linux noapic nolapic but it didnt work for me

---

### Post by Diddy1 on 2005-04-16
oh sorry forgot. 

5.04 hoary 

and all i know is that i use an intel celeron and a compaq fs7600 color monitor.

Thanx im trying the thing u said right now.

---

### Post by Diddy1 on 2005-04-16
[QUOTE=Diddy1]oh sorry forgot. 

5.04 hoary 

and all i know is that i use an intel celeron and a compaq fs7600 color monitor.

Thanx im trying the thing u said right now.[/QUOTE]
 Tried doesn't work. And when i looked more i saw that same messege"uncompressing linux, Ok.....booting the kernel" Then it restarts. 

If anyone has any idea please post it.

Thank You

---

### Post by dcahrakos on 2005-04-16
seems you get the same error as me, I was talking to someone in the IRC chatroom, and he said it might be power management issues, but im not sure what that really means.

---

### Post by Diddy1 on 2005-04-16
I just tried the live cd i get the same thing. 

Could someone plese offer any advice?

---

### Post by codejunkie on 2005-04-17
i had exact same problem with my compaq presario SR1103WM i had to boot with the) linux acpi=off (option or it just kept rebooting try that it should fix the problem.
for the live cd use.       live acpi=off

---

### Post by dcahrakos on 2005-04-17
THANK YOU! that worked perfectly :) time to go install now.

---

### Post by arctic on 2005-04-17
hmm... some computers, especially laptops do require different parameters in order to boot them. once the cd starts, press f1 for advanced options and take a look at the various screens (pressing f2 - f8) and try with different kernel-parameters.

BUT it might not work at all with some machines. ati and nvidia graphic cards are known to be somewhat problematic, but i cannot give much advice in this area as i don't use them on my boxes. but a search in these forums or debian lists (e.g via google) may be helpful in this respect.

---

### Post by dcahrakos on 2005-04-17
ok, I got passed booting the cd, and it does its thing, then it ejects the cd at the end, and reboots, then when it starts up, it does somethings, and when it gets to Starting Hotplug Subsystem it seems to hang.....and doesnt do anything at all...what could cause this?

---

### Post by Diddy1 on 2005-04-17
It worked thanx man. But may i ask what does turning acpi off do? By the way  i happen to have a compaq presario too.

Thanx again.

---

### Post by dcahrakos on 2005-04-17
can you get yours past the starting hotplug subsystem?

---

### Post by Diddy1 on 2005-04-17
Yeah the live cd booted up ok. Im gonna try the install right after this.

---

### Post by arctic on 2005-04-17
[QUOTE=dcahrakos]ok, I got passed booting the cd, and it does its thing, then it ejects the cd at the end, and reboots, then when it starts up, it does somethings, and when it gets to Starting Hotplug Subsystem it seems to hang.....and doesnt do anything at all...what could cause this?[/QUOTE]
 do you have any usb-devices plugged into your system? if yes, unplug them and retry booting.

---

### Post by dcahrakos on 2005-04-17
[QUOTE=arctic]do you have any usb-devices plugged into your system? if yes, unplug them and retry booting.[/QUOTE]
 I tried, hangs at the same place...

---

### Post by arctic on 2005-04-17
hmm.... when it hangs, can you bypass the hotplug, pressing ctrl+c? it works for some other stuff, but i am not sure if your system completely froze. in that case, bypassing won't help....

out of ideas atm.  :neutral:

---

### Post by dcahrakos on 2005-04-17
[QUOTE=arctic]hmm.... when it hangs, can you bypass the hotplug, pressing ctrl+c? it works for some other stuff, but i am not sure if your system completely froze. in that case, bypassing won't help....

out of ideas atm.  :neutral:[/QUOTE]
 yeah, I bypassed it, and everything installed, but when it boots up, it says there was an error with the X-server and it cant be run, and there no desktop, and only runs in console mode....

---

### Post by codejunkie on 2005-04-18
[QUOTE=Diddy1]It worked thanx man. But may i ask what does turning acpi off do? By the way  i happen to have a compaq presario too.

Thanx again.[/QUOTE]

The acpi=off just turns off the powermangent features built into the motherboard i think if im wrong someone please let me know.

my compaq my motherboard has a  feature that lets the os/windows adjust the fan speeds automatically, i dont think linux supports this yet, again if im wrong someone please let me know. in windows they are super quiet, with the acpi=off they run at full speed a bit louder but still very quiet.. i dont know if this was the answer you were looking for but i hope it helps.

---

### Post by codejunkie on 2005-04-18
[QUOTE=dcahrakos]yeah, I bypassed it, and everything installed, but when it boots up, it says there was an error with the X-server and it cant be run, and there no desktop, and only runs in console mode....[/QUOTE]

you said your specs are
specs:
Intel Celeron 2.8ghz
786MB ram
Radeon 9250 128MB video card.

does your motherboard have onboard video? and the Radeon 9250 128MB video card? or just the Radeon card i have had the same problems trying to use two video cards at the same time when installing linux.

---

### Post by dcahrakos on 2005-04-18
[QUOTE=codejunkie]you said your specs are
specs:
Intel Celeron 2.8ghz
786MB ram
Radeon 9250 128MB video card.

does your motherboard have onboard video? and the Radeon 9250 128MB video card? or just the Radeon card i have had the same problems trying to use two video cards at the same time when installing linux.[/QUOTE]
 yeah, it has both...thats probably the reason...what can I do to just make it use the radeon?

---

### Post by codejunkie on 2005-04-18
The first thing that i would try is going into the bios and disable the onboard video completely if you could post these specs it would be a great help.

computer manufacture 
computer model number 
what kind is your radeon card / pci,agp,pci express
and if you built the computer yourself 
what is the modle number of your motherboard

---

### Post by codejunkie on 2005-04-18
**dcahrakos**  I read  your other forum posts about the problem  and it answered my 
questions on my motherboard it would'nt let me disable the onboard video either it just let me set 8mb - 64mb for onboard video memory, on my motherboard the only way i have to upgrade is pci slots because compaq disabled the agp slot. and i had to use a pci card also in my case the problem with this is x automaticly uses the onboard video.in my case the easiest thing i have found to fix this is use onboard video but if you have an agp slot in your computer, i was told if you use an agp video card insted of the pci one the motherboard will automatically diable the onboard video and use the agp card because the onboard video and agp slot use the same 
Bus address. 
      if you have an old agp video card you could try that and see if it works or edit the /etc/X11/xorg.conf file to use the Bus address of the pci card i assume.  i know this info aint much but i hope it helps you. if you do find a solution please keep me posted because i would really like to use my other video card also.

---

### Post by dcahrakos on 2005-04-18
Ill try but oddly enough, this pc doesnt even have an agp slot, or I would have had agp video card...for some reason, so benchmark and pc info software said I had one, but it was wrong. ill reinstall it tomorrow morning, and take a look at the xorg.conf file, and see what I can do to get it working.

---

### Post by codejunkie on 2005-04-19
my computer does'nt have agp slot either :-k  it just has the place where it should be its  labled agp 1 i did alot of checking on the motherboard and i found out that compaq/hp does this on alot of there computers which make no sence the only reason i think it's done is to limit there lower end pc's upgradeability because most of there higher end pc's all have the same motherboards but they have agp slots :mad:

---

### Post by codejunkie on 2005-04-19
dcahrakos how did you get past the **Starting Hotplug Subsystem** when i use the **install disk** it kept freezing on me i pressed **ctrl+c** and it just locked up again and again but if i use the **live cd** and press **ctrl+C** @  **Starting Hotplug Subsystem** i get console mode but it won't work for me using the install disk. this thing is driving me crazy i reinstalled just to see if i could get my video card with tv out to work but im back at thinking i may be stuck with onboard video.

---

### Post by dcahrakos on 2005-04-19
I got past the hotplug by pressing Ctrl+C right before it shows "Starting hotplug Subsystem" and it gets past it, if you do it when it already says it, for some reason it doesnt go...so do it just before..and press it 3 or 4 times.

I wonder if there is a way to open up the agp slot...they couldnt have butchered it that much

theres also this on ATI drivers for ubuntu
[http://www.ubuntuforums.org/showthread.php?t=24557&highlight=ati](http://www.ubuntuforums.org/showthread.php?t=24557&highlight=ati)

also, when that says to install them, it says you need the kernel version, is that just linux-386?

---

### Post by dcahrakos on 2005-04-19
I FINALLY got it to start up, with xserver running....by reconfiguring the xserver to use vesa, and my built in video card...its a start, but now, it doesnt detect my ethernet card...is there a way to make it detect and configure it?

---

### Post by codejunkie on 2005-04-20
thanks for the help with ctrl+c @ Starting hotplug Subsystem it works but i still can't get my nvidia card working either X will only use the onboard intel video no mater what i 've tried in /etc/X11/xorg.conf 

[QUOTE=dcahrakos]
I wonder if there is a way to open up the agp slot...they couldnt have butchered it that much
[/QUOTE]

in my case i don't think that there's much i can do with the agp slot they have removed the agp card slot an soldered up all the connectors that would be an easy fix but time consuming i think it's more in the bios flash but i'd be more afraid playing with that than  the agp slot because i know how quick you can kill a motherboard playing with it.

as far as the networkcard i think that maybe something to do with hitting ctrl+c at
Starting hotplug Subsystem because my network and sound did'nt work either 
so i just removed my nvidia card ](*,) formatted and reinstalled every thing works great except im stuck with 8mb onboard video.

---

### Post by dcahrakos on 2005-04-20
[QUOTE=codejunkie]thanks for the help with ctrl+c @ Starting hotplug Subsystem it works but i still can't get my nvidia card working either X will only use the onboard intel video no mater what i 've tried in /etc/X11/xorg.conf 



in my case i don't think that there's much i can do with the agp slot they have removed the agp card slot an soldered up all the connectors that would be an easy fix but time consuming i think it's more in the bios flash but i'd be more afraid playing with that than  the agp slot because i know how quick you can kill a motherboard playing with it.

as far as the networkcard i think that maybe something to do with hitting ctrl+c at
Starting hotplug Subsystem because my network and sound did'nt work either 
so i just removed my nvidia card ](*,) formatted and reinstalled every thing works great except im stuck with 8mb onboard video.[/QUOTE]
 yeah, I think it gets stuck at the hotplug because of the network card, and/or sound..cause neither worked for me......oh well, guess im stuck with windows until I can get it to work right...thats not too bad, as I know some programming languages that are windows only...like VB and VB.NET..so its not the end of the world..I just wanted a change.

---

### Post by codejunkie on 2005-04-20
you could remove your ati video card completly and just use onboard video everything works great on mine now but i had to remove my nvidia card completly from the system and reinstall ubuntu but i'd rather be stuck with onboard video than windows. but if you need support for the the ati card for games and other stuff like that right now i think windows would be the only option.

---

### Post by dcahrakos on 2005-04-21
[QUOTE=codejunkie]you could remove your ati video card completly and just use onboard video everything works great on mine now but i had to remove my nvidia card completly from the system and reinstall ubuntu but i'd rather be stuck with onboard video than windows. but if you need support for the the ati card for games and other stuff like that right now i think windows would be the only option.[/QUOTE]
 The only problem is, my brother uses this pc also, and he doesnt want to use linux...so if I removed it, we would have to keep putting it back in and out everytime one of us was using the pc....so thats not really an option.

im gonna try Microsoft virtual PC..i heard it was much faster then vmware...so we will see what happens

---

### Post by codejunkie on 2005-04-22
yeah i understand that it would be a pain doing that.. about the Microsoft virtual PC
using windows xp i got better preformance with vmware under windows  i used the trial of Microsoft virtual PC and it took almost an hour a half  to install windows xp compared to vmware only taking about 30 minutes, plus apps were so slow in Microsoft virtual PC it was almost like using a 386 processor all over again. but it could have been locked down or something where it was a trial version who knows but i thought microsoft would at least make it preform well under windows. I read somewhere that the mac version was real fast funny huh! microsoft software works better on a mac. ;-)
let me know how it works out for ya, maybe my bad experince with it was caused by something else.

---

### Post by dcahrakos on 2005-04-22
[QUOTE=codejunkie]yeah i understand that it would be a pain doing that.. about the Microsoft virtual PC
using windows xp i got better preformance with vmware under windows  i used the trial of Microsoft virtual PC and it took almost an hour a half  to install windows xp compared to vmware only taking about 30 minutes, plus apps were so slow in Microsoft virtual PC it was almost like using a 386 processor all over again. but it could have been locked down or something where it was a trial version who knows but i thought microsoft would at least make it preform well under windows. I read somewhere that the mac version was real fast funny huh! microsoft software works better on a mac. ;-)
let me know how it works out for ya, maybe my bad experince with it was caused by something else.[/QUOTE]
 it took forever to install, but I didnt notice much of a difference between that and vmware...infact, vmware was a little faster...ive also heard of colinux, where you can run linux under windows, but it supposed to be hard to use...I may try that though.

---

