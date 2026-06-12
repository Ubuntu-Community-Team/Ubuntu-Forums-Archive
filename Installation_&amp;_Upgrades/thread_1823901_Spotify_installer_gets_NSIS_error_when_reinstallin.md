---
title: "Spotify installer gets NSIS error when reinstalling"
date: 2011-08-12
forum: Installation &amp; Upgrades
---

### Post by 8bitpalace on 2011-08-12
Hey!

I recently removed Spotify using the Wine remove software function. When I try to reinstall Spotify using the "Spotify Installer.exe" I just keep getting the famous "NSIS error" (without any error code, it's plain NSIS). When I try to run the "Spotify Installer.exe" through a terminal it gives me:
wine: cannot find L"unix\\home\\user\\Desktop\\Spotify Installer.exe"

Any help in this bloody mess is much appreciated since I can't (I hope no one can) live without music. 

I'm running Ubuntu Natty 11.04.

Regards,
8bitpalace

---

### Post by 8bitpalace on 2011-08-13
Solved.

Had to move the "Spotify Installer.exe" into the .wine folder inside my home folder and then run in from there.

---

