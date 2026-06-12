---
title: "Question about NAS Sharing &amp; Setup"
date: 2008-02-18
forum: Installation &amp; Upgrades
---

### Post by R00tKid on 2008-02-18
I was able to set up my NAS server following the instructions and advice on these forums.

From the terminal, I used the smbmount commands to mount the NAS to my U-Desktop.  I also reviewed the instructions on editing the fstab file to allow for auto-mounting at bootup.  Here is the issue.

Mounting the NAS in fstab allows all users to access the NAS when they log in.  However, I have set up my NAS (DLinkk DNS 323) to allow access to specific directories for individual users. So for my uname,pwd, it allows access to the whole volume, for my daughter, she has her own uname/pwd that allows access to only a particular directory..and so on.

If I put in my uname/pwd in the fstab file, then she has access to it as well.  I want to prevent this so that the desktop user login drives the specific access to specific directories in the NAS.

Is there a way to set it up in the fstab (or some other startup script) to drive this access? So when I login, it mounts using my uname/pwd, when my wife logs in, it mounts using her uname/pwd... I would prefer this approach.

Or is the alternative to set permissions on the NAS directories to disallow access by specific groups/users?  There will be a Windows machine also accessing the NAS and will setting permissions impact the ability of the Windows machine to access these directories?

Thanks

---

### Post by R00tKid on 2008-02-18
????

Still searching for an answer...this is easy in WinXP - login, open Explorer, click Map/connect Network Drive, access under different uname, reconnect at login - and it is done.  Whenever the user logs in, they are mapped and connected to the NAS directory with their NAS credentials automatically giving them their allowed access.  It can't be that difficult in Linux now, would it??:confused:

---

### Post by R00tKid on 2008-02-19
Bump!!!!

C'mon, this can't be that difficult!!!  Unless it is that easy and no one wants to waste their time and help:) - I will take anything - a full detailed step-by-step description, a short summary explanation or even a pointer to another posting/web site.

BTW, I am reading the guides on Linux Documentation Project - by far the best site for me to learn about Linux - really helping me understand the fundamentals of Linux - but it will still be a while before I learn from that about what to do.

---

### Post by tlynch999 on 2008-04-04
Bump!

Did you ever hear how to do this?  I wish I could help you, but I'm looking for some similar help.  I'm running hardy and for whatever reason, I have to reconnect to my NAS every time I restart.  Gutsy left the icons in place...and I didn't do anything differently (that I remember)...

---

### Post by tlynch999 on 2008-04-04
I may have just gotten my answer thanks to PeteBuntu...

System >> Preferences >> Sessions
Click on the last tab (Session Options)
Check the Checkbox (Automatically remember running applications when logging out)

I'm going to try this when I get home...hope it helps you out.

---

