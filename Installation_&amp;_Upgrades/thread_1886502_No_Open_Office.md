---
title: "No Open Office"
date: 2011-11-25
forum: Installation &amp; Upgrades
---

### Post by undo123 on 2011-11-25
Hi all.
I have just up graded to Ubuntu 11.04 and in the process the installation removed Open office and replaced it with LidreOffice. 
I can not remove LidreOffice and if I try to reinstall open office it autocratically install Libreoffice.

Had Ubuntu become a dictatorship that now we can only have what they want or have I missed something somewhere.
JSK

---

### Post by BC59 on 2011-11-25
Here are the instructions on how to do it:

[http://www.webupd8.org/2010/03/install-upgrade-openoffice-32-from-ppa.html](http://www.webupd8.org/2010/03/install-upgrade-openoffice-32-from-ppa.html)

A correction

I tried to install the PPAs but because is for Karmic only, they aren't working directly.
You have to go to Software Sources-->Other Software and Edit the 2 PPAs

> [http://ppa.launchpad.net/openoffice-pkgs/ppa/ubuntu](http://ppa.launchpad.net/openoffice-pkgs/ppa/ubuntu)
[http://ppa.launchpad.net/openoffice-pkgs/ppa/ubuntu](http://ppa.launchpad.net/openoffice-pkgs/ppa/ubuntu)

to have as Distribution not Oneiric (if you use 11.10) but Karmic

---

### Post by crazy bird on 2011-11-25
First of all, Ubuntu 11.04 comes standard with LibreOffice, so most likely you didn't do anything during installation. In fact, during installation there's no option to change/view the applications which will be installed (correct me if i'm wrong).
 
I think you need to add the PPA of OpenOffice in order to get it installed properly:
Open a terminal and type the following command: 
**sudo add-apt-repository ppa: openoffice-pkgs/ppa** 
(make sure that ppa: and openoffice-pkgs/ppa are written in one word) 
Then in the same terminal type: **sudo apt-get update**
 
Then go to synaptic and search for libreoffice. Mark everything of LibreOffice for removal, best is to select the -common package (or the -base package) since this package then will select every dependency needed for installation/removal of the -common package (or -base) package.
 
Then search for openoffice and select the -common (or -base) package for the same reason as above mentioned. Mark them for installation.
 
This should do the trick.
 
 
> Had Ubuntu become a dictatorship that now we can only have what they want or have I missed something somewhere.
No, Ubuntu is not. If Ubuntu did become a dictator, then it won't be possible or it was very difficult to install other program's then the standard installed applications. And this would be a "direct attack" on the philosophy of Linux being an open and free operating system in which every user can change/modify whatever the user wishes to do.

---

### Post by BC59 on 2011-11-25
> **crazy bird said:**
> 
Then go to synaptic and search for libreoffice. Mark everything of LibreOffice for removal, best is to select the -common package (or the -base package) since this package then will select every dependency needed for installation/removal of the -common package (or -base) package.
 


The best way to remove LibreOffice is through Ubuntu Software Center. From Synaptic there is a risk of an error.

---

### Post by robert shearer on 2011-11-25
> **BC59 said:**
> The best way to remove LibreOffice is through Ubuntu Software Center. From Synaptic there is a risk of an error.

care to expand on that...?
(as I doubt your assertion but am open minded enough to accept new information...:) )

---

### Post by crazy bird on 2011-11-25
> **BC59 said:**
> From Synaptic there is a risk of an error.
 
Please explain! I never had and/or experienced any problems using synaptic! I always advice synaptic since i think synaptic is a much better place for adding/removing software!
 
What kind of risks you're talking about?

---

### Post by mastablasta on 2011-11-25
Libre office is improved and bugfixed Open Office. Why would you want to replace is with OpenOffice that stalled in it's development?

---

### Post by BC59 on 2011-11-25
I'm sorry for my opinion but from Synaptic I count **32** LibreOffice packages to remove and I'm not pretty much sure if I have to remove them all.

From Ubuntu Software Center you have to click **Remove** from the 5 apps installed Writer, Base etc.

Of course there is people who like always to do it the hard way....

---

### Post by crazy bird on 2011-11-25
> **BC59 said:**
> I'm sorry for my opinion but from Synaptic I count **32** LibreOffice packages to remove and I'm not pretty much sure if I have to remove them all.
 
From Ubuntu Software Center you have to click **Remove** from the apps installed.
 
Of course there is people who like always to do it the hard way....
 
And do you really think that using Ubuntu Softwarecentre for removing any applications those other files (dependencies) will not be removed? If you remove an application by using Softwarecentre, all depedencies for that one application will also be removed since they are no longere needed. The only difference is that Synaptic shows you which packages will be removed. Softwarecentre is just an easy GUI for un-/installing applications, but beneath that shinny layer it does exacly the same as Synaptic! The main disadvantage of Ubuntu Softwarecentre is that it doesn't show you which packages will be installed or uninstalled. For me Ubuntu Softwarecentre is nothing more than "*un-/installing applications for dummies*". 
 
And yes, sometimes you want to install just 1 single application and during the installation several more packages will be installed. Those packages are called dependencies and are needed just for that single application. When such dependencies are not already installed, they will be marked for installation too. Compare it with buying a car. You not only buy the chassis, but also the wheels, seats, engine, gearbox, bodywork, etc. 
 
 
And as mastablasta already mentioned, why downgrading to OpenOffice since LibreOffice is the improved OpenOffice?
 
> Of course there is people who like always to do it the hard way
It has nothing to do with the "hard way"!

---

### Post by BC59 on 2011-11-25
> **robert shearer said:**
> care to expand on that...?
(as I doubt your assertion but am open minded enough to accept new information...:) )

Well there is always time to learn

> The 11.04 doc states

Synaptic's interface is more complicated and does not support newer Software Center features like ratings and reviews and thus is not recommended for use by those new to Ubuntu.

And read more here.

[https://help.ubuntu.com/11.04/ubuntu-help/addremove-install-synaptic.html](https://help.ubuntu.com/11.04/ubuntu-help/addremove-install-synaptic.html)

---

### Post by crazy bird on 2011-11-25
> Synaptic's interface is more complicated
More complicated??? In what way???? Synaptic is more powerful than Ubuntu Softwarecentre but that doesn't make synaptic more complicated.
 
> and does not support newer Software Center features like ratings and reviews
Who selects his/her applications by reviews and ratings? IS personal preference not the decisive factor wether to use or not to use an application? Reviews and ratings can be quite contradictory.
 
> and thus is not recommended for use by those new to Ubuntu. 
It should be recommended for new users to use synaptic! Then they would learn much more about Ubuntu and the way applications are installed instead of pressing a button and watch a progress bar like a dumb sheep...
 
Like i said, Ubuntu Softwarecentre is more like "*installing applications for dummies*" and that is not ment offensively.

---

### Post by BC59 on 2011-11-25
In general you have right and I use Synaptic as well, but I feel that Ubuntu Software Center is more apt for a starter, because the error possibilities are less (not zero).

Of course there is a long way ahead for Soft Center to include all the capabilities of Synaptic.

---

### Post by vasa1 on 2011-11-25
> **mastablasta said:**
> Libre office is improved and bugfixed Open Office. Why would you want to replace is with OpenOffice that stalled in its development?

Just in case this ^^^ gets lost in the Synaptic versus Ubuntu Software Center debate!

---

### Post by crazy bird on 2011-11-25
Good point vasa1! We were heading towards offtopic lane!
 
@undo123:
Basically me, mastablasta and BC59 are pointing out to you that downgrading to OpenOffice has effectively seeing no point. LibreOffice works as good as OpenOffice!

---

### Post by BC59 on 2011-11-25
I posted a correction above for our friend who started the thread, because the PPAs needed a tweak to work.

---

### Post by anyone786 on 2011-11-30
It is good that Libreoffice (LO) has forked, however, there are benefits to OpenOffice, eg I have spent a long time trying to open pdf  in LO Draw or Writer.  I have only obtained gobbledygook.  All LO addon/extension sites have nothing for pdf.  Yet LO  claims to have inherent pdf importer and claim to be compatible with imports from openOffice addons.

Thus, I tried to use Oracle pdfimporter1.0.4 and got either nothing happening or errors of dependency and reference to a file that should possibly not be a dependcy.

However, in frustration I am going to try install Openoffice alongside LO and see if I can then use pdfimporter1.0.4 .

However I am not a techie and having problems with using Ubuntu SoftwareCentre to point to the folder where I have downloaded openoffice OOo_3.3.0_Linux_x86_install-deb_en-GB.tar.gz..

---

### Post by grahammechanical on 2011-11-30
If Ubuntu/Canonical is not some kind of dictatorship then why is Mark Shuttleworth called SABDFL by the Ubuntu developers?

Self Appointed Benevolent Dictator For Life. It says it all. As they say Ubuntu is not a democracy and neither is democracy a requirement for developing Open Source Software.

It is my understanding that Ubuntu is firmly set on being open source but also firmly set on giving users the option to used closed source/proprietary software if they so choose. The question is how long will OpenOffice remain open source?

LibreOffice was selected as the default office suite because its developers are firmly set for Libreoffice to remain open source whereas there are doubts that the copyright owners of OpenOffice are committed to the concept of open source.

Regards.

---

### Post by bluexrider on 2011-11-30
I'm sorry, if I may

This thread has become a bi*ch session. If you people can't answer the question quit elongating.

Answer the question 

OpenOffice was replaced by LibreOffice as a default suite. Period!

If you choose to download it and replace LibreOffice then use xxxxxx.com

and address the last question which was rhetorical. NO! 

> **undo123 said:**
> Hi all.
I have just up graded to Ubuntu 11.04 and in the process the installation removed Open office and replaced it with LidreOffice. 
I can not remove LidreOffice and if I try to reinstall open office it autocratically install Libreoffice.

Had Ubuntu become a dictatorship that now we can only have what they want or have I missed something somewhere.
JSK


Happy *buntuing

---

### Post by mastablasta on 2011-12-01
> **anyone786 said:**
> It is good that Libreoffice (LO) has forked, however, there are benefits to OpenOffice, eg I have spent a long time trying to open pdf in LO Draw or Writer. I have only obtained gobbledygook. All LO addon/extension sites have nothing for pdf. Yet LO claims to have inherent pdf importer and claim to be compatible with imports from openOffice addons.
 
Thus, I tried to use Oracle pdfimporter1.0.4 and got either nothing happening or errors of dependency and reference to a file that should possibly not be a dependcy.
 
However, in frustration I am going to try install Openoffice alongside LO and see if I can then use pdfimporter1.0.4 .
 
However I am not a techie and having problems with using Ubuntu SoftwareCentre to point to the folder where I have downloaded openoffice OOo_3.3.0_Linux_x86_install-deb_en-GB.tar.gz..
 
 
never tried that. i have to give it a try. there are two versions of Libre office and one of them is (IMO) broken. didn't even want to open old Word file.
 
The file you downloaded needs to be extracted first. from it's description it might have a .deb file inside, which is kind of just like exe file in windows. you double click it and install it. of not then try to get the .deb file. also these .tar.gz install files usually contain a readme file that explains how to install it (often you can copy paste commands form it to terminal to make it all faster if they need to be compiled)

---

### Post by ottosykora on 2011-12-01
>Synaptic's interface is more complicated and does not support newer Software Center features like ratings and reviews<

well such nonsense is nice for simples like smartphone users and not for normal average computer user. Ratings and reviews are often just advertising matter and are very bad for new users as some of them might really believe the message behind it...

---

