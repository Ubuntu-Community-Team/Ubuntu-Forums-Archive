---
title: "most painless way to go from Hardy to Intrepid"
date: 2008-10-21
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by mfox on 2008-10-21
I have Hardy with the Netbook Remix installed on my MSI Wind.  I've been happy with it up until now when the Realtek wireless broke with the latest kernel upgrade.  I still have wireless if I boot from the slightly older kernel, but this little glitch motivates me to move from Hardy to Intrepid when the final Intrepid release is out.  (Intrepid is supposed to support Realtek wireless out of the box.)

I know that one can do a distribution upgrade within Hardy, but I've heard that this type of upgrade can cause dependency problems down the road.  Should I be concerned about this with a Hardy to Intrepid conversion?

I wouldn't mind installing the new system from scratch, except that certain modifications would have to be redone, and outside programs I've installed would have to be reinstalled from scratch.  In particular I'm concerned with programs I installed under Wine, like MS Office.  Is there some way, for example, that my Wine programs can just be copied over to the new installation?

---

### Post by FutanariKitty on 2008-10-21
Well, the distro upgrade may still be your best option. When trying out Intrepid (upgraded from Hardy) I had no problems related to dependencies and the like. For that matter, in all the years I've toyed with Debian-based distros I've rarely had a problem in that vein (though it has happened, you rarely see these types of issues these days, in my experience).

I'm going to make the assumption that you did not partition your /home directory seperately from /, so one particular option is to boot from CD/USB, then manually remove all the various directories on your partition, except for /home. During the installation process, configure your partitions manually, and make sure you don't format /.

It's ugly, potentially dangerous, but it CAN work. There are far better solutions, like backing up your /home directory, then dropping it back in place after you've installed a fresh system. The wonderful thing about Wine's default configuration is that all the various Windows apps you've installed reside directly in your /home directory, not anywhere else on the system.

Good luck, if this ends up being your only option. As I mentioned, it's clunky and dangerous, but doable.

EDIT: Also, this should come as no surprise, but verify that your wireless DOES indeed work with Intrepid...when I played with the beta I had all sorts of little issues with video, networking, sound, etc. that did not pop up in Hardy.

---

### Post by mfox on 2008-10-21
Thanks, FutanariKitty; your answer is very helpful.  I didn't realize that Wine programs all reside in the /home directory and that this directory could simply be dropped into a new installation.  Your posting suggests to me a dual strategy:
(1) back up my /home folder on a separate disk (usb stick?)
(2) attempt an update on my present installation
(3) if there are problems with #2, install from scratch and replace the /home folder with my old one.
By the way, your assumption is correct; I did install into one partition (other than swap).

Your advice about the wireless is also good.  I am monitoring the situation on the MSI Wind forums.  There are still some Wind-specific issues in Intrepid, but it's still a beta and hopefully they'll work them out by the time it's released.  

Meanwhile, I'll happily continue to use Hardy, booting into the 2.6.24-19 kernel until -21 is fixed for Realtek wireless or until the kernel is updated.  Speaking of which, is there an easy way to boot into the older kernel as default without removing the newer kernel?

---

### Post by sethvath on 2008-10-21
> **mfox said:**
> 

Meanwhile, I'll happily continue to use Hardy, booting into the 2.6.24-19 kernel until -21 is fixed for Realtek wireless or until the kernel is updated.  Speaking of which, is there an easy way to boot into the older kernel as default without removing the newer kernel?

Its in /boot/grub/menu.lst 
If you're not comfortable editing grub files install [BUM]("http://www.marzocca.net/linux/bum.html") and let it do it for you.

---

### Post by w3rt on 2008-10-21
my wired connection doesnt seem to work, is there a list of ethernet cards that dont work with intrepid?

---

### Post by Ng Oon-Ee on 2008-10-21
> **mfox said:**
> Thanks, FutanariKitty; your answer is very helpful.  I didn't realize that Wine programs all reside in the /home directory and that this directory could simply be dropped into a new installation.  Your posting suggests to me a dual strategy:
(1) back up my /home folder on a separate disk (usb stick?)
(2) attempt an update on my present installation
(3) if there are problems with #2, install from scratch and replace the /home folder with my old one.
By the way, your assumption is correct; I did install into one partition (other than swap).

