---
title: "Won't boot after dist-upgrade (14.04)"
date: 2015-01-09
forum: Installation &amp; Upgrades
---

### Post by plkoij on 2015-01-09
I'm testing 14.04 64-bit on a persistent USB, to try to fix a wifi problem before I commit to installing it. In the Networking and Wireless thread, it asks to run

```

sudo apt-get update
sudo apt-get dist-upgrade

```

I did this, and now can't boot off the USB. Instead I see

```

BusyBox v1.21.1 (Ubuntu 1:1.21.0-1ubuntu1) built-in shell (ash)
Enter 'help' for a list of built-in commands.

(initramfs) 

```

Any suggestions for what to do with this?

---

### Post by ubfan1 on 2015-01-10
I've never tried dist-upgrade on a persistent usb installer, but even just update will not really update everything, kernels being the main item which wont work.  What are you trying to do, just test wireless?  Doesn't the 14.04.1 iso work?  In that case, try the 14.10 release.

---

### Post by chkneater on 2015-01-10
I have an esternal HDD, it's my only HDD for this compl.  I store everything on it rather than a Desktop and losing everything when the computer screw.s.  I chrooted into the parttition and found out dpkg was't working at al...Every tteun I try to a normal command like 'dpkg' I get rons of errors and a longl ist of commands thag absoltoeoy did not work.  whenI chrooted into the parttion I couodn't do nothing to fix it,..  I keep geting 'dpkg' errrors with dpkg and also keep getting messages about 'cannot find a device; is /dev mounted etc..  I can't do u[grdae-grub from chrooting in to it, it says 9can't fined / is 
/dev mounted?)  I tried to reinstall 12..04 ....  Right now mu main prob is getting the new install to boot to grub successfully wihitfh ws the original prob. After reinstalling i anc't boog ingo gurb at startu. thanx

If it's not booting from the GRUB which is what it looks liek, you may wanna try to put the file 60_grub-imageboot from the synaptic file ' grub-imageboot '.  Boot to a Live CD and use in terminal do " sudo apt-get install grub-imageboot " and then ' sudo gedit '.  Must do the sudo command.  Open the /etc/grub.d/ from gedit and save as the same name only on your filesystem instead in the same directory: /etc/grub.d/ You should see 60_grub-imageboot in /etc/grub.d/ on your installed filesystem.  That may help you boot.  This file has a grub hook that recognizes all akinds of removable media.  I run exclusively from an Ext HDD thanx to this little file.

---

