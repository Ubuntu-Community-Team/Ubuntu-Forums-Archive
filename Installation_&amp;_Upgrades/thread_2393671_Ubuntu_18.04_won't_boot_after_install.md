---
title: "Ubuntu 18.04 won't boot after install"
date: 2018-06-06
forum: Installation &amp; Upgrades
---

### Post by Spaceman9 on 2018-06-06
I used wubi to install Ubuntu 18.04 LTS into an HP 2000 laptop with an Intel(R) Pentium(R) CPU B950 @ 2.10GHz and Intel graphics. I started en using Ubuntu in 2012 in this laptop and never had a problem with Ubuntu booting.

Everything worked fine after installing and updating but that was last night. This morning it only boots into a dark blueish-purpleish screen.

I looked at the text in the second Grub. This is not the Grub that lists both Windows 7 and Ubuntu, the is the Grub that comes after that.

So, the first line of text is: setparams 'Ubuntu'
					gfxmode $linux_gfx_mode

I have to get into this install of Ubuntu because I moved data files from my backup drive into this install i can't replace.

Any help is welcome. Thank you.

---

### Post by ajgreeny on 2018-06-06
You are unlikely to get much help any more with wubi installs of Ubuntu as wubi has not been supported for several years, was never intended to be used as a dual boot setup but only to test hardware compatibility. Most of us have now completely forgotten all about wubi.

I suggest that you do a "proper" dual boot installation from a live USB system which is easy enough particularly as you seem to still have Windows 7 which always (as far as I'm aware) was installed in legacy BIOS, not using UEFI.

For more help have a look at:-
[https://help.ubuntu.com/community/DualBoot](https://help.ubuntu.com/community/DualBoot)
[https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)

---

### Post by Spaceman9 on 2018-06-06
Thankx for your help ajgreeny. I can't do anymore installs until I get back into this current install and rescue those data files.  Do you know of some way to "see" those files in the current install I have of Ubuntu 18.04?

---

### Post by ajgreeny on 2018-06-06
> **Spaceman9 said:**
> Thankx for your help ajgreeny. I can't do anymore installs until I get back into this current install and rescue those data files.  Do you know of some way to "see" those files in the current install I have of Ubuntu 18.04?

Sorry, I'm afraid not as I have no personal experience of WUBI, nor of the details of using Win 7; my last Windows OS experience was using XP 13 years ago.

---

### Post by Spaceman9 on 2018-06-06
Then maybe someone else will know how I can rescue those data files.

---

### Post by QIII on 2018-06-06
From the file explorer in Windows, do you see a directory like "C:\ubuntu\"?

---

### Post by Spaceman9 on 2018-06-06
Thankx for the help QIII. Yes, I can see the Ubuntu folder and if i click on it i can see folders called disks, install and winboot. there are also files named Ubuntu.ico, Ubuntu.png and uninstall-wubi.exe. The problem is that's all I can find. I don't know how to see the data files I moved from my backup drive to the Pictures folder in the new insillation of Ubuntu 18.04.

---

### Post by Spaceman9 on 2018-06-06
QIII if someone could tell me how to get Ubuntu 18.04 to boot that would help a lot. Even if it's just in low-res graphics mode.

---

### Post by QIII on 2018-06-06
Wubi installs (or did back in the day) to blob file at C:\ubuntu\disks\root.disk.  If you don't see that there, then please have a look at [this]("https://wiki.ubuntu.com/WubiGuide") in the subsection "Cannot boot into Ubuntu".  If that is not helpful, there is a much more detailed bit of advice [here]("https://askubuntu.com/questions/201485/how-can-i-recover-files-inside-a-wubi-install-before-re-installing-ubuntu?utm_medium=organic&utm_source=google_rich_qa&utm_campaign=google_rich_qa").

SAVE A COPY of root.disk if you find it in case something goes wrong.

Those come from 2014 and 2012, respectively.  Most folks will have forgotten anything they knew about Wubi back then.  I used it exactly once so that I could answer questions about installation and removal, so I can't really be of much more help.

Best wishes!  There must certainly be a way to do what you are asking for!

---

### Post by Spaceman9 on 2018-06-06
Thank you QIII very much. I'll have a look at those links. Have a good day.

---

