---
title: "permisson denied at end of installation"
date: 2012-03-13
forum: Installation &amp; Upgrades
---

### Post by gettingintothis on 2012-03-13
i tried to dowload the version for windows. after i get done all the settings and stuff at the end of installation an error box appears. permisson denied view file. so i went to the file changed the properties to allow everything and it still says it when i try again please help.

---

### Post by gettingintothis on 2012-03-13
someone please help

---

### Post by westie457 on 2012-03-13
Welcome to UF.

A clue to what you were trying to download and install would be helpful. What you have written so far is vague.

We could guess at something and be completely wrong, then the advice would be worthless.

---

### Post by gettingintothis on 2012-03-13
i am trying to download wubi. i have a windows 7 hp notebook.

---

### Post by gettingintothis on 2012-03-13
ubuntu-11.10-wubi-amd64.tar.xz

---

### Post by westie457 on 2012-03-13
Thank you for the info.

Take a look at this page. [http://www.ubuntu.com/download/ubuntu/windows-installer](http://www.ubuntu.com/download/ubuntu/windows-installer)

It has the correct file and some guides to help you.

Installing things using .tar files is not the best way to do things. Tar files are usually the 'when all else fails' option.

---

### Post by gettingintothis on 2012-03-13
thanks for info but i tired your link and its still downloading the file tar. i looked at guides and they have no info on my problem

---

### Post by keithwill on 2012-03-13
I have just tried the link posted to help you, clicked on the large orange button saying "Start Download Ubuntu Installer for Windows" and it tries to download the file wubi.exe which is exactly what you want.

[http://www.ubuntu.com/download/ubuntu/windows-installer]("http://www.ubuntu.com/download/ubuntu/windows-installer")

I've reposted the link just in case.

---

### Post by westie457 on 2012-03-13
I have tried that link twice, once each for Windows 7 and Ubuntu. Each time I downloaded a file called 'wubi.exe' - a Windows executable file. I found a link for a 'lubi' - a linux based installer which uses a tar.gz file.

The link is here. [http://lubi.sourceforge.net/lubi.html](http://lubi.sourceforge.net/lubi.html)

However the information is nearly 5 years old and is probably out of date.

---

### Post by gettingintothis on 2012-03-13
i clicked your link and hit the big orange button. i get this far all the time. i choose my password and i hit install after that it starts to install and then it says extracting then expanding then i get an error occured:
permission denied for more info please see the log file c:\user\tinker~1\appdata\local\temp\wubi-11.10-rev245.log

---

### Post by westie457 on 2012-03-13
Try it this way.

Right-click the wubi.exe file and select 'run as Administrator'.

I had to install this way once before after getting the same error you are getting.

---

### Post by gettingintothis on 2012-03-13
this stuffs getting old man i tried it that way same thing. is there anything else i can do.

---

### Post by adstri on 2012-03-13
Dont suppose you would happen to know about the install issue I am having?

[http://ubuntuforums.org/showthread.php?t=1940167](http://ubuntuforums.org/showthread.php?t=1940167)

---

### Post by westie457 on 2012-03-13
Okay there are 2 options.

The easy one is to download an ISO file of your choice and create either a LiveCD or a LiveUSB and run wubi.exe from within Windows.

The hard way is to search the C:\ Drive for all files with wubi in the name and delete them. Then you have to the same with the Windows registry. Can be very time consuming and dangerous for your computer if you do this manually. The best thing to clean the registry imho is a program called 'ccleaner' available form here. [http://www.piriform.com/ccleaner](http://www.piriform.com/ccleaner)  This program is free. Then you can repeat the installing process you have already tried. It should work perfectly if you run wubi.exe as administrator. However it might still failwith the same errors.

There is a third option available. That is to create a dual-boot with Windows and Ubuntu on separate partitions using this link for guidance. [http://www.ubuntu.com/download/ubuntu/download](http://www.ubuntu.com/download/ubuntu/download)

Hope this is helpful.

---

### Post by westie457 on 2012-03-13
@adstri

I took a look at your thread and at the moment your problem is beyond my abilities and knowledge as I have nothing that uses a GPT partition table.

My suggestion to you is search this forum for posts by 'oldfred' using the keywords 'missing partitions' and 'GPT partitions. Somewhere you will find the information you need to help you. Also take a look here for information. [http://www.rodsbooks.com/fixparts/](http://www.rodsbooks.com/fixparts/)

---

### Post by bcbc on 2012-03-13
> **gettingintothis said:**
> this stuffs getting old man i tried it that way same thing. is there anything else i can do.

There is a log file that contains the answer to your problem. But it sounds like bug [lpbug]862003[/lpbug]. If the permission denied comes right at the end (and the progress bar has completely finished) it's likely that bug - which means the install is actually successful (just reboot).

---

