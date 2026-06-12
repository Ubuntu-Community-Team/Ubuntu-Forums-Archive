---
title: "Permission issues. Thanks for the help."
date: 2007-05-12
forum: Installation &amp; Upgrades
---

### Post by Jay_in_TN on 2007-05-12
NOTE: this thread has been edited, including the title. The problems have been resolved and thanks to the great people of this forum for their patience and their responses!


Man--I put Ubuntu on my laptop as a second OS. What a giant problem. First of all Fiesty ran fine from the Live CD, but wouldn't connect to my wireless network after install. So I reinstalled Ubuntu using Edgy on an Ext3 partition. Now it connects fine....but I no longer have permission to write anything to my hard drive while in Ubuntu. What a total ****-around-trip. I am soooooo pissed. I have tried to change the owner using SUDO but it keeps giving me errors and not changing. Since I defaulted EVERYTHING in the setup..this should not be necessary.
Can anyone tell me how to change the permissions so I can actually use the computer? Or at least tell me what format type the partition wants so I can reinstall it without it causing me all this trouble?

I am trying. I have an open mind.I have been intalling and reinstalling for 4 hours now and still don't have a working version of an operating system.
Jay

---

### Post by eentonig on 2007-05-12
Linux doesn't need to take over the desktop world. 

Now, can you the specs of your machine? 

Why installed an older version and not troubleshoot your original Feisty install? Did you install over your existing Feisty or did you wipe the partition and did a fresh install?

What/where do you want to write?

---

### Post by kelvin spratt on 2007-05-12
you need to go for a walk and clear your mind first refomat the partition and do a fresh install if it found your wireless network on live cd then it should on install i use fiesty make sure its the latest version and the ISO has been burned using a high quality program as some progs do not write the image correctly as it is laid out on the original Iso after install if you have a problem come back here for help? don't get stessed out just chill the people will sort you out

---

### Post by bapoumba on 2007-05-12
@ Jay_in_TN: we all get frustrated at time, when things do not work out, when we do not understand what's going on, when we experiment new environments, new languages.

If you need help, you'll get helped here. There are lots of very knowledgeable users around, very dedicated.
If you just wanted to vent, well, you've done it.

Now keep in mind that we won't let flames take over.

---

