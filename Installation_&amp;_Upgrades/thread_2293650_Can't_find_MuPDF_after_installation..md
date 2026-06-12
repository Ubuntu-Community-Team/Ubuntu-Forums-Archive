---
title: "Can't find MuPDF after installation."
date: 2015-09-06
forum: Installation &amp; Upgrades
---

### Post by AmericanPi on 2015-09-06
I've searched the great threads in this forum and this is where I am now.

I can find MuPDF in the Ubuntu Software Center's Installed/Graphics window. And there is a check mark on the app.
But it won't come up in the search bar! And it isn't in the Apps section either.

I have to have a PDF viewer for school and the semester just started. (can I get ADOBE?) Please Help :confused::confused:
nOOb to Linux ):P
What do I do now?

---

### Post by coffeecat on 2015-09-06
The default and already-installed PDF viewer in Ubuntu is called Document Viewer, previously Evince. Simply double-click on a pdf file and it will open in Document Viewer. 

MuPDF doesn't appear in the dash, but if you right-click on a pdf file and choose "open with", MuPDF will appear in the context menu. If you open the pdf with MuPDF, the icon for MuPDF will appear in the launcher from where you can right-click on it -> Lock to Launcher to keep it in the launcher for next time. That being said, I think you'll find the default Document Viewer better.

---

### Post by AmericanPi on 2015-09-06
Well....It did come up when I right clicked and "opened with", and thanks for telling me about Doc Viewer. I like Doc Viewer better.

the app did pop up into the launcher and is locked there now.
Thanks for the help!
but looking forward, i anticipate problems if i cant find things I download.

thoughts?

---

### Post by coffeecat on 2015-09-07
> **AmericanPi said:**
> 
but looking forward, i anticipate problems if i cant find things I download.

thoughts?

The vast majority of applications that you will install from the Software Centre will show up properly in the dash. The main exceptions being terminal only apps, which need to be executed from the terminal. A few applications not in the main or restricted repositories - that is, not officially supported - won't have been packaged with *.desktop configuration files, and these won't appear in the dash unless you create your own desktop file or use the trick I suggested. If you experience any problem accessing any application you install, you are very welcome to start a new thread.

As a newcomer to Ubuntu, you may find this description of the four principle repositories helpful: [https://help.ubuntu.com/community/Repositories/Ubuntu](https://help.ubuntu.com/community/Repositories/Ubuntu)

If you find a GUI application in the Main or Restricted repositories that has not been properly configured to appear in the dash, I'll eat my hat - or post a bug report! :wink: Applications in the Universe and Multiverse are sometimes of a lower standard. MuPDF is in the Universe repository, but unfortunately Software Centre is rather vague about which repo a particular application is installed from, contenting itself with this for MuPDF:

> Canonical does not provide updates for MuPDF. Some updates may be provided by the Ubuntu community.

In time you will come across PPA repositories. Very useful, but exercise extra caution if you decide to use any PPA or other 3rd party repositories. Some are excellent; some can damage your system. And don't go downloading stuff from random sites on the internet, like many do with Windows. 99.9% of what you need should be available via a repository somewhere.

---

