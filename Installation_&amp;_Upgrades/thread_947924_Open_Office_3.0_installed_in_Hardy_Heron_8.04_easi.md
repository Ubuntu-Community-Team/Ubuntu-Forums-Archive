---
title: "Open Office 3.0 installed in Hardy Heron 8.04 easily"
date: 2008-10-14
forum: Installation &amp; Upgrades
---

### Post by 73ckn797 on 2008-10-14
I have installed OO 3.0 on my desk and laptops with Hardy and Intrepid. Everything was effortless and is running great.

I completely removed all OO related installs through Synaptic.

Went to [http://download.openoffice.org/other.html#en-US](http://download.openoffice.org/other.html#en-US) 

Selected the English (in my case) version: OOo_3.0.0_LinuxIntel_install_en-US_deb.tar.gz

Downloaded the file (OOo_3.0.0_LinuxIntel_install_en-US_deb.tar.gz) from Openoffice.org

Created a directory in /home/name/whatever. 
edit: name = your name (directory created during Ubuntu installation) (whatever = Oo30 (that is what I named it) There is actually another sub-directory created so you could just extract to your home folder or even to the desktop. Once installation is completed you can delete the folder. With in that folder will be a DEBS and desktop-integration sub-directories.

Extracted files using File Roller (default Gnome compression utility) to the created directory. Double click on file downloaded will open in File Roller.

Went to terminal and "cd" to new directory (example: /home/name/OO3/DEBS)  then entered "sudo dpkg -i *.deb" The "DEBS" sub-directory is created when extracting. This installs the program.

Then changed to the other sub-directory created during extract (~/DEBS/desktop-integration) and repeated command "sudo dpkg -i *.deb". This creates the menu choices.

Started OO 3.0 and it works like a charm for me.

The desktop icon created using menu right click was read only but right click, properties allows changing that so I could rename the shortcut icon if you do not like the default short-cut name.

---

### Post by spawn. on 2008-10-15
Downloading...

---

### Post by CharonM72 on 2008-10-15
Note I had to log out and back in for this to work.
Also, uninstalling OpenOffice 2.4 seems to have uninstalled a lot of my language support. So far it seems that the only way to get multiple language support in OpenOffice 3 is to download the ones you want from the site and install their language packages. I'm doing that right now to make sure it works...
Installing OpenOffice language packs off Synaptic will uninstall OpenOffice 3 and reinstall 2.4.

---

### Post by elav on 2008-10-16
hi, I'm still a day and half Ubuntu user. I've installed Hardy x64, uninstalled Open Office 2 but failed to install Open Office 3.
My problem, I can not go into the folder where I extracted the OO 3. is it cd ..<path\folder>, cd ~<path\folder>, can enlighten me on this. I tried to find places where I can download the console commands but also failed.

---

### Post by GCG199 on 2008-10-17
I found a tutorial that had commands listed for upgrading to OpenOffice 3.0. 

Here are some links:

[http://openofficedocs.wordpress.com/2008/10/14/install-openoffice-30-on-ubuntu/](http://openofficedocs.wordpress.com/2008/10/14/install-openoffice-30-on-ubuntu/)

[http://www.tectonic.co.za/?p=3363](http://www.tectonic.co.za/?p=3363)

[http://howtoforge.org/how-to-install-openoffice-3.0.0-on-ubuntu-8.04](http://howtoforge.org/how-to-install-openoffice-3.0.0-on-ubuntu-8.04)

---

### Post by quanumphaze on 2008-10-17
> **elav said:**
> hi, I'm still a day and half Ubuntu user. I've installed Hardy x64, uninstalled Open Office 2 but failed to install Open Office 3.
My problem, I can not go into the folder where I extracted the OO 3. is it cd ..<path\folder>, cd ~<path\folder>, can enlighten me on this. I tried to find places where I can download the console commands but also failed.

I recommend you read this free e-book: "[Introduction To Linux: A Beginner's Guide]("http://www.linux-books.us/linux_general_0003.php")" by Machtelt Garrels. It will help with the basics of moving around in the terminal.

Just to let you know now that a ".." at the start of the path means "go back one folder".
The "~" means "my home directory" (/home/yourusername).
A single "." means the current directory and is mostly used when running a program in the current directory.
Absolute paths start with / and always go from the very start of the filesystem instead of from the current directory.

Examples:
You are in /home/user/Documents/work and want to go into /home/user/Documents/fun
[LIST]
[*]cd ../fun
[*]cd ~/Documents/fun
[*]cd /home/user/Documents/fun
[/LIST]

---

### Post by March Felloworthy on 2008-10-17
Another trap for the unwary: Make sure to download the Linux DEB version specified by the original poster! I somehow managed to get the Linux RPM one - I don't know whether there's a way to actually get it going (I assume there is) but as it's not the one specified in the above instructions I'm using another 150MB downloading the DEB one now!

---

### Post by quanumphaze on 2008-10-17
> **March Felloworthy said:**
> I'm using another 150MB downloading the DEB one now!

I hope you're not with Telstra :p

In order to install the Debian menu/Desktop integration deb you have to remove OOo2.  [This is a good guide]("http://tombuntu.com/index.php/2008/10/14/install-openofficeorg-30-in-ubuntu-804-and-810/")

I found a thread about getting Nautilus to show ODF thumbnails for those interested. Works with OOo3, just change all 2's to 3.
[http://ubuntuforums.org/showthread.php?t=76566](http://ubuntuforums.org/showthread.php?t=76566)

---

### Post by crjackson on 2008-10-17
Please ignore. Posted in error.

---

### Post by March Felloworthy on 2008-10-17
> **quanumphaze said:**
> I hope you're not with Telstra :p

In order to install the Debian menu/Desktop integration deb you have to remove OOo2.  [This is a good guide]("http://tombuntu.com/index.php/2008/10/14/install-openofficeorg-30-in-ubuntu-804-and-810/")

I found a thread about getting Nautilus to show ODF thumbnails for those interested. Works with OOo3, just change all 2's to 3.
[http://ubuntuforums.org/showthread.php?t=76566](http://ubuntuforums.org/showthread.php?t=76566)

I am indeed with Telstra, Quanum! Thankfully, I habe a 12GB plan, which I hit the limit on for the first time last month. Thankfully, it was right at the end of the billing cycle so we only had to put up with a shaped connection for about a day.

And thanks for the guide; I've taken OO2.4 all the way off.

---

### Post by stinger30au on 2008-10-18
thanks for the info. for rmeove i went to applications -> add remove programs and searched on open office and removed everyhting i could. 

it would not remove open office draw


then i went to system->synaptic

and searched on open office and removed the open office core and it took care of the remainder packages

then install and presto... all working

thanks so much!


and incase your wondering the directory you extracted the files to can be deleted as oo3 gets installed to its own working directory

---

### Post by JazonEsti on 2008-10-19
Will 3.0 be available via Add/Remove or Adept? Thanks!

---

### Post by 73ckn797 on 2008-10-21
> **stinger30au said:**
> thanks for the info. for rmeove i went to applications -> add remove programs and searched on open office and removed everyhting i could. 

it would not remove open office draw


then i went to system->synaptic

and searched on open office and removed the open office core and it took care of the remainder packages

then install and presto... all working

thanks so much!


and incase your wondering the directory you extracted the files to can be deleted as oo3 gets installed to its own working directory

Thanks for the thanks! Yes the directory can be deleted. Not much different than Windows where it creates an installation directory on the desktop. Don't have Windows except in VirtualBox for only one reason; Java on one website I have to use.

---

### Post by lavadisco on 2008-11-07
I followed all of the instructions in the first post, and it appeared to install everything as expected. However, when I go to my applications menu, there is nothing there! Synaptic doesn't show Oo3 as being installed either. But if I try and run any of the debs individually, it tells me it's reinstalling them, as if they're already installed. What's going on?

---

### Post by Strog on 2008-11-29
This tut worked like a charm for me... Thanx man!

---

### Post by kitchenguy on 2008-12-25
Worked for me too.  Thanks man.

---

### Post by babloo75 on 2009-01-09
> **73ckn797 said:**
> I have installed OO 3.0 on my desk and laptops with Hardy and Intrepid. Everything was effortless and is running great.

I completely removed all OO related installs through Synaptic.

Went to [http://download.openoffice.org/other.html#en-US](http://download.openoffice.org/other.html#en-US) 

Selected the English (in my case) version: OOo_3.0.0_LinuxIntel_install_en-US_deb.tar.gz

Downloaded the file (OOo_3.0.0_LinuxIntel_install_en-US_deb.tar.gz) from Openoffice.org

Created a directory in /home/name/whatever. 
edit: name = your name (directory created during Ubuntu installation) (whatever = Oo30 (that is what I named it) There is actually another sub-directory created so you could just extract to your home folder or even to the desktop. Once installation is completed you can delete the folder. With in that folder will be a DEBS and desktop-integration sub-directories.

Extracted files using File Roller (default Gnome compression utility) to the created directory. Double click on file downloaded will open in File Roller.

Went to terminal and "cd" to new directory (example: /home/name/OO3/DEBS)  then entered "sudo dpkg -i *.deb" The "DEBS" sub-directory is created when extracting. This installs the program.

Then changed to the other sub-directory created during extract (~/DEBS/desktop-integration) and repeated command "sudo dpkg -i *.deb". This creates the menu choices.

Started OO 3.0 and it works like a charm for me.

The desktop icon created using menu right click was read only but right click, properties allows changing that so I could rename the shortcut icon if you do not like the default short-cut name.

can u explain a bit in descriptive manner how to do these steps...?

---

### Post by 73ckn797 on 2009-01-09
> **babloo75 said:**
> can u explain a bit in descriptive manner how to do these steps...?

I have since found an easier way to install Oo3.0.

Go to System/Administration/Software Sources/Third-Party Software/Add and paste this link in there: [http://ppa.launchpad.net/openoffice-pkgs/ubuntu](http://ppa.launchpad.net/openoffice-pkgs/ubuntu)

Then I went to System/Administration/Update Manager and ran that and Oo3 showed up as an update. 

That installs Oo3 via Synaptics. Worked perfectly for me. It also has the same Ubuntu flavor in the start-up window/pop-up. The other method is not specific to Ubuntu, if that matters.

If that does not work I will clarify my previous info as requested.

---

### Post by babloo75 on 2009-01-09
> **73ckn797 said:**
> I have since found an easier way to install Oo3.0.

Go to System/Administration/Software Sources/Third-Party Software/Add and paste this link in there: [http://ppa.launchpad.net/openoffice-pkgs/ubuntu](http://ppa.launchpad.net/openoffice-pkgs/ubuntu)

Then I went to System/Administration/Update Manager and ran that and Oo3 showed up as an update. 

That installs Oo3 via Synaptics. Worked perfectly for me. It also has the same Ubuntu flavor in the start-up window/pop-up. The other method is not specific to Ubuntu, if that matters.

If that does not work I will clarify my previous info as requested.

after copying and pasting the link, "add source" option remains in the "off" state

---

### Post by babloo75 on 2009-01-09
> **73ckn797 said:**
> I have since found an easier way to install Oo3.0.

Go to System/Administration/Software Sources/Third-Party Software/Add and paste this link in there: [http://ppa.launchpad.net/openoffice-pkgs/ubuntu](http://ppa.launchpad.net/openoffice-pkgs/ubuntu)

Then I went to System/Administration/Update Manager and ran that and Oo3 showed up as an update. 

That installs Oo3 via Synaptics. Worked perfectly for me. It also has the same Ubuntu flavor in the start-up window/pop-up. The other method is not specific to Ubuntu, if that matters.

If that does not work I will clarify my previous info as requested.

after copying and pasting the link, "add source" option remains in the "off" state. hence cannot proceed further....

sorry for double post

---

### Post by 73ckn797 on 2009-01-09
> **babloo75 said:**
> can u explain a bit in descriptive manner how to do these steps...?


What part(s) do you not understand and I will explain?

---

### Post by silvagroup on 2009-01-16
73ckn797 how will this affect the upgrdae process for hardy when one wnats to upgarde to the next lts version. Or will it be a mess to get it all working?
I would like to have OO3 but not willing to have to spend days fixing problems later now that I have a nice rubnnin system.

---

### Post by pcowley on 2009-01-21
> **babloo75 said:**
> after copying and pasting the link, "add source" option remains in the "off" state
You have to add deb and a space at the front and a space at the end followed by a distribution name i.e intrepid

So the whole thing looks like deb https........ intrepid Open Office Org 

Having said this, it did not show the latest Open Office packages to me nor any "update" messages, probably becasue I have a 64 bit system. Oh Well, it'll probably work for you if you have a 32 bit system.

Hope this helps
Cheers
Pete

---

### Post by mikemunsil on 2009-02-10
73ckn797, thank you for the instructions on the install. It worked like a charm.  Running Ubuntu 7.10 .

Mike

---

### Post by Petalpumkin on 2009-02-26
Hi i have followed the procedure stated which seems to have worked but i dont have anything in the applications menu, i have tried restarting but still nothing.

can anyone help with how i get the items in the applications menu

Regards
Mark

Have now sorted the problem, opened up the desktop-integration folder double clicked on the icon it contained and it then installed all now working.

---

### Post by silvagroup on 2009-02-26
Found a link that appears to make the installation of OO3 really simple [http://news.softpedia.com/news/How-To-Install-OpenOffice-org-3-0-in-Ubuntu-8-10-96449.shtml#add_review_form]("http://news.softpedia.com/news/How-To-Install-OpenOffice-org-3-0-in-Ubuntu-8-10-96449.shtml#add_review_form").
But be aware that it is a PPA so it may not be the best option.
A heck my OO2 works just fine I'll wait for the official Ubuntu repo version and avid any problems.

---

### Post by acton on 2009-02-26
Ubuntu 8.10 CD has OpenOffice 2.4. It is old. So it is better to downloa OpenOffice 3.0. 

The new version of Ubuntu will be released in less than two months, on April 23rd, and it will be dubbed Jaunty Jackalope. Then, everybody will have Open Office 3.0 easily.

---

### Post by TODDMAN on 2009-02-26
Thanks, silvagroup

---

