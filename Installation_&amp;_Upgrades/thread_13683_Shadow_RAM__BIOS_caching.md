---
title: "Shadow RAM / BIOS caching"
date: 2005-02-02
forum: Installation &amp; Upgrades
---

### Post by Ron W on 2005-02-02
In section 3.6.3.4. of the Ubuntu's Manual files it says:-

"**Shadow RAM**
Your motherboard may provide shadow RAM or BIOS caching. You may see settings for ``Video BIOS Shadow'', ``C800-CBFF Shadow'', etc. Disable all shadow RAM. Shadow RAM is used to accelerate access to the ROMs on your motherboard and on some of the controller cards. Linux does not use these ROMs once it has booted because it provides its own faster 32-bit software in place of the 16-bit programs in the ROMs. Disabling the shadow RAM may make some of it available for programs to use as normal memory. Leaving the shadow RAM enabled may interfere with Linux access to hardware devices."

Question 1
In my BIOS (AmiBIOS) there are two options called 'System BIOS Cacheable', and 'Video, 32k shadow' which I'm sure need to be set to disable. However, there are another two of which I'm not sure; these are called 'External cache' and 'Internal cache'.
Are these also forms of BIOS caching mentioned above that need to be disabled?

Question 2
As the Video, Internal, and External mentioned in question 1 are set to 'Enabled' for my current O/S (Windows 98 SE), will there be a conflict as I want to dual boot my computer with Ubuntu and Windows 98? If so, what can I do about it?

Thanks

Ron

---

