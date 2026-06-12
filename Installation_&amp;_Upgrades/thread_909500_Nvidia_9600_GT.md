---
title: "Nvidia 9600 GT"
date: 2008-09-03
forum: Installation &amp; Upgrades
---

### Post by The Tactics on 2008-09-03
Hi, well finally managed to install Ubuntu. Next step install my GFX card! I've tried allsorts! Is it at all possible to install a driver for this card? If yes, Please let me know!

I'm desperate to give ubuntu a good workout!

Cheers

---

### Post by baggins on 2008-09-03
Have you checked the restricted drivers?
Go to :
**System > Administration > Restricted Drivers Manager**

 -- Jon

---

### Post by The Tactics on 2008-09-03
Yes it is empty.

---

### Post by baggins on 2008-09-03
Ok strange.
Try running this in a terminal, it ought to show the same result, but you never know :)
```
jockey-gtk -l
```
Also try to run
```
lspci |grep VGA 
```
And post the output.

You might also want to check this:
[http://ubuntuguide.org/wiki/Ubuntu:Hardy]("http://ubuntuguide.org/wiki/Ubuntu:Hardy")

-- Jon

---

### Post by tuxxy on 2008-09-03
As your card is so new it isnt able to recommend a driver for you, I think this post may help you

[http://ubuntuforums.org/showpost.php?p=4558708&postcount=37](http://ubuntuforums.org/showpost.php?p=4558708&postcount=37)

---

### Post by Kalith on 2008-09-03
I had problems installing 9600gt on ubuntu,i got it working though.GO to your system packages,search for nvidia untick anything to do with nvidia.GO download the 177.67 beta drivers.Take a note of the filename and its location and these commands.Right press Ctrl+Alt+F4 login with username password. Type sudo /etc/init.d/gdm stop now cd to the location of the driver ie cd /home/joe/desktop etc Then type./NVIDIA-Linux-X86-177.67-pkg1.run install it follow commands it should build its own kernel etc When you get back to screen type sudo /etc/init.d/gdm start.Now restart pc or press Alt+backspace.It took me a few attempts to get working,i solved it finally though.You will probably have to mess with xconfig later aswell like i did.

Good luck

---

### Post by The Tactics on 2008-09-04
Cheers I will try these things when I return from work! Will post to let you know!

---

### Post by Norwal on 2008-09-04
I had the same problem too and the fix was very easy. I followed Lantesh's fix at this link and was up and running.

[http://ubuntuforums.org/showthread.php?p=5722924#post5722924]("http://ubuntuforums.org/showthread.php?p=5722924#post5722924")


Good luck.

:lolflag:

---

### Post by cocopuffz on 2008-09-04
Ive had this card installed for a while now. I'm not sure if envy does it now, but I know for sure if you install the linux drivers from Nvidia's download site, it works.

a quick ref:

download the driver to your desktop
Drop into the CLI (cntrl + alt + f1) and log in.
kill x by going "sudo /etc/init.d/gdm stop"
then change directories (cd /home/yourname/Desktop)up to your desktop 
Then give the file the proper permissions chmod -x Desktop/Nvidia_filename.run

Then run the file "sudo sh Nvidia_filename.run"

It will compile the kernel... just go "yes, yes yes.."
Once that's done, you can either restart x by going
"sudo /etc/init.d/gdm start" or you can restart your pc by
going "sudo restart -r now" 

if all goes well, you're good to go.
If you arrive after reboot to a low res craptacular resolution
go back into CLI and go "gksudo displayconfig-gtk " and select your monitor in the list. Or go and select the plug and play one with the resolution you want. apply.. bam. Should be good to go.

---

### Post by The Tactics on 2008-09-04
tony@tony-desktop:~$ jockey-gtk -l
tony@tony-desktop:~$ lspci |grep VGA
01:00.0 VGA compatible controller: nVidia Corporation Geforce 9600 GT 512mb (rev a1)
tony@tony-desktop:~$ 

Baggins here is your reply. Cheers

Coco followed your guide and I'm stuck in low gfx mode. The last part returned the following error.

(gksudo:7626): GTK - Warning **: Cannot open display.

Thx

---

### Post by The Tactics on 2008-09-04
Norwal thx! that guide did the trick! Only one problem now. When I set my resolution to 1440 x 900 the desktop dosent extend fully across my monitor. Can anyone help me? I'm nearly there!!

---

### Post by The Tactics on 2008-09-04
ok resolved. For anyone else I did the following.

sudo nvidia-settings

Set resolution in the nvidia settings manually then saved the xorg file.

Hey presto!

CHEERS everyone! At last!!

---

### Post by Norwal on 2008-09-06
The Tactics, would you pls click on the Medal beside my post. It records your thank you to me. 

On and your welcome. :)

---

