---
title: "Installing the new LTS version"
date: 2010-05-04
forum: Installation &amp; Upgrades
---

### Post by bobmac on 2010-05-04
Folks,

I'm running the 8.04 LTS version complete with all the latest updates. I've noticed that there is a new LTS version ready for download.

Is there any way that I can install the new LTS version while keeping all the stuff that I have on my disk. That is, can I install the new version without losing all my information.

I'm pretty new at this but I seem to recall that there is a way to do this.

Any help will be gratefully appreciated.

Regards,

Bob

---

### Post by cuby on 2010-05-05
shure!
If you upgrade from update manager your /home will still be there, unchanged. If you have important stuff, as usual, backup it before just in case.

---

### Post by suryaccnamcse on 2010-05-05
You can also do a fresh install of the new LTS version and while the installation choose the option to install Ubuntu along with the version already installed. You will be able to choose at the boot time, which version you want to boot into... I have 9.10 and 10.04 installed on the same hard disk. I chose the advanced option...ie to install them on different partitions.

---

### Post by cuby on 2010-05-05
careful with this... if you /home is not in a different partition, if you install from cd there is a great chance you will end formatting your data.

---

### Post by Ad@m on 2010-05-05
In any event I would highly recommend you backup your files before attempting anything.

Upgrading from a previous release can cause many issues. A clean install is always the better option.

In future specify your /home directory on a different partition. By doing this you can install any ubuntu release and tell the partitioner not to format the home partition. 

This will allow you to do a clean install and preserve your files at the same time.

It will even make it easier to change to a different distribution without losing your files.

---

### Post by golfnut324 on 2010-05-05
> **Ad@m said:**
> In future specify your /home directory on a different partition. By doing this you can install any ubuntu release and tell the partitioner not to format the home partition. 

This will allow you to do a clean install and preserve your files at the same time.

It will even make it easier to change to a different distribution without losing your files.


Brand new to Linux and have just set up 9.10 to my liking. Here's my partition scheme:

Partition 1    Swap         2.0gb     /dev/sda1
Partition 2    /               30gb      /dev/sda2    Ext4
Partition 3    /home       608gb    /dev/sda3    Ext4

Now for the stupid questions: 1) Do I "upgrade" to 10.01 using update manager or clean install to root and not partition /home? 2) What happens to all my settings (i.e. desktop, icons, bookmarks, preferences, animations, etc.) 3) Will VirtualBox and other apps work the same?

I've been using Ubuntu now for about a month and every day I find new ways to eliminate dependence on XP.

Thanks for the help.
Craig

---

### Post by snowpine on 2010-05-05
It is easy to upgrade from 8.04 to 10.04, or from 9.10 to 10.04. You shouldn't lose any applications, settings, or data (though it is always a good idea to have a backup of your important files). Here are the official instructions for both options:

[http://www.ubuntu.com/getubuntu/upgrading](http://www.ubuntu.com/getubuntu/upgrading)

(edit) In my opinion, it is always a good idea to burn a Live CD of the new release and test it thoroughly on your hardware, prior to upgrading. If there are any problems with your hardware and the new release, you want to know about them before upgrading.

---

### Post by golfnut324 on 2010-05-05
Thanks for the help. Being a noob here, what's the best way to back up with Ubuntu? Is there open source imaging software you can recommend? Does it come in Ubuntu?

I'll take your advice and try out the live cd!

Thanks

---

