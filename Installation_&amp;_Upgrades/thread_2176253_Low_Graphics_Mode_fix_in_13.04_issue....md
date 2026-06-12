---
title: "Low Graphics Mode fix in 13.04 issue..."
date: 2013-09-23
forum: Installation &amp; Upgrades
---

### Post by Jimmy_Conway on 2013-09-23
[FONT=arial][COLOR=#262626]First off; if I'm breaching some kind of "First Post Protocol"  and I should have posted an introduction elsewhere, I'm sorry...

I really hope someone here can help - and apologies if this particular problem has been posted...and if this is the wrong place for it.[/COLOR][/FONT]

[FONT=arial][COLOR=#262626]After much apprehension, I finally upgraded to 13.04, and promptly encountered what was apparently a widespread issue with my system booting in Low Graphics Mode.[/COLOR][/FONT]

[FONT=arial][COLOR=#262626]After a quick search (from my phone) I found the fix for it with no problem, save one:[/COLOR][/FONT]

[FONT=arial][COLOR=#262626]When I get to this point in the steps to fix the problem: [/COLOR][/FONT]> [COLOR=#333333][FONT=UbuntuRegular]In some cases failsafeX will load fine (You lucky dog), for others (Me) it will give an error along the lines of "The system is running in low-graphics mode" and will stay there forever. When this happens, press [/FONT][/COLOR]CTRL[COLOR=#333333][FONT=UbuntuRegular]+[/FONT][/COLOR]ALT[COLOR=#333333][FONT=UbuntuRegular]+[/FONT][/COLOR]F1[COLOR=#333333][FONT=UbuntuRegular] to go to the terminal. Type in your Username and Password.[/FONT][/COLOR][COLOR=#262626][FONT=arial] 

 It won't accept my username/password. (Just to clarify; I'm referring to the information I use to log in to my computer upon normal startup. I know that seems obvious, I just want to make sure there's no doubt.)

After a moment or two, it says
>  "Login Incorrect"
"Name"
"Password"

Also, this is all on an otherwise black screen. I've tried every possible combination, to no avail.

This is *really* frustrating to me, because it's the one thing stopping me from accessing a terminal, and I feel that I if I could reach the terminal, I could fix the issue.


Any help would be greatly appreciated, and once again, if this is in the wrong place and needs to be moved, that's okay....as long as I can get it solved.[/FONT][/COLOR]:cool:

---

### Post by oldfred on 2013-09-23
Welcome to the forums.

It has to be the same user name & password. Sometimes something obvious like caps key on as case is also important and name is normally lower case. You do not see password as you type, so you are blind typing it. I usually keep my home desktop with a simple password as it is less important.

If you can get into system with low graphics, then you may just need to install proprietary driver. But that will also ask for user name & password.
You should be able to go to system settings and additional drivers. In 12.04 that was a separate icon, but newer versions it is a tab under software updates or something. I still am running 12.04.

---

### Post by Jimmy_Conway on 2013-09-23
Thanks for the welcome.

See, that's the problem. I am using the correct name and password, but the system is telling me that it is incorrect.

---

### Post by oldfred on 2013-09-23
There is only one name, password combination.

 [https://help.ubuntu.com/community/LostPassword](https://help.ubuntu.com/community/LostPassword)
[http://www.psychocats.net/ubuntu/resetpassword](http://www.psychocats.net/ubuntu/resetpassword)
[http://askubuntu.com/questions/140513/how-can-i-regain-admin-privileges](http://askubuntu.com/questions/140513/how-can-i-regain-admin-privileges)

---

