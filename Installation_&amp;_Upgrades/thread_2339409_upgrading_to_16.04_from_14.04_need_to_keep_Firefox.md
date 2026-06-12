---
title: "upgrading to 16.04 from 14.04: need to keep Firefox passwords."
date: 2016-10-08
forum: Installation &amp; Upgrades
---

### Post by Autodave on 2016-10-08
Wife's machine still running 14.04 and I want to update her to 16.04. I have learned that updating usually is not worth the problem because it rarely works. So, I want to do a clean install of 16.04. What I would like to know is how I can save her Firefox favorites (which I know how to copy) and her saved passwords. Is there a file or files that I can copy from the current installation and then put into the new install in order to save her passwords.

---

### Post by oldfred on 2016-10-08
I always backup & copy entire profile for both Firefox & Thunderbird. I know that works.
With new install, start Firefox once to create default profile and hidden folder. Then copy old profile into .mozilla and edit profile.ini to use your profile not new one just created.

But I also copy profile to laptop when traveling & back again to desktop.
I also moved profiles to /mnt/data partition. Originally data partition was NTFS to share with XP, but now it is ext4. Also then copied from old desktop to new desktop.

Same for Firefox & Thunderbird.
[http://kb.mozillazine.org/Moving_your_profile_folder](http://kb.mozillazine.org/Moving_your_profile_folder)
[http://support.mozillamessaging.com/en-US/kb/Profiles](http://support.mozillamessaging.com/en-US/kb/Profiles)
[http://www.mozilla.org/support/thunderbird/profile](http://www.mozilla.org/support/thunderbird/profile)

I use Firefox passwords only for those sites that do not have any or much data on me, never financial sites. I use mostly keypassX and copy its key file from system to system.

---

### Post by ian-weisser on 2016-10-08
> **Autodave said:**
> I have learned that updating usually is not worth the problem because it rarely works. 

Untrue.
I have found Ubuntu release-upgrades to be well-tested and reliable.
 
I have done release-upgrades for over 10 years on multiple systems.
I have had exactly two failures, both for the same reason: I failed to uninstall non-Ubuntu software. Neither of those failures were Ubuntu's fault.

Breakage is everywhere in life. The cause of the breakage is important.

---

### Post by Autodave on 2016-10-08
Last upgrade from 14.04 to 16.04 was tried by me on 8 computers: one worked perfectly, 1 kinda worked, other 6 failed to where they were unusable and had to be installed fresh.

---

### Post by Autodave on 2016-10-08
I am not finding the profile folder. I have it showing hidden files, but all I am finding is a *profiles.ini *file. When I open that, there really isn't much there: only 7 short lines.

---

### Post by Autodave on 2016-10-08
OK: got it. You need the profile.ini file and the folder next to it with the name of the folder specified in the .ini file.

Thanks for the help!

---

