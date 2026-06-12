---
title: "Allow work without pass for sudoers not work in karmic beta"
date: 2009-10-06
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by lemmyg on 2009-10-06
Hi,
I am trying to allow work without pass to sudoers in karmic beta and it not works. In jaunty works normal.

Any one, can confirm this issue?


thanks in advance.




Linux 2.6.31-11-generic #38-Ubuntu SMP Fri Oct 2 11:06:40 UTC 2009 x86_64 GNU/Linux

---

### Post by lemmyg on 2009-10-07
Hi,

this is my /etc/sudoers archive. 


# /etc/sudoers
#
# This file MUST be edited with the 'visudo' command as root.
#
# See the man page for details on how to write a sudoers file.
#

Defaults	env_reset

# Host alias specification

# User alias specification

# Cmnd alias specification

# User privilege specification
root	ALL=(ALL) ALL

# Uncomment to allow members of group sudo to not need a password
# (Note that later entries override this, so you might need to move
# it further down)
# %sudo ALL=NOPASSWD: ALL

# Members of the admin group may gain root privileges
%admin ALL=(ALL) ALL

%sudo ALL=NOPASSWD: ALL

My user is added to sudo group. 

sudo useradd -G sudo lemmy
useradd: user 'lemmy' already exist

I think it is correct. But system still ask me for password. In Jaunty Works normaly. But in Karmic beta dont works.

---

### Post by VMC on 2009-10-07
You may or may not get help on this. If you come freshly from Windows, people tend to circumvent any password files.

I don't know your reasoning, but you may be opeing yourself up for security risks. If you need to do some work in ROOT issue ```
sudo su-
``` ,temporarily.

---

### Post by slakkie on 2009-10-07
I think it is a bad idea, but I'm not going to stop you, you will figure it out once you read the manuals.

```

%sudo ALL=(ALL) NOPASSWD: ALL

