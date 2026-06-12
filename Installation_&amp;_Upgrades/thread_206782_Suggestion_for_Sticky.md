---
title: "Suggestion for Sticky"
date: 2006-06-30
forum: Installation &amp; Upgrades
---

### Post by stychman on 2006-06-30
I've noticed a recurring theme in a few questions posted here.  Some people are installing the server version and then get stuck at a text login.  To help alleviate some of this problem from the beginning could the web developers for the Ubuntu site put something next to the server install download that this will not install a graphical desktop?  Or another suggestion is to put a sticky here on the installation forum about what the best procedure is if someone has downloaded and installed the server.

---

### Post by ubuntu_demon on 2006-06-30
Thnx for the suggestion

```

First change your sources.list to a clean one right here :
http://www.ubuntuforums.org/showpost.php?p=1090438&postcount=2

To use this sources.list replace your sources.list with this one using your favorite editor. Do the following command in the terminal (without the $):
$sudo pico /etc/apt/sources.list

Then do this command to take the new sources.list into effect do the following command in the terminal (without the $) :

$sudo apt-get update

install a kernel suitable for the desktop (or linux-686 or linux-k7) :
$sudo apt-get install linux-386

Make sure the entire base system is installed :
$ sudo apt-get install ubuntu-base

Install the graphical stuff :
$ sudo apt-get install xserver-xorg ubuntu-desktop

Do a reboot in order to boot from the newly installed kernel and everything should probably work now!

```

I just wrote it down and I want some people to test it first before I sticky it.

For example maybe some additional stuff is installed which needs removing. TESTERS wanted and appreciated !

---

### Post by aysiu on 2006-07-01
Those commands are redundant. If you do ```
sudo aptitude update
sudo aptitude install ubuntu-desktop
``` you should get *xserver-xorg* and *x-window-system-core*. You should also already have the correct kernel installed if you installed the server edition.

---

### Post by ubuntu_demon on 2006-07-01
[QUOTE=aysiu]Those commands are redundant. If you do ```
sudo aptitude update
sudo aptitude install ubuntu-desktop
``` you should get *xserver-xorg* and *x-window-system-core*. You should also already have the correct kernel installed if you installed the server edition.[/QUOTE]

The linux-server kernel will probably work in most instances. But the desktop kernels are optimized for drivers and desktop users.

I think linux-server is the kernel which gets installed if you install the server edition. Although I'm not sure. Does someone (running a clean server install) want to check this ?

You can check what is installed with :
$ dpkg -l | grep linux

You can check which kernel you are currently running with :
$ uname -a

ubuntu-desktop doesn't depend on xserver-xorg. So let's make sure it gets installed. It's possible that apt-get/aptitude figures it out somehow. (xfree86 is also in the repositories but most people should use xserver-xorg)

You are right about the x-window-system-core. Thanks for noticing it. A vaguely remember that in the past ubuntu-desktop didn't depend on x-window-system-core as well.

I suggest people to install ubuntu-base because I want to make sure it is installed. (sometimes people mess around to try to solve their issues and accidentily remove the ubuntu-base meta-package)

---

### Post by aysiu on 2006-07-01
I've done many a server install and then an installation of a _________-*desktop* package, and that's all I've ever needed to do--not extra need to install a kernel or xserver-xorg.

---