### Post by sandman55 on 2007-05-12
When you download there is a checksum to check to see that your download is not corrupt and after you burn your disk you should click on "check disk" when you put in your live CD you can still do that now. If you have any problems and dont want to download or burn again you can get free disks [Here](https://shipit.ubuntu.com/)

---

### Post by Jay_in_TN on 2007-05-12
First of all, thanks for trying to help me.
And yes--I am fairly pissed at the situation.
Fiesty worked fine on one desktop that I have. Wouldn't work at all on the other one. Worked in live mode on my laptop, but the wireless wouldn't work after install. I went back and forth from live to installed version and the driver for the wireless card was different between versions. WTF? I am happy to use Edgy. I would be happy to reinstall it. And yes--all the installs were clean installs with reformatted drives.
It looks like the problem is that I set up the partition as an EXT3 partition. It seems that if you install edgy onto an EXT3 partition you don't have permission to your hard drive once you boot up. I can't write or copy anything to any directory.
So--first question--what file system is the preferred file system for edgy?
As for Feisty--I don't have too much good to say about it at this point. It seems very, very buggy.
Right now--if I can just reinstall edgy to the correct type of file system I will probably be able to get going.

Also--I created a FAT32 partition so Windows and Edgy could share a drive, but that drive is not even visible in edgy. What is THAT about?

Thanks again for offering to help. I am enthusiastic about Linux and I like Ubuntu--but tonight it has kicked my *** and really taken me for a ride.

Jay

BTW--I am very familiar with proper etiquette for forum use. And yeah--I did vent for a minute there. Reached the temporary end of my rope. But that post (or this one) was not intended to be a flame. I am not even sure it qualifies as a flame. Just an angry and desperate cry for help.

---

### Post by bapoumba on 2007-05-12
ext3 is the correct file system for ubuntu, regardless of release.

What is the output to 
```
groups
```
from a terminal (> Accessories > Terminal).
Remember that you have full privilege to you /home, but you have to get admin privilege to access the system. Please read:
[https://help.ubuntu.com/community/RootSudo]("https://help.ubuntu.com/community/RootSudo")

for your fat32 partition, what is the output to:
```
cat /etc/fstab
sudo fdisk -l
```
(you may not be able to run the second commend until your user gets granted with admin privileges, if thats the problem).

---

### Post by kelvin spratt on 2007-05-12
they all us ext3 for my setup i used edgy never had write permission problems for me also after a couple of updates ntfs3g is installed this reads the ntfs windows file system, you can then either download automatix or download the latest update from the NTFS 3g site and get full read and write to NTFS, or
fat i would not recommend the fat system its very hard on the hard drive and shortens the life of the drive i hope this helps or am i just rabbiting on

---

### Post by Jay_in_TN on 2007-05-12
Thank you for your reply. It is clear you are trying to help me. However--I did not understand either one of your suggestions. I guess they are just above my head.
Which sort of leads me back where I started. I am an IT professional for a living. I work with Educational Technology. I am a very good Windows technician. But Ubuntu is really killing me right now. I can't believe that after an install the primary user would not have access to the hard drive without having to change code. That is just not right.
I am gonna look at your suggestions again in the morning after a night's rest. Perhaps I will understand them then. It seems that you are talking in programming code and frankly I have no idea what you suggested. I do, however, sincerely thank you for your effort to assist me.
I will just try again in the morning.
BTW--this happened because I installed edgy and all looked great. I went to the Internet and immediately got flagged for not having Flash installed. Very surprising that Flash doesn't install automatically, but I downloaded the tar file and tried to install it. It saved to my desktop, but I couldn't change directory to desktop from terminal to get to the file. (tried a bunch of combinations of cd... all to no avail). So I tried to drag and drop the extracted folder onto the root to install from there. But I had no permissions at the root. Also--tried to modify the menu.lst to put Windows at the top of the list but again, I did not have permission to modify. That just really does not make sense to me. The primary user should have access to the hard drive to do such things as install flash and modify the menu.lst. I am just baffled.

Anyway--thanks again for trying to help. I am just gonna go to bed and worry about it later. 
I am at a total loss.

Jay

---

### Post by bapoumba on 2007-05-12
Hey Jay, sweet dreams.

Linux security issues are handled very differently from Windows.
As a regular user, you cannot perform administrative task that require admin rights, for security reasons (this is one of the reasons there are few viruses on Linux, because they can yank your user /home but nothing more, not the root file system. Well, being over simplistic here).

You probably need to get more infos on the file system, permissions and such.

Please read here:
[https://help.ubuntu.com/7.04/newtoubuntu/C/index.html]("https://help.ubuntu.com/7.04/newtoubuntu/C/index.html")
Specially the last link ;)

edit: flash, you'll worry about later on. Get the fundamentals first.
I'm not an IT pro, never had any classes about computers or anything like that. I'm a basic user, you can make it :)

---

### Post by badboy_24u on 2007-05-12
[SIZE="4"]Tip During installation...

Make sure that your Ram is in good condition and not too hot.Common installation problems occur when the ram is too hot then hangs up. So, i suggest you try installing it after letting your pc rest for while.

Second most common problem is the electricity. Make sure that your electricity is very stable. Cause, unstable flow of electric current would make your system behave mysteriously causing installation errors base on my experience.

Last, do a bit of sacrifice and just install 6.06. It's the most stable and the apps that aren't working on edgy and feisty definitely works well on 6.06ver. 

Note: Frequent formatting of hard disk can shorten the life of it. Format at your own risk... Good luck:popcorn:  [/SIZE]

---

### Post by sandman55 on 2007-05-12
Hi Jay I thought I saw this command in this thread but I must be thinking of another thread.
Being a windows user if you use the command ```
gksudo nautilus
``` in terminal or alternatively Alt + F2 and type gksudo nautilus in the prompt.
You can then wander around in a GUI as you would in windows and you will be in root (you will see it at the top left of the window) you can right click on files as you would in windows and when you close the window you will be out of root

---

### Post by Jay_in_TN on 2007-05-12
Thanks for the help. The "learning about Ubuntu" page was a lot more elementary than any assistance I would need. I did read through the information to see if I could learn anything, but I already knew all of that stuff.
I tried again with the flash install and after putting the files in the /home directory it was a simple procedure.
However--I would still like to edit the menu.lst in grub. Could someone please explain to me how I can get permission to edit that file? I just want to put windows at the top of the list.


Note: I did not see the above post regarding sudo until just now. I will try it now

Thanks,
Jay

---

### Post by Jay_in_TN on 2007-05-12
gksudo nautilus!!!!!!
That is the answer!!!!
Thanks so much.
Clearly I needed to go to sleep. Today I got flash installed and edited the menu.lst in less than half an hour, while watching TV.
Thanks guys and sorry I was so crabby last night. It was a crappy set of problems.

Jay

---

### Post by bulldog on 2007-05-12
```
gksudo gedit /boot/grub/menu.lst
``` will do the trick :) 
Don't think you did understand everything about being a user and being root.

