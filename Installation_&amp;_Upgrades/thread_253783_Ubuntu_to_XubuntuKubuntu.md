---
title: "Ubuntu to Xubuntu/Kubuntu?"
date: 2006-09-08
forum: Installation &amp; Upgrades
---

### Post by forcesofhabit on 2006-09-08
How can I make these changes? I read somewhere in the Xubuntu documentation you could switch Xubuntu to look like Ubuntu and vice versa, but couldn't find instructions on how to do so.

Could someone help me out?

Thanks!

---

### Post by zxee on 2006-09-08
> **forcesofhabit said:**
> How can I make these changes? I read somewhere in the Xubuntu documentation you could switch Xubuntu to look like Ubuntu and vice versa, but couldn't find instructions on how to do so.

Could someone help me out?

Thanks!

I think that you're asking about desktop environments or DE's 
Ubuntu comes with gnome kbuntu has KDE and xubuntu uses xfce.
You can use apt-get to install those on your system if you want them.
Maybe you want to take a look at those desktops and even use them before you decide to download them/change your system. That's another great thing about live cds you can check out the differences.
If you decide you do want to have a different desktop environment then take a look at the install help here: [https://help.ubuntu.com/community/SoftwareManagement](https://help.ubuntu.com/community/SoftwareManagement)

If however your just asking about changing the looks and not the actual DE then you can get themes from places like [http://www.gnome-look.org/](http://www.gnome-look.org/)
And have almost any look you can imagine.

---

### Post by aysiu on 2006-09-08
Since Xubuntu and Ubuntu both use GTK themes, it's not that difficult to make XFCE *look* like Gnome--just switch the theme.

Or were you talking about installing a different desktop environment altogether?

---

### Post by forcesofhabit on 2006-09-08
I was looking to change DE's all together. I don't mind Ubuntu's, but despite my machine's specs, it's not as fast as I'd like it to be.

Any downsides to switching over to Xubuntu?
...and how would I make the switch without having to reinstall everything and start from scratch?

---

### Post by jISh on 2006-09-08
If you want Xubuntu without reinstalling anything all you have to do is open a terminal and write:
sudo apt-get install xubuntu-desktop
Then you can log out. In the Session part of the login screen choose XFCE.
You can always switch back to GNOME at login screen.

Same thing can be done with KDE. And other window managers.

---

### Post by aysiu on 2006-09-08
jISh is mostly right. You would, of course, do ```
sudo aptitude update
sudo aptitude install xubuntu-desktop
``` because *apt-get* will leave you with no easy way to remove Xubuntu later, should you wish to do so.

---

### Post by jISh on 2006-09-08
Shrug. I never converted to apitude, don't know why.
Maybe I should..:P

---

### Post by aysiu on 2006-09-08
You don't have to convert to *aptitude*, but *aptitude* should definitely be used for installing desktop environments.

```
sudo aptitude update && sudo aptitude install xubuntu-desktop
sudo aptitude remove xubuntu-desktop
``` installs Xubuntu and then removes it.

```
sudo apt-get update && sudo apt-get install xubuntu-desktop
sudo apt-get remove xubuntu-desktop
``` Installs Xubuntu and that's it. It doesn't remove anything except the pointer to all the Xubuntu packages (not the packages themselves).

If you're going to answer all the "I installed Xubuntu with *apt-get*. How do I remove it now?" threads, then you're welcome to keep advising people to use *apt-get*. You don't have to use *aptitude* on your own computer to advise other people to use it, but it is a good idea to recommend it in a situation like this.

---

### Post by jISh on 2006-09-08
Heh, yeah, typo. Got it :P
For fun I just used *aptitude* to install kubuntu-desktop.
Haven't played with KDE in a while.

---

### Post by max.diems on 2006-09-08
To avoid changing ther session on each login, when it says "You are logging in to Xfce session but your default session is GNOME" or whatever it is, choose "Make default". You can still use any other session by switching to it the same way.

---

### Post by aysiu on 2006-09-09
> **max.diems said:**
> To avoid changing ther session on each login, when it says "You are logging in to Xfce session but you default session is GNOME" or whatever it is, choose "Make default". You can still use any other session by switching to it the same way.
Or use KDM instead of GDM. KDM makes your default whatever you last logged into.

---

### Post by forcesofhabit on 2006-09-09
Thanks for the help! I love that it's so easy to switch between DEs. I'm sold on Ubuntu.

---

### Post by Mimsy on 2006-09-09
I installed the Xubuntu desktop environment, and I definitely prefer it to the Gnome one. It is faster on my old laptop, and it looks a lot prettier. Plus, the hamster in the wheel is funny.

Is there any way I can uninstall the gnome environment, since I don't plan to use it again?

> sudo aptitude remove ubuntu-desktop

seems logical, but I'm too ignorant about the commands in general to be comfortabe experimenting. Can I just use that remove command,or will that break stuff?

Thanks,
Mimsy

---

### Post by aysiu on 2006-09-09
Now, that's a little more complicated. Since you didn't install Ubuntu with *aptitude*, you can't just remove it with *aptitude*.

There's a workaround, but it's not perfect (I've heard that if you're running a server, it'll remove LAMP, PHP, and a bunch of other stuff):
[http://www.psychocats.net/ubuntu/purexfce](http://www.psychocats.net/ubuntu/purexfce)

Are you using a 4 GB hard drive? Honestly, there's no reason to remove Gnome. It doesn't take up that much space, and it isn't using system resources if you're using XFCE.

---

### Post by Mimsy on 2006-09-09
In that case I won't bother, since the reason I wanted it out was to conserve resources. But if it's not going to use up system resources I'll just keep logging in to the Xubuntu desktop by default, and not worry about it.

Thanks! :-)

/Mimsy

---

