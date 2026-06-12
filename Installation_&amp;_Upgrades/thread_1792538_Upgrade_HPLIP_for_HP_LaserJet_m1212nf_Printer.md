---
title: "Upgrade HPLIP for HP LaserJet m1212nf Printer"
date: 2011-06-28
forum: Installation &amp; Upgrades
---

### Post by martinr on 2011-06-28
This thread covers setting up Ubuntu for usage with a "HP LaserJet Professional M1212nf MFP" printer. The goal is to get: printing, scanning and faxing working.

I'm running  Lucid 10.04 LTS  and want to use a network printer of type HP LaserJet Professional M1212nf MFP.

The drivers for this printer are contained in: HPLIP version 3.10.4 (and beyond)

The pre-packaged Ubuntu version of HPLIP currently is at version: 3.10.2-2ubuntu (output from $ dpkg -l hplip)

This [page]("http://hplipopensource.com/hplip-web/models/laserjet/hp_laserjet_professional_m1212nf_mfp.html") says that v3.10.4 works with Ubuntu 10.04 and that (network) printing, scanning and faxing should work.

What is the best way to install a newer version of HPLIP without breaking Synaptic package management?

---

### Post by nomko on 2011-06-28
HPLIP doesn't need synaptic to get installed. The file you download is a .run file. This file needs to be exectued in a terminal. Best is to download the file to your Download folder ( /home/{username}/Downloads ). Then open a terminal, go to your Downloads folder using: cd /home/{username}/Downloads. Type in the following command:[COLOR=black]** sudo chmod +x hplip-3.11.5.run** (this will make the file executable). Type in your password and Enter.[/COLOR]
 
After that type in: **./hplip-3.11.5.run** and the installation process starts. Make sure you choose for custom installation just to check what's going on and see what's happening. It will check for missing dependencies and it can install them automaticly (somehwere at the beginning you have to enter your password to let the installation procedure getting root priviliges). The installation is very easy and not so difficult. Any questions? let me know!
 
Oh yes, almost forgotten. This is the file you need: [http://prdownloads.sourceforge.net/hplip/hplip-3.11.5.run](http://prdownloads.sourceforge.net/hplip/hplip-3.11.5.run)
 
And noticing your Dutch, go to my site and see the procedure i set up for the HP ePhotoprinter B110a. The installation of your printer and mine is equally, you install the driver, not the printer ;-)

---

### Post by martinr on 2011-06-28
> **nomko said:**
> HPLIP doesn't need synaptic to get installed. The file you download is a .run file.
Thanks for your reply.

According to Synaptic version 3.10.2-2ubuntu is already installed on my system and managed by Synaptic. Should I first un-install this version with Synaptic or can I bluntly run the HPLIP auto-installer?

---

### Post by collisionystm on 2011-06-28
> **martinr said:**
> Thanks for your reply.

According to Synaptic version 3.10.2-2ubuntu is already installed on my system and managed by Synaptic. Should I first un-install this version with Synaptic or can I bluntly run the HPLIP auto-installer?


Uninstall it from Synaptic and run the installer from the HPLIP website.

I have done this a few times with no problems.

I to am using the same printer, but on 11.04.

---

### Post by nomko on 2011-06-28
> **collisionystm said:**
> Uninstall it from Synaptic and run the installer from the HPLIP website.
 
I have done this a few times with no problems.
 
I to am using the same printer, but on 11.04.
 
Also do a purge in a terminal:
 
```
sudo apt-get purge hplip*
```
 
This will remove any hplips remaining files.

---

### Post by martinr on 2011-06-28
Thanks guys! I followed both your advise and
I've got printing working now. :D

Scanning works occasionally for unknown reasons.

I get the following problems when trying to capture a scan:
```
Using device hpaio:/net/HP_LaserJet_Professional_M1212nf_MFP?zc=HP
Opening connection to device...
error: SANE: Error during device I/O (code=9)
```

Any ideas?

---

### Post by nomko on 2011-06-28
> **martinr said:**
> Thanks guys! I followed both your advise and
I've got printing working now. :D

Scanning works occasionally for unknown reasons.

I get the following problems when trying to capture a scan:
```
Using device hpaio:/net/HP_LaserJet_Professional_M1212nf_MFP?zc=HP
Opening connection to device...
error: SANE: Error during device I/O (code=9)
```Any ideas?

