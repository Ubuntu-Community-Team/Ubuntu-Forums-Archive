---
title: "Can't upgrade"
date: 2013-12-01
forum: Installation &amp; Upgrades
---

### Post by c1933044 on 2013-12-01
Hi all, I will try to keep this explanation short, but I've been working on this for most of today so there's lots of steps I've already taken.

I have an IBM T60 laptop that I installed Ubuntu 10.10 with Gnome on a while ago. I downloaded the ISO and burned a CD on another laptop and installed off this live CD. "About" says I have Ubuntu 10.10, "Maverick Meerkat", released Oct 2010 and supported until last April. I used to get tons of update reminders but since the system was stable and I wasn't really doing much with the T60 aside from email and web browsing, I ignored it. 

However, I recently got involved in a hardware project that uses Linux to interface with a device over USB. When I tried to install the software, part of the prerequisites involved updating software packages, which failed on 10.10.  So, I thought it was time to finally update Ubuntu.  In the GUI, I clicked System...Administration...Update Manager.  I get this error:  "Your Ubuntu release is not supported anymore.  You will not get any further security fixes or critical updates.  Please Upgrade to a later version of Ubuntu Linux".

Ok, I guess that's reasonable since 10.10 is so old. Clicking "Close" still brings up the update manager, which says:"New Ubuntu release '11.04' is available" with a button that says "Upgrade".

Great, I think- time to upgrade. I saw online that the newest versions are 12.10 (long term support) and 13.04.  So, I figure, for some reason, Ubuntu makes me upgrade in steps from 10.10 to 11.04 etc until I get to the latest.

So I click Upgrade and get another dialog which says "Release Notes" and"= Upgrading to a no longer supported version =You are about to upgrade to a version of Ubuntu that is no longer supported.The target release of Ubuntu is '''no longer supported''' by Canonical. The support timeframe is between 18 month and 5 years after the initial release. You will not receive security updates or critical bug fixes. See [http://www.ubuntu.com/releaseendoflife](http://www.ubuntu.com/releaseendoflife) for details. It is still possible to upgrade this version and eventually you will be able to upgrade to a supported release of Ubuntu. Alternatively you may want to consider to reinstall the machine to the latest version, for more information on this, visit:[http://www.ubuntu.com/desktop/get-ubuntuFor](http://www.ubuntu.com/desktop/get-ubuntuFor) pre-installed system you may want to contact the manufacturer for instructions."  

Ok, it seems I have two choices;

[LIST=1]
[*] As the file recommends 'reinstall to the latest version' (which I assume means to download the latest ISO and boot off that to install from a live CD, vs trying upgrading in steps from within 10.10).   

