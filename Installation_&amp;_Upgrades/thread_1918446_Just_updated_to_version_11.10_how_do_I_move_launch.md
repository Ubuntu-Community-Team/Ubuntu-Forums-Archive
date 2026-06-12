---
title: "Just updated to version 11.10 how do I move launcher bar to bottom of screen"
date: 2012-02-01
forum: Installation &amp; Upgrades
---

### Post by SUPERFITTER on 2012-02-01
[FONT=Times New Roman][SIZE=4]I Just updated to version 11.10 from 10: 

1. How do I move launcher bar to bottom of screen[/SIZE][/FONT][SIZE=4]?  [FONT=Times New Roman]With version 10. I had everything at bottom of desktop and I could find everything faster.
[/FONT]
[FONT=Times New Roman]2. How do I find if this is a 32 bit or a 64 bit install?[/FONT][/SIZE]

---

### Post by ScientificProp on 2012-02-01
You can see if it's 32 or 64 bit by checking the System Info in the System Settings collection of programs.

---

### Post by ottosykora on 2012-02-01
>1. How do I move launcher bar to bottom of screen? <

you can't

---

### Post by raja.genupula on 2012-02-01
> **SUPERFITTER said:**
> [FONT=Times New Roman][SIZE=4]I Just updated to version 11.10 from 10: 

1. How do I move launcher bar to bottom of screen[/SIZE][/FONT][SIZE=4]?  [FONT=Times New Roman]With version 10. I had everything at bottom of desktop and I could find everything faster.
[/FONT]
[FONT=Times New Roman]2. How do I find if this is a 32 bit or a 64 bit install?[/FONT][/SIZE]

