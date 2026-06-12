---
title: "installing lightscribe"
date: 2008-08-18
forum: Installation &amp; Upgrades
---

### Post by crashingsucks9 on 2008-08-18
alright so i am trying to install lightscribe but i am really new at all of this so i need help with a few steps so if someone could help that would be awesome here is what it is telling me to do... i defiantly don't know what to do for step 2 thats what my main trouble was everything else seemed not too bad


   1. Administrator or SuperUser account access and passwords are required for the rpm package installations.

   2. This package (Lightscribe System Software lightscribe.rpm) must be installed before your LightScribe labeling applications to maintain the necessary dependencies.

   3. Save any work in progress and close down all active programs, especially any labeling applications.
   4. Click on above file download link.
   5. After reading and acknowledging the licensing agreement, choose “Save” or “Download” to start the file download process.

      Depending on your internet connection speed, the update file may take a few minutes to download, so please be patient.

   6. The exact installation steps will be different depending on your Linux installation. Below are example procedures using the command line or a graphical user interface (KDE GUI).

      Command Line

         1. Activate your terminal program.
         2. Locate the downloaded rpm file and “cd” into the same directory.
         3. You’ll need to use the “su” command to log on as the Super User using your root password.
         4. Here are the related commands to use:

            Log on as Super User with your root password:
            Su
            <type your root password>

            Verify your user status:
            id

            Install the package on a clean system:
            rpm -i <filename.rpm>

            Uninstall:
            rpm -e <filename.rpm>

            Upgrade from older version to new one:
            rpm -Uvh <filename.rpm>

            List currently installed LightScribe packages (packages with names starting with Lightscribe):
            rpm -qa | grep lightscribe

            <filename.rpm> = name of downloaded or installed rpm file.

         5. Remember to log out of Super User by typing “exit” when done.

      GUI (KDE)

         1. You may close any browser download screen when the download process is complete.
         2. The selected .rpm file will most likely be downloaded onto your “home” directory.
         3. Locate and double click the .rpm file to install using your default software installer. You may also right click the .rpm file, then choose "Open with Install Software".
         4. Enter the Administrator password when prompted if you’re not logged in as an Administrator.

---

### Post by Partyboi2 on 2008-08-18
ubuntu is debian based, so you will need to install the deb package not the rpm package. Rpm's are used for some other distro's like readhat etc...
Once you have downloaded the deb package you can double click on it to start the install process. (easiest way) If you want to do it from command line follow the steps below.

> [DEB Package Instructions]("http://lightscribe.com/#")
[LIST=1]
[*]**Administrator or SuperUser account access and passwords are required for the deb package installations.**
[*][B]This package MUST be installed BEFORE your LightScribe labeling applications to maintain the necessary dependencies.

[/B]
[LIST=1]
[*]Save any work in progress and close down all active programs, especially any labeling applications.
[*]The exact installation steps will be different depending on your Linux distribution. Below are example procedures using the command line or a graphical user interface.

**Command Line**
[LIST=1]
[*]Activate your terminal program.
[*]Locate the downloaded installation file and &#8220;cd&#8221; into the same directory. Typically, this is your "home" directory.
[*]You will need to have Administrator privileges by either logging in as "superuser" or use the "sudo" command. In either case, you will need to have your Admin password, and the following steps will use the "sudo" command.
[LIST=1]
[*]Type the following in your command line, inserting the downloaded filename

*sudo dpkg -i «filename»*
[*]Enter your Admin password when prompted
[*]To check the status of the installation, type the following command:

*dpkg -s lightscribe*
[/LIST]
 
[/LIST]
 **GUI (e.g. Gnome)**


[LIST=1]
[*]You may close any browser download screen when the download process is complete.
[*]Locate and double click the downloaded installation file to start the package installation using your default package installer. Files are typically downloaded to your "home" directory.
[*]Enter the Administrator password when prompted if you&#8217;re not logged in as an Administrator.
[/LIST]
 
[/LIST]
 
[/LIST]
 


---

