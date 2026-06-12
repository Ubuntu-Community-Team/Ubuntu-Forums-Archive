---
title: "Installation help"
date: 2012-02-19
forum: Installation &amp; Upgrades
---

### Post by xAGENTP6x on 2012-02-19
Hey guys. I have always been a windows guy due to my love for gaming and just TBH accepting the status quo of windows OS. I like the allure of ubuntu, what i can learn from a linux/unix based OS, and the sexiness of the design

Heres my situation

I bought a somewhat high end gaming computer, complete with tons of RAM, blah blah blah, and windows 7 home premium came pre-installed.

I have purchased valuable software compatible with only windows and installed them on the hard drive contaoning the windows OS
After all the aforementioned, i purchased an additional HDD and installed it (my old STOCK HDD WAS 5400rpm WD"green" which was a performance bottleneck, and my HDD seagate 1TB HDD SATA 7200 RPM 32mb cache is a bit of a performance upgrade

My question is: can i completely install a FULL version of ubuntu on my new HDD without it IN ANY WAYY affecting my wi dows 7 installation and the programs therein on MY PREVIOUS HDD? Essentially, i want a new OS on my new HDD and dont want to bother my old HDD in the process......how do i go about this task?

[B]I WANT ADVICE ON HOW TO INSTALL UBUNTU on a seperare HDD than windows 7, be able to thoroughly enjoy both OS's, yet not experience much priblems with either....how do i achieve that?

I already installed the ubuntu CD demo
Version but TBCH, the load time was feckin horrid, and it required 3 reboots to take me to am OS UI. First attempt was BIOS config, second was same, third was UserFriendly OS MENUS. 

So im asking: 
-is the load time shortened when the OS is installed directy on a HDD
-can i install ubuntu directly to a new HDD and leave the old HDD AND ALL CONTENT AND OS THERIN SAFE TO BE ACESSED LATER, 
If all the above suits my preferences, how do i execute this task?

---

### Post by Rodney9 on 2012-02-19
Nice guide for installing Ubuntu and yes it will go much faster installed.

[http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)

Rodney

---

### Post by MG&amp;TL on 2012-02-19
You can indeed partition your drive (allow a set amount of space for Ubuntu on the disk, choose between Ubuntu and Windows on boot).

Just a note: Ubuntu's graphics card support is not fantastic. What graphics card do you have? (it'll most likely work, but some can be problematic, typically the newer ones from the big brands)

I estimate at least ten times faster than from a CD when installed, and twice as fast from a USB to installed. Depends on your I/O speed.

---

### Post by xAGENTP6x on 2012-02-20
Hey everyone, I just need some help getting ubuntu up and runnning...here's my situation:

I just bought a new HDD, a 1TB Seagate SATA 7200 rpm Barracuda and want to keep my other main HDD the way it is with Windows 7 on it and all my games and software stuff, and install ubuntu onto my new HDD for something fun and unique to try out instead of windows.

First of all, is this doable? Like can I have two different OS's on seperate HDD's in the same computer, and choose which one to boot from perhaps in the BIOS? If so, could someone explain what I have to do to get the full ubuntu on my HDD? As of right now the HDD is setup in my computer but I haven't formatted it yet. To use ubuntu, should I set my new HDD to MBR or GPT? After the HDD is all formatted, how do I get the full version of ubuntu OS on that HDD? I could not find a simple option on the ubuntu website to just simply download the whole version of the OS, since all the downloads are geared to be trials on disk or USB so that noone accidentally or naively overwriting their current OS. Could someone direct me to the page where I would download the full version to put on my new HDD?

Also, I tried the trial version where you write the OS to a CD or DVD, and I found the OS to be extremely sluggish, and in fact wouldn't load, as the DVD bay would spit out the disk before Ubuntu completely loads, and then reverts to windows 7. Does Ubuntu typically run worse on a disk, cuz I wasn't too impressed. Hopefully it will run well on an internal HDD

Thanx for your help :)

---

### Post by uRock on 2012-02-20
Merged duplicate threads.

Ubuntu runs much slower from CD.

What GPU does your system have?

---

### Post by jinjanjaa on 2012-02-20
both of the above questions are possible..... you can either choose write grub to the first HD and boot both or use BIOS boot device priority, as someone suggested.......

both are possible......

for ubuntu though u must use "boot-repair" to write the boot record to the same disk/partition (so that it prevents it from writing boot info to MBR which u may not want)......

more info:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

the option to install in the same partition is in "advanced", 2nd or 3rd tab......

---

### Post by xAGENTP6x on 2012-02-20
Sorry for the duplicate threads, I thought I had not followed through with actually posting my topic last night.

Thanx for all the help thus far.

My GPU is a Radeon HD 6770 (although Windows seems to recognize it as the very similar 5770)
CPU: AMD Phenom II 1065-T six core @~2.9GHz

If you need to know any other specs, heres what they are:
[_[COLOR="Blue"]**My Specs**[/COLOR]_]("http://h10025.www1.hp.com/ewfrf/wc/document?docname=c02874899&cc=ca&dlc=en&lc=en&product=5097932#N1479")

I'm super new to anything that ISN'T windows, so the learning curve with ubuntu might be a little tough.

Ill check out those links right now, thanks for that Rodney9 and jinjanjaa

Another little tidbit: when using the CD, sometimes I would get locked up in a purplish color screen with "Ubuntu" displayed in the middle, and other times I would get locked up in a DOS-like screen, with no way out that I could figure out. Again, hopefully this works out better installed on an HDD.

---

### Post by xAGENTP6x on 2012-02-20
So i got it all set up now, didnt screw up anything on windows, and ubuntu is fully functional and seperate on its own HDD. All i have to do is press Esc when at a certain loading screen, and pick my seagate HDD!

I was cautious about the custom partition making. I ended up making 3 primary and one logical, and installed Ununtu at the root partition i made. After restarting, startup was MUCH quicker than on CD. 

AMD offered two patches for GPU...the original release patch for ubuntu, and one update that i for some reason couldnt install. Either way i can access some basics on my CCC, but my GPU CCC on windows offers SOOO muh more. I was impressed how easily it is to find and install my most basic drivers for GPU, printer, etc.

Im a little disappointed that the famous ubuntu "cube" requires some tinkering before i can use/see it :(

---

### Post by MG&amp;TL on 2012-02-20
> **xAGENTP6x said:**
> So i got it all set up now, didnt screw up anything on windows, and ubuntu is fully functional and seperate on its own HDD. All i have to do is press Esc when at a certain loading screen, and pick my seagate HDD!

I was cautious about the custom partition making. I ended up making 3 primary and one logical, and installed Ununtu at the root partition i made. After restarting, startup was MUCH quicker than on CD. 

AMD offered two patches for GPU...the original release patch for ubuntu, and one update that i for some reason couldnt install. Either way i can access some basics on my CCC, but my GPU CCC on windows offers SOOO muh more. I was impressed how easily it is to find and install my most basic drivers for GPU, printer, etc.

Im a little disappointed that the famous ubuntu "cube" requires some tinkering before i can use/see it :(


Brilliant! Well, I hope you enjoy it. :)

It used to be rather easy, but with the new interface, they've broken a few things. Still quite easy though, [this]("https://help.ubuntu.com/community/CompositeManager") guide worked pretty good for me. Just make sure you get the right section.

If everything breaks, you can always login to Unity2d and fix it there.

---

