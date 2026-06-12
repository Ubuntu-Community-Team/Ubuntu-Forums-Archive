---
title: "Post Installation Question...Plz Reply"
date: 2006-03-25
forum: Installation &amp; Upgrades
---

### Post by Dissel on 2006-03-25
[COLOR="DarkRed"]hi.....
i am a novice user of ubuntu.....just today i install ubuntu in my PC...
i have some question.....about this ubuntu 5.10....plz answer....

Question 1.
I am using GNU GURB VERSION 0.95.....and there i see 3 entries about ubuntu...here the details:-
Ubuntu,Kernel 2.6.12-9-386
Ubuntu,Kernel 2.6.12-9-386 (recovery mode)
Ubuntu,Kernel memtest86+
Other Operatings Systems: Windows NT/2000/XP (loader)

How can i remove the the entry "Ubuntu,Kernel memtest86+" without uninstalling/reformatting the system.....Is it possible to describe the comand or procedure ?

Currently i am using 6.5 GB partion with doubling my ram 512 MB as a swap....so i made it 7.8 GB partion for the ubuntu.....
so
Question 2. What is the Decent partion size[plz mention the size in MB/GB] leave for ubuntu installation ?

Question 3.
When i am adjusting my Screen Resoloution from (System-->Preferences-->Screen Resoloutions) it says that refresh rate is 85Hz....i think this is to high for my 17" Samusng CRT....i want to set it as 75hz or 65 hz....but there is no option....only 85Hz is available....how to configure this ? plz help

Question 4.
When i try to Add Application from (Application-->Add Application) a pop up box appered and ask my 
password.....after i putting the password there is nothing happen....
I think this is the way to install additional application/Operating system components from the ubuntu installation CD....if not ....then wher to go for such things?

Question 5.
When the installtion process going on .....the system ask me to give the root password for adminstration and also a user name and password after that....i entered the both info correctly....and now my question is when i am trying to log.....from the login/welcome screen....if i use the username as root with assigned password...the following message shows "THE SYSTEM ADMINISTRATOR IS NOT ALLOWED TO LOGIN FROM THIS SCREEN".....but if i login with my username with assigned password.....then it is absoloutly fine....why i can't log as root?

Question 6.
How to access the internt from ubuntu.....i have a ADSL connection and 2 LAN card installed in my system....one for Home Networking and another connect to DSL modem....when i am trying to use network features from (Systems-->Administration-->networking) it asks my password...and after putting the password nothing happen...

Question 7.
I have some setup(Linux package) of MP player in .rar and .tar extension in a CD-Rom....i wnat to install it....though i extract the file from .rar/.tar in the seperate folder....i,e c:/mp player or hda --> mp player...ok....now how i can install it to the ubuntu ?

Question 8.
How can directly launch comand prompt/terminal from ubuntu interface ?

sorry for my long question list.....it may disappoint many ppl....but i am really thankfull to those pepople who consider to show me light in above mention problem.....

Any link or forum post about those matter also welcome.....

Thank you all....plz response. [/COLOR]

---

### Post by Swab on 2006-03-25
8. Application > Accessories > Terminal

1. Open a terminal as shown above, type "sudo gedit /boot/grub/menu.lst"  Enter your user password. Find the section that looks like this:

title           Ubuntu, memtest86+
root            (hd0,1)
kernel          /boot/memtest86+.bin
boot

and delete it.  Save the file and close gedit.  Then back in the terminal type sudo "grub-install hd0"  Then reboot

5. I don't believe you were asked for a root password during install.  By default the root account is disabled in Ubuntu.  Instead we use the sudo command.

---

### Post by Bartender on 2006-03-27
Dissel -
Why would you want to dump the memtest option?  I don't think it's hurting anything.  They put it in there so you could test your RAM.

Looks a little complicated, but I did a quick search for "refresh" and came up with this...

