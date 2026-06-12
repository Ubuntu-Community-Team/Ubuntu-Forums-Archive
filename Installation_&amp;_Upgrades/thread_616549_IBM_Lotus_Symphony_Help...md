---
title: "IBM Lotus Symphony Help.."
date: 2007-11-18
forum: Installation &amp; Upgrades
---

### Post by Scorpio123 on 2007-11-18
Hi there, im trying to install IBM Lotus Symphony on Ubuntu 7.10 Gutsy, but i can't seem to manage to complete the second step...

I'm using the following guide: [http://www.howtoforge.com/ibm_lotus_symphony_ubuntu_7.04](http://www.howtoforge.com/ibm_lotus_symphony_ubuntu_7.04)

With the 7.10 Step 3 fix from here: [http://symphony.lotus.com/software/lotus/symphony/thread.jspa?threadID=3415](http://symphony.lotus.com/software/lotus/symphony/thread.jspa?threadID=3415)

As you can see, Step 2 is:

chmod +x IBM_Lotus_Symphony_Linux.bin
./IBM_Lotus_Symphony_Linux.bin
cd IBM_Lotus_Symphony_Linux/
sudo ./setup.bin

After i type out "./IBM_Lotus_Symphony_Linux.bin" It begins to extract bundle etc. and launch the install shield. But then the following error pops up in terminal:

"The install is unable to run in graphical mode. Try running the installer with the -console or -silent flag"

I have no idea what to do, i have turned of Compiz etc. Im a first time ubuntu user, so im not familiar with command line.. Please help! Thanks!!

---

### Post by bearrider on 2007-11-19
This is because you don't have Sun JRE/JDk installed. This is required.

1. Uninstall by going to  /opt/ibm/lotus/Symphony/_uninst/ and run uninstaller.bin

2. Install JRE using : sudo apt-get install sun-java6-jre sun-java6-plugin

3. Test your install with java -version. This should show you the sun java info, not the gij info.

4. reinstall  IBM Lotus Symphony with
        chmod +x IBM_Lotus_Symphony_Linux.bin
        ./IBM_Lotus_Symphony_Linux.bin
        cd IBM_Lotus_Symphony_Linux/
        sudo ./setup.bin


If all went well, you'll get the installer GUI

---

### Post by guhpraset on 2008-01-31
it give me this:

engine is missing (/root/InstallShield/Universal/ibm/Symphony/Gen2): run installation from source media

what should i do?

---

