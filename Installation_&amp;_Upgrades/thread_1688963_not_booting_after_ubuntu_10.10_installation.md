---
title: "not booting after ubuntu 10.10 installation"
date: 2011-02-16
forum: Installation &amp; Upgrades
---

### Post by srihari29691 on 2011-02-16
I installed ubuntu 10.10, 64 bit on my friend's computer recently

after installation and reboot it stops without even without displaying the grub menu.No start up, no booting, not booting into windows.** i get a non-blinking cursor after the Toshiba start screen. not able to access the setup or boot options either! what do i do?!**

details:
-toshiba laptop, intel pentium processor
-had windows 7 installed previously
-new partition created prior to installation

**need a solution desperately! and soon!**

---

### Post by Rubi1200 on 2011-02-16
Hi and welcome to the forums :-)

Please do the following:

Boot the Ubuntu Live CD/USB. Choose the option "Try Ubuntu without any changes." Once the desktop loads come back here and do the following:

1. Download the boot info script. There is a link in my signature.
2. Once downloaded, move the boot info script to the desktop.
3. Open a terminal and run the command

```
sudo bash ~/Desktop/boot_info_script*.sh
```

This will create a RESULTS.txt file on the desktop. Paste the _entire_ contents of that file back here in a new post. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text.

---

### Post by srihari29691 on 2011-02-16
Hi Rubi! thanks for your reply!:)
turns out it was some kind of a static on the RAM that i could set right by a power reset... :) worked fine after that! thanks a lot anyway! :)

---

### Post by Rubi1200 on 2011-02-16
No problem, you are more than welcome :-)

Glad you got it sorted out.

---

### Post by DegreesCelsius on 2011-02-16
I was having this same problem and I still am. Umm... Well I don't have an internet connection on the computer that I have ubuntu 10.10 installed. It doesn't always boot. I have reset the computer a few times. It has worked twice. I had to re-install in order to get it to boot a second time.

Is there a way to fix this?

---

### Post by Rubi1200 on 2011-02-16
> **DegreesCelsius said:**
> I was having this same problem and I still am. Umm... Well I don't have an internet connection on the computer that I have ubuntu 10.10 installed. It doesn't always boot. I have reset the computer a few times. It has worked twice. I had to re-install in order to get it to boot a second time.

Is there a way to fix this?
Hi and welcome to the forums :-)

We need more information to help you.

1. how did you install Ubuntu exactly; with Wubi inside Windows or to the drive?

2. what are the specifications for the computer?

Any other relevant information would also be good.

Thanks.

---

### Post by DegreesCelsius on 2011-02-16
I have a FS7600 Compaq Desktop Computer.
It originally ran Windows XP but I removed that.

I installed it using a 10.10 Ubuntu Live CD I received in the mail.

I have no internet connection with that computer.

---

### Post by Rubi1200 on 2011-02-16
When the computer is booting, hold down Shift to bring up the GRUB menu.

When the entry for Ubuntu is highlighted, press "e" to edit. Navigate using the arrow keys and find the line that ends with > quiet splash

Remove this and type nomodeset instead then "Ctrl" + "X" to boot.

Does this get you further?

If you do not get the GRUB menu, what exactly happens?

(by the way, you may have to play around with using Shift to get it right).

---

### Post by DegreesCelsius on 2011-02-16
Well I am at school right now, I will try this when I get home.

When I boot, it kinda puts my computer into standby mode unless I select "Press ESC for Bootmenu" which I am guessing is the GRUB?

---

### Post by Rubi1200 on 2011-02-16
What happens when you select  "Press ESC for Bootmenu"?

Does the computer have only 1 drive?

By the way the Boot Menu is not the same as the GRUB menu.

The boot menu allows you to change the boot priority of the various devices such as CD drive, hard-drive, removable devices etc. in terns of which one has priority when the computer starts.

Tell us what it shows you when you go in there.

---

### Post by DegreesCelsius on 2011-02-16
I have accessed the grub menu before but I had to press F10 repeatedly. It listed.
-Ubuntu 10.10
-Ubuntu 10.10 (Safe Mode)
- and some other options that I cannot recall at the moment.

---

### Post by Rubi1200 on 2011-02-16
I would go with trying all those options and see how far you get.

When you post back, try and be as specific as possible as to the problems/errors you encounter.

Thanks.

---

### Post by chrisjabroni on 2011-04-14
Hi, sorry if this is too late of a post, it just directly relates to this thread.

