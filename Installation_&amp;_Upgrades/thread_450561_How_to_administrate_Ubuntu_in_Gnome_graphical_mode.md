---
title: "How to administrate Ubuntu in Gnome graphical mode [Resolved - Cause Unknown]"
date: 2007-05-21
forum: Installation &amp; Upgrades
---

### Post by aldav on 2007-05-21
Hello, I recently installed Ubuntu 7.04 Feisty, initially, it installed only Gnome graphical interface. I then tried to update my system by installing new software from the repository and then I realized I had no visual tool available to run. I mean, there's no link to synaptic or Add/Remove Software in the the Applications menu so I had to do it all by commands in the terminal, something I can do, but I don't like. I also can't find a way to manage my user accounts. I mean, I'm kind of new in the Linux world, but not THAT new, I installed Kubuntu in another machine and everything went well, I didn't had these problems. Maybe it's because I'm new to Gnome, but I can't find a way to manage my system in graphical mode. If anyone could give me some clues I'll appreciate. Thanks in advance

---

### Post by aysiu on 2007-05-21
You're saying when you went to System > Administration that Synaptic Package Manager was not one of the choices? Can you post a screenshot of your System > Administration menu?

Managing user accounts should also be in the System > Administration menu as Users & Groups.

---

### Post by aldav on 2007-05-21
You're saying when you went to System > Administration that Synaptic Package Manager was not one of the choices? Can you post a screenshot of your System > Administration menu?

Managing user accounts should also be in the System > Administration menu as Users & Groups.

That's exactly what I mean, there's no Synaptic Package Manager nor Users & Groups in my System > Administration menu

I attached a screenshot of my Administration menu

---

### Post by aysiu on 2007-05-21
Whoa! That's weird. This is from a fresh installation?

Well, first of all, do you even have Synaptic installed? Can you paste this command in the terminal and post back any error messages you get? ```
gksudo synaptic
```

---

### Post by aldav on 2007-05-21
Yes I have synaptic installed, but when I tried:
gksudo synaptic
I can't enter the root password, I mean, I can type it, but it says it's incorrect, when it's not. The password I typed was correct because I checked it in the terminal by entering "su -". I then launched synaptic as a regular user and it started, although it said I couldn't do some things because I wasn't root user.

---

### Post by aysiu on 2007-05-21
It's not asking for your root password (why do you have one?). It's asking for your user password.

---

### Post by eentonig on 2007-05-21
[Sorry *rant*)]

And again, someone who managed to screw up by enabling root access and not knowing what he's doing. [*rant off*]

Try reinstalling the missing stuff by typing

> sudo apt-get ubuntu-desktop

Then check if you're Administrattion menu is still uncomplete.

---

### Post by aldav on 2007-05-21
I entered my user password and it gave me the following error message:

Failed to run synaptic as user root.
The underlying authorization mechanism (sudo) does not allow you to run this program. Contact the system administrator.

I have a root password because when I installed and tried to type "sudo passwd" it gave me an error, so I went into Internet and someone told me a method to restore the root password. I though every Linux installation had to have a root password, this is not the case in Ubuntu?

---

### Post by aysiu on 2007-05-21
Sounds as if you're not an administrator for the computer. Can you log in as root and give yourself sudo/gksudo privileges? ```
su
adduser aldav admin
``` and then try running ```
gksudo synaptic
``` again?

---

### Post by aldav on 2007-05-21
"adduser aldav admin" worked just fine, I can interact with Synaptic now. Still I don't have access to it through the Administratior menu.

---

### Post by aldav on 2007-05-21
> **eentonig said:**
> [Sorry *rant*)]

And again, someone who managed to screw up by enabling root access and not knowing what he's doing. [*rant off*]

Try reinstalling the missing stuff by typing



Then check if you're Administrattion menu is still uncomplete.

I reinstalled ubuntu-desktop but the problem persisted, I don't have access to Synaptic nor Add & Remove Users from the Administration menu.

---

### Post by aysiu on 2007-05-21
That I'm stumped on--why it doesn't show up in the menus.

But you can edit the menu by right-clicking *Applications* and selecting *Edit Menus*. That should allow you to at least manually add Synaptic (*gksudo synaptic*), Users & Groups (*gksudo users-admin*), and Add/Remove (*gksudo gnome-app-install*).

---

### Post by aldav on 2007-05-21
That worked just fine. Still, when I opened the Edit Menu window, all was there, I mean, I contained Synaptic, Add & Remove Users, and a lot of other stuffs that don't really show up in the menu.

---

### Post by aldav on 2007-05-21
I can fix the menu, although it's gonna cost me some time. I can add new items with the exact information of the items that doesn't really appear in the menu.

THANK A LOT FOR THE HELP

---

### Post by quaystone on 2008-02-12
I have the same problem.  I can only see about 5 menu choices under Administration, although all of them were there last week.  Nothing has changed for the user's permissions in the mean time.

I tried the right-click on applications and got all of the choices; tried to add "screen and graphics" which is what I really need the most because my screen resizes on it's own at every login. 

It did NOT appear in the menu after that.

thanks in advance

Sharon

---

