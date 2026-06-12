---
title: "Gah, upgrade woes"
date: 2006-08-03
forum: Installation &amp; Upgrades
---

### Post by Mozzer on 2006-08-03
**[COLOR="Red"]Warning: the following post contains major rant.[/COLOR]**

I've said this before, and I'll say it again: I really want to love Ubuntu. And for a while now, I have. Breezy was working pretty much like a charm, and it fixed for me a lot of problems from Hoary. But  yesterday I decided to begin my pilgrimage across the rocky roads of upgrading.

First of all I downloaded the installer iso from the website. Burned it to CD. Then I couldn't actually see how to use it to upgrade so I looked for help here. The general message seemed to be "use the alternate installer" which was not particularly helpful (and also quite hard to find). Downloader 4 X refused to download properly so I was stuck with the Firefox download manager. Halfway through the download I tried to pause which, instead of resuming, restarted. So I gave up on that.

Then there were various instructions for upgrading. In the end I plumped for apt-get update and apt-get dist-upgrade. All seemed to be well, except for the fact that nearly all the information was downloaded anew. At the end it seemed to display some dependancy errors but I thought nothing of it. After reboot I had the old X server error. Woo yay.

This threw up all sorts of errors such as failing to load GLCore, unknown items like 'QUOTAS_ENAB' when I tried to log in on the command line, and when trying to reconfigure xserver-xorg it said it was broken/missing. So now to try some repairs. I trawled through the forums and found various solutions... or not.

apt-get install ubuntu-desktop threw hundreds of dependancy errors at me.
So did apt-get upgrade --fix-missing, although it did helpfully suggest apt-get install -f. This seemed to help, and it began patching up the half-arsed upgrade that had taken place earlier. Then I did ubuntu-desktop. Then I did fix missing. Overall this whole process has taken about 4 hours.

Finally, after a reboot, I can login. But now two problems have arisen. [COLOR="Red"]The system hasn't configured either of my sound cards, and there was some error about loading ndiswrapper on boot so I have no internet either.[/COLOR]

Now why does everything have to throw up so many errors? Why can't there be a simple upgrade that just works? I hate to say it, but wasn't Service Pack 2 for XP so much easier? Forget about all of Windows' other faults for a minute and think about that.

I know I'm probably going over the top with all this but I had to get it off my chest, maybe share my experience with other people and, if I'm lucky, inspire some improvements.

Thanks for listening, and thanks in advance for any help with my current predicaments.

---

### Post by Mozzer on 2006-08-05
Ok, I've looked into the ndiswrapper problem and I can't modprobe it:

mozzer@ubuntu:~$ sudo modprobe ndiswrapper
FATAL: Error inserting ndiswrapper (/lib/modules/2.6.12-10-386/kernel/drivers/net/ndiswrapper/ndiswrapper.ko): Operation not permitted

So I've gone back to all the installation guides and threads and everything. I seem to have the same problem as before and it's to do with my linux-headers package. I've look in Synaptic and linux-headers-2.6.15-23 is available but I am running kernel 2.6.12-10-386... so does this mean I need a new kernel? I tried running an apt-get install for my version but it couldn't find one.

---

### Post by tseliot on 2006-08-05
> **Mozzer said:**
> Ok, I've looked into the ndiswrapper problem and I can't modprobe it:

mozzer@ubuntu:~$ sudo modprobe ndiswrapper
FATAL: Error inserting ndiswrapper (/lib/modules/2.6.12-10-386/kernel/drivers/net/ndiswrapper/ndiswrapper.ko): Operation not permitted

So I've gone back to all the installation guides and threads and everything. I seem to have the same problem as before and it's to do with my linux-headers package. I've look in Synaptic and linux-headers-2.6.15-23 is available but I am running kernel 2.6.12-10-386... so does this mean I need a new kernel? I tried running an apt-get install for my version but it couldn't find one.

Make sure that all your repositories are set to dapper

then type:
```
sudo apt-get install linux-386
```

and reboot so as to boot in your new kernel


And about your problems with the Xserver you can try this:
[http://ubuntuforums.org/showthread.php?t=187177](http://ubuntuforums.org/showthread.php?t=187177)

---

### Post by Mozzer on 2006-08-06
No worries tseliot, I got X-server sorted out after all my mad package fixing upgrading replacing etc.

All addresses in sources.list are set to dapper; obviously apt-get update does not work as I have no internet connection yet.

So here's what I did...

```
mozzer@ubuntu:~$ sudo apt-get install linux-386
Reading package lists... Done
Building dependency tree... Done
linux-386 is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 53 not upgraded.

mozzer@ubuntu:~$ sudo apt-get install linux-headers-$(uname -r)
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package linux-headers-2.6.12-10-386

mozzer@ubuntu:~$ (uname -r)
2.6.12-10-386
```

So I'm definitely running 2.6.12, for which there are no headers, and the linux-386 package is already up to date... apparently. So is there anywhere I can download the latest in a deb or something and manually install it?

And I got the sound fixed using the comprehensive sound guide so no probs there.

Thanks for help so far,
Mozzer

---

### Post by tseliot on 2006-08-06
> **Mozzer said:**
> So I'm definitely running 2.6.12, for which there are no headers, and the linux-386 package is already up to date... apparently. So is there anywhere I can download the latest in a deb or something and manually install it?

Try this:

1) Download Ubuntu's CD

