---
title: "Why when i log off i don't get the panel that let you change between gnome and kdm?"
date: 2010-03-18
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by aviramof on 2010-03-18
Let me explaine the bug more clearly now if i use auto login meaning disable the password box at the log off windows i can't replace between DM'S. 
 
For instance between ubuntu GDM and xubuntu XFC the cause is that the bottom panel simply don't appear unless i start typing password and that is the bug pure and simple. 
 
[https://bugs.launchpad.net/ubuntu/+source/gdm/+bug/540775](https://bugs.launchpad.net/ubuntu/+source/gdm/+bug/540775)

---

### Post by meborc on 2010-03-18
i think the panel "appears" when you start to type your password... at least it seems to me like this... will test to be sure :)

CONFIRMED: as soon as you hit enter or click on user, the panel with options about keyboard and DE will appear

---

### Post by aviramof on 2010-03-18
the problem is i diabled in account and users the need to enter password all the time which means it never appears becasuse when i press enter it's already log in i can restore the option to ask for password of course but this is still a bug and that is something that need to be fix.

---

### Post by meborc on 2010-03-18
> **aviramof said:**
> the problem is i diabled in account and users the need to enter password all the time which means it never appears becasuse when i press enter it's already log in i can restore the option to ask for password of course but this is still a bug and that is something that need to be fix.

that is interesting... and serious bug... report it to launchpad, link here, and I will comment on it too

---

### Post by ankspo71 on 2010-03-18
It effects me too. The disable password feature is something I don't use, so I never noticed.

---

### Post by aviramof on 2010-03-18
i don't need it because i'm the only user with access to this computer so why do i need it?

