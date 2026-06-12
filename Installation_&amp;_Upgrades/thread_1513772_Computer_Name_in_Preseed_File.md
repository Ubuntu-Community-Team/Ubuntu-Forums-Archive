---
title: "Computer Name in Preseed File"
date: 2010-06-20
forum: Installation &amp; Upgrades
---

### Post by ncwilde43 on 2010-06-20
I've successfully created an unattended install using a preseed file, but I can't seem to set the 'computer name' for the new install.

The default computer names comes out as 'ubuntu'

[FONT="Courier New"]username@ubuntu:~$[/FONT]

Is there a d-i option that needs to be set in order to change this?

From: [https://help.ubuntu.com/10.04/installation-guide/i386/preseed-contents.html](https://help.ubuntu.com/10.04/installation-guide/i386/preseed-contents.html)
```
# Skip creation of a root account (normal user account will be able to
# use sudo). The default is false; preseed this to true if you want to set
# a root password.
#d-i passwd/root-login boolean false
# Alternatively, to skip creation of a normal user account.
#d-i passwd/make-user boolean false

# Root password, either in clear text
#d-i passwd/root-password password r00tme
#d-i passwd/root-password-again password r00tme
# or encrypted using an MD5 hash.
#d-i passwd/root-password-crypted password [MD5 hash]

# To create a normal user account.
#d-i passwd/user-fullname string Ubuntu User
#d-i passwd/username string ubuntu
# Normal user's password, either in clear text
#d-i passwd/user-password password insecure
#d-i passwd/user-password-again password insecure
# or encrypted using an MD5 hash.
#d-i passwd/user-password-crypted password [MD5 hash]
# Create the first user with the specified UID instead of the default.
#d-i passwd/user-uid string 1010
# The installer will warn about weak passwords. If you are sure you know
# what you're doing and want to override it, uncomment this.
#d-i user-setup/allow-password-weak boolean true

# The user account will be added to some standard initial groups. To
# override that, use this.
#d-i passwd/user-default-groups string audio cdrom video

# Set to true if you want to encrypt the first user's home directory.
d-i user-setup/encrypt-home boolean false
```

---

