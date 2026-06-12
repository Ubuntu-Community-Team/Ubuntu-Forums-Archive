---
title: "Trouble installing Ubuntu (7.04, 10.04, 12.04) to a Dell Dimension 4700"
date: 2013-06-12
forum: Installation &amp; Upgrades
---

### Post by medallion19 on 2013-06-12
Ok, ok, so I know that the first question that begs to be asked here is, why in the world are you even attempting to install anything to that dinosaur (circa 2004)?  

The answer is two fold: One, I have a 7 year old who now wants to be on the computer looking at Nick Jr., or watching netflix, or just typing out "songs" that she is making up, and two, I originally started out attempting to create a Minecraft server for a very small group of friends, and since I had this desktop sitting in the basement, for about the past 6 or 7 years, I figured, why not?  I have heard that Linux works great, and for whatever reason, it works better on "older" systems, so I figured I would give it a go.  

Having said all that, my Linux experience is all of the past three months of me trying to get it installed on this machine.  

The machine is a Dell Dimension 4700, and it has a Pentium 4 Prescott HD chip.

So, I was able to install MineOS Turnkey, which is a Debian based Linux OS that was created specifically to run a Minecraft server.  I am able to install this to the machine pretty much effortlessly, and within 15 minutes, I have a successful install, and a fully functional Minecraft server running.  This worked great for the initial install, and ran perfectly for about two weeks, then, and I know I am going to catch a lot of flack for not knowing the errors, but I started receiving error messages, and sometimes I would have to just restart the machine and it would work fine, or other times I would get errors that pertained to values not matching, and they needed to be changed.  It got to the point though, where the OS would only work for about a day or a day and a half before the system crashes now.  I didn't add any mods or upgrades either.

So I tried switching to Ubuntu, and I haven't been able to get a full install on the machine yet.  Every I try to install Ubuntu, I get the same ultimate result, just at different points of the install, but it always freezes prior to completing the install.  I have tried installing 12.04, 10.04, and 7.04, and yes I have tried changing all sorts of parameters with the install.  

The part that I find completely puzzling, is as long as the Debian core system is installed on the computer, I can run Ubuntu 10.04 from a live cd, but as soon as I click on the install now option on the desktop, it freezes at 5% on the install.  If Ubuntu gets past the disk partitioning stage of installation, then freezes, when I reboot the system and attempt to run the live cd, it won't run unless I go back and re-install some form of a Debian core system, then I am able to run the Ubuntu 10.04 live cd.

At this point, because I keep hearing that there is no reason as to why I shouldn't be able to install Ubuntu to this machine, although no one has been able to tell me how to do that, it has become completely personal.  I have spent hours reading over posts, googling over and over again, and I haven't been able to find any posts that detail how it was installed on a Dell Dimension 4700, just that it was successfully installed.  

So, as a last resort to help me maintain my sanity, I am turning the the community to help me maybe put this white whale down.  Any suggestions?

---

### Post by ahallubuntu on 2013-06-12
~

---

### Post by oldos2er on 2013-06-12
Try the newest version of Lubuntu, [https://help.ubuntu.com/community/Lubuntu/GetLubuntu](https://help.ubuntu.com/community/Lubuntu/GetLubuntu)
You should have better luck installing Lubuntu than an unsupported version of Ubuntu (7.04 and 10.04).

---

### Post by ajgreeny on 2013-06-12
How much ram does it have?  I see some reference to 512MB in google, but yours may be different.

If I'm right I would certainly look at Lubuntu, or if you have more ram than that (1GB) you could also try Xubuntu.  Finally as an option, if you have trouble installing because of pae kernel requirement, have a look at Bodhi 2.3, which is based on ubuntu but has a non-pae version and runs on very little ram.

---

### Post by medallion19 on 2013-06-13
Thank you for all of the responses.

I originally thought that maybe it was the hard drive, and without running any of the tests, I did replace the hard drive with a 1tb Seagate hard drive, and it still freezes up.

I currently have 4 gb of ram installed on the machine, and although Ubuntu won't install, the MineOS Turnkey will, which is based on Debian, but when I attempt to install Debian 7.0, I can't get a full installation, only a core installation.  

I'll try using Lubuntu, Xubuntu, and then Bodhi.  If I get anything to finally work, I'll post the results back here.  I noticed that it was mentioned to try Ubuntu 12.04, not sure if I really clarified that part, but that was the distro that I tried first, and I tried every combo imaginable to try to get it to work.  I had read a post on a different forum telling someone else to possibly try loading an older version, and then upgrading from there.  I went back to 7.04, because I couldn't get any of the other distros to work, so I googled circa 2004 Ubuntu, and it said that was the version at that time, so I figured I would just try that too.  At this point, I was just trying to get anything (other than MineOS Turnkey, which again loads with no problems at all) to work.  

Its rather frustrating.

---

### Post by mörgæs on 2013-06-13
> **ajgreeny said:**
> ...if you have trouble installing because of pae kernel requirement...

All Pentium 4's have PAE.

---

### Post by medallion19 on 2013-06-14
All, again, thanks for your guidance, I literally spent numerous hours over the past two months trying to figure this thing out, and I am happy to report that today I managed to get 12.04 installed on this machine.  For whatever reason, Ubuntu was not liking my RAM, so I pulled 3 of the 4 gbs out of the machine, and as soon as I did that, it installed with no problem. 

So after I managed to get a successful install, I attempted to put all the RAM back into the machine, I booted the system, and absolutely nothing.  So I pulled the three back out again, and rebooted and it worked.  So I then shutdown and installed another gig of RAM, and rebooted, and it worked, so I shutdown, installed a third gb, and attempted to reboot, and nothing, so I shutdown, removed that memory stick, and placed the remaining stick into that same slot, and when I rebooted, it worked fine.  I then installed the 4th stick back into the machine, just in a different slot than where it had previously failed, and when I rebooted, it all worked perfectly fine.  

As weird as that sounds, the system has been up and running strong now for about 6 hours.  I'll check back in if it crashes and report any errors that I get. 

Thank you all.

---

### Post by medallion19 on 2013-06-14
And one last thing, I am excited to start exploring what Ubuntu has to offer, I know that I said that this machine is going to be mainly used by my daughter, but I think I may have an Ubuntu bug, I have always heard great things about this OS, so here I go.

---

### Post by ahallubuntu on 2013-06-14
~

---

