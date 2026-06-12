---
title: "Can't Log On as Root in Lucid Alpha 2"
date: 2010-01-15
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by LaneLester on 2010-01-15
I know the above Subject will get the purists fuming, but this is important to me. Years ago I decided that Linux made sense as my only OS only if I could run it like a responsible adult: as root.

From one distro to the next, there's always been some way to log on as root. With Karmic it became really easy: just give root a password with the User-Groups GUI or the passwd command.

Unfortunately neither of these techniques work in [Lucid Alpha 2]("http://cdimage.ubuntu.com/releases/lucid/alpha-2/"). If you choose "root" as an alternative user at logon, the process just starts over again without allowing you to enter the root password.

I hope this will be fixed in Alpha 3 or whatever.

Lane

---

### Post by sisco311 on 2010-01-15
> **LaneLester said:**
> 
I hope this will be fixed in Alpha 3 or whatever.

Lane

Fix what?

You are circumventing Ubuntu's security model.There is nothing to be fixed. As a  responsible adult you will probably find a way to log in as root. 

Good luck!

---

### Post by darkod on 2010-01-15
> **sisco311 said:**
> Fix what?

You are circumventing Ubuntu's security model.There is nothing to be fixed. As a  responsible adult you will probably find a way to log in as root. 

Good luck!

Plus, it's only Alpha 2. I'm not sure how the development process stages go, but it doesn't mean it needs "fixing" at all. In the final release you might be able to log in as root as in Karmic. It all depends whether it's planned to exist in the final release, and if yes, does that mean it needs to exist right now in Alpha 2.

---

### Post by phillw on 2010-01-15
Hi,
I disabled root on 9.10 that long ago, I can't even remember how to do it !! So, you don't need root - it is a danger and a security weakness. At 45 years young - I count myself as an adult !!

Regards,

Phill.
P.S. I think it was in the security forum stickies somewhere.

---

### Post by VMC on 2010-01-15
Why do you find the need to always be logged in as root? That's definitely a security breach. Some root-kit will come along and your left wide open, or with your pants down as they say.

Most day to day operations don't require root access. Even so it should be short lived.

I would still like to know your reasoning as to be root. Is it laziness or something else?

---

### Post by Ibidem on 2010-01-15
Ubuntu was designed to make doing that hard.
If you can setup the root account from Ubiquity, that's most likely a bug.
You should be able to use sudo, and there are ways to disable password checking in that (I don't use them).
(Hint: man sudoers)
Or there's the "expert" install.
If you have a reason to use the root account, you should be able to figure those out.
But the methods you referred to are *serious* security breaches, as they allow any user to set the root password and gain full control of the system.  This is unacceptable in any production environment.

I would suggest using a different distro, such as Puppy/Dpup (autologin as root standard).
Ubuntu is supposed to have security.

Ibidem

---

### Post by ayates on 2010-01-15
It is not only root but any "other' user.

[https://bugs.launchpad.net/ubuntu/+source/gdm/+bug/490349](https://bugs.launchpad.net/ubuntu/+source/gdm/+bug/490349)

---

### Post by zika on 2010-01-16
I had root enabled in KK, even earlier. Now, I've changed root's pass to blank in System>Admin>Users>root>pass. But, if I got to tty I still can log as root with old password. I do not have an option to login as root in GDM login window. Is that how it is supposed to be? The only way, I can think of, to dissable root login in tty is passwd -l, and, yes, that works. Are there any side-effects of disabling root that way?

---

### Post by k64 on 2010-01-16
> **LaneLester said:**
> I know the above Subject will get the purists fuming, but this is important to me. Years ago I decided that Linux made sense as my only OS only if I could run it like a responsible adult: as root.

From one distro to the next, there's always been some way to log on as root. With Karmic it became really easy: just give root a password with the User-Groups GUI or the passwd command.

Unfortunately neither of these techniques work in [Lucid Alpha 2]("http://cdimage.ubuntu.com/releases/lucid/alpha-2/"). If you choose "root" as an alternative user at logon, the process just starts over again without allowing you to enter the root password.

I hope this will be fixed in Alpha 3 or whatever.

Lane

sudo init 3 && sudo startx

---

### Post by LaneLester on 2010-01-19
Interesting comments, guys. Today I switched over from Karmic to Lucid and updated everything. This time I was able to access the Advanced user settings, and I gave user "root" the privileges I thought he should have.

Now I can log on as root and enjoy the system.

This computer is in my office at home, and I'm the only one who uses it. I give my password when I fire it up, and I don't want the system asking for it again.

Lane

---

### Post by VMC on 2010-01-19
> **LaneLester said:**
> ...
This computer is in my office at home, and I'm the only one who uses it. I give my password when I fire it up, and I don't want the system asking for it again.

LaneYour not the only guy on the internet. And when you use the internet your running root !

---

### Post by garba on 2010-01-19
> **LaneLester said:**
> Years ago I decided that Linux made sense as my only OS only if I could run it like a responsible adult: as root.

:-k 8-[ :?:

---

### Post by sisco311 on 2010-01-19
> **LaneLester said:**
> Interesting comments, guys. Today I switched over from Karmic to Lucid and updated everything. This time I was able to access the Advanced user settings, and I gave user "root" the privileges I thought he should have.

Now I can log on as root and enjoy the system.

This computer is in my office at home, and I'm the only one who uses it. I give my password when I fire it up, and I don't want the system asking for it again.

Lane

You can disable the password authentication by editing the sudoers file and the /usr/share/polkit-1/actions/* files.

If you do so, at least, you don't have to run your x server, web browser...  as root.

But, in my experience, if a users is prompted for the admin password too often he/she is doing something wrong. ;)

---

### Post by ankspo71 on 2010-01-19
Once I learned the commands to launch applications from the terminal, I no longer had a need to be able to log into the root account. Most of the hints I needed were right there in the start menu editor. :D I already got used to entering my password repeatedly too, which seemed like a real chore at first. I can see why someone would want full user privileges though (as I once did) but I'm more comfortable with the added protection now. Just remember that the whole system is always exposed to whatever could happen when enabling root login... not just one program, directory, or file like when you type sudo in the terminal. It's good to be a responsible user in this situation.

---

### Post by k64 on 2010-01-19
Try running the "sudo -s" command. It will, at least, get you root access in a terminal. You can also kill the xserver (killall xorg) and re-run it as root (sudo startx).

---

