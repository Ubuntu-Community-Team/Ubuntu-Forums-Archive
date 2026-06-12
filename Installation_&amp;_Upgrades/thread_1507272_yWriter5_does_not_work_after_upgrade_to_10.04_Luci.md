---
title: "yWriter5 does not work after upgrade to 10.04 Lucid"
date: 2010-06-11
forum: Installation &amp; Upgrades
---

### Post by 28_SNaKeS on 2010-06-11
Hello there, Ubuntu Community!

I'm fairly new to Linux, but I love it. I can't stand Windows anymore! 

Anyway, I've been using Ubuntu 9.10 for almost six months and decided to upgrade to 10.04. The only reason being was that I read somewhere that 10.04 supports iPod Touch "out of the box" and would allow me to organize add/remove music from it. Not that it matters, but it was my stepson's ipod that I wanted to connect, so I soley upgraded to help him out. Needless to say, after upgrading, it STILL didn't work. BAH!

Sorry for all the information you didn't even need to know ;)

Here's the problem:
Before upgrading to 10.04 I had already installed and had been using yWriter5, a novel writing software. I am using it to organize an adventure game I am writing. It's great software and is very helpful.

After the upgrade to 10.04, yWriter DOES NOT start anymore.

I get this following messege:
-------------------------------------
snake@snakepit:~/yWriter5/bin$ mono yWriter5.exe

** (yWriter5.exe:4171): WARNING **: The following assembly referenced from /home/snake/yWriter5/bin/yWriter5.exe could not be loaded:
     Assembly:   Microsoft.VisualBasic    (assemblyref_index=1)
     Version:    8.0.0.0
     Public Key: b03f5f7f11d50a3a
The assembly was not found in the Global Assembly Cache, a path listed in the MONO_PATH environment variable, or in the location of the executing assembly (/home/snake/yWriter5/bin/).


** (yWriter5.exe:4171): WARNING **: Could not load file or assembly 'Microsoft.VisualBasic, Version=8.0.0.0, Culture=neutral, PublicKeyToken=b03f5f7f11d50a3a' or one of its dependencies.
The entry point method could not be loaded
--------------------------------------

It acts as if the VisualBasic libraries aren't installed, but yet when I tried installing them again (to make sure) it says that they are already installed and are up to date.

I have emailed the creator of yWriter, but he was of no use. All he did was tell me that yWriter needs mono 2.4 (already installed) and the VB libraries (already installed) which I had already told him in the mail that I had those already installed. It's very frustrating and I can't find any threads about it anywhere on the web.

Thanks in advance for any help!
:)

---

### Post by 28_SNaKeS on 2010-06-11
I'm sorry for double posting, but did I post this in the wrong forum?

---

### Post by Tombgeek on 2010-06-11
No, you are in the right forum.

From the error message, I will assume you did not do a clean install of 10.04.
That is why I always tell people to rather do a clean install, overwriting the previous operating system, rather than just upgrading.

Perhaps reinstalling yWriter will solve the problem. From my experience in PCs (especially in Windows), if a program won't work, reinstall. There is probably a corrupt file or something, which is obviously the fault of the upgrade.

Also, as far as I know, the iPod thing only works through Rythembox, but I am not sure. I do not own an iPod.

Try reinstalling yWriter and see what happens.

P.S. I too am writing a novel at the moment, but I am not using yWriter. I was using it back when Windows XP was my primary OS, but Windows got corrupt and I lost my previous novel. I just use Abiword and OpenOffice Writer, because I am too lazy write out character bios and scene descriptions.

---

### Post by 28_SNaKeS on 2010-06-11
You are correct: I did not do a clean install. I upgraded using the Update Manager. Lesson learned. I'll make sure I do a clean install next time (If I even upgrade again in the future). Thank you for letting me know that was a bad choice :)

Well, I removed all the yWriter files and downloaded a fresh zip and followed all the directions like I did in 9.10. It was a no go. I get the same messege I posted above.

Would it be an idea to uninstall the VB libraries and install again? What about mono 2.4? If I do an uninstall of either, how do I go about this?

Also, would it be possible to reinstall Ubuntu 9.10 without losing any of my data?

