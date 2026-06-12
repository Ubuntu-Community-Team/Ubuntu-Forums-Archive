---
title: "Lts?"
date: 2015-05-20
forum: Installation &amp; Upgrades
---

### Post by Bob_Younkin on 2015-05-20
I do tech support for AARP Taxide.  We have a small army of volunteers who do income taxes for the elderly and financially disadvantaged.  Most of the XP laptops in our inventory weren't robust enough to be upgraded to WIN7.  The software we use in cloud-based and not terribly well written.  The only browsers it will allow are IE and Google Chrome. It will not run on Firefox and when I spoof it to think I'm running IE when I'm really running Firefox, it doesn't display correctly.

So as an experiment, I loaded Ubuntu 14.04 LTS on three machines along with Chrome.  About half way through tax season, we developed problems printing pdfs from Chrome and different parts of the website displaying content.  I couldn't figure out a fix but I discovered upgrading to 14.10 solved the problem OR installing Linux Mint instead.  Linux Mint say it is based on 14.04.

Is LTS really LTS or not.  I'm not excited about having to do a baziilion upgrades on these computers every year to keep them working.

Bob

---

### Post by TheFu on 2015-05-20
14.10 is NOT an LTS release. Support lasts about 9 months.
If you need LTS, use an LTS release.
[http://www.ubuntu.com/info/release-end-of-life](http://www.ubuntu.com/info/release-end-of-life) shows a graph pf the support which is nice.

The website is likely the issue, IMHO. Report the problem and have them fix it.

---

### Post by sudodus on 2015-05-20
In most cases and for most purposes the LTS releases offer long time support. Many Ubuntu users (including me) use LTS versions for the 'production computer', and test new things in the newest versions (which is seldom an LTS version). I think you had very bad luck, that the pdf printing stopped working.

If you need help with it, please describe the problem with more details. I think you should start a new thread with a good descriptive title (about the printing problem, Chrome and pdf).

The point release 14.04.2 LTS contains the kernel and the 'hardware enablement stack' from 14.10, and might work too for your printing. One the other hand, a kernel upgrade (within the same series of kernels) might have caused the problems. In that case starting again and updating other things, but not the kernel, might help. The problem might also be caused by an update of some application software, Chrome or some program library to manage pdf files or printing.

But if you are happy with 14.10, you might backup one of the computers and upgrading to the new version installing 15.04 - it will give you another 6 months of service, if it works well.

Before upgrading you should [try Ubuntu (Kubuntu, Lubuntu, Xubuntu,  ...) before installing it]("http://ubuntuforums.org/showthread.php?t=2230389") and if the upgrading fails you can make a fresh installation.

If there is not too much special software and tweaks, it is easier to make a fresh installation of the new version (without bothering with upgrading). If you want the same system in many computers, you can make one [master installation with OEM]("https://help.ubuntu.com/community/Ubuntu_OEM_Installer_Overview"), and clone it to the other computers. If you use the built-in free drivers (avoid proprietary drivers) for graphics and wifi, Ubuntu is portable between computers, that can be quite different.

---

### Post by TheFu on 2015-05-20
Adding onto what sudodus said ... you don't need for each of these PCs to be constantly updated. You can actually have them boot a minimal Linux (either from local, USB, or network) with X/Windows, then remotely connect on the LAN to a central box to run the browser and handle the printing. This is common in businesses.  On a LAN, running a remote browser won't feel any different than running it locally.

As to printing and viewing PDF files - there are many different ways to accomplish this.  Some tools will print to PDF directly. Others will have (or allow) you print to a generic postscript file, then automatically convert that to PDF.  Certain PDF generators may use Adobe extensions, so if that is how the PDF file is being created, you may need to use only Adobe products to handle the PDF.  The PS-->PDF method is pretty safe. That might be a workaround for you in the short term. With CUPS and a "Linux print server", you can automate this in almost any way you want.  Directly print the PS to a printer, print the PS file to PDF AND the printer, etc....

It is hard for a business NOT to have one Windows machine available "somewhere", but there isn't any need to have a 1-for-1 setup for every user. Deploying Windows into a VM and placing it on the network might be desirable - then users who might have issues can connect to it over RDP - it needs to be painful enough to make using it a last resort for the users or they will all cling to it. Which version of Windows to install would come down to budget and how many concurrent users are need to be supported.

---

### Post by ajgreeny on 2015-05-20
I would also suggest that when appropriate you download the PDFs and print them, if it's possible.

However it is just possible that the PDFs are "annotated" I think that is the word, as one or two that I have used from my bank have been, in which case they would not even open in Linux.  They had to be opened in Windows and would then change, and add pages according to what you entered on the forms.  If I am able, as it a large file, I will add an attachment archive of a PDF form from a UK bank which will not open in Ubuntu but does open in a VBox install of WinXP.
Sorry, the file is too large.

I have also occasionally had difficulties printing PDFs in Ubuntu when using evince, but have been able to do so when opening the PDF using okular, so maybe you also could use a different application to open and print the PDF.

---