Basically you only can do about anything within your /home folder.
Outside your /home,you can't get anything done without root permissions,which you get by using the sudo command.
If you want to use a application with a GUI,you better use gksudo instead of sudo.

---

### Post by Jay_in_TN on 2007-05-12
I understand permissions just fine. I have been administrating Novell servers and NWadmin for years. I have a fairly strong grasp of permissions, users, and groups. However, I have used Fedora, openSUSE, Linspire, Mandrake, and Ubuntu. Ubuntu is the first OS I have seen that doesn't allow access to the hard drive when logged in as the primary (admin/root) user. I did not get that I had to enter a special command to provide permission to the file system when logged in as the top-level user. I totally understand the concept and I see where it can improve security, however, it seems perhaps just a bit "going overboard."
Anyway--now that I understand that I can hit alt+F2 and then type the gksudo nautilus command to provide access I am able to use the OS as I need to.
In other linux OS's you sometimes have to log out and back in as "root" to accomplish the same thing, so I suppose the sudo route is actually faster and easier.....if it were obvious.

Anyway--thanks for the help. I may decide to intsall Feisty again and trouble shoot why the wireless wont work. It works fine in Edgy, but it is harder to choose between available networks.

BTW--what is the "GK" in front of the sudo command?

Jay

---

### Post by maddog39 on 2007-05-12
> **Jay_in_TN said:**
> NOTE: this thread has been edited, including the title. The problems have been resolved and thanks to the great people of this forum for their patience and their responses!


Man--I put Ubuntu on my laptop as a second OS. What a giant problem. First of all Fiesty ran fine from the Live CD, but wouldn't connect to my wireless network after install. So I reinstalled Ubuntu using Edgy on an Ext3 partition. Now it connects fine....but I no longer have permission to write anything to my hard drive while in Ubuntu. What a total ****-around-trip. I am soooooo pissed. I have tried to change the owner using SUDO but it keeps giving me errors and not changing. Since I defaulted EVERYTHING in the setup..this should not be necessary.
Can anyone tell me how to change the permissions so I can actually use the damn computer? Or at least tell me what format type the partition wants so I can reinstall it without it causing me all this trouble?
God I am soo pissed at this crap at the moment!!!!
I assure you---Linux is nowhere near taking over the desktop envrionment from Windows. I am trying. I have an open mind. But this is beyond irratating. I have been intalling and reinstalling for 4 hours now and still don't have a working version of an operating system. Not even near ready for Prime Time.
Jay
I have no sympathy for you, seriously. You come on here cussing your mouth off, and blaming all these problems on linux. When the reality is that most of the time, whatever the problem is, was your own fault. I dont think coming on here agrivated is going to get you anywhere and was annoying the heck out of me just reading it. In windows, wireless setup is a nitemare and I hate doing it everytime with my parents' laptops. With your wireless on feisty, the only thing you probably had to do was go into network manager and enable the connection. Thats probably all you had to do. Also, your filesystem doesnt get locked for no aparent reason or because you reinstalled the OS. You had to have done something to it.

