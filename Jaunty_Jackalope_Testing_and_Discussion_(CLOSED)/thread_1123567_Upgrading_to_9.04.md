---
title: "Upgrading to 9.04"
date: 2009-04-12
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by lolol i r linux noob on 2009-04-12
I was wondering wether i should upgrade to 9.04 now or wait untill a stable version comes out.

What bugs are there in the test version?

---

### Post by Myglaren on 2009-04-12
Haven't found any yet - go ahead and upgrade unless you have irreplacable data, in which case do the reccommended thing and back it up first :)

---

### Post by nandemonai on 2009-04-12
> **lolol i r linux noob said:**
> I was wondering wether i should upgrade to 9.04 now or wait untill a stable version comes out.

What bugs are there in the test version?

Many. If you are not comfortable with a potential broken system, reporting bugs and testing patches I wouldn't risk it.

[https://bugs.launchpad.net/ubuntu/jaunty](https://bugs.launchpad.net/ubuntu/jaunty)

---

### Post by linux_lover69 on 2009-04-12
Jaunty works plenty fine for me. In fact I think its the best one yet.

---

### Post by lolol i r linux noob on 2009-04-12
when will ther be a stable release?

---

### Post by nandemonai on 2009-04-12
> **lolol i r linux noob said:**
> when will ther be a stable release?

[https://wiki.ubuntu.com/JauntyReleaseSchedule](https://wiki.ubuntu.com/JauntyReleaseSchedule)

---

### Post by lolol i r linux noob on 2009-04-12
I'll just wait till the 23rd

---

### Post by chazn85 on 2009-04-12
depends how happy you would be rebuilding your system on the off chance that things went wrong.  Personally i generally try to stick with the LTS versions and upgrade only if there is a particular feature i need/want

Thanks

---

### Post by lolol i r linux noob on 2009-04-12
a rebuilt me system a few week ago after a wreked me boot loader.

---

### Post by tofiluk on 2009-04-12
i upgraded my ubuntu 8.10 to 9.04 a week ago and it works perfectly fine :D

---

### Post by Paqman on 2009-04-12
It's not really about how many bugs there are *now*, the risk of using the testing branch version is that there are a ton of updates every day, and that any one of them could break something tomorrow. Unless you know how to fix that or you can live with the breakage, then stick to the stable version.

---

### Post by freeman2000 on 2009-04-13
Noob here to both Ubuntu & Linux.  On day 1, I installed Intrepid (8.10).  Everything worked.  On day 2, I figured why wait, so I downloaded and upgraded to Jaunty (9.04).  I've been running Jaunty for 2 days now (I said I was a noob) and all is good.  I haven't had any problems, even though I am running it on a dual-boot Vista laptop with wireless and NVidia (2 of the most common problem areas I see here on the forum).  I think Jaunty has a better look/feel to it, and it is very stable.  There hasn't been an onslaught of updates as mentioned.  If you wait for the release date, prepare for millions of users trying to download 700mb each all at once.  Good luck.

---

### Post by Paqman on 2009-04-13
> **freeman2000 said:**
> If you wait for the release date, prepare for millions of users trying to download 700mb each all at once.  Good luck.

Best way around this is to get it over P2P. There are official .torrent files available on the download page. I've had download rates of 1000KB/s on release day for new versions of Ubuntu.

---

### Post by peakshysteria on 2009-04-13
Been running 9.04 since this morning. All seems smooth so far (except I can't seem to update my Vuze client). Ofcourse it could break any moment. I've read somewhere that X crashes if the machine is running more than a day. This doesn't fit my machine which is used to run 24/7. I took the chance anyway. My advice is to read the instructions at:  [http://www.ubuntu.com/testing/jaunty/beta](http://www.ubuntu.com/testing/jaunty/beta) Then decide if you want to take the chance to upgrade or not. Upgrading can leave you with an unusable system.

Check out Known issues (This is not all bugs, only the most known apparently):

> As is to be expected at this stage of the release process, there are several known bugs that users are likely to run into with Ubuntu 9.04 Beta. We have documented them here for your convenience along with any known workarounds, so that you don't need to spend time reporting these bugs again:

    *

      A bug in an Ubuntu-specific patch to X server logging code will cause X sessions to crash after they have been running for longer than a day. Users encountering this bug should upgrade to the latest version of the xserver-xorg-core package, which will be available immediately after the beta release. 328035.
    *

      Some users of Intel i8x5 video chipsets are unable to load X, getting an error message of "Fatal server error: Couldn't bind memory for BO front buffer". As a workaround, use the VESA driver by logging into a text console, running "sudo nano /etc/X11/xorg.conf", and adding the line Driver "vesa" to the Device section. An alternative (experimental) workaround is to use the UXA acceleration method (see below). If in doubt, please do not upgrade to Ubuntu 9.04 Beta yet. 304871
    *

      Users of Intel video chipsets have reported performance regressions in Ubuntu 8.10 compared with previous releases. (252094) Although these performance issues have not been resolved by default in Ubuntu 9.04, a new experimental acceleration architecture option, DRI2/UXA, is available for Intel graphics users. Our testing has found this provides significant performance improvements for many users, but has also shown risk of severe stability problems, thus we are not yet providing to the general public. You can opt-in to enable this by running "sudo gedit /etc/X11/xorg.conf", and adding Option "AccelMethod" "UXA" to the Device section of your xorg.conf. Users wishing to maximize stability should stay with the standard default acceleration method, "EXA".
    *

      Ctrl-Alt-Backspace is now disabled, to reduce issues experienced by users who accidentally trigger the key combo. Users who do want this function can enable it in their xorg.conf, or via the command dontzap --disable.
    *

      Ubuntu 8.10 systems installed from the desktop CD mistakenly had the lilo package installed as well as grub, although grub was used for booting. If you use the recommended Update Manager upgrade method, then the lilo package will be removed if it does not appear to be used. If you upgrade using some other method and are sure that you only use the GRUB boot loader, then we recommend that you remove the lilo package manually. 314004
    *

      On the timezone map in the desktop CD installer, the markers for cities are displaced from their correct locations. Users should be aware of this issue when selecting their timezone. This bug will be resolved for daily builds immediately after the 9.04 Beta. 334284
    *

      If any filesystems are mounted when starting the desktop CD installer, then a dialog labelled "Unmount partitions that are in use?" will be presented. Unfortunately, the buttons on this dialog box are poorly named: "Continue" attempts to unmount filesystems and then repeats, which will often just display the same dialog box again, while "Go Back" ignores this condition and continues. This will be corrected for the final release. 346589
    *

      On desktop installations from USB disks, such as typical Ubuntu Netbook Remix installations, the installer displays a warning about the fact that the installation medium itself (often /dev/sdb) is mounted. This warning is unnecessary, because the fact that it is mounted is completely normal, and does not interfere with the user's ability to install the system to devices other than the USB disk itself. You should ignore this warning; note that in order to do so you will need to select "Go Back", due to the issue above. 347916
    *

      In some cases, the "Prepare Disk Space" screen in the desktop installer displays obviously incorrect partition sizes in its graphical disk previews. This is only an error in the preview and does not reflect a problem with the partitioning changes that will actually be applied. 336203
    *

      The mythtv frontend in mythbuntu fails to render fonts correctly when using video drivers other than the Intel or closed-source nVidia drivers. This issue is expected to be resolved for the final 9.04 release. 341898
    *

      When installing to a system with another OS previously installed, the migration assistant will offer to migrate settings and documents even when the entire disk is being overwritten. The migration assistant will not be able to preserve documents when using the entire disk for installation. 339898
    *

      Users who were running eCryptfs on the Jaunty Alpha milestones are advised to re-encrypt any encrypted files. An upstream 2.6.28 kernel bug caused random kernel memory to be written to eCryptfs encrypted file headers. The fix has been applied and deployed to Ubuntu users in the Jaunty Beta kernel. Ubuntu eCryptfs users running this kernel should re-encrypt each encrypted file using /usr/bin/ecryptfs-rewrite-file. For more information, please see ecryptfs-rewrite-file(1). See 345544.
    *

      Users of Compaq Smart Array controllers will be unable to remove existing LVM volumes using the partitioner in the installer. 341928
    *

      The mdadm package in Ubuntu 9.04 Beta will fail to assemble RAID10 arrays on boot. Other types of RAID are not affected; investigation of this issue is ongoing. 316670
    *

      Booting degraded RAID may fail in virtual-machine setups where the host is running with cpu frequency scaling enabled, due to a non-deterministic race condition, 334994. Booting degraded RAID on physical hardware should not be affected, since the cpu frequency is constant through the hard disk detection process.
    * Upgrading a desktop system using an ATI video chipset with the fglrx binary-only driver may result in a warning that the driver needs to be replaced. There is a bug in the driver replacement logic, so if you see this prompt, please cancel the upgrade until this is fixed, which will happen immediately after the beta release.


For me, all went smooth as ever. Several threads are no also saying that it's better to upgrade than to make a clean install. And at least for me this has seemed to work perfectly.

---

### Post by gslo on 2009-04-13
You could always download Sun VirtualBox and install 9.04 that way(I did).
It runs beautifully with VBox Additions installed. I even have compiz running (haven't tried emerald yet).
So far very happy.

P.S. I'm using Daily Build Apr 13 x86 alternate install ISO.

---

### Post by mitchellcipriano on 2009-04-19
> **gslo said:**
> You could always download Sun VirtualBox and install 9.04 that way(I did).
It runs beautifully with VBox Additions installed. I even have compiz running (haven't tried emerald yet).
So far very happy.

P.S. I'm using Daily Build Apr 13 x86 alternate install ISO.
How are you getting the additions to run? Each time I try it completely messes up my install. Also, I was able to manually adjust the resolution in Ibex running in Vbox, but I do not seem able to with Jaunty. Any suggestions?

---

