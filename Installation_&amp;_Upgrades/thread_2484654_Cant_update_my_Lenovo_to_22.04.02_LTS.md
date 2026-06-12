---
title: "Cant update my Lenovo to 22.04.02 LTS"
date: 2023-03-05
forum: Installation &amp; Upgrades
---

### Post by daveyb415 on 2023-03-05
Lenovo G505s / Memory 5.0 GiB / AMD A10-5750M APU with Radeon HD graphics x4
64 bit Disk has 900GB free space

This machine hasn't been used in 4 or 5 years. It is running 16.04 LTS.  The challenge is it will not connect to wireless or a direct plug in to internet router.  The USB port doesn't recognize any USB sticks. 

I can get into the terminal. I am not a savvy computer person however I can follow directions well.  

This is still a pretty good machine if I can get it upgraded.

---

### Post by MAFoElffen on 2023-03-06
Is it Desktop or Server Edition?

And you are saying that it will not connect to the internet via wired nor wifi?

And it will not recognize any usb devices?

So, if all that is true, then it seems that it is locked away from the world. If it does not connect to any netwroks, you can't even download a package. Without USB, you cannot run a LiveCD, connect a USB thumb drive to copy packages over to it, nor connect a USB network device...

What does it do?

---

### Post by Impavidus on 2023-03-06
So the OS doesn't respond to usb drives when inserted? And the bios/uefi doesn't see them either?

Maybe it just needs a good cleaning.

---

### Post by daveyb415 on 2023-03-06
I does not connect to the internet.  It is desktop version of Ubuntu.  I tried to reboot it with the boot USB plugged in and it did not recognize it, nor does it recognize just a USB plugged into the machine once it boots up. 
The OS boots up to the desktop, it runs the programs that are on it.  It just will not interact outside of the harddrive.  This was a machine I purchased for my daughter when she started high school in 2016.  Somehow the CD Rom unit in the machine is broken. arrggh!!

---

### Post by daveyb415 on 2023-03-06
A good cleaning? How could I do that?

---

### Post by guiverc on 2023-03-07
I have a machine here with Ubuntu 16.04 LTS Desktop...  thus it uses the Unity 7 desktop. I kept it there as it was only rarely used (*the device when used is just used as a media player** which is barely twice a year*), and a *release-upgrade* would bring that desktop to GNOME as used by Ubuntu 18.04 LTS Desktop; alas the idea of GNOME desktop didn't appear to me. 

 As I don't really want the GNOME Desktop, I decided I'd do a *non-destructive* re-install of a later *flavor* desktop to have it moved to 20.04 (*or now 22.04; I decided to do this back in 2020*) but for more than two years I've been unable to decide what *flavor* so it remains undone.

With internet working; you can still *release-upgrade* a 16.04 system to 18.04 HOWEVER depending on where you are in the world, it maybe too late for you as your system may have *expired* certificates for your location (*unless ESM upgrades have been applied*) & thus it won't work as it detects issues (*expired certificates*) & won't proceed due to problems.  I tried this on my system a few months ago & had the upgrade was available & I started it (*then aborted it so the system remained on 16.04; I was answering a support question only & was using my box to confirm it was still available** which it was at that time*), and just tried again in the last ~15 mins and yep (*it downloaded the bionic tarball & gpg keys without issue & [I]it estimates >30 minutes download time, a few hours install time*)...[/I]

The *release-upgrade* will require (*my understanding*)

- internet working
- you're in a location where your certificates are still valid (*I've read many reports from others elsewhere in the world where they can't proceed here because they need to upgrade certificate files; those packages are only available if they have ESM enabled, I don't have ESM enabled but I'm geo-location-lucky I guess*)

To upgrade via re-install (*what I intended doing with my box; only couldn't decide what flavor to do it with*), you'll need a working USB port & thumb-drive with ISO written/burnt with the release you want to move to, and if you want the non-destructive re-install to restore all your *manually-installed *packages (ie. *those you'd added to your box after your initial install*); you'll need internet to be working too.

For releases up to 20.04 you can use a DVD or *optical* media instead of USB drive; if lucky you can with 22.04 too, but it'll be very slow and I'd not recommend it (*in QA I found it can take up to three installs if your box is old & slow like some of the boxes I use in QA*).

*FYI:  I just started my 16.04 boxes release-upgrade off to 18.04; I likely won't cancel it it this time..*

---

### Post by guiverc on 2023-03-07
Also asked at [URL="https://askubuntu.com/questions/1458134/lenovo-g505-running-16-04-lts-does-not-read-usb-boot-stick"]https://askubuntu.com/questions/1458134/lenovo-g505-running-16-04-lts-does-not-read-usb-boot-stick


[/URL][I][SIZE=1]My 'release-upgrade' is still installing packages, now two hours after my prior comment...   A upgrade via re-install would have been all done in less than 30 minutes (closer to 20 I suspect) I know, though that's not counting the ~two years of me trying to work out what flavor to re-install instead of Ubuntu Desktop of course.

(in fact I've performed a 'Upgrade via re-install' ('Repair install') during the last two hours too (on an older & slower box) done as a QA test)[/SIZE]


[/I]I just started a QA-test on a

```
lenovo g560 (i5m-480, 4gb, i915)
```

and to boot external thumb-drive, I had to
- insert thumb-drive
- quickly press F12 so I was asked what to boot; I selected the Sandisk thumb-drive

DO NOTE: I actually had to restart box **twice** before I pressed the F12 fast enough that it asked me to select what to boot, and didn't boot to the grub on the installed OS(es) on this box. 

This is mentioned as I believe this is the closest box I have in my QA (*Quality Assurance*) hardware... to your lenovo g505s

---

### Post by daveyb415 on 2023-03-07
Wil try that, THx.  F12-my fate is your hands.

edit: The F12 did not initiate anything. The escape key is what interrupts the boot process.  The USB is not a choice.  This machine is locked up. Appreciate the help but I found DVD/CD replacement so I will change out the broken unit and hopefully I can get that to read a boot disc. 

THx-d

---

### Post by Impavidus on 2023-03-07
Try the lsusb command. It will list all connected usb devices (some may be fake). Insert a usb drive and try it again. Is it listed? Maybe your usb stick is detected, but cannot be mounted, so isn't shown.

If you haven't used a computer in a long time, the usb ports may be covered in dust, oxide or fatty deposits, preventing good electrical contact. You can clean them similar to how you clean your kitchen, or your bicycle. But keep in mind that some chemical cleaning agents not only react with copper oxide or fat, but also with plastic or aluminium. That is to be avoided. You don't want to dissolve your computer.

---

### Post by MAFoElffen on 2023-03-07
Lenovo laptop. Things wrong: Ethernet, Wifi, USB ports...

Please post the results of 
```

lspci -v

```
Then try to reset your BIOS to defaults...

Set your BIOS back up to what you need to for Ubuntu... 

Then reboot and run the above again...

Just making sure there isn't something there causing this. Something that stuck out from my Lenovo Warranty Service certs...

---

### Post by lucant on 2023-03-10
In my old Lenovo, there was a hole on the left side, where if I inserted the tip of a 0.5 pencil, the boot option would open.

---

