---
title: "Trouble installing"
date: 2008-10-01
forum: Installation &amp; Upgrades
---

### Post by Saedin on 2008-10-01
I'm completely new to linux...I download ubuntu-8.04.1-desktop-i386.iso, burned it to a disk, booted from it and tried to install ubuntu. 

It opens up "BusyBox v1.1.3(Debian 1:1.1.3-5ubuntu12 Built-in Shell (ash)"

Then I get the message: "revalidation failed (errno=-5)

Followed by 
"exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x2 frozen"
"cmd a0/00:00:00:24:00/00:00:00:00/A0 Tag 0 pio 36 in"
"status { DRDY }

which just repeats over and over...

I'm on:

Dell Vostro VOSTRO_200
Intel Pentium Dual CPU
E2160 @ 1.80GHz
1.79 GHz, 1.99 GB or RAM
Disk Drive: SAMSUNG HD161HJ
Display Adapter: Intel G33/G31 Express Chipset Family

---

### Post by Saedin on 2008-10-02
If someone could even just point me in the right direction to look for a solution, I'd be grateful... I'm completely new to this and I don't even know where to begin.

---

### Post by Saedin on 2008-10-02
The same thing happens when I try with ubuntu-8.04.1-desktop-amd64.iso

---

### Post by kruisa7 on 2008-10-02
> I'm completely new to linux...I download ubuntu-8.04.1-desktop-i386.iso, burned it to a disk, booted from it and tried to install ubuntu.


Did you check the md5 checksum before burning the CD?

---

### Post by Saedin on 2008-10-02
Check it for what? I'm not sure what you mean...

---

### Post by iponeverything on 2008-10-02
When boot with the CD, in the initial menu you will see a menu option 
that says something like "check cd for errors" -- choose it.

---

### Post by Saedin on 2008-10-02
I tried that, it did the same thing...it does the same thing with install, demo and check cd for errors.

---

### Post by roberto.eiberle on 2008-10-02
seems there is a confusion at boot, make sure to select cd as startup option in setup bios and disable flopies, flashcards etc.

---

### Post by Saedin on 2008-10-02
Well, I can get to this step: [http://www.psychocats.net/ubuntu/images/installinghardyplus02.png]("http://www.psychocats.net/ubuntu/images/installinghardyplus02.png") but after that I get the errors I mentioned in the first post. I did select cd to boot, but how would I disable flopies and flashcards?

---

### Post by roberto.eiberle on 2008-10-02
press f4 and try OEM setup, that was the only way I got it working on a packardbell laptop

---

### Post by klambert on 2008-10-03
i have this exact same error if u get it to work, let me know how please

---

### Post by daGeneral on 2008-10-03
I have the same exact problem as well. My error messages are:

[92.435152] ata2.00: revalidation falied (errno=-5);
[92.530816] ata2: COMRESET failed (errno=-16);
[92.563881] ata2: exception Emask 0x1 SAct SErr 0x0 action 0x0 t4;
[92.563933] ata2: irq_stat 0x40000008;

I have tried 32bit and 64bit versions. I managed to start live cd once and thats it. whatever i do i always get the same error messages. I have a clevo M57 based laptop.

so far nothing anyone has told me works. so much for the great ubuntu.

---

### Post by daGeneral on 2008-10-03
btw I managed to install it as a vista application and i dont want it that way

---

