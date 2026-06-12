---
title: "Qt4 Won't Install"
date: 2012-08-10
forum: Installation &amp; Upgrades
---

### Post by dragonwrenn on 2012-08-10
I'm having a bit of trouble installing Qt4 on Ubuntu 12.04 LTS 64-bit

NOTE:  I tried this with BOTH the Qt Linux 32 bit and 64 bit packages, offline and online, all the same error.

sudo chmod u+x QtSdk-offline-linux-x86-v1.2.1.run 

./QtSdk-offline-linux-x86-v1.2.1.run 
bash: ./QtSdk-offline-linux-x86-v1.2.1.run: No such file or directory

Any ideas as to why I'm getting this strange error?  Terminal is able to execute other executables perfectly fine, its only Qt that seems to have this problem.

---

### Post by raja.genupula on 2012-08-10
take out that file to some other location and try out there .

---

### Post by dragonwrenn on 2012-08-10
> **raja.genupula said:**
> take out that file to some other location and try out there .
Tried it- no good :\
Even tried installing it off a flash, still no good

---

### Post by raja.genupula on 2012-08-11
could you give us the exact code of terminal , i mean what you have entered and what you have got .

---

### Post by spjackson on 2012-08-11
According to [this]("http://qt-project.org/forums/viewthread/16861") you can get this error if you are trying to install the 32-bit download on 64-bit linux without having the necessary 32-bit libraries installed.

However, you say that you have the same error with the 64-bit download.

I have tried the 32-bit and 64-bit online versions on 64-bit 12.04. The 32-bit gives me the error you report, precisely for the reason indicated in the above link. However the 64-bit online starts up fine. I haven't tried the offline installs because I don't want to download that much when I don't need it.

If you are getting the same error with the 64-bit download, it could still be due to missing libraries. Do you have the build-essential package installed?

Is the file on a non-Linux partition? (e.g. FAT, NTFS etc.) This can sometimes be a problem, but you would get "permission denied" rather than "No such file or directory".

---

