---
title: "trying to update open office via terminal"
date: 2008-02-11
forum: Installation &amp; Upgrades
---

### Post by Meow27 on 2008-02-11
hi im using fiesty 7.04 on my old thinkpad and im attemtping to update my old version of OOo from 2.20 to 2.3.1

since synaptic only has 2.2 im wondering if there is a way to update OOo via terminal like you can with WINE

thanks
-meow

edit- i just realized this belongs to the wrong forum i apologies,

---

### Post by mikewhatever on 2008-02-11
Here you go --> [http://user.services.openoffice.org/en/forum/viewtopic.php?f=16&t=68](http://user.services.openoffice.org/en/forum/viewtopic.php?f=16&t=68).
Here's another --> [http://www.stchman.com/install_oo.html](http://www.stchman.com/install_oo.html)

Just googled them.

---

### Post by Meow27 on 2008-02-11
cant get the 1st one to work for the tar vszf one

and i dont trust the 2nd one :/

---

### Post by mikewhatever on 2008-02-11
> **Meow27 said:**
> cant get the 1st one to work for the tar vszf one

The command given is <tar -vxzf namefile.tar.gz> where namefile is the name of the file you've downloaded. It could be Open_Office_for_Ubuntu, or something else. It would also be enough to simply right click the tar.gz file and choose 'Extract here'.
Edit: The file name is OOo_2.3.1_LinuxIntel_install_wJRE_en-US.

> and i dont trust the 2nd one :/

Why? Is it because the background is black? You should google for it and pick the most trusted one.

---

### Post by Meow27 on 2008-02-12
not because of that. its cause i have to download an extra script that the dude made :/

---

### Post by mikewhatever on 2008-02-12
> **Meow27 said:**
> not because of that. its cause i have to download an extra script that the dude made :/

That was an option, but you did not have to do it, besides, you could open the script with your text editor and check it, or ask questions.
> [SIZE="1"][FONT="Fixedsys"][COLOR="SlateGray"][COLOR="DarkSlateGray"]#!/bin/sh

# This script will install/update Openoffice.org V2.3 on Ubuntu Edgy
# This script must be run as root with 755 permission
# This procedure was designed with Ubuntu Edgy but should work for Feisty
# Feisty already has OO2.2 installed by default
#
# Authored by Bob Nelson  [email]admin@stchman.com[/email]
#

script_name="OO_2_3_1_install.sh"

# Script must run as root 
if [ $USER != "root" ]; then
	echo "You need to run this script as root."
	echo "Use 'sudo ./$script_name' then enter your password when prompted."
	exit 1
fi

# First remove the old Openoffice.org V2.0 or V2.2
# This information was gotten from [http://www.psychocats.net](http://www.psychocats.net)
sudo apt-get -y remove openoffice.org openoffice.org-base openoffice.org-calc openoffice.org-common openoffice.org-core openoffice.org-draw openoffice.org-evolution openoffice.org-filter-mobiledev openoffice.org-gnome openoffice.org-gtk openoffice.org-help-en-us openoffice.org-impress openoffice.org-java-common openoffice.org-l10n-common openoffice.org-l10n-en-gb openoffice.org-l10n-en-za openoffice.org-math openoffice.org-style-human openoffice.org-writer

# remove any additional style themes the user may have installed
sudo apt-get -y remove openoffice.org-style-andromeda openoffice.org-style-crystal openoffice.org-style-default openoffice.org-style-hicontrast openoffice.org-style-human openoffice.org-style-industrial openoffice.org-style-tango

# After the old office has been removed we need to get the Openoffice 2.3.1 tar.gz file
# change to the users home folder
cd ~

# Get the tar.gz file from [www.stchman.com](www.stchman.com)
wget [http://www.stchman.com/tools/openoffice/OOo_2.3.1_LinuxIntel_install_en-US_deb.tar.gz](http://www.stchman.com/tools/openoffice/OOo_2.3.1_LinuxIntel_install_en-US_deb.tar.gz)

# Unpack the archive to the users /home directory
tar -vxzf ~/OOo_2.3.1_LinuxIntel_install_en-US_deb.tar.gz

# Install the packages
sudo dpkg -i ~/OOG680_m9_native_packed-1_en-US.9238/DEBS/*.deb

# Install the debian menus
sudo dpkg -i ~/OOG680_m9_native_packed-1_en-US.9238/DEBS/desktop-integration/*.deb

# Clean up
# remove the .tar.gz archive and the installation files as they are no longer needed
rm -f ~/OOo_2.3.1_LinuxIntel_install_en-US_deb.tar.gz

# Remove the entire directory and all sub-directories
rm -r -f ~/OOG680_m9_native_packed-1_en-US.9238

# Openoffice 2.3.1 installed!!!!![/COLOR][/COLOR][/FONT][/SIZE]

---

### Post by Meow27 on 2008-02-13
k. got it to work [didnt know thats what scripts were(used the commands the script gave)] learned something new :)

thanks for dealing with my idiocy :popcorn:

---

