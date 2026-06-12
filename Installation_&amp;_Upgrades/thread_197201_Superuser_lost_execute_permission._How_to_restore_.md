---
title: "Superuser lost execute permission. How to restore his permission?"
date: 2006-06-15
forum: Installation &amp; Upgrades
---

### Post by laodan on 2006-06-15
This is a follow-up on a thread that I launched yesterday[ "No profile for user ... found" at booting.]("http://www.ubuntuforums.org/showthread.php?t=196862")

Following the advise of xzee I added a new user (laodan2) and thus could enter my system under this new user.
I checked the permissions on my initial laodan (superuser) home folder and discovered that execute permissions had vanished (???). This explains why I could not boot the system any longer. 

The tricky question now. Can I can restore the execute permission to my initial laodan home folder (superuser on my system) from within my new user account as laodan2 ? 

Thanks.

---

### Post by laodan on 2006-06-15
From my browsing around I see nobody addressing the question I'm stuck with. It seems as if there were[COLOR="Red"] no way to restore the execute permission to the initial home folder (superuser home) from within a new user account.[/COLOR]

Could someone please confirm or infirm that point.

I have a second HDrive with all my data so a complete re-install is not the end of the world, I would just like to know if there is no easy command that could avoid me the hassle to reinstall and all the customization that goes with it.

Thanks.

---

