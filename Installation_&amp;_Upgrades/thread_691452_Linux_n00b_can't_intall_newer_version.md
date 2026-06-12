---
title: "Linux n00b can't intall newer version"
date: 2008-02-08
forum: Installation &amp; Upgrades
---

### Post by agent_smart on 2008-02-08
^That's "install."  sorry.

My mom's computer has Linux, and really, none of us know how to use it.

A couple of years ago, the computer was running on Windows, and it was going much faster.  It takes like 30 seconds for a page to load, and it's enough to make one kill oneself.

I noticed that her version of Ubuntu is out-of-date, so I'm trying to upgrade it.  Update manager does not notify me of newer versions.  It tells me that the distribution is no longer supported and tells me to visit [www.ubuntulinux.org](www.ubuntulinux.org) to... find out about that.  I know that this version is 5.10, so I have to upgrade to 6.06, but following the directions is getting me nowhere, because:

1. Update manager isn't working as the directions say it should.
   when I do this: "Make sure your system is using this repository. Confirm that you have version "0.42.2ubuntu12~breezy1" or newer of Update-manager installed, using the "Synaptic Package Manager" application. You need to ensure that your system is aware of what the latest versions are. If your system is not automatically checking for the latest updates, turn it on or do it manually. (In Synaptic go to menu "Settings -> Repositories", then the "Settings" button.
          o

            If the check box "Automatically check for software updates" is off,
                +

                  turn it on, or
                +

                  do it manually via either the "Reload" button or menu "Edit -> Reload Package Information").
    *

      Then, still in "Synaptic Package Manager", update "Update Manager" to the latest version and quit "Synaptic Package Manager"."

...there is no option to update "Update Manager".

Also, the option to periodically update IS checked off, but the computer never offers to update anything.

2. I don't have a c.d.

3. even if I did, or I wanted to upgrade through using commands (do I even know what I'm saying?) I don't think I have this "ubuntu-desktop" thing, which is "VITAL" to having it install the right way.



Can I just download the entire version and extract it??
I'm guessing not, since that wasn't one of the options.

What do I do?

---

### Post by bwhite82 on 2008-02-08
Being that your install is very outdated, it would be more of a headache (IMO) to upgrade rather than just backing up your data and doing a clean install. You can either download a disk image and burn a CD:

[http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download)

Or you can order a free CD (it will take a while to receive it):

[https://shipit.ubuntu.com/](https://shipit.ubuntu.com/)

Or you can purchase a CD/DVD:

[http://www.ubuntu.com/getubuntu/purchase](http://www.ubuntu.com/getubuntu/purchase)

---

### Post by zvacet on 2008-02-08
Be sure that you have all repositories open.Look [this](https://help.ubuntu.com/community/Repositories/Ubuntu) page on place where they describe how to do it in Dapper,because it is same in Breezy.If you allready did that even better.All you need to do is make sure that your Breezy is up-to-date.Type in terminal

```
sudo apt-get update && sudo apt-get upgrade
```

Backup all your valuable date on some safe place and you are ready for upgrade.

---

### Post by agent_smart on 2008-02-09
Thanks, both of you, for your advice.  My mom doesn't have much on her computer... I wonder if I could put it all onto a 1G jump drive.  

How do I get to the terminal?  Does the process automatically format the hard drive during installation?

---

### Post by Partyboi2 on 2008-02-09
For a terminal 
go to Applications>Accessories>Terminal
If you are upgrading from the net it will not format your drives.

---

### Post by zvacet on 2008-02-09
All  data and files you want to keep burn to CD/DVD or put on stick.If you don´t have separate home partition you will lose all settings and files wich are now in home directory.You can export your adressbook,bookmarks...and send to yourself by e-mail.Well,after all these things you can do upgrade.Program>accessories>terminal and type 

```
sudo apt-get update && sudo apt-get upgrade
```

After this package manager should give you option to upgrade.

2.Maybe it is better to download Dapper or Gutsy (recent Ubuntu version ) and do clean install.This time create separate home partition during install.You can read instrtuctions for install [here](http://www.psychocats.net/ubuntu/installing).

> Does the process automatically format the hard drive during installation?

All these I told you in short means yes.It will format your root partition and if that is only one you have (aside of swap) all your files and datas will be erased.If I´m not giving you clear enough explanation just ask what do you want to know.

---

