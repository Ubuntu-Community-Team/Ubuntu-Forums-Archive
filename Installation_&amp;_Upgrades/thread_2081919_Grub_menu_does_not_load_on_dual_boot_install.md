---
title: "Grub menu does not load on dual boot install"
date: 2012-11-08
forum: Installation &amp; Upgrades
---

### Post by malt loaf on 2012-11-08
I have a problem with a new dual boot install.  I had a functioning Win7 installation and ran the Ubuntu 12.04 install CD to install Ubuntu as dual boot.

The install seemed to go OK, although it was a bit messy right at the end, (more details later if required).

Now when I boot the laptop I get a choice of the two OSs.  If I choose Win, everything fine, if I choose Ubuntu it goes to a Grub prompt but sticks there.  i.e no Grub menu loads.

I should mention that when partitioning I specified sda5 as the " device for boot loaderinstallation".  I used EasyBCD to add Ubuntu to the Windows MBR.

Anyone help?

---

### Post by oldfred on 2012-11-08
Do not know much about EasyBCD. You may do better in their forums, if a EasyBCD issue.

[http://neosmart.net/blog/](http://neosmart.net/blog/)
[http://neosmart.net/wiki/display/EBCD/Linux](http://neosmart.net/wiki/display/EBCD/Linux)
[http://neosmart.net/wiki/display/EBCD/Ubuntu](http://neosmart.net/wiki/display/EBCD/Ubuntu)

Can you hold shift from click on Ubuntu item in EasyBCD menu, and does that give the grub menu?

It may still be a video issue with Ubuntu.

Post this to see details, it cannot fix most Windows or EasyBCD issues but report will tell us if configured correctly:

Post the link to the BootInfo report that this creates.

Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.
Full RepairCD with Boot-Repair (for newer computers) 
[https://help.ubuntu.com/community/UbuntuSecureRemix](https://help.ubuntu.com/community/UbuntuSecureRemix)

---

### Post by malt loaf on 2012-11-08
Thanks for the suggestions.  We have a time zone issue.  I am in Greece, many hours ahead of you, Oldfred, and I cannot easily get to the PC right now to check out some of your points.  Probably tomorrow I will download the Remix CD and try to install again.  That sounds cool.

Given that I can see the Ubuntu partitions in Windows Disk Management, and the dual boot works OK up to the point of choosing Ubuntu, are you saying you think it is an issue with EasyBCD?  It has the feel of Grub pointing to the wrong place to boot from.

---

### Post by oldfred on 2012-11-08
You can download Boot-Repair into your Ubuntu liveCD or USB, the repair ISO is for a separate repair CD or USB if needed.

The Boot-Info report should tell us if grub is installed ok or not.

A lot of the users on the forum are in your time zones and may add their 2 cents, if you post report before I am on line.

---

### Post by malt loaf on 2012-11-09
Well, I got it working, but I don't like the boot procedure I've ended up with.  Here is the Boot Info link, but I think it refers to the successful setup, so I don't think it helps much.  [http://paste.ubuntu.com/1344799/](http://paste.ubuntu.com/1344799/)

What I've got is, on boot I get the Grub menu with Windows 7 as the last option.  If I choose Ubuntu, then it loads up as you would expect.  If I choose Windows it gives me the Windows loader menu with Win 7 and Ubuntu in it.  So, I guess it is the reverse of what I would see if the system was starting up from the Windows loader and then pointing to Grub for Ubuntu, which I could not get working before.

As far as I can tell Boot Repair has installed grub on sda1, the Windows partition although I originally specified sda5 during installation from the iso.

Anyone know why the iso ignores what I asked for when installing?  Since I had no way of knowing this was happening, I was telling EasyBCD to look for grub on sda5, which I guess is why system would not boot to Ubuntu?

Another thing that is muddying the waters.  First couple of times I tried to install from the iso, when I got to the "who are you" screen, I chose the option to log in automatically or some such wording.  The install then stuck at this dialogue, with the "continue" button inactive.  Once all CD activity seemed to have stopped I forced a shutdown as I had no other choice.  Did this have the effect of terminating the install before it could change the default grub location?  Who knows.  What pisses me off is an install procedure that falls over because I choose an option it has offered.  When I went back on the next install, (sigh), and chose a password everything completed normally.  How can this be?  BTW, I found out later that not having entered a password meant I could only get on as guest.  Not explained anywhere!  Bit tricky for newbies.  Do we need to go on a basics course before we even try to install?  And if it's going to fall over, why offer that option.  I just don't get it.  I'm beginning to think Ubuntu is not as "friendly" as I first thought.

One final question, how do I change the default OS to load in the grub menu?

Thanks for any help that might be forthcoming.

---

### Post by darkod on 2012-11-09
The second menu appears because you added entry for ubuntu in the windows bootloader using EasyBCD. Open EasyBCD again once you boot windows, and delete the ubuntu entry. That should sort out that problem since there will be only windows as far as windows bootloader is concerned and it will not show a menu.

The default entry you can select in /etc/default/grub or for a GUI approach you can use something like Grub Customizer.
[http://ubuntuforums.org/showthread.php?p=10340183](http://ubuntuforums.org/showthread.php?p=10340183)

---

### Post by malt loaf on 2012-11-09
Thans Darko.  Will try that.  Actually, I think I did the thing with Easybcd before when I dumped Ubuntu, and strangely, it still displays amenu with only Windows in.  So I dropped the time delay to 0, and that sort of fixed it, although the menu still flashes up briefly!!

Will have another go, and also will try out Grub Customiser.

---

