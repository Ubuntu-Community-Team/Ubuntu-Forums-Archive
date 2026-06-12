---
title: "help in installing &quot;motion&quot; with ubuntu"
date: 2008-09-11
forum: Installation &amp; Upgrades
---

### Post by nouraldin on 2008-09-11
hi
i have been doing a security camera with Ubuntu ,
every thing looks fine , until i tried to install "motion",

here is the guide :
[http://infectedproject.wordpress.com/2007/06/26/set-up-a-webcam-security-system/]("http://infectedproject.wordpress.com/2007/06/26/set-up-a-webcam-security-system/")

in step 4 it shows what to wright in the terminal:
sudo mv ~/Desktop/Motion Config.zip_FILES /etc/motion/

i downloaded the "motion" package on the desktop,
but the code in step 4 dosen't fit ,

here is the error i get :
mv: cannot stat `/home/nour/Desktop/Motion': No such file or directory
mv: cannot stat `Config.zip_FILES': No such file or directory


thanks for the helpers

---

### Post by Partyboi2 on 2008-09-11
Have you installed the motion package first? Step 4 is to configure motion after you have installed it.
If you have a working internet connection you can install motion by
```
sudo apt-get install motion
``` If not then double click on the motion deb that you have on your Desktop and install it.

---

### Post by nouraldin on 2008-09-11
yes i had download motion and installed it,
but now i want to install the Motion’s configuration file .
maybe u r right i will install the motion by u r way ,
coze i don't know if i downloaded the right package, i hope that linux can download auto the right package:).

---

### Post by SkonesMickLoud on 2008-09-11
> **nouraldin said:**
> hi
i have been doing a security camera with Ubuntu ,
every thing looks fine , until i tried to install "motion",

here is the guide :
[http://infectedproject.wordpress.com/2007/06/26/set-up-a-webcam-security-system/](http://infectedproject.wordpress.com/2007/06/26/set-up-a-webcam-security-system/)

in step 4 it shows what to wright in the terminal:
sudo mv ~/Desktop/Motion Config.zip_FILES /etc/motion/

i downloaded the "motion" package on the desktop,
but the code in step 4 dosen't fit ,

here is the error i get :
mv: cannot stat `/home/nour/Desktop/Motion': No such file or directory
mv: cannot stat `Config.zip_FILES': No such file or directory


thanks for the helpers

This happens when packages are named with a space in the title.  There are three easy options:

1:  Open nautilus and rename the file, replacing the space with an underscore.
2:  Enter the file name as "Motion\ Config.zip..." where \ indicates a space.
3:  In a terminal, enter "sudo nautilus" in a terminal, and open a second window.  Navigate to the folders you're looking for, drag and drop.  Close both of these nautilus window's when you're done with them, as you're using them as root, and can break things.

---

### Post by nouraldin on 2008-09-11
hi and thanks for the help ,
i used the first way and aded to the downloaded zip file as asked and to the extracted file of it ,

here is the downloaded pakage name:
 /home/nour/Desktop/Motion_Config.zip

and here it is after the extract:
/home/nour/Desktop/Motion_Config

and i wrote in the terminal :
 sudo mv ~/Desktop/Motion_Config.zip/etc/motion/

but again i have an error:
mv: missing destination file operand after `/home/nour/Desktop/Motion_Config.zip/etc/motion/'
Try `mv --help' for more information.

i didn't use the 2 and the 3 way u told me about coze they seem to me a little complex to understand ,
i am from Israel it is a little bit hard for me ,

:)

---

### Post by SkonesMickLoud on 2008-09-11
> **nouraldin said:**
> hi and thanks for the help ,
i used the first way and aded to the downloaded zip file as asked and to the extracted file of it ,

here is the downloaded pakage name:
 /home/nour/Desktop/Motion_Config.zip

and here it is after the extract:
/home/nour/Desktop/Motion_Config

and i wrote in the terminal :
 sudo mv ~/Desktop/Motion_Config.zip/etc/motion/

but again i have an error:
mv: missing destination file operand after `/home/nour/Desktop/Motion_Config.zip/etc/motion/'
Try `mv --help' for more information.

i didn't use the 2 and the 3 way u told me about coze they seem to me a little complex to understand ,
i am from Israel it is a little bit hard for me ,

:)

You forgot a space:

 sudo mv ~/Desktop/Motion_Config.zip/etc/motion/

Should be:

 sudo mv ~/Desktop/Motion_Config.zip_FILES /etc/motion/

Also, you need to move the file ~/Desktop/Motion_Config.zip_FILES and not the actual .zip.

---

### Post by nouraldin on 2008-09-11
ok
it return one error less that's a good ,

it return's that error:
mv: cannot stat `/home/nour/Desktop/Motion_Config.zip_FILES': No such file or directory

---

### Post by SkonesMickLoud on 2008-09-11
> **nouraldin said:**
> ok
it return one error less that's a good ,

it return's that error:
mv: cannot stat `/home/nour/Desktop/Motion_Config.zip_FILES': No such file or directory

