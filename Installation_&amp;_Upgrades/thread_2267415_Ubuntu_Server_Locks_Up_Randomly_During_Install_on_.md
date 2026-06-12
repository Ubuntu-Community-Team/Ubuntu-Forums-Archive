---
title: "Ubuntu Server Locks Up Randomly During Install on Penguin Computing Servers"
date: 2015-03-01
forum: Installation &amp; Upgrades
---

### Post by soundblastdj on 2015-03-01
Yesterday I bought four Penguin Computing Servers off of Craigslist.  After getting them hooked up, I went to install Ubuntu Server with a freshly burned copy of Ubuntu Server 14.10 x64 (these servers have AMD Opteron processors).  I got to "Loading Additional Components" and then it locked up on me.  At first, the install just stopped, then the keyboard stopped responding and the only way to shut it down was to do a hard power off.  It wouldn't respond to Ctrl + Alt+ F2 or anything else.  I though it might just be a bad disk or download so I redownloaded the iso file and burned it to a new disk.  Again, around 5 percent of the way through "Loading Additional Components" it locked up on me.  I spent all of last night messing with the BIOS trying to see if there was some setting messed up there, I tried multiple versions of Ubuntu (Server 14.10 x86, Server 14.04 x64 and x86, Server 12.04 x64) on many disks.  I don't have any more things to try.  I'm out of ideas.  I'm going to check to see if I can install a desktop version of Ubuntu, but I don't have high hopes.

Anybody know what might be causing this and any potential solution? I'm open to them all.

---

### Post by soundblastdj on 2015-03-01
As expected, the Ubuntu Desktop install didn't fare any better.  It partially loaded the desktop, the DVD stopped reading, and the server locked up again.

---

### Post by tgalati4 on 2015-03-01
What was running on these servers previously?  How old are they?  Perhaps PSU problem.  Have you cleaned them up and reseated the internals?

---

### Post by soundblastdj on 2015-03-01
> **tgalati4 said:**
> What was running on these servers previously?  How old are they?  Perhaps PSU problem.  Have you cleaned them up and reseated the internals?

I don't know a whole lot about these particular models.  The guy who sold them to me had already wiped the drives.  The BIOS seems to be from around 2006.  I can almost definitely rule out power supply problems because I can install Windows and it won't lock up (although after the install, I get no video...) and I can sit at the BIOS configuration screen for the whole day with no problems.  I haven't done a complete cleaning of them yet, but the processors have been reseated along with the RAM.  I also did a test where I installed Ubuntu on a desktop and dropped the hard drive into the server.  It seemed to boot, but as soon as it started loading the OS I lost all video.  The monitor didn't say no signal, but it was a black screen.  When I get the chance, I am going to try to find the IP address and SSH into it (I had the forethought to install SSH during the install).

I've only had these since last night, but I've spent close to 20 hours working on them.  I have people who depend on the NAS that one of these is replacing.

---

### Post by tgalati4 on 2015-03-01
Make a LiveUSB of 14.04, 64-bit and try booting from that.  When you get the boot menu, choose "Check media files" to make sure the USB stick files have passed their individual checksums.  If the USB stick checks out OK, then try booting in Safe mode or Compatibility mode, since most servers have minimal graphics cards.  If that works, then try installing.  If you can't get it to boot into a Live Session, then don't bother with installation.  It's possible that only 12.04 will run, but I think you have some bad disks that are tripping up your installation.

---

### Post by soundblastdj on 2015-03-02
I'll try with USB when I get home later today. I forgot that theses were built to run RedHat Linux, although when I rand the install disk it locked up the same way that the others did (though that could be because the ISO came from a questionable source). One is a Relion 140 and the other 3 are Altus 1650. 

Why do you think that 12.04 will work? What's different about it?

---

### Post by tgalati4 on 2015-03-02
I know for IBM servers, Red Hat is a Big Endian distro and Debian/Ubuntu is Little Endian and the firmware of the server must be able to detect Big or Little Endian to be able to load the boot image.  Firmware updates to the servers can often fix this detection problem.  So a server that is "certified" to run Red Hat may not run Debian/Ubuntu without a firmware upgrade.  

Check Penguin's website for firmware files and try to perform an update if one is available.  The alternative is to run Fedora and spend time in another forum.  Because of the age of these servers, the CD readers that you are using could be dirty and worn out.  Try taking one out and gently cleaning the optics with a cotton swab.  Lube the rails with silicone grease and describe how much dust has accumulated.

Used servers require quite a bit of "hands-on" care to get them running again.  So although they may be cheap, they are not free.

---

### Post by MAFoElffen on 2015-03-04
See attached, from the Penguin site... CentOS, Rhel, SUSE ... and Ubuntu. So the vendor does say it supports running Ubuntu 64bit.

But, at the moment, they do not seem to run anything well do they? The following are just observations and ideas...

Having said that... during the install CD's, <cntrl><shift><F2> gets out to a shell, where as from a normal boot, it would have been <cntrl><alt><F2>...

If from an install cd, if you give it a boot option for "--verbose debug nosplash" and pop over to the shell, you might be able to see if it is booting the kernel, then during the device queries, if it is hanging on a certain device.

Their boards are muliple procs with multiple memory controllers. I'm not familair with their site and don't know where their guides are, but this is what I ssspect... Open up the covers and look at the memory modules. Look to see that they are distributed in the banks evenly in the banks, distributed between the processors. As with some boards, and how they describe their boards, it sounds like it has a separate bank for each proc. Of course you would need to confirm that yourself. On a new to you server, this might be un-noticed if this is setup out of kilter or not.

Next is the optical drives... if 2006, check to see if CD or DVD drives and which format of. Present ISO tip just over 700MB, which may be a problem if it has an older CD ROM drive in it.

---

### Post by soundblastdj on 2015-03-04
I also posted on the FreeNAS forums, and between there, here, and some of my own tests, I have come to the conclusion that they are actually overheating, which is causing the whole server to lock up.  I had noticed that the installations ran for longer after I had unplugged the server for the day and left it in my unseated basement, but it would continue to lock up less then half way through the install. I pulled the top cover off and set a box fan on top of the server on its hughest speed and it made it almost entirely through the install before locking up. 

Also, the RAM is distributed evenly. There are 24 GB entirely filling the two banks with even amounts in each. 

The disk drive is DVD, it says it on the front and I have only been using DVDs. (With the exception of a few flash drives)

---

### Post by tgalati4 on 2015-03-04
Perhaps you need to clean off the old heat paste and apply some Artic Silver or some decent ceramic heat paste.

---

### Post by MAFoElffen on 2015-03-04
> **tgalati4 said:**
> Perhaps you need to clean off the old heat paste and apply some Artic Silver or some decent ceramic heat paste.
+1

That's exactly what came to mind as I was reading the OP's post. <-- Especially if rackmount cases.

+2 on the silver heat paste... I experience this heat paste problem on 1U cases and old servers. The white ceramic heat sink paste "sets" with heat and gets hard. On 1U cases, when you pull them out of the racks, such as these did when pulled, sold to you, transported to your home... would be suspect. Those cases tend to flex during that, popping the integrity of the heat sink contact. That causes an NMI error when it overheats.

The silver heat sink paste, stays soft and pliant... and is my forgiving. I seem to have learned (the hard way) to buy the silver heat paste in the large tubes and keep them on-hand.

Curios how many cores your opterons have... and how many fans.. (Most my 1U cases have at least 8 mini-fans...)

---