If this is at all helpful, I think I may have installed Mono 2.4 OVER the mono I had in 9.10. But even if that is the case, I only installed it because yWriter wasn't working. The problem HAS to be the upgrade to 10.04.

Thanks for your suggestions.

---

### Post by Tombgeek on 2010-06-11
> **28_SNaKeS said:**
> You are correct: I did not do a clean install. I upgraded using the Update Manager. Lesson learned. I'll make sure I do a clean install next time (If I even upgrade again in the future). Thank you for letting me know that was a bad choice :)

Well, I removed all the yWriter files and downloaded a fresh zip and followed all the directions like I did in 9.10. It was a no go. I get the same messege I posted above.

Would it be an idea to uninstall the VB libraries and install again? What about mono 2.4? If I do an uninstall of either, how do I go about this?

Also, would it be possible to reinstall Ubuntu 9.10 without losing any of my data?

If this is at all helpful, I think I may have installed Mono 2.4 OVER the mono I had in 9.10. But even if that is the case, I only installed it because yWriter wasn't working. The problem HAS to be the upgrade to 10.04.

Thanks for your suggestions.

Hey

There is nothing wrong with upgrading via the Update Manager, it just opens up the possibility of something not working properly. Which is why most people recommend rather doing a clean install, because it limits the potential problems.

Hmm, looks like you have a tough situation. Well, I am no Linux expert, I am also a casual newbie user like youself.
Maybe it would perhaps work if you reinstalled VB libraries and Mono 2.4.
You can remove them through Synaptic, which is in System -> Administration.
Then just reinstall the packages.

You can downgrade to an older version, but it is a bit risky as far as I know. Here is the article.
[https://help.ubuntu.com/community/DowngradeHowto](https://help.ubuntu.com/community/DowngradeHowto)
You are really better off just backing up your files, format your drive, and reinstall Ubuntu if you are planning to downgrade. I just hope you don't have capped internet.

Sorry I can not be of much help. But from what I can see, the upgrade may have messed up your system a bit. You can try to reinstall VB libraries and Mono, maybe that would work.

---

### Post by 28_SNaKeS on 2010-06-11
Tried uninstalling the VB libraries and reinstalling them. Nothing different.

I'll try uninstalling/reinstalling mono I guess when I have some time. It's not looking good :(

All I want to do is use yWriter, without being forced to use Windows, for the love of God.

Thank you for your help, Tom.

(heh, my name's Tom as well)

---

### Post by Tombgeek on 2010-06-12
Just try reinstalling Mono. If all else fails, looks like your system is corrput and you need to format and reinstall your OS.
Just make sure you backup all your files beforehand.

Have you written back to the creator of yWriter, explaining that you did reinstall VB libraries and Mono, as well as the application itself, and nothing worked?

I can understand your frustration. While Ubuntu is a good OS, it is not exactly the most convienient OS, especially coming from Windows. You just want to do simple tasks, but you are bombarded with crap like this. Trust me, I have had a fair share of frustration with Ubuntu as well. But at least it does not compare to Windows, where you get tons of viruses and trojans.

---

### Post by Tombgeek on 2010-06-12
Also, before you do anything, try asking this question in the General Help section. Perhaps someone there can help because most threads in this section is for problems of the OS itself. So try asking in that section. Otherwise, ask the creator of yWriter again.

---

### Post by 28_SNaKeS on 2010-06-13
Thanks again, Tom.

I have spoken to the creator of the program and he thinks that it may be Mono. He is suggestion reinstalling Mono and Mono Basic with the Ubuntu Package Manager.

I've looked through the manager, but I don't know what I'm looking for. How do I reinstall these two?

---

### Post by Tombgeek on 2010-06-13
I don't see why you can't just use the terminal like he suggested on his site.
[http://www.spacejock.com/yWriter5_Linux.html](http://www.spacejock.com/yWriter5_Linux.html)

---

### Post by 28_SNaKeS on 2010-06-14
I am going to attemp uninstalling Mono and then reinstalling it.

Tom, I have already and it does nothing. He thinks that doing that may have made matters worse. So uninstallin mono completely and doing a fresh install of it may fix the problem.

He knows the software works with 10.04 since he has tried it. Somewhere along the line with upgrading has messed mono up.

---

