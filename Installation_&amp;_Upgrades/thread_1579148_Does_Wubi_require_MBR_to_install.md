---
title: "Does Wubi require MBR to install?"
date: 2010-09-21
forum: Installation &amp; Upgrades
---

### Post by Redmage913 on 2010-09-21
Greetings,

I've got an Asus Eee Pc 1005P which is dual-booting Win7 Pro and MeeGo with GRUB. I want to get rid of Meego and install Ubuntu 10.10 Beta using Wubi, since I forgot my pen drive when I went in to school today.

My question is, does the Wubi installer require Windows to have its MBR as the boot manager? I tried running the wubi.exe file and it failed at the end when it tried to edit the boot sequence. I got the error message:

> Error executing command
>>command=C:\windows\System32\bededit.exe /create /d Ubuntu /application bootsector
>>retval=1
>>stderr=The boot configuration data store could not be opened. The system cannot find the file specified.

>>stdout=

For more information, please see the log file:

c:\users\*username*\appdata\local\temp\wubi-10.10-rev193.log 

I attached the log file.

Would it be best just to wait until I can grab my thumbdrive?

Regards,

--Red

---

### Post by bcbc on 2010-09-21
No, wubi uses the windows bootloader in the MBR, and then a variant of grub4dos to boot the wubi ubuntu. This won't be the cause of your problems - it doesn't care what's in the member - just you have to boot windows somehow before selecting the Ubuntu installed with wubi from the windows boot manager. Your problem sound more like you're not running wubi.exe as an administrator.

Why do you want to use 10.10? It's in beta right now. 10.04 is a long term support release (now in 10.04.1). This will be more stable. 
Wubi, in particular, tends to be less stable in the build up to a new release so I'd advise against using it on 10.10beta.

---

### Post by Mark Phelps on 2010-09-22
Strongly advise against using a wubi install of a Beta version of Ubuntu.  The last version had an entire thread devoted strictly to wubi-install related problems.  

There are enough problems inherent in a prerelease version without adding wubi complications to the list.

---

### Post by psusi on 2010-09-22
Of course if there are problems with a Wubi install, the time to find that out is now, BEFORE the release, so it can be fixed.

---

### Post by perspectoff on 2010-09-22
> **psusi said:**
> Of course if there are problems with a Wubi install, the time to find that out is now, BEFORE the release, so it can be fixed.

Yeah, good plan. Let's tell the newbies to work out the bugs.

---

### Post by psusi on 2010-09-22
> **perspectoff said:**
> Yeah, good plan. Let's tell the newbies to work out the bugs.

He chose to beta test... given that he already is willing to TEST a system that likely still has bugs, there is no reason to spread FUD that you shouldn't do it as a wubi install.

---

