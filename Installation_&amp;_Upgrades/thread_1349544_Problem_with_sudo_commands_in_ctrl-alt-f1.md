---
title: "Problem with sudo commands in ctrl-alt-f1"
date: 2009-12-08
forum: Installation &amp; Upgrades
---

### Post by ve3sjk on 2009-12-08
I am trying to run sudo commands in a virtual console that it get when i type ctrl-alt-f1.

I can login using my normal login at the first prompt and get a command prompt as usual.

My problem is when i try and use any sudo commands it asks me for the password again and fails every time giving me a password prompt loop. 

I have tried my normal password and even a blank password nothing seems to work to allow the sudo commands from tty1.

I am using Ubuntu 9.10 Karmic

---

### Post by phillw on 2009-12-08
> **ve3sjk said:**
> I am trying to run sudo commands in a virtual console that it get when i type ctrl-alt-f1.

I can login using my normal login at the first prompt and get a command prompt as usual.

My problem is when i try and use any sudo commands it asks me for the password again and fails every time giving me a password prompt loop. 

I have tried my normal password and even a blank password nothing seems to work to allow the sudo commands from tty1.

I am using Ubuntu 9.10 Karmic

Check that you are in the sudoers list.

> Go to System >> Administration >> Users and Groups.

Then:

(1) Click on the name of the user that you want to elevate.
(2) Click on the properties button to open a new settings window.
(3) In the new window, click on the User Priviledges tab.
(4) Check the box next to "Executing system administration tasks".

Click OK all the way out, and that user should now be able to sudo. 		                   		  		  		 		 			 				

If you're in that list, it should work - coz i just tried it -lol

Phill.

---

