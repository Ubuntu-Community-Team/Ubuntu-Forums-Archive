---
title: "Ubuntu can't boot properly after interrupted upgrade"
date: 2011-07-29
forum: Installation &amp; Upgrades
---

### Post by malapradej on 2011-07-29
HI,
I am running nutty and update manager has been asking me to run a  partial upgrade. This would not work through the GUI so I tried it  through the terminal (sudo apt-get upgrade). It was running fine until  it asked me to either install a new configuration file, keep the old, or  compare. Unfortunatley I can't remember which package it was for. I  tried to compare and it entered a text editor mode. I then tried to get  back to tell the system to keep the old but upon me using the Ctrl-Z  keystroke to exit the editor, it went back to the terminal prompt as if  the upgrade was aborted. I tried to run upgrade again but the system  said that it could not lock on a folder/file and that another process  may be running it. I then tried to reboot but it then hangs at the round  ubuntu symbol. I then tried to boot into the previous version (recovery  mode). I  tried to run the upgrade again but now it won't boot into  either recovery or normal mode. IT JUST HANGS...
Please help.....

More info:

After booting into the "restore" version (as the normal version  hanged), I opted to boot into the command line mode and used "sudo  apt-get upgrade" to continue the upgrade. This is all I know how to  continue, even the man pages did not seem to have a command to continue  an interrupted upgrade. When the upgrade appeared to finish, and I was  back at the command prompt I typed reboot to try and get back to the  normal mode. This where everything hangs.
 The following is an extract of the text:

*Checking file systems...
*File system check failed.
A log is being saved in /var/log/fsck/chkfs if that location is writable.
Please repair the file system manually.
*A maintenance shell will now be started.
Ctrl-D will terminate the shell and resume boot.
Give root password for maintenance:


 On typing the 1st character it comes up with:

Login incorrect. It seems to do this with any character even the Ctrl-D.


 When I boot into recovery mode the boot sequence ends with:

Begin: Running /scripts/local-bottom... done.
done.
Begin: Running /scripts/init-bottom... done.
init: unreadahead main process (245) terminated with status 5.


 All I can do in both is reboot.

---

