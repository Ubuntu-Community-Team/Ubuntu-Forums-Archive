---
title: "Installing Ubuntu 10.10 on Toshiba NB Netbook"
date: 2011-02-07
forum: Installation &amp; Upgrades
---

### Post by TheManWhoWas on 2011-02-07
On Friday I got it into my head to try and install Ubuntu Netbook Remix on my 18 month old Toshiba NB200. All seemingly went well with the installation, but then the nightmare began!

After installation I was left with a machine where Ubuntu kept "freezing" and XP wouldn't boot at all. And when I started Googling I discovered these were known problems. Tracking down the solutions to get my netbook working again was soul destroying, but eventually I did, so I thought I'd post the solution here for any other poor saps who find themselves in the same fix!

So, you have 3 steps to happiness:

1. Getting Ubuntu working properly

Fortunately 10.10 doesn't appear to have any obvious issues with networking and sound like older versions, but it does suffer from narcolepsy - it falls asleep every couple of seconds which is what makes it looks like it has frozen. You need to prod it to keep it awake (hold down a shift key for instance).

Once booted, open an Applications > Terminal and follow the instructions here to add a line to your GRUB boot:

[http://ubuntuforums.org/showpost.php?p=10199447&postcount=244](http://ubuntuforums.org/showpost.php?p=10199447&postcount=244)

Also, in the BIOS, switch the HDD controller from AHCI to Compatibility Mode

Reboot and Ubuntu should boot up and work fine - hurrah!

2. Getting Windows back

OK, I realise die hard Linux fans don't want Windows back, but I did. Research showed the issue was that GRUB installed itself over the Windows boot partition, and the solution was to repair that with your Windows CD - which of course netbooks don't have.

Eventually I found this guide which explains how to sort it out from Ubuntu:

[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector)

Reboot and Windows goes "tsk, tsk" and fixes itself up again. Hurrah! Now you have XP working again.... but you just overwrote GRUB so now Ubuntu is unbootable. Doh!

3. Getting Ubuntu back

Fortunately this is pretty easy to fix. Just use your Ubuntu installation USB to boot up and follow the instructions here:

[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

The key point is to install GRUB to 'sda' and NOT to 'sda1' where it went before.

Now reboot again and you should have a dual booting Ubuntu / Windows Toshiba NB200/205/305 or whatever netbook. Woohoo! :guitar:

Anyway, hope that helps anyone who finds themselves in the same boat I was.

---