Your advice about the wireless is also good.  I am monitoring the situation on the MSI Wind forums.  There are still some Wind-specific issues in Intrepid, but it's still a beta and hopefully they'll work them out by the time it's released.  

Meanwhile, I'll happily continue to use Hardy, booting into the 2.6.24-19 kernel until -21 is fixed for Realtek wireless or until the kernel is updated.  Speaking of which, is there an easy way to boot into the older kernel as default without removing the newer kernel?

Hi, I'd just add concerning Wine that all the information is stored in a single folder. This is by default named ".wine" in your /home/{your_username}/ folder. If you are ONLY concerned with keeping your wine programs, then this is the only folder you need to backup. For myself, I just setup wine, copy the folder to another hard disc, then run using the following commands:-

```
WINEPREFIX = /path/to/wherever/you/copied/the/wine/folder wine {name_of_your_executable}.exe
```

This also helps to 'freeze' your wine setup for a particular program so that if you setup another program, it uses a different bunch of settings and doesn't mess up your older (working) programs.

However, all that being said, backing up your home folder is still highly recommended. Lots of your application-specific settings (firefox, thunderbird (or evolution), pidgin, and all the utilities) are there, in hidden folders (folders with a '.' at the start of their names) or hidden files (files with a '.' at the start of their names). Just open Nautilus and press Ctrl-H to see the large number of files :).

---

### Post by mfox on 2008-10-22
> **sethvath said:**
> Its in /boot/grub/menu.lst 
If you're not comfortable editing grub files install [BUM]("http://www.marzocca.net/linux/bum.html") and let it do it for you.
I'm not sure how to proceed from here.  I looked at the menu list and it just lists the boot options in the same order as I see when I boot.  If I want to change the default option, do I just move the preferred one to the top of the list or is there a default statement I have to add?

I also downloaded bum but I couldn't see its relevance to my wanting to change the default boot option.

---

### Post by priegog on 2008-10-22
Let me add that IF you end up having to reinstall from scratch, it would be a good time to setup a separate /home partition so as to prevent these dilemmas in the future. The RC is due out tomorrow, and the final release in a week, so we won't have to wait too long either way.

---

### Post by mfox on 2008-10-22
So is it generally safe to overwrite the /home folder produced by the newer version of a distro with that of an older version of the same distro?  Until I read some of these responses, I would have worried that I would screw things up by doing this.

---

### Post by Sef on 2008-10-22
> So is it generally safe to overwrite the /home folder produced by the newer version of a distro with that of an older version of the same distro? Until I read some of these responses, I would have worried that I would screw things up by doing this.

1) Always **Back Up** your data before upgrading or reinstalling.   

2) If you upgrade make sure that you have a reinstall disk around.   Sometimes the upgrade fails to install properly.

3) When root and home are on the same partitions and you upgrade the data should be preserved; if you reinstall the data will be lost.   In the former case, please reread #1.  

4) If you have a separate home and root partitions, then the data should be preserved in both cases.   Again reread #1.

---

### Post by maestrobwh1 on 2008-10-23
I actually had no issue upgrading my Acer Aspire laptop... other than the intrepid kernel made my wifi really unstable.  I compiled madwifi from source (I put an atheros mini pci in favor of the broadcom card).

Back up your data using simple-backup or something else, and give the upgrade a whirl.  After a I rebooted, I then ran gtkorphan (frontend for deborphan) and ticked the box for other installed programs (I forget what it is labeled) that were orphaned, and ran through that a few times until nothing showed up as orphaned.  I opened synaptic, went to "status" and "not installed - residual" and selected all of those things and purged them.

Aside from wireless which is still flaky as of now, the upgrade was worth it.  I have all of my "stuff" and along with the extremely fast shutdown time, and it wakes up out of suspend to ram within seconds (except of course for wireless).  It even hibernates to disk, which it never did properly.

I have upgraded countless times all the way from Edgy Eft (6.10).

---

### Post by JohnSearle on 2008-10-24
@MFox

I know this is WAY off topic, but you're living in PTBO, Ontario, eh? I went to Trent University there (graduated 2 years ago), and I still have a number of friends who live there, of whom I visit every so often. 

Small internet.

EDIT: Yes, I think this was probably better conducted through PM. My apologize to the forum police.

- John

---