[http://ubuntuforums.org/showthread.php?t=83973&highlight=refresh+rate](http://ubuntuforums.org/showthread.php?t=83973&highlight=refresh+rate)

My Ubuntu install is hanging right around 4.5 GB right now with Automatix added and a few other tweaks.  From that I'd guess 8 or 9 GB would be enuf for a modest Ubuntu project.


"Add Applications" is one way.  Have you tried Synaptic?  See if that works.

---

### Post by Buffalo Soldier on 2006-03-27
[QUOTE=Dissel]hi.....
i am a novice user of ubuntu.....just today i install ubuntu in my PC...
i have some question.....about this ubuntu 5.10....plz answer....

Question 1.
I am using GNU GURB VERSION 0.95.....and there i see 3 entries about ubuntu...here the details:-
Ubuntu,Kernel 2.6.12-9-386
Ubuntu,Kernel 2.6.12-9-386 (recovery mode)
Ubuntu,Kernel memtest86+
Other Operatings Systems: Windows NT/2000/XP (loader)

How can i remove the the entry "Ubuntu,Kernel memtest86+" without uninstalling/reformatting the system.....Is it possible to describe the comand or procedure ?[/QUOTE]
At the command line / terminal, enter this command:
```
sudo gedit /boot/grub/menu.lst
```
Comment out the entry that you do not wish to see during boot.
How to get to command line / terminal? *Please refer to question/answer 8.*
What is sudo? *Please refer to question/answer 5.*

[QUOTE=Dissel]Currently i am using 6.5 GB partion with doubling my ram 512 MB as a swap....so i made it 7.8 GB partion for the ubuntu.....
so
Question 2. What is the Decent partion size[plz mention the size in MB/GB] leave for ubuntu installation ?[/QUOTE]I don't really understand this question. Setting the size of your swap partition to double the size of your RAM is just right. About the rest of the partition for Ubuntu, I've personally installed it on a 5GB partition. Not sure what's the smallest size, but I think there's no maximum limit.

[QUOTE=Dissel]Question 3.
When i am adjusting my Screen Resoloution from (System-->Preferences-->Screen Resoloutions) it says that refresh rate is 85Hz....i think this is to high for my 17" Samusng CRT....i want to set it as 75hz or 65 hz....but there is no option....only 85Hz is available....how to configure this ? plz help[/QUOTE]
At the command line / terminal, enter this command:
```
sudo dpkg-reconfigure xserver-xorg
```
By choosing to answer in detail when asked about your monitor spec, you will be able to specify your monitor refresh rate.
How to get to command line / terminal? *Please refer to question/answer 8.*

[QUOTE=Dissel]Question 4.
When i try to Add Application from (Application-->Add Application) a pop up box appered and ask my 
password.....after i putting the password there is nothing happen....
I think this is the way to install additional application/Operating system components from the ubuntu installation CD....if not ....then wher to go for such things?[/QUOTE]What do you man by nothing happened? Not a window popped up? Nor an error message?

How about trying to go to: System -> Administration -> Synaptic Package Manager.

[QUOTE=Dissel]Question 5.
When the installtion process going on .....the system ask me to give the root password for adminstration and also a user name and password after that....i entered the both info correctly....and now my question is when i am trying to log.....from the login/welcome screen....if i use the username as root with assigned password...the following message shows "THE SYSTEM ADMINISTRATOR IS NOT ALLOWED TO LOGIN FROM THIS SCREEN".....but if i login with my username with assigned password.....then it is absoloutly fine....why i can't log as root?[/QUOTE]
Please read about sudo  -->  [https://wiki.ubuntu.com/RootSudo](https://wiki.ubuntu.com/RootSudo)

[QUOTE=Dissel]Question 8.
How can directly launch comand prompt/terminal from ubuntu interface ?[/QUOTE]
Applications -> Accessories -> Terminal

---

### Post by Dissel on 2006-04-08
[COLOR="DarkRed"]Thanks from replying......
but ....

Under the Administaration menu.....nothing respond.....except device manager and printer.
Expl:-> Say....

When i click on the Networking field......a pop-up asking for my Password....and then a tab appear in the taskbar...saying"Starting Networking....." and after 2-3 sec it disappear.....

same happen as when i try to open a user and groups.....

The whole thing is no item under System--->Adminstartion menu never ever respond...no error msg...nothin....

I create diffrent users.....and same was happend from those A/C also.

and Synaptic Package Manager not respond....as it is under the Administration menu.....:confused: [/COLOR]

---

### Post by xenmax on 2006-04-08
Perhaps you did an expert install?
Try this thread: [http://ubuntuforums.org/showthread.php?t=146859](http://ubuntuforums.org/showthread.php?t=146859)

---

