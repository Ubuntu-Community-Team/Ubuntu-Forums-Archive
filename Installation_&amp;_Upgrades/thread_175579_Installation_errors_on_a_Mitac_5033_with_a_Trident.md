---
title: "Installation errors on a Mitac 5033 with a Trident Video Accelerator"
date: 2006-05-13
forum: Installation &amp; Upgrades
---

### Post by oli888 on 2006-05-13
Hi

I tried to install Ubuntu Breezy Badger on my Mitac 5033 laptop. The graphics card is a Trident Video Accelerator.

Here are my problems:

1. Sometimes the installation crahsed. However, this could normally be solved by moving the mouse every couple of minutes.

2. Usually, the following error message was displayed:

"Base System Installation Error. The debootstrap program has exited with an error (return value 1)" and then it gives a file which I don't know how to open without an operating system.

3. One time I was lucky and managed to get Ubuntu installed. However, when the logon screen was shown, it was in the wrong place - it was split all around my screen.

NORMAL DISPLAY:

1     2

3     4

DISPLAY AFTER INSTALL:

-     -

2     1

(where "1", "2", "3", and "4" are the 4 quarters of the screen and "-" is when nothing is displayed)

After this I checked the Ubuntu installation guide and it said that I should have a choice of resolutions. However, I did not get this, so I decided to re-install on expert mode (using boot:expert). Since then, I have tried about 10 times to install Ubuntu but I get the debootstrap error described above. I get through about 33% of the installer when this message is displayed. This has happened with both Ubuntu Breezy Badger and Debian 3.1. Both CDs pass the disc integrity check before the error message is displayed but not afterwards. A different file fails the check each time.

Is there a solution to my problems?

Thanks in advance for any help you can offer,

Oli

---

### Post by Avionix on 2006-05-13
Hi oli888,
your video error sounds very similar to mine,  also on a Mitac 5033 with trident video chipI have played about with the resolutions to no avail. I found some info on another forum, a mandrake installation forum I believe it was, here is what is says regarding the installation of X "the onboard trident video chip is very picky about resolution, colour depth and refresh rate.You should choose XFree 4.1.0 with a resolution of 800 X 600, a colour depth of  65 thousand colours (16 bits) and a 'generic laptop display panel 800x600'. If you have a Mitac MiNote 5033 with a 1024 x 768 screen, you have to change these settings accordingly"
Unfortunately I don't know enough about Linux to get and install XFree 4.1.0 and then configure it especially as I have to do everything on the Mitac laptop using the command line and I have not connected it to the internet yet.
Hopefully the above will make some sense to you.

---

### Post by oli888 on 2006-05-14
I'm new to Linux to so I don't know how I can adapt it for Ubuntu. I hear that its easy to switch between Linux distributions so I'll try installing Mandrake and then change to Ubuntu (hopefully).

Thanks for your help,

Oli

Edit: I have found that you can install Knoppix to the HDD successfuly by loading the Knoppix live CD and typing the following into the command line:

sudo knoppix-installer

---

