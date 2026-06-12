---
title: "How can I backup my *old* /home directory?"
date: 2011-10-02
forum: Installation &amp; Upgrades
---

### Post by Vkthor on 2011-10-02
Hi.

My Ubuntu 10.10 is not working properly I need to reinstall it but although I had backups of all my documents data, like spreadsheets or text documents, I would like to keep all my settings and small programs I have in /home/vkthor.

This way I can install Ubuntu a new way, one partition for it and another for my *new* /home directory.

It should be easy. I thought I could copy my *old* /home/vkthor directory to an USB drive and after install copy it again to the new partition.

The problem is: I only can boot from an Ubuntu CD. It starts a new /home/ubuntu directory and when I try to copy /media/acdcab9b3....(File System)/home/vkthor to target drive (using Nautilus windows) it says that some files/directories can not be copied because I do not have rights to do it.
I have tried to input 
```
sudo nautilus
```
in a console window but also did not worked.
How can I copy it using the command line?
I have found that 
```
ubuntu@ubuntu:~$ sudo su
``` give me the righs to do it, but if I try
```
root@ubuntu:/media/acdcab9b3....(File System)/home# cp vkthor/*.* /media/Ubuntu.bak/home/
``` I receive several messages «Omit directory 'vkthor/netbeans'» and so on and the copy is not performed. Several directories are missing in the target drive.
Can you please tell me what am I doing wrong? And how to round this?

Thank you.

PS. I am thinking about files and directories like a MS-DOS old user. It seems *cp *does not work exactly like MS-DOS *copy *command. Maybe this is my mistake.

[COLOR="Sienna"]**The solution**
```
ubuntu@ubuntu:$ sudo rsync -av /media/acdca9b3-38ff-4dd6-8209-49b4fb92e5c9/home/vkthor /media/ubuntu.bak
```
I have opened the file manager and browse through File system > acdca9b3-38ff-4dd6-8209-49b4fb92e5c9 > home. My Vkthor's home folder was there. Pressed CTRL L to see the path copied it to terminal console end ENTER.
As easy as that.
Hope this can help someone else.
Thank you all who helped me along this thread.[/COLOR]

---

### Post by zvacet on 2011-10-02
See if [this]("http://psychocats.s465.sureserver.com/ubuntu/backup") can be of any help to you.

---

### Post by Hakunka-Matata on 2011-10-02
> **Vkthor said:**
> Hi.

I have tried to input 
**```
sudo nautilus
```in a console window but also did not worked.**

```
gksu nautilus
```,

---

### Post by Vkthor on 2011-10-03
Hi Hakunka-Matata
Tanks for your answer, but it still does not work.

I have got this error:
```
ubuntu@ubuntu:~$ gksu nautilus
Initializing nautilus-gdu extension

** (nautilus:4672): WARNING **: Failed to get the current CK session: GDBus.Error:org.freedesktop.ConsoleKit.Manager.GeneralError: Unable to lookup session information for process '4672'

(nautilus:4672): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed
Nautilus-Share-Message: Called "net usershare info" but it failed: 'net usershare' devolveu o erro 255: net usershare: cannot open usershare directory /var/lib/samba/usershares. Error Ficheiro ou directoria inexistente
Please ask your system administrator to enable user sharing.


(nautilus:4672): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed
```

The last line repeats itself each time I try to use any windows operation.

I am booting from Ubuntu Live CD, so, what am I doing wrong?

---

### Post by Hakunka-Matata on 2011-10-03
[(nautilus:4672): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed]("http://ubuntuforums.org/%28nautilus:4672%29:%20GConf-CRITICAL%20**:%20gconf_value_free:%20assertion%20%60value%20%21=%20NULL%27%20failed")

That link references a bug report with symptoms that sound a lot like yours, it's on Ubuntu 10.10 da-de-da.............  
If you have a CD with a different Release, say 10.04 it might prove interesting.....

What's wrong with your installation?, maybe it could be fixed - cleaned up?

```
das@160GB:~$ sudo cp -r Downloads/* /media/dougbackuptest
```that command works fine for me.........  But I'm not running in "liveCD" mode,,

---

### Post by Vkthor on 2011-10-04
> **zvacet said:**
> See if [this]("http://psychocats.s465.sureserver.com/ubuntu/backup") can be of any help to you.

Hi zvacet.
Thanks for your help.
I never used rsync before. I have looked for a linux backup solution and after all I used Sync Back through Wine. I could backup files and directories but not the system folders like what happens in Windows.
But after reading that, it was very easy to backup my /home directory.

I hope that now I can use it to recover my all my data after reinstall Ubuntu that crashed some time ago.

Best regards.

---

### Post by Vkthor on 2011-10-04
> **Hakunka-Matata said:**
> (snip) it's on Ubuntu 10.10 da-de-da.............  
If you have a CD with a different Release, say 10.04 it might prove interesting..... (snip)

Hi again Hakunka-Matata.
Well, it was the *only* CD I had.
I have tried to install 10.10 after making new formated partitions and restore my *old* /home/vkthor directory to one of them.
It seemed the install was working fine but I have got an endless loop at login screen. I have typed my password (with no errors) and Ubuntu asked for it again and again and again...
After deleting (and formating) my data partition (the /home/vkthor) the install worked fine.
I have updated to the new 11.04. May be it works better. I will try to recover my old /home now.
Wish me luck.
Best regards.

---

### Post by Vkthor on 2011-10-05
I was lucky.
[LIST]
[*]I have used rsync to backup my SinceIntrepidIbex original /home/vkthor folder
[*]I have used GParted to «kill» Microsoft Windows XP partition (I did not use it since my first steps with Ubuntu), and organize my HD for a fresh Ubuntu install: 15Gb for Ubuntu, 2Gb for Linux-swap and all the rest of space to the new /home/vkthor 
[*]After successful partitioning I have restored my backup /home/vkthor to the new partition  I have also used rsync to do it. All my data was well recovered.
[*]Then I tried to install Ubuntu 10.10 from the liveCD I had telling it to use the /home/vkthor as new /home directory. It did not worked well. I do not know why but I could not bypass the login window. Maybe it was an install bug. Do not know.
[*]Trying to go on I have erased all the content of the /home/vkthor folder. No problem. I had a backup. Then the new install worked fine. I used it to upgrade online to the new 11.04 Ubuntu
[*]I thought I had lost all the chances of recovering all my programs data and settings I have backup. I only had Firefox, LibreOffice and a few new programs. Not my desktop and all the stuff I was collecting since Intrepid Ibex. I did not give up. What if I try to restore the /home/vkthor data now? I thought. 
[*]Well, **it worked**! The Firefox has begun to update my extensions. My desktop returned, also my themes and icons. Uau! I only have to download and install all my programs. My data and settings are there.
[/LIST]
It was NOT the perfect way, I know, but worked and I could change an unknown «bad» first install for a new one the way it must be. Ubuntu in a partition, /home in another. And no data loosing.

If you are reading this, remember: never give up and ALWAYS have a backup of your data. It is not the question IF you will loose your data, but WHEN you will.

Best regards.

---

