---
title: "Upgrade 10.04 boots slow with blinking cursor, then text"
date: 2010-06-11
forum: Installation &amp; Upgrades
---

### Post by ddumanis on 2010-06-11
Hi, just upgraded to Lucid. When booting, I get a blinking cursor on a black screen for 30 sec. Then I get some flashes of text about UDEV. Finally, I get a desktop after about 30 more sec.

Any way to speed this up? I've already tried disabling my nonexistent floppy drive in the bios, but it didn't help.

All suggestions appreciated!

---

### Post by X-Windows on 2010-06-11
Same problem here on a dual boot clean install.

---

### Post by drs305 on 2010-06-11
One problem encountered early in Grub2 testing was a delay caused by Grub2 installations on the second hard drive. In this case, BIOS was set to boot off another drive first. G2 spent time searching for it's files on the first drive, and only when it didn't find them did it start searching the drive on which G2 was actually installed. The delay was usually in the 30 second to 2 minute time range.

If this might be the case with your setup, change the BIOS boot order so that the drive with the Grub2 installation is the first one in the list. You can usually enter the BIOS setup by pressing a function key (F1-F12), the DEL or ESC key during the initial boot. Often the computer monitor will provide information on which key to press to enter the BIOS setup.

If you see the Grub2 menu and then the delay occurs the problem does not lie with Grub2 but with something that is happening after Grub2 has passed control over to the kernel. There may be an option that could be placed in the Grub settings but we would need more information to make that determination.

---

### Post by X-Windows on 2010-06-11
Don't know about the OP, but the delay is there and I only have one hard drive.

---

### Post by asphixmx on 2010-06-12
I have the same problem. I am using a Dell XPS laptop. I have installed: Linux Mint (based on Ubuntu 10.04), Kubuntu 10.04, Ubuntu 10.04. Have tried with dual boot (windows/linux) and linux only. Same result always. A blinking cursor after grub, about 30-45 seconds later, the boot continues normally. Anyone has a solution for this? Thanks.

---

### Post by X-Windows on 2010-06-12
*bump

Seems several of us are having this issue. Anyone know of a fix?

---

### Post by guyguyguy on 2010-06-24
another bump.
To clarify - I'm guessing all others have the same issue 
We get the cursor blinking AFTER we select the OS from the grub menu. 
In my case at least the problem is only with the ubuntu boot. The winXp boots immidiately

Thanks
Guy

---

### Post by rob45 on 2010-06-24
what bugs me is the fact that the boot screen appears....it shouldn't if theres only 1 OS..Im running 9.10....n0t 10.04.

---

### Post by asphixmx on 2010-06-24
Ok, a feedback: Had the same problem (as I said in my last post). I had to change the CDRW/DVD combo on my laptop, because I upgraded to a DVDRW. I noticed the problem is gone now. Why? I don't know. The only thing I know is since I changed the optical unit, the problem is gone.
Maybe the problem is something about the SATA interface and with some units (optical or maybe hard disk). Definitly it is a bug in the kernel... maybe it keeps looking for the boot device when we select the Linux OS instead of Windows (in a dual boot), and keeps looking for something for those 30 secs... until it continues. 
Maybe it could be a clue to someone who knows more than I know about Linux. Hope it is fixed soon.

---

### Post by lechien73 on 2010-06-24
As a test you could try changing the BIOS setting for your SATA controller to either "Compatibility" or "ATA" mode instead of "AHCI".

Note if you have a dual-boot system that changing this setting will likely stop Windows from booting until it's changed back, but this will confirm if it actually is a SATA driver problem.

---

### Post by Hack.The.Pow. on 2010-10-18
Anybody ever figure out a solution for this?

It never happened when I ran 10.04 but ever since I updated to 10.10 its been happening.  

Cursor blinks for about 10-15 seconds.  Then it says something about my WiMax working and then something about cannot find usable firmware image and that it can't bootstrap the device.  I would post the full output but it goes by in about 5 seconds.

After this the ubuntu 10.10 splash image comes up.  It then has an error message comes up, something about polipo.  It goes by in about a second so theres no chance that I could read it.

