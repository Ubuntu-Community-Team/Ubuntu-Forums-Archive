---
title: "Installing ubuntu on Gateway Solo 5150 laptop"
date: 2006-11-22
forum: Installation &amp; Upgrades
---

### Post by T_MAC on 2006-11-22
I'm a new user to Ubuntu, and I'm trying to install it on a  Gateway Solo 5150 laptop.

Its a PII processor
366Mhz
128 MB of RAM

I have been tring to get the 6.0.6 installer to work.

If I try the Live CD it stalls out at "Mounting root file system".

Then defaults back to the "Uncompressing Linux... Ok, booting the kernel." screen. 

If I add to the boot menu: acpi=ht pci=conf2
I get to the point of "Configuring X..", but then a Blue screen.

If I try the Alternate installer in text mode, it gets to the point just after detecting hardware and then stalls out at a blue screen.

Any help would be appreciated.

Thanks,
T_MAC

---

### Post by DFLiddle on 2006-11-22
Try changing the display mode (F4?) at the boot menu from VGA to 640x480 (16-bit). I had to do this for a Dell Latitude C400 after several puzzling attempts. Now I think I'm going to try Xubuntu on a Solo notebook like yours.

---

### Post by T_MAC on 2006-11-29
I tried changing the video settings for the boot listings but it didn't help.

I then installed Xubuntu 6.0.6, using the Alternate CD, and selecting just the server install. Using acpi=ht pci=conf2 as boot settings.

It installed the base system so all I have is the command prompt. 

I then logged into the system mounted the CD with:
sudo mount /cdrom

then ran:
sudo apt-get install xubuntu-desktop

It looked like it was installing but I got message:
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem.

So I ran:
sudo dpkg --configure -a

It says:
Setting up xserver-xorg (7.0.0-0ubuntu45)...

Then Freezes. It goes to a blue screen where I cant do anything. Mouse and keyboard dont work.

Any suggestions?

Thanks,
T_MAC

---

