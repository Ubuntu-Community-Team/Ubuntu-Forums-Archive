---
title: "Ubuntu install freezes at hardware detection!"
date: 2005-10-16
forum: Installation &amp; Upgrades
---

### Post by henrypootel on 2005-10-16
I was very excited to get 5.10 onto my PC at home, so i threw the cd in, and started up.
I entered 'expert' at the prompt, and watched all the pretty messages go past, and then...... that was it.
The scrolling text stuff stopped just after saying something abour using a PS2 mouse, and some stuff about USB hubs etc...
And it just sits there. I tried unplugging some devices, and it displays everything that is happening(ie. USB hub has disconnected etc...).

I have tried the install using the 'noapic' 'nolapic' and 'acpi=off' arguments, as well as just a standard install, but none of them work.

It's running on a MSI Mega 865(Intel 865 chipset), with a p42.6GhzHT CPU, 1536 megs of RAM, Geforce4MX graphics card, and a Seagate Barracuda 200Gb SATA HDD.

Can anyone help me?
I know that i can just install hoary(which installed without a hitch, and worked fine for me for several months), and then upgrade using the cd, but i would much rather do a 'clean' install.

---

### Post by henrypootel on 2005-10-17
Can somebody please help me.
After further investigation:
-The install cd for hoary works fine.
-the live cd for Breezy has the same problem as the install cd.
-My SATA drive seems to be detected fine

Can i possibly grab some driver or something off the hoary cd and put them on the breezy one and use that?

Please help me, i miss my ubuntu!

---

### Post by keron on 2005-10-18
This is a stabb in the dark: When I tried to install ubuntu or gentoo on my server they both freezed during hardware detection. It seems to me that it does that if there are no primary IDEs (I hade removed my old PATA disks) but secondary ones (I still needed the CDROMS and didn't bother to switch IDE). The solution? I didnt figur this out 'till it was too late, so I just plugged in a pata and did the install on the sata, and since it was a server I removed the cdrom and pata after the install... But I do belive that just moving the CD to the primary IDE would have done the trick...

Hope this helps.

---

### Post by henrypootel on 2005-10-18
[QUOTE=keron]This is a stabb in the dark: When I tried to install ubuntu or gentoo on my server they both freezed during hardware detection. It seems to me that it does that if there are no primary IDEs (I hade removed my old PATA disks) but secondary ones (I still needed the CDROMS and didn't bother to switch IDE). The solution? I didnt figur this out 'till it was too late, so I just plugged in a pata and did the install on the sata, and since it was a server I removed the cdrom and pata after the install... But I do belive that just moving the CD to the primary IDE would have done the trick...

Hope this helps.[/QUOTE]

Hmm.
That sounds like a possibility.
I will give it a try tonight.

Thanks heaps.

---

