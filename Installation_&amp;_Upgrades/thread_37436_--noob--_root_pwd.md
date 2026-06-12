---
title: "--noob-- root pwd??"
date: 2005-05-27
forum: Installation &amp; Upgrades
---

### Post by JNaas on 2005-05-27
Hi all

I'm new to Ubuntu, and fairly new to linux in genral!
actually im kinda surfin' through distro's to find the one that suits be best!

But i came to wonder about something!

how come during install I am not given the option to define a root password??
Is it because there is a default password your supposed to change afterward? 
or am i missing something?

any help appreciated!

---

### Post by Infernal on 2005-05-27
[QUOTE=JNaas]Hi all

I'm new to Ubuntu, and fairly new to linux in genral!
actually im kinda surfin' through distro's to find the one that suits be best!

But i came to wonder about something!

how come during install I am not given the option to define a root password??
Is it because there is a default password your supposed to change afterward? 
or am i missing something?

any help appreciated![/QUOTE]
 go to users and groups and change the pass for the root user there. the pass to access that is the same pass as your usersaccount. You can also use this command: 
sudo passwd root

---

### Post by SGC on 2005-05-27
You don't ask for a root password , becuse there is no root account by defult. to perform a root action you need to use sudo command.

If you want to create a root accout use the following command:
sudo  passwd
then enter the root password that you want

PS: most people here will recomand you not to enable or use the root account, But I don't see any harm of doing so.

---

### Post by Shakie on 2005-05-27
I asked pretty much the same question here: [http://www.ubuntuforums.org/showthread.php?t=37121](http://www.ubuntuforums.org/showthread.php?t=37121)

This is the link that explained pretty much everything: [http://www.ubuntulinux.org/wiki/RootSudo](http://www.ubuntulinux.org/wiki/RootSudo)



Basically, for better security, root is disabled by default in Ubuntu. Instead it uses something called sudo. The first user you create on an Ubuntu box is made part of the administrators group and can use sudo. Click the above links for more information.

---

