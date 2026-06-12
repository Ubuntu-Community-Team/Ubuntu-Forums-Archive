---
title: "Old laptop boots from Win XP CD but not Linux CD"
date: 2014-04-01
forum: Installation &amp; Upgrades
---

### Post by Andrew_Largin on 2014-04-01
The Laptop is an RM CY25, 256Gb RAM, Mobile Intel(R) Celeron(R) CPU 1.40GHz.  It currents run XP Pro SP3 and runs like a dog, without legs.  It boots from the XP CD but I don't see the point in restoring it as it will at best run like a dog with 2 legs, if I'm lucky.

I have burnt 2 CDs, Slacko 5.6 PAE and Lubuntu 13.10 desktop.  These both work on my PC as live CDs.  When inserted in the laptop XP boots immediately without any prompt to run from CD.  I have also got a USB stick with Ubuntu 12.04.3 desktop which works on my PC.  I changed the BIOS to recognise removable drives (no USB option) and again nothing.

Any ideas will save a laptop from an untimely death and will be appreciated as it will stop me pulling out the little hair I have left.

---

### Post by Bashing-om on 2014-04-01
Andrew_Largin; Hi ! Welcome to the forum.

With the 256 [color=red]Gb[/color], you do mean Mega Bytes, no ?
With the limitation of 256 MB of ram, may I suggest you try Lubuntu minimal install :
[https://help.ubuntu.com/community/Lubuntu/Documentation/MinimalInstall](https://help.ubuntu.com/community/Lubuntu/Documentation/MinimalInstall)

Designed to run on that older hardware.

There are several threads on the forum in respect to keeping the old hardware alive and functioning well.
There are even lighter distributions (of linux) available that you will find will run admirably. 

[INDENT]where there is a will there is a way
[/INDENT]

---

### Post by Andrew_Largin on 2014-04-01
Yes 256Mb, a slip of the keyboard.  I didn't burn the minimal disc as I wasn't sure if it would run as a live CD, I wanted to see if it worked before installation.  I will try this but surely the other Linux CDs would try to install but they don't, the laptop boots from the HDD into Windows?????????????

---

### Post by Andrew_Largin on 2014-04-01
Minimal CD worked, loading slowly, still don't understand why others wouldn't

Thanks

---

### Post by Bashing-om on 2014-04-01
Andrew_Largin; Hey,

Glad to be of some small help.
How does Lubuntu perform for you ? 
Reason the others will not load is a lack of ram space in which to build the image for the file system. Even now Lubuntu would want more - 512 MB would give added performance too.

If you are satisfied with this as a solution, please mark this thread solved; 1st post -> thread tools. This aids others seeking a similar solution and as well helps keep the forum tidy .

[INDENT]as we go 
[INDENT][INDENT]merrily on our way
[/INDENT][/INDENT][/INDENT]

---

### Post by mastablasta on 2014-04-02
it could be a bad CD burn or bad download.

note that 256Mb is not enough to perform graphic install in lubuntu anyway. 

i suggest you also have a look at chrunchbang linux. it "saved" a maschine with similar specs.

one more thing - if oyu have a floppy disk you can use that to boot from and then choose USB to continue with the boot (investigate plop boot manager)

---

### Post by Andrew_Largin on 2014-04-02
I checked the RAM and CD integrity

Lubuntu loaded sysytem? and software, grub failed.  I used Guided- use entire disk for partitioning

I tried again and it was successful but when it rebooted it got stuck in a loop of the screen going blank for about 15 seconds, the mouse cursur then appearing for 15s etc.

I used the rescue option from the CD then got lost.

I have looked for documented assistance but can't find anything suitable.

I'll have a look at crunchbang and get hold of a floppy from somewhere.

I will give this computer away when it is fixed but it will be to someone who is not computer literate.  Thats why I like the look of Ubuntu as it justs looks pleasing with nice buttons so it will seduce a new user.  If I can get something to work on this I will upgrade the RAM and put the easiest to use ditro on that I can find.  I don't want to spend cash until it proves not to be a dead dog.  Just a bit of background for you.

Off to get crunchbang any ideas on Lubuntu?

---

### Post by Bashing-om on 2014-04-02
Andrew_Largin; Hey,

I often retrieve old hardware, and install some version of linux, and pass that computer to some deserving child.

In some instances I have had to go to a very low resource distribution Damn Small Linux (DSL). 1st time install of DSL can be confusing to set up the partitions, but documentation will get you through it. 
[http://damnsmalllinux.org/](http://damnsmalllinux.org/)
I have had no issues at all and am impressed at what and how well DSL performs on these old computers. But, my 1st choice is Lubuntu as a minimal install, and then add what packages I think the hardware can stand. ( as I am the more comfortable with  'buntu) There are those times that a Graphics driver is not available, and one must help with providing a "boot parameter(s)" - many many times "nomodeset" will do 'till I can do better.
However, there is no substitute for more ram, the more the better.

"tinycore" is also devoted to resurrecting old hardware, I have heard great things about it.
[http://distro.ibiblio.org/tinycorelinux/welcome.html](http://distro.ibiblio.org/tinycorelinux/welcome.html)

[INDENT]hey,
[INDENT][INDENT]it ain't dead
[INDENT][INDENT][INDENT]'till the motherboard gives up the ghost
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by Andrew_Largin on 2014-04-02
I think I have to give up on Lubuntu for this machine.  I loaded slacko-5.7-NO-pae and with a bit of fiddling it works but so far is a bit high maintenance for a novice.  Interestingly slacko-5.6-PAE didn't work.  I also tried crunchbang bit it wouldn't fit on a CD.  I got plop boot manager burnt a CD (I have no floppies left) and tried to load cruchbang from a USB stick, no joy.

I will try DSL and maybe tinycorelinux and see if they work.  Maybe more RAM if I think aby of them are suitable.

Interestingly Win XP which was loaded years ago ran OK without antivirus and streaming seems better than Slacko.  However all modern antivirus really hurt it and make it pretty unusable.

If I have any more adventures I will post them then close the thread but I haven't a clue how to do that so it could take as long as me loading Linux.

---

### Post by sudodus on 2014-04-02
If you want adventures, you can try the experimental ***9w*** installer and install Lubuntu Core Trusty with a non-pae kernel. Lubuntu Core is lighter than standard Lubuntu, and Trusty is the next version of Ubuntu, to become 14.04 LTS.

See this link (posts #88 and #89 and the following describe testing done with it). 9w is a debian installer that can install systems using very low RAM.

[http://ubuntuforums.org/showthread.php?t=2209683&page=5&p=12957586#post12957586](http://ubuntuforums.org/showthread.php?t=2209683&page=5&p=12957586#post12957586)

You can download it from this link

[http://phillw.net/isos/linux-tools/9w/](http://phillw.net/isos/linux-tools/9w/)

---

### Post by mastablasta on 2014-04-03
what is the GPU?

Chrunchbang is not for beginners. it is very light, but is also for intermediate users! i found that, eventhough install and use is very simple, i often needed command line and to edit config files.

Lubuntu should work and boot. Even though ram is low, computer should boot after install.

if you have time on your hand do this: [http://www.psychocats.net/ubuntu/minimal](http://www.psychocats.net/ubuntu/minimal)

this type of install shouldn't give any issues due to ram. Futrhetmore the suggested icewm widnows manager should work even under vesa graphics. 

also make sure to check the BIOS settings for graphics and let us know how much ram can be dedicated for the GPU. if 16MB or 32MB then all is good in that area.

as suggested you will want to explore boot options: [https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

---

