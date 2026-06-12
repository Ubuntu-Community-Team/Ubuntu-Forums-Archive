---
title: "Switch user, log out -&gt; Black screen. Anyone else?"
date: 2010-04-08
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by QwUo173Hy on 2010-04-08
Can anyone confirm this? Just switch users and then log out of that users account. The screen goes black for me and there's no way back. I don't even know what to report against exactly so if anyone can help there that would be great too.

Thanks,
Jarlath

---

### Post by foobar66 on 2010-04-10
Hmm ... I may have the same issue. My screen is not black. Top half is black, bottom half shows horizontal lines white/black.

---

### Post by QwUo173Hy on 2010-04-10
It's no longer a problem for me.. it seems. Maybe an update fixed it, there have been many since I first posted. I'll keep an eye on it.

---

### Post by QwUo173Hy on 2010-04-10
Cancel that, it happened again. At this point I have no idea how to test this or pin it down. The logouts that caused the problems were actually being used by someone for a period of time. When I tried to reproduce them  I was logging in and out almost immediately.

---

### Post by Didius Falco on 2010-04-10
Try making a new account and see if you get the same behavior, would by my suggestion. If that person is no longer using that account, delete it, too.

If the same thing occurs, you'll know that it's something to do with logging out, which would be associated with the "gnome-session"  package. You should then file a bug report by hitting ALT+F2, and typing ```
ubuntu-bug gnome-session
```.

There is more information on filing bugs here:

[https://help.ubuntu.com/community/ReportingBugs](https://help.ubuntu.com/community/ReportingBugs)

Good Luck!!

Didius

---

### Post by QwUo173Hy on 2010-04-10
Thank you Didius - that's what I needed!

---

### Post by jimbop99 on 2010-04-10
I have the same problem. A minor work around is to log out then switch user.

---

### Post by QwUo173Hy on 2010-04-10
> **jimbop99 said:**
> I have the same problem. A minor work around is to log out then switch user. Thanks jimbop -  if it's still an issue in the final release I might remove the option from the menu (if possible) on my friends machines to prevent problems.

Step 1 of course is to report it, which I will.

---

### Post by demauk on 2010-04-11
Hi, Jarlath,

I have the same problem, and I also cannot pin it down.

To anybody else, who might know anything, it doesn't seem to be related to logging out, but to logging *back* into the first account.

For example, my wife wanted to print something from the test machine, but I hadn't set up the printers yet. So I took the machine, switched into my (sudoer) user, and started setting it up. My printer is a bit new, so I had to hunt down (again) the manufacturer's linux drivers. When I was done (about 20 minutes later) I *switched* to my wife's account, and I got a blank screen. The screen is on, but it's like there's no signal being sent to it.

Another important detail, if I *switched* to my wife's account, I could switch back to mine by using Ctrl-Alt-F7 (or something). But if I logged out of my account, I couldn't do anything.

*Another important thing:* Once on the blank screen, I started banging some keys (TAB, Enter, my wife's password), and then the machine *shut itself down!*

So, I don't think it's gnome-session. It might be gnome-screensaver, which is conveniently set to "blank screen"!

---

### Post by QwUo173Hy on 2010-04-11
That's exactly right demauk - managed to get a shutdown and I believe my keystrokes were being processed. I'll have to test that too to be sure. I think I did Password -> Enter -> Power button (which gives a shutdown menu) and Enter again (which confirms the Shutdown option.

---

### Post by QwUo173Hy on 2010-04-11
Bugged [https://bugs.launchpad.net/ubuntu/+source/gnome-session/+bug/560911](https://bugs.launchpad.net/ubuntu/+source/gnome-session/+bug/560911)

---

