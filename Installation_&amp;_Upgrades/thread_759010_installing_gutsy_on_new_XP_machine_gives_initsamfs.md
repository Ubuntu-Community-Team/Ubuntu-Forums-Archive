---
title: "installing gutsy on new XP machine gives initsamfs error"
date: 2008-04-18
forum: Installation &amp; Upgrades
---

### Post by silbar on 2008-04-18
Greetings,

My old machine (originally running Win98, but RedHat and Ubuntu for the last five years) has just now been replaced by a new Dell Inspiron 530 running WinXP Pro.  The big 500 GB disk has, essentially, just one partition, the C: drive.  Hoping to return to Ubuntu as quickly as possible, today I inserted the Gutsy CD in the drive and rebooted to make the installation.  

Clicking on the "Start or Install" option, the boot process for a Live CD session does not proceed as I have often seen in the past (on the old machine).  It hangs in what looks like an application or script called "initsamfs".  At least it provides a "(initsamfs)" prompt.
And, it "fails to set xfermode", whatever that means.  Then, after a bit, about a dozen other error mesages before it hangs up totally.

I am unable to proceed from that point.  This CD did start the Live CD session just fine, albeit slowly, on the old Micron machine.

If someone can help me get out of XP and back into Gutsy, I'd be very appreciative.  Thanks in advance,

   Dick Silbar

---

