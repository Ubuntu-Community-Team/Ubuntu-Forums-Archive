---
title: "Newly installed Kubuntu boots to Windows instead"
date: 2012-10-04
forum: Installation &amp; Upgrades
---

### Post by pwabrahams on 2012-10-04
I just finished installing Kubuntu 12.04.1 on my laptop, which already had Windows 7 installed.  The Windows boot partition is sda1; the Kubuntu boot partition is (or is supposed to be) sda6.  The installation had a couple of minor burps that I didn't worry about.  But now, when I reboot, I get into Windows rather than Kubuntu.  I was expecting to see the Grub2 screen, offering me a choice of systems to boot to.  I think I can get into Kubuntu by booting into SuperGrub, but I shouldn't have to.  What might have gone wrong?

---

### Post by jrog on 2012-10-04
> **pwabrahams said:**
> I just finished installing Kubuntu 12.04.1 on my laptop, which already had Windows 7 installed.  The Windows boot partition is sda1; the Kubuntu boot partition is (or is supposed to be) sda6.  The installation had a couple of minor burps that I didn't worry about.  But now, when I reboot, I get into Windows rather than Kubuntu.  I was expecting to see the Grub2 screen, offering me a choice of systems to boot to.  I think I can get into Kubuntu by booting into SuperGrub, but I shouldn't have to.  What might have gone wrong?
Is this a newer machine? You say that /dev/sda1 is the "Windows boot partition;" does that mean that there is a separate small partition for booting at the front of the drive? I'm asking because I'm wondering if your problem is (U)EFI-related. This is a typical symptom of such cases.

---

### Post by pwabrahams on 2012-10-04
Yes, it's a new machine -- a Lenevo Z580.  It came with 4 primary partitions, so I had to go through some gyrations to make a partition available for Linux.  Right now the configuration is:

  sda1  Windows boot
  sda2  Windows C:
  sda3  Extended
  sda4  Windows recovery (I think)
  sda5  Windows D:
  sda6  Kubuntu /
  sda7  Kubuntu /home
  sda8  Linux swap

I don't know anything about (U)EFI -- that's not the kind of information that laptop makers provide to buyers.

Now I'm wondering -- am I going to wreck something if I install Grub using grub-install?

---

### Post by Bashing-om on 2012-10-05
pwabrahams; Hi !

It does appear that sda1 (as stated windows boot ) is UEFI, and that does present a problem, that is surmountable, to install grub properly. A bit more effort on your part.

Here are the relevant links with background info to resolve:
[http://ubuntuforums.org/showthread.php?t=2059640 dual boot & UEFI advise](http://ubuntuforums.org/showthread.php?t=2059640 dual boot & UEFI advise)
[http://ubuntuforums.org/showthread.php?t=1974392](http://ubuntuforums.org/showthread.php?t=1974392)
[http://ubuntuforums.org/showthread.php?t=2064761](http://ubuntuforums.org/showthread.php?t=2064761)
[https://gitorious.org/tianocore_uefi_duet_builds/pageshttp://](https://gitorious.org/tianocore_uefi_duet_builds/pageshttp://)

To verify UEFI:
You can find out by typing "bcdedit" in a Windows Administrator Command Prompt window and looking for the "path" line in the "Windows Boot Loader" section. If this line refers to winload.efi, then you're booted in EFI mode; if it refers to winload.exe, then you've booted in BIOS mode.[INDENT]HTH <==BDQ

[/INDENT]

---

### Post by pwabrahams on 2012-10-05
The instructions at [https://help.ubuntu.com/community/UEFIBooting]("https://help.ubuntu.com/community/UEFIBooting") are for Ubuntu, not Kubuntu.  They involve a "boot repair" step that doesn't seem to exist (or at least I can't find it) after the reboot of Kubuntu.

---

### Post by Wim Sturkenboom on 2012-10-05
If I understand it correctly, you can install (temporarily) bootrepair while using the liveCD.

If you have used a liveUSB with persistence, it can be permanently installed on the liveUSB.

---

### Post by jrog on 2012-10-05
> **Wim Sturkenboom said:**
> If I understand it correctly, you can install (temporarily) bootrepair while using the liveCD.

If you have used a liveUSB with persistence, it can be permanently installed on the liveUSB.
This is correct, though I believe that installing Boot Repair while using the LiveCD requires adding a PPA. An alternative is downloading the Ubuntu Secure Remix LiveCD and using that as a LiveCD; it comes with Boot Repair on it.

pwabrahams, based on the partitioning of your disk and the issue you are having, it is a virtual certainty that your computer is booting in (U)EFI mode. For help on resolving your issue, read this page (different from the one you linked earlier): [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

You will likely be able to resolve this by performing steps #1 and #4 at the beginning of that document. In short: burn the Ubuntu Secure Remix to a CD, use it as a LiveCD, and then do the rest of what is said in step #4. (Differences between Ubuntu and Kubuntu won't matter here; the LiveCD for Ubuntu Secure Remix will be used only to set up GRUB properly.)

---

### Post by pwabrahams on 2012-10-05
Those instructions leave out a critical step: how to start up a Ubuntu terminal if you're not familiar with Ubuntu.  Ubuntu confronts you with an essentially featureless desktop, with no obvious way to bring up your chosen application.  (That's part of why I prefer Kubuntu.)

---

### Post by jrog on 2012-10-05
> **pwabrahams said:**
> Those instructions leave out a critical step: how to start up a Ubuntu terminal if you're not familiar with Ubuntu.  Ubuntu confronts you with an essentially featureless desktop, with no obvious way to bring up your chosen application.  (That's part of why I prefer Kubuntu.)
The instructions do show you how to start an Ubuntu terminal, though I suppose it's easy to miss: "open a terminal (Ctrl+Alt+T)."

EDIT: Also, to get to your applications in Ubuntu, you can generally click on the Ubuntu logo on the launcher (top left side of the screen) -- or hit your Windows key, if you have one -- and, when the Dash shows up (the window with the transparent blurred background), either type in what you're searching for or click the icon for Applications (the thing that looks like a ruler and a pencil and maybe a pen) and browse through them.

---

### Post by pwabrahams on 2012-10-05
Thanks to all for your help in making these instructions work in Kubuntu as well as in Ubuntu.  I've edited the help page in the wiki ([https://help.ubuntu.com/community/UEFI?highlight=%28%28UEFI%29%29]("https://help.ubuntu.com/community/UEFI?highlight=%28%28UEFI%29%29") to reflect this extra information.  Some of the participants in this conversation might want to look at my edits and improve (or correct) them further.

---

### Post by jrog on 2012-10-05
> **pwabrahams said:**
> Thanks to all for your help in making these instructions work in Kubuntu as well as in Ubuntu.  I've edited the help page in the wiki ([https://help.ubuntu.com/community/UEFI?highlight=%28%28UEFI%29%29](https://help.ubuntu.com/community/UEFI?highlight=%28%28UEFI%29%29) to reflect this extra information.  Some of the participants in this conversation might want to look at my edits and improve (or correct) them further.
Glad it worked out! Can you please mark the thread as solved (using "Thread Tools" at the top of the page) when you get a chance?

---