I am having the same issue. By changing to "nomodeset" it booted no problem, but whenever GRUB appears when i first boot to select the OS, and I select Ubuntu, it just goes to a black screen.

Any ideas?

Thanks!

---

### Post by chrisjabroni on 2011-04-17
Bump

---

### Post by Rubi1200 on 2011-04-17
Are you saying you get the blank screen after using nomodeset or on subsequent boots?

If the former, I don't know what to tell you.

If the latter, then you can make it more permanent.

See here for details on how to do this:
[http://ubuntuforums.org/showpost.php?p=10069997&postcount=1](http://ubuntuforums.org/showpost.php?p=10069997&postcount=1)

---

### Post by chrisjabroni on 2011-04-17
> Are you saying you get the blank screen after using nomodeset or on subsequent boots?

If the former, I don't know what to tell you.

If the latter, then you can make it more permanent.

See here for details on how to do this:
[http://ubuntuforums.org/showpost.php...97&postcount=1](http://ubuntuforums.org/showpost.php...97&postcount=1)

It was the latter, but ...

THAT'S PERFECT!!!!!!!!! THANK YOU SOOOOO MUCH!!!! I'm new to forums is there a way to add to reputation or something along those lines? You so deserve it!


I have another question for you, since you are now officially my hero :)

Can I change the order on the grub page? Instead of having Ubuntu at the top of the list can I change it Win7?

---

### Post by Rubi1200 on 2011-04-18
Excellent, I am really pleased you got it sorted out :-)

As to the GRUB question, I can help there too.

There is a nice GUI application called Grub Customizer that does what you want.

Here is the link with a tutorial by staff member drs305:
[http://ubuntuforums.org/showthread.php?t=1664134](http://ubuntuforums.org/showthread.php?t=1664134)

See section 4 on how to move entries to a different position on the menu.

By the way, there is no official way of thanking someone other than what you have already said in your post. 

I appreciate the kind words :-)

---

### Post by chrisjabroni on 2011-04-18
> 1. Installation
Synaptic:
Start Synaptic
System > Administration > Synaptic Package Manager
Add the repository
Settings tab > Repositories > Other Software > Add
Type: ppa:danielrichter2007/grub-customizer > Add Source > Close
Reload
Install Grub Customizer
'Quick-search' > type "grub-customizer" > Select "grub-customizer" in lower panel.
Apply.

Software Center:
Start Software Center
Applications > Ubuntu Software Center
Add the repository
Edit > Software Sources > Other Software > Add 
Type: ppa:danielrichter2007/grub-customizer > Add Source > Close
Reload
Install Grub Customizer
Highlight "Get Software" in the left panel.
In the upper right search window, type "Grub Customizer".
Double-click "Grub Customizer" and click the 'Install' icon.

Terminal:
Add the repository to your system. The following commands will add the repository, import the security key, update the list of available packages and install Grub Customizer.
Open a terminal
Applications > Accessories > Terminal
Install Grub Customizer
Code:
sudo add-apt-repository ppa:danielrichter2007/grub-customizer
sudo apt-get update
sudo apt-get install grub-customizer


How would I do all of this without an internet source? Right now I am currently in discussion with some people in a couple of threads, trying desperately to get some internet but I am having no luck thus far.

If your interested and could possibly have some insight on how to fix either issue:

[http://ubuntuforums.org/showthread.php?t=885847&page=101](http://ubuntuforums.org/showthread.php?t=885847&page=101)

[http://ubuntuforums.org/showthread.php?t=1729941](http://ubuntuforums.org/showthread.php?t=1729941)

I tried to download the GRUB customizer from another source and then USB it over to the computer, but it says:

> 
To compile this you have to install libgtkmm-2.4-dev, cmake and cmake

Then run:
                cmake   .
                make
                sudo make install


I really do appreciate all your help Rubi, thank you so much! :D

---

### Post by Rubi1200 on 2011-04-19
I took a quick look at those threads, but unfortunately I have nothing to add as it seems the users there are doing the best they can to help.

I would put the Grub Customizer thing on hold until you get the connectivity issues sorted out.

Sorry I can't be of more help on that score :-(

---

### Post by chrisjabroni on 2011-04-19
No worries!

With my experiences thus far I'm sure once i get the connectivity issue resolved i'll be back with questions with this grub customizer :P

You are very knowledgable Rubi, thank you for your help! :)

---

