---
title: "update problem"
date: 2005-05-14
forum: Installation &amp; Upgrades
---

### Post by godders on 2005-05-14
I have recently installed 5.04 noticed up dates were available so clicked on button all went well but got this message after install

W: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/o/openoffice.org/openoffice.org-bin_1.1.3-8ubuntu2.3_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/o/openoffice.org/openoffice.org-bin_1.1.3-8ubuntu2.3_i386.deb)
  Bad header line


W: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/o/openoffice.org/openoffice.org-l10n-en_1.1.3-8ubuntu2.3_all.deb](http://security.ubuntu.com/ubuntu/pool/main/o/openoffice.org/openoffice.org-l10n-en_1.1.3-8ubuntu2.3_all.deb)
  Bad header line

Do I need to do anything

---

### Post by defkewl on 2005-05-14
Do you have internet connection?

Check you ipaddress settings. Or perhaps your internet connection is slow.

---

### Post by godders on 2005-05-14
I have broadband internet access, the update button at the top of the desktop stays red and it tells me I have two packages for download but I get the above error message every time I try

---

### Post by Xian on 2005-05-14
It is probably just a temporary "glitch"  with the ubuntu.com server.

If it persists you can try and remove the contents of your /var/cache/apt folder.
Then try to fetch the update again.

---

### Post by Luinar on 2005-05-14
I'm getting the same problem, with those same two files, so it would make sense if it was a server issue.

---

### Post by Xian on 2005-05-14
It will likely correct itself after the next server sync.
You could install openoffice.org2 if interested & remove that openoffice-1.1.3-8.

---

