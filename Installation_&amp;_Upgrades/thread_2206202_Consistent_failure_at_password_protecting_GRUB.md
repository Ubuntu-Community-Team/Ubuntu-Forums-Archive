---
title: "Consistent failure at password protecting GRUB"
date: 2014-02-17
forum: Installation &amp; Upgrades
---

### Post by ben54 on 2014-02-17
OK, so I've tried several times to password protect GRUB. I've used the guide found here ([http://www.howtogeek.com/102009/how-to-password-protect-ubuntus-boot-loader/](http://www.howtogeek.com/102009/how-to-password-protect-ubuntus-boot-loader/)). The last time around, I even made a username with a cleartext account just to see if the hash was causing a problem, but no matter what I try,I get error messages. The most recent one that I get upon starting up says "error: SecureBoot forbids loading module from (dh0,gpt2)/grub/x86-64-efi/password.mod". After I correctly enter my username and password, it always prevents me from logging in.

---

### Post by deadflowr on 2014-02-17
That guide seems to be missing some crucial steps.
This is probably better
[https://help.ubuntu.com/community/Grub2/Passwords](https://help.ubuntu.com/community/Grub2/Passwords)

My own advice would be to try adding an entry for something like the recovery mode first, then try expanding it to other menuentries.

---

### Post by ben54 on 2014-02-17
Thanks for your reply. :-) I just finished following those instructions to the letter (or at least I think I did.) I saved everything, restarted, and as soon as it booted up, I saw "error: not an assignment." I entered my name and password, and received "error: access denied."

---

### Post by deadflowr on 2014-02-17
Did you update grub?
ala
```
sudo update-grub
```
Nothing in grub changes until this is run.

Edit: If you have run update-grub and the problems still arises, would you please post the out for the files you edited.
00_header and 10_linux and 39_os-prober and any others if you have edited them as well.
[USE CODE TAGS]("http://ubuntuforums.org/showthread.php?t=2171721") , please.

Also, if you want to edit out the password stuff, that's fine, as long as the rest is there as is.

---

