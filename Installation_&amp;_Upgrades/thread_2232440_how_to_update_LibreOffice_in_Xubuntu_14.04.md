---
title: "how to update LibreOffice in Xubuntu 14.04"
date: 2014-07-02
forum: Installation &amp; Upgrades
---

### Post by Steve_and_Becky on 2014-07-02
I hope I am posting this in the correct forum.  If I am not, please forgive me!

I have Xubuntu 14.04, which is the newest LTS version.  Libre Office has just come out with 4.2.5.  I have Libre Office 4.2.4 on my  computer.  I wanted to update to Libre Office 4.2.5, but I am having trouble doing that.  I tried updating through the ppa and through the sofware center.  The software center does not even recognize that there is a newer version of Libre Office.  I keep getting an error message when I use the software updater.    The message says to the effect that it "requires the installation of untrusted packages"  and asks me to choose ok.  I choose ok, and then it closes without updating or installing the newer Libre Office. I have even tried using the terminal. I used this command:  "sudo apt-get update && sudo apt-get -y upgrade" The error message I got there said to the effect that there were problems, and that -y was used without --force-yes. 

So, what kind of problems am I having?  What can I do to correct these problems?  Is there a way to update my LibreOffice from 4.2.4 to 4.2.5?  If so how?  I could use some suggestions.

Steven

---

### Post by Dennis N on 2014-07-02
The LibreOffice PPA would be the best way. Did you have some problem with using it? If you elaborate, perhaps someone will help. In the ppa now is version 4.2.5-rc2.

---

### Post by Adam_GUI on 2014-07-02
I'm on 12.04 on my main machine, but, this process shouldn't have changed any.
I'm running LibreOffice 4.2.5.2 from the LibreOffice website.

Software Centre got used in place of synaptic as a main line after a point.  I forget where.
So, this route may have you do stuff that could be a tad involved, but, not by much.

First, navigate to [http://www.libreoffice.org/download/libreoffice-fresh/#change]("http://www.libreoffice.org/download/libreoffice-fresh/#change")
and select the appropriate version for your installation.  You'll want deb files.  But, I don't know if you're running on an x86 or x64 platform.

Create a directory in your home folder.
/home/<user>/Programs/LibreOffice/

Download and unzip the *.tar.gz into that directory.  Be sure to also grab the help file install.

In software centre, you'll want to uninstall LibreOffice.
Completely uninstalling (May be called purging) the LibreOffice meta package should take care of everything.
Close Software Centre to release the apt lock.

Open a terminal emulator.
Change the Directory to your unzipped folders.

cd /home/<user>/Programs/LibreOffice/LibreOffice_4.2.5.2_Linux_x86-64_deb/DEBS/
sudo dpkg -i *.deb

Do the same for the help file.
cd /home/<user>/Programs/LibreOffice/LibreOffice_4.2.5.2_Linux_x86-64_deb_helppack_en-US/DEBS/
sudo dpkg -i *.deb

Things like theme files are still available in the software centre, and should work fine.

You should now find LibreOffice 4.2.5 in your Programs tree.

[ATTACH=CONFIG]254388[/ATTACH]

---

### Post by ajgreeny on 2014-07-02
You problem may be simply that there are several ppa repos for LO.
You do not need:-
[http://ppa.launchpad.net/libreoffice/libreoffice-4-0/ubuntu](http://ppa.launchpad.net/libreoffice/libreoffice-4-0/ubuntu)
or
[http://ppa.launchpad.net/libreoffice/libreoffice-4-1/ubuntu](http://ppa.launchpad.net/libreoffice/libreoffice-4-1/ubuntu)

but you do need:-
[http://ppa.launchpad.net/libreoffice/ppa/ubuntu](http://ppa.launchpad.net/libreoffice/ppa/ubuntu)
Which will give you LO-4.2.5.2

PS:
I am still using 12.04, but I imagine the same version will be available for 14.04
PPS:
Yes, LO 4.2.5.2 is available in that ppa; I have just updated my Virtual machine install of Trusty to see what happened.

---

