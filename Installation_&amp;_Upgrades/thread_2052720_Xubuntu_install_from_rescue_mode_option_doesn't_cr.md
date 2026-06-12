---
title: "Xubuntu install from rescue mode option doesn't create a user"
date: 2012-09-03
forum: Installation &amp; Upgrades
---

### Post by opus1 on 2012-09-03
I installed Ubuntu Lucid with LUKS encryption a couple of years ago using this link: [http://ubuntuforums.org/showthread.php?t=1205372&highlight=cryptsetup]("http://ubuntuforums.org/showthread.php?t=1205372&highlight=cryptsetup").  I am now trying to install Xubuntu Precise while preserving /home following the same tutorial (the "Reinstall Ubuntu 9.04, 9.10, 10.04 over existing encrypted LUKS/LVM partitions" section).

Following the steps completely, I found everything worked as expected except that the installation never asked me for a password or initiated a new user dialog. When the install was done, I couldn't log in (which was no surprise).  The troubling thing is, there was no root account either; I didn't enter a password for one.

Entering the rescue mode from CD again, I was able to open a terminal and create a user, but again, it was with no root privileges. Additionally, none of the desktop components appeared to be installed despite my having selected desktop installation.

I also noticed that the installer main menu (in rescue mode) doesn't even list gather user account information.

What I would like to know is: Is there anyway to install Xubuntu precise using the tutorial listed above and preserve my /home directory data?  This rescue option seems pretty useless if one can't define the system users or root password.

I know I can reinstall from scratch, but the whole reason I went to having a separate home directory was so that I wouldn't have to copy 1 TB of data from backup everytime I upgrade.

Any help would be appreciated. I'll be happy to clarify anything if it's not already clear.

Thanks.

---

### Post by opus1 on 2012-09-07
**** BUMP ****

Any Ideas?

Should I file this as a bug?

---

### Post by opus1 on 2012-09-09
The solution to the problem of not having a desktop install was simple: I found that when there are multiple choice options, you use the arrow up and arrow down keys to move a red marker in the selection boxes. This is just a highlighter and you have to hit the space bar to actually make your selection (indicated by an asterisk). I did not do this when the install asked if I wanted a file server install, desktop install, etc. etc., and so the installation proceeded without a selection, which apparently is a bare-bones install.  This seems really silly to me; I think it should be set up so that there is always a selection instead of the possiblity of being left blank.  As it is, it can be confusing.

The solution to the problem of not having user accounts created was equally as simple, but in my mind completely unnecessary. I just had to throw some terminal Linux-fu at it, I was hoping to find a solution that fit with the tutorial (i.e., performed from within the install script). Here are the steps (assuming you have an encrypted disk with LVM after following the tutorial noted in the OP):

1. Boot from the Alternate Installer CD again (not desktop Installer)
2. Language: English
3. Main Menu: Rescue a broken system
4. Choose language: English
5. Choose a country: United States
6. Detect keyboard layout: No
7. Origin of the keyboard: USA
8. Keyboard layout: USA
9. Hostname: ubuntu (or whatever)
10. Time Zone: Eastern (or whatever)
11. Passphrase for /dev/sda5: [YOUR PASSPHRASE HERE]
12. Device to use as root file system: /dev/vg1/lvroot
13. Rescue operations: Execute a shell in /dev/vg1/lvroot
14. Select: Continue
15. Enter the following commands (running as root and assuming the user's name is "bob"):
    a. [I moved my old user directory because I didn't know if adding a new user would clobber it] ```
mv /home/bob /home/bob.old
```
    b. ```
passwd
``` (Follow the resulting prompts. This allows you to change the root password &#8212; so now you can actually log into the new xubuntu installation!)
    c.    ```
useradd -c "Bob Smith" bob
```
    d.    ```
passwd bob
``` 

The first time I tried to log in as "bob", it failed, kicking me back to the log in screen. Logging in as root, I was able to see that the new user home directory was owned by root. 

I changed the owner 
```
chown user:user /home/user 
```
After that I was able to log in successfully.  Then I just copied data from "bob.old" to "bob".

---