### Post by Pumalite on 2008-04-18
Try a few boot parameters:
[http://www.hispafuentes.com/hf-doc/HOWTOs/BootPrompt-HOWTO-html/BootPrompt-HOWTO.html#toc1](http://www.hispafuentes.com/hf-doc/HOWTOs/BootPrompt-HOWTO-html/BootPrompt-HOWTO.html#toc1)
[http://d-i.alioth.debian.org/manual/en.i386/ch05s02.html](http://d-i.alioth.debian.org/manual/en.i386/ch05s02.html)
[http://www.tldp.org/HOWTO/BootPrompt-HOWTO.html](http://www.tldp.org/HOWTO/BootPrompt-HOWTO.html)

[http://grumpymole.blogspot.com/2007/05/ubuntu-how-to-edit-grub-boot-parameters.html](http://grumpymole.blogspot.com/2007/05/ubuntu-how-to-edit-grub-boot-parameters.html)
[https://help.ubuntu.com/7.04/installation-guide/hppa/boot-parms.html](https://help.ubuntu.com/7.04/installation-guide/hppa/boot-parms.html)
[http://www.cyberciti.biz/tips/10-boot-time-parameters-you-should-know-about-the-linux-kernel.html](http://www.cyberciti.biz/tips/10-boot-time-parameters-you-should-know-about-the-linux-kernel.html)
[http://www.knoppix.net/wiki/Cheat_Codes](http://www.knoppix.net/wiki/Cheat_Codes)
[http://www.knoppix.net/wiki/Kernel-parameters-2.6.11](http://www.knoppix.net/wiki/Kernel-parameters-2.6.11)
noapic nolapic acpi=off pci=noacpi pnpbios=off vga=0x317 vga=791 vga=775
Try:
noapic nolapic first

---

### Post by silbar on 2008-04-21
Thanks, Pumalite, for the quick reply.  My delay in responding is that I had other problems to solve (with the XP side) before getting back to trying to install Gutsy.

The problem is that, looking at your suggested links, I don't understand how to proceed.  I am trying to boot up using the Ubuntu CD (received from them, so unlikely to be corrupted).  Where then is the opportunity to set the boot parameters you suggest?

I have to read this Forum from the XP side, so I will next try again with the install CD, but going to the command line to see if the boot parameters can be set that way.

Thanks,

   Dick Silbar

---

### Post by Maintech on 2008-04-21
If that command doesn't work for you then try --nomsi. A lot of the newer motherboards have chipsets that the kernel gets confused by and goes into a loop. There are discussions about it on the kernel forums.

---

### Post by silbar on 2008-04-21
Well, thanks to Pumalite -- I'm maybe halfway there!

On starting up with the LiveCD disk, I now discover that I mis-spelled "initramfs" as "initsamfs" in the title of this thread.  That does make more sense.  Sorry if this threw people off or drove them away.

I also discovered, when the choice of what to do comes up, that there is an <F6> option that allows me to add the two boot parameters that Pumalite suggested, 'noapic' and 'nolapic'.  With _both_ of these and no others, THIS allowed the boot process to continue to the Ubuntu screen.

From which I was able to install Gutsy 7.10.  

On the restart, however, the Grub menu comes up correctly, and on choosing the usual Ubuntu, the progress bar stops almost at once.  It does NOT boot into a non-LiveCD session.

Restarting, I was able to edit the boot parameters in the Grub, again adding separate lines for noapic and nolapic after the quiet parameter.  HOWEVER, this does not help the boot process to get past the first blip on the Ubuntu load process progress bar.

So, I am still stuck, and this still comes to you from XP.  I will next try Maintech's suggestion of 'nomsi', but probably not until this evening.

   Dick Silbar

---

### Post by Pumalite on 2008-04-21
This is a particularly good guide on how to do it:

[http://grumpymole.blogspot.com/2007/...arameters.html](http://grumpymole.blogspot.com/2007/...arameters.html)

---

### Post by silbar on 2008-04-22
This is STILL coming to you from Win XP!

Pumalite wrote,

>This is a particularly good guide on how to do it:
>[http://grumpymole.blogspot.com/2007/...arameters.html](http://grumpymole.blogspot.com/2007/...arameters.html) 

Yes, I was there yesterday, thank you.  Unfortunately the link given here seems not to find that blog.

Anyway, following Warren Butler's blog, I have not been successful in getting into Gutsy.  It seems that every time I edit the Grub and exit, it says "Starting Up..." and the boot parameters I added apparently are no longer there.  So, it hangs at the first blip, as noted before.

So, this morning I decided to follow Warren's other advice, to make the boot params permanent by editing /boot/grub/menu.lst.
To do this I tried to boot from the LiveCD disk.  Now, BEFORE, I was able to do this by <F6> and adding the 'noapic nolapic' parameters.  And that's how I did the install of Gutsy.  NOW, however, I can NOT get into a Live CD session with those parameters.  Nor any of the others that Pumalite and Maintech have suggested.  It always hangs up with the "(initramfs)" prompt and its error messages, as indicated in my very first posting in this thread.

Maybe I'll have to wait for Hardy Heron, which apparently allows me to run Ubuntu within Windows.  Doesn't sound like that's what I'd call a good solution.

Anybody know what I'm doing wrong?  Thanks, again,

   Dick Silbar

---

### Post by silbar on 2008-04-29
THIS, amazingly, is coming to you from Gutsy Gibbon, NOT from XP.

This thread had died about a week ago after my last posting, which indicated that I might be waiting for Hardy Heron to come out.  It has since come out, at least in the Release Candidate form (8.04 LTS).  So, I eventually got a copy, courtesy of a friend (George Brehm), who has a faster connection for the 700 MB download and who burned me a CD installation disk.

However, on trying it out, I once again invariably hit the (initramfs) error mentioned earlier.  And. I tried it with all the suggested boot parameters mentioned above -- today in ten different variations of those parameters, all to the same state of nowhere, never getting to the point of being able to install Hardy.

So, I stopped trying that and went back into XP to post an update to this thread about how I couldn't resolve the problem with Hardy.  On going to the Installations & Upgrades forum, however, I saw that there was an active thread entitled "initramfs + busybox trouble installing".  That sounded familiar enough that it was worth reading (and printing out).

OK, one of the suggestions there was to go to the BIOS and change the SATA mode setting (in my BIOS found under Integrated Periphereals) from IDE to RAID.  Or, another person said, from AHCI to RAID.  

Hmmm!?, since this machine has just one hard disk (for now), certainly not a RAID setup.  But, what the heck, why not try it?  So, I did.

On the restart, there NOW is a message saying that the AHCI BIOS is installed.  Presently, there was always a warning that it wasn't installed.  Even though the Hardy 8.04 CD was still in the machine, it somehow came to the grub menu (why, I do not know).  Well, what the heck (again), why not try to 7.10 generic bootup?  So, I did.

AND, it booted directly into the Ubuntu login sc reen, complete with sound.  So, I logged into Gutsy.  Recall, that sometime earlier I had been able to install Gutsy, just had not ever been able to back into it.

So, I consider my problem solved, even though I have no idea why RAID on a non-RAID machine did the trick.  Hoping this posting can help someone else with this problem,

   Dick Silbar

---

