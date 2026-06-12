---
title: "Error On Clean Install"
date: 2011-06-21
forum: Installation &amp; Upgrades
---

### Post by T3rminus on 2011-06-21
I have not used ubuntu server before but I need it to set up my new server... so I D/Led it. I am running it next to Win 7 Home Pre. for right now but I am going to uninstall Win 7 after I get this installed.
 
I need to know why I cant install UBU 11.04. I keep getting an error even when I try to install enterprise cloud. It says: 
 
"Please insert the disc labeled: 'Ubuntu-Server 11.04 _Natty Narwhal_- Release amd64 (20110426)' in the drive '/media/cdrom/' and press enter."
 
I tried installing the regular Ubu server but the same error appeared. Any help?
 
Thx in advance.
 
-Phill

---

### Post by ajgreeny on 2011-06-21
Windows 7 often comes installed using all of the maximum of 4 partitions on a disk, so it is impossible to install any other OS.  You need to look at the current partition layout in Windows Disk Management, and if there are all 4 used you will need to delete one in order to install ubuntu server.  However be careful what you do as all the partitions may be important.

I will try to find the post I added to with links about how to deal with this problem, if that is what it turns out to be for you.

EDIT:  OK, here it is [http://ubuntuforums.org/showthread.php?p=10924416#post10924416](http://ubuntuforums.org/showthread.php?p=10924416#post10924416)

---

### Post by T3rminus on 2011-06-21
I am not trying to partition I am just trying to write over Win7 to install. I told Ubu to write over the existing files. I dont really need Win7 on the server soooo. I think that it did. The problem is that it only get part of the way through the install before giving me that error. Shouldn't the Ubu installer just format over Win7?

---

### Post by T3rminus on 2011-06-22
I have tried clearing and deleting two of the four partitions and then doing a clean install on the formated partition. Still no go. Kind of at a loss, still getting the same error. Any help anyone?
 
-Phill

---

### Post by dino99 on 2011-06-22
its always better to format your partition(s)/disk first with tools like partedmagic in case of hidden partitions (OS and/or manufacturer: tatooed)

---

### Post by T3rminus on 2011-06-22
Well they are gone and I need to find a way to get that specific file on to a disk and use it during install. Does anyone know where I can get it? Or could you make a copy of one from one of your systems and email it to me. Would help a lot. I would really like to start using Ubu for my server but I guess I could try a different one... :P
 
-Phill

---

### Post by ajgreeny on 2011-06-22
> **T3rminus said:**
> Well they are gone and [COLOR=Black]I need to find a way to get that [COLOR=Red]specific file[/COLOR] on to a disk and use it during install[/COLOR]. Does anyone know where I can get it? Or could you make a copy of one from one of your systems and email it to me. Would help a lot. I would really like to start using Ubu for my server but I guess I could try a different one... :P
 
-Phill
Now you've completely lost me!

What specific file are you talking about?   What you have said does not make any sense, so more info is needed.

---

### Post by T3rminus on 2011-06-22
The error I posted at the beginning says that I need that disc or file or something to finish the install. So I figure that someone must have it. I have completely deleted two of the partitions and formated but I still cant install the server, because of this error. It is kind of wierd that I cant install this server OS with a completely empty HD??? :P

---

### Post by tim44 on 2011-06-23
This error was caused by bad DVD drive in my case

---

