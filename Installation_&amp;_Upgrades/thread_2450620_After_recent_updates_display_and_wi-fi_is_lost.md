---
title: "After recent updates display and wi-fi is lost"
date: 2020-09-17
forum: Installation &amp; Upgrades
---

### Post by apatos on 2020-09-17
Dear people, I realized that after recent updates between 31.8-2.9 2020 Ubuntu  Studio loses the second display and wi-fi connections. I had to reverse  back to 30.8 Timeshift backup to get the external display back. Anyone  else having same problem?

I was waiting to get fixed updates to this day, but nothing had changed since that. I have Dell Precision M4700.

---

### Post by deadflowr on 2020-09-17
What does that even refer to?
I have no idea what 31.8-2.9 2020 or 30.8 are.
Some context of what those mean would help to understand.

---

### Post by CatKiller on 2020-09-17
> **deadflowr said:**
> What does that even refer to?
I have no idea what 31.8-2.9 2020 or 30.8 are.
Some context of what those mean would help to understand.

I'm pretty sure they're dates. I don't know what's caused the OP's problems with their proprietary bits, though.

---

### Post by apatos on 2020-09-17
Those are simply dates. So I was waiting till this day to see if any correcting updates would appear but no. But I think it's the "Ubuntu Studio base" part of the updates that causes the problem. There are now two different ones to update, but they both contain plenty of sub-categories to untick so it would be huge effort to go through each of them one by one to see where it goes wrong.

---

### Post by mastablasta on 2020-09-18
> **apatos said:**
>  I have Dell Precision M4700.

why people assume all models are the same is beyond me. even when companies offer you to configure the model yourself, they would still say i have gazelle or XPS or whatever.

