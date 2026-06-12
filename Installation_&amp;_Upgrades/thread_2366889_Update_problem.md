---
title: "Update problem"
date: 2017-07-23
forum: Installation &amp; Upgrades
---

### Post by John_Rose on 2017-07-23
Hello, I have Ubuntu 12.04, that I would like to upgrade to 14.04, but first I have a problem. When I launch the package manager, it does not open, only an error message "Impossible d'initialiser les données sur les paquets" [sorry I am working with the French system but would like to correspond in English]. I tried the solution at [http://ubuntu.5.x6.nabble.com/probleme-mise-a-jour-td786218.html](http://ubuntu.5.x6.nabble.com/probleme-mise-a-jour-td786218.html) but get the following message from the terminal:

E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/apt/lists/linux.dropbox.com_ubuntu_dists_precise_main_i18n_Translation-en
E: The package lists or status file could not be parsed or opened.
root@JOHN-PC:/home/john# apt-get upgrade
Reading package lists... Error!
E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/apt/lists/linux.dropbox.com_ubuntu_dists_precise_main_i18n_Translation-en
E: The package lists or status file could not be parsed or opened.

What to do? Thanks and best wishes, John

---

### Post by John_Rose on 2017-07-23
Seems now to be solved. I deleted /var/lib/apt/lists as per [https://askubuntu.com/questions/180837/apt-lists-in-var-lib-apt-lists-overwritten-with-html-page-for-starbucks-wifi-te#180847](https://askubuntu.com/questions/180837/apt-lists-in-var-lib-apt-lists-overwritten-with-html-page-for-starbucks-wifi-te#180847) and got the package manager back. Sorry will get back to you if further problem. Thanks and best wishes, John

---

### Post by John_Rose on 2017-07-23
Hello,

I tried to upgrade from Ubuntu 12.04 LTS to 14.04 LTS by using the following commands:
sudo apt-get update
sudo apt-get upgrade
sudo do-release-upgrade

The first two commands ran normally but the last command stopped/blocked (no error message) after running for perhaps about an hour at a line containing "trusty/main textlive-latex-extra-doc".

I had to exit the terminal and then (probably stupidly) tried to get back the original system by running:
sudo apt-get update
sudo apt-get upgrade

It did a lot of installation for about 2 hours and exited normally.

After that the system boots normally as 12.04 LTS (kernel 3.2.0-126-generic) [except that the package manager doesn't load and some of the program menu items are in English instead of French as before], but when I run "lsb_release -a", it gives:

Description:    Ubuntu 14.04.5 LTS
Release:    14.04
Codename:    trusty

Then when I try to upgrade to 14.04 with "sudo do-release-upgrade", it aborts with the following results [sorry some is in French because my system is in French]:

Checking for a new Ubuntu release
Prendre :1 Upgrade tool signature [836 B]                                      
Prendre :2 Upgrade tool [1 265 kB]                                             
1 266 k o réceptionnés en 0s (0  o/s)                                          
authenticate 'xenial.tar.gz' against 'xenial.tar.gz.gpg' 
extracting 'xenial.tar.gz'
Can not run the upgrade
The error message is 'Aucun fichier ou dossier de ce type'.

So the upgrade program seems to be confused because there is a parameter telling it that the system is 14.04 when it is in fact 12.04.

Can you help me to upgrade?

I also have another computer with a similar configuration that I want to upgrade. Should I try the same method, and if the upgrade blocks somewhere in the upgrade process what should I do?

Thanks and best wishes, John

---

### Post by deadflowr on 2017-07-23
Threads merged.

---

### Post by John_Rose on 2017-07-24
Hi, I've advanced on the problem of the broken upgrade, applying the rescue method given in [https://administratosphere.wordpress.com/2011/11/02/rescuing-an-interrupted-ubuntu-upgrade/](https://administratosphere.wordpress.com/2011/11/02/rescuing-an-interrupted-ubuntu-upgrade/)

The problem was that after the commands "apt-get update" and "apt-apt upgrade" I had not payed attention to the "packages held back" ("conservés" in French) which numbered more than 1000.

I used command "apt-get install some-package some-other-package" but only needed 3 lines by starting with the kernel:

sudo apt-get install linux-generic linux-headers-generic linux-image-generic
sudo apt-get install libfolks25
sudo apt-get install accountservice acpid activity-log-manager-control-center aisleriot alacartarte [the first line of the packages held back]

After that "apt-get update" and "apt-apt upgrade" said that all was installed except a long list of automatically installed packages. The system booted and worked (except that the log-in page still said  12.04). Then I did the last step in the method and ran "apt-get  autoremove" and rebooted which gave me a broken system (no internet and no desktop  icons). I got back fixed internet by am now running the update manager which wants to add or replace more than 500 packages.

I am leaving this post to show the way forward. NO ADVICE IS REQUESTED AT THIS POINT - I will repost with either a complete solution or continuing problems to be solved.

Thanks and best wishes, John

---

### Post by vocx on 2017-07-24
> **John_Rose said:**
> Hi, I've advanced on the problem of the broken upgrade, applying the rescue method given in [https://administratosphere.wordpress.com/2011/11/02/rescuing-an-interrupted-ubuntu-upgrade/](https://administratosphere.wordpress.com/2011/11/02/rescuing-an-interrupted-ubuntu-upgrade/)

The problem was that after the commands "apt-get update" and "apt-apt upgrade" I had not payed attention to the "packages held back" ("conservés" in French) which numbered more than 1000.

I used command "apt-get install some-package some-other-package" but only needed 3 lines by starting with the kernel:

sudo apt-get install linux-generic linux-headers-generic linux-image-generic
sudo apt-get install libfolks25
sudo apt-get install accountservice acpid activity-log-manager-control-center aisleriot alacartarte [the first line of the packages held back]

After that "apt-get update" and "apt-apt upgrade" said that all was installed except a long list of automatically installed packages. The system booted and worked (except that the log-in page still said  12.04). Then I did the last step in the method and ran "apt-get  autoremove" and rebooted which gave me a broken system (no internet and no desktop  icons). I got back fixed internet by am now running the update manager which wants to add or replace more than 500 packages.

I am leaving this post to show the way forward. NO ADVICE IS REQUESTED AT THIS POINT - I will repost with either a complete solution or continuing problems to be solved.

Thanks and best wishes, John

Just a tip. Before deciding to upgrade your system, you should make sure you have the newest packages for your distribution. It is not clear from your first post if you had all packages up to date, or some were held back for some reason. If you have external sources in your "/etc/apt/sources.list", you may want to remove them temporarily, and the installed programs as well.

Of course, I should point out that 12.04 is quite an old version of Ubuntu. To prevent having a lot of upgrading problems you should really upgrade to the newest version earlier. That is, I would have upgraded to 14.04 in 2015, and then to 16.04 in 2017. Letting a system get that old is risky as the software tends to become obsolete, and even the repositories may stop working. Maybe this was the source of your original error.

Also, that the login screen shows you 12.04 instead of 14.04 is no confirmation of which version you have. The version is mostly determined by the Linux kernel version, and the C library, as basically the entire system depends on those two. The login screen is just a drawing.

So, I think you are on a good path trying to fix the system. Try to install as many packages as you can that correspond to the 14.04 version. You can check [https://packages.ubuntu.com/](https://packages.ubuntu.com/) to see that the version of the packages that are being installed corresponds to those in the repositories for 14.04.

---

### Post by oldos2er on 2017-07-24
If I'm understanding correctly you're trying to upgrade from 14.04 to 16.04? You would first need to run ```
sudo apt-get update && sudo apt-get dist-upgrade 
```

---

### Post by #&amp;thj^% on 2017-07-24
I think OP is dealing with this on his own here now.
>     I am leaving this post to show the way forward. NO ADVICE IS REQUESTED AT THIS POINT - I will repost with either a complete solution or continuing problems to be solved.

    Thanks and best wishes, John 

    Last edited by John_Rose; 3 Hours Ago at 03:24 PM. Reason: Further work in progress - **_suspend request for help_** 
Hope to hear the outcome though, and may it be successful.

---

### Post by John_Rose on 2017-07-25
Thanks so much to all three of you. I did make sure that my 12.04 was up-to-date before upgrading. I believe that I caused the problem myself by canceling the upgrade script after it hung up for more than 10 minutes - I see now that the French Ubuntu server often interrupts connection and I should have just let it sit. My 14.04 is now complete. I believe it is important in such a interrupted upgrade to first install with "apt-get install" the key held-back packages (especially the kernel) which also install many dependent packages, then "apt-get update" and "apt-get upgrade", then try to use the Update Manager from the new installation. Installing the missing packages with "apt-get install" is not only tedious but risks generating unresolved dependencies.

BUT I am thus far very unhappy with 14.04 under GNOME Metacity. It is very slow on my old machine relative to my 12.04 installation, and after a lot of searching and trying I still do not have my program icons on the desktop nor the Wifi management icon in the toolbar. My feeling is that I will have to try to install GNOME 2 instead of the GNOME 3 provided with the distribution. If anyone has a magic solution it would be very welcome, but if not I will keep working on it and post another question if needed.

Best wishes, John

---

### Post by vocx on 2017-07-25
> **John_Rose said:**
> Thanks so much to all three of you. I did make sure that my 12.04 was up-to-date before upgrading. I believe that I caused the problem myself by canceling the upgrade script after it hung up for more than 10 minutes - I see now that the French Ubuntu server often interrupts connection and I should have just let it sit. My 14.04 is now complete. I believe it is important in such a interrupted upgrade to** first install with "apt-get install" the key held-back packages (especially the kernel) which also install many dependent packages**, then "apt-get update" and "apt-get upgrade", then try to use the Update Manager from the new installation. Installing the missing packages with "apt-get install" is not only tedious but **risks generating unresolved dependencies**.

Correct! Don't let your system get too old.

But I don't understand the second part, you first used "apt-get" to install the held packages, then you used it again to install more packages and your system broke down? And then you used the Update Manager to finally get your system correctly? I find it hard to believe. The "apt-get" command should correctly identify all the dependencies and install them when necessary so I don't think it should break things. I think since you never finished the original upgrade your system was in an inconsistent state. But normally, "apt-get" is very useful to install packages and keep the system up to date.

> 
BUT I am thus far very unhappy with 14.04 under GNOME Metacity. **It is very slow on my old machine** relative to my 12.04 installation, and after a lot of searching and trying I still do not have my program icons on the desktop nor the Wifi management icon in the toolbar. My feeling is that I will have to try to install GNOME 2 instead of the GNOME 3 provided with the distribution. If anyone has a magic solution it would be very welcome, but if not I will keep working on it and post another question if needed.

Best wishes, John
That your computer is slow may be a sign that you are not using the appropriate video drivers for your machine, especially if your computer has an Nvidia or an ATI/AMD video card. Maybe you should check this first.

Maybe you did not read this, but the official GNOME project moved to GNOME 3 some years ago, which also inspired the creation of the Ubuntu Unity desktop. Many people liked the old GNOME 2 feel, so they forked GNOME 2 and continued development of it under the name MATE. I haven't tried it, but it apparently intends to retain the simple GNOME 2 interface. So you may try to install "ubuntu-mate-desktop", and see if you like that. Metacity is not a desktop environment, it's just a window manager, so probably you are already using a version of GNOME 3, or Unity, and you don't realize it.

If your computer is old, maybe you'd like a lighter desktop environment, such as XFCE installed by the package "xfce4", or LXQT, installed by the package "lxqt".

Also, don't you prefer to upgrade to 16.04? It's great that you upgraded to 14.04, but remember that it is already 3 years old, so if you don't keep your system updated you may again run into issues of obsolescence.

---

### Post by John_Rose on 2017-08-03
Thanks so much, VOCX, for this very detailed advice.
  
  In fact I made an error when I spoke of GNOME 2 - as you say my 12.04 already had GNOME 3. Concerning the "held-back" packages, I was following the method recommended in [https://administratosphere.wordpress...buntu-upgrade/]("https://administratosphere.wordpress.com/2011/11/02/rescuing-an-interrupted-ubuntu-upgrade/"). In effect the system was too broken for update and upgrade to fix all of the inconsistencies regarding the missing (held-back) packages (perhaps "apt-get update --fix-missing" could have fixed them, didn't know about it at that time). After I sent my last post, I was able to fix the WiFi problem (essentially by undoing the temporary fixes needed to get access during the rescue and to get back the desktop icons by completely removing and reinstalling GNOME ([https://askubuntu.com/questions/462163/uninstall-gnome-completly-from-ubuntu-14-04-lts](https://askubuntu.com/questions/462163/uninstall-gnome-completly-from-ubuntu-14-04-lts)). I thus got a clean system, but it did not speed up any. It does not seem to be a problem with the video drivers as all seems well for my basic Intel Integrated Graphics Controller.

  I then upgraded to 16.04 without interruption this time. The boot time up until the user prompt now takes 1 1/2 minutes instead of 1 minute under 14.04, and I get the feeling that execution is substantially slower (unfortunately I do not have any benchmark data). In addition 16.04 takes up more than 1.7GB of extra disk space. My feeling is that I should not have upgraded to 16.04 on this small and old computer (7 year-old netbook with Intel Atom N450 processor). I will try XFCE and/or LXQT and report back if any better results. I also saw a posting recommending Nemo ([http://www.noobslab.com/2013/10/nemo-file-manager-with-extensions-for.html](http://www.noobslab.com/2013/10/nemo-file-manager-with-extensions-for.html)) as a lighter workaround for Nautilus, do you have an opinion on that?

  Anyway, I have learned a lot thanks to you and other members. Thanks so much again, John

---

### Post by vocx on 2017-08-03
> **John_Rose said:**
> ...

  I then upgraded to 16.04 without interruption this time. The boot time up until the user prompt now takes 1 1/2 minutes instead of 1 minute under 14.04, and I get the feeling that execution is substantially slower (unfortunately I do not have any benchmark data). In addition 16.04 takes up more than 4GB of extra disk space. **My feeling is that I should not have upgraded to 16.04 on this small and old computer (7 year-old netbook with Intel Atom N450 processor)**. I will try XFCE and/or LXQT and report back if any better results. I also saw a posting recommending Nemo ([http://www.noobslab.com/2013/10/nemo-file-manager-with-extensions-for.html](http://www.noobslab.com/2013/10/nemo-file-manager-with-extensions-for.html)) as a lighter workaround for Nautilus, do you have an opinion on that?

  Anyway, I have learned a lot thanks to you and other members. Thanks so much again, John
I have to disagree with staying on 14.04 and not upgrading to 16.04. You can read plenty of stories on people who are happily using 10-year old computers with Ubuntu 16.04 and a lightweight desktop. It seems your system is old, and yes, the Atom processor is not very powerful, but this should not prevent you from having a workable system. So, my advice stands. Don't use Gnome 3 or Unity, use a lighter desktop like MATE, LXQT, or XFCE4.
> **vocx said:**
> ...
Many people liked the old GNOME 2 feel, so they forked GNOME 2 and continued development of it under the name MATE. I haven't tried it, but it apparently intends to retain the simple GNOME 2 interface. So you may try to install "ubuntu-mate-desktop", and see if you like that. Metacity is not a desktop environment, it's just a window manager, so probably you are already using a version of GNOME 3, or Unity, and you don't realize it.

If your computer is old, maybe you'd like a lighter desktop environment, such as XFCE installed by the package "xfce4", or LXQT, installed by the package "lxqt".
...

I don't have experience with Nemo, but I don't think the file explorer is particularly important when it comes to speed. It's the rendering engine that actually draws things on screen what could make your system slow. Once you boot your system, run "htop" in the terminal to see which processes are consuming more CPU cycles, and RAM. Surely something like "Xorg" and "Compiz" are at the top.

The fact that your desktop starts a bit slow is also puzzling. You may be having some processes running and failing at the beginning, so maybe disabling some things, removing some unneeded packages would help you. I suggest booting your computer, and checking the messages from the kernel for any strange behavior. Just run "dmesg" in the terminal after booting up.

---

### Post by John_Rose on 2017-08-06
Yes, thanks so much VOCX, I will definitely follow your advice when I can and report back (but for the moment I have to put this computer aside). Please note that I corrected downwards the extra disk space that 16.04 is taking relative to 14.04 - around 1.75 GB after removal of the old kernel.

---

