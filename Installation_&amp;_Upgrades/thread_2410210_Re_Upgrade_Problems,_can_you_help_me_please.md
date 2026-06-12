---
title: "Re: Upgrade Problems, can you help me please"
date: 2019-01-12
forum: Installation &amp; Upgrades
---

### Post by stephen-parish on 2019-01-12
Whilst trying to upgrade Ubuntu on my laptop from 16.04 LTS to 18.04.1 LTS everything seemed to go without a hitch, all questions answered all followed perfectly as i progressed through the installation. Then the box that had text in it letting me know how far through the installation i had got suddenly went weird, all text was replaced with tiny empty boxes, hundreds of them.

Now the laptop will not boot into ubuntu at all, the screen is black although i can see the cursor and move it around the screen. I have tried restarting the laptop several times but the problem is still there.
Can you advise please

I have managed to get it to boot up, but now it will not accept my password, i have checked to make sure i am typing in the correct one and typing it correctly, yet it will not accept it and keeps telling me it's incorrect.
I am lost how to proceed and correct this, i would really appreciate some help on this PLEASE

I have just upgraded my Ubuntu from version 16.04 LTS to the latest 18.04.1 LTS
had trouble getting it to boot up to start with, but by trial and error i managed it, but now it will not accept my password even though i am entering the right one.
Can you help me please, i am lost

---

### Post by Bashing-om on 2019-01-12
stephen-parish; Hello -