```

This should fix it, but why do you want to allow such rigorous and security compromising  methods?

Increase the default timestamp_timeout, which is 15 minutes. Become root via some other way, but plainly allowing members of the sudo group to do root stuff without ever using a password..

---

### Post by lemmyg on 2009-10-08
Thanks for the answers.
Really is an option what I use for my desktop system. When I'm working, like my user is the administrator, I tired having to enter the password. In jaunty used this option and it worked perfectly, but in karmic has stopped working. I think to have to enter password is correct to work in a company but not to work in home notebook.

---

### Post by slakkie on 2009-10-08
I still think it is a bad idea. But not stopping you.

---

### Post by anders_c_ on 2009-10-08
you could just allow root login, and always be logged in as root, it will ofcourse be a huge security risk. But the way you do it now isnt much safer.

---

### Post by VMC on 2009-10-08
> **lemmyg said:**
> I think to have to enter password is correct to work in a company but not to work in home notebook.It doesn't matter if your at home, work or at Starbucks. Your opening yourself up for attack by using root.

---

### Post by lemmyg on 2009-10-08
hi, 
thanks for reply.

In Jaunty I use this option %sudo ALL=(ALL) NOPASSWD: ALL and works well.  my question is, will this option work in karmic beta? because is not working for me.


thanks in advance.

---

### Post by lemmyg on 2009-10-08
hi,
I am a normal user.
why is it so dangerous?

---

### Post by anders_c_ on 2009-10-08
I personally think most people on these forums exaggerate, logging in as root is no more dangerous than using windows, but far more vulnerable than being logged in as normal user...every program you start will have the power to wipe your entire system!

---

### Post by seeker5528 on 2009-10-09
> **lemmyg said:**
> hi,
I am a normal user.
why is it so dangerous?

You are connected to the internet, correct?

Security is never good enough, the more doors you leave open the more chance somebody will try to take advantage while you are not looking.

If you look at the situation in Windows.

Go to a site with hacked advertising that takes advantage of a flaw in flash that you never got the security update for yet, don't click on anything, but still end up with a rogue security program that claims you are infected with a bunch of crap and to [www.whatever](www.whatever) to pay to get rid of it. Find out you can't uninstall the rogue security program and can't delete it either. Also it hit you with some stuff that hijacked the DNS so you can't go to some security related sites, get security updates, etc.... When you finally do get rid of it, no you didn't because it either insterted something randomly named in the boot up or replaced a system file somewhere with something that looks for a randomly named file, files which you find spread out through various system directories, in particular in directories it should have never been able to get to without having something pop up to ask for permission. 

UAC helps, but the mentality at MS seems to be that UAC is not a security mechanism so what people point to as flaws that still allow stuff in, aren't really security flaws in their view, don't know if that's the unanimous opinion, but that statement has come out of MS at least a couple of times. 

No matter how good the security is, the user is always a weak link, but that should not be an excuse to make it easier. Anything you run as a user has the same access to the system that you do, so if you are running as the root user or the way sudo is used in Ubuntu allow sudo to be used without requiring a password, that's a lot of access. No matter how unlikely it might seem for the above Windows example to play out on Linux at present, you leave that door open for it to happen at some point. Waiting until something happens then attempting to deal with it after the fact is a PITA, potentially costly for some people. Significantly reducing the risk at the cost of having to type in a password once in a while seems like a small price to pay.

Later, Seeker

---

### Post by lemmyg on 2009-10-10
Hi,
I greatly respect your position. but I think in my case as I navigate with a dynamic ip is very difficult for someone with enough knowledge want to hack my laptop. I think there is more chances to compromise the system by installing a package with a bug, corrupting the system, than a hacker wants to waste their time in accessing my system. Safety is important but I need to be easy to use. Enter a password for everything when I am the system administrator seems like a waste of time. Simply entering  the password when starting the session, is sufficient for me.  then I don't want ask for the password, because I'm  the administrator. I also think it wrong to use the word "windows" as wrong. "Because is windows is bad. wrong!. windows have very good thing that I would like to have in Linux. For me, windows itself is not bad, the bad are their patents. So I think that	
would be good to catch good thinks and apply in Linux, to make better.

---

### Post by slakkie on 2009-10-10
Well, remove your user and login as root, no need to configure sudo, you can safely remove it.

Basicly you are used to the Windows way of working with a PC. Do everything without having to think wheter it is actually needed.

There is a reason why Unix has a root account and normal user accounts and why you need to use a password to become the admin of a box. You are basicly violating the number one rule of Unix/Linux.

[http://www.control-escape.com/linux/lx-postinstall.html](http://www.control-escape.com/linux/lx-postinstall.html)

If you have to type in the root password multiple times a day for simple things then you might be doing something wrong... If you need to run multiple commands as root, get a propper root shell and then you can do whatever your want as root without having to retype your password everytime.

---

### Post by seeker5528 on 2009-10-10
> **lemmyg said:**
> Hi,
but I think in my case as I navigate with a dynamic ip is very difficult for someone with enough knowledge want to hack my laptop.

Whether you use a static or dynamic IP doesn't really make much difference, for those kind of attacks where people try to hack your machine. A firewall or router will block random attempts to access your machine through services that work over TCP/IP depending on what ports you have exposed to the internet.

For the example I gave, how you connect or if you use a firewall is not relevant.

If there is a known security flaw in software a lot of people use, flash, IM client, media player, whatever, and that flaw is able to be used to put something on your machine, they just have to get the stuff out there some place where you will access it.

In the Windows example I gave, they are not hacking the machines of individual users, they are hacking web sites, and once you make that connection and load the hacked content, if you are not using updated stuff that has been fixed for the security issue in question, it's game over.

It doesn't take much code to create a key logger, or create something that will download other stuff off the internet, or open a door and send word someplace that a vulnerable machine is available.

As it stands today, you *can* run as root and feel reasonably safe if your installed software reasonably up to date, but it's not a given. The more people that use Linux, and the more software that gets created for those users, proprietary software in particular, the higher the risk factor becomes.

It's a topic that gets debated endlessly and I'm not really interested in debating it, just feel like I have to chime in once in a while so people at least think about it.

Later, Seeker

---

### Post by anders_c_ on 2009-10-11
> **lemmyg said:**
> I think there is more chances to compromise the system by installing a package with a bug, corrupting the system, than a hacker wants to waste their time in accessing my system.

Running as user also protects against bugs, not only hackers. If you run a buggy program that accidentaly runs something like "dd if=/dev/zero of=/dev/sda" that would mess up your system, but if you started that program as a user nothing will happen. Some programs even runs as a unprivileged users to make it even more safe, like Apache running as "www-data" no matter how buggy that code is it will not be able to mess up your system, because www-data doesnt have write access to any critical files or folders.

---

### Post by lemmyg on 2009-10-13
Hi,
I don`t want to enter into a debate of security. I just want to know if that "%sudo ALL = NOPASSWD: ALL" is currently working in Karmic beta, because it is not working for me.

