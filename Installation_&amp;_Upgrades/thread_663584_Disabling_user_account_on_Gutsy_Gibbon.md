---
title: "Disabling user account on Gutsy Gibbon?"
date: 2008-01-10
forum: Installation &amp; Upgrades
---

### Post by patrikwa on 2008-01-10
Hi there,
im kinda annoyed at one thing that i cant find how to remove. When i start Ubuntu i come to a log in screen (why would i need one when im the only user of this computer?) that i want removed. All the administration thingys like installing updates/programs or even accessing ntfs disks require authentication which really is annoying to do EVERY time i start Ubuntu and want access. How can i completely disable user accounts so i never get the pop-up to type in administrator password?

Regards / Patrik

---

### Post by chewearn on 2008-01-10
User authentication is part and parcel of having a more secure OS.  It is extremely unwise to disable this.

However, one thing you can remove is login when starting up.

Click on top panel menu > System > Administration > Login Window
Select Security tab > check "Enable Automatic Login" > select your user from the dropdown list.

---

### Post by codesplice on 2008-01-10
So you're essentially wanting to automatically log in as root?

That's not a good idea.  You're much more likely to break something that way.

However, in the interest of science...

Automatica login is easy: Pull up the Login Window utility (System-->Administration-->Login Window).  Click on the Security tab, and click the checkbox next to "Enable Automatic Login".  Click the dropdown, and select your account.  You should now be automatically logged on after bootup.

The root account can't be automatically logged in, but you can give yourself root priveleges.  Go to System-->Administration-->Users and Groups.  Click on your user name, and select Properties.  Under the Advanced tab, change your main group to "root".

Reboot, and you should be automatically logged in with full administrative access.

---

### Post by zvacet on 2008-01-10
In everyday work you don´t need admin privileges so much.That is why you make second user without admin privileges and you work with it most of the time.It is not just for security from others,it keep you secure from yourself.You know how easy is to type something wrong or make other mistakes.If you do it under admin you risk to break your system.If you want to login automaticly 
 System > Administration > Login Window> Security tab > check "Enable Automatic Login" >ansd select user without admin privileges.If you need admin user swich user and when you do what you want come back to user with no admin privileges.All this story is just suggestion,and you will do whatever you think it is best for you.

---

### Post by patrikwa on 2008-01-11
> **zvacet said:**
> In everyday work you don´t need admin privileges so much.

Uhh i must do something wrong then, i need admin privileges EVERY time i log in to Ubuntu just to access my disk where i keep music/movies etc etc, every or every second day updates are released which require admin, every time i need to update/install a new program i need to be admin and there are probably more stuff which i forgot.

The opinion about making ubuntu secure towards myself since its easy to make errors, well, thats just not a good reason, sure i could do an error causing the entire OS to crash but i mean, that requires me to work in a terminal and accidently type something like -sudo blabla or edit some vital file which IMO has a very low chance of accidently happen.

Everyone keeps saying its BAD to disable user accounting since its dangerous etc, anyone have a good example of what could happen? i always log in as admin, do things that requrie password and always type in password for what i need doing, if the step "type in password" was disabled i cant see the difference in effect between typing the password or just skip that part... so i really cant see your point here.

---

### Post by codesplice on 2008-01-11
Regardless of your (flawed) reasoning.... did any of the suggestions offered help?

---

### Post by patrikwa on 2008-01-11
Yes it was helpful to get info about how to enable automatic login, thx alot for that =) 
However, is it possible to do what i want? I understand that it's not recommended for some reason and i'd like to know the downsides with doing so if anyone knows =)

---

### Post by chewearn on 2008-01-11
Have a look here for some tips:
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by Aishiko on 2008-01-12
have you tried running a comand to change the ownership of the directory were your muisc/movies/crap is located to move it from what sounds like root ownership to your log in name ownership?

---

### Post by zvacet on 2008-01-12
@ **patrikwa**

If you still want to do what you asked for regardless of what we all saying and what you can read about this topic here it is 

[http://ubuntuforums.org/showthread.php?t=641968&highlight=sudoers]("http://ubuntuforums.org/showthread.php?t=641968&highlight=sudoers")

---

