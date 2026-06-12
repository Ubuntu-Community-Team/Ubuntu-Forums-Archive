---
title: "Default Keyring problems"
date: 2009-07-25
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by FatalChaos on 2009-07-25
Whenever I boot up ubuntu one makes me enter a password to unlock my default key ring. I've done some research on this, and it seems like there are only two ways to make this behavior go away is to either set the password as the same as your login password and manually log in or to edit the lib-pam config. 

Problem is, the lib-pam conifig edits i've found don't seem to work for karmic, and I installed karmic with auto login and can't seem to change it. I've tried editing /etc/gdm/custom.conf and setting auto login to false, but all that happens then is at the login screen the only option i have is to click autologin. Upon further inspection, the users and groups option under system -> administration doesn't let me change my password, which right now is set to nothing. When i try to change it and click okay, it acts like everything went through fine but when I go back to it it still shows me as having no longin password. 

Has anyone managed to solve this problem?

---

### Post by ajgreeny on 2009-07-25
In *System > Preferences > Encryption and keyring* try setting the password you set there to be blank, ie type in nothing to the box, just hit return.  There will be a warning, if I remember correctly, but at least it should let you do what you want, if it's the same as jaunty.

---

### Post by FatalChaos on 2009-07-25
That option is no longer in Karmic (there is a password and encryption program, seahorse, under applications -> accessories, but it doesn't contain the options needed to do this anymore.) 

Instead, i deleted my default.keyring file, which wiped the data on it but all I had stored on it was the ubuntu one stuff, which i just reinstalled to fix. Directions: [https://answers.launchpad.net/ubuntu/+source/gnome-keyring/+question/61775](https://answers.launchpad.net/ubuntu/+source/gnome-keyring/+question/61775)

---

