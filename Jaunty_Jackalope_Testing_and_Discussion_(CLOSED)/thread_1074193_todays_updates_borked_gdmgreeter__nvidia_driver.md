---
title: "todays updates borked gdmgreeter / nvidia driver"
date: 2009-02-18
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by ugkbunb on 2009-02-18
I have been running relatively stable Xubuntu AMD64 Jaunty with compiz etc... Today I realized there was a number of updates in my update-manager... I installed them all and upon reboot gdm complained that the current greeter was corrupt/unavailable. Only way for me to login in is to edit the gdm conf file and set auto-login to enabled. That lets me get logged-into my xfce session but upon boot everything seems fine at first.. the mouse changes to my set icon theme and then eveything turns into garbled random collage of pictures, mouse reacts to input (moves)... but everything else is locked up... like the xserver is freezing, however I really have no clue. To get my computer temporarily working... I dropped down CTRL-ALT-1 to CLI.

sudo dpkg-reconfigure -phigh xserver-xorg
(gives me a vanila xorg.conf and backups the one nvidia created)
sudo /etc/init.d/gdm restart

Then I able to login and use my computer... if I try reconfigure the xorg with sudo nvidia-xconfig it leads me back to my initial problem.

I have tried reinstalling nvidia*, gdm, xfdesktop4, xfce4

ctrl-alt-delete which should take me to gdmgreeter screen of course does not work.

just wondering if anyone else is experiencing this... if i should wait out for an update or just reinstall. wouldnt be so bad I can easily backup my home partition.

I not sure what logs I should look into for necessary debug info... but I can reproduce it easily so if you let me know I will post up any log output.

