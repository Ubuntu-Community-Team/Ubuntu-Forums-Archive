---
title: "installation of 6.10 hangs at 76%"
date: 2007-01-31
forum: Installation &amp; Upgrades
---

### Post by fat buddha on 2007-01-31
Hi - a newbie here

I'm trying to install Ubuntu 6.10 on an old PIII system with a 6Gb drive. I've set the install to completely delete old files and use a single partition. The install seems to chunter along fine and then stops at 76% completed - the disk partition is only shwoing 38% full - and the whole machine is locked out. No keyboard action, no mouse action (cursor moves but nothing happens when you click), no disk or CD light flashing away.

I've tried this twice now - 76% and stalls.

Have I hit a bad sector on the disk - it was working fine with Win98 - or is the install CD corrupted at this point of file transfer. 

any ideas out there??

thanks

---

### Post by commonplace on 2007-01-31
Did you check the disk for defects (it's an option on the boot menu)? It it shows problems, try burning again but at a lower speed, or using a better disc. If it tests okay, then that's obviously not the problem. You can try running the memory test (also on the boot menu), too.

With all that said, I've run into the same problem before, and can't really state any specific fix. Usually it's hardware-related, though, but that's vague and could be anything, I realise.

Does booting the disc as a live CD work okay, and just the actual installation process fails?

/Kevin

---

### Post by fat buddha on 2007-02-01
hi guys

I've tried installing this on a different PC but with basically the same config of memory and CPU except the hard drive is different (10gb as opposed to 6Gb).

guess what - same problem - install hangs at 76%.  now I've run another integirty check on the CD and done a MD5 sum check and they pan out fine.

what's going on here??

maybe I'm being impatient and it's not hung at 76% but is just being very very very slow??  but i don't see that as the keyboard and mouse are hung as well - ony way to get action is a reboot which naturally takes me back to square 1............

live CD works fine...

---

### Post by roberthr on 2007-02-01
Happens to me a lot. In 5 instalations, 4 were defective. Two were solved by replacing CD-ROM drive, one by putting in another VGA card and one... well I've spent already 3 hours working on it. Nothing helps. Tried different CD-ROM drive, different VGA card, pulled out one RAM chip, but still hangs. Once at 76%, once soon after boot and now at 96%.

I think it's not all hardware related since Windows installed just fine on those same machines.

I guess K/Ubuntu installer is very poor written and when it hits an error, machine just freeze.

---

### Post by roberthr on 2007-02-01
Wow, it installed!!!

The last thing I replace were IDE cables... I don't believe this was the reason but I finally got it installed...

---

### Post by fat buddha on 2007-02-02
pah - am giving up with that installation - I guessed the problem is a hardware issue somewhere (probably same one in both machines as it hangs at the same place) and I just can't be arsed to fiddle around......

will try an install on a spare Dell Optiplex I have and have a dual boot with XP (IF it installs)

I can now perhaps understand why Linux is still the preserve of geeks - I've never had these sort of issues with Windoze installs and if the hardware drivers don't install to start with - at least it doesn't just give up and you can install later!!  It's the lack of feedback from the failed Ubuntu install that is frustrating - some sort of message telling me why it's failed would be helpful.......just hanging is useless

---

### Post by roberthr on 2007-02-02
I couldn't agree more. I have about 30 Ubuntu 6.10 installation behind me. Some went smooth and I had system up an running in less than 30 minutes but some were so frustrating and painful and took me hours to made it work.

I always open console window before starting installation and have tail -f /var/log/kern.log inside. Before hanging, there were usually some kernel messages that didn't really look fatal. But few minutes later machine just hanged and I was forced to turn it off since no keyboard actions worked.

There were cases where I dint' change anything in hardware. Installation just went smoothly after tenth time. That's why I doubt it's only the matter of hardware. And also cases where i.e. Suse or some other distro installed fine, but Ubuntu didn't.

I think *buntu should move to more safe installation. Maybe having hardware check after system is installed and machine booted from it so you wouldn't have to run the same steps again and again. And simple messages during installation would be nice so we could see what went wrong. CD and memory tests aren't reliable in those cases.

The domain of installation freezing computer usually belonged to Windows installations. Is Ubuntu moving to such method to remind us of the old days with Windows 9X?

P.S.

One of my frustrating installs are documented here: [http://ubuntuforums.org/showthread.php?t=284427](http://ubuntuforums.org/showthread.php?t=284427)

---

### Post by fat buddha on 2007-02-02
thank robertthr for your feedback - and just had a look at your other thread........

seems this issue is a pretty common one then

Ubuntu - ARE YOU LISTENING??  Sort out your installation problems please.  Rememeber we aren't all Linux geeks with experience of hardware /software issues beyound resolving simple issues and a lot of us don't have time to fart around with complex installs.

You want to compete with Windoze and the new Vista OS??  You've got a ready market wanting to give you guys a go but you won't succeed until you make life easier for the masses to use your product.  At least Mac OS is ahead of you on that game - shame it's restricted to Apple hardware.

No wonder Windows rules the roost - it's simple to install and run despite all it's security/virus etc problems.  Free software is only any good if it works.

---

### Post by ExemplarUbuntu on 2007-02-02
I have had similar experiences even though I have only done a few installs.

On more than one occasion it was a problem with the CD (not the drive). I burned a fresh CD and things worked.

---

### Post by Gasp100 on 2007-02-02
"You want to compete with Windoze and the new Vista OS?? You've got a ready market wanting to give you guys a go but you won't succeed until you make life easier for the masses to use your product. At least Mac OS is ahead of you on that game - shame it's restricted to Apple hardware."

--- Okay, I'm an extreme Linux Newbie but a seasoned Microsoft vet (it's my job) and have some mac experience as well. I did try to install 6.10 from the live CD but a couple of things:
#1 - I was trying to breathe new life into old hardware (PII400Mhz, 192MB RAM Toshiba laptop)
#2 - The OS is pretty darn new and FREE -- remember, FREE!
This did hang similar to your installation woes but the Live CD worked fine (albeit slowly) and I agree it was frustrating. I had an official 5.04 CD and installed that and it worked great. I also installed Kubuntu on said machine using the alternate CD (for machines with less than the RECOMMENDED 256MB of RAM). I'm considering trying an upgrade from 5.04 to 6.10 but might take some more time to learn the OS first. 
Anyway, how much does Windows Vista cost (a REAL copy, no a crack)?
What are the Vista prereq's? 16GB MIN harddrive, at least 1GB of RAM to even use it?
Ever try and run Vista in a virtual machine? Forget it... 
And MAC? Can't even vm a MAC is as lame as can be -- why? Proprietary hardware/systems.... can't get further from free than that. 
So, I say give these guys a break. The have so much less in terms of resources than the big players but they are still working like mad to provide a FREE OS and give people like you and me the chance to break it. 
Try another Distro, take a step back and try different versions... troubleshoot. 
Signed, Windows Guy (or should I say Windooooze Guy)

---

### Post by fat buddha on 2007-02-02
Gasp - I can't disagree with a lot of what you said and I know the overheads (cost/hardware) for Windows - XP or Vista - are big compared to a free option for old hardware but what gets me about Ubuntu - and other Linux flavours I've looked at - is that they all make out that installing Linux is a piece of pish - when you, me (now) and many others know this is not the case and for the uninitiated it's hard work or impossible........

I'm giving the guys a break and haven't given up yet - am currently trying an install from a more slowly burnt CD........

next stop is Kubuntu or another 

BUT I would really like Linux distributors to state somewhere that things aren't all sweetness and light installing/running it so please accept it's free and do your best.................

---

### Post by roberthr on 2007-02-02
Gasp: I do agree with some things you said. I'm not a Linux Newbie. Been using it for quite some time for running servers which IMO works really great and plays nice. The only thing that always kept me away from using linux as Desktop was hardware configuration and fact that lots of devices were unsupported. Which, thank God, changed.

So last year I was searching for nice Linux distro to use it as desktop. Ubuntu came out as the best and simplest of other distros I tried. That made me completely switched to Ubuntu, erasing Windows from all machines I work with. I just couldn't believe I can work with almost same things in Linux as in Windows and I don't mean just hardware. Even most of Windows software we use in company, works just fine with Wine. And even main app was developed using QT for Windows so our programmer had a Linux version prepared which turned out perfect. 

What else made me switch to Linux? Almost every Windows program has Linux alternative which is more or less the same or even better. So why buying CorelDraw if I can make same things with Inkscape. Why buying MS Office if I'm more used to OpenOffice. Why buying Photoshop if there is Gimp? I'm not professional desktop user. Just need a lot of programs to achieve my tasks.

So why would I bother with Windows?  I have to, since I work as a support for users using Windows. I also convinced some users to switch completely to Ubuntu rather than buying Windows and they seem to be quite happy to have a legal system that plays and work perfect and has just what they need. This is the point where drawbacks came out.

Those users I convinced to switch to Ubuntu brought their machines for me to install Ubuntu. You can't imagine the shame when we found out Ubuntu doesn't install on their machines or even worse, it just hangs.

How can I  continue to  convince  people to switch to Linux if I can't get it installed? Like I said, some machines are up and running in less than 30 minutes, some are pain. Can you image giving them CD and tell them to install Ubuntu by themselves after I showed them how easy and with small steps, it is to install?

Aren't more Linux or Ubuntu users also treated as a contribution to community?

---

### Post by fat buddha on 2007-02-02
well guys - I got it installed from the slower burnt (4X) CD..............

now to my simple mind, that just doesn't make any sense especially as the other CD burnt at max speed showed nothing wrong on the intergrity check and the .iso was fine on the checksum...........it even played nicely on live CD and up to 76% install!!

so - what have I learnt??

perseverance and reading these fora for tips - thanks whoever suggested a more slowly burnt CD as I would never have thought of that..........

BUT it still doesn't alter my view that the Linux distributors NEED to give facts that not all installs work - and if burning to a CD, do so SLOWLY!

I know someone who's having install problems as well - his issues are with his Speedtouch USB router - he has to update the firmware to use it with Linux - but have you SEEN those instructions??  that would challenge many techheads let alone someone without experience.........

so - I shall now give Ubuntu a run for it's money and see how I get on

thanks for all your help chaps - and Ubuntu - please take note of what is being said...

---

### Post by galvatron1983 on 2007-02-02
I had a similar problem with a Kubuntu install ISO burnt onto a CD RW. The installation would hang at 83% everytime I tried. In the end I used one of my older official pressed Ubuntu 5.10 discs I got through ShipIt!, they installed fine. Upon checking the CD-RW it does have a few scratches and wear on the suface, and it was burnt at a high burn speed, all of which contributed to my installation woes.

---

### Post by woodmedic on 2007-02-02
I to was having trouble installing but could play from the live CD.  My install would always hang at 82%.  I was just about to give up when the last time the system hung, I noticed activity on the lan.  I then unplugged the network cable from my machine and tried to install ubuntu again.  This time it installed like a charm and has been very stable since.  I hope this helps someone!!

---