here is the bug report link i'm hopping i did it right this time:
[https://bugs.launchpad.net/ubuntu/+source/gdm/+bug/540775](https://bugs.launchpad.net/ubuntu/+source/gdm/+bug/540775)

---

### Post by meborc on 2010-03-18
> **aviramof said:**
> i don't need it because i'm the only user with access to this computer so why do i need it?

here is the bug report link i'm hopping i did it right this time:
[https://bugs.launchpad.net/ubuntu/+source/gdm/+bug/540775](https://bugs.launchpad.net/ubuntu/+source/gdm/+bug/540775)

ok, added "affects me" and a comment to the bug

---

### Post by aviramof on 2010-03-18
thank you very much let's hope it would be fix in the near future.:)

---

### Post by meborc on 2010-03-18
I always hated the fact that the selection bar only appears after you click on user... it seemed like the page is still loading itself :)

please people, test it and comment on the bugreport... then it might get fixed before release!!!

---

### Post by ankspo71 on 2010-03-18
I used the 'it effects me too' option, and then left a comment.

---

### Post by Psumi on 2010-03-18
I have a feeling that instead of fixing this bug, they'll force the enabling of passworded login and just make a guest account for no passworded login like with Windows.

Developers cater to mainly businesses, schools, etc. because that's mainly who uses linux distros. Hence, they see more people using passwords than not.

---

### Post by aviramof on 2010-03-18
they should simply let it appear the moment you log off or wants to log on that's all.

---

### Post by meborc on 2010-03-18
> **aviramof said:**
> they should simply let it appear the moment you log off or wants to log on that's all.

i totally agree... the option to switch desktop environment (even when straight from booting) should appear WITHOUT the need to select ANY user

the way it works at the moment hinders usability and is not intuitive (how should i know that i need to click on my name before I can select the environment I want to load?)

---

### Post by aviramof on 2010-03-19
let's hope they want forget to fix it like so many other things for exemple url support.

---

### Post by meborc on 2010-03-21
> **aviramof said:**
> let's hope they want forget to fix it like so many other things for exemple url support.

we need more people commenting on the bug and marking it "affects me too"... the more the bug gets publicity, the bigger the chance this serious flaw gets fixed

---

### Post by Psumi on 2010-03-21
> **meborc said:**
> we need more people commenting on the bug and marking it "affects me too"... the more the bug gets publicity, the bigger the chance this serious flaw gets fixed

Either that, or the more frustration the devs have, and will physically delete the bug.

---

### Post by aviramof on 2010-03-21
this bug is a genuine bug there is no reason that they want fix it but keep commenting on the bug report page.
 
[https://bugs.launchpad.net/ubuntu/+source/gdm/+bug/540775](https://bugs.launchpad.net/ubuntu/+source/gdm/+bug/540775)

---

### Post by kansasnoob on 2010-03-21
Sorry, maybe I'm being dense about this but if you've chosen to "auto-login" at what point would you be able to "select session"?

I use "auto-login" also, so if I want to change desktop environments I just restart X w/Ctrl+Alt+Bkspc (which I enabled in Sys > Pref > Keyboard), then I click on my username and change session, and of course I must then enter my password.

It seems to me like you want a system that never requires a password and I doubt that will be taken seriously by any of the devs.

---

### Post by MacUntu on 2010-03-21
Yeah, I too cannot confirm this behaviour. If I log off with my auto-login user, I have to click on my user name and provide a password in GDM (therefor being able to choose language/session type).

---

### Post by aviramof on 2010-03-21
I don't think you understand if i disable the need to enter password when i'm login then i can't change sesseion when i press on the log off option in the top panel or if you like hot key's when i press alt-k-Sysrq which are the most basic options to log off from the current user accont because i can't enter password there without disable the auto login or by enabling a special hot key's like Ctrl+Alt+Bkspc that you said.

try to log off the normal way via the button or alt-k-Sysrq and you would understand what i mean. 
if you really use auto login you will never get the panel of switiching sessions.

---

### Post by kansasnoob on 2010-03-21
Just tried it. I click on logout and it asks me if I want to logout or switch user. I click on logout and I get dumped back at gdm (maybe the behavior is different if you're using kdm).

Then in gdm I click on my username and I get the option of changing session, then after doing so I must enter my password.

---

### Post by meborc on 2010-03-21
> **kansasnoob said:**
> Just tried it. I click on logout and it asks me if I want to logout or switch user. I click on logout and I get dumped back at gdm (maybe the behavior is different if you're using kdm).

Then in gdm I click on my username and I get the option of changing session, then after doing so I must enter my password.

that is true for those users who have password login enabled, but this bug is about those who don't...

how to reproduce the bug:
1) create new test user with system-administration-users...
2) add a new password to this user, but tick the "log in automatically" box
3) log out and try to log in with the new user using a different desktop environment

as soon as you click on the new user, gnome will load... there is no option to choose any other DE

this is with gdm as stated in the bug report, NOT kdm

suggested fix: have the bar with keyboard and DE selection appear as soon as GDM loads, NOT when you click on any user

this needs to be fixed!

please comment here - [https://bugs.launchpad.net/ubuntu/+source/gdm/+bug/540775](https://bugs.launchpad.net/ubuntu/+source/gdm/+bug/540775)

---

### Post by MacUntu on 2010-03-21
-- deleted --

---

### Post by MacUntu on 2010-03-21
-- deleted --

---

### Post by ankspo71 on 2010-03-21
Hi,
It's not the auto login feature in question. That works fine for me and I am allowed to log out and change session type. 

It's the disable enter password feature found in "users and groups", the place where you add and remove users. :D See screenies:

---

### Post by MacUntu on 2010-03-21
Thanks, didn't even know about that. Yes, confirmed, adding myself to the bug report

---

### Post by meborc on 2010-03-22
> **MacUntu said:**
> Thanks, didn't even know about that. Yes, confirmed, adding myself to the bug report

nice :) we now have 5 people who are affected by this

it is easy, please support fixing this bug by adding yourself as affected

it seems like a "design" feature... how the bar "automagically" appears when a username is clicked - I would rather have usability than design, though

---

### Post by aviramof on 2010-03-22
> **meborc said:**
> nice :) we now have 5 people who are affected by this

it is easy, please support fixing this bug by adding yourself as affected

it seems like a "design" feature... how the bar "automagically" appears when a username is clicked - I would rather have usability than design, though

i too prefer usability over design:)

---

### Post by meborc on 2010-03-22
> **aviramof said:**
> i too prefer usability over design:)

great, sometimes i feel that i would rather have a text only boot and log in, then starting X with startx instead of all that plymouth boot weirdness and gdm slowness and non-configurability

