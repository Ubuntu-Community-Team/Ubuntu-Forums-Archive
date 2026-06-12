---
title: "Base Installation Error: Return 1"
date: 2006-02-28
forum: Installation &amp; Upgrades
---

### Post by Arkolm on 2006-02-28
Hello everyone,

Yesterday I got a new laptop which is an HP Pavilion zv6000, on which I was attempting to install Ubuntu. I decided on the i386.iso install and I downloaded it, md5 checksummed it, and burnt it at 4x. The HP has XP on it, so I created a 12gb partition on it for Ubuntu. 

At first when I went to install it the screen would go black. After hunting the forums to find the problem rather than ask it for the fifteenmillionth time I found that linux vga=771 worked. At the creating of the partition for linux I tell it to make 11gb at the end in logistic FAT32, and the remaining as swap. It starts up and then I get the error: Base Install Error, Return 1. This is not verbatium as I don't have the laptop with me here, and if more is needed I'll post it when I get home. This was after a few hours of me trying to figure everything out, so I looked and looked for a solution, and I'm sure it's right under my  nose, but I can't find it! 

Anyway, what should my next step be? If more info is needed, please let me know.

Thank you

---

### Post by Arkolm on 2006-03-01
If this matters the laptop has a Fujitsu MHT2080AT PL HDD that's 80GB. GB of RAM, Athlon 64 3200+. Ran through install again and got the same base install error, I'll check here and try again tomorrow.

---

### Post by Arkolm on 2006-03-03
Sorry to bump this again but I'm at my wit's end. I reburnt the cd at 2x and got the same error yet again;

Base System Installation error The debootstrap program exited with an error (return value 1). Check /target/var/log/bootstrap.log for details.

I am using a widescreen athlon 64 so I tried again using 

linux vga=771 acpi=off noapic nolapic

though to be fair I dont know exactly what apic and lapic is, this was just a suggestion I found. Same resulting error.

So do I have to give up trying to install ubuntu, is it a lost cause? I very much want it to run :( 

Anyway, thanks for any help.

---

### Post by nevyndweomer on 2006-03-03
Hi 

well i am completely out of my depth here and a real noob but just one thing in your post struck me 

you said you downloaded the i386 image and your CPU is an Athlon 64  

Isn't the Athlon 64 a 64bit processor? 
and I think there is a different image for 64bit cpu's? 

now i could be completely off track here so please don't flame me but it is what I would try if I were you and really stuck ;)

good luck I hope you get more than I have had so far with this thing 

Nevyn

---

### Post by nevyndweomer on 2006-03-03
Hi again 

here is the bit from the install site  
I think you do need the 64 bit version 

64-bit PC (AMD64) install CD
For computers based on the AMD64 or EM64T architecture (e.g., Athlon64, Opteron, EM64T Xeon). It is not necessary for all (even most) processors made by AMD -- only their 64 bit chips.

Good Luck 

Nevyn

---

### Post by Arkolm on 2006-03-03
Thanks for the reply,

I actually originally got the 64 bit version and recieved problems, after some investigation I found out that the i386 will work fine and that wine (which I need, at least for now) is much friendlier on i386. That's why I went with i386 rather than staying with the 64bit version. If I'm wrong and I must use the 64bit let me know, but from what I've been reading I might as well use the i386 for now.

---

### Post by KansasJoe on 2006-03-03
I had a little problem installing as well...here's what i did....dl from a different source and burned it to a CD-R at 4x....i was using a CD-RW at 8x....not sure which one of those was the problems but once i did that it magically worked.

---

### Post by Arkolm on 2006-03-03
Which other source did you use? I may be just slow but all the links I went to seemed to come back to the here. Or do you mean just a different mirror from here?

---

### Post by R3linquish3r on 2006-03-03
[QUOTE=nevyndweomer]Hi 

well i am completely out of my depth here and a real noob but just one thing in your post struck me 

you said you downloaded the i386 image and your CPU is an Athlon 64  

Isn't the Athlon 64 a 64bit processor? 
and I think there is a different image for 64bit cpu's? 

now i could be completely off track here so please don't flame me but it is what I would try if I were you and really stuck ;)

good luck I hope you get more than I have had so far with this thing 

Nevyn[/QUOTE]

386 will run on a 64 system. I'm doing it now :)

---

### Post by Ptero-4 on 2006-03-03
Arkolm. By the extent of your issues I can recomment two things.

1> Burn the iso at 1x. Sometimes those HP bricks get nasty at anything faster than 1x when burning isos.
2> If that doesn't fix your issue. Consider yankin that HP brick of a laptop you got. Those HP $PCs are hostile towards non-M$ apps and OS's.

---

### Post by KansasJoe on 2006-03-03
meant different mirror

---

### Post by Arkolm on 2006-03-03
[QUOTE=Ptero-4]Arkolm. By the extent of your issues I can recomment two things.

1> Burn the iso at 1x. Sometimes those HP bricks get nasty at anything faster than 1x when burning isos.
2> If that doesn't fix your issue. Consider yankin that HP brick of a laptop you got. Those HP $PCs are hostile towards non-M$ apps and OS's.[/QUOTE]

I'll try reburning and redownloading it, and I can't really get rid of it, it's pretty nice and it cost a bit :p worst comes to worst I may have to look at a different flavor though I really don't want to!!

Okay, I'll try a different mirror Joe.

---

### Post by Arkolm on 2006-03-04
I suppose I'm about given up, I've been trying to get this installed all day. I re downloaded it from a german server, did a sum check it was good, burnt the disk at 1x on a different computer and verified it and it came out fine. But I can't get past this evil debootstrap program exit error :(

I tried installing it as a server, but not luck, still got the same error. No one knows what causes it? Ah well, maybe Ill try kubuntu and swap to ubuntu after it's installed, how difficult is that? I'd prefer gnome.

Edit:

I found this

[http://www.ubuntuforums.org/showthread.php?t=132424&highlight=debootstrap+program+exited+error](http://www.ubuntuforums.org/showthread.php?t=132424&highlight=debootstrap+program+exited+error)

I'm going through trying them, I couldn't use the -d1 with my cdrom, I got an error, I'm going to try using a different language now.

Edit II:

Changing the language didn't work, but changing the filesystem to EXT 3 worked, at least as far as to get past the debootstrap error. It's doing remaining packages now and all looks clear. I had it as FAT32 because I'm dual booting with windows, and I was informed that if I want to have the two partitions communicate I should have the linux parition as FAT32, and not EXT3. Ah well, maybe I can reinstall it FAT32, if this is true.

---

