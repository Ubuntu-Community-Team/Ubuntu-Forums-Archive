---
title: "Install Multiple Programs Using Shell Scripts"
date: 2010-12-06
forum: Installation &amp; Upgrades
---

### Post by WolfgangCS on 2010-12-06
I am trying to create a shell script to do a multitude of things. I would like this script to be open source and perfect for any clean installation of Ubuntu.

Objectives:
-Show visual Prompts for the $user to continue the the beginning stages of installations

-Keep a single terminal up to show details of the whole process

-Install Chrome and Dropbox

-Update System (without restarting, or restart and continue where script left off)

-Show website of in Chrome example: [Welcome]("http://www.wolfgangcomputer.com/projects/wolfgang-university/computer-installations/ubuntu-installation")

```
#!/bin/bash

$sudo gnome-terminal -x $sudo apt-get update

#SLEEP or another command to wait till completion of task

#Prompt User to continue with next step "Y/n"

#If needing to restart, continue script after reboot

#Re-run Update if needed
$sudo gnome-terminal -x $sudo apt-get update

#Then install Google Chrome

$sudo gnome-terminal -x $sudo wget http://www.google.com/chrome/eula.html?platform=linux_ubuntu_i386

#Update Chrome

$sudo gnome-terminal -x $sudo apt-get update google-chrome

#Prompt $User if they would like to continue, "We are going to Update your system one more time, OK? (Y/n)"

#Re-run Update if needed
$sudo gnome-terminal -x $sudo apt-get update

#Show Specified Website
$sudo google-chrome http://www.wolfgangcomputer.com/projects/wolfgang-university/computer-installations/ubuntu-installation

#Prompt $user: "$user, Update was successful, Are you ready to continue? (Y/n)"

sudo apt-get upgrade nautilus-dropbox

#Prompt $user: "$user, once you have completed and login/created account with dropbox, are you ready to continue? (Y/n)

echo "Welcome to Ubuntu! Please Close this Window"


```

Any ideas or things to change would be great!

---

### Post by WolfgangCS on 2010-12-06
I have moved this thread to 
[http://ubuntuforums.org/showthread.php?p=10207445#post10207445]("http://ubuntuforums.org/showthread.php?p=10207445#post10207445")

Thanks

---