In a terminal enter:

```
ls ~/Desktop
```

And paste the results here.

---

### Post by nouraldin on 2008-09-11
here it is :

gspcav1-20071224                         Motion_Config
gspcav1-20071224.tar.gz                  Motion_Config.zip
motion_3.2.10.1-2.ubuntu.hardy_i386      nautilus-computer.desktop
motion_3.2.10.1-2.ubuntu.hardy_i386.deb

---

### Post by Partyboi2 on 2008-09-11
deleted

---

### Post by SkonesMickLoud on 2008-09-11
> **nouraldin said:**
>  gspcav1-20071224 Motion_Config

Sorry it too me so long to get back to you.  Looks like this is the file you want to copy.  Try this:

```
sudo cp ~/Desktop/gspcav1-20071224[COLOR=Red]_[/COLOR]Motion_Config /etc/motion
```Or:

```

sudo cp ~/Desktop/gspcav1-20071224\ Motion_Config /etc/motion

```

---

### Post by nouraldin on 2008-09-11
> **Partyboi2 said:**
> deleted

so what now??

---

### Post by nouraldin on 2008-09-11
> **SkonesMickLoud said:**
> Sorry it too me so long to get back to you.  Looks like this is the file you want to copy.  Try this:

```
sudo cp ~/Desktop/gspcav1-20071224[COLOR=Red]_[/COLOR]Motion_Config /etc/motion
```Or:

```

sudo cp ~/Desktop/gspcav1-20071224\ Motion_Config /etc/motion

```

it's OK,

say i tried both code's but they didn't work :(
the error it gave me : 
cp: cannot stat `/home/nour/Desktop/gspcav1-20071224 Motion_Config': No such file or directory

that OK i will keep trying other way's,
but if u have any suggestion i will be glad to hear about it ,
thank u for all the help:)

have a nice day

---

### Post by SkonesMickLoud on 2008-09-11
> **nouraldin said:**
> it's OK,

say i tried both code's but they didn't work :(
the error it gave me : 
cp: cannot stat `/home/nour/Desktop/gspcav1-20071224 Motion_Config': No such file or directory

that OK i will keep trying other way's,
but if u have any suggestion i will be glad to hear about it ,
thank u for all the help:)

have a nice day

Easiest way would be to do this:

```
sudo nautilus
```

Click "File" >> then "New Window"

Now you have 2 windows open, both of which should be in your /home/ folder.  In one of the windows, double click on your /Desktop/ folder.  This will have your folder.  Now, in the second window, type "/etc/motion/" in the location bar.  Drag and drop the file you're trying to move from the window containing the desktop folder into the window containing "/etc/motion/".

Close both windows.

GUI drag and drop at it's simplest.

---

### Post by nouraldin on 2008-09-12
> **SkonesMickLoud said:**
> Easiest way would be to do this:

```
sudo nautilus
```

Click "File" >> then "New Window"

Now you have 2 windows open, both of which should be in your /home/ folder.  In one of the windows, double click on your /Desktop/ folder.  This will have your folder.  Now, in the second window, type "/etc/motion/" in the location bar.  Drag and drop the file you're trying to move from the window containing the desktop folder into the window containing "/etc/motion/".

Close both windows.

GUI drag and drop at it's simplest.

ok i did that but how i can be sore that its working coze in the first time i pressed inter after i moved desktop folder and it gave me that error : 
** (nautilus:5722): WARNING **: Unable to add monitor: Operation not supported
Nautilus-Share-Message: Called "net usershare info" but it failed: 'net usershare' returned error 255: net usershare: cannot open usershare directory /var/lib/samba/usershares. Error No such file or directory
Please ask your system administrator to enable user sharing.

but then i tried again exactly as u said , but again how can i be sore that it works

:)

---

### Post by nouraldin on 2008-09-13
help
how can i be sore that it works.:confused:

---

### Post by SkonesMickLoud on 2008-09-13
Try running motion.

---

### Post by gusanto on 2008-11-26
Sory guys if I'm hijacking this thread.  I have similar question regarding motion.  I installed motion thru synaptic without a problem then I download the motion.conf file from here [http://infectedproject.wordpress.com...curity-system/]("http://infectedproject.wordpress.com...curity-system/").  I moved it to /etc/motion then unzip it there and replaced the original motion.conf file.
Then when I run "motion", it told me these:
> [0] Processing thread 0 - config file /etc/motion/motion.conf
[0] Unknown config option "minimum_gap"
[0] Unknown config option "ffmpeg_filename"
[0] Processing config file /etc/motion/thread0.conf
[0] Motion 3.2.9 Started
[0] Motion going to daemon mode


I don't if those are errors, or where the picture taken by my webcam stored? In the motion.conf, it says that the target will be stored in /Security so I created /Security directory in my home folder.  Even so, after running motion again, nothing has been stored in /Security folder. Do I miss something (or many things)?
Please show me how to make this think work, I'm so curious.
Thanks.

---

