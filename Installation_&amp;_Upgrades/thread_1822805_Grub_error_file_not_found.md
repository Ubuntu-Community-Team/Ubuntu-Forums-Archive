---
title: "Grub error: file not found"
date: 2011-08-11
forum: Installation &amp; Upgrades
---

### Post by dosh on 2011-08-11
I've had my Ubuntu crash and had to reload it. I;ve reloaded 9.1 and am now getting the error

GRUB loading.
error: file not found 
grub rescue>

I have tried a number of solution attempts I've found on the internet with no success. 

I have Windows 7 also loaded however I'm not getting a Grub menu only the error above. I seem to have a number of Linux partitions I believe my correct one is on sda7. I had at one stage tried to have a boot partition on sda4. But I think this is where it has caused the problem. Any help much appreciated.

---

### Post by MG&amp;TL on 2011-08-11
Probably means Ubuntu's got itself corrupted or deleted somewhere along the line, and grub can't find it. Try and reinstall Ubuntu over the previous one, I think that should work.

If you want a file recovery tool (before doing that), I can suggest Puppy Linux, an OS in its own that runs on RAM from a memory stick or live cd.

---

### Post by garvinrick4 on 2011-08-11
Just a guessing game unless we see a boot script as per below: Will tell us why you cannot boot.

 

 #Download this Script to DESKTOP:
 [http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
 Open a Terminal and use these four commands one at a time. copy and paste will work fine.
 ```

 cd Desktop
 unzip boot_info_script060.zip
 chmod +x boot_info_script.sh
 sudo ./boot_info_script.sh

``` There will now be a file called RESULTS  on Desktop copy and paste to this Thread:
 Use code tags and will be easier to read: (Highlight all text after pasting and click on # sign in upper right of message box)


#What you have done below:

 
[LIST=1]
[*]You are changing directory's to     Desktop
[*]You are unzipping
[*]You are making executable
[*]You are executing  the Script
[*]Done Results on Desktop
[/LIST]

---

### Post by dosh on 2011-08-11
Thanks...have solved it, Installed Ubuntu 11.04. Solved the problem

---

