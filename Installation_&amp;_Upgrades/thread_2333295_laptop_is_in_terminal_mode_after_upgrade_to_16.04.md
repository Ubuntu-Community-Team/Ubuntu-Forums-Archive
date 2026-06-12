---
title: "laptop is in terminal mode after upgrade to 16.04"
date: 2016-08-08
forum: Installation &amp; Upgrades
---

### Post by HippieDave on 2016-08-08
When I upgraded my Thinkpad X220 all I got was a blank screen and some terminal language that was not very informative....everything seemed to be frozen.
I installed 14.04 off my thumb drive alongside 16.04, and 14.04 opens fine...albeit without any of my data files.  When I selected 16.04 off the boot menu, I just get a Terminal login/password prompt.  It recognizes my user name and password, but I have no clue what sudo commands to provide it to get a GUI and see if my new upgraded version can get up and running.   Any suggestions?

---

### Post by mastablasta on 2016-08-09
system specs?: [ ]("https://ubuntuforums.org/showthread.php?t=1422475")[SIZE=2][https://ubuntuforums.org/showthread.php?t=1422475](https://ubuntuforums.org/showthread.php?t=1422475)
[/SIZE]

i am sure the error message will says what is wrong. What kind of message is it? 

you can also access the files and logs from 14.04 partition or you can use live USB session to access the logs. check them to see where the errors are and post the last few entries at least here (dmesg, syslog, kernel.log...). : [https://help.ubuntu.com/community/LinuxLogFiles](https://help.ubuntu.com/community/LinuxLogFiles)


dmesg should tell you where the issue is. if you get to terminal in 16.04, you can also type *dmesg* there to see what went wrong.

---