Maybe reset the password ?
[http://www.psychocats.net/ubuntu/resetpassword](http://www.psychocats.net/ubuntu/resetpassword) <- Here are easy instructions to reset your password in Ubuntu
[https://help.ubuntu.com/community/LostPassword](https://help.ubuntu.com/community/LostPassword)

[INDENT][INDENT]hope this helps
[/INDENT][/INDENT]

---

### Post by stephen-parish on 2019-01-12
Thank you, i will try that now

ok i have followed the instructions to reset my password, rebooted yet all it keeps doing is asking me for the password, it pauses for about 20 seconds as though it is going to start up normally then just chucks me back to the screen to enter my password again, It's so frustrating !
I just can not get past this screen

---

### Post by Bashing-om on 2019-01-12
stephen-parish Hummmm ...

Let say that what we have here is a graphic's driver issue .

At the login screen key combo ctl+alt+F2 to activate a console interface.
Login here with username and password ( no response to screen when pw entered).
what shows for a driver in the configuration line from terminal command :
```

sudo lshw -C display

```

[INDENT][INDENT]maybe this
[INDENT][INDENT]maybe other
[/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by stephen-parish on 2019-01-12
[h=2]On no 3 what is meant by "Select your image" ????

The Other Way[/h]If the "Standard Way" does not work for you and you recieve the "Give root password for maintenance" message, you can recover your password using the following steps
1. Reboot your computer
2. Press SHIFT or ESC at the grub prompt (as earlier).
3. Select your image.
4. Highlight the line that begins kernel and press 'e' to edit
5. Go to the very end of the line, change the ro to rw and add init=/bin/bash
press enter, then press b to boot your system.
Your system will boot up to a passwordless root shell.
6. Type in passwd username
7. Set your password.
8. Type in reboot

> **Bashing-om said:**
> stephen-parish Hummmm ...

Let say that what we have here is a graphic's driver issue .

At the login screen key combo ctl+alt+F2 to activate a console interface.
Login here with username and password ( no response to screen when pw entered).
what shows for a driver in the configuration line from terminal command :
```

sudo lshw -C display

```
[INDENT][INDENT]maybe this[INDENT][INDENT]maybe other
[/INDENT]
[/INDENT]
[/INDENT]
[/INDENT]


It just keeps asking me for my password, which i enter, then it tells me it's incorrect.

---

### Post by Bashing-om on 2019-01-12
stephen-parish; Well !

Then we do have an invalid password.

Let's do [http://www.psychocats.net/ubuntu/resetpassword](http://www.psychocats.net/ubuntu/resetpassword) as the common reference.

It is very precise with screenshots .. Though old it remains applicable.

Have a read there and try to reset your password. Any issues then explain what you did, and what happened and what you do not understand.

We are here to help
[INDENT][INDENT]we will get through this
[/INDENT][/INDENT]

---

### Post by ubfan1 on 2019-01-13
The first thing to check is the NUM lock  and CAPS lock state.  Sometimes the NUM lock does not even have an LED to indicate its state.  Another cause of this problem is having a wrong keyboard definition, so the keys you type are not what the computer sees. If you switch to a virtual terminal (ctl-alt-F3  through F6) to get to a text login, what do you see when you type your password at the username prompt (which should echo)?

---

### Post by stephen-parish on 2019-01-13
Ok these are the steps i have just tried in order

Hold down start and left shift button to start up Laptop.
Scroll down to 2nd option "Advanced options for ubuntu"
Press enter
Choose 2nd option (Recovery Mode)
Press enter
Scroll down and choose "Root" Drop to shell prompt.
Press enter

On the screen i now see "Give root password for maintenance, or press control D to continue"
I type in root password
Press enter
Type password
Type password again
Type exit
Press enter
Choose resume normal boot
Press enter
Press enter again
Press enter again
Wait for laptop to boot up
I now have a black screen with a blinking cursor in the top left corner.
I wait for 20 min and nothing has happened
Hold down start button and force a shutdown
Wait 5 min then press start button
once laptop has booted i am at the enter password screen
I enter my password and press enter
the password screen vanishes as if its excepted the password and going to start up, but then just chucks me right back to the password screen again.
I can not get any further

Please help

ok just tried your instructions and this is what i now see on the screen

Ubuntu 18.04.1  LTS (My Username)
My Username -R59P-R60-R61 Login: (My Username)
Password:
Last Login: Fri Jul 8.20:33:15  BST 2016 on tty1
Welcome to Ubuntu 18.04.1 LTS  (GNU/Linux 4.4.0-141-generic x86_64)

* Documentation:    [https://help.ubuntu.com](https://help.ubuntu.com)
* Management:       [https://landscape.canonical.com](https://landscape.canonical.com)
*Support:               [https://ubuntu.com/advantage](https://ubuntu.com/advantage)

1239 packages can be updated.
0 updates are security updates.

My Username@MyPassword-R59P-R60P-R61P:~$

And still not able to get any further, please help

---

### Post by ubfan1 on 2019-01-13
The virtual terminal login appeared to work, so the problem is with the login screen. See bug [https://bugs.launchpad.net/ubuntu/+source/gnome-shell/+bug/1765261](https://bugs.launchpad.net/ubuntu/+source/gnome-shell/+bug/1765261) for similar problems with suggested workarounds.  If you get exactly the same login error message as when you type in the wrong password, then probably it something to do with the keyboard layout.  Which keyboard layout are you using?  If the login screen just repeats, without an error message, then probably some file like .Xauthority is causing the issue (like it's owned by root).

---

### Post by stephen-parish on 2019-01-13
I have no idea what keyboard layout it's using as i can't get into it to change or alter anything.
It is set to English UK that's all i know, And no matter what i try to do it just keeps throwing me back to that darn enter your password screen.
I even downloaded a fresh copy of the latest version of ubuntu ISO and put it onto a USB stick, tried to get it to boot from the USB rather that the HD hoping that with a fresh install my problems would be resolved.
No such luck, just keeps asking for my password, looks as if it's accepted it for a few seconds then jumps back to enter your password yet again, and so this loop keeps going.

I will take a look at the link you provided and see if that works and report back with the result's.
If you have any other tricks or things i can try to resolve this problem i would be most grateful, as at the moment i am totally locket out of my Laptop.

---

### Post by ubfan1 on 2019-01-13
If you're not getting an error message at the login screen, just a repeat of the screen, the problem is likely in the dot files (files in your home directory whose first character is a period).  Try logging into the guest session, which starts with a clean home directory.  If that succeeds, then back at a virtual terminal, login and check the ownership of the dot files with the command ls -lA   and if any are owned by root, change them back (recursively if a directory) to be owned by you. Search this site and askubuntu.com for "login loop" for this issue.

---

### Post by stephen-parish on 2019-01-13
Ok i have an update,
On the password log in screen i enter my password but instead of pressing enter i use the backspace to clear the password.
Once cleared i enter my password again then press Enter
This time after a few seconds i momentarily see an open folder (HOME) with several folders inside it
Then it just goes straight back to the desktop enter password screen.

Hoping this info helps you help me with solving this issue and getting me back into my Laptop.

> **ubfan1 said:**
> If you're not getting an error message at the login screen, just a repeat of the screen, the problem is likely in the dot files (files in your home directory whose first character is a period).  Try logging into the guest session, which starts with a clean home directory.  If that succeeds, then back at a virtual terminal, login and check the ownership of the dot files with the command ls -lA   and if any are owned by root, change them back (recursively if a directory) to be owned by you. Search this site and askubuntu.com for "login loop" for this issue.

Sorry to be a pain but i am very new to ubuntu and struggling to understand some of the lingo.
How do i log into a Guest session ?
How do i log into a Virtual Terminal ?
The last part of your message has me totally lost !

i found one that was owned by root

drwxr-xr-x 3 root root 4096 Jul 6 2016 ..

i have now changed it to

drwxr-xr-x 3 matrix matrix 4096 Jul 6 2016 ..

Rebooted Laptop, and entered my password, for a split second i saw my normal desktop screen, then is went right back to the enter your password screen again.

Almost there but i think there is a bug somewhere that is stopping it working. How i fix it and get past this point i am lost

when i go to try and change it it says the following  drwxr-xr-x: command not found
how do i change it from root to matrix ?

---

### Post by howefield on 2019-01-13
Duplicate threads merged.

---

### Post by stephen-parish on 2019-01-13
> **howefield said:**
> Duplicate threads merged.

Thank you for merging the threads, I did not know how to delete the other one

Update,

I finally managed to get it to do a re - install of the latest version of ubuntu, took quite a while but stayed with it watching very carefully.
It did complete the installation, but stated the installation was successful but had several errors.
I have now lost faith in trying to solve this issue as i have spent two days of my time trying everything possible to always come back to the same problem.
I am now going to take the Laptop to a shop and get them to put Windows back on it a rid Ubuntu out of it and the bugs/errors once and for all.

It is really weird though as i did the upgrade on my other Laptop and all went without a hitch and is working perfectly, and seems a bit quicker if i'm honest.
Why this one went base up i will never know as i followed the very same procedure.
Appreciate those that did try to help me
Thank you for your time and patience.  :)

---

### Post by ubfan1 on 2019-01-13
At the login screen, there should be a choice of users to login, one should be the "guest session" -- blank password.  That login creates a temporary home directory in /tmp, and sets up the default desktop.
The virtual terminal login are text only logins available through the keyboard ctl-alt-F3 through F6 commands.  You get a login prompt, type in your username, then password.  You get a shell prompt, 
The ".." file is a shorthand for "parent directory", and in this case, it is /home and should be owned by root.  Letter case is important in most commands, and the command I suggested with a capital A, would have suppressed the .. output (and the . which is the current directory). Fix the /home from a virtual terminal (not the guest session even if it works, since it cannot run the sudo command).  
  ```
sudo chown root:root /home
```  

However, if the .. was the only drirectory owned by root (as it should be), then the problem is not ownership.  A new version of a progarm looking at an old version of the configuration file(s) stored in a dot file may fail.  If the guest session works, that is probably the issue (the guest session starts fresh, with no dot files). You may have important things stored in your dot files, (you had upgraded, not a fresh install),  so don't just delete them. But, you can get them out of the way.  Again from a virtual terminal, create a directory (it'll be in your home directory),
 ```
mkdir mydots
```  
Then just move the dot file into this directory:
mv .cache mydots
mv .local mydots
mv .Xauthority mydots
...etc.
Try a login again from the login screen.  If that works, you may move the dot files back to the home (up a level), or just leave them and let them be recreated as needed.  If you find anything missing (like your mail, etc. ) you can go back to the mydots directory and pull out the dot file containing your mail (.mozilla, .thnderbird, whatever).

---

### Post by stephen-parish on 2019-01-14
At the Login screen the only choice of user is "Matrix" which is me. If i click on the round logo slightly to the right of my username i see the following ...

Select desktop environment

GNOME Flashback (Compiz)
GNOME Flashback (Metacity)
Ubuntu
Ubuntu on Wayland
Unity (Default)

Over on the top right of the screen if i click on the cog wheel i see the following....


Suspend
Hibernate
Shutdown

Now on my other Laptop that has the latest version of Ubuntu 18.04.1 i see a lot more when i click on that cog wheel, which seems to me that something is missing.
I will try your suggestion and see how i get on and report back. Thank you

i still have got nowhere with this laptop and the upgrade issues so am throwing in the towell.
I have now wiped Ubuntu completely off the Laptop and have gone back to Windows, all is working fine now.
I will keep Ubuntu 18.04.1 on my other laptop as that one is ok.

Thanks for all the help
Have a super week

---

