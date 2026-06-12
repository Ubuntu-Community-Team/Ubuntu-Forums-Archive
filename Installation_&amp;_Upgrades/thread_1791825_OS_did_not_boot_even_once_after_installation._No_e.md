---
title: "OS did not boot even once after installation. No error specified."
date: 2011-06-27
forum: Installation &amp; Upgrades
---

### Post by Chandra sekhar on 2011-06-27
Hi 
  I am new to both this place and ubuntu. I have a HP-G42 laptop with a 64 bit processor running and windows 7 home basic. I have a 500GB hdd which i divided into 4 drives.
 
  So today i installed ubuntu studio 9.04 in my laptop by formatting one of the remaining 3 drives (windows 7 and ubuntu installed in 2 different drives). so the whole installation was successful & when i start my system i see both windows 7 option and ubuntu option but when i select ubuntu a ms-dos like black screen comes with a lot of lines & codes or something (i am sorry i have no clue of what it is) & it just stays like that. i waited for like 20 min. before i shut down the computer (by long pressing the power button) & restarted it. this time i selected windows 7 & it is working fine. So what could the problem be? If you need any more help like the system config or something then i would be very happy to provide it to you. 
           Thanks in advance.

---

### Post by Chandra sekhar on 2011-06-27
Can anybody help me please??

---

### Post by goldshirt9 on 2011-06-27
mmmmmm seems there is a lot of black screens at the moment after installation.
have you ever booted into ubuntu

---

### Post by Chandra sekhar on 2011-06-27
nope. cudnt boot even once. This thing happend the very first time i tried to boot itself.

---

### Post by dFlyer on 2011-06-27
Can you boot into a live desktop using the cd?

---

### Post by Chandra sekhar on 2011-06-27
and how do i do that??

---

### Post by dFlyer on 2011-06-27
Place a live desktop which is the standard ubuntu download in you cd and make sure your cd is set to boot off the cd when computer starts. Pressing the f10 or f12 key on some computers allow you to choose the cd for booting. If your doesn't than change your BIOS to boot off cd/dvd as your first choice.

---

### Post by Chandra sekhar on 2011-06-27
wil try & tel u in a minute

---

### Post by Chandra sekhar on 2011-06-27
Still the same... and here is the picture of the exact error...

---

### Post by Chandra sekhar on 2011-06-27
Somebody please reply...

---

### Post by Quackers on 2011-06-28
That's a kernel panic. Are the caps lock and num lock lights flashing as well?
You could try some boot options, like acpi=off or noapic or nolapic.
For how to use boot options see this thread
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)

---

### Post by Chandra sekhar on 2011-06-28
> **Quackers said:**
> That's a kernel panic. Are the caps lock and num lock lights flashing as well?
You could try some boot options, like acpi=off or noapic or nolapic.
For how to use boot options see this thread
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)


I am sorry but i did not understand anything from the link u provided. i am a total noob in this..
and no, caps lock and num lock lights are not flashing.
and one more thing... i have  a 64 bit processor. Could it be that i installed a 32 bit version of ubuntu and thats why it is not working?

---

### Post by Quackers on 2011-06-28
32 bit should be fine.
What pc are you using?

---

### Post by Chandra sekhar on 2011-06-28
Hp-g42.

---

### Post by Quackers on 2011-06-28
In the link below scroll down to the heading
"How to temporarily set kernel boot options on an installed OS (not wubi)"
and follow the directions. If you don't get a grub menu when booting, holddown the shift key whilst booting and then it should show up.

[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)

---

### Post by Chandra sekhar on 2011-06-28
Still not working.
whtever i do i still get the same black screen.

---

### Post by Chandra sekhar on 2011-06-28
Anybody?? please help...

---

### Post by Chandra sekhar on 2011-06-29
I am seriously in a need of help. Somebody help please...

---

### Post by Quackers on 2011-06-29
Which boot options have you tried?

---

### Post by Chandra sekhar on 2011-06-30
OK ppl, i am tired of this. i want to uninstall ubuntu from my comp. so i logged from windows 7 and tried to delete that particular drive so that i get it as unallocated space and then create it as a new drive. but it says it cant delete that drive.

pls tel me how ro delete that drive so that i cat get back my drive in NTSC format again.

---

### Post by Chandra sekhar on 2011-06-30
anybody care to reply??

---

### Post by Chandra sekhar on 2011-06-30
Is this community dead??
Guys... just this one help! please...

---

### Post by Chandra sekhar on 2011-07-01
OK ppl, i am tired of this. i want to uninstall ubuntu from my comp. so i logged from windows 7 and tried to delete that particular drive so that i get it as unallocated space and then create it as a new drive. but it says it cant delete that drive.

pls tel me how ro delete that drive so that i cat get back my drive in NTSC format again.

---

### Post by kptsuresh on 2011-07-01
HP laptops were not supporting for ubuntu OS.. Its better to use any other OS like windows... the problem is with drivers. getting drivers for ubuntu of hp systems is difficult..

if u still want to use ubuntu try new version 11.04..if its not supported 9.04 is the best suited version...even though some of the drivers not supported

---

### Post by kptsuresh on 2011-07-01
if u want to delete ubuntu drive follow these steps :

if u r installed inside windows uninstall on control panel..

otherwise the best way is to delete/format the drive by rebooting with any windows server cd/dvd or with windows 7 dvd..


I hope this works...

---