### Post by zxee on 2006-06-15
Setting permissions is a tricky business, but you should be able to do it. I was hoping that someone more expert with this issue would take the ball-however if I were you I might try reading some of the online documents on this. This is just one: [http://www.perpetualpc.net/perms_poss.html](http://www.perpetualpc.net/perms_poss.html)
To just be able to access your accounts in an admittedly quick and dirty way (meaning you could open yourself to security risks) type sudo chmod ug+x on the directory or files you want access to. That will inable execute.

---

### Post by laodan on 2006-06-15
[QUOTE=zxee]Setting permissions is a tricky business, but you should be able to do it. I was hoping that someone more expert with this issue would take the ball-however if I were you I might try reading some of the online documents on this. This is just one: [http://www.perpetualpc.net/perms_poss.html](http://www.perpetualpc.net/perms_poss.html)
To just be able to access your accounts in an admittedly quick and dirty way (meaning you could open yourself to security risks) type sudo chmod ug+x on the directory or files you want access to. That will inable execute.[/QUOTE]

Thanks zxee for your following my adventures. (Sorry I mixed up the x and z position in an earlier post)

**I tried a myriad of commands, here some of the most interesting ones:**

The one you advised:
[COLOR="Blue"]sudo chmod ug+x /home/laodan[/COLOR]
gives [COLOR="Blue"]Sorry. try again[/COLOR]

One that was advised on [http://ubuntuforums.org/showthread.php?t=91455]("http://ubuntuforums.org/showthread.php?t=91455")
[COLOR="Blue"]sudo chmod 755 /home/laodan[/COLOR]
password:
gives [COLOR="Blue"]Sorry, try again.[/COLOR]


disabling the root account as advised on [http://www.linuxquestions.org/questions/showthread.php?p=2277136#post2277136]("http://www.linuxquestions.org/questions/showthread.php?p=2277136#post2277136")
[COLOR="Blue"]passwd -l root[/COLOR]
gives [COLOR="Blue"]permission denied[/COLOR]
After reading some commentaries on
[http://www.linuxtoday.com/news_story.php3?ltsn=2006-06-05-013-26-RV-DB-DT-0001](http://www.linuxtoday.com/news_story.php3?ltsn=2006-06-05-013-26-RV-DB-DT-0001)  
I had some hope about disabling the root account... 
*[COLOR="DarkOrange"]I installed the last version Ubuntu on a box to test its appropriateness as a kiosk machine. I was most impressed with its default behavior of disabling the root account by default, then giving all users membership in sudoers. Then I checked, and by default, it allowed *any* user I created to enable the root account and change the root password. [/COLOR]*


**In conclusion, it seems the sudo command is not accessible in my circomstance. **
This seems logical to me, for, sudo is for the superuser and **my superuser home forlder lacking an execution permission** the sudo becomes non-executable.

As I wrote earlier *"It seems as if there were [COLOR="Red"]no way to restore the execute permission to the initial home folder (superuser home) from within a new user account.[/COLOR]"*

So it seems that I'm dreaming against all logic that an angel could send me a magical command that would restore my superuser's home folder permissions to their old status from within the account of my new user. 
I'm starting to think seriously to restart an install from sratch... but this is embarassing to say the least. Install is one things customization thereafter is a totally different thing.

Thanks zxee for trying to help so far.

---

### Post by meng on 2006-06-15
The use of sudo should work independently of whether the root account password is enabled. The "Sorry try again" message should only occur with an incorrect password. Stupid question: are you using your user password with sudo (as you should be)?

---

### Post by laodan on 2006-06-15
[QUOTE=meng]The use of sudo should work independently of whether the root account password is enabled. The "Sorry try again" message should only occur with an incorrect password. Stupid question: are you using your user password with sudo (as you should be)?[/QUOTE]

The root password was enabled at installation attributing automatically superuser character to the person making the install. 
To my understanding sudo can only answer to the root password. 

My problem is not related to passwords but well to the home folder of the superuser that, for whatever bizarre reason, lost its execution permission. 

My problem is thus[COLOR="Red"] how to change the permissions of the superuser's home folder from within the account of a new user.[/COLOR]

Check the responses I get from the execution of the following commands:

[COLOR="Blue"]laodan2@ubuntu:~$ ls -l /bin/bash .bashrc
-rw-r--r-- 1 laodan2 laodan2   2227 2006-06-14 22:32 .bashrc
-rwxr-xr-x 1 root    root    664084 2006-04-21 17:51 [/COLOR][COLOR="Lime"]**/bin/bash**[/COLOR]

[COLOR="Blue"]laodan2@ubuntu:~$ ls -l /home
total 8
drw-r--r-- 59 laodan  laodan  4096 2006-06-14 18:36 laodan
drwxr-xr-x 21 laodan2 laodan2 4096 2006-06-15 17:00 laodan2[/COLOR]

[COLOR="Red"]drw-r--r-- 59 laodan[/COLOR] (superuser)
Owner: Read Write
Group: Read
Others: Read

[COLOR="Red"]drwxr-xr-x 21 laodan2[/COLOR] (new user)
Owner: Read Write Execute
Group: Read Execute
Others: Read Execute

---

### Post by zxee on 2006-06-15
[QUOTE=laodan]The root password was enabled at installation attributing automatically superuser character to the person making the install. 
To my understanding sudo can only answer to the root password. 

My problem is not related to passwords but well to the home folder of the superuser that, for whatever bizarre reason, lost its execution permission. 

My problem is thus[COLOR="Red"] how to change the permissions of the superuser's home folder from within the account of a new user.[/COLOR]

Check the responses I get from the execution of the following commands:

[COLOR="Blue"]laodan2@ubuntu:~$ ls -l /bin/bash .bashrc
-rw-r--r-- 1 laodan2 laodan2   2227 2006-06-14 22:32 .bashrc
-rwxr-xr-x 1 root    root    664084 2006-04-21 17:51 [/COLOR][COLOR="Lime"]**/bin/bash**[/COLOR]

[COLOR="Blue"]laodan2@ubuntu:~$ ls -l /home
total 8
drw-r--r-- 59 laodan  laodan  4096 2006-06-14 18:36 laodan
drwxr-xr-x 21 laodan2 laodan2 4096 2006-06-15 17:00 laodan2[/COLOR]

[COLOR="Red"]drw-r--r-- 59 laodan[/COLOR] (superuser)
Owner: Read Write
Group: Read
Others: Read

[COLOR="Red"]drwxr-xr-x 21 laodan2[/COLOR] (new user)
Owner: Read Write Execute
Group: Read Execute
Others: Read Execute[/QUOTE]

I'm not sure if you're saying you created a root account when doing the ubuntu install or not? Normally root is disabled on ubuntu. So please try the sudo command with your user password-that is the way sudo is suppose to work.
And if you do have a root account enabled then you wouldn't use sudo (with root's password) to become root; you would use su.
So just for clarity, if you have a root account on your system typing su will ask for the root password. On ubuntu normally the root account is disabled and the user gains administrative privledge by typing sudo with the command and then entering the user password when the system asks for a password.

---

### Post by laodan on 2006-06-15
[QUOTE=zxee]I'm not sure if you're saying you created a root account when doing the ubuntu install or not? Normally root is disabled on ubuntu. So please try the sudo command with your user password-that is the way sudo is suppose to work.[/QUOTE]

It is confusing and the confusion comes from the sentence in my post n#6: [COLOR="Orange"]"The root password was enabled at installation attributing automatically superuser character to the person making the install.
To my understanding sudo can only answer to the root password. "[/COLOR]

I read a [post in Linux Today by Dennis Soper]("http://www.linuxtoday.com/news_story.php3?ltsn=2006-06-05-013-26-RV-DB-DT-0001") Jun 6, 2006  saying:
[COLOR="Orange"]"My Favorite Ubuntu Feature....
I installed the last version Ubuntu on a box to test its appropriateness as a kiosk machine. I was most impressed with its default behavior of disabling the root account by default, then giving all users membership in sudoers. Then I checked, and by default, it allowed *any* user I created to enable the root account and change the root password. And this was after I applied all the security patches.
Yes, I know I can fix this, but it certainly gave me pause, as I'm not sure what other little "surprises" to expect. This is certainly not the sort of behavior I want on a computer in an out-of-the-way nook that a constantly changing group of college students are using to check email."  [/COLOR]
[COLOR="Blue"]If what Soper writes was right,[/COLOR] I guess that I would have no difficulty to [COLOR="Blue"]open Nautilus in root which would allow me to go modify the permissions on my superuser's home directory[/COLOR]. But that did not turn out to work for I could not open Nautilus in root from my new user's account (laodan2). Then I saw [the answer of brm ]("http://www.linuxtoday.com/news_story.php3?ltsn=2006-06-05-013-26-RV-DB-DT-0003") to Soper's post which basically confirms the substance of what I'm saying: the installer of Ubuntu gets superuser privileges to go in root mode by opening a command starting with sudo...
[COLOR="Orange"]"Ubuntu's default behaviour is to enable sudo access for the first and only the first user account, that is, the one created during installation. "  [/COLOR]

So the superuser has a monopoly on sudo through the password he used at install of Ubuntu. (what I called the root password)  But my problem is not the superuser's password, laodan's password. (it's mine so I know it and for sure I'm using it) . 

[COLOR="Red"]The problem is that to enter the account of the superuser I need to execute his home folder and that is what is refused to me and this is why I can't change the permissions on the superuser's home directory...[/COLOR]
[See my post n#4]("http://www.ubuntuforums.org/showpost.php?p=1143074&postcount=4")

---

### Post by zxee on 2006-06-16
My curiosity gets the best of me with this problem-and I think that the moderators should look into this because if I'm understanding you correctly then this is a big problem/flaw. Please ask the moderators here to look at your post(s) as it's how we can improve things. 
Ok after saying that-Have you tried to use sudo with the user, not root, password? If you have what exactly is the result?

Note: You might want to read this thread: [http://www.ubuntuforums.org/showthread.php?t=197798](http://www.ubuntuforums.org/showthread.php?t=197798)

---

### Post by laodan on 2006-06-17
[QUOTE=zxee]My curiosity gets the best of me with this problem-and I think that the moderators should look into this because if I'm understanding you correctly then this is a big problem/flaw. Please ask the moderators here to look at your post(s) as it's how we can improve things. 
Ok after saying that-Have you tried to use sudo with the user, not root, password? If you have what exactly is the result?

Note: You might want to read this thread: [http://www.ubuntuforums.org/showthread.php?t=197798](http://www.ubuntuforums.org/showthread.php?t=197798)[/QUOTE]


Sorry for my delayed response.
Here a summary of my adventures with Dapper Drake since my last post:

[COLOR="Red"]1.  Having lost all hope to find a miracle command that would retsore my superuser execute permission on the home folder, I tried a re-install from cd.[/COLOR]
Booting is ok but ends with a text command from where I could not enter the system. I tried to re-install a second time and got stuck with the same problem. (I checked the integrity of the CD before install and it was without flaws) 
There is visibly a problem with cd install... what a shame that new-comers to Ubuntu get this kind of treatment at their first contact with this otherwise great OS.. 

[COLOR="Red"]2. Re-install of Breezy and re-upgrade to 6.06 from an installed 5.10.[/COLOR]
Being an "old Ubuntu user" (full since well over a year) I had been impressed with the ease at installing 6.06 without a glitch from the upgrade button in my breezy 5.10 update gui (at least till my superuser lost his execution permission)... so here came this crazy idea:
- re-install 5.10
- from 5.10 upgrade to 6.06
And everything went without a glitch... 
Happy... I customized my new 6.06 system and must say that I have been extremely satisfied of what I got UNTIL... my super-user AGAIN lost its execute permission. 
Whar! This was last night around 2am. I went to bed.
It might be interesting to note when this loss happened. 
I have 2 Hard Drives:
- hda with Ubuntu, my applications and my data (as most people do I suppose)
- hdb mounted on a storage directory in  hda ( /storage)
I was using the new back-up program that was installed in system (if my memory is right). I saw that back-up operated in the background so I started to do other stuff and then came the fatal moment when I clicked on file manager with the idea to check if the back-up operated as should and blam stand-still... I had again lost all control over the system. I powered off (push button on the computer) and tried a reboot. Everything went fine till the text command. I tried the same commands we went over in my initial post and found the same answer:
sudo: /home/laodan command not found.
I have the confused feeling that something is wrong with Nautilus (file-manager). Remember what [Dennis Soper wrote]("http://www.linuxtoday.com/news_story.php3?ltsn=2006-06-05-013-26-RV-DB-DT-0001"). [COLOR="Orange"]""My Favorite Ubuntu Feature....
I installed the last version Ubuntu on a box to test its appropriateness as a kiosk machine. I was most impressed with its default behavior of disabling the root account by default, then giving all users membership in sudoers. Then I checked, and by default, it allowed *any* user I created to enable the root account and change the root password. And this was after I applied all the security patches."[/COLOR]
I did not particularly focus on this but after this upgrade of 6.06 from 5.10 when I went to check how the upgrade had set the permissions on my superuser's home folder I discovered that permissions were not protected.. that means that i could modify them without root access... This was not so on Breezy.  Is this the cause of my execute permission disabling? Now I have no clue about that.

[COLOR="Red"]3. Remaking an install of Breezy and re-upgrade 6.06 from an installed 5.10.[/COLOR]
Yes, I'm presently in Breezy. After terminating this post I'm going to start the upgrade to 6.06 AGAIN.

I'll keep you informed a few hours later.

---

### Post by laodan on 2006-06-17
Third upgrade  without a trace of a glitch.

I must say that, from the point of view of an "old Ubuntu full-time user", this is one of the most interesting advances in Dapper Drake. Pity that the cd install was so poorly bundled. Old Ubuntu users are not suffering the cd pain but let's try to understand how negatively this is impacting on the new user having his first experience through the cd install...

For now I can say no more. I will start to play customizing my system. 
I'll keep you posted further down the road.

---

### Post by stoneguy on 2006-06-17
If it happens again, there's a few things you can do to get back on the air without reinstalling.

One is to activate root logon. Boot up from some Live CD, mount the partition that contains Ubuntu's /, and edit /etc/passwd to remove the 'x' between the 1st pair of colons on the line starting with root. Save the file. Reboot Ubuntu, alt-F1 to a  shell, and login as root with no password. Immediately use the passwd command to to create a secure root password. Now at least you can operate from a shell, although you can't from your X window.

Check the /etc/passwd file. The last entry should be

[INDENT]aodan:your-encoded-password:1000:1000:laodan,,,:/home/laodan:/bin/bash[/INDENT]

Now take a look at /etc/sudoers. It should have (if the 1st user you created is laodan)

[INDENT]root     ALL=(ALL) ALL
laodan ALL=(ALL) ALL
%laodan ALL=(ALL) ALL[/INDENT]

If not, repair using visudo.

Now check /etc/group. laodan should be in groups 4,20,25,29,30,44,46,106, and 110. The last line should be

[INDENT]laodan:x:1000:laodan[/INDENT]

Now cd to ~laodan, and use ls -l to make sure the files and groups have to correct owwnership. If not, correct with chown. Where u-x permission is missing, fix with chmod.

If you're paranoid, edit /etc/passwd again and replace whatever is between the 1st 2 colons on the root line with an x to disable root logon.

Reboot into your gui, and you should be able to log on again as laodan.

Now you can try to track down what's triggering your problem without reinstalling each time.

---

### Post by October on 2006-06-19
I'm running into similar problems...

I have ran 5.10 on my family file/music/print server since it came out reserving /home/files and /home/music between upgrades and installs.  Recently I did an upgrade to one of the 6.06 betas and things went well and I was impressed with the adept notifier.

A few days ago my samba server died and when I ssh'd into the server to take a look I noticed that only "root" (I have root enabled) could even read any of my archived /home directories.  chmod -R a+r /home did no good...  I still get "Permission denied." as any user besides root!

I tried a virgin 6.06 LTS install (preserving /home/files and /home/music) and that didn't fix it either.  Something is definately sounding wrong with the latest CD release! 

Will hope someone comes up with a fix soon or will backtrack to 5.10 again.

Thanks in advance.

---

### Post by nitin_mz on 2006-06-19
I had a slightly different problem - I created a new user with sudo permissions, and then deleted the original user created during dapper install. 

As a result, I started seeing "broken pipe" error messages running sudo.

Thankfully, I didnt screwup the root passwd, and was able to run "su" and fix these files:

[QUOTE=stoneguy]
Check the /etc/passwd file. The last entry should be

[INDENT]aodan:your-encoded-password:1000:1000:laodan,,,:/home/laodan:/bin/bash[/INDENT]

Now take a look at /etc/sudoers. It should have (if the 1st user you created is laodan)

[INDENT]root     ALL=(ALL) ALL
laodan ALL=(ALL) ALL
%laodan ALL=(ALL) ALL[/INDENT]

If not, repair using visudo.

Now check /etc/group. laodan should be in groups 4,20,25,29,30,44,46,106, and 110. The last line should be

[INDENT]laodan:x:1000:laodan[/INDENT]
[/QUOTE]

Some of the groups listed in /etc/group were empty, and I added the new username to them. Some of them already have users assigned to them - do I append, or replace the username?

Also, System -> Administration on the desktop no longer lists the users/groups manager, or the synaptics application. Is there a way to restore the admin menus?

---

### Post by laodan on 2006-06-19
Thanks stoneguy and nitin mz for the procedure to follow in case of trouble with execute permission on superuser home folder.

My third upgrade went without a glitch as the 2 earlier ones. The automatic upgrade is absolutely working fine. 
This time my installation seems to be more stable. (touching wood...)

What I can see as a difference between the 2 first upgrades and this 3rd is that the two first upgrades had been done on Breezy with nautilus-root and file manager-root being installed while the 3rd upgrade has been realized on a Breezy without root-power to Nautilus...

After the 2 first upgrades I had observed some bizarre behavior in Nautilus (access appeared to function as in root on all files from the standard file-manager). That's why I avoided to root enable Nautilus on Breezy before the 3rd upgrade. 

I don't know if this was the reason for superuser to loosing execute permission on his home folder some time after the 2 first upgrades. But fact is that this 3rd upgrade is definitely lot more stable and the behavior of Nautilus seem to be normal this time.


About stoneguy's post:
Check the /etc/passwd file. The last entry should be

    laodan:your-encoded-password:1000:1000:laodan,,,:/home/laodan:/bin/bash

Now take a look at /etc/sudoers. It should have (if the 1st user you created is laodan)

    root ALL=(ALL) ALL
    laodan ALL=(ALL) ALL
    %laodan ALL=(ALL) ALL

If not, repair using visudo.

Now check /etc/group. laodan should be in groups 4,20,25,29,30,44,46,106, and 110. The last line should be

    laodan:1000:laodan

_________________________________
I went into the file from nautilus-root.

1.  laodan:x:1000:1000:laodan,,,:/home/laodan:/bin/bash   (no password, only a "x")

2.  # User privilege specification
root	ALL=(ALL) ALL
# Members of the admin group may gain root privileges
%admin	ALL=(ALL) ALL

3.  /etc/group. laodan is in groups 4,20,25,29,30,44,46,106, and 110. But the last line is not
 laodan:1000:laodan    (this is nowhere to be seen in this file)  Only a line:     laodan:x:1000:

Thanks for advising how to proceed further. Is it imperartive to operate those changes?

---

