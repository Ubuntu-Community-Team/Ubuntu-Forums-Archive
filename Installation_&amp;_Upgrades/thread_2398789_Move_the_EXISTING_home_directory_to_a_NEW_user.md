---
title: "Move the EXISTING home directory to a NEW user"
date: 2018-08-17
forum: Installation &amp; Upgrades
---

### Post by stsolution on 2018-08-17
Hi gurus, I am new to Linux and need some help. I have searched for this topic, I found one thread but still I am confused.

Problem:

One of our user JERRY tried to upgrade from Ubuntu 16.04 to 18.04. Installation went fine but there are certain issues.

1. Desktop display is not right, things are overlapped and icons are displaced
2. He has admin rights, but he can not copy any text from any file.
3. He is unable to change desktop and display settings.

So, I created a new user account and there everything is working fine. That was a test account. We deleted it later. 

Now I want to create a new user account for JERRY, and move all his existing data and home directory to theis new account. Or you can say I want to point the Home Directory of New user to the old one.

Can anyone please help me about this.

The following command does create and replace the existing home directory.

sudo usermod -d /home/jerryNEW -m jerry

But if a new home directory is created, does this mean a new user has also been created or we need to create a new user and then point his home directory to this one.

Thanks in advance guys.

---

### Post by Tadaen_Sylvermane on 2018-08-17
You should just move the actual data to the new /home/$USER directory. If you copy the entire folder then you will also copy the . files, which I believe is where the problem is. You need a fresh /home/$USER directory. This is a poster child of why not to use a /home between different distros, rather to use a data partition and allow /home/$USER to be overwritten with new data instead of hanging onto the old stuff.

*EDIT* Yes you lose your settings. But a half hour reconfiguring vs problems like this. Easy choice.

---

### Post by ubfan1 on 2018-08-17
Programs and data may well be stored in some dot files too (e.g. everything installed and created with wine, mail, etc.), so better keep a copy of them until things get sorted out.  Another way to handle this is to make a directory in the user's home and move all the dot file into it.  Let the user login again without the dot files, letting new ones get created as needed, resulting in a normal desktop.  Then move the dot files that were not created back one at at time to preserve as much as possible.

---

### Post by stsolution on 2018-08-20
Thank you very much for both the suggestions but something is not working correctly. Ubuntu doesn't let me execute simple commands. I am trying to do:

sudo cp -r /home/usr1 /home/user2

it asks me for admin password,  but when I enter the password, the system gets confused or lost or whatever you wanna call it, it doesn't do anything, i don't see any prompt or message or reply or error... strange.

I guess I would need to do a new installation.

---

### Post by deadflowr on 2018-08-20
If you're not seeing the return prompt (meaning the default prompt of user@machine-name~$), then it means the command is still running.
You won't see any notification-like prompts if the command runs fine, only if there are errors or required user input for some needed action.

What does (or did) /home/user2 look like?
Still empty or now populated with a lot of files?

---