### Post by ubuntu_demon on 2006-07-01
[QUOTE=aysiu]I've done many a server install and then an installation of a _________-*desktop* package, and that's all I've ever needed to do--not extra need to install a kernel or xserver-xorg.[/QUOTE]
But did you check which kernel was running ? A server kernel also works (if you don't need some specific drivers) but it is not the best option.

---

### Post by aysiu on 2006-07-01
Hm. I never checked that, actually.

---

### Post by ubuntu_demon on 2006-07-01
[QUOTE=aysiu]Hm. I never checked that, actually.[/QUOTE]
Before Dapper there was no linux-server kernel. 

But since Dapper there's an alternate installer cd which installs the linux-386 kernel and the server cd which AFAIK installs linux-server.

---

### Post by aysiu on 2006-07-01
Well, believe it or not, I'm going to try it out.

If it isn't smart enough to install the desktop kernels, then we may have to advise people not only to install it, but to also remove the server kernel.

---

### Post by aysiu on 2006-07-01
Okay. It took me a while because my test computer's a bit slow, but I finally did a server install and then *aptitude* installed *ubuntu-desktop* on top of it.

As far as I can tell, it uses the desktop kernel. I'm not sure, though.

In /boot/grub/menu.lst it says: ```
Ubuntu, kernel 2.6.15-23-386
``` Is that the desktop kernel or the server kernel?

Also when I did a search in Synaptic for the phrase *linux-image*, only two results came up and both were installed: *linux-image-2.6.15-23-386* and *linux-image-386*

So did it work or not? Is there some separate desktop kernel I'll have to install?

---

### Post by ubuntu_demon on 2006-07-01
$uname -a

desktop :
Linux hostname2.6.15-25-686 #1 SMP PREEMPT Wed Jun 14 11:34:19 UTC 2006 i686 GNU/Linux

server :
Linux hostname 2.6.15-25-server #1 SMP Wed Jun 14 11:52:05 UTC 2006 i686 GNU/Linux

(it wouldn't hurt to keep the linux-server kernel around but it does use some diskspace)

---

### Post by aysiu on 2006-07-01
I got this: ```
Linux ubuntu 2.6.15-23-386 #1 PREEMPT Tue Jul 1 13:49:40 UTC 2006 i686 GNU/Linux
``` So I think the desktop one took over when I installed *ubuntu-desktop* over the server.

---

### Post by ubuntu_demon on 2006-07-01
[QUOTE=aysiu]I got this: ```
Linux ubuntu 2.6.15-23-386 #1 PREEMPT Tue Jul 1 13:49:40 UTC 2006 i686 GNU/Linux
``` So I think the desktop one took over when I installed *ubuntu-desktop* over the server.[/QUOTE]
That looks like a desktop kernel. But the ubuntu-desktop meta-package doesn't mention any kernel. 

Are you sure you installed from a server cd ? Or did you just use the alternate installer to install a bare system ?

(don't mistake the alternate installer cd for the server cd)

---

### Post by aysiu on 2006-07-01
Ah! That's what you're talking about!

Yes, I did a server install from the alternate CD. I did not use the server CD.

Wouldn't a server install from the alternate CD be the same as a regular install from the server CD, though?

---

### Post by ubuntu_demon on 2006-07-02
[QUOTE=aysiu]Ah! That's what you're talking about!

Yes, I did a server install from the alternate CD. I did not use the server CD.

Wouldn't a server install from the alternate CD be the same as a regular install from the server CD, though?[/QUOTE]
Before Dapper (breezy and before) you could type "server" from the installation cd in order to install a bare system. In Dapper you type something different from the alternate installer cd to install a bare system. I can't remember what it is. "base" or something ?

So when you type "base" or something from the alternate installer cd you get something different then when you install from the server cd (a server install).

A server install installs linux-server kernel instead of a desktop kernel. AFAIK the root account is enabled on default. Maybe it also installs some specific packages. But there won't be any ports opened by default or something. From a server install you can easily set up apache,mysql,php in this way :
$sudo lamp

(in order to see what packages are installed you can use $dpkg -l , or use debfoster if you know how that works)

If people say they have done a server install or installed a server then I think they mean that they downloaded the server cd and installed from it. But some might actually have installed a bare system from the alternative installation cd instead. My instructions work also for people who have used an alternate cd to install a bare system though.

---

### Post by aysiu on 2006-07-02
It's not called a base or bare install off the alternate CD. It's actually called a server install.

---

### Post by ubuntu_demon on 2006-07-02
[QUOTE=aysiu]It's not called a base or bare install off the alternate CD. It's actually called a server install.[/QUOTE]
Are you sure ? Did you try a regular Dapper cd or a flight cd ?

If it's true that's totally confusing for the users :?

---

### Post by aysiu on 2006-07-02
It's a regular one--the actual release.

---

### Post by ubuntu_demon on 2006-07-02
[QUOTE=aysiu]It's a regular one--the actual release.[/QUOTE]
That's totally confusing :(

---

### Post by aysiu on 2006-07-02
Yeah. What I *don't* know, though, is what you were wondering before--does the server install from the server CD use a different kernel from the server install from the alternate CD. Honestly, I didn't check the kernel *before* I installed *ubuntu-desktop* on top of it.

---

### Post by ubuntu_demon on 2006-07-02
[QUOTE=aysiu]Yeah. What I *don't* know, though, is what you were wondering before--does the server install from the server CD use a different kernel from the server install from the alternate CD. Honestly, I didn't check the kernel *before* I installed *ubuntu-desktop* on top of it.[/QUOTE]
AFAIK linux-server gets installed by the server install cd instead of a regular desktop kernel such as linux-386.

---

### Post by aysiu on 2006-07-02
Yeah, but I guess what we don't know at this point (since I did lousy testing) is whether or not the server install from the alternate install CD installed a server kernel that got changed to a desktop one... or installed a desktop kernel in the first place.

---

### Post by ubuntu_demon on 2006-07-02
[QUOTE=aysiu]Yeah, but I guess what we don't know at this point (since I did lousy testing) is whether or not the server install from the alternate install CD installed a server kernel that got changed to a desktop one... or installed a desktop kernel in the first place.[/QUOTE]
The server install from the alternate install installs just the desktop kernel. I'm sure of that because the ubuntu-desktop package is in no way depending on a server package nor is it recommending one. So installing ubuntu-desktop can't possibly change your kernel.

I just thought they had changed the name to something like bare or base instead of server.

---

### Post by aysiu on 2006-07-02
No, you're right--that'll confuse users.

---

