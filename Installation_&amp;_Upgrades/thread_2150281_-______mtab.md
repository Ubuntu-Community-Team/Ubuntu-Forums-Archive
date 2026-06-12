---
title: "-????????? ? ? ? ? ? mtab"
date: 2013-05-31
forum: Installation &amp; Upgrades
---

### Post by NadineH on 2013-05-31
I have copied/pasted a post from over two years ago at the end of this post. I am having the same issue and none of my searches have been able to provide me with a solution. The earlier post has no replies and the thread has been closed.

I am running Ubuntu 12.04 from a pendrive (Kingston Traveler 8G) with persistence that I installed about 20 days ago. This has not been an effortless task. So far Ubuntu is not recognizing my Linksys wireless N adapter. But I believe that I am getting very close to solving that issue.

But two days ago I received the same error as show in this previous post. I am able to boot up all right, but cannot mount any of the Windows drives that are on my system. And what greatly concerns me is the status of the mtab file: [COLOR=#417394]-?????????[/COLOR] [COLOR=#417394]?[/COLOR] [COLOR=#417394]?[/COLOR] [COLOR=#417394]?[/COLOR] [COLOR=#417394]?[/COLOR] [COLOR=#417394]?[/COLOR] [COLOR=#417394]mtab[/COLOR][COLOR=#000000]. The only thing showing up in the /media folder is the cdrom. All of the drives show up in the Nautilus window, but clicking on them produces the error regarding already being mounted. I need to have access to at least one of the Windows drives.

I suspect from what I have been able to glean from the forums, that this is a result of not making sure that all the drives were unmounted before shutting down Ubuntu (which it does not do gracefully).

Should I just try to remove the mtab file? Should I use chmod/chown to change the attributes of the mtab file? Should I do something with the fstab file? Should I just use the mount/unmount commands? 

[/COLOR]BYW, the only shot I have at internet access is via the wireless adapter. I have successfully installed Synaptic to facilitate downloading and installing packages offline. I use Win 7 (on this same computer) to download the packages to be installed. Everytime I clear one hurdle, up pops another one.

I would very much appreciate the wisdom that all of you have to offer.

Life is a journey and Ubuntu is another adventure along the way.

NadineH




May 10, 2011
[**[COLOR=#000000]Crasch[/COLOR]**]("http://ubuntuforums.org/member.php?u=1072273") 



**damaged /etc/mtab file**
[INDENT]I installed ubuntu 10.4 on a 8G pen drive.
Everithing went smooth, after doing some stuff (updgading, mounting samba) I get a damaged [COLOR=#417394]mtab[/COLOR] file.
No matter what I try this file seems to be gone. (sudo gedit /etc/mtab, sudo rm /etc/mtab )

doing a ls -l I get

lrwxrwxrwx 1 root root 13 2010-04-29 12:17 motd -> /var/run/motd
[COLOR=#417394]-?????????[/COLOR] [COLOR=#417394]?[/COLOR] [COLOR=#417394]?[/COLOR] [COLOR=#417394]?[/COLOR] [COLOR=#417394]?[/COLOR] [COLOR=#417394]?[/COLOR] [COLOR=#417394]mtab
[/COLOR]-rw-r--r-- 1 root root 624 2009-11-13 18:45 mtools.conf

Trying to mount a drive I get

Error mounting: mount exited with exit code 21: mount: according to [COLOR=#417394]mtab[/COLOR], /dev/sdb1 is already mounted on /media/System

Obviously I found nothing on /media.

Any idea on how solve this problem? [/INDENT]

---

### Post by ahallubuntu on 2013-05-31
~

---

### Post by NadineH on 2013-05-31
Thank you for your reply.

Am I wrong in thinking that with the question marks in place of real file attributes the file is inaccessible? Could the error that I am receiving be from not being able to read the mtab file? And why does it report that the drive is already mounted under /media when there is clearly nothing there for that drive?

NadineH

---

### Post by sudodus on 2013-05-31
Welcome to the Ubuntu Forums :-)

Your problem is probably a damaged file system where the persistence is stored (either a loop mounted casper-rw file or a casper-rw partition). You can try to repair it, which might work, or simply wipe of of its content (format it), or make an installed system on the 8 GB drive.

One common problem with systems on USB pendrives (at least USB 2 drives), is that it is slow, so slow, that you might be tempted to remove the pendrive before everything is written to it at shutdown. And this causes damages on the file system.

The problem with /etc/mtab is only a symptom, not the problem itself, as *ahallubuntu* wrote.

---

