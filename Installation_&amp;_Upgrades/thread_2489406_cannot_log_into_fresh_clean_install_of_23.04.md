---
title: "cannot log into fresh clean install of 23.04"
date: 2023-07-29
forum: Installation &amp; Upgrades
---

### Post by dwater on 2023-07-29
I did an incremental upgrade, but it went wrong. I was able to log in so I did complete backups/etc/etc, then used links to download an iso, flashed it to a usb flash drive, and installed a clean version of 23.04.
Unfortunately, while the installation seemed to go well, I have not been able to log in.

I tried lots of combinations of my password, but none worked, so I figured I had made a typo (twice) and/or there was a keyboard layout issue (UK keyboard); so I went ahead and did another clean install and double checked the password and it all looked fine, and I selected the 'auto login' option so I would at least be able to use the system. After rebooting, I tried to 'su - davidmaxwaterman' and again it would not recognise my password. I tried on a console too, with the same results.

/var/log/auth.log shows lines like this:
```
pam_unix(passwd:chauthtok): authentication failure; logname= uid=1000 euid=0 tty= ruser= rhost=  user=davidmaxwaterman
su[4986]: FAILED SU (to davidmaxwaterman) davidmaxwaterman on pts/
```

My password is a combination of upper and lower case letters, plus numbers and special characters. One character is different from the US and UK layouts, but I tried plugging in a US keyboard and it still didn't work...and I tried typing it as plain text and it looked as I would expect.

Does anyone know what might be the problem?

---

### Post by MAFoElffen on 2023-07-29
Get to the initial Grub2 menu on boot > Advanced Options > Select any entry that has "Rescue mode" > When it gets to the rescue menu, select "network", to mount the filesystem in rw mode. Then select "root" to drop to a root prompt.
```

passwd davidmaxwaterman

```
Enter and confirm your new password.

Type exit<Enter>. At the rescue menu select continue...

---

### Post by dwater on 2023-07-29
Thanks for responding so quickly.

[EDIT: I found the 'shift' method to get the grub menu]

Yes, that worked...so, what went wrong with setting the password during the installation?

---

### Post by MAFoElffen on 2023-07-29
Not sure in your instance. But I have typo'ed that a few times, in the thousands of installs I have done for customers in 13 years... "I" am not immune. LOL

---

### Post by dwater on 2023-07-31
Well, I used virtualbox to try yet again, and indeed it still fails. I think this is a bug in the installation s/w. i wonder how to proceed to bring it to someone's attention?

---

