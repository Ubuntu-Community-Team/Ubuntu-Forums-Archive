---
title: "Re-install to fix missing file?"
date: 2011-01-02
forum: Installation &amp; Upgrades
---

### Post by MattOsprey on 2011-01-02
Hi guys,
I have a Dell mini 9 or 10 (not sure which one) running Ubuntu 8.04. When trying to watch youtube clips it says install missing plugins. I have tried most of the work arounds on these forums but can't get it to work. I have therefore downloaded the latest version of Netbook Ubuntu and put it on a pendrive. 
Can someone kindly tell me if installing the new Ubuntu will solve my problem and how do I do this?
I am okay on a computer but not great. I am after step by step instructions on how to uninstall and then install.
All advice is greatly appreciated.
Thanks.
Matthew

---

### Post by davec64 on 2011-01-02
Once you've carried out your installation have a look in the Software Centre for Ubuntu Restricted Extras.
This will then install all the codecs etc needed which couldn't be included due to licensing issues. :)

---

### Post by MattOsprey on 2011-01-02
Thanks Dave.
Can you tell me if I should install the new version and then remove the old, or uninstall then install.
Is it just a question of putting in the pendrive in to the Dell on start up after the other version has been uninstalled.
Thanks.
Matthew

---

### Post by davec64 on 2011-01-02
Hi Matt,

First off, back up any documents and settings you want to keep!

When you downloaded 10.10 and put it on the Pen Drive did you just copy the downloaded file to the Pen Drive or did you go through the process of making the Pen Drive bootable by using **Startup Disk Creator**?

If you didn't, here's a guide to set things up correctly:

[https://help.ubuntu.com/community/Installation/FromUSBStick]("https://help.ubuntu.com/community/Installation/FromUSBStick")

As far as upgrading to the latest version, you've got 2 options:

1. Using the Pen Drive and wiping the previous installation during the installation. There's an option as you go through the process to use the entire disk. That will wipe format the disk and then install the latest version from he Pen Drive.

2. It's also possible to upgrade from 8.04 through to 10.10 using the Update Manager. With this method you need to ensure a tick box is checked somewhere in the settings which will make the upgrades visible. If memory serves me right the upgrade would be from 8.04 to 10.04 to 10.10. I think 8.04 was an LTS version so you can jump to the next LTS version (10.04) and then to 10.10. I've never used this method so you'll need to search the forum for more info.

Which method to use?
It's really down to personal preference! You can read lots on the forum as to which is best, so I'll stay out of that argument! :)

I use Option 1 each time and a fresh install.

Something to think about is whether to partition your disk manually. By this I mean making a separate partition for your **home** directory. Doing this makes life easier in the future when you install the latest version as you can keep the home partition intact keeping all you documents and settings, But if your a little nervous of manual partitioning just stick with the straight forward automatic install.

I think I've covered everything but shout if you need anymore help! :)

---

### Post by oldos2er on 2011-01-02
Ubuntu doesn't come with flash, so reinstalling it won't solve your original problem. To install flash, open a terminal and run ```
sudo apt-get update && sudo apt-get install flashplugin-nonfree
```

---

### Post by davec64 on 2011-01-02
oldos2er is right, I missed the first part of your post! Sorry!

Have a look at the package Ubuntu-restricted-extras, I think tat has Flash in it along with several other non free codecs which might be useful for the future.

If you still want to upgrade to the latest version my advice still applies. :)

---

