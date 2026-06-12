---
title: "Ubuntu 24.04 doesn’t launch installation anymore"
date: 2024-05-31
forum: Installation &amp; Upgrades
---

### Post by tom1242 on 2024-05-31
Hello, I tried to install Ubuntu on my computer, but when it was near finish installing it got an unknown error and when I tried to reboot the installation it say “[COLOR=#353C41][FONT=Inter]could[/FONT][/COLOR][COLOR=#353C41][FONT=Inter] not create MokListRT: volume full could not create M[/FONT][/COLOR][COLOR=#353C41][FONT=Inter]okListXRT: volume full could not create MokListTrustedRT: volume full Something has gone seriously wrong: import_mok_state() failed: Volume full” I do not know anything about Linux or where to get help, I am sorry if this is not the right place for this.[/FONT][/COLOR]

---

### Post by tea for one on 2024-05-31
Access your UEFI settings
Disable Secure Boot
Disable TPM (and other similar-named security settings)
Boot into a "Try Ubuntu" liive session and try to install again

---

### Post by tom1242 on 2024-05-31
Ok, thanks, that work

---

### Post by tea for one on 2024-05-31
Splendid, don't forget to mark the thread as solved - very helpful for other users/searchers.
[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

---

### Post by alextkirk on 2024-07-08
Hi there... I have the same problem showing this same message but that happens when I try to install ubuntu 24.04 within windows 10. I have a bootable pendrive which I used Ventoy, Rufus and Balena to make and none of them helped me. Everytime I insert the pendrive, make the necessary changes on the bios, and start the re-boot, the same message shows up and the laptpo turns off.... Can anyone help me through this?

---

