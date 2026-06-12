---
title: "Nvidia graphics drivers (.run) file want to open in a text editor, how to install?"
date: 2013-09-27
forum: Installation &amp; Upgrades
---

### Post by Crinkle on 2013-09-27
Double clicking opens the run file with gedit (a text editor)

Web says tick "run as application from settings", but it still opens with a text editor.

Web also says select "run from terminal" but there is no option for that.

How to install these?

---

### Post by Crinkle on 2013-09-27
Update: Tried following this: [http://www.ehow.co.uk/how_6769624_check-graphics-driver-ubuntu.html](http://www.ehow.co.uk/how_6769624_check-graphics-driver-ubuntu.html)

But cant, as theres no "Administration" in the system settings.

Same problem, when following this link too: [https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia](https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia)

Are these links out of date? Or is something wrong with my linux?

---

### Post by deadflowr on 2013-09-27
First off, did you try installing the drivers through Ubuntu, rather then trying the run file?

Secondly, the file needs to be marked as executable
In a terminal
```
chmod + x filename
```
the + x will make it executable.
change filename to the path to the run file.

Back to question # 1 though, it is easier to install the drivers through Ubuntu's driver management program(Additional Drivers) then the run file.
[https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia](https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia)

Additionally, if using 12.10, or 13.04 the additional drivers are inside the program software sources or software and updates.(not software updater)

---

### Post by Crinkle on 2013-09-27
I downloaded the drivers from the website, I have no idea how to do your step one. Where is the driver management program? I checked that link you sent but it said Nouveau drivers are no good for 3d and a lot of my games are 3D. So they are no good, also further down it again says I should go into "administration" in system are which is not there.

I also cannot try your second solution because I've no idea how it works. The file is downloaded in home/downloads so do i type:

chmod +x home/downloads/(filename)

?

EDIT: nope that doesnt work with either backslashes or forward slashes, what the hell?

---

### Post by Crinkle on 2013-09-27
Ok i used the software and updates feature in the system settings to find a page with driver information, and i changed and downloaded a NVIDIA driver instead of whatever weird driver it was using. It didn't error, didn't break anything, didn't bring up a message saying anything installed correctly, and it most importantly DIDNT WORK.

I used the unformation on this page: [http://askubuntu.com/questions/23238/how-can-i-find-what-video-driver-is-in-use-on-my-system](http://askubuntu.com/questions/23238/how-can-i-find-what-video-driver-is-in-use-on-my-system)

to try the lshw -c video command.

It says I'm still using the Nouveau crao. How do i make it change?

---

### Post by deadflowr on 2013-09-27
By default, you should be in /home/username folder in a terminal (the ~ symbol is where you are and means home/username).
If the file is in Downloads move into Downloads with cd(change directory)
```
cd Downloads
```
this will move you into the downloads folder.
Then simply do the chmod + x command with the file name.
Example (Do not copy and paste this as it is wrong for you, change the file name to yours)
```
chmod + x Nvidia-something-something.run
```

Added: The backslash before home is super important. home without it does not exist.
home is a sub folder of root (/). So typing home/stuff(or whatever) will result in nothing happening, where as /home/stuff(again whatever) will do something.

---

### Post by oldos2er on 2013-09-28
> **Crinkle said:**
> Ok i used the software and updates feature in the system settings to find a page with driver information, and i changed and downloaded a NVIDIA driver instead of whatever weird driver it was using. It didn't error, didn't break anything, didn't bring up a message saying anything installed correctly, and it most importantly DIDNT WORK.

I used the unformation on this page: [http://askubuntu.com/questions/23238/how-can-i-find-what-video-driver-is-in-use-on-my-system](http://askubuntu.com/questions/23238/how-can-i-find-what-video-driver-is-in-use-on-my-system)


That info is outdated.

Can you tell us which Nvidia card you're using?

This command will install the proprietary Nvidia drivers from the repositories ```
sudo apt-get update && sudo apt-get install nvidia-current
```

---

