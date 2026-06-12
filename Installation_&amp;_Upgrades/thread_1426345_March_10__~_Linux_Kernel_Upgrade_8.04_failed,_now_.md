---
title: "March 10  ~ Linux Kernel Upgrade 8.04 failed, now unusable"
date: 2010-03-10
forum: Installation &amp; Upgrades
---

### Post by avantgardaclue on 2010-03-10
Hi Guys, been running my HP Compaq on 8.04 for the last couple of years. Utterly reliable, updates have come and gone and installed perfectly UNTIL today!

Today there was an update to the Linux Kernel itself. OK been done loads of times before, so what.

Well it downloaded the files OK and was in the process of installing. The 'bar' moved about a qtr inch then just stopped. I left the machine to sort its self out. Came back after a while and the mouse wouldn't move and the whole screen had 'greyed down'.

Did a hard reboot and Ubuntu loaded OK. Prompted to download files again, (but probably didn't) and went straight into 'install mode'. Perfect, then prompted to reboot, OK. Started to reboot as usual, then code lines appeared to say something was missing. Rebooted again and the boot graphic was just moving left and right and doing nothing.

So now I have an unusable Ubuntu machine :frown: Thank heavens I had a copy of Puppy Linux on a flash drive which allows me to use the hardware and access the files/

Any ideas please.

Many thanks

---

### Post by Fafler on 2010-03-10
That doesn't sound good. Are you familiar with grub? This is from memory, so it's probably not 100% correct, but press escape to enter the grub menu. Select you kernel and press e to edit the command line. Remove the words quiet and splash and press b to boot. Now the kernel should boot in text mode and display a lot of information. The last thing that happen should point to the course of your problem.

BTW; if your old kernel is still on the list, try booting it. If it's related to the new initrd, which is quite probable, it should boot without any problems.

---

### Post by slakkie on 2010-03-10
Boot your old kernel as the poster above me alrady said, then if that works, the new kernel has a problem. Then use ubuntu-bug against your kernel (assuming -generic, could be different):

ubuntu-bug linux-image-generic

---

### Post by avantgardaclue on 2010-03-10
Thank you Fafler and Slakkie, able to boot perfectly by hitting ESC at grub boot up and selecting the previous kernel.

---

### Post by kansasnoob on 2010-03-10
Now that you can boot again I'd run the following to see if you have a disc space issue:

```
df -H
```

Then to clear the old partially/improperly installed updates run:

```
sudo apt-get autoclean
```

```
sudo apt-get clean
```

```
sudo dpkg --configure -a
```

Then I'd personally use Synaptic to try and update again by clicking on Reload > Mark all Upgrades, then when you click on Apply another window will pop up so you can review what's going on before deciding whether or not to proceed.

Synaptic also has a nifty feature to deal with broken packages, Edit > Fix Broken Packages. That may even produce some useful info. Or you can use the Custom Filters > Broken option to gather some info.

---

