---
title: "setting wacom(bamboo fun)"
date: 2011-02-12
forum: Installation &amp; Upgrades
---

### Post by apis_apih on 2011-02-12
hello,:D
need help to setting wacom in ubuntu 10.10:o
 
- i download file at ([http://sourceforge.net]("http://sourceforge.net/")) and try to install ([COLOR=#000000][FONT=Times New Roman][FONT=sans-serif]**[xf86-input-wacom]("http://sourceforge.net/apps/mediawiki/linuxwacom/index.php?title=Xf86-input-wacom")**[/FONT][/FONT][/COLOR]):(:)


s3mpoi@s3mpoi:~$ cd  xf86-input-wacom-0.10.10.tar.bz2
bash: cd: xf86-input-wacom-0.10.10.tar.bz2: No such file or directory

[COLOR=Red]-after that i mass up with  code, then it be like this[/COLOR]:confused:

s3mpoi@s3mpoi:~$ cd  xf86-input-wacom-0.10.10.tar.bz2
bash: cd: xf86-input-wacom-0.10.10.tar.bz2: No such file or directory

[COLOR=Red]- so where directory it refer to(i want paste the file in directory):confused:
- or how to change the directory[/COLOR]
[COLOR=Red]- itry this code[/COLOR]

- s3mpoi@s3mpoi-desktop:~$ mkdir/home/s3mpoi/desktop
bash: mkdir/home/s3mpoi/desktop: No such file or directory

-s3mpoi@s3mpoi-desktop:~$ cd/home/s3mpoi/desktop
bash: cd/home/s3mpoi/desktop: No such file or directory

---

### Post by Favux on 2011-02-12
Hi apis_apih,

Welcome to Ubuntu forums!

The tar in the name means it is a compressed file/folder like zip.  You can't change directory into a compressed file/folder or file ever.  Since you are in Maverick it probably down loaded into your /home/yourusername/Downloads directory rather than your Destop.

When you open a terminal the prompt ~$ is in the /home/yourusername directory.  So you would do:
```
cd Downloads
```
Now the prompt will look like '~/Downloads$'.  Then to see what's in it enter 'ls' (list):
```
~/Downloads$ ls
```
If you see it there to unpack or extract the tar (unzip it) enter:
```
tar xjvf xf86-input-wacom-0.10.10.tar.bz2
```
To change directories back a level you can use:
```
cd ..
```
A handy reference to teach you all of this is available free, the [Ubuntu Pocket Guide]("http://www.ubuntupocketguide.com/download_main.html").  Of course you can do all that graphically in Places (Nautilus) and to extract it right click on it and chose 'Extract here'.

But you don't want 0.10.10 as it has a known bug for the pad (tablet buttons).  See instead the [Bamboo P & T HOW TO]("http://ubuntuforums.org/showthread.php?t=1515562").  I'm assuming your Bamboo Fun is one of the new ones with touch.

Hope this helps.

---

### Post by apis_apih on 2011-02-12
> **Favux said:**
> Hi apis_apih,

Welcome to Ubuntu forums!

The tar in the name means it is a compressed file/folder like zip.  You can't change directory into a compressed file/folder or file ever.  Since you are in Maverick it probably down loaded into your /home/yourusername/Downloads directory rather than your Destop.

When you open a terminal the prompt ~$ is in the /home/yourusername directory.  So you would do:
```
cd Downloads
```Now the prompt will look like '~/Downloads$'.  Then to see what's in it enter 'ls' (list):
```
~/Downloads$ ls
```If you see it there to unpack or extract the tar (unzip it) enter:
```
tar xjvf xf86-input-wacom-0.10.10.tar.bz2
```To change directories back a level you can use:
```
cd ..
```A handy reference to teach you all of this is available free, the [Ubuntu Pocket Guide]("http://www.ubuntupocketguide.com/download_main.html").  Of course you can do all that graphically in Places (Nautilus) and to extract it right click on it and chose 'Extract here'.

But you don't want 0.10.10 as it has a known bug for the pad (tablet buttons).  See instead the [Bamboo P & T HOW TO]("http://ubuntuforums.org/showthread.php?t=1515562").  I'm assuming your Bamboo Fun is one of the new ones with touch.

Hope this helps.

thank you for the help and the refrent to. :P.

---

### Post by apis_apih on 2011-02-12
i am lost....

i manage to open unzip file and chage the directory to find a file, but..

**Configuring the build **


[COLOR=Red] ./autogen.sh [/COLOR]--prefix=/usr --libdir=/usr/lib        # on 32-bit install
[COLOR=Blue]icant find[/COLOR] [COLOR=Red]./autogen.sh [COLOR=Blue]in the download file, so i try install 
[/COLOR][/COLOR]**Install from Prebuilt **

 [jej@ayukawa jej]$ cd linuxwacom-0.8.6-1/prebuilt.......[B][COLOR=Blue].ok[/COLOR]
[/B] [jej@ayukawa prebuilt]$ su......................[COLOR=Red](need password)[/COLOR]
 [jej@ayukawa prebuilt]# ./uninstall
 [jej@ayukawa prebuilt]# ./install
[COLOR=Blue]need pasword----- i am sure i enter correctly, but...[/COLOR]

[COLOR=Black]
[/COLOR][COLOR=Black]s3mpoi@s3mpoi-desktop:~/linuxwacom-0.8.8-10/prebuilt$ su
Password: 
su: Authentication failure
s3mpoi@s3mpoi-desktop:~/linuxwacom-0.8.8-10/prebuilt$ 

how can i fix that
[/COLOR]

---

### Post by Favux on 2011-02-13
Hi apis_apih,

Don't follow the LWP HOWTO.  Follow the Bamboo P & T HOW TO I linked you to above.  If you hover your cursor pointer on it you'll see it changes color and if you click on it, it will take you to the HOW TO.  That's what the underline means.  Here it is non-embedded:

[http://ubuntuforums.org/showthread.php?t=1515562](http://ubuntuforums.org/showthread.php?t=1515562)

Notice the HOW TO assumes you download the files onto your Desktop.  So if they're in the Downloads folder move them to the Desktop.

---

