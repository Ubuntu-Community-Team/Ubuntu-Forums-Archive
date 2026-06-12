---
title: "Ubuntu x86 Edition - Network Problems - Plz help!"
date: 2005-04-27
forum: Installation &amp; Upgrades
---

### Post by -`Orb!t@l´- on 2005-04-27
Hello all :).

A couple of months ago i had the strongest virus on my laptop i ever met during the years i'm using the internet,and trust me,those are quite alot of years :).I had Windows XP and a variant of the wellknown "Sasser Virus".From the moment i plugged  my utp in the laptop the other computers on our homenetwork couldn't get any connection anymore to the internet.Also the laptop couldn't browse the internet anymore,so basicly i was stuck.I gave the laptop to a specialist person for laptops who has told me the checksum of the bios didn't work so that i basicly had to flash my bios.I searched for it and called Compaq is they could help me.But they gave me the sad information that the bios couldn't be downloaded anymore,so i tried something else -> Installing Ubuntu x 86 version. 

The positive thing is that i can get the laptop on the internet again,also the others when the laptop is plugged in. BAD thing is that the internet on the other computers is going REALLY REALLY slow.My question is,can this problem be caused cause of that virus in my bios or is this a setting which isn't set right in ubuntu? Since (like i said) i recently installed linux i don't know alot bout it...

Plz help me out,
Greetz Orbi

---

### Post by Gallows on 2005-04-27
I 'm assuming that you have enough internet bandwidth and that your clients on your home network are not also virus ridden or attempting to download large amounts of data from the internet.... Windows update maybe?  Try turning off all the other (Windows?) machines and see if you get your bandwidth back - If you do then it look like sasser has twonked all your other machines too.

If not then it name resolution issue - Have a look at the DNS settings on the other (Linux?) clients on your home network and make sure they don't have any unreachable name servers.

BTW - It has *nothing* to do with a corrupt laptop BIOS - That sounds like BS to me

---

