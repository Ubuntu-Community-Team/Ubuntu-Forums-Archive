---
title: "Error calling EVIOCSKEYCODE: Invalid argument"
date: 2014-10-27
forum: Installation &amp; Upgrades
---

### Post by 316479 on 2014-10-27
During boot on a 64-bit 14.04 LTS system I was getting several error messages

systemd-udevd[319]: Error calling EVIOCSKEYCODE: Invalid argument

The problem turned out to be invalid entries in  

/lib/udev/hwdb.d/60-keyboard.hwdb

for the keyboard on this system.

Clue:  number of error messages == number of entries.

Removing the entries for my keyboard eliminated the error messages.

---

### Post by Tanel_Tammik on 2015-02-04
Hi, which entries did you remove?

Dell E5420, 14.04

---

### Post by Robert_Blaschke on 2015-02-07
Hi I am an Ubuntu user with no knowledge of Linux code nor commands. I have the same problem, and I have read I should edit the file /lib/udev/hwdb.d/60-keyboard.hwdb . But system is only in maintenance shell and no gedit window is possible. I am completely lost and cannot get over that. Can anybody write here a sequence of commands I should type to get into Ubuntu?
I have Dell Latitude laptop with dual Win7/Ubuntu and now I write this from windows. Thanks in advance.

---

### Post by masroor2 on 2015-02-12
i too have the same problem and so far nothing is working, i don't know what the heck i am supposed to do with the hwbd file, please tell us how to configure the invalid entries and how to change it ,, as i'm a total beginner and n00b at this ubuntu thing. An early help will be so so so appreciated.


take some popcorn:popcorn:

---

### Post by Kai_Agapo on 2015-02-16
> **masroor2 said:**
> i too have the same problem and so far nothing is working, i don't know what the heck i am supposed to do with the hwbd file, please tell us how to configure the invalid entries and how to change it ,, as i'm a total beginner and n00b at this ubuntu thing. An early help will be so so so appreciated.


take some popcorn:popcorn:

########################################################################################################

Here is for the last two gents, but a quick disclaimer, as using my commands are considered a hold harmless contract between us: 

Meaning I will give you the best of what I know, but it is your fingers that type in the terminal window and your brain should make sure it is what you want to do and agree to not hold me liable for anything that goes wrong as a result of your typing or my commands.

Now that is out of the way and you say your new, so this assumes that is the case and so this is not meant to offend you, but assumes you need this amount of help, so don't get thy panties in a bunch :). Really meant only to help you.

Just a couple notes:
1. is that a Logitech keyboard and mouse causing your issue and they seem to for me and Linux.
2. Try another keyboard and mouse and it is likely to go away, but in case not, then carry on.
3. Second issue could be you have a laptop and instead of using the built in keyboard and mouse pad you have another keyboard and mouse plugged in and so the mapping of the second keyboard is choking after the first is mapped :) This is what I did anyway.