Thanks.:P

---

### Post by JRoque250 on 2009-10-17
Lemmyg,

I'm also having the same issue as you are. Anything I put in sudoers with visudo is being "ignored".... Just like your request for help here that instead is getting you lectured.

I run MythTV on my 9.10 box and it can't suspend (or halt) anymore after being idle. The log shows "sudo: no tty present and no askpass program specified". The same sudoers worked on 9.04.

Thanks,
JR

---

### Post by Aearenda on 2009-10-17
First let me echo that this is a really bad idea. By doing this you open your system completely to any malware you encounter while browsing the web, which is able to switch to root from your user without hindrance.

Second, I'm guessing that your sudo group is empty, even though you have tried to add your user.
```
grep sudo /etc/group
```This should reveal the answer.

---

### Post by lemmyg on 2009-10-18
Hi, 
I fixed finally with %"myusergroup" ALL=NOPASSWD: ALL. 
%sudo ALL=NOPASSWD: ALL don't work for me.

---

### Post by Aearenda on 2009-10-18
Did you try my suggestion about finding out whether you are really a member of the sudo group?

---

### Post by lemmyg on 2009-10-18
Hi, 
my sudo group was empty.  I changed and now it works.

I was used: 
sudo useradd -G sudo myuser


finally I used
sudo usermod -G sudo myuser

and works.

---

### Post by Aearenda on 2009-10-18
Thanks for confirming that. Others who come across this thread will have more complete information as a result. Good luck in avoiding the nasties!

---

### Post by juancarlospaco on 2009-10-18
***Kamikaze...***

---

### Post by blazk on 2009-10-25
Hi, I believe i've got the same problem in Karmic.

using 'visudo' I uncommented the line

  %sudo ALL=NOPASSWD: ALL

in /etc/sudoers and added myself to the sudo group
(usermod -a -G sudo username) but I'm still prompted for password.

This used to work...

---

### Post by lemmyg on 2009-10-26
Hi, 
look if you have added correctly you user in sudo group. 
in etc/group
this was the problem that I had.

---

### Post by ranch hand on 2009-10-26
As long as you are using the box connected to the internet, turning your box into a poor copy of the security hole called Windows is really stupid.

It really is not hard to put in a password, lengthen the sudo time out or run sudo su.  This is the type of laziness that makes malware developers drool.  I am sure they all thank you.

---

### Post by lemmyg on 2009-10-26
The access to  my personal data is what really worries me. For that malware does not need to be root. Also, default security mask 022 of files, all users can access it.

---

### Post by blazk on 2009-10-28
> **lemmyg said:**
> Hi, 
look if you have added correctly you user in sudo group. 
in etc/group
this was the problem that I had.

yup, my user is there. I dunno.. it looks like a bug for me

folks concerned about security got a good point, however that functionality was built into sudo by its developers and it seems to be broken in Karmic. Or if it was switched off for purpose then the instructions in comments in /etc/sudoers are broken. I've filled a bug report about it to launchpad (Bug #460761).

---

### Post by lemmyg on 2009-10-28
thanks.

---

### Post by mister_pink on 2009-10-28
> **anders_c_ said:**
> you could just allow root login, and always be logged in as root, it will ofcourse be a huge security risk. But the way you do it now isnt much safer.
Logging in as root and having a passwordless sudo are two very different things. 

If you log in as root all your applications will run with root priviledges. This means if something goes wrong then they could damage anything.

If you have a passwordless sudo, then whilst it is a huge security risk, an application would have to deliberately request root priviledges in order to get them. This means that accidentally damaging data is much less likely, but malicous attacks are still very much possible.

---

