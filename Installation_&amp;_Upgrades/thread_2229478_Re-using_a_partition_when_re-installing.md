---
title: "Re-using a partition when re-installing"
date: 2014-06-13
forum: Installation &amp; Upgrades
---

### Post by Randy M on 2014-06-13
I'm re-installing 12.04 and I need to reuse the partition on a dual boot machine. I don't want to screw things up further so my basic question is "Where do I go from here?" How do I tell it to format SDA5 and install there? I tried to upload a screen capture, but it didn't make it. Thanks for any help.

---

### Post by Randy M on 2014-06-13
I found these instructions [http://askubuntu.com/questions/339606/how-to-do-a-fresh-re-installation-of-ubuntu-safely-on-dual-boot](http://askubuntu.com/questions/339606/how-to-do-a-fresh-re-installation-of-ubuntu-safely-on-dual-boot)

Does the process explained there seem accurate?

---

### Post by oldfred on 2014-06-13
Yes, if you do not click format it is what may be called a 'dirty' install and only new files are overwritten and anything you have is still there.

       System settings or anything in / may be overwritten with defaults. Good backups still important
[https://help.ubuntu.com/community/UbuntuReinstallation](https://help.ubuntu.com/community/UbuntuReinstallation)

Other Something Else examples:

 Install to external drive. Also any second drive.
Also shows combo box with location of grub2 boot loader
[https://help.ubuntu.com/community/Grub2/Installing](https://help.ubuntu.com/community/Grub2/Installing)
Does not hightlight changing boot loader to sdb, but shows other install screenshots:
[http://askubuntu.com/questions/312782/how-to-install-ubuntu-on-separate-hard-drive-in-a-dual-boot](http://askubuntu.com/questions/312782/how-to-install-ubuntu-on-separate-hard-drive-in-a-dual-boot)
[http://askubuntu.com/questions/274371/install-on-second-hard-drive-with-startup-boot-option](http://askubuntu.com/questions/274371/install-on-second-hard-drive-with-startup-boot-option)
Install 14.04 Something Else explanation and screenshots (note boot load to VM, most may install to MBR of drive sda, or sdb)
[http://www.tecmint.com/ubuntu-14-04-installation-guide/](http://www.tecmint.com/ubuntu-14-04-installation-guide/)
And you want this screen to choose where to install the grub2 boot loader which is only available with Something Else or manual install
[https://help.ubuntu.com/community/Grub2/Installing#Installing_Ubuntu_to_a_Specific_Partition_.28.22Something_Else.22.29](https://help.ubuntu.com/community/Grub2/Installing#Installing_Ubuntu_to_a_Specific_Partition_.28.22Something_Else.22.29):

---

### Post by Randy M on 2014-06-13
Thanks oldfred, there's a wealth of information in that response.

---

### Post by kansasnoob on 2014-06-13
Just FYI I got here from here:

[http://ubuntuforums.org/showthread.php?t=2229403](http://ubuntuforums.org/showthread.php?t=2229403)

And I have a couple of things to add :)

You're talking about reinstalling 12.04 because an upgrade from 10.04 to 12.04 failed (or 12.04 blew up shortly thereafter). I just want to be sure you consider which version of Ubuntu to install. First consider the life cycle:

[https://wiki.ubuntu.com/Releases](https://wiki.ubuntu.com/Releases)

As you can see there 12.04 (aka Precise) is supported until April 2017 whereas 14.04 (aka Trusty) is supported until April 2019.

I personally find Precise to be a bit more "friendly" to work with ATM but I also find Trusty to be stable enough with only a few minor annoyances (no show-stopper bugs). From that original thread I assume you're interested in the "classic" style session and it can be used in either Precise or Trusty but you may want to give this a quick browse before deciding:

[http://ubuntuforums.org/showthread.php?t=2220264](http://ubuntuforums.org/showthread.php?t=2220264)

Now, I'm not done messing with your mind just yet ;)

If you do decide to use Precise rather than Trusty you also need to consider the LTS hardware enablement policy:

[https://wiki.ubuntu.com/Kernel/LTSEnablementStack](https://wiki.ubuntu.com/Kernel/LTSEnablementStack)

In a nutshell; if you download Precise from the standard download page you'll get 12.04.4 which is the 4th point release of Precise and it has the Saucy kernel and X-stack so you'll be faced with an upgrade to the Trusty kernel and X-stack in July or August :(

Therefore I personally prefer using the archived 12.04.1 images for my Precise re-installations since they have the actual Precise kernel and X-stack which are supported throughout April 2017:

[http://old-releases.ubuntu.com/releases/precise/](http://old-releases.ubuntu.com/releases/precise/)

So, if I were you I'd either install Trusty or use the 12.04.1 image to install Precise.

---

### Post by oldfred on 2014-06-13
Just to add that I am running fallback/flashback or gnome panel in both 12.04 and 14.04 following mostly kanasnoob's directions. My 12.04 does not include the enablement stack.

My laptop is too old to run Unity and my desktop has a 4:3 monitor so top & bottom panel make more sense. But I want the standard Ubuntu's packages. Plus oldfred does not easily change from old gnome2 style menus.

---