1 Ans [http://www.webupd8.org/2011/10/how-to-move-unity-launcher-to-bottom-of.html](http://www.webupd8.org/2011/10/how-to-move-unity-launcher-to-bottom-of.html)

2 . as our friend said system settings-> system info .
all the best . 

small suggestion : please make post with a nice look . :D:D

---

### Post by SUPERFITTER on 2012-02-01
[FONT=Times New Roman][SIZE=4]Thank you ScientificProp, I have a 32 bit system

Thank you raja.genupula, I ran into a slight problem. At the terminal (Ctrl + Alt + T), I pasted this:

[/SIZE][/FONT][FONT=Times New Roman][SIZE=4]mkdir -p ~/.compiz-1/plugins cd ~/unityshell cp libunityshell.so ~/.compiz-1/plugins/ mkdir /tmp/unityshell cp *.png /tmp/unityshell/ cd /tmp/unityshell/ chmod 644 *.png sudo chown root:root *.png sudo cp *.png /usr/share/unity/4/[/SIZE][/FONT][FONT=Times New Roman][SIZE=4]And got this:

[sudo] password for dennis:


My log in password does not work, any ideas what I am doing wrong :(:(?[/SIZE][/FONT] 

 [FONT=Times New Roman][SIZE=4]I'm still new to Linux[/SIZE][/FONT]

---

### Post by raja.genupula on 2012-02-01
password not working means 

1. May be CAPS LOCK ON is one issue .
2. Everything is fine but still same issue means we have to rest the password.

But before going to 2nd make sure about the 1st thing . i.e everything is fine in your keyboard .

---

### Post by SUPERFITTER on 2012-02-02
[FONT=Times New Roman][SIZE=4] No joy. I changed the password and checked on the cap lock. I cannot type in my password yet on a terminal[/SIZE][/FONT].[FONT=Times New Roman][SIZE=4] Are there any other options?

Thanks[/SIZE][/FONT]

---

### Post by raja.genupula on 2012-02-02
[FONT=Times New Roman][SIZE=4]I[/SIZE][/FONT]> [FONT=Times New Roman][SIZE=4] cannot type in my password yet on a terminal[/SIZE][/FONT]

Hi
 did you mean you're not seeing the password you're typing in terminal ? or still its saying wrong password . ?

ok give me the terminal code of what you entered and what you got . It can helps us to understand your issue .

Thank you .

---

### Post by SUPERFITTER on 2012-02-02
[SIZE=4]This  is what I get in terminal.  I cannot type in my password. It shows that no such file or directory.  Any idea what I'm doing wrong?

Thanks:(:(


dennis@dennis-desktop:~$ mkdir -p ~/.compiz-1/plugins
dennis@dennis-desktop:~$ cd ~/unityshell
bash: cd: /home/dennis/unityshell: No such file or directory
dennis@dennis-desktop:~$ cp libunityshell.so ~/.compiz-1/plugins/
cp: cannot stat `libunityshell.so': No such file or directory
dennis@dennis-desktop:~$ mkdir /tmp/unityshell
mkdir: cannot create directory `/tmp/unityshell': File exists
dennis@dennis-desktop:~$ cp *.png /tmp/unityshell/
dennis@dennis-desktop:~$ cd /tmp/unityshell/
dennis@dennis-desktop:/tmp/unityshell$ chmod 644 *.png
dennis@dennis-desktop:/tmp/unityshell$ sudo chown root:root *.png
[sudo] password for dennis: [/SIZE]

---

### Post by raja.genupula on 2012-02-02
> **SUPERFITTER said:**
> [SIZE=4]This  is what I get in terminal.  I cannot type in my password. It shows that no such file or directory.  Any idea what I'm doing wrong?

Thanks:(:(


dennis@dennis-desktop:~$ mkdir -p ~/.compiz-1/plugins
dennis@dennis-desktop:~$ cd ~/unityshell
bash: cd: /home/dennis/unityshell: No such file or directory
dennis@dennis-desktop:~$ cp libunityshell.so ~/.compiz-1/plugins/
cp: cannot stat `libunityshell.so': No such file or directory
dennis@dennis-desktop:~$ mkdir /tmp/unityshell
mkdir: cannot create directory `/tmp/unityshell': File exists
dennis@dennis-desktop:~$ cp *.png /tmp/unityshell/
dennis@dennis-desktop:~$ cd /tmp/unityshell/
dennis@dennis-desktop:/tmp/unityshell$ chmod 644 *.png
dennis@dennis-desktop:/tmp/unityshell$ sudo chown root:root *.png
[sudo] password for dennis: [/SIZE]

the third point in the link i have given to you 

```
Extract the downloaded archive to your home directory. A new folder called "unityshell" should be created upon the extraction.

```

please watch and follow the steps carefully . 

try again . you cant watch the password as ***** what you're typing in terminal . so just type and give enter it will take automatically . please follow steps carefully .

all the best and let me know what you got .

---

### Post by SUPERFITTER on 2012-02-03
[FONT=Times New Roman][SIZE=4]Hi raja.genupula[/SIZE][/FONT][FONT=Times New Roman][SIZE=4] 

I got my password to work as you can see. I logged off and logged back in, no change in launcher location, so I repeated the terminal and had the same results. I had to enter my password twice to get it to accept. This time I rebooted and got the same results, launcher is still on left side of desktop.[/SIZE][/FONT]:(


[FONT=Times New Roman][SIZE=4]
dennis@dennis-desktop:~$ mkdir -p ~/.compiz-1/plugins
dennis@dennis-desktop:~$ cd ~/unityshell
bash: cd: /home/dennis/unityshell: No such file or directory
dennis@dennis-desktop:~$ cp libunityshell.so ~/.compiz-1/plugins/
dennis@dennis-desktop:~$ mkdir /tmp/unityshell
dennis@dennis-desktop:~$ cp *.png /tmp/unityshell/
dennis@dennis-desktop:~$ cd /tmp/unityshell/
dennis@dennis-desktop:/tmp/unityshell$ chmod 644 *.png
dennis@dennis-desktop:/tmp/unityshell$ sudo chown root:root *.png
[sudo] password for dennis: 
Sorry, try  again.
[sudo] password for dennis: 
dennis@dennis-desktop:/tmp/unityshell$ [/SIZE][/FONT]

---

### Post by raja.genupula on 2012-02-03
HI man 
         please follow the steps in the link carefully . you did some mistake thats why  actions not  had taken . ok let me explain what you did . 

If did properly , i mean exactly as mentioned in the link then you will never get a message like this

 > dennis@dennis-desktop:~$ cd ~/unityshell
bash: cd: /home/dennis/unityshell: No such file or directorythat step 3 is already trying to say this , 
> Extract the downloaded archive to your home directory. **A new folder called "unityshell" should be created** upon the extraction.you got that error because you have not done this step properly . 

so please follow all the steps mentioned properly .
All the best :D:D
if you got anything , let us know that .

---

### Post by SUPERFITTER on 2012-02-03
In my home folder I had this: 
/home/dennis[/SIZE]/unityshell.tar-1 

Which I put in the trash. I ran through all the steps again and got this folder in the home folders
 /home/dennis/unityshell.tar.lzma

Now I have the correct folder.  Then I ran this in the terminal:
sudo apt-get install lzma

And got this:

dennis@dennis-desktop:~$ sudo apt-get install lzma
[sudo] password for dennis: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
lzma is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 5 not upgraded.
dennis@dennis-desktop:~$ 

Then I ran this in terminal and got this:


dennis@dennis-desktop:~$ mkdir -p ~/.compiz-1/plugins
dennis@dennis-desktop:~$ cd ~/unityshell
bash: cd: /home/dennis/unityshell: No such file or directory
dennis@dennis-desktop:~$ cp libunityshell.so ~/.compiz-1/plugins/
dennis@dennis-desktop:~$ mkdir /tmp/unityshell
mkdir: cannot create directory `/tmp/unityshell': File exists
dennis@dennis-desktop:~$ cp *.png /tmp/unityshell/
cp: cannot create regular file `/tmp/unityshell/Firefox_wallpaper.png': Permission denied
dennis@dennis-desktop:~$ cd /tmp/unityshell/
dennis@dennis-desktop:/tmp/unityshell$ chmod 644 *.png
chmod: changing permissions of `Firefox_wallpaper.png': Operation not permitted
dennis@dennis-desktop:/tmp/unityshell$ sudo chown root:root *.png
[sudo] password for dennis: 
Sorry, try again.
[sudo] password for dennis: 
dennis@dennis-desktop:/tmp/unityshell$ 

Then I logged out and then logged back in, and the launcher is still 
on the left side. I don't know what else to do?:(:(:(

---

### Post by raja.genupula on 2012-02-04
[SIZE="1"]dennis@dennis-desktop:~$ mkdir -p ~/.compiz-1/plugins
dennis@dennis-desktop:~$ cd ~/unityshell
bash: cd: /home/dennis/unityshell: No such file or directory[/SIZE]

you have to extract that unityshell.tar.lzma folder . Please follow the instructions man . again and again you're doing same mistake . extract that folder then only you can get that unityshell in your home folder . do it carefully man .

---

### Post by SUPERFITTER on 2012-02-04
that step 3 is already trying to say this , 
 
Quote: Extract the downloaded archive to your home directory. **A new folder called "unityshell" should be created** upon the extraction. 
Extract the downloaded archive to your home directory. 
 
you got that error because you have not done this step properly. 
 
 
It seems that I don't know how to do this correctly. That is probably why I keep getting the same results. How do I extract the downloaded archive to my home directory correctly. I should have asked that question first.
 
Thank You:)

---

### Post by MG&amp;TL on 2012-02-04
If I am not...mistaken, there is a much easier way to do it.

[http://www.webupd8.org/2011/11/install-ubuntu-unity-bottom-launcher.html]("http://www.webupd8.org/2011/11/install-ubuntu-unity-bottom-launcher.html")

---

### Post by raja.genupula on 2012-02-04
yeah @MG&TL . that's really easy way . I think it could help him.

---

### Post by SUPERFITTER on 2012-02-05
I think I found the problem. I used update to get version 11.10.  When I checked my downloads they were all there, but some would not load. When I updated from version 10 series, I should have downloaded and burned a copy and installed it that way.  I backed up my downloads so I can reinstall them.  When I updated to version 11.10, it asked if I wanted to keep some old version folds and files that would no longer work in version 11.10, so I deleted them. I don't know if I should have keep them?  Maybe all of my downloads would still work.
I think this is why I cannot get the launcher to move to the bottom of the desktop because files are missing?

---

### Post by MG&amp;TL on 2012-02-05
> **SUPERFITTER said:**
> [SIZE=2]I think I found the problem. I used update to get version 11.10.  When I checked my downloads they were all there, but some would not load. When I updated from version 10 series, I should have downloaded and burned a copy and installed it that way.  I backed up my downloads so I can reinstall them.  When I updated to version 11.10, it asked if I wanted to keep some old version folds and files that would no longer work in version 11.10, so I deleted them. I don't know if I should have keep them?  Maybe all of my downloads would still work.[/SIZE]
 [SIZE=2]
[/SIZE] 
 [SIZE=2]I think this is why I cannot get the launcher to move to the bottom of the desktop because files are missing?[/SIZE]

We found an easier way to do things: please just follow the link I gave in my last post.

---

### Post by SUPERFITTER on 2012-02-12
[SIZE=1]I installed Gnome and ran it in classic mode. It has two panels, one at the top of desktop and one at the bottom. This is a great improvement from the left side unity panel for me. I snuck over to Linux Mint and found Cinnamon. 

[http://cinnamon.linuxmint.com/?page_id=61](http://cinnamon.linuxmint.com/?page_id=61)

This is perfect for me, one small panel with everything in one location.  You can also move the panel to the top of the page or have both top and bottom.  I hope this helps others with the unity panel.:):)

[http://cinnamon.linuxmint.com/](http://cinnamon.linuxmint.com/)[/SIZE]

---