---

### Post by PhatStreet on 2007-05-12
> **Jay_in_TN said:**
> Thank you for your reply. It is clear you are trying to help me. However--I did not understand either one of your suggestions. I guess they are just above my head.
Which sort of leads me back where I started. I am an IT professional for a living. I work with Educational Technology. I am a very good Windows technician. But Ubuntu is really killing me right now. I can't believe that after an install the primary user would not have access to the hard drive without having to change code. That is just not right.
I am gonna look at your suggestions again in the morning after a night's rest. Perhaps I will understand them then. It seems that you are talking in programming code and frankly I have no idea what you suggested. I do, however, sincerely thank you for your effort to assist me.
I will just try again in the morning.
BTW--this happened because I installed edgy and all looked great. I went to the Internet and immediately got flagged for not having Flash installed. Very surprising that Flash doesn't install automatically, but I downloaded the tar file and tried to install it. It saved to my desktop, but I couldn't change directory to desktop from terminal to get to the file. (tried a bunch of combinations of cd... all to no avail). So I tried to drag and drop the extracted folder onto the root to install from there. But I had no permissions at the root. Also--tried to modify the menu.lst to put Windows at the top of the list but again, I did not have permission to modify. That just really does not make sense to me. The primary user should have access to the hard drive to do such things as install flash and modify the menu.lst. I am just baffled.

Anyway--thanks again for trying to help. I am just gonna go to bed and worry about it later. 
I am at a total loss.

Jay
As an IT professional you would allow any user to modify system software, install what they want, and edit boot menus? No offense, but that's just asking for disaster.

---

### Post by jfinkels on 2007-05-12
> **maddog39 said:**
> I have no sympathy for you, seriously. [etc...]

Then don't post here. We're trying to help, not inflame, problems.

I think the 'gk-' comes from GTK toolkit, which is the graphical toolkit that most of the applications in the GNOME desktop use. It's a GTK front-end for sudo, as it says in gksudo's man page:
```
man gksudo
```

As for wireless problems, make a new thread, describe your problem very clearly, and tell us what kind of wireless card you have. You may have to install a driver.

---

