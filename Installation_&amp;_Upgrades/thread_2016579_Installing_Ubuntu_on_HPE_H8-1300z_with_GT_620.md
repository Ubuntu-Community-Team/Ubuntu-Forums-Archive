---
title: "Installing Ubuntu on HPE H8-1300z with GT 620"
date: 2012-07-04
forum: Installation &amp; Upgrades
---

### Post by Orbital_sFear on 2012-07-04
I bought a brand new H8-1300z and it is a bear to install linux on.

My background:
Personally I wouldn't read this paragraph.  Before everyone calls me a noob, I want to explain who I am.  I'm a professional software developer, primarily working with embedded linux systems for my day job.  I first started using linux as my main desktop in 1998 with redhat.  I have a masters degree in computer science.  I've severed as linux system admin for 3 years in college.

This only works with 32bit:
Keep in mind, I can't get ubuntu 64bit installed because the NVIDIA driver just returns an IO error.  I've tried everything from vmalloc settings to custom NVIDIA drivers, nothing seems to work.  I'm running this system in 32bit for now, and hoping when ubuntu 12.10 comes out, I'll be able to get 64bit installed.

BIOS Setup:
This HP uses UEFI, luckly it will allow you to use a legacy setting as well.  In my boot options I turned of UEFI, and setup my USB CD as the first boot.

Live CD:
Getting the live CD to boot correctly.  When the CD is first inserted, you must push escape when the man and keyboard icons show up.  Select your language, push F6, select nomodeset.  Now you can continue into a normal live cd setup.  Make sure you select try ubuntu.

Dont select updates while installing:
When installing, I selected to install 3rd party software, however if I did the updates, it will not boot.  I made sure there was no internet connection.  You should do the same.

Hard drive Setup:
For the drive setup, I've always down my own since 1998 when I first started using linux.  This is the first system where the setup of a / main, and a swap wouldn't work.  If you select the erase xxx and reinstall option, then it works, otherwise it wont boot.  I haven't investigated what is different in this option versus a simple partition setup is.  If you need custom partitions, set them up before installing, or expect to tinker to get it booting.

Before you reboot:
Before rebooting,  you'll need to setup a timeout on grub because it wont boot yet.  Click on your home folder, open the HD you just installed to.  This will ensure it is mounted.  Open a terminal.  
cd into your freshly installed dir, here is mine: cd /media/3ce1fb91-s35/boot/grub
Edit your grub config: sudo gedit grub.cfg
Change: 
set default="0" 
to
set default="1"
Save
This will force us into the recovery on the next boot, which is required to get the system online the first time.

On your first boot:
Connect your internet connection, I am using a cable, for brevity, I wont go into how to do through with wireless.
When you are presented with a list of options, start your network settings.  Now drop to root.  
Reset our grub changes made before, type: update-grub

Type startx 
When X comes up, select additional drivers program, install the updated NVIDIA driver.  When that completes reboot your system and you should be set.

At this point you should reboot your system.  Mine comes up normally.

Get Windows to boot:
Nothing yet.  I had to format the windows drive and reinstall.

I hope this helps someone.  I would recommend not buying this machine if you plan on using Linux with it.
-Orbital

---

### Post by Chatoyer on 2012-09-08
Thank you loads, Orbital_sFear, for your conscientious advice.  I might have thought twice about my purchase if I had seen this first, (but then again, I might not have, either. )

I'm looking at the live 12.04 amd-64 desktop right now, and I feel optimistic that the install shall proceed happily, too.  I'm hoping to be in touch though, in case of any hitch.  I was already practicing my tirade at Redmond for my return-trip to the computer store, but I'm more pleased now that that seems unnecessary.

---

### Post by Chatoyer on 2012-09-08
For some reason, I don't find the option to erase the fixed drive for the install.  I'm presented with the partition editor, which is non-functioning, and an error: "No root file system is defined.  Please correct this from the partitioning menu."

None of the buttons in the partition editor do anything, though.

Must the fixed drive be erased manually, before starting the install?

---

