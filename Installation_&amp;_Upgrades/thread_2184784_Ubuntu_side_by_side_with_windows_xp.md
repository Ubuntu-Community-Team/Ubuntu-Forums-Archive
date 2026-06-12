---
title: "Ubuntu side by side with windows xp?"
date: 2013-10-30
forum: Installation &amp; Upgrades
---

### Post by tomsubt on 2013-10-30
I may have posted this in the wrong section before but here it is>>

Hi,  I tried to install ubuntu next to windows xp but now when I turn off the pc and restart I cannot get to windows anymore, I did however have a ubuntu screen come up and said  I have both on my pc.
But here is the problem, not only can I Not get windows xp on the startup, I still have to put the ubuntu cd in the pc to make it work, so I figured it did not completely install so on installing it again I keep getting stopped at the "Install Who Are You" screen, I put my computer name in and check mark  "automatic sign in" then I hit Continue but Nothing happens I waited for over have hour and the screen is still sitting there. What can I do to get ubuntu installed and maybe get windows xp as a dual boot like its suppose to do? Any  help would really be appreciated. Thanks

---

### Post by deadflowr on 2013-10-30
Silly question, but did you make a password?

---

### Post by tomsubt on 2013-10-30
Very Good Question as a matter of fact I did not because I wanted to log on without one, do I have to have one? Thanks

---

### Post by deadflowr on 2013-10-30
Yes

---

### Post by tomsubt on 2013-10-30
deadflowr,  Thank You, I put the password in and its now installing I hope correctly. Being new at this I hope I can come back to ask other questions, this is really new to me but I like ubuntu alot. until later (maybe in a few minutes)"LOL"

---

### Post by deadflowr on 2013-10-30
In general, Ubuntu sets the first user with admin rights, giving that user the ability to install, remove or change software and the system.
Since Ubuntu locks the root account, the first user has the right to use sudo to access the elevated rights.
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)
The autologin feature simply lets the user login without the need to use the password.

You'll probably find, once you've setup your system to the liking that fits your needs, the password will be of little use.
Regardless of how often you use it, do not disable it.
It can cause problems when you do.

Good luck, though, and hopefully you'll have a functioning dual-boot when done.

---

### Post by tomsubt on 2013-10-30
Deadflowr,  Thanks for the links and info. I will be looking into them tomorrow.

I think my dual boot is worthless, I clicked on xp at boot and it brought up the hp recovery instead of windows so i guess it got messed up somehow when installing ubuntu. 
The pc was given to me by a friend and they accidently remove the D drive which is the Recovery with the !386 files in it and the recovery got pretty far into completing but a message came up and said it could not find this file so I said Ignore and it just kept trying to install windows but after a couple of hours I just shut it down it got to 87% and would not install any further.
So I guess I could never get xp back on the pc again there is No System Recovery Disk to it, the got lost, and Hp said they dont have them anymore for the  HP a1010n desktop, But I guess it dont matter it will be unavailable by April and I plan on using Ubuntu anyway.
Thanks, Later, Tom

---

### Post by tomsubt on 2013-10-31
If you could tell me how to do to things, One how to bring up the terminal prompt, and Two how to install Pidgeon(can I use yahoo messenger with Pidgeon)?  Thanks

---

### Post by tomsubt on 2013-10-31
ok  I figured out how to get to the terminal prompt but when I type in "Sudo apt-get install pidgin"  it asks for my sudo password. How do I get a sudo password or can I some how bypass sudo passwords? Thanks

---

### Post by tomsubt on 2013-10-31
PS: It wont let me type anything in the window either??

---

### Post by tomsubt on 2013-10-31
I figured it out and installed pidgin it took time to process all but it is now done, but I dont know how to bring up pidgin and hopefully set it up for yahoo messenger can this be done if so how? Thanks

---

### Post by deadflowr on 2013-10-31
FYI
passwords are invisible in the terminal.
Just type it as well as you can remember it and press enter.

The sudo password is whatever password you made during the install.

(Unless after the install you made a new user, which seems unlikely.
And you would know if you made a new user.)

Edited: Added FYI, as the problem was resolved.

As far as getting things like pidgin to work right, you might have better help starting a new thread specifically for that subject.
People who know what to do won't be looking for threads with titles about installation problems.
I ,myself, am clueless on issues with pidgin, so...

---

### Post by tomsubt on 2013-10-31
FYI     ok Thank you, I will start another thread about Pidgin

---

### Post by winlinuser-gmail on 2013-10-31
Hi Tomsubt - the Sudo password is the same as your user password.  In other words, the system is checking that the command is coming from the (admin) user.  When you enter your password it will not show anything on the terminal screen as passwords are TOTALLY invisible (I found this myself only a week ago).  
For your email I have found Thunderbird (already installed as standard) to be very good and would not bother installing others until you try it - it's very easy to set up.
Hope it all goes well.

---

### Post by tomsubt on 2013-10-31
Hi  winlinuser-gmail   Thanks for the tip I will look into thunderbird too, before I go to start another thread about pidgin does anyone know how long it takes to install all of it, its been running now for an over an hour and when I try to close the terminal window it states that it is still processing pidgin and if I close out now I will lose all so I keep cancel the exit.  How long does it take or is there something wrong with the install? Thanks

---

### Post by winlinuser-gmail on 2013-10-31
Oh, that does not sound good as its a <31Mb download.  In my experience things download and install quite quickly. Of course i depends on your broadband.
Are you installing using the software centre or a direct link?

---

### Post by tomsubt on 2013-10-31
I used the terminal prompt to install pidgin but I just noticed Pidgin is already installed but the terminal kept telling me 
the process was still installing but I think it is because I had mutiple terminal screens going at the same time before I figured out that the password was installed I forgot to close all the other term windows.
So I closed out ignoring the warning and like I said I do have pidgin installed now and I brought up two of my Instant messengers to put on it and they are google talk and yahoo messenger but the pidgin cannot connect to yahoo messenger for some reason I rechecked the username and password that I use and there is nothing wrong on that end.
Any ideas as to why pidgin cannot connect to yahoo messenger? Thanks

---

### Post by winlinuser-gmail on 2013-11-01
Hi [[COLOR=#000000]tomsubt[/COLOR]]("http://ubuntuforums.org/member.php?u=485567") - sorry, I don't use pidgin so can't help. :-(

---

### Post by tomsubt on 2013-11-01
Ok  Thanks to you and all I will start another thread with pidgin as topic!

---

