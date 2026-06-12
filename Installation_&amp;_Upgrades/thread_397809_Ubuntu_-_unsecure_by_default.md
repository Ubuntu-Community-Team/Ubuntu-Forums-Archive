---
title: "Ubuntu - unsecure by default"
date: 2007-03-31
forum: Installation &amp; Upgrades
---

### Post by Karolaq on 2007-03-31
Hello,
I think you talked about it but I couldn't find it.
I have some experiences with GNU/Linux and this problem doesn't touch me, because i know how to solve it.
I've installed Ubuntu 7.04. I wanted to install FGLRX driver, but I had some problems and I had to run Ubuntu in recovery mode. I chose from grub menu list this option. after minute I was logged on root 8-|
the question is: WHY?
I understand that Ubuntu doesn't set password for root user but in this case it's stupid because it makes this operation System is insecure because everyone can run Ubuntu in recovery mode... I think it should be changed. IMHO, Ubuntu should set grub password as default. I don't have any better idea.

---

### Post by louieb on 2007-03-31
If someone can get there hands on a computer, what is stopping them from  removing the hard drive or the whole computer and messing with it at there leisure? Put in a GRUB password if you want. If I can get my hands on the PC it not going to keep me from getting anything it has off of it.  There are things that the paranoid can do to make it harder.  

Don't know of any Linux distro that makes the Boot Loader password mandatory.  If a person or company needs physical security the they keep there  PC's under lock and key. and only grant access to people they trust.   

Security in Linux has everything  to do with accessing the computer over a network. Making sure that Tom, Dick and Harry can only access the part of the computer they have permission to.

---

### Post by PilotJLR on 2007-03-31
This isn't a security hole... this is single user mode. Every linux system has the ability to do this! With out, you would have no way to recover from a lost root password.

Keep in mind GRUB options are not available remotely, so this isn't something you hack into. It is assumed that people with PHYSICAL access to the machine get this privilege (after all, they could just pop the case and pull the hard drive, if they wanted to).

---

### Post by Karolaq on 2007-03-31
so, why root is disabled by default? what does it change? users can't run gnome under root because GDM doesn't let them (there is option in GDM configuration which is enabled). if root had a password it wouldn't change.
ok, maybe we can't protect our computer in 100%... does it mean we should don't care about our security?

---

### Post by Burning Bronx on 2007-03-31
Ubuntu is as secure as any other distro. And if you are so desperate to have a root password just use sudo passwd and set one. Not that you´d need it. 
Oh, and remember - the only way to make sure your PC is safe is to remove all network h/w and lock it in a vault.

---

### Post by FuturePilot on 2007-03-31
Any computer can be compromised if someone has physical access to it regardless of the OS. If someone can boot a live CD on your computer it doesn't matter how many passwords you have. Just my $.02

---

### Post by 23meg on 2007-03-31
> **Karolaq said:**
> so, why root is disabled by default?
 what does it change? 

Mainly because it's dangerous, and you can easily shoot yourself in the foot by logging in as root, especially if you make a habit of it. 

> **Karolaq said:**
> users can't run gnome under root because GDM doesn't let them (there is option in GDM configuration which is enabled). 

You can enable the root account with ```
 sudo passwd root
``` and go to System / Administration / Login Window / Security  and check the "Allow local system administrator login" box to enable logging in as root in GDM. There's no known use case requiring you to do so, however, and it's both unsupported and recommended against.


> **Karolaq said:**
> if root had a password it wouldn't change.

If root were enabled by default, to hack the root account, all that had to be done would be to guess the password, since the username is fixed. 


> **Karolaq said:**
> ok, maybe we can't protect our computer in 100%... does it mean we should don't care about our security?

Who's saying we shouldn't care about security?

Take a look at this: [http://www.psychocats.net/ubuntu/security](http://www.psychocats.net/ubuntu/security)

And this: [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by Karolaq on 2007-03-31
no, no.. you don't understand me.

root is disabled because running all programs by root isn't secure etc...
but in fact, it's not necessary bacause GDM doesn't let to run GNOME session by root.
so, it's not argument that root shouldn't have password - it's not necessary.
but there is a good argument why should have - RECOVERY MODE!
don't give me advice how to set password bacause I know how.
I'm thiking about normal users. for example:
there is a internet cafe where computers work under linux.
stupid client which want to break something will do it easily.
maybe you don't know people like that, but I know.

---

### Post by PilotJLR on 2007-03-31
Please re-consider the posts above; it seems you're not understanding what we're trying to communicate.

Physical access grants you more privileges on the machine - period. In a public setting like you mention, then it's appropriate to use BIOS and GRUB passwords, just like you said.  You could also go one step further and use thin clients, so that people couldn't even steal hard drives or other worthwhile components.

But many computers are NOT public terminals... and these steps aren't necessary, so there's not a one size fits all solution. 90% of the time people want GRUB wide open.

---

### Post by 23meg on 2007-03-31
> **Karolaq]no, no.. you don't understand me.[/QUOTE]

It's the other way around said:**
> root is disabled because running all programs by root isn't secure etc...
but in fact, it's not necessary bacause GDM doesn't let to run GNOME session by root.
so, it's not argument that root shouldn't have password - it's not necessary.

Root isn't disabled because running programs as root isn't secure. You still typically have to run things as root; you can't make proper use of your computer without running administrative apps, for example. It's just that instead of having the user log in as root, Ubuntu uses sudo (and so do many other operating systems, including OSX) to perform administrative tasks and run applications as root. There are multiple advantages of the sudo model over the root model, which have been discussed ad nauseam; you can find them by doing a forum or web search. 

Disabling GDM root login doesn't completely prohibit you from running graphical applications as root either, let alone logging in as root; if the root account is enabled, you can still use *su* to become root, and everything you launch will run as root. You can also log in as root and start X without GDM.

[QUOTE=Karolaq]but there is a good argument why should have - RECOVERY MODE!
don't give me advice how to set password bacause I know how.
I'm thiking about normal users. for example:
there is a internet cafe where computers work under linux.
stupid client which want to break something will do it easily.
maybe you don't know people like that, but I know.[/QUOTE]

Recovery mode is for recovering things. What if the user forgot their root password? I'll tell you what: they'll have to use a live CD, and what would be the purpose of recovery mode if it couldn't be logged on to? The user could have used a live CD to recover things regardless of whether there's a recovery mode or not, since they have unrestricted physical access. Besides, there's no way to disable the root account and have a password for recovery mode, since it's basically single user mode, in which you can only be root.

You shouldn't expect an operating system that's used in many different scenarios to cater for the security needs of all its users. In any case, the system administrator is responsible from security, not the operating system; the operating system only provides the tools that the administrator is expected to use and customize according to the scenario. In your internet cafe scenario, the system administrator is the cafe owner, who should set a GRUB or BIOS password to keep clients from abusing the recovery mode.

In a personal desktop install meant for a single user, that user is also the system administrator, and again, should set things up according to their own security needs.

---

