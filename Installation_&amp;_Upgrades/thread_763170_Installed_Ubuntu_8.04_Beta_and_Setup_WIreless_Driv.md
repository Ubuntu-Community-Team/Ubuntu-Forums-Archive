---
title: "Installed Ubuntu 8.04 Beta and Setup WIreless Driver on Gateway ML3109 (Notebook PC)"
date: 2008-04-22
forum: Installation &amp; Upgrades
---

### Post by darkwing_duck on 2008-04-22
Hi all, hope this helps.  Keep in mind, this is my first experience with Ubuntu (I've tried other Linux Distributions, but always gave up and returned to Windows).  I already had a wireless router setup at my home with encryption disabled (I'll enable encryption soon).

Thanks to ["ICould Beat Simon"]("http://ubuntuforums.org/showthread.php?t=664353") for showing how to setup wireless for Ubuntu 7.10

1. Installed Ubuntu 8.04 (on my [Gateway ML3109]("http://support.gateway.com/s/Mobile/2007/Apache/1014550R/1014550Rnv.shtml"))
 - Downloaded [Ubuntu 8.04 Beta]("http://www.ubuntu.com/testing/hardy/beta") ISO Image
 - Burned image onto a CD using my Windows Vista machine and [ISO Burner]("http://isorecorder.alexfeinman.com/isorecorder.htm")
 - Inserted CD into Gateway ML3109
 - Restarted ML3109 and selected the install option from Ubunto menu

2. Downloaded files for wireless driver installation (Using another computer)
 - On my Windows Vista Desktop I downloaded the following files:
   [ndiswrapper 1.52]("http://ndiswrapper.sourceforge.net/joomla/")
   [realtek 8185 drivers]("ftp://152.104.238.19/cn/wlan/RTL8185_6.1102.0702,UI_1.00.0006.zip")
 - Unzipped the realtek file and fetched the "WINXP" directory
 - I put the "WINXP" and 'ndiswrapper' files onto my thumbdrive for transfer to the laptop ML3109

3. Connected ML3109 to internet
 - Climed into the attic and connected to modem (with ethernet cable)
 - System > Administration > Update Manager (checked for, and installed, updates)

3. Configured Synaptic Package Manager to not prompt me for Ubuntu CD
 - Settings > Repositories
   - Went to "Ubuntu Software" Tab (was there by default)
     - Unchecked the "Installable from CD-ROM/DVD" box
     - Checked all other boxes
   - Went to "Third-Party Software" Tab
     - Checked all boxes
   - Went to "Updates" Tab
     - Checked "Important security updates"
     - Checked "Recommended updates"

4. Used Synaptic Package Manager to download and install
 - g++-4.2
 - g++-4.2-multilib
 Note: Synaptic Package Manager installed many other necessary packages.

5. Installed build-essentials
 - Applications > Accessories > Terminal
 - 'sudo apt-get install build-essential'

6. Escaped from the attic
 - Turned off computer
 - Unpluged from modem
 - Returned downstairs to the livingroom
 - Turned on computer

7. Updated blacklist file
 - Applications > Accessories > Terminal
 - 'sudo gedit /etc/modprobe.d/blacklist'
 - Added the following lines to the end of the file:
   blacklist r818x
   blacklist r8180
   blacklist r8187
 - Restarted the laptop (Gateway ML3109)

8. Transferred "WINXP" and 'ndiswrapper' to ML3109
 - plugged in thumbdrive and transferred "WINXP" and 'ndiswrapper' to ML3109 desktop
 - Opened terminal (Applications > Accessories > Terminal)
 - Changed directory to desktop ('cd Desktop')
 - Extracted 'ndiswrapper' file ('tar -xf ndiswrapper-1.52.tar.gz')
 - Changed directory to extracted 'ndiswrapper' ('cd ndiswrapper-1.52')
 - 'sudo make uninstall'
 - 'make'
 - 'sudo make install' (no errors or warnings observed)

9. Installed wireless drivers
 - opened terminal (Applications > Accessories > Terminal)
 - Changed directory to "WINXP" ('cd Desktop/WINXP/')
 - 'sudo bash'
 - 'ndiswrapper -i net8185.inf'
 - 'ndiswrapper -l' (returned message: 'net8185:driver installed device (10EC:8185) present)
 - 'modprobe ndiswrapper'
 - 'sudo gedit /etc/modules'
 - added 'ndiswrapper' to end of file so it will load when I power up the ML3109 laptop

10. Connected to internet (wireless, no encryption enabled yet)
 - Clicked on the network connection icon in upper right corner of screen
 - Selected my network essid from a list of nearby network essid's

Next step: setup encryption

---

### Post by evil baz on 2008-04-25
Darkwing, this is an excellent resume to how to make Ubuntu/Kubuntu Work with a ML3109 (which is not mine, it is of my brother) I spent 2 day trying to fix the Wirless card, but you rpost saved my day, thanks pal.

---

### Post by darkwing_duck on 2008-04-27
Glad to have helped.  Enjoy!

---

### Post by xtkid on 2008-04-29
Hi darkwing_duck, thanks for this great guide. I also recently tried a live cd of Ubuntu 8.04 final. I immediately switched back to Windows. Ubuntu has fixed lots of problems on Gateway ML3109 but wirless is still a big issue and I heard that Sound is only Mono. Have you tried Ubuntu 8.04 Final? If yes, were there any changes needed in your guide above?

Again, Thanks.

---

### Post by darkwing_duck on 2008-05-02
Xtkid,

The wireless on my ML3109 works with no problems (including encryption).  To tell you the truth, I almost never use the audio on this ML3109 anyways, so Mono is just fine for me.  However, I'll look into it ASAP and reply here if I find out how to make it Stereo.

I'll upgrade from 8.04 Beta to 8.04 Final tonight and let you know if I find anything out.

Keep trying my friend.](*,)

---

### Post by xtkid on 2008-05-11
Thanks darkwing_duck.  PLS let me know about your Ubuntu 8.04 Final results.

---

### Post by darkwing_duck on 2008-07-23
Yup, just installed 8.04 final version (non-beta).  Sound works and so does the wireless with WEP encryption.  Don't know how to check if sound is stereo or if WPA encryption works, but I'm not too worried about those either.

P.S. Used same installation steps of beta version.

---

### Post by neofreud on 2009-04-02
Could the same process be used with a differnt model laptop .. it seems like all you would swap out would be the driver right?

---

