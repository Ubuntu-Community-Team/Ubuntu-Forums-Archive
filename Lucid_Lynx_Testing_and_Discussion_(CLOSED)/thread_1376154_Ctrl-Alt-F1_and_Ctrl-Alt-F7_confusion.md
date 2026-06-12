---
title: "Ctrl-Alt-F1 and Ctrl-Alt-F7 confusion"
date: 2010-01-08
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by ranch hand on 2010-01-08
These commands seem to be fairly useless to me as they do not seem to work.

I am having problems with my 9.10>10.04 upgraded version.  It will not boot.  So when the bugger just stops dead I try these commands.  Nothing happens for either one.

Boot from recovery and the bugger stops short and there is no promt.  So I try to use Ctrl-Alt-F1.  This gives me nothing.  Try Ctrl-Alt-F7 and this takes me to a blank page with the "can't start session message" (the one that pops up on all versions during boot right before the login page comes up).  Just sits there.

So I hit Ctrl-Alt-F1 and it takes me back to the incomplete recovery boot text page.

Am I doing something wrong?

I did try Ctrl-Alt-F1 at the login page on another install that insists on "low graphics".  This was just as useful.  It took me to a black screen.  Ctrl-Alt-F7 did take me back to the login through the low graphic messages.  So basically this looks like a waste of time to me.

I have a hard time believing that these commands exist if all they do is let you dick around to et back where you were.  I have to be missing something or completely misunderstanding what these commands are for.  Or I am using them at the wrong time.

---

### Post by VMC on 2010-01-08
Research [**Magic SysRq key**]("http://en.wikipedia.org/wiki/Magic_SysRq_key") hand commands:

[**Alt+SysRq+REisUB**]("http://fosswire.com/post/2007/9/fix-a-frozen-system-with-the-magic-sysrq-keys/") < Lift the elephant. 

Alt_SysRq+b = boot

Tip: "**R**aising **S**kinny **E**lephants **I**s **U**tterly **B**oring"

---

### Post by ranch hand on 2010-01-08
Yes, I use them quite a bit although I have trouble with the first one due to hands that have seen the inside of too many heifers in freezing weather (not to bad when you are in there but real tough when you finally get the calf out and are working on getting it going while wet to the bare shoulder).

---

### Post by Ibidem on 2010-01-09
You're not doing anything "wrong", just not getting everything:
In text mode, <Alt>+F1 to F6 switches among the *six* virtual terminals, tty1-6.
X starts on tty7 (<Alt>+F7).
But once you get in X, you need the <Ctrl> to get to text mode.
The first terminal (Ctrl+Alt+F1) is your original "login" terminal--so it will be busy until the startup scripts, including X, finish.
That means you need Ctrl+Alt+F2, F3, F4, F5, or F6 to get to a terminal.
Then it's the login prompt, since Linux is multi-user.
I believe if you boot with a "single" argument you autologin, or if you skip the standard init (add " rw init=/bin/bash" to the kernel options), you only have one terminal (I THINK)--IIRC, init sets up terminals.
Don't quote me on the last, though.
But add that "rw init=/bin/bash" in GRUB, if you can't start X.
Hope this helps,
Ibidem

---

### Post by ranch hand on 2010-01-09
> **Ibidem said:**
> You're not doing anything "wrong", just not getting everything:
In text mode, <Alt>+F1 to F6 switches among the *six* virtual terminals, tty1-6.
X starts on tty7 (<Alt>+F7).
But once you get in X, you need the <Ctrl> to get to text mode.
The first terminal (Ctrl+Alt+F1) is your original "login" terminal--so it will be busy until the startup scripts, including X, finish.
That means you need Ctrl+Alt+F2, F3, F4, F5, or F6 to get to a terminal.
Then it's the login prompt, since Linux is multi-user.
I believe if you boot with a "single" argument you autologin, or if you skip the standard init (add " rw init=/bin/bash" to the kernel options), you only have one terminal (I THINK)--IIRC, init sets up terminals.
Don't quote me on the last, though.
But add that "rw init=/bin/bash" in GRUB, if you can't start X.
Hope this helps,
Ibidem
Ah, I was under the impression that Ctrl-Alt-F7 started gdm.

I am a little ignorant about the whole tty deal.  No i am real ignernt about it.  This is different levels of permissions is it not?

I am not on that drive right now as I use a stable OS (Stoner Edition 1.0 - 9.04 respin) at night so I can go to bed and let boinc run and not wake up to a frozen system or some other FUN.

In the morning  will update from one of my installs and then give some of the other ttys a chance to come up.  This would be a good thing.

The OS that is down is my designated "production" OS for daytime.  I did get my boinc transfered to another 10.04 and any files I may want are just a nautilus visit away too, but I would like to get it going.  It is my oldest 10.04.  9.01>tool chain (first day) upgrade.  Do not want to screw that one to badly.

Thanks a bunch.  I believe that your information is putting things together in my head from what I have read about tty so that I may, at least, have an idea what I need to find out and I can certainly have more confidence in trying to get a text login up.

---

### Post by zika on 2010-01-09
Just think about tty as a terminal connected to a *nix mainframe. On tty{1,2,...,6} You have text-based monitors. On tty{7,8} You have  a graphics display. Everybody with username and pass can sit on tty1...tty6 and do whatewer he/she wants but in text-mode. On tty{7,8} You get the whole deal: GDM or KDE... At any given time all tty can be active, just like in old days...
You switch between them with Ctrl-Alt-Fi, i=1,...8.
You login as ususal, exit as usual, as with Terminal in GDM.
While in tty You can kill GDM, restart it... (sudo service gdm {start,stop,restart})
Feel free to ask about whatever I missed. I might have an answer.

---

### Post by ranch hand on 2010-01-09
Yes, I am getting the picture now.

I actually was doing  one thing wrong in that I was hoping this would get me logged in.

It is going to be tough for that to happen as the problem is that x refuses to start.

I see that we have been getting updates for all xorg related things a couple times a day for a while too.  I have  updates running now for that OS in hopes something will work.

I have, from this, learned a little about tty stuff that will come in handy.  I can see, better than before, what it can do for me.  Could be real handy.

---

### Post by Ibidem on 2010-01-09
I would go to tty2 (or another tty), login, and run startx.  If X refuses to start, look at the error messages (~/.xsession-errors); if it says it could not lock the .Xauthority file, one remedy is simple:
rename, move, or delete the file
I figured that out a few days back (on VirtualBox) after going
sudo -s
startx
 (since sudo doesn't change $HOME, I ended up with root owning .Xauthority)--with my mistake, it took "sudo rename" to get things right.
Then I had to delete ~/.Mozilla/, since I ran firefox too.
Hope this helps, 
Ibidem

---