I go to the Ubuntu website and get the latest ISO (the T60 only has 500MB of RAM, and the site recommends getting the 32-bit version for machines with less than 2GB of RAM, so I choose that.  I get the .ISO and burn it to CD, however the burner complains that I don't have enough space to store the ISO.  A little Googling reveals that the ISOs are now greater than the size of a Standard CD-R.  

Options are burning to a larger CD (some go up to 800MB or something), making a live USB stick, or burning to a DVD.-I look around and all I have are 700MB CD-Rs so I don't currently have a way to burn this on a CD.-My other PC doesn't seem to be burning DVDs correctly, so (even though I found my original Ubuntu 10.10 install CD) I can't make a new one for Ubuntu 12 or 13 to put into the T60.  

Alternately, I can't burn a new DVD on the T60 itself because it only has a CD-R/DVD-ROM drive (it can burn CDs but not DVDs)-I investigate the live USB stick method and find this page ( [http://www.ubuntu.com/download/desktop/create-a-usb-stick-on-windows](http://www.ubuntu.com/download/desktop/create-a-usb-stick-on-windows) ).  It recommends the USB installer at pendrivelinux.com ( [http://www.pendrivelinux.com/universal-usb-installer-easy-as-1-2-3/](http://www.pendrivelinux.com/universal-usb-installer-easy-as-1-2-3/) ). 

I download the installer (Universal-USB-Installer-1.9.5.1.exe) and run it.   It throws up a window saying:"NSIS ErrorInstaller Integrity check has failed.  Common causes include incomplete download and damaged media. Contact the installer's author to obtain a new copy.  More information at http://nsis.sf.net/NSIS_Error".    

I cleared the cache and re-downloaded the file from pendrivelinux, which came out at the same file size and did the same thing again when I tried to run it.  I googled this problem and did not find anyone else with this specific issue.

Having exhausted all of my sub-options under #1, I try #2:

[*] Trying to install 11.04 and then incrementally getting to a supported release. In the (still-open) window titled "Release Notes" on the T60, I click "Upgrade".

This results in an error window that says:"Failed to fetchFetching the upgrade failed.  There may be a network problem."

With a sigh, I close this window (there is no network problem I know of; I am able to browse the web with the T60 and there is no hardware or software firewall). I googled the issue where I can't even update from 10.10 to 11.04 and found that the problem is that after some time, the upgrades are moved off the main server to the Archive servers.  

This guy is having the same problem I am:[http://stackoverflow.com/questions/19431895/trying-to-upgrade-ubuntu-10-10-to-12-04It](http://stackoverflow.com/questions/19431895/trying-to-upgrade-ubuntu-10-10-to-12-04It) suggests running "do-release-upgrade and looking at  [https://help.ubuntu.com/community/Repositories/CommandLineI](https://help.ubuntu.com/community/Repositories/CommandLineI) ran do-release-upgrade but it terminated with errors.

As per the suggestion on that page (that the upgrades get their repository info from /etc/apt/source.list), I edited those files per [https://help.ubuntu.com/community/Repositories/CommandLine](https://help.ubuntu.com/community/Repositories/CommandLine), uncommenting the lines with the Archive servers on them.  However, this didn't work either.I also found this page: [https://help.ubuntu.com/community/EOLUpgrades/](https://help.ubuntu.com/community/EOLUpgrades/) which talks about upgrading from unsupported versions, but it only discusses going from 4.10 in steps up to 10.04 (stopping at an even earlier version than I already have). So, that exhausted my options, but I figured maybe I can download the .ISO on the .t60 (on the existing Ubuntu 10.10 install) and get it to work somehow.  

I found this page:  [http://askubuntu.com/questions/91815/how-to-install-software-or-upgrade-from-old-unsupported-release/91821#91821which](http://askubuntu.com/questions/91815/how-to-install-software-or-upgrade-from-old-unsupported-release/91821#91821which) has more tips on editing the sources.list file to include old-releases.ubuntu.com.   

It suggests issuing these two commands:sudo sed -i -e 's/archive.ubuntu.com\|security.ubuntu.com/old-releases.ubuntu.com/g' /etc/apt/sources.listandsudo apt-get update && sudo apt-get dist-upgrade I tried this but got lots of errors referencing us.old-releases.ubuntu.com so I tried:sudo sed -i -e 's/archive.ubuntu.com\|security.ubuntu.com/us.old-releases.ubuntu.com/g' /etc/apt/sources.listbut that didn't help either, resulting in many, many lines of " No address associated with hostname" errors.

I figured next that, even if I can't burn a new DVD on my other computer, I could download it on the T60 and somehow install it that way.  Fun side note, this page ([https://help.ubuntu.com/community/UpgradeNotes](https://help.ubuntu.com/community/UpgradeNotes)) has a paragraph titled "Unsupported and Obsolete Versions".  

If you click on the text that says "Ubuntu 10.10 Maverick Meerkat" See THIS page for upgrade information, the destination link is 404 not found...Some more Googling eventually landed me here:  [http://askubuntu.com/questions/39105/how-to-upgrade-ubuntu-from-an-iso-imageThis](http://askubuntu.com/questions/39105/how-to-upgrade-ubuntu-from-an-iso-imageThis) page says you can mount the .ISO image as a CDROM drive and issue these three commands:sudo mkdir -p /media/cdrom  sudo mount -o loop ~/Desktop/(whatever).iso /media/cdrom(alt+F2) gksu "sh /media/cdrom/cdromupgrade"I tried this but it didn't work, then I realized the instructions say to get the ALTERNATE installation CD.  I don't know why that is, and it took me a long time to find it, but I did eventually locate "ubuntu-12.04.2-alternate-i386.iso".

At the 3rd step, where you open the "Run Application" window, I type in gksu "sh /media/cdrom/cdromupgrade".  It then says "Entere your password to perform administrative tasks" and "the application sh /media/cdrom/cdromupgrade lets you modify essential parts of your system."Then a window pops up saying "Distribution Upgrade Upgrading Ubuntu to version 12.04Preparing to upgrade"A window pops up over this that says "Can not upgradeAn upgrade from 'maverick' to 'precise' is not supported with this tool"
[/LIST]
I've spent all day trying to upgrade this T60 and have failed at every turn.  Does anyone have any advice on a way to do this?Thank you for reading all of this.

---

### Post by c1933044 on 2013-12-01
Awesome.  My post comes out with no Newlines?  I typed them but they don't come out.testing123

---

### Post by Bashing-om on 2013-12-01
c1933044; Hey ... I know you are tired, aggravated and frustrated, so
My Suggestion
Download Lubuntu version 13.10;
 - Fits on a CD
 - recommended edition to run on older hardware
 - a fresh start with something that will work
[https://help.ubuntu.com/community/Lubuntu/GetLubuntu](https://help.ubuntu.com/community/Lubuntu/GetLubuntu)

When you have the .iso downloaded, verify the file integrity;
[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

Burn the .iso as an image (not as data !)
[https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)

Reset bios to boot from the CD device and
Boot Lubuntu to "try ubuntu" -> make sure all devices and everything functions in this mode, then:

Install Lubuntu !
I would suggest that you NOT check the boxes for 3rd party software or updates as it seems sometimes on older hardware the install process hangs. You can install these after the install is completed.

To me this is the easy course to get you a good operating system.

[INDENT][INDENT]just my thought
[/INDENT][/INDENT]

---

### Post by c1933044 on 2013-12-01
Thank you for the response!  And thank you to the moderators who added lines to my post and deleted my double post (believe me, I tried).  Yes- I am tired and frustrated :-D

I guess I could try a new OS...   Would like to find a way to update 10.10 but if there just is no way, I will give it a shot.  Is the GUI also gnome?  

thanks again.


Edited to add:  Oh look, I have Newlines now!  Things are getting better already...

---

### Post by mörgæs on 2013-12-02
The GUI is LXDE and not Gnome, but let's focus on that later. For now it's just a matter of getting Lubuntu 13.10 running.

---

### Post by c1933044 on 2013-12-07
I fixed my other computer and it now seems to be burning DVDs correctly.  I just gave up on trying to upgrade from within the Ubuntu 10.10 system, and instead burned a disk with 12.04LTS and did a fresh install with that.  Luckily, I had literally nothing on the 10.10 install that I cared about, or else I would be pretty annoyed that there seems to be no way to upgrade from 10.10 to a newer version.  I understand support for 10.10 has ended but there's really no good technical reason that I can detect which would prevent a sucessfull migration.  I thought Linux was supposed to get away from the rigid stupidity of the Windows evil empire...Anyway, lesson learned- I should take some of the intermediate upgrades when Ubuntu nags me about them!

---

### Post by Bashing-om on 2013-12-07
c1933044; Hey,

Pleased ya got things sorted out to your satisfaction !

There is a path indeed, however, that far back to get to a current version just is not recommended, lots a time and effort and the chance of error is great.
see:
[https://help.ubuntu.com/community/EOLUpgrades](https://help.ubuntu.com/community/EOLUpgrades)
For the details.

[INDENT][INDENT]not much else one can say
[/INDENT][/INDENT]

---