**[COLOR=#008080]Legend[/COLOR]**
# - Denotes an information line
[B][COLOR=#0000FF]Bold and blue is a command
[/COLOR][/B]^ - Is the control key
# There is a information line or more
#[COLOR=#0000ff]** Followed then the command line**[/COLOR]

Terminal commands entered after prompt:

# Lets set the debug up to see what's is really going on, but if you don't want to go that route and and just fix it, then bypass and get to the meat of the issue
################################################################################################################ 
# Sudo Command to write to the file and Nano is the editor, then path and file name
[COLOR=#0000ff][B]sudo nano /etc/udev/udev.conf

[/B][/COLOR]# prompt to enter the root password
[B][COLOR=#0000ff]Root password and Enter
[/COLOR][/B]
# This shows the position of the cursor [COLOR=#ff0000]**(Important Note!!!!!!!! This tells you where the issue is from the log error.)**[/COLOR][COLOR=#ff0000] (systemd-udevd[358]: - AKA line 358 is the keyboard that is having the isssue)[/COLOR][COLOR=#0000ff][B]
^C
[/B][/COLOR]
# use the arrow keys to highlight the #udev_log="info" and replace it with:
[COLOR=#0000ff][B]udev_log="debug"
[/B][/COLOR]
# This write the file back
[COLOR=#0000ff]**^O**[/COLOR]

# It will ask to overwrite the file, so just hit the enter key
[COLOR=#0000ff][B]Enter
[/B][/COLOR]
# Now exit the Nano editor
[COLOR=#0000ff]**^X**[/COLOR]

# Reboot
[COLOR=#0000ff][B]sudo reboot
[/B][/COLOR]
#########################################################################################################

Find and edit out the keyboards you don't want:
# Open the file from the first post and find and kill the keyboard entries, by putting a # in front of them 
[COLOR=#0000ff][B]sudo nano /lib/udev/hwdb.d/60-keyboard.hwdb
[/B][/COLOR]
# Prompt for root password and enter
**[COLOR=#0000FF]root password and enter[/COLOR]**

# Once it opens hit Control C and go to the line with the error (# 358 in my case) and Hit Control C again to change the position  displayed.
[COLOR=#0000ff]**^C**[/COLOR]

# You start off at position line 1 and go to line 358 and disable that keyboard 
[COLOR=#0000ff]**#** 
[/COLOR]
# Should look Like this when finished:[COLOR=#0000ff]
[/COLOR]# Slimstar 320
# keyboard:usb:v0458p0708d*dc*dsc*dp*ic*isc*ip*in01*
# KEYBOARD_KEY_0900f0=scrollup
# KEYBOARD_KEY_0900f1=scrolldown
# KEYBOARD_KEY_0900f3=back
# KEYBOARD_KEY_0900f2=forward
# KEYBOARD_KEY_0900f5=wordprocessor
# KEYBOARD_KEY_0900f6=spreadsheet
# KEYBOARD_KEY_0900f4=presentation
# KEYBOARD_KEY_0c0223=www
# KEYBOARD_KEY_0900f7=chat
# KEYBOARD_KEY_0900fb=prog1

# This write the file back
[COLOR=#0000ff]**^O**[/COLOR]

# It will ask to overwrite the file, so just hit the enter key
[COLOR=#0000ff][B]Enter
[/B][/COLOR]
# Now exit the Nano editor
[COLOR=#0000ff]**^X**[/COLOR]

# Reboot
[COLOR=#0000ff][B]sudo reboot

[/B][/COLOR]###################################################################################################

The other thing said in post 1 was number of errors equals the number of keyboard entries that need commented out with the #

So rinse and repeat the process above until the errors are gone. 

Welcome to Linux btw :) It really will change you and make you better. Not to mention make more money if you apply it to an IT career.

Caio,
Kai Agapo

---

### Post by timfinley on 2015-03-12
> **Kai_Agapo said:**
> ########################################################################################################

Here is for the last two gents, but a quick disclaimer, as using my commands are considered a hold harmless contract between us: 

Meaning I will give you the best of what I know, but it is your fingers that type in the terminal window and your brain should make sure it is what you want to do and agree to not hold me liable for anything that goes wrong as a result of your typing or my commands.

Now that is out of the way and you say your new, so this assumes that is the case and so this is not meant to offend you, but assumes you need this amount of help, so don't get thy panties in a bunch :). Really meant only to help you.

Just a couple notes:
1. is that a Logitech keyboard and mouse causing your issue and they seem to for me and Linux.
2. Try another keyboard and mouse and it is likely to go away, but in case not, then carry on.
3. Second issue could be you have a laptop and instead of using the built in keyboard and mouse pad you have another keyboard and mouse plugged in and so the mapping of the second keyboard is choking after the first is mapped :) This is what I did anyway.

**[COLOR=#008080]Legend[/COLOR]**
# - Denotes an information line
[B][COLOR=#0000FF]Bold and blue is a command
[/COLOR][/B]^ - Is the control key
# There is a information line or more
#[COLOR=#0000ff]** Followed then the command line**[/COLOR]

Terminal commands entered after prompt:

# Lets set the debug up to see what's is really going on, but if you don't want to go that route and and just fix it, then bypass and get to the meat of the issue
################################################################################################################ 
# Sudo Command to write to the file and Nano is the editor, then path and file name
[COLOR=#0000ff][B]sudo nano /etc/udev/udev.conf

[/B][/COLOR]# prompt to enter the root password
[B][COLOR=#0000ff]Root password and Enter
[/COLOR][/B]
# This shows the position of the cursor [COLOR=#ff0000]**(Important Note!!!!!!!! This tells you where the issue is from the log error.)**[/COLOR][COLOR=#ff0000] (systemd-udevd[358]: - AKA line 358 is the keyboard that is having the isssue)[/COLOR][COLOR=#0000ff][B]
^C
[/B][/COLOR]
# use the arrow keys to highlight the #udev_log="info" and replace it with:
[COLOR=#0000ff][B]udev_log="debug"
[/B][/COLOR]
# This write the file back
[COLOR=#0000ff]**^O**[/COLOR]

# It will ask to overwrite the file, so just hit the enter key
[COLOR=#0000ff][B]Enter
[/B][/COLOR]
# Now exit the Nano editor
[COLOR=#0000ff]**^X**[/COLOR]

# Reboot
[COLOR=#0000ff][B]sudo reboot
[/B][/COLOR]
#########################################################################################################

Find and edit out the keyboards you don't want:
# Open the file from the first post and find and kill the keyboard entries, by putting a # in front of them 
[COLOR=#0000ff][B]sudo nano /lib/udev/hwdb.d/60-keyboard.hwdb
[/B][/COLOR]
# Prompt for root password and enter
**[COLOR=#0000FF]root password and enter[/COLOR]**

# Once it opens hit Control C and go to the line with the error (# 358 in my case) and Hit Control C again to change the position  displayed.
[COLOR=#0000ff]**^C**[/COLOR]

# You start off at position line 1 and go to line 358 and disable that keyboard 
[COLOR=#0000ff]**#** 
[/COLOR]
# Should look Like this when finished:[COLOR=#0000ff]
[/COLOR]# Slimstar 320
# keyboard:usb:v0458p0708d*dc*dsc*dp*ic*isc*ip*in01*
# KEYBOARD_KEY_0900f0=scrollup
# KEYBOARD_KEY_0900f1=scrolldown
# KEYBOARD_KEY_0900f3=back
# KEYBOARD_KEY_0900f2=forward
# KEYBOARD_KEY_0900f5=wordprocessor
# KEYBOARD_KEY_0900f6=spreadsheet
# KEYBOARD_KEY_0900f4=presentation
# KEYBOARD_KEY_0c0223=www
# KEYBOARD_KEY_0900f7=chat
# KEYBOARD_KEY_0900fb=prog1

# This write the file back
[COLOR=#0000ff]**^O**[/COLOR]

# It will ask to overwrite the file, so just hit the enter key
[COLOR=#0000ff][B]Enter
[/B][/COLOR]
# Now exit the Nano editor
[COLOR=#0000ff]**^X**[/COLOR]

# Reboot
[COLOR=#0000ff][B]sudo reboot

[/B][/COLOR]###################################################################################################

The other thing said in post 1 was number of errors equals the number of keyboard entries that need commented out with the #

So rinse and repeat the process above until the errors are gone. 

Welcome to Linux btw :) It really will change you and make you better. Not to mention make more money if you apply it to an IT career.

Caio,
Kai Agapo

Hello. I'm having the same issue with an older Dell latitude D630. I followed these instructions and I no longer get the EVIOCSKEYCODE error during sthe boot process. But I'm still just cycling back to the ubuntu login screen after I enter the password for a user or try the guest account. 

I also tried this solution:

[http://ubuntuforums.org/showthread.php?t=1034762&page=2](http://ubuntuforums.org/showthread.php?t=1034762&page=2)

To no avail. When I attempt to login i press ctrl-alt-f1 and see an error like this one over and over again:

```

ata3.00: exception Emask 
[...]
ata3.00: [...] Emask 0x9 (media error)
ata3.00: status: {DRDY ERR}
ata3.00: error: {UNC}

```

I tried to be as verbose as possibl3, but typing on a touch screen isn't much fun. If you need any more information let me know. Thanks for the help.

---

