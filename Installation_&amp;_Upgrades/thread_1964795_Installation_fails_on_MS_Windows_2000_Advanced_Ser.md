---
title: "Installation fails on MS Windows 2000 Advanced Server"
date: 2012-04-24
forum: Installation &amp; Upgrades
---

### Post by rzward on 2012-04-24
Hi,

I am trying to install Ubuntu Linux on a server running MS Windows 2000 Advanced Server. 

Unfortunately, after the wubi installation program downloads the files and begins installing, it shows an error message saying that it cannot find the log file wubi-11.10-rev245.log in the C:\Documents and Settings\Administrator\Local Settings\Temp folder.

When it reports this error, it uses the 8-character-maximum versions of the folder names. Upon clicking on the OK button, the installation program disappears.

The thing is the log file is actually there. I've tried this at least 4 times now, trying different user names in the installation program's first dialog box, finally figuring out that the installation program uses the currently-logged in user name to store the temporary file and not the user name I enter in the dialog box.

The installation program also insists upon uninstalling before installing again. Then when installation begins again, it downloads the files again, which takes 1-2 hours, so this is taking a very long time. 

It would be great to have Linux on this server alongside MS Windows. If I can't get wubi to work on this server, is there another way to get a dual boot Windows/Linux?

Any help would be appreciated.

---

### Post by newbie-user on 2012-04-24
Use a virtual machine instead if you want Windows and Ubuntu running at the same time. A wubi installation is somewhat limited compared to a full install. VirtualBox is a good option.

However, you did say dual boot. So use Windows Disk Management to shrink your Windows partition to make space for Ubuntu, then use that new free space for a full install of Ubuntu.

---

### Post by darkod on 2012-04-24
If you don't want it to download every time, download the iso and put it in the same folder with wubi.exe. In that case it will use the iso. Make sure it's EXACTLY the same version otherwise it will ignore it. In fact, since wubi.exe is inside the iso you can extract it from there. That way you are sure it's the same version.

I don't recall now whether server 2000 has some security block, in vista and 7 you need to start the installation with right-click, Run As Administrator, not as double click. See what option right-click on wubi.exe offers on the server.

Dual booting a server? I can't really see your point. I guess you should look into VMware, XenServer, etc about virtualization, not wubi.

---

### Post by rzward on 2012-04-24
Thank you both. 

As this is MS Windows 2000 Advanced Server, I don't see the run as option when I right-click on the installation program. I'll confirm this but don't think this option came about until later.

If that doesn't work, I'll shrink the partition and install from a CD, which I have already made.

This server is turned off most of the time. It's a back-up of the main web server just in case something catastrophic happens and I need to use this server while the main web server is being fixed. Having Linux on it will actually give it more of a reason to be turned on.

Thanks again.

---

