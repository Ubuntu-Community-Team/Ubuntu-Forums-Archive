---
title: "Making .bin files executable"
date: 2006-09-10
forum: Installation &amp; Upgrades
---

### Post by voodoonirvana on 2006-09-10
Im trying to install RealPlayer10GOLD.bin and im trying to do what the installation instructions say which are...

nstallation Instructions

- Ensure that the .bin file you downloaded is executable. You can make the .bin file executable by running the "chmod a+x RealPlayer10GOLD.bin" command from a terminal window.

- Run the .bin file by typing "./RealPlayer10GOLD.bin". Follow the prompts provided to finish installing the player.

- When you launch the player for the first time, a set-up assistant will take you through configuring your player.

- Enjoy your RealPlayer10 for Linux!

And when I try to make the bin file executable, it says that there is no such file or directory. Im new to linux, so some help would be great.

---

### Post by jISh on 2006-09-10
Make sure you have the capital letters correct. Linux is case-sensitive.

---

### Post by taurus on 2006-09-10
You need to know where you download it!!!  Chances are it's in ~/Desktop...

```
cd ~/Desktop
chmod 755 RealPlayer10GOLD.bin
./RealPlayer10GOLD.bin (for personal use...)
-or-
sudo ./RealPlayer10GOLD.bin (for system wild...)

```

---

### Post by voodoonirvana on 2006-09-10
> **taurus said:**
> You need to know where you download it!!!  Chances are it's in ~/Desktop...

```
cd ~/Desktop
chmod 755 RealPlayer10GOLD.bin
./RealPlayer10GOLD.bin (for personal use...)
-or-
sudo ./RealPlayer10GOLD.bin (for system wild...)

```

Thankyou soooo much, I dont know what I would do without this forum.

---

### Post by borisdaniel on 2007-03-31
> cd ~/Desktop
chmod 755 RealPlayer10GOLD.bin
./RealPlayer10GOLD.bin (for personal use...)
-or-
sudo ./RealPlayer10GOLD.bin (for system wild...)

ok chmod 755 ./RealPlayer10Gold.bin i get
chmod: cannot access `/RealPlayer10Gold.bin': No such file or director

sudo ./realplayer10gold.bin
i am asked for password yet i cannot type the password which is numerical

HELP MEEEEEEEEE

thanks,
boris

---

### Post by taurus on 2007-03-31
> **borisdaniel said:**
> ok chmod 755 ./RealPlayer10Gold.bin i get
chmod: cannot access `/RealPlayer10Gold.bin': No such file or director

sudo ./realplayer10gold.bin
i am asked for password yet i cannot type the password which is numerical

HELP MEEEEEEEEE

thanks,
boris

```
**chmod 755 RealPlayer10Gold.bin**
```

---

### Post by borisdaniel on 2007-03-31
okay just to make sure am doing this properly.
I go app / access/terminal

then i type in chmod 755 RealPlayer10GOLD.bin

here's what am doing and results
> boris@boris-desktop:~$ chmod 755 RealPlayer10GOLD.bin
chmod: cannot access `RealPlayer10GOLD.bin': No such file or directory


the file on my desktop is RealPlayer10GOLD.bin directly from the real site download

---

### Post by taurus on 2007-03-31
```
cd ~/Desktop
chmod 755 RealPlayer10GOLD.bin
sudo ./RealPlayer10GOLD.bin
```

You need to be in the right directory before you can run the "chmod" command.

---

### Post by borisdaniel on 2007-03-31
THANK YOU!!!!!!

now am in step two i think.
enter the complete path.

---

### Post by taurus on 2007-03-31
It means where would you want to install RealPlayer?  I usually pick 

```
/opt/RealPlayer
```
and when it asks if you want to link it, answer yes.

---

### Post by borisdaniel on 2007-03-31
just when you think you have it, stuff happens.

heres a error message when opening real player it is showing up under sound and video :

> Details: Failed to execute child process "realplay" (No such file or directory)
 
do i need to remove the install and redo to the bin and if so what / where was the problem. after i opened the bin it asked for a path directory I assumed /RealPlayer10GOLD.bin and it started the installation process.

---

### Post by taurus on 2007-03-31
Did you install it to /opt/RealPlayer?  Did you happen to link it to /usr/bin?  What's the output of this command from a terminal?

```
realplay
```

---

### Post by borisdaniel on 2007-03-31
funny i dont know what i did now i have real player 10 working .. well i think i havent yet tried opening a media file

as soon as the install completed it was sent to 
[http://www.adobe.com/shockwave/download/download.cgi?P1_Prod_Version=ShockwaveFlash](http://www.adobe.com/shockwave/download/download.cgi?P1_Prod_Version=ShockwaveFlash)
i think i already have this installed but wouldnt the system detect it and not open the download page?

Next? how can i change my default media to real player 10? when i download a media ithe choices is only a movie player and other but i cant find another audio media?

---

### Post by borisdaniel on 2007-03-31
Thank You... got real player 10 up and running and working. I even added Beep Media, i guess am on a roll using unbuntu :)
 
Is there any threads i can find about learning more about .bin and how to work with terminal to install future programs? is there any way to find a media that is compatible with windows media, like openoffice is with word doc files?

thanks.
boris

---

### Post by taurus on 2007-03-31
[http://monkeyblog.org/ubuntu/installing/](http://monkeyblog.org/ubuntu/installing/)

[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

---

### Post by KuroYoma on 2008-01-19
Ok Everything works until i put in the command
 
sudo ./RealPlayer10Gold.bin

It comes up with this error

error while loading shared libraries: libstdc++.so.5: cannot open shared object file: No such file or directory

---

### Post by oldos2er on 2008-01-19
Don't run it as sudo.

---

### Post by GavinZac on 2008-01-19
Just as an aside, RealPlayer is available as a .DEB file somewhere on the net if you google for it :)

---

