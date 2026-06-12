---
title: "Ubuntu Jammy (in WSL): adding armhf arch, can't find packages"
date: 2024-04-17
forum: Installation &amp; Upgrades
---

### Post by parduz on 2024-04-17
I'm trying to use WSL to cross-compile a c++ program for armhf on a Windows PC.
I've was able to do it on a Debian image some years ago, and now i need to do it again on a new PC. Since the powershell command **[COLOR=#000080][FONT=lucida console]wsl.exe --install[/FONT][/COLOR]** automagically installed Ubuntu Jammy, i'm fine at keeping it.


I've learned that armhf binaries are on the "ports" repository, so i added these lines to a **[FONT=lucida console]/etc/apt/sources.list.d/armrep.list[/FONT]** file:


```
deb [ arch=armhf ] http://ports.ubuntu.com/ jammy main restricted universe multiverse
deb [ arch=armhf ] http://ports.ubuntu.com/ jammy-updates main restricted universe multiverse
deb [ arch=armhf ] http://ports.ubuntu.com/ jammy-security main restricted universe multiverse
deb [ arch=armhf ] http://ports.ubuntu.com/ jammy-backports main restricted universe multiverse

```

Then I add the armhf architecture (**[COLOR=#000080][FONT=lucida console]sudo dpkg --add-architecture armhf[/FONT][/COLOR]**) but i get a many errors like these ones:
```

E: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/jammy/main/binary-armhf/Packages  404  Not Found [IP: 91.189.91.83 80]
E: Failed to fetch http://security.ubuntu.com/ubuntu/dists/jammy-security/main/binary-armhf/Packages  404  Not Found [IP: 91.189.91.82 80]
E: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/jammy-updates/main/binary-armhf/Packages  404  Not Found [IP: 91.189.91.83 80]
E: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/jammy-backports/main/binary-armhf/Packages  404  Not Found [IP: 91.189.91.83 80]
E: Some index files failed to download. They have been ignored, or old ones used instead.

```

Then, when i try to install the gtk3 libraries ([COLOR=#000080]**[FONT=lucida console]sudo apt install libgtk-3-dev:armhf[/FONT]**[/COLOR]) i get a whole lot of [FONT=lucida console]**unmet dependencies**[/FONT] errors.

Could someone tell me what should i do to build for armhf using the Ubuntu Jammy image available from the Windows Store for WSL?

---

### Post by yancek on 2024-04-17
The 404 error reported means it cannot find the IP address which generally means the server is down or your internet connection is.  Have you checked that?   Just ping the IP you have and see if it is successful to eliminate that as a possible problem.   The WSL was a non-gui program but should have a gui with windows 11 although I don't know that is the default.  The gtk toolkit is used for graphical user interfaces.


You are not using a standard Ubuntu but rather a version modified by microsoft so you may be better off at a windows forum.

---

