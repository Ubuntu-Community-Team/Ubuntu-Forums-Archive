---
title: "rtl8812AU_8821AU driver installation for Ubuntu 14.04"
date: 2016-01-29
forum: Installation &amp; Upgrades
---

### Post by ethan30 on 2016-01-29
there was previously a thread for this issue, but it was closed. My problem was not solved. I have a brand new installation of Ubuntu 14.04. i understand that it is not the most recent version but I assessed the two versions of ubuntu and decided that with my current processor strength the older version (14.04) was a better choice. After booting ubuntu I came to find that my wifi adapter is not compatible with Ubuntu on its own and that the drivers need to be compiled manually to use this wifi adapter.
I used the list of commands suggested:

lsusb                                              to locate and see the name of my wifi reciever.
uname -r                                         to view my kernel version.
Sudo modprobe 8812au                      I'm not sure what this was supposed to do.

using the "sudo" command forced me to give my user password to continue, and i gave it and it appeared to work at first, but it gave me a failure message saying there was an error with the module or something like that.
Turns out the errors were in that I didn't have the build-essential kit or the linux-headers-generic kit. I downloaded those to a usb and put them onto my desktop in ubuntu, along with the driver package for rtl8812au.
After doing all of this I tried again, getting the same error report and telling me to try using the commands "install --help", "make --help", "dpkg --help" and so on. I used all of these commands and even retried the original commands using the suggested syntax supplied by the help command output.
Again nothing worked towards my goal.

I have tried changing directories to the directory containing the program files for the driver for easiest reference while writing the commands and not having to write the file location as specifically into the commands.
Again, nothing is working.

I have tried all suggested actions supplied in this forum: [http://ubuntuforums.org/showthread.php?t=2240631](http://ubuntuforums.org/showthread.php?t=2240631) which has been closed and labeled as solved. The only option, which i am unfortunately able to use, that I have not used is to connect to an alternate source of internet and install the driver through github.

Ubuntu and the windows10 I am writing this from are on the same computer and I have no way of connecting it to a modem to use the internet bypass to compile and install the driver.

I also have found that I need the program dkms to compile. I cannot seem to find where to get this program from, but if it needs to be installed via internet, then I won't be able to do that and will need another method of installing this driver!

---