2) Type:

```
sudo apt-cdrom add
```

then it should ask you to insert Ubuntu's cd.

Then (after the previous process finishes) type:

```
sudo apt-get update
```

3) install the new kernel:
```
sudo apt-get install linux-386
```

4) reboot

---

### Post by Mozzer on 2006-08-06
I already had the Ubuntu 6.06 CD (though not the "alternative" one) so...

```
mozzer@ubuntu:~$ sudo apt-cdrom add
Using CD-ROM mount point /cdrom/
Unmounting CD-ROM
Waiting for disc...
Please insert a Disc in the drive and press enter
Mounting CD-ROM...
Identifying.. [d9f91a1075ce140463bf88837cc07be6-2]
Scanning disc for index files..
Found 2 package indexes, 0 source indexes and 1 signatures
This disc is called:
'Ubuntu 6.06 _Dapper Drake_ - Release i386 (20060531)'
Copying package lists...gpgv: Signature made Wed 31 May 2006 04:16:20 BST using DSA key ID FBB75451
gpgv: Good signature from "Ubuntu CD Image Automatic Signing Key <cdimage@ubuntu.com>"
Reading Package Indexes... Done
Writing new source list
Source list entries for this disc are:
deb cdrom:[Ubuntu 6.06 _Dapper Drake_ - Release i386 (20060531)]/ dapper main restricted
Unmounting CD-ROM...Repeat this process for the rest of the CDs in your set.
```

After this the apt-get update just coughs up a load of errors about not resolving the web addresses. And it still thinks linux-386 is the newest version.

Is it something to do with the unmounting bit at the end of apt-cdrom add?

---

### Post by tseliot on 2006-08-07
> **Mozzer said:**
> I already had the Ubuntu 6.06 CD (though not the "alternative" one) so...

```
mozzer@ubuntu:~$ sudo apt-cdrom add
Using CD-ROM mount point /cdrom/
Unmounting CD-ROM
Waiting for disc...
Please insert a Disc in the drive and press enter
Mounting CD-ROM...
Identifying.. [d9f91a1075ce140463bf88837cc07be6-2]
Scanning disc for index files..
Found 2 package indexes, 0 source indexes and 1 signatures
This disc is called:
'Ubuntu 6.06 _Dapper Drake_ - Release i386 (20060531)'
Copying package lists...gpgv: Signature made Wed 31 May 2006 04:16:20 BST using DSA key ID FBB75451
gpgv: Good signature from "Ubuntu CD Image Automatic Signing Key <cdimage@ubuntu.com>"
Reading Package Indexes... Done
Writing new source list
Source list entries for this disc are:
deb cdrom:[Ubuntu 6.06 _Dapper Drake_ - Release i386 (20060531)]/ dapper main restricted
Unmounting CD-ROM...Repeat this process for the rest of the CDs in your set.
```

After this the apt-get update just coughs up a load of errors about not resolving the web addresses. And it still thinks linux-386 is the newest version.

Is it something to do with the unmounting bit at the end of apt-cdrom add?

try with:
```
sudo apt-get install linux-image-2.6.15-23-386
```

---

### Post by Mozzer on 2006-08-08
> **tseliot said:**
> try with:
```
sudo apt-get install linux-image-2.6.15-23-386
```

This needed an active web address so this failed but it did provide with a download URL. So I went back to Windows and downloaded the deb from there. Then back to Ubuntu and did a manual dpkg -i. All seemed to run smoothly.

Rebooting showed a definite improvement; after the upgrade the graphical boot loader got stuck at a certain point and reverted to text-based, generally at the point where it tried to load ndsiwarapper. I was hopeful.

Next thing I noticed was that the login screen appeared straight away instead of temporarily being the random blur that I have become accustomed to in recent days.

I log in, go to Networking. wlan0 is up! It's fixed itself, and the interweb is working fine. I'm posting this from Ubuntu, thank god.

Now I have just one minor problem left with Nautilus randomly crashing whenever I try to open a folder, but I think that should be ok once I've followed the instructions on [http://ubuntuforums.org/showthread.php?t=184066&highlight=application+nautilus+quit+unexpectedly](http://ubuntuforums.org/showthread.php?t=184066&highlight=application+nautilus+quit+unexpectedly)

Cheers tseliot!

---