The site of Sane shows that your device is not supported: [http://www.sane-project.org/sane-mfgs.html#Z-HEWLETT-PACKARD](http://www.sane-project.org/sane-mfgs.html#Z-HEWLETT-PACKARD)
Both Xsane as Simple-scan uses Sane as backend so using simple-scan should give you the same error.

Did you answered with Y (Yes) during the installation of the HPLIP driver when the question "**Do you wish to enable 'Scanning support' (y=yes*, n=no, q=quit) ?**[COLOR=#000000]**"** was asked?[/COLOR]

---

### Post by martinr on 2011-06-29
> **nomko said:**
> The site of Sane shows that your device is not supported: [http://www.sane-project.org/sane-mfgs.html#Z-HEWLETT-PACKARD](http://www.sane-project.org/sane-mfgs.html#Z-HEWLETT-PACKARD)
Both Xsane as Simple-scan uses Sane as backend so using simple-scan should give you the same error.

Did you answered with Y (Yes) during the installation of the HPLIP driver when the question "**Do you wish to enable 'Scanning support' (y=yes*, n=no, q=quit) ?**[COLOR=#000000]**"** was asked?[/COLOR]
I did answer Yes during installation of Scanning support.

The sane-project site does not mention the HP m1212nf (which is of the m1210 series, which it neither mentions). So it does not state if it is supported or not (unsupported printers are also explicitly mentioned).

The [hplip-website]("http://hplipopensource.com/hplip-web/models/laserjet/hp_laserjet_professional_m1212nf_mfp.html") states that scanning should work for the hp_laserjet_professional_m1212nf_mfp on Ubuntu 10.04.

There is a remark on that page however, that states:
> Scan supported means that PC initiated scan using a SANE compatible software application is supported over parallel, USB, or network (depending on I/O connection). Information on digital sending products is covered in note 9, below.

9. Device supports digital sending, not standard scanning protocols. See this KB article for more info

[KB article]("http://hplipopensource.com/node/302"):
HPLIP software is not used in support of scanning on certain multifunction products (MFP's).  These products which use HP Digital Sending Technology allow scanning directly to email addresses, network folders, or other networked devices.
 
These MFP's do not support the SANE or TWAIN APIs, so HPLIP which provides SANE support is not needed for these devices.


I'm connected over a network. It seems that the printer has Digital Sending capabilities, but how can that be used from Ubuntu?

On the other hand I did manage to scan in B/W (with hp-scan) and Color (with xsane) only once right after set-up (or reset), but then it just stops working.
The [product specifications]("http://h10025.www1.hp.com/ewfrf/wc/document?docname=c02001433&tmp_task=prodinfoCategory&lc=en&dlc=en&cc=us&lang=en&product=3965849#N1647") note that it does support TWAIN:
> Scanning specifications
    * Scan from TWAIN-compliant or Windows Imaging Application (WIA)-compliant software.
    * Scan from a computer by using HP LaserJet Scan software for Windows or by using HP Director software for Mac.

[TWAIN VERSION]("http://h71016.www7.hp.com/html/pdfs/LaserJetProM1212nf.pdf"): Version 1.9


One has to actually reset the printer in order for it to scan again. Even from a Windoze Client scanning is blocked after xsane has scanned once.

Any suggestions, anybody?

---

### Post by Alfagulf on 2011-07-06
Dear Martinr,

I have the same problem, that is, it does not scan again (from another computer) unless I restart the printer!!

What firmware version do you have on your printer?
I have:
Firmware Datecode:	20100921

There seems to be a newer firmware available at HP web site :
[http://h10025.www1.hp.com/ewfrf/wc/softwareDownloadIndex?lc=en&dlc=en&cc=us&softwareitem=Im-80799-6&product=3965849&](http://h10025.www1.hp.com/ewfrf/wc/softwareDownloadIndex?lc=en&dlc=en&cc=us&softwareitem=Im-80799-6&product=3965849&)

Version 20110512

Description:
		This firmware update utility is for the HP LaserJet M1130_M1210 series printer only. The firmware version can be found on the Self Test / Configuration page. The configuration page can be printed by press go button.



I assume this firmware applies to HP Laserjet M1212nf, Does it?

Has any one tried to upgrade to this latest firmare?

Thanks

Update: I upgraded to the latest firmware mentioned above, but I am still unable to scan from other computers on the network after initiating a successful scan from one of the computers on the network!!
The error I got from the "Simple Scan" is "Failed to scan" "Unable to connect to scanner"

---

### Post by martinr on 2011-07-07
@Alfagulf The printers firmware version over here is: 20100921

After some testing I am sure now, that scanning from Ubuntu Linux with xsane only works once and then the printer needs to be reset/turned off and on again. Even trying to scan with another machine/OS like Windoze doesn't work anymore until the printer is reset. When initially scanning from Windoze, it does not leave the printer in an odd state, so multiple consecutive scans are no problem, but as soon as I do one scan with xsane on Linux the first scan succeeds but then the scanning capability stops working.

It seems that after scanning with xsame it leaves the printer in an odd state that requires a reset to get scanning working again.

Do more people experience this problem and might someone have succeeded in solving it already?

---

### Post by Alfagulf on 2011-07-07
I agree,
I have asked a question in launchpad for HPLIP developer hoping that they might have crossed over such issue:
[https://answers.launchpad.net/hplip/+question/163947](https://answers.launchpad.net/hplip/+question/163947)

A friend of mine who is a network administrator in a university have confirmed such problem with other HP scanners on their network!!

Can we expect support from HP?!!

---

### Post by martinr on 2011-07-07
Windoze scanning seems to work just fine. The problem seems to be the state that the SANE driver leaves the scanning facility in after it's done.

I have first submitted a bug at the XSANE project site [here]("https://alioth.debian.org/tracker/index.php?func=detail&aid=313207&group_id=30186&atid=410366").
The SANE people concluded that they do not provide the back-end for the hpaio driver and that it is part of the HPLIP project. See the next posting.

---

### Post by martinr on 2011-07-07
The SANE people concluded that they do not provide the back-end for the hpaio driver and that it is part of the HPLIP project, so I submitted the bug there.

Please view, add comments or vote for it [here]("https://bugs.launchpad.net/hplip/+bug/806950") in order to get scanning fixed.

Currently this bug only seems to affects 2 people and hasn't been assigned yet.

The bug heat score is too low, Launchpad looks at the bug's:
    number of subscribers
    number of duplicates
    number of people who've selected the "this bug affects me" option
    length of time since the last action

So if you experience similar problems please selected the "this bug affects me" option.

---

### Post by martinr on 2011-07-11
Today I needed to print a document and guess what, printing doesn't work any more. Back to square one :(

hp-check shows the following problem:
```

$ hp-check -t
...
HP_LaserJet_Pro_M1212nf_MFP
---------------------------
Type: Printer
Device URI: hp:/net/HP_LaserJet_Professional_M1212nf_MFP?zc=HP
PPD: /etc/cups/ppd/HP_LaserJet_Pro_M1212nf_MFP.ppd
PPD Description: HP LaserJet Professional m1212nf MFP, hpcups 3.11.5, requires proprietary plugin
Printer status: printer HP_LaserJet_Pro_M1212nf_MFP is idle.  enabled since Mon 11 Jul 2/usr/lib/cups/backend/hp failed
Required plug-in status: Installed
error: Unable to communicate with device (code=12): hp:/net/HP_LaserJet_Professional_M1212nf_MFP?zc=HP
error: unable to open channel
error: Communication status: Failed
...

```

Resetting the printer nor Ubuntu solves it. I'm baffled? After installing HPLIP 3.11.5 printing first worked fine. Pinging the printer works. I did not run update manager yet and only rebooted a few times. What's gone wrong here?

To fix it run hp-setup again and select the printer again as your preferred printer.

---

### Post by Alfagulf on 2011-07-13
[Solved] :)


After upgrading to 3.11.5 I deleted both the printer and FAX queues in HPLIP utility, I then used hp-setup and recreated the printer _without_ the FAX queue.

It seems to work now, I only have to power cycle the printer once while testing!!

---

### Post by martinr on 2011-07-14
> **Alfagulf said:**
> [Solved] :)


After upgrading to 3.11.5 I deleted both the printer and FAX queues in HPLIP utility, I then used hp-setup and recreated the printer _without_ the FAX queue.

It seems to work now, I only have to power cycle the printer once while testing!!

Is scanning working corectly too? Also consecutive times?
Does it keep working after a reboot / update ?

---

### Post by Alfagulf on 2011-07-14
Dear Martin,

Yes, I rebooted all machines and did consecutive scans from different machines and all seems to work!
I did not do any update however!
Are you still facing a problem?

Update: I just updated to the latest kernel 3.6.38.10 and scanning still work after that.

---

### Post by bluedalek on 2011-09-15
> **collisionystm said:**
> Uninstall it from Synaptic and run the installer from the HPLIP website.

I have done this a few times with no problems.

I to am using the same printer, but on 11.04.

Hi All

I need to chime in with a "me too!".

I have the same printer, and have had it for about a year now.  I've been very happy with it thus far, until last night. 

I finally got around to trying to install the hplip software (latest from hpopensource) on my laptop, and it's a no go.  The software downloads and installs fine, but when the software goes to install the binary driver, I get an error indicating that the file downloaded is incorrect or corrupted and to try again.

I've tried runnnig hp-setup as sudo and as a regular user, and no difference.

Any thoughts or suggestions?

Many thanks in advance!

---

### Post by martinr on 2011-09-17
> **bluedalek said:**
> Hi All

I need to chime in with a "me too!".

I have the same printer, and have had it for about a year now.  I've been very happy with it thus far, until last night. 

I finally got around to trying to install the hplip software (latest from hpopensource) on my laptop, and it's a no go.  The software downloads and installs fine, but when the software goes to install the binary driver, I get an error indicating that the file downloaded is incorrect or corrupted and to try again.

I've tried runnnig hp-setup as sudo and as a regular user, and no difference.

Any thoughts or suggestions?

Many thanks in advance!

Dear bluedalek,

I did not have your problems and assume that you really do have a corrupt installation package. I would suggest un-installing the packages, downloading a fresh copy and install it again (see first posting for the used versions).

After initial installation scanning freezes up after the first scan.
To fix it: delete the print queues run hp-setup again and select the printer again as your preferred printer (this recreates the print queues). All should work fine (printing, scanning and faxing) after recreating the print queues.

Good luck and let us know if it has worked for you.

---

