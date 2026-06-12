---
title: "Ubuntu install problem - PC goes idle"
date: 2008-02-28
forum: Installation &amp; Upgrades
---

### Post by klaztaz on 2008-02-28
Hi all,

could you please shed some light on my annoying problem?

i downloaded Ubuntu 7.04 and now 7.10 and again the same thing happens.

I enter the menu and select Start and Install Ubuntu when i boot from the CD.

The screen them shows me some messages like kernel alive if i remember correctly and then the screen pop-up comes up telling me that the monitor has no signal (meaning its either disconnected which is not or basically there is nothing happening) and the CD reader stops spinning. I waited for quite some time but it seems to just sit there and the screen just goes to sleep mode.

I also tried the safe graphics card option just in case it has something to do with my graphics card but unfortunately it doesn't.

Could you please advise me on what i haven't done or not doing?

I am using the Intel AMD 64-bit 7.10 version.

My PC is:

AMD 939socket +4200 Dual Core (not O/C)
ASUS A8 N32 - SLI Deluxe
3GB ram
NTFS hard drive but also tried with FAT32
FireGL V5100 GPU card


Also another quick question, can i install Ubuntu on an NTFS hard drive?

---

### Post by Pumalite on 2008-02-28
Download from here:
[http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download)
Follow this:
[https://help.ubuntu.com/community/BurningIsoHowto?highlight=%28burn%29%7C%28](https://help.ubuntu.com/community/BurningIsoHowto?highlight=%28burn%29%7C%28)
Do md5sum on the iso, burn at 4x or less, check for CD integrity before install.

---

### Post by klaztaz on 2008-02-28
I did complete a CD integrity check last time on the 7.04 version and everything was fine but no on the 7.10 version.

But i never did a md5sum before.

Thanx a lot for the help, ill give it a go.

---

### Post by klaztaz on 2008-02-28
Ok,

i re-downloaded Ubuntu, installed the md5sum program and run it as well, everything good so far. I then burned the image file at 8x because 4x wasnt an option.

I restart and boot from the CD and choose to check the CD for defects. When i press it the kernel loads to 100% and my PC just restart again.

I also tried to install which does exactly the same thing. It loads the kernel to 100% and then diaplys some letter like' kernel alive' and some wird line about some tables 1000000 (something like that) , the screen goes black and shows 'No signal' and finally the PC just restarts.

Arggggg!
Whats wrong?

---

### Post by Pumalite on 2008-02-28
Probably hardware incompatibility. Nevertheless set your BIOS to default values and try again.

---

