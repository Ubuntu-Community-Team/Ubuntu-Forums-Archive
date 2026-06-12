---
title: "Installing Smartboard notebook and drivers"
date: 2011-02-26
forum: Installation &amp; Upgrades
---

### Post by scmior on 2011-02-26
Hi so I just install Ubuntu 10.10 and downloaded the Smartboard install. After I click the program to install it starts thinking then asks for my password. I enter my password it takes it then stops thinking. All other functions work just fine apart from the install. It hasn't started yet. 

I have a feeling that it would install just fine if I could take of the whole asking for the password nonsense. is there a way to do that. Might there be some other horrible prob I have not considered? Any help would be great!

---

### Post by scmior on 2011-02-26
K on second thought I uninstalled the program that it install when clicked on. It install an AutoPackager to turn the install into an executable. I uninstalled because I remeber it saying install incomplete. Now I cannot try to reinstall... has anyone had success with installing this software on their Ubuntu system. Or have I just messed it up?

---

### Post by Mithrandir1002 on 2011-03-07
Hi Scmior

I think I had exactly the same issues as you are experiencing with installing SMART notebook and drivers. I also have a fresh install of Ubuntu 10.10 (Maverick) on a notebook.

I'm not an Ubuntu wizard, but I succeded in making this program install and run on this 10.10. I can only refer to how I came around the problem, and then hope that it will solve your problem as well.

**step 1:** Downloaded the Linux software from [http://smarttech.com/us/Support/Browse+Support/Download+Software/Software/SMART+Notebook+collaborative+learning+software/SMART+Notebook+software/SMART+Notebook+for+Linux](http://smarttech.com/us/Support/Browse+Support/Download+Software/Software/SMART+Notebook+collaborative+learning+software/SMART+Notebook+software/SMART+Notebook+for+Linux)

**Step 2:** Browsed to the download folder in a terminal and wrote the command $ sudo tar -xvzf smart_notebook_software_with_drivers_10_2.tar.gz

**Step 3:** I then doubbleclicked the SMART Notebook Software With Drivers 10.package, in Nautilus, and made it run in a terminal. It installed the AutoPackager program.

**Step 4:** I then again doubbleclicked the SMART Notebook Software With Drivers 10.package file and it started to ask me for my password. I typed in the password and then it didn't do nothing else than just have a bar bouncing back and forth as if the installation had stalled by a problem, but just didn't tell me what was wrong. - I kinda have the feeling that this might be where you are right now.

**Step 5:** I then returned to the terminal and tried installing it from the command line with the command $ sudo package install SMART\ Notebook\ Software\ With\ Drivers\ 10.package. Then a window popped up and I was able to follow the software checking for different dependencies, and it turned out that I needed a package called "libmng1".

**Step 6:** I installed the missing package by entering $ sudo apt-get install libmng1 - and then tried to install the package again using the command $ sudo package install SMART\ Notebook\ Software\ With\ Drivers\ 10.package. It checked all dependencies and found them all and then proceeded with installing the SMART notebook software.

I havent tested the software with a smartboard yet, but it's now working on my Ubuntu box.

Hope this will help you

---

### Post by tomcripps on 2011-03-27
Hi, 

I had the same problem as you. Followed your instructions which got me so far as... " Failed...." " uninstall smart-common files before continuing" I'm a bit stuck now. I went on to 3rd part software manager and it does not show that Smart notebook has been installed. How do I uninstall the the common files... I didn't think had been installed....

Tom


Done it ....

---

