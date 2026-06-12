---
title: "Install wireless printer HP OfficeJet 7400 Series"
date: 2011-12-22
forum: Installation &amp; Upgrades
---

### Post by nawab_sahab on 2011-12-22
How do I install a wireless printer HP OfficeJet 7400 Series.

I am able to plug in the printer with a USB and able to print, but not through my wireless.

---

### Post by TBABill on 2011-12-22
In Ubuntu it's usually just a matter of opening the printing app, selecting add new printer, select "find wireless printers" and then waiting. It takes quite a bit of time and you get no indication that anything is happening, but on my HP C309A it just pops up on the list. Then I just select it, select forward, then it adds the driver and utility and asks if I want to print a test page or not.

---

### Post by chili555 on 2011-12-22
> **nawab_sahab said:**
> How do I install a wireless printer HP OfficeJet 7400 Series.

I am able to plug in the printer with a USB and able to print, but not through my wireless.Please clarify. Is the USB printer attached to Computer A and you wish to print to it wirelessly from Computer B?

---

### Post by Mark Phelps on 2011-12-22
Couple of ideas ...

Some HP printers do not allow simultaneous USB connection and Wireless.  You have to disconnect one or the other.  Check the manual that came with yours to see if this is the case.

You can try adding the printer using CUPS.  To do this, open a browser and enter "localhost:631".  That will start CUPS.

Then go to the Add option and see if the printer is listed on the networked printers page.  IF it is, select it and continue through the setup.

---

### Post by nawab_sahab on 2011-12-22
@Chili: The USB printer(HP OfficeJet 7400) is not attached to the Computer A. I want to use Computer A to print wirelessly to the printer(HP OfficeJet 7400).
 
Since Computer A cannot detect printer(HP OfficeJet 7400) wirelessly, I am having to use a USB cord to connect to the printer(HP OfficeJet 7400) which works fine.
 
I have Verizon Fios and use their wireless router. Also I use RALink RT 5370 Wireless adapter. The printer is on the wireless network and I have the IP address for the printer.

---

### Post by nawab_sahab on 2011-12-22
@Mark Phelps: I have tried that but it does not show my printer on the wireless network. Also I have tried using the IP Address of the printer but still nothing.

---

### Post by agillator on 2011-12-22
Since you have the ip of the printer, have you tried manually installing through HPLIP's HP Device Manager? Sometimes that is simpler and more successful than installing directly through CUPS, although it uses CUPS.

---

### Post by nawab_sahab on 2011-12-22
> **agillator said:**
> Since you have the ip of the printer, have you tried manually installing through HPLIP's HP Device Manager? Sometimes that is simpler and more successful than installing directly through CUPS, although it uses CUPS.
@agillator: Can you give me instructions on how to locate and use HPLIP?? I am new with Linux, never used it before until about a week ago.

---

### Post by agillator on 2011-12-22
Go to [http://hplipopensource.com/hplip-web/install_wizard/index.html](http://hplipopensource.com/hplip-web/install_wizard/index.html) and download the installation file. Important: PURGE the version Ubuntu installs (sudo apt-get purge hplip). That version has never worked right for me for some reason, so you will be replacing it. As I remember, you will need to change the permissions on the downloaded file so it is executable. 'chmod o+x' or 'chmod 744 <filename>' should do it. Then run the downloaded file. Be sure you do NOT run it as root or sudo. Run it as your normal user. You will want it to do the automatic installation. When it asks, give it your password. After that, sit back and watch - it will take a few minutes. There will probably be half a dozen or more dependencies it has to install. Some take several minutes. If automatic doesn't work, you will have to do those installations manually, so cross your fingers. Once the installation is complete, follow the instructions and run hp-setup. When that is complete you will have HPLIP installed and should be able to use any HP printer made in the last several years - my HP970, almost an antique, works fine.  But, you aren't done quite yet.

There should be an hp symbol on the panel now. That is the device manager. Right click on it and select the option to run the device manager. In the device manager, click the plus symbol or the DEVICE|SETUP DEVICE menu. In that window, select the 'network' option (NOT THE WIRELESS OPTION) and the Advanced option. On advanced, click on Manual Discovery and enter the ip of the printer in the box that is enabled. The next window SHOULD tell you one device was discovered. If so, click next, fill in the information on the next screen and click the install printer button. The program will install the printer through CUPS. Print a test page and everything should be fine. 

If your printer is not discovered after the step where you enter the ip then there is something else wrong. The printer could be misconfigured, there could be something wrong with the wireless network, it will require more digging. The first thing to check is probably the configuration of the printer. For example, is the ip you are using really what the printer is using and does the network really see it at that ip. Sometimes, on a reboot, the ips can get screwed up and that causes the printer to not be seen where you expect it. 

Let us know how this works. HP has done a pretty good job of developing linux support for their printers. I suppose there are a few that are not supported, but I haven't found any, new or old. So, good luck and we'll be waiting for your status report.

---

### Post by nawab_sahab on 2011-12-22
> **agillator said:**
> Go to [http://hplipopensource.com/hplip-web/install_wizard/index.html](http://hplipopensource.com/hplip-web/install_wizard/index.html) and download the installation file. Important: PURGE the version Ubuntu installs (sudo apt-get purge hplip). That version has never worked right for me for some reason, so you will be replacing it. As I remember, you will need to change the permissions on the downloaded file so it is executable. 'chmod o+x' or 'chmod 744 <filename>' should do it. Then run the downloaded file. Be sure you do NOT run it as root or sudo. Run it as your normal user. You will want it to do the automatic installation. When it asks, give it your password. After that, sit back and watch - it will take a few minutes. There will probably be half a dozen or more dependencies it has to install. Some take several minutes. If automatic doesn't work, you will have to do those installations manually, so cross your fingers. Once the installation is complete, follow the instructions and run hp-setup. When that is complete you will have HPLIP installed and should be able to use any HP printer made in the last several years - my HP970, almost an antique, works fine.  But, you aren't done quite yet.

There should be an hp symbol on the panel now. That is the device manager. Right click on it and select the option to run the device manager. In the device manager, click the plus symbol or the DEVICE|SETUP DEVICE menu. In that window, select the 'network' option (NOT THE WIRELESS OPTION) and the Advanced option. On advanced, click on Manual Discovery and enter the ip of the printer in the box that is enabled. The next window SHOULD tell you one device was discovered. If so, click next, fill in the information on the next screen and click the install printer button. The program will install the printer through CUPS. Print a test page and everything should be fine. 

If your printer is not discovered after the step where you enter the ip then there is something else wrong. The printer could be misconfigured, there could be something wrong with the wireless network, it will require more digging. The first thing to check is probably the configuration of the printer. For example, is the ip you are using really what the printer is using and does the network really see it at that ip. Sometimes, on a reboot, the ips can get screwed up and that causes the printer to not be seen where you expect it. 

Let us know how this works. HP has done a pretty good job of developing linux support for their printers. I suppose there are a few that are not supported, but I haven't found any, new or old. So, good luck and we'll be waiting for your status report.
@agillator: **Well hello wireless printing.** That was too easy.

I have used windows all my life and this Ubuntu is one hell of an OS. I  always thought this was like a DOS but its come a long way. Granted I  cannot do it myself...yet. But wow. 

I wish i could upload the test page that it just printed. Thank you agillator. This is amazing.

---

### Post by agillator on 2011-12-22
Glad to help, and glad it worked. Now you can help someone else. :)

---