### Post by bapoumba on 2007-05-12
For more on graphical sudo:
[http://psychocats.net/ubuntu/graphicalsudo]("http://psychocats.net/ubuntu/graphicalsudo")

---

### Post by Jay_in_TN on 2007-05-12
**"As an IT professional you would allow any user to modify system software, install what they want, and edit boot menus? No offense, but that's just asking for disaster."**

No--I would never do that. What you posted is not related to the issue I was having. I was referring to logging into the OS as the TOP-LEVEL user and THEN not having access to file systems and boot menus. I have never heard of such a thing. The solution has been provided and the issue is now moot. Ubuntu has it's way of doing it. It works. I was just a little put off by the top-level user not having access to the files. Never seen that in any version of an OS. That is all I was saying. The "gksudo nautilus" command addressed the issue perfectly.

As for wireless: That guy that was trying to start a flame war does not give me enough credit nor did he bother to read the thread before attacking me.

As already stated: I first booted up using the Feisty Live cd and the wireless worked fine. In fact, everything worked so well that I installed Feisty. But when booting up to Feisty the wireless would not get an IP address from the DHCP server (linksys router). Obviously I used the network manager to adjust settings. I messed with the properties of the wireless card repeatedly and booted back and forth from Live to the HD. I chose my wireless network and my neighbors wireless network and was unable to get a valid IP either way. Interestingly--the driver (linksys wireless card for laptop) was orinoco_cs in the Live version but was a different driver in when booting from the HD.

Anyway--I kept connecting and reconnecting and changing and changing and finally gave up and installed Edgy, which works fine.

If I decide to fight this issue again I will start a new thread and seek assistance.

BTW--I attempted to change the thread title but it won't change. I made a point of thanking everyone for their assistance throughout this thread. I retracted my anger as soon as I vented the first time. Clearly I was not out to dog Ubuntu or start a flame war. There is always someone trolling a forum looking for a fight, no matter the forum. I belong to guitar repair forums and caving forums and it is the same thing. There is always "that guy."

So anyway--thanks again for all the help. The good things I had read about user forums was my primary motivation for moving to Ubuntu. I still like openSUSE quite a lot, but I prefer the forums for Ubuntu and also the relative small size of the OS.

Jay

---

### Post by bapoumba on 2007-05-12
> **Jay_in_TN said:**
> [B]
BTW--I attempted to change the thread title but it won't change. 
Go back to your first post > edit > go advanced > you'll have access to the title. If you want to change the main title, let me know.

---

### Post by jfinkels on 2007-05-12
I think what's a bit confusing in this situation is that you're calling the user you created when you installed Ubuntu the "top-level user". As it is in Ubuntu (and as I think you understand now :D), this first user isn't really a "top-level" user, more just a regular old user with sudo privileges (i.e. in the /etc/sudoers file).

Let us know if you need any more help on anything! We love to see people succeed.

---

### Post by Jay_in_TN on 2007-05-12
The main title was written when I was very frustrated. I do not hate Linux at all and that title will not help anyone else who may have the same issue with permissions. I think that "Permission Issues" or "Accessing File System Issues" or something similar might be more helpful for someone searching the forum in the future.

Thanks again for everything.

Jay

---

### Post by bapoumba on 2007-05-12
Done.

And you're welcome.

---

### Post by pxa270 on 2007-05-12
> **Jay_in_TN said:**
> 
I was referring to logging into the OS as the TOP-LEVEL user and THEN not having access to file systems and boot menus. I have never heard of such a thing. The solution has been provided and the issue is now moot. Ubuntu has it's way of doing it. It works. I was just a little put off by the top-level user not having access to the files. Never seen that in any version of an OS. 

As Jfinkels already pointed out, you were NOT logged in as the "top-level user", which is what seemed to have gotten you confused. I'm not sure if you're already aware of it now, but your default user account in Ubuntu is not "root".

Btw, permissions in Apple's Mac OS X work exactly like in Ubuntu, and has for many years.

---

### Post by Jay_in_TN on 2007-05-12
OK then--I must ask--and sorry to beat a dead horse here because as mentioned--I have solved my particular set of problems.
But in other Linux distributions I can log in as "root" and then I have total administrative rights.
If the first user created in Ubuntu has access to Sudo but is not a top-level user--then how would someone log in as "root?"

As far as I can see you can't. It is not how Ubuntu works. It seems that the "first user created" is, in fact, the top-level user, and has access to gksudo which in turn allows administrative access.

Am I missing something? Is there a top-level user that is accessable in Ubuntu? In comparison--using Fedora or openSUSE I can always log in as "root" and then I have admin rights. As far as I can tell--in Ubuntu the "first created user" is the primary, top-level user, and does not have admin rights until activating the gksudo command.

Again--am I missing something?

Jay

---

### Post by pxa270 on 2007-05-12
I suggest you read this: 
[https://help.ubuntu.com/community/RootSudo]("https://help.ubuntu.com/community/RootSudo")

You can enable root login with "sudo passwd root", but that's not recommended, so you if you did you should disable it with "sudo passwd -l root".

---

### Post by bulldog on 2007-05-12
Nope you don't miss anything.
The reason is that it's safer to not log in as a root,but you can make a root terminal session as long as you want by typing sudo -s and provide your password.
Also gksudo nautilus will do that in a graphical manner.

But most user have enough using sudo in a command to get things done.
In that way you have root privileges for about 15 minutes,then you have to provide the password again.

I know SuSe and Fedora have a root account,I worked with them too.
But I use ubuntu for about a year know,and I don't really miss it.:)

---

