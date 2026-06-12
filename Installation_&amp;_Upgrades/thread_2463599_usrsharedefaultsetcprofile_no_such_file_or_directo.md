---
title: "/usr/share/defaults/etc/profile no such file or directory"
date: 2021-06-14
forum: Installation &amp; Upgrades
---

### Post by grxgghxrpxr on 2021-06-14
Hello

I installed Ubuntu Budgie 21.04 over the Home directory of my previous installation of Solus 4.2 Budgie. Everything has worked out quite well, and I am able to access my personal files and do everything, but an error message comes up everytime I log on & when I click 'OK', I can continue to the desktop & work like normal.

What kept coming up was:
Error found when loading /home/inclusivetechworld/.profile:
/home/inclusivetechworld/.profile: line 1: /usr/share/defaults/etc/profile: No such file or directory

So I used the Terminal to create this folder - now it says: 
Error found when loading /home/inclusivetechworld/.profile:
/home/inclusivetechworld/.profile: line 1: /usr/share/defaults/etc/profile: Is a directory

How do I stop this from coming up?

Thank you
Gregg

---

### Post by GhX6GZMB on 2021-06-14
Well, you'll have to look into your $HOME/.profile

Try posting it here.

---

### Post by The Cog on 2021-06-14
There is no such file in Ubuntu. I am guessing you need to edit the file to look for /etc/profile instead. I think that script wasn't written for Ubuntu.

---

### Post by grxgghxrpxr on 2021-06-14
It won't let me open it or edit at all, it just says permission denied. I've tried opening it in the Terminal with sudo and it just doesn't open, it says the same thing. (I'm referring to .profile in my Home directory)

---

### Post by MAFoElffen on 2021-06-14
What the others are trying to tell you is that there is a pointer to a non existent entry in your profile.  For ubuntu, every user has a .profile file in the base of their Home directory. The dot in front of a filename will make that file a hiiden file, so, in GUI File Manger, you would have to change the settings to "Show Hidden Files" for you to see it. In the Debian Branch, if a change to a users profile is not "an additional personal change" then it goes off what is in /ETC/Profile (as noted)... That is not your problem.

In the base of the user's home directory, there are also hidden applications directories, that contain the current user profiles for that application. And if you find the hidden directory that contains that hidden profile file, "~/.inclusivetechworld/.profile" that is where it is telling you that there is a problem.

That really does not matter much. As others have explained to you... It seems you had, in the past installed something that was originally written for another (old) branch of Linux, where the filesystem was different than the Debian branch. It looks like it was written for a RHEL branch before Linux evolved into systemd. In upgrading, there was not a good, current candidate that upgraded with that, so now you see an error message, that displays that there is a pointer/path problem.

From what I can see, you may have installed a third party USB boot creation application in the past. Did you? If you did, list out your installed packages and find it. It seems to have dead-ended with no newer release candidates. Uninstall it. It doesn't seem to be something that you have used recently. Right?

EDIT: If it didn't install during the release upgrade, because the do-release-upgrade script determined that it had no newer candidate in the package resolve process, then the error was a clean-up error that the script couldn't guess at (because it was legacy third party). You can safely remove the "~/.inclusivetechworld/" directory. Then the error will just go away.

---

### Post by grxgghxrpxr on 2021-06-14
No, I didn't install that application as I used my Windows laptop to create this USB. I can find that file in my Home directory, but it won't allow me to open it. Is this the file I'm supposed to be deleting?

---

### Post by grxgghxrpxr on 2021-06-14
I did delete the Home directory, and the message stopped coming up every time I log on. I also deleted the profile folder I created in /usr/share/defaults/etc/, but whenever I open the Terminal, the first line always says: 'bash: /usr/share/defaults/etc/profile: no such file or directory'.

Deleting the .profile from my Home meant I had to readd my custom resolution, but that's okay, it only took me 2 minutes.

---

### Post by MAFoElffen on 2021-06-14
Hopefully not the whole home directory, but just that one hidden application directory that was in home:  "~/.inclusivetechworld/"

---

### Post by michaelmacho on 2021-08-15
in /usr/share/defaults 

after this there is no etc folder

but i do see a /etc/profile.d

There is also a directory in the /etc and a file called profile

---

### Post by GhX6GZMB on 2021-08-15
> **michaelmacho said:**
> in /usr/share/defaults 

after this there is no etc folder

but i do see a /etc/profile.d

There is also a directory in the /etc and a file called profile

Is this a question? Then please open a new thread.
This thread is 2 months old, so I expect it to be solved.

---

