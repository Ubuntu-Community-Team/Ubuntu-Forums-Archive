---
title: "Ubuntu for Intel Atom processor"
date: 2011-09-08
forum: Installation &amp; Upgrades
---

### Post by abhimohpra on 2011-09-08
Hello experts,

 I knew there was edition ubuntu 10.04 netbook remix for Intel Atom processor. Now of i am not able to find out suitable release of ubuntu remix. Read somewhere that Ubuntu is no more supporting remix releases.
  Which is the best suitable ubuntu for the Intel atom processor?

Thanks,
Prasad

---

### Post by mikewhatever on 2011-09-08
10.04 had a netbook version, with various GUI modifications, but never was it specifically tailored to the Intel Atom CPU. The 10.04 netbook edition is still available.
[http://releases.ubuntu.com/10.04.3/](http://releases.ubuntu.com/10.04.3/)

As of Ubuntu 11.04, the netbook edition has been cancelled because the new Unity interface was deemed to suite all form factors - netbook, laptops and desktops alike.
If you wish to use 11.04, download the desktop edition.

---

### Post by uRock on 2011-09-08
I am using the 32bit version on ubuntu 11.04 on my netbook. I was running the 32bit 10.04 in the past. As mentioned, there isn't a different version for the Atom processor.

---

### Post by abhimohpra on 2011-09-08
Thanks for your replies.

Yes currently i am using UBUNTU 11.04 on Atom processor. 

Initially it started well. Later it started creating lot of problems with grub loading, computer hangs, metacity loading. even sometimes it does not detects hard drives. 
After repetitive trials sometimes it loads. But, next time you can not gurentee to load properly.

I tried many grub fixer (grub recovery tools), live CD and error related helps but nothing works.

The issues get vary all the time so I am not able to fix it. 
I have also tried upgrading 11.04 latest kernel but then that completely fails my grub loader.

So, finally i thought to specifically go for Atom dedicated version if assume 11.04 needs lot of power issues to run the application.

I confused whether to downgrade the ubuntu version or do i have any hardware problems!

Could you please suggest the right path to me?

Thanks in advance
Prasad

---

### Post by mikewhatever on 2011-09-08
As already mentioned, an 'Atom dedicated version' does not exist. If you want something that needs less power, try Lubuntu.
[http://lubuntu.net/](http://lubuntu.net/)

---

### Post by uRock on 2011-09-08
What are the system specs of your Netbook? 

From looking at your system's symptoms I am thinking there is a hardware issue, but it is hard to be sure. 

Have you been having these problems since you first installed ubuntu or was there a moment where your system started giving your these troubles?

---

### Post by abhimohpra on 2011-09-08
Hi,

Specification of the system is intel atom n270, 2GB RAM and 36GB harddisk.

When I freshly installed UBUNTU 11.04(/10.10) (Without install-time downloads) the system was running smoothly. I never upgraded system with the fear that grub with new upgraded kernel will give me a problem. I had bad experience after updating the system previously. 

But things are not still going well....

Initial boots went well. I only made change in grub by adding a line for my egalax touch screen (This is mandatory for me to add touch screen considering my application). I upgraded grub and everything worked well for one or two days.

After that suddenly it started creating trouble like below:
1. It ends to grub> prompt 
2. only read error sometimes
3. Sometimes it is checksum error
4. Today it did not accept hard drive at bios device loading time.

I tried to figure out problems by searching google and applied relevant solutions but that worsen the situation.

Any idea what could be the problem?

Prasad

---