I also get a standard verbose shutdown message at shutdown.

I have inserted quiet into my /etc/default/grub file with no luck.

The messages don't cause any problems but I like to have a clean bootup and shutdown splash with no odd messages.

---

### Post by trazalca on 2010-10-18
Me too!! i upgrade from 10.04 and now, when the maverick boot, the cursor blink for a few seconds, a text appear, but i cant read it, and then the ubuntu splash come.... someone can help me for fix please?? Thanks

---

### Post by asphixmx on 2010-10-18
I am still in 10.04. No solution yet. My cursor blinks for about a minute, then boots normally. I think it's something with the dvd drive, because when I replaced it, the problem was solved...for a few days. Then it came back.

---

### Post by Hack.The.Pow. on 2010-10-18
I just used this tutorial and it solved all of my woes.

[http://idyllictux.wordpress.com/2010/04/26/lucidubuntu-10-04-high-resolution-plymouth-virtual-terminal-for-atinvidia-cards-with-proprietaryrestricted-driver/](http://idyllictux.wordpress.com/2010/04/26/lucidubuntu-10-04-high-resolution-plymouth-virtual-terminal-for-atinvidia-cards-with-proprietaryrestricted-driver/)

hopefully it will help you as well

---

### Post by asphixmx on 2010-10-19
> **Hack.The.Pow. said:**
> I just used this tutorial and it solved all of my woes.

[http://idyllictux.wordpress.com/2010/04/26/lucidubuntu-10-04-high-resolution-plymouth-virtual-terminal-for-atinvidia-cards-with-proprietaryrestricted-driver/](http://idyllictux.wordpress.com/2010/04/26/lucidubuntu-10-04-high-resolution-plymouth-virtual-terminal-for-atinvidia-cards-with-proprietaryrestricted-driver/)

hopefully it will help you as well

My laptop has Intel graphics. I had the problem that is solved on the link you provided, but the problem was on my desktop computer with nvidia graphics and the problem was not the blinking cursor, it was only the ugly plymouth in low res at boot.

---

### Post by Hack.The.Pow. on 2010-10-19
> **asphixmx said:**
> My laptop has Intel graphics. I had the problem that is solved on the link you provided, but the problem was on my desktop computer with nvidia graphics and the problem was not the blinking cursor, it was only the ugly plymouth in low res at boot.

Oops Sorry!  My apologies then for getting your hopes up.

---

### Post by thebarisaxkid on 2010-10-19
> **X-Windows said:**
> *bump


Can someone tell me what bump means?!  I keep seeing it everywhere and I have no idea what people are talking about.

---

### Post by drs305 on 2010-10-19
> **thebarisaxkid said:**
> Can someone tell me what bump means?!  I keep seeing it everywhere and I have no idea what people are talking about.

It's just a way of moving a thread back to the top of the list by adding a new post so viewers will see it.

Forum protocol requests users wait at least 24 hours before 'bumping' a thread.

---

### Post by asphixmx on 2010-10-20
> **Hack.The.Pow. said:**
> Oops Sorry!  My apologies then for getting your hopes up.

No problem! :) I know someday the bug will be fixed... I am patient :P

---

### Post by jeetendra.choudhary on 2010-10-20
Hi All,

I am also facing same issue and after trying that tutorial [http://idyllictux.wordpress.com/2010...ricted-driver/]("http://idyllictux.wordpress.com/2010/04/26/lucidubuntu-10-04-high-resolution-plymouth-virtual-terminal-for-atinvidia-cards-with-proprietaryrestricted-driver/") the splash screens comes but instead of ubuntu logo at centre of screen i am getting the ubuntu 10.10 text and the dots blinking below it. i am having ATI graphics card. Can some one put some light in this.

Thanks & Regards
Jeetendra

---

### Post by thebarisaxkid on 2010-10-22
> **drs305 said:**
> It's just a way of moving a thread back to the top of the list by adding a new post so viewers will see it.

Forum protocol requests users wait at least 24 hours before 'bumping' a thread.

Ahhh, clever!

---

