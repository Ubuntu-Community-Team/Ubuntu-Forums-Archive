---
title: "Turn on Computer  Black Screen after failed xubuntu installation"
date: 2013-02-03
forum: Installation &amp; Upgrades
---

### Post by trindade on 2013-02-03
Hi All,


I have decided to try and step away from windows and give xubuntu a go.
I created a bootable usb drive with the latest x64 12.10 and ran it. I tried to run the installation and it gave a few errors  which i ignored. I believe one was kernel related and the other was about something not being able to be verified until after reboot. So i selected the region got these errors it failed.
I chose the remove windows 7 option and install xubuntu.
Since it wasn't working i decided to reboot and start over.
Unfortunately I have only a black screen in front of me. I tried looking online and found some sort of boot repair tool. created a bootable usb drive with the repair tool and turned on the pc but the screen is black.
It is just black no logos nothing.

How can i get it to work?
I kno my description was a bit vague but i didn't pay attention to the errors because on windows i just click on next next next and it all somehow works and if it doesn't i figure it out. This is something so new to me that i have no idea of what to do.

---

### Post by Bashing-om on 2013-02-03
trindade; Hi ! Welcome to the forum.

It is regretful that you are experiencing such difficulties. From your description I surmise that the install medium is corrupted. 
Verify the check sum on the .iso file and reburn that .iso as an image.
[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

Then verify the integrity of the burned image:
Boot the install usb, at the purple splash screen (stick figure and keyboard images at bottom of screen) press any key -> language screen, press escape key to accept default language ->boot options screen;
select "to verify the disk".

Once past all these checks, still with a problem, a likely issue is graphics related, or maybe UEFI settings in bios ? 
[INDENT]one step at a time and we will see

[/INDENT]

---

### Post by trindade on 2013-02-04
Hey! thanks for your reply.

I have downloaded [PC (Intel x86) desktop image]("http://releases.ubuntu.com/12.10/ubuntu-12.10-desktop-i386.iso").
I believe i downloaded the AMD earlier and strangely I didn't even notice, which is strange because the iso has amd labelled on it.

I will try out what you suggested tomorrow when i have some free time

---

### Post by trindade on 2013-02-05
hey i have given it a try.
created isos both on usb and cd and it didnt work. even tried previous versions of xubuntu and it did not work.

Tried with a working windows cd to get it back to previous state and the cd is not being read.

I simply turn on the computer and i see a black screen. I put the cd and it makes the noise as if its loading something but nothing appears.

I have tried pressing several combinations of keys to no result.

BIOS is not accesible.

is my laptop now forever going to be a paper brick?

---

