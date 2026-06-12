---
title: "SATA drive, DVI Radeon 9800 Pro compatibility?"
date: 2004-11-12
forum: Installation &amp; Upgrades
---

### Post by nehalem on 2004-11-12
Hi all,
I have ubuntu installed on an older system but I've reached the point (because I'm so impressed with it) where I think I would like to use it full time.  This for me entails dual booting my newer system.  It's specs are as follows:

-Nforce3 250gb with sata (does raid but I'm not using that), onboard audio (7.1 channel audio codec RealTek ALC850, ac 97 2.3 compliant), and gigabit ethernet(nvidia's own??).
-AMD 64 (not worried)
-ATI 9800 Pro using DVI to my 21' Dell LCD
-HP DVD burner 
-Etc.

As stated in the title, the areas of concern lie with the DVI compatibility, which I'm thinking will work after I get the ubuntu ATI binary driver installed (?), and the SATA HD.  Just doing a quick search it seemed like some users had issues with sata drives but I couldn't tell whether this was common or uncommon (I understand that about any piece of HW can give issues in certain scenario's, does Ubuntu even claim SATA support and is that pretty standard like IDE support??).  I also have to wonder if the gigabit ethernet and audio will work as well since the nforce3 is a pretty new product.

I don't want to go through all the partitioning trouble, etc. if this is something that doesn't have a good chance of working.[list]
[/list]

---

### Post by nehalem on 2004-11-12
After doing some more research it looks like support for this mb was added in the 2.6.7 kernel, which would be good.  Still I have to wonder if there are some ubuntu users out there using a similar setup.  

Thanks.

---

### Post by daniels on 2004-11-12
[QUOTE=nehalem]As stated in the title, the areas of concern lie with the DVI compatibility, which I'm thinking will work after I get the ubuntu ATI binary driver installed (?)[/QUOTE]You won't need the ATI binary driver, no.  2D output will work just fine.

---

### Post by nehalem on 2004-11-12
[QUOTE=daniels]You won't need the ATI binary driver, no.  2D output will work just fine.[/QUOTE]
Thanks Much.

So does anyone know if SATA will work under Ubuntu.  I mean it's a new kernel but I've seen really mixed reviews on the web.

The only thing I can confirm is that Gentoo supports it.

Edit:
One of the things I've read is that the installer kernels don't detect it but the running kernel will, which would be bad.  is there a big difference between these kernels with ubuntu?

Reading the 2.6.8 kernel change log it looks like an SATA driver driver for nvidia was added by someone from nvidia.  

I guess I'll just keep posting my updates so if someone can't help me then hopefully I'll be able to help someone else later on.  :)

---

### Post by daniels on 2004-11-12
[QUOTE=nehalem]So does anyone know if SATA will work under Ubuntu.  I mean it's a new kernel but I've seen really mixed reviews on the web.[/QUOTE]I seem to recall a few Ubuntu devs running it on machines with big SATA disks.

In fact, I definitely recall fixing discover1-data (or merging Colin Watson's fixes to discover1-data) so we properly detected SATA chipsets, and that this resulted in working SATA.  So, yes.

> One of the things I've read is that the installer kernels don't detect it but the running kernel will, which would be bad.  is there a big difference between these kernels with ubuntu?No.

---

### Post by nehalem on 2004-11-12
So I ran the live CD version of ubuntu and the SATA seemed to work great and no probs with the DVI.

However when I went to HW browser it doesn't seem to recognize my ethernet card or my soundcard (both packaged with the MB).

:(

Is the live CD's kernel the same?  If so will Warty see any updates that aren't just security specific, in other words updates to newer kernels with newer drivers?  (although there really isn't much newer)

---

### Post by daniels on 2004-11-12
[QUOTE=nehalem]So I ran the live CD version of ubuntu and the SATA seemed to work great and no probs with the DVI.

However when I went to HW browser it doesn't seem to recognize my ethernet card or my soundcard (both packaged with the MB).

:(

Is the live CD's kernel the same?  If so will Warty see any updates that aren't just security specific, in other words updates to newer kernels with newer drivers?  (although there really isn't much newer)[/QUOTE]The kernels should be the same, only the detection routines.  What sort of ethernet/sound cards do you have?  Output of both lspci and lspci -n would be useful.

---

### Post by nehalem on 2004-11-12
Ok, my motherboard is the following:  [MSI K8N Neo Platinum](http://www.msicomputer.com/product/p_spec.asp?model=K8N_Neo_Platinum&class=mb) 

As for the lspci info, this was a pain, to get.  I ended up having to take pictures of my screen since I could find no other way to get the info over (USB would not write, network card doesn't work, and no floppy).  So provided are the links to the pictures.

(took off the picture since I created a bug report with them and don't want these to eat any of my bandwidth)

Thanks.

---

### Post by daniels on 2004-11-13
Could you please file a bug on discover1-data at [http://bugzilla.ubuntu.com](http://bugzilla.ubuntu.com) with this data, and set the assigned to field to [email]daniel.stone@canonical.com[/email]?  Cheers.

---

### Post by nehalem on 2004-11-13
[QUOTE=daniels]Could you please file a bug on discover1-data at [http://bugzilla.ubuntu.com](http://bugzilla.ubuntu.com) with this data, and set the assigned to field to [email]daniel.stone@canonical.com[/email]?  Cheers.[/QUOTE]

Submitted it (you'll see like 5 emails for this one, I haven't ever done this so I tweaked some of the original summary stuff and added attahments)

Thanks for your help!  You guys have an incredible product!

---

### Post by daniels on 2004-11-13
[QUOTE=nehalem]Submitted it (you'll see like 5 emails for this one, I haven't ever done this so I tweaked some of the original summary stuff and added attahments)

Thanks for your help!  You guys have an incredible product![/QUOTE]Thanks dude -- it's just a way for me to better keep track of everything (I have to write a long letter [never done that!] and pack everything here up tonight before I fly out tomorrow, and I'm incredibly tired already).  In general, if issues get reported to Bugzilla, they'll get tracked pretty well through there.

Cheers for the compliment; hope you have as much fun using it as we have had developing it. :)

---