filed a bug on lp:
[https://bugs.launchpad.net/ubuntu/+bug/331390](https://bugs.launchpad.net/ubuntu/+bug/331390)

---

### Post by ayates on 2009-02-19
You are not alone. I had to boot back into Intrepid. I'm getting the same weird things on regular 32 bit Ubuntu.

---

### Post by Kow on 2009-02-19
There is a perfectly good explanation for it too... This was the first day I decided to try out jaunty (via virtualbox). This would be the third set of testing repositories in a row in which a major app broke the first day I tried using it, LOL. BTW, it's segfaulting so it's fairly hard to backtrace. I'm guessing a dependency was upgraded and gdmgreeter or one of it's backends needs to be rebuilt.

---

### Post by Denestria on 2009-02-19
Yeah, after installing updates tonight I logged out and got a black/hot pink screen.  Then it complained about GDM being broken.  I couldn't even ctrl-alt-f# to a terminal, ended up having to sysrq reboot out of it.  sudo dpkg-reconfigure kdm and restarting X didn't help either.  I had to remove GDM from the boot sequence, add KDM and reboot again before I finally got my desktop back.

---

### Post by johoe on 2009-02-19
Same situation here on two PC's (both nvidia). 
Uninstalled gdm and installed kdm - works perfect! Although I would like to have gdm.

joho

---

### Post by Kow on 2009-02-19
Has anyone been able to figure out which package update b0rked gdm? Perhaps libc? I would think that if it was libc then a whole lot of other apps would be broken (even before making it to gdm).

---

### Post by stovenator on 2009-02-19
I've figured out the packages...

I downgraded libgtk2.0 and everything is back to normal. The following list are interdependent, so I downgraded them all:

libgtk2.0-0
libgtk2.0-bin
libgtk2.0-common
libgtk2.0-dev
libgtk2.0-doc
libgail18
libgail-common
libgail-dev
gtk2-engines-pixbuf

I haven't narrowed it down further, and it's possible you might be able to upgrade a couple of them without the others (and you may not have the dev library), but this should get you back.

---

### Post by stovenator on 2009-02-19
Oh, and in my case what I did was Ctrl-Alt-F1 to a terminal. Then I changed to /var/cache/apt/archives/

and then did:

sudo dpkg -i libgtk2.0-doc_2.15.3-0ubuntu2_all.deb libgtk2.0-common_2.15.3-0ubuntu2_all.deb libgtk2.0-bin_2.15.3-0ubuntu2_all.deb libgtk2.0-dev_2.15.3-0ubuntu2_amd64.deb libgtk2.0-0_2.15.3-0ubuntu2_amd64.deb gtk2-engines-pixbuf_2.15.3-0ubuntu2_amd64.deb libgail-dev_2.15.3-0ubuntu2_amd64.deb libgail-common_2.15.3-0ubuntu2_amd64.deb libgail18_2.15.3-0ubuntu2_amd64.deb

That's assuming you have those versions of the files in your apt archive.

---

### Post by Kow on 2009-02-19
See [http://ubuntuforums.org/showpost.php?p=6759269&postcount=8](http://ubuntuforums.org/showpost.php?p=6759269&postcount=8) if you feel like using a new version of gdm which apparently was not b0rked by the Feb 18 updates.

EDIT: Immediately after rebooting with gdm-new I have no input devices. :(

---

### Post by grash on 2009-02-19
I have the same problem after updating.  Killing gdm and and using startx gets me in but the graphics are sloooowww.  Tried gdm-new and that gets me in also but the graphics are slooowww.  Tried the nv driver as well as the nvidia driver with the same results.  Guess I'll just have to run slow until the next update which I hope will correct the problem.:(


I wonder if there may be other problems other than gdm...

---

### Post by ugkbunb on 2009-02-19
glad to hear I am not alone... if you guys want to downgrade gtk the deb files are available here:
[http://de.archive.ubuntu.com/ubuntu/pool/main/g/gtk+2.0/?C=D;O=D](http://de.archive.ubuntu.com/ubuntu/pool/main/g/gtk+2.0/?C=D;O=D)

---

### Post by philinux on 2009-02-19
It's been fixed now with an update. I had installed kdm from tty but I updated about 2 hours ago and it's fixed.

---

### Post by andrewabc on 2009-02-19
Exact same problem.
Updated today, and now it just brings me to a text login/password. No GUI at all.

When going into second grub menu item (the recovery option), I notice:
Starting GNOME Display manager   FAIL

So, apparently there is an update out for this?
So I just have to do sudo apt-get update and sudo apt get-upgrade?
Right now when I do sudo apt-get upgrade, there are about 10 programs that give errors and do not update.

When I first got this problem I was updating, but not at the computer. I went to computer and the screen was black and would not show anything. So I had to press computer power button to shutdown.

---

### Post by philinux on 2009-02-19
> **andrewabc said:**
> Exact same problem.
Updated today, and now it just brings me to a text login/password. No GUI at all.

When going into second grub menu item (the recovery option), I notice:
Starting GNOME Display manager   FAIL

So, apparently there is an update out for this?
So I just have to do sudo apt-get update and sudo apt get-upgrade?
Right now when I do sudo apt-get upgrade, there are about 10 programs that give errors and do not update.

When I first got this problem I was updating, but not at the computer. I went to computer and the screen was black and would not show anything. So I had to press computer power button to shutdown.

Let the login screen fail then press ctrl alt f1 to get tty. Login and then sudo apt-get update etc. It should work from the recovery mode too.

---

### Post by ugkbunb on 2009-02-19
I can confirm that this bug is fixed for me with todays updates to the gtk packages.

---

### Post by andrewabc on 2009-02-19
> **philinux said:**
> Let the login screen fail then press ctrl alt f1 to get tty. Login and then sudo apt-get update etc. It should work from the recovery mode too.

It automatically brings me to user login/password text when I turn computer on, I input them and it logs me in (still text).

I type:
sudo apt-get update
and it shows it checking the mirror for new packages. But for some reason it isn't downloading the new lists. When I type sudo apt-get update it does it all in 2 seconds, and does not download the 10mb of lists like it normally would to see if new files to download. So I don't think it is possible for me to download any updates currently.

sudo apt-get upgrade shows 13 packages not getting installed because of dependency errors. They are:
```
libgweather-common
libgweather1
libpanel-applet2-0
gnome-panel
gnomeapplets
evolution-data-server
evolution-plugins
gnome-power-manager
indicatorapplet
indicator-messages
ubuntu-desktop
evolutionindicator

```

Anything I can do?
I am using a Canadian mirror, which is usually only 6 hours behind ubuntu.
The thing I am worried about is that it is not actually connected to the servers at all. I have wireless USB on an old computer. The USB stick shows that it is active, but I don't think the internet is working.

I type
wget google.com
and it says unable to resolve it.

I'm guessing I will have to connect the internet directly into ethernet card, and it will recognize the internet?

---

### Post by BuckroeBill on 2009-02-19
My Jaunty system failed after todays update also. It goes into "GRUB" and I have no idea how to proceed from there. How do I get to a point that I can download the fix? Any help will be most appreciated.
I managed to use the recovery mode and it fixed the problem. Thanks any way.
FYI I have Jaunty a a second system and chainload it with a 1 second delay. I think I'll adjust that to 3 seconds so I can have a second to select from the menu.
Bill

---

### Post by grash on 2009-02-19
I too can confirm that gdm is fixed with the latest upgrade.  However my system is still running slooowww.  Hopefully another update will fix it.:)
(P4 with Nvidia)

---

### Post by grash on 2009-02-19
BuckroeBill - Your problem has nothing to do with the GDM problem.  I am suprised that the update messed up your Grub install though.
You can try this:

This procedure assumes you have one partition, i.e NOT a separate boot partition.

1.  - Boot off of a live cd.
2.  - Start a terminal and change to root.
3.  - Create a directory (mount point) inside of mnt, i.e. #> mkdir /mnt/root
4.  - Run fdisk, i.e. #> fdisk -l to find out which partition you need to mount if you don't already know.
5.  - Mount the partition, i.e. #> mount /dev/sda1 /mnt/root  (Note: use your partition in place of sda1)
6.  - Mount proc, i.e. #> mount -t proc none /mnt/root/proc
7.  - Mount dev, i.e. #> mount -o bind /dev /mnt/root/dev
8.  - Chroot to new partition, i.e. #> chroot /mnt/root /bin/bash
9.  - Start Grub, i.e. #> grub
10. - Set root partition (where grub files are), i.e. grub> root (hd0,0)
       (Note: The Grub numbering system uses one less than Linx numbering system.
       i.e. sda=(hd0), sda1=(hd0,0), sdb1=(hd1,0), sdb2=(hd1,1), etc.
       The 1st number = hard drive (hd0), (hd1), etc.
       second number = partition 0, 1, 2, etc.)
       (hd0)=MBR, (hd0,0)=1st partition on 1st drive.
11. - Write new boot information, i.e. grub> setup (hd0)
       (Note: This will write the boot information to the MBR.  Again, without more information this is merely an assumption.  You may need to write it to the 1st partition.
           REPOST IF IN DOUBT OF ANY OF THE STEPS!!
12. - If you get any errors you will need to repost so we can help figure them out.
13. - Exit Grub, i.e. grub> quit
14. - Exit chroot, i.e #> exit
15. - Exit root, i.e. #> exit
16. - Reboot
17. - Hopefully everything is OK.

I'm going to be working 4-12's the next 4 days.  If I don't respond right away perhaps someone else can help where I left off.
Good luck.

---

### Post by andrewabc on 2009-02-20
I had to connect my computer directly to ethernet connection since wireless did not work in text mode. I installed the updates and I can now get back to desktop. But now I have other problems.

See screenshots. My panel apps do not work.

Any help!?

---

### Post by ugkbunb on 2009-02-20
> **andrewabc said:**
> I had to connect my computer directly to ethernet connection since wireless did not work in text mode. I installed the updates and I can now get back to desktop. But now I have other problems.

See screenshots. My panel apps do not work.

Any help!?

I had something similiar with my panels acting whacky after the update. I had to delete the panel config file (for me ~/.config/xfce4/panel)... and then restarted the panel + re-configged my settings.

---

### Post by andrewabc on 2009-02-20
> **ugkbunb said:**
> I had something similiar with my panels acting whacky after the update. I had to delete the panel config file (for me ~/.config/xfce4/panel)... and then restarted the panel + re-configged my settings.

I use gnome.
I deleted the entire .config folder and same problem.

---

### Post by theSpaceAmoeba on 2009-02-20
My Firefox extension "Tab Kit" no longer seems to work. It stopped working at the same time that the gdmgreeter problem occurred. The gdmgreeter has been fixed with updates, but my extension still does not work. I get no errors and I'm able to access the extension options and change them, but to no effect. I've uninstalled and reinstalled the extension, still nothing. Any ideas?

---

### Post by ugkbunb on 2009-02-20
> **andrewabc said:**
> I use gnome.
I deleted the entire .config folder and same problem.

not sure but gnome might store it's panel config in .gnome2, .gconf, or perhaps some wherelse...

> **theSpaceAmoeba said:**
> My Firefox extension "Tab Kit" no longer seems to work. It stopped working at the same time that the gdmgreeter problem occurred. The gdmgreeter has been fixed with updates, but my extension still does not work. I get no errors and I'm able to access the extension options and change them, but to no effect. I've uninstalled and reinstalled the extension, still nothing. Any ideas?

Weird I have no idea how the two issues could intertwined... perhaps try purging firefox completely with it's config folder (backup your bookmarks/anything you may need) and try reinstalling it.

---

### Post by andrewabc on 2009-02-20
> **ugkbunb said:**
> not sure but gnome might store it's panel config in .gnome2, .gconf, or perhaps some wherelse...


I tried a couple of those folders, but no luck.
So now I'm reinstalling alpha 3 (only one I had downloaded/burned), and everything seems to be fine for now.

---

