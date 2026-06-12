---
title: "Updating Error, couldn't intialize pkg info"
date: 2011-04-15
forum: Installation &amp; Upgrades
---

### Post by firefish5000 on 2011-04-15
Whenever I try to run update manager I get the following message after it gets 1/3rd of the way through reading the package list(about 3 to 5 seconds after update manager pops up). And everything after the first 'E:' appears when I use apt-get <install,update, ...>, dpkg 

Could not initialize the package information

An unresolvable problem occurred while initializing the package information.

Please report this bug against the 'update-manager' package and include the following error message:

'E:Encountered a section with no Package: header, E:Problem with MergeList /var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_natty-security_restricted_binary-amd64_Packages, E:The package lists or status file could not be parsed or opened.'

I dont believe i did anything to recently to have caused this. My ubuntu version is natty 11.04, I updated it last about 20 hrs ago(3:00 Am UTC, though i am not in that time range, 10:00 Pm for me... dont know my own time zone) I attempted to check for new updates 2hr ago (4:00 Pm in my time zone) and it gave me an error after 2 minutes of downloading package information, the apport thing popped up for me to report the bug... and a system error message (i can not recall what it stated but i recieve this every now and then, small message with two options for you to select.), i told it to send the bug report... Apport crashed, update manager crashed and dissapeared a message to restart apport appeared and went away imedeantly... and i have been recieving that error message above since then. I cannot seem update my package information now... I am a little lost. I am relativly new to ubuntu/linux and  have yet to find out how to do more than absolute basic commands for the terminal and following instruction on how to do ____ in the terminal. Please forgive me if I have provided mostly invaluable and irrelevant information.
I would also like to state that nothing appears in my software center i still get the basic screen that list the catagories but if i click of something such as sound and video it is a blank screen...

---

### Post by plucky on 2011-04-16
> 'E:Encountered a section with no Package: header, Problem with MergeList /var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_natty-security_restricted_binary-amd64_Packages, E:The package lists or status file could not be parsed or opened.'

Close Synaptic Package Manager,Update Manager etc,

Then

Open a terminal **(Applications > Accessories > Terminal)** and copy and paste these commands (one at a time) into it ```
sudo rm /var/lib/apt/lists/*
sudo apt-get update
sudo apt-get upgrade
```

The first line will complain about being unable to delete a directory "partial",but just ignore it.
The "update" line will download and re-create the list files again.
The last line will install any upgrades it finds.

Post back any errors encountered.

Good Luck

---

