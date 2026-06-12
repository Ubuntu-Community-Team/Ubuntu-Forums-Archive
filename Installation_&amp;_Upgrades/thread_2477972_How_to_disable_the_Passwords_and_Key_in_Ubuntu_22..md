---
title: "How to disable the Passwords and Key in Ubuntu 22.04.1 LTS"
date: 2022-08-13
forum: Installation &amp; Upgrades
---

### Post by ubontik22 on 2022-08-13
Hello, 

I installed the 22.04 and get the message below. How I can get rid off one, how to disable Passwords and Keys. When I install Skype (snap) I get a blank screen instead of a list of contacts.

[IMG]https://ubuntuforums.org/attachment.php?attachmentid=290855&stc=1[/IMG]

Thank you for your suggestions.

---

### Post by QIII on 2022-08-13
Would you please post the command(s) you issued.

Rather than posting an image, please cut at paste all terminal commands and output in code tags.

```
man apt-key
``` returns the following in its text:

```
       update (deprecated)
           Update the local keyring with the archive keyring and remove from the local keyring the archive keys which are no longer valid. The archive keyring is shipped in the archive-keyring package of your distribution, e.g. the
           ubuntu-keyring package in Ubuntu.

           Note that a distribution does not need to and in fact should not use this command any longer and instead ship keyring files in the /etc/apt/trusted.gpg.d/ directory directly as this avoids a dependency on gnupg and it is
           easier to manage keys by simply adding and removing files for maintainers and users alike.


```

---

### Post by deadflowr on 2022-08-13
The message has nothing to do with Passwords and Keys, since Passwords and Keys deals with user passwords and keys,
and not with system passwords and keys such as apt keys.

The message actually comes from Ubuntu Software.

As for fixing the warning you can try this
[https://www.omgubuntu.co.uk/2022/06/fix-apt-key-deprecation-error-on-ubuntu]("https://www.omgubuntu.co.uk/2022/06/fix-apt-key-deprecation-error-on-ubuntu")

---

### Post by ubontik22 on 2022-08-17
Yes, this is what I meant. This is Ubuntu software issue. I'll try to fix but before I need to back up the data.

---

