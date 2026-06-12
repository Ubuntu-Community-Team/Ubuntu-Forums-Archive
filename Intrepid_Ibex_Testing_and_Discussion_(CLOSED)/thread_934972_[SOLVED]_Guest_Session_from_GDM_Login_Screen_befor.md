---
title: "[SOLVED] Guest Session from GDM Login Screen before X Start"
date: 2008-10-01
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by wilsong on 2008-10-01
I would like to have Ubuntu Intrepid Ibex 8.10 set up that when at the first startup screen, i can login, or a guest can click and enter no password and use the guest session 

It doesnt make much sense to me that they would have to log into my session, (having to know my password) and then click on the users in the top and then choose guest session? 

I would also like if i were to go away from my pc, and the screen saver came on, someone could click and go to the guest account, and use it when i am gone.  That would make the most sense to me ? Am i Wrong here? Does this seem right to anyone else? Am I doing something wrong?

---

### Post by forumache on 2008-10-01
What you say makes sense to me too.

---

### Post by olskar on 2008-10-01
I most certainly agree, my guess is that the solution they have chosen in the first place makes it hard to achieve this because I don't think they haven't thought about it

---

### Post by wilsong on 2008-10-01
> **olskar said:**
> I most certainly agree, my guess is that the solution they have chosen in the first place makes it hard to achieve this because I don't think they haven't thought about it

Wow this really isn't cool... I wonder who or what idea was behind having a guest session, I cant find any thing about it really, I really would like to see the guest on the first login screen where i put in my user name and password, 

But when i click, System, Administration, Login Window (gdmsetup) and i click on Users, I unchecked Include all users from /etc/passwd  

this gave me the ability to add myself to the include side.. and i tried to add guest but i get this error 

"The guest user UID is lower than allow minimalUID" 

and i dont even see my own login to select either, which sort of bites, i dont mind typing in my login username, but i would much rather be able to click and type password only, and have my girlfriend be able to click guest, and use the computer without me having to worry about her having permissions to mess anything up.. 

If i leave it logged into my account i could show her how to launch a guest session but i really think that defeats the purpose.. I could make her another account, but i dont want to set an extra up (i really dont think i should have to isnt that the purpose of a guest account? ) 

Anyone with thoughts or ideas please advise?

---

### Post by wilsong on 2008-10-01
> **forumache said:**
> What you say makes sense to me too.

I am glad someone agrees with what i am saying, hrmm :/

---

### Post by wilsong on 2008-10-02
I found a page that said Martin Pitt helps with the guest session, i am going to see if i can email him, hopefully he will be able to see if theres some way we can have this work this way, does anyone else thing this would be a nice feature?

---

### Post by pingpongboss on 2008-10-02
The point of having a user explicitly start a guest session is because of security. This way, you know that "guests" aren't messing with your computer when you're not around.

At least that's the idea. I'd also like an option of just logging into a guest session from GDM.

---

### Post by wilsong on 2008-10-02
> **pingpongboss said:**
> The point of having a user explicitly start a guest session is because of security. This way, you know that "guests" aren't messing with your computer when you're not around.

At least that's the idea. I'd also like an option of just logging into a guest session from GDM.

I guess the security aspect, you could set up the security that only root could enable it to even be allowed, and then once root has allowed it, it becomes an option, and then you could use it. I like that someone can use the system but have VERY LITTLE PRIVILEGES (just to get on the internet, and small stuff like that) 

Of course, Guest only be able to login from the "console" (physical pc) not remote or anything but i am glad you like to see this feature i hope Mr. Pitts Will be able to take this suggestion and review it. I really hope this comes out.

---

### Post by forumache on 2008-10-03
Thinking about this... I come to realise that it may make sense the way it is.

For example, if my wife might use the computer to check her email, I would make an account for her. This way she will be able to save her bookmarks, passwords, documents and find them next time. For her it makes sense to be able to login from gdm.

A friend comes to my house and he wants to check his email. I am at home and logged in. I will select the guest session and let him check.

The only inconvenient is when a friend comes to my house and my computer is shut down or I am logged off or the screen is locked. He has no business of using my computer alone then, sorry. I would need to login and let him use the guest account. For every other frequent user, make an account.

Yes, it would be nice to have an option to allow guest from shutdown/logged off/locked, although I wouldn't use it.

I guess I reverted my original opinion ;)

---

### Post by wilsong on 2008-10-03
> **forumache said:**
> 
The only inconvenient is when a friend comes to my house and my computer is shut down or I am logged off or the screen is locked. He has no business of using my computer alone then, sorry. I would need to login and let him use the guest account. For every other frequent user, make an account.


Ok, think about this, HOW ABOUT having the CHOICE to CHOOSE! I would like to have someone to be able to log into my computer when I am not around as a GUEST! I would much rather anyone use my computer under a guest account. Can we make some way to accommodate both!? I am sure it can be? Some how some way ;)

---

### Post by forumache on 2008-10-03
> **wilsong said:**
> Ok, think about this, HOW ABOUT having the CHOICE to CHOOSE! I would like to have someone to be able to log into my computer when I am not around as a GUEST! I would much rather anyone use my computer under a guest account. Can we make some way to accommodate both!? I am sure it can be? Some how some way ;)

