---
title: "Trying to burn ubuntu 14.04 installation DVD"
date: 2014-07-26
forum: Installation &amp; Upgrades
---

### Post by AlyssaVS on 2014-07-26
I am trying to install ubuntu 14.04 to an older laptop that has 13.10 on it. I'd like to do a fresh install. The laptop I am currently using has 14.04 and I am trying to burn a DVD for the install to the other one. I have actually done this before (burn an installation DVD) so am a little frustrated that this is giving me trouble. Every step by step direction simply states "find the iso file" and then write that to disk. After the download there are multiple folders and I have spent a lot of time trying to locate "the iso file." Can somebody please explain to me HOW to locate this iso file. They make it sound so simple but I CANNOT find it. or figure out which one is "the iso file" I need to burn.

Thank you!

---

### Post by grahammechanical on 2014-07-26
Let us suppose that you download the ISO image from here:

[http://www.ubuntu.com/download/desktop/](http://www.ubuntu.com/download/desktop/)

or here

[http://cdimage.ubuntu.com/trusty/daily-live/current/](http://cdimage.ubuntu.com/trusty/daily-live/current/)

And you use a web browser to download. If this is being done in Ubuntu then by default the web browser will download the ISO image to the Downloads folder. Open the File Manager and open the Downloads folder and look for a file called trusty-desktop-amd64.iso.

Put a DVD writeable disc in the DVD drive. Allow a few seconds for the OS to mount the DVD disc. In the File Manager right click trusty-desktop-amd64.iso and from the menu select Write to Disc...

A dialog will appear that will ask for your authentication to write to the disc and over-write anything on the disc by blanking it. Then the burning of the ISO image to the disk will take place and at the end the disc will be ejected and you can close the application window.

By the way, the browser should tell you the name of the file that is being downloaded.

Regards.

---

### Post by kansasnoob on 2014-07-26
I like to use Brasero, in fact I'm just going to burn Ubuntu GNOME 14.04.1 i386, so first open Brasero and click on Burn image. That opens the Image Burning Setup:

[ATTACH=CONFIG]255053[/ATTACH]

There I click on *Click here to select image* - mine is in a sub-folder named Ubuntu_GNOME in Downloads:

[ATTACH=CONFIG]255054[/ATTACH]

Once selected a mouse hover allows me to see the full path to the image, but we need to click on Properties:

[ATTACH=CONFIG]255055[/ATTACH]

Once that opens you'll see that Maximum speed is set by default but **you should always select the lowest possible speed for iso burning**:

[ATTACH=CONFIG]255056[/ATTACH]

Once that's done and you click on close you're ready to burn:

[ATTACH=CONFIG]255057[/ATTACH]

It's always good to enter the Advanced boot options and run Check disc for defects after creating a new image:

[https://help.ubuntu.com/community/BootOptions#Ubuntu_CD_Advanced_Welcome_Page_Options](https://help.ubuntu.com/community/BootOptions#Ubuntu_CD_Advanced_Welcome_Page_Options)

BTW, don't be surprised if you see this bug when inserting a blank DVD:

[https://bugs.launchpad.net/ubuntu/+source/unity-settings-daemon/+bug/1069964](https://bugs.launchpad.net/ubuntu/+source/unity-settings-daemon/+bug/1069964)

---

### Post by AlyssaVS on 2014-07-27
Got it done. Turns out the package was mounted to the toolbar right after the download like it was occupying it's own drive. Once I unmounted it, the iso file appeared in the downloads folder for me to right click on. Never seen anything like that. I thought I was going crazy.

Thanks for your responses!

Now to proceed to another section of the forums. After two attempts at fresh installs... applications won't open and everything is horribly slow and freezes. Sigh, Lol. Wish me luck.

---

