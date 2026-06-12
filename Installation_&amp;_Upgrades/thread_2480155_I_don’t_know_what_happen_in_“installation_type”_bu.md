---
title: "I don’t know what happen in “installation type” but can you tell me about this?"
date: 2022-10-21
forum: Installation &amp; Upgrades
---

### Post by excelonvive on 2022-10-21
[COLOR=#000000]Good day, I'm new to the forum and hoping to find help here.

I just trying to instal ubuntu on my laptop, all is well until i stuck with instalation type

[/COLOR][https://drive.google.com/file/d/1nJMnQ9O1gEROpwGGS4t5GQQ0LX_R2bfF/view?usp=drivesdk](https://drive.google.com/file/d/1nJMnQ9O1gEROpwGGS4t5GQQ0LX_R2bfF/view?usp=drivesdk)
[https://drive.google.com/file/d/10WPCRbYsYUHQHJFPWVzd0ARxW3c8zI1b/view?usp=drivesdk](https://drive.google.com/file/d/10WPCRbYsYUHQHJFPWVzd0ARxW3c8zI1b/view?usp=drivesdk)

[COLOR=#000000]And when i click &#8220;change&#8221; on second pic this happen

[/COLOR][https://drive.google.com/file/d/1pcgDCsQJwILFESHrT7uqu4p5E-N_O0v8/view?usp=drivesdk](https://drive.google.com/file/d/1pcgDCsQJwILFESHrT7uqu4p5E-N_O0v8/view?usp=drivesdk)[COLOR=#000000]

I don't know where to start. Please leave some suggestions. Thank you very much![/COLOR]

---

### Post by Dennis N on 2022-10-21
I get "access denied" to your images. With Google Drive, I think for each image you need to set sharing for "anyone with the link", copy the link and post it.

---

### Post by excelonvive on 2022-10-21
Wait a minute

---

### Post by excelonvive on 2022-10-21
And done! Now you can access the images, thank you for your attention

---

### Post by Dennis N on 2022-10-21
Is this a new disk, or does it have Windows on it?
If its new, you need to make a partition table. The installer will do that for you if you just choose "erase and install ubuntu" on a previous screen. That choice will erase anything on the disk, set up the partitions, and then complete the installation.
I don't use Windows, so if you are trying to dual boot with Windows, someone else will need to answer. Not sure, but I have read that not shutting down Windows completely can make any partitions invisible.

---

### Post by ActionParsnip on 2022-10-21
Are you setting up a dual boot? If so then shutdown the system then cold boot to the installer. You may want to run a full chkdsk on your internal file systems in Windows too (if you are dual booting)

---

### Post by ajgreeny on 2022-10-21
As Dennis N said, Windows by default uses a fast startup[ system, meaning the system goes into a form of hibernation which causes all sorts of problems in dual boot.

Unfortunately I also can not help in more detail as I gave up using Windows 17 years ago but search around for how to turn off fast startup and one possible problem should be removed.  Windows can turn it back on so you need to check occasionally that has not happened.
I am not sure if the partitions will be invisible if fast startup is enabled but they will certainly be impossible to mount in order to see what is on them so disable it before doing anything else.

---

### Post by yancek on 2022-10-21
You need to post more information, the questions asked above.  It doesn't appear to have a partition table so check that.  Also very important if there is another OS (windows?) on the drive or if it is a new blank drive.  Also, the last image where you indicate you clicked change shows nothing to change.  You would need to click the + symbol to add something new and on the lower right of the window, you need to set the Mount point to /, the symbol for the root of the filesystem where you will install Ubuntu.

---

