---
title: "lg3d-jdk needs to be reinstalled"
date: 2008-06-02
forum: Installation &amp; Upgrades
---

### Post by jdorenbush on 2008-06-02
So this all started out when I tried to setup *folder sharing*.

I got a prompt saying:
[SIZE="1"]Sharing service is not installed
You need to install the Windows networks sharing server in order to share your folders.[/SIZE]

I clicked, **Install Service**

I received this error message:
[SIZE="1"]E: The package lg3d-jdk needs to be reinstalled, but I can't find an archive for it.
E: Internal error opening cache (1). Please report.[/SIZE]

I tried doing this via Terminal (sudo apt-get install lg3d-jdk), and received this error:
[SIZE="1"]E: The package lg3d-jdk needs to be reinstalled, but I can't find an archive for it.[/SIZE]

I downloaded this, **lg3d_jdk1.6.0_i686.deb**, and double clicked to install.

I received this error message:
[SIZE="1"]Could not open 'lg3d_jdk1.6.0_i686.deb
The package might be corrupted or you are not allowed to open the file. Check the permissions of the file.[/SIZE]

These are the permissions of that file:
[SIZE="1"]Owner: jeff - jeff User
Access: Read and Write
Group: jeff
Access: Read and Write
Others
Access: Read and Write
Execute: Allow executing file as program[/SIZE]

I am out of ideas and I am a Ubuntu noob (TBH). Any help is much appreciated. Thanks!

---

### Post by iaculallad on 2008-06-02
Check you repository if enabled:

Navigate through System->Administration->Software Sources. On the "Ubuntu Software" tab, put a check mark on Main, Universe, Restricted, and Multiverse. Uncheck the check box w/c says "Installable from CD-ROM/DVD". Click on close and choose reload on the next window w/c pops-up and do the "Install Service" again.

---

### Post by PmDematagoda on 2008-06-02
The package isn't in the repositories, so you would have to download it and manually install it.

Did you download the deb package from [here]("https://lg3d-core.dev.java.net/binary-builds.html")? If so, did you download the one for the 22 Feb 2008 update?

---

### Post by iaculallad on 2008-06-02
> **PmDematagoda said:**
> The package isn't in the repositories, so you would have to download it and manually install it.

Did you download the deb package from [here]("https://lg3d-core.dev.java.net/binary-builds.html")? If so, did you download the one for the 22 Feb 2008 update?

Thanks for pointing it out, I just thought it comes with the repo's :)

---

### Post by jdorenbush on 2008-06-11
> **PmDematagoda said:**
> The package isn't in the repositories, so you would have to download it and manually install it.

Did you download the deb package from [here]("https://lg3d-core.dev.java.net/binary-builds.html")? If so, did you download the one for the 22 Feb 2008 update?

I tried to download and install the following. I got this error, "The package might be corrupted or you are not allowed to open the file. Check the permissions of the file." :(
**2007-02-08 **
# lg3d_jdk1.6.0_i686.deb

---

### Post by jdorenbush on 2008-06-11
Somehow I fixed it - I think? I basically followed the steps iaculallad left and now I am able to install software. So I assume its fixed.

---