From my previous message:
[QUOTE=forumache]Yes, it would be nice to have an option to allow guest from shutdown/logged off/locked, although I wouldn't use it.[/QUOTE]

I am pro choice ;)

From Feasibility Study episode in The Outer Limits:
"For centuries philosophers and theologians have debated what it means to be human. Perhaps the answer has eluded us because it is so simple. To be human is to choose."

---

### Post by Locke_99GS on 2008-10-03
I'd like the *option* of logging in as guest from the chooser, as well.

---

### Post by wilsong on 2008-10-03
> **forumache said:**
> From my previous message:
I am pro choice ;)


Haha, and i need glasses.. Locke_99GS I am hoping to hear from one of the guys helping to program all the features for Guest Sessions, hopefully he will contact me or view this forum, anyone else played around with Guest Sessions much?

---

### Post by MJWitter on 2008-10-03
From [Guest Session settings:]("http://ubuntuforums.org/showthread.php?t=936742")

I really like the idea of the guest session but was wondering if there is any way to make changes to its defaults?

For example, when i open Firefox in the guest session i have to choose my settings for Add-ons. When I log out and open a new Guest session I have to do it all over again.

So it would be great if I could set things like that by default and, say, add specific icons to the desktop.

---

### Post by wilsong on 2008-10-03
Well, I just got through having a chat with Martin Pitt (aka pitti on irc) [https://launchpad.net/~pitti](https://launchpad.net/~pitti) 

> Guest session

The User Switcher panel applet (package fast-user-switch-applet) now provides an extra entry for starting a Guest session (by Martin Pitt). This creates a temporary password-less user account with restricted privileges: the account cannot access any users' home directories, nor permanently store data. This is sufficiently safe to lend your laptop to someone else for a quick email check 


Martin and I had a chat about these ideas on IRC, see attached chat.txt if you want to see the full chat, 

basically he said "we don't want to configure this kind of "everyone can use my computer" by default" 

Though it would be nice to have the option to enable a guest account that doesn't save files and clears settings on logoff (like i would i like) i would of course not want someone able to use the system if it was stolen (which a guest like that would allow). I am going to mark this as solved because after talking to Martin he suggest creating a regular account "called guest" and not setting a password, which would resolve a few of our request for features though I was aware of this I was hoping to alter the guest account for more usefulness. (because now its something i will probably never use). 

If you have any Q , Comments Or Want to Post Feel Free! Love to Hear your ideas!

---

### Post by taavikko on 2008-10-03
IMHO thats better idea to create guest-account to machines held at home, than to enable gdm-guest-session, via login.

I'm also wondering about altering setup to guest-session,
but what i've gathered, it creates random guest-xxx session.
So it would be difficult to change the defaults.

Maybe via somekind of a guest-session-daemon?


But there's an ugly bug at the moment
[https://bugs.launchpad.net/ubuntu/+source/gdm-guest-session/+bug/269921](https://bugs.launchpad.net/ubuntu/+source/gdm-guest-session/+bug/269921)
So i'm not lending any of mine laptops to no-one :(

---

### Post by wilsong on 2008-10-04
> **taavikko said:**
> IMHO thats better idea to create guest-account to machines held at home, than to enable gdm-guest-session, via login.

I'm also wondering about altering setup to guest-session,
but what i've gathered, it creates random guest-xxx session.
So it would be difficult to change the defaults.

Maybe via somekind of a guest-session-daemon?


But there's an ugly bug at the moment
[https://bugs.launchpad.net/ubuntu/+source/gdm-guest-session/+bug/269921](https://bugs.launchpad.net/ubuntu/+source/gdm-guest-session/+bug/269921)
So i'm not lending any of mine laptops to no-one :(


I think that guest sessions will always be buggy, I just dont feel theres a way that they will be able to protect the system enough and still give people access to the internet, someone will find some way to use some port, or some function, i like the idea, but it just seems that it might be doomed to issues and problems. 

Like when i used it i was able to go login with guest sessions and read a file in my own home directory.. i couldnt delete it, or read other ones.. but for some reason 1 file i could, and i looked at the permissions and it was owned by me not guest or anything.. i heard on launchpad theres a bug that lets people to read the file off the users home dir.. i am sure there will be other issues but i guess ill end up setting up another user account for other people i wish to use my comp :)

---

### Post by taavikko on 2008-10-04
> **wilsong said:**
> i heard on launchpad theres a bug that lets people to read the file off the users home dir.. i am sure there will be other issues but i guess ill end up setting up another user account for other people i wish to use my comp :)

Yep. the one I just referred to...

In *nix you can always view the contents of /home
Default rights are 755 for directories and 644 to files.
I'll leave the calculating to you
4=read
2=write
1=execute
Thats much more secure than resticted rights of gdm-guest-session ;)

The bug in question, is marked as security vulnerability.
The basic idea of gdm-guest-session is absolutely marvelous.
Once they get it to work.

---

