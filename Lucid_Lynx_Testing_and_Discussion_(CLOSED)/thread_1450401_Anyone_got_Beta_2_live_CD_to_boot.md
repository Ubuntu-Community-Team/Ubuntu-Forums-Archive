---
title: "Anyone got Beta 2 live CD to boot ?"
date: 2010-04-09
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by ToxicBurn on 2010-04-09
I just want to see if anyone has got 
 
[**[COLOR=royalblue]ubuntu-10.04-beta2-desktop-i386.iso[/COLOR]**]("http://releases.ubuntu.com/releases/10.04/ubuntu-10.04-beta2-desktop-i386.iso")**[COLOR=royalblue] - 06-Apr-2010 21:23 696M[/COLOR]** 
 
 
to boot at all or can we confirm the Iso is trash ?

---

### Post by seenthelite on 2010-04-09
Kubuntu Beta 2 I have downloaded today and booted as live CD, created new partition with it and installed as Triple Boot with Ubuntu 10.04 and Windows 7.

---

### Post by barbz127 on 2010-04-09
I downloaded mine (desktop amd64) from the torrent source but I cannot get it to install. Just hangs with the timer icon spinning around.

I have tried to click install by selecting it from the initial prompt then I rebooted, selected to try Ubuntu then hit the install icon on the desktop and it just hung.

Now trying to download the alternate disk.

Cheers
Paul

---

### Post by xens on 2010-04-09
downloaded via torrent today, copied on a usb stick and installed on my EEPC-1000h. 

Everything is fine

---

### Post by norbs on 2010-04-09
Check this thread: [http://ubuntuforums.org/showthread.php?p=9096982#post9096982]("http://ubuntuforums.org/showthread.php?p=9096982#post9096982")

I've managed to install it, after the same problem: reply#10

---

### Post by kansasnoob on 2010-04-09
Works fine for me. Did you check the md5sum? Did you try the option Check CD for defects?

---

### Post by halj32 on 2010-04-09
maybe it's the same as the B1.. you must liveboot then install from the icon on the desktop???
think I'll wait for the final

---

### Post by bennachie on 2010-04-09
The i386 LiveCD has worked just fine for me - there was no need to actually launch the OS before installing. The installation seemed to proceed a bit quicker than in previous iterations.

---

### Post by tokyobadger on 2010-04-09
> **halj32 said:**
> maybe it's the same as the B1.. you must liveboot then install from the icon on the desktop???
think I'll wait for the final
that wasn't the case for me with beta1 - installed as an install CD, not from live environment

---

### Post by phibxr on 2010-04-09
> **ToxicBurn said:**
> I just want to see if anyone has got 
 
[**[COLOR=royalblue]ubuntu-10.04-beta2-desktop-i386.iso[/COLOR]**]("http://releases.ubuntu.com/releases/10.04/ubuntu-10.04-beta2-desktop-i386.iso")**[COLOR=royalblue] - 06-Apr-2010 21:23 696M[/COLOR]** 
 
 
to boot at all or can we confirm the Iso is trash ?

I did download, md5check, burn and verify both the desktop and the netbook editions, both on my netbook and my desktop computer.

They stop during booting at the Plymouth (?) Ubuntu-screen with all dots being orange, as has been reported in several other places too. :(

---

### Post by Jerry N on 2010-04-09
> **bennachie said:**
> The i386 LiveCD has worked just fine for me - there was no need to actually launch the OS before installing. The installation seemed to proceed a bit quicker than in previous iterations.

The install took a REALLY long time for me, particularly the last 5%.  Boot time is really great though!  I got an error when I let it try to install the Nvidia proprietary drivers.  

Jerry

---

### Post by RTrev on 2010-04-12
I've had a particularly weird time with the Lubuntu Beta 2 iso.

I got it via torrent, and compared the md5s.  They matched what they were supposed to be.

I then tried to burn it to a CD, and this is where things got strange.

To make a long story shorter, I've tried to burn this ISO to 4 different BRANDS of CD, in three different computers, using three different kernels, and using three different burning programs.  It simply can't be burned so that it ends up with the correct md5.  Letting the CD run it's self-check always shows 1 file is wrong (it doesn't say which one.)

So, it fails to burn under even Karmic with Gnome Baker.  After the burn, it still shows on the desktop as a blank CD.  Brasero under Lucid Gnome errors out, and xfBurn under Lucid Lubuntu says it succeeded but in fact it creates the same error.

Interesting that ALL created CDs have the exact same md5.  So the error is reproducible.  In fact, it appears to be unavoidable.

I don't know quite what to think.  Sometimes now my Brasero and xfBurn say that there is no CD in the drive to burn to, which can't be a problem with the iso.  But assuming it's a CD-related problem with Lucid doesn't explain why my wife's Karmic system can't burn this iso either.

Again, the iso has the *correct* md5, as specified by the download site: 1bfcb7bf3616dea4614c056023fe482b

Anybody got any ideas?

---

### Post by bennachie on 2010-04-12
If you have a live connection to the Internet (ethernet or wireless) the installer gets to around the 88% mark, then spends ages downloading and installing language packs - if you don't need these, just pull the plug before launching the installer, and you'll save a heap of time.

---

### Post by Plumtreed on 2010-04-13
@RTrev

I had a similar thing in an earlier Alpha version but I think it worked on K3b. This was also in 9.04 if that makes any difference?

---

### Post by RTrev on 2010-04-13
Thanks Plumtreed.  K3b did the same thing.  I looked at the CD manually, and tracked the change down to one file named cat.boot -- and I'm not sure how important this file is.  I boot from the CD and it worked fine.  I'm leery of installing from it, as it might work fine right up to the point where it trashes my master boot record or something.

Besides, my current install of Lubuntu is up-to-date so should be the same thing.

I'm really looking forward to the 10.10 alphas being released, because my understanding is that then Canonical will have officially adopted Lubuntu, so we'll know we're on track to having this distro become a supported member of the Ubuntu family.

---

