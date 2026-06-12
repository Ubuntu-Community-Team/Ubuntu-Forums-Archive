---
title: "Ubuntu 11.10 Office Suite Installation Problem"
date: 2011-12-22
forum: Installation &amp; Upgrades
---

### Post by piezoelectron on 2011-12-22
Hello all,

I am seriously quite frustrated right now.

I installed Ubuntu 11.10 a few days ago and am enjoying the experience except for one messy problem.

I have many important files in .docx format in my Windows 7 Partition, which I want to open and read in Ubuntu. Since the default LibreOffice cannot do this, I decided to install OpenOffice 3.3.0. However, I have tried following at least 5 different installation instructions from various sites, including the official one, but to no avail. 

Hence, I decided to abandon OpenOffice and go for MS Offie 2010. I got Wine 1.3 and all its components from the Software Center, did the necessary configuration changes, got MSXML 6.0, VC2005 and gdiplus. I got the MS Office 2010 installation folder by copying it from my Windows C drive to the Ubuntu Home folder. However, when I try to open the setup.exe, the installation screen shows up for a splut second followed by the error message, "Installation Language not Supported". I am seriously at breaking point right now since the .docx files are of great importance and I really want a platform on 11.10 on which to view them. Possibly the problem is that the MS Office 2010 installation files are for 64-bit while my Ubuntu is 32-bit?

I would greatly, GREATLY appreciate any help in regard to an accurate installation procedure for OpenOffice 3.3.0, or for MS Office 2010, any troubleshooting, or any other software through which I can open, view, edit and save .docx and similar files on Oneiric. 

I am also looking for a good .docx to .odf converter as a last resort, so you can help in this regard as well.

---

### Post by darkod on 2011-12-22
When you say LibreOffice can't open .docx do you mean that it changes the layout etc? Because it can open them, but if there are specific MS features in the documents I don't think it can display them properly.

Not sure what happened during the OpenOffice install because you didn't provide any details, but you should be able to install. But even if you do, I think the same applies as with Libre, yes it can open them but not with any special features included only in MS Office.

As a quick fix, and depending how many documents you need, you can open them in windows and use Save As to save them as .doc and not .docx (you can still keep the .docx version). But again, that might lose some of the features, depending.

Bottom line, I wouldn't count too much on opening .docx in linux. Not only from linux perspective, it's how MS does things too I guess. You can't simply open them in OpenOffice in the same way, even on windows.

---

### Post by cybergalvez on 2011-12-22
Not sure what you mean, Libreoffice opens docx files, I know the formatting isn't always perfect but its pretty good. In fact I just tested it, I created a docx file on my mac (word 2011) and opened it in libreoffice with 11.10

---

### Post by Mark Phelps on 2011-12-23
Office 2010 does not work well in Linux, even with all the Wine tweaks applied.

The only way you're going to be able to RELIABLY edit your Windows DOC files in Ubuntu, is if you open them all in Word 2010 and save them using the old .doc extension.

Sorry, but it took CodeWeavers three years to get SOME of Office 2007 working reasonably well in Wine; expect the same delay for Office 2010.

---

### Post by grahammechanical on 2011-12-23
> Possibly the problem is that the MS Office 2010 installation files are for 64-bit while my Ubuntu is 32-bit?

It is not going to help, is it? If Ubuntu is 32bit, then wine is 32bit. It mostly likely is expecting 32bit Windows programs. But I do not really know.

Regards.

P.S. Having said the above I realise that I am using wine to run a Windows program that requires XP, Vista or Windows 7 and no mention is made as to whether it is 32bit or 64bit. I am using 11.10m 64bit.

---

### Post by piezoelectron on 2012-01-04
Hey everybody, 
Very sorry for the delay in replying. I wasn't being notified of these replies so I thought that the thread had bumbed.
Anyway, I DID succeed in installing OpenOffice. LibreOffice is not opening .docx files in my OS. I guess my version was outdated. 

The missing features are the main problem. Though OpenOffice does open .docx files, the format, as you said, is totally changed. 

And speaking of MS Office, I got a 32-bit CD and tried running it, but again, the same error of 'Installation Language not Supported' persisted. Any solutions for this?

Still, thanks a lot for all the support and help being provided!:D

---