---

### Post by aviramof on 2010-03-31
is there any news about this bug?
[https://bugs.launchpad.net/ubuntu/+source/gdm/+bug/540775](https://bugs.launchpad.net/ubuntu/+source/gdm/+bug/540775)

---

### Post by meborc on 2010-03-31
> **aviramof said:**
> is there any news about this bug?
[https://bugs.launchpad.net/ubuntu/+source/gdm/+bug/540775](https://bugs.launchpad.net/ubuntu/+source/gdm/+bug/540775)

unfortunately, people who are affected by this bug (or actually use the computer in a way that brings this bug into light) is very small... 5 at the moment

even I'm not really affected because I use password to log in and have only one DE anyway :) 

but this is not the point, this should be fixed! only way - log in to launchpad, comment on the bug, mark it "affects me" and hope that the devs notice it

---

### Post by autark on 2010-03-31
I'm sorry to have to say this, but the bug description probably doesn't help getting the bug fixed. I think most people reading the description will just skip it, because it is virtually unreadable. Somebody who cares about the bug should edit the description, explaining the problem more to the point. Using more than one sentence would probably help, too.

And, while you're at it, you could improve the bug title as well.

---

### Post by aviramof on 2010-03-31
edited the bug with better explination from the comments but i think that it's very strange that from all the people who viewed this thread only five says it effect them i'm sure that everyone would discover that it also effect them if they disable the need to enter password and enable auto login.

---

### Post by aviramof on 2010-03-31
i don't understand so many people viewed this thread and so many replied in this thread why does no one press the this bug effect me too button???

it's a genuine bug that sooner or later might effect everyone after all.

---

### Post by meborc on 2010-03-31
> **aviramof said:**
> i don't understand so many people viewed this thread and so many replied in this thread why does no one press the this bug effect me too button???

it's a genuine bug that sooner or later might effect everyone after all.

maybe it is just us 5 who follow this thread and have read it so many times already :)

but yes, please voice your opinions on this bug!

---

### Post by aviramof on 2010-03-31
well i guess we can only hope that the final lucid version would not stay with such an obvious bug because i don't think it would look very good to the ubuntu developers.

---

### Post by meborc on 2010-04-01
> **aviramof said:**
> well i guess we can only hope that the final lucid version would not stay with such an obvious bug because i don't think it would look very good to the ubuntu developers.

Yeah, I still think the design team really wanted the fade in selection bar appearance... I admit, it is cool, but it just does not work well with no password logins

---

### Post by MacUntu on 2010-04-01
> **aviramof said:**
> well i guess we can only hope that the final lucid version would not stay with such an obvious bug because i don't think it would look very good to the ubuntu developers.

I doubt a lot of users are using this "don't ask" option.

---

### Post by aviramof on 2010-04-01
it's still a valid bug that need to be fixed.

---

### Post by aviramof on 2010-04-21
Is there any news about this bug i'm thinking of installing xubuntu again in parallel to ubuntu but the lack of easy method to switch between the two without disalbe auto login so sort diture me from doing so so is there any news?
 
thanks in advance.

---

### Post by Mr. Picklesworth on 2010-04-21
Well, as a workaround, you can enable passworded login, then head to System Administration › Login Screen and enable "Log in automatically" with a short timeout. It won't unlock your default keyring when you log in (don't know if your current approach does… I assume it doesn't), but GDM should behave a bit more smoothly.

In my opinion, login should always be a two step process, passworded or not, where the second step is a confirmation screen if not an authentication screen. It can be really ugly to log in to the wrong account by accident.
(Granted, such a move would probably provoke intense fury, although the feature hasn't been in for long enough — yet — that people could become settled in to it).

---

### Post by aviramof on 2010-04-21
I don't have other accounts that's what people don't always understand this is my own not portable computer 
that no one but me have access to it so why would i want to type passwords all the time just to login to my one and only personal account?
 
As for session keyring i have set it as unsafe meaing no password at all and i think it's working fine expect when there is problem with the 
communication with keyring daemon i have made a bug report about that in launchpad that you can check.
 
But i will check your workaround thanks for the idea:)

---

