---
title: "Tips for troubleshooting a preseed install?"
date: 2014-03-14
forum: Installation &amp; Upgrades
---

### Post by UsernameNumber on 2014-03-14
Hello all,

I [posted this to ask.ubuntu]("http://askubuntu.com/questions/433732/advice-for-troubleshooting-a-url-preseed-file") recently but haven't gotten any answers, so I thought I would try here. Responses are welcome in either place, of course.

[COLOR=#333333][FONT=UbuntuRegular]I'm working on my first preseed file, and to avoid having to re-burn a DVD every time I make a change, I'm hosting it on a webserver and loading it with **preseed/url=...**

To load the preseed, I'm booting a virtual machine from an edubuntu 12.04 LTS DVD, selecting the **Install Edubuntu** option, pressing **F6**, and replacing the **file=... **with **auto  url=...**

According to the logs on my webserver, the preseed file *is* getting downloaded by the installer, but then... as far as I can tell, it isn't being used. For example, I get prompted to select a language even though **d-i debian-installer/locale string en_US** is right there at the top of the preseed. I also tried this ["100% automated"]("https://help.ubuntu.com/community/InstallCDCustomization/PreseedExamples") preseed with the same results.

So, apparently something is going wrong between the installer retrieving my preseed and the contents thereof actually getting used, and I'm at a loss for how to troubleshoot this further.

If I do a **Ctrl+Alt+F2** while the installer starts, I can see a bunch of stuff happening, including several "Authentication Failed" messages that may or may not mean anything, but if that output gets saved in any way that lets me do a meaningful examination of it I haven't found it.

I'm sure I can't be the first person to have this problem, but I didn't find much when I searched for "preseed troubleshooting" here or on the Ubuntu forums, so perhaps this would be a good thread to start. Any advice would be greatly appreciated!


[/FONT][/COLOR]

---