the model you posted can be configured at least with the following GPU chips (if there aren't even more of them out there):
> [COLOR=#444444][FONT=Arimo]Intel HD 4000 (with NVIDIA Optimus)[/FONT][/COLOR]
[COLOR=#444444][FONT=Arimo]AMD FirePro M4000 Mobility Pro 1GB GDDR5[/FONT][/COLOR]
[COLOR=#444444][FONT=Arimo]NVIDIA Quadro K1000M 2GB GDDR3[/FONT][/COLOR]
[COLOR=#444444][FONT=Arimo]NVIDIA Quadro K2000M 2GB GDDR3[/FONT][/COLOR]

i am sure there are a couple of vairous wi-fi chips used in same model. since they can be different even based on serial number / manufacture date.

in any case please let us know the specs of the machine and possibly the drivers being used.

few weeks ago a display on one of the PCs switched to nouveau drivers after HWE kernel upgrade, until i selected a newer nvidia driver version (which was now recommended) in additional drivers application. it reverted back to correct resolution and speed.

wi-fi chips drive could have a regression in kernel. again we have no idea what you are running. for production machines it is best to keep the kernel the same and receive only security patches. anyway, depending on the chip you might be able to manually patch the kernel with driver. but make sure secure boot is off.

---

### Post by Impavidus on 2020-09-18
I don't know what upgrades you installed between 31 August and 2 September. It was in your logs, but you probably deleted those while restoring your backup. Not everyone installs the same upgrades on the same day, as (A) some mirrors may be delayed relative to others, (B) many only install upgrades once a week, not on the same day for all, (C) phased upgrades mean that an upgrade can be delayed for different users by a different random time and (D) not all users have the same packages installed. But if I had to guess, I expect a kernel upgrade would have been responsible. After installing a new kernel, the old one isn't automatically deleted. You can use the grub menu and select advanced options for Ubuntu to boot using an older kernel.

---

### Post by apatos on 2020-09-18
Thanks for all the replies. I now found out it is probably the kernel  thing. If I go to the other options in grub 2 menu and select Ubuntu  with Linux 5.4.0 -42 instead of the new -47 version it works. I have [COLOR=#444444][FONT=Arimo]NVIDIA  Quadro K2000M 2GB GDDR3 as a GPU. And i7 QM 2.6Ghz processor. In the next replies I'll post screenshots of the update lists and in the last two images unticked  the parts in submenu I suspect  are the culprit. This is from the moment after I reversed back with the  Timeshift. What you think am I on the right track opting them out?[/FONT][/COLOR] (I could not attach them here for some reason as I got an error, so I'll make separate reply) Edit: This system does not allow me to add screenshots even without text and resized to smaller scale.

---

### Post by apatos on 2020-09-18
In the security updates submenu there is an item called: " Linux kernel extra modules for version 5.4.0 on 64 bit x86 SMP". That was the one I thought of opting out. And then under the "other updates" submenu there is "Tool for enabling and disabling wireless devices". Maybe I should leave it out as well?

---

### Post by Impavidus on 2020-09-18
You can use attachments to add screenshots to your post. If you use a screenshot of only the relevant window (not your entire desktop), the picture is smaller, so it's easier to use and the forum won't resize it. And in case you considered it: don't use screenshots of plain text. Paste it as text in your post.

---

### Post by deadflowr on 2020-09-18
> **CatKiller said:**
> I'm pretty sure they're dates. I don't know what's caused the OP's problems with their proprietary bits, though.

Makes sense.
I see there were kernel and xserver (display server) security updates around that time.
So probably some issue with those updates.
Here's the security notices for those updates:
[https://ubuntu.com/security/notices/USN-4483-1]("https://ubuntu.com/security/notices/USN-4483-1")
[https://ubuntu.com/security/notices/USN-4488-1]("https://ubuntu.com/security/notices/USN-4488-1")

That said, as far as posting images use attachments.
(For attachments any reply option except quick reply should give add a paperclip icon in the reply toolbar.
Click on that to open the attachments utility, then simply use the upload feature to upload the image(s) from your computer.
New uploads should automatically get selected for the current thread)

For adding text outputs please use code tags.
See this post for code tags: [https://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168]("https://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168")

---

### Post by apatos on 2020-09-19
deadflowr, thanks for those tips. However, I have no idea what to do with those security notices? Am I suppose to somehow manually install the code found on those sites to correct the errors? Or shall I wait till they will be implemented in upcoming update packages that can be automatically installed as usual? I'm afraid I can't do anything with them manually as I'm totally incapable in touching anything "under the hood". Should I just update everything and boot in older kernel version -42? As I said that seemed to work and the errors came with the -47 version. And then just wait till some newer better optimized automatic updates come along to switch to the newer one?

---

### Post by apatos on 2020-09-22
deadflowr, I don't know if you got notice of my reply as I did not do it as quick reply directly to you, but just continued this thread?

---

### Post by deadflowr on 2020-09-22
> **apatos said:**
> deadflowr, thanks for those tips. However, I have no idea what to do with those security notices? Am I suppose to somehow manually install the code found on those sites to correct the errors? Or shall I wait till they will be implemented in upcoming update packages that can be automatically installed as usual? I'm afraid I can't do anything with them manually as I'm totally incapable in touching anything "under the hood". Should I just update everything and boot in older kernel version -42? As I said that seemed to work and the errors came with the -47 version. And then just wait till some newer better optimized automatic updates come along to switch to the newer one?
Sorry, I should have made clear the security links are just for reference of what major packages were upgraded around the time you started getting your issues.
Nothing more to those than that.

And yes you can boot into the older kernel if the new one is broken.
It the design of the system to allow reverting to a good and properly working kernel for such an event.

> And then just wait till some newer better optimized automatic updates come along to switch to the newer one?
You can try.
But unless you know the developers have been notified of any issues, don't expect it to be any different.

Beyond that I really don't know much of how to help as I don't have wifi currently and don't have nvidia cards.
You have other posters involved who can give better advice on what to do.

> **apatos said:**
> deadflowr, I don't know if you got notice of my reply as I did not do it as quick reply directly to you, but just continued this thread?
Quick Reply is a posting option.
It's at the bottom of the thread area.
Unlike the other Reply to Thread options  Quick Reply is limited to a select few options in it's toolbar editor.
Which does not include the attachments feature.

---

### Post by apatos on 2020-09-27
Thank you again., But how do I reach the developers to inform them about this error? Should I contact the Canonical support?

---

### Post by deadflowr on 2020-09-27
> **apatos said:**
> Thank you again., But how do I reach the developers to inform them about this error? Should I contact the Canonical support?

File bug reports:
[https://help.ubuntu.com/community/ReportingBugs]("https://help.ubuntu.com/community/ReportingBugs")

---

### Post by apatos on 2020-10-22
After taking a look at the Launchpad thing it looks way too intimidating for newbie to use. It looks like I should read page after page info on how to use it and set the PGP keys and stuff. Could you please send this issues there through your system if you have such a launch pad set? I am sure I'm not the only one with this problem. I wonder why there isn't simply a support e-mail address where I could link this thread. I find myself having zero interest in concentrating in studying all details in development bug reporting in such a multiple step process. This makes me hate Ubuntu/Linux and regret I ever chose it.

---

