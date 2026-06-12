---
title: "Preseeding Grub Password"
date: 2017-03-14
forum: Installation &amp; Upgrades
---

### Post by cdgg_cali on 2017-03-14
To generate an encrypted password, open a terminal and run the following command:
grub-mkpasswd-pbkdf2Hi,

I have been trying to secure grub using the preseed file.

On [https://help.ubuntu.com/lts/installation-guide/example-preseed.txt](https://help.ubuntu.com/lts/installation-guide/example-preseed.txt) you can see that it mentions this can be done using the line below, but based my testing looks like is not working.[INDENT]"[COLOR=#000000]d-i grub-installer/password-crypted password [MD5 hash]"
[/COLOR][/INDENT]
[COLOR=#000000]
Has anyone tried and make it work successfully?

The documentation points that you need to use '[/COLOR]grub-md5-crypt' but this is a GRUB Legacy commands, I'm using Trusty, so the default is GRUB2 and based on [https://help.ubuntu.com/community/Grub2/Passwords](https://help.ubuntu.com/community/Grub2/Passwords), looks like now, to generate an encrypted password you need to use the "grub-mkpasswd-pbkdf2" command. I haven't being able to find any documentation about a mix of grub-mkpasswd-pbkdf2 and the preseed file.


[COLOR=#000000]Regards,
Carlos[/COLOR]

---

