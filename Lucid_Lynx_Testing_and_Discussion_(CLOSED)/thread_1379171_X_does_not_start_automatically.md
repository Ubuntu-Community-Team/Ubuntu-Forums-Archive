---
title: "X does not start automatically"
date: 2010-01-12
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by dawynn on 2010-01-12
I just upgraded a Karmic / Helena (Mint) system to Lucid / Helena.  Main GUI is Gnome.  Now have the computer in a partially working state.  Not sure where to look to diagnose the problem.

Computer currently boots to cli.  On one of the boots, I checked for /var/log/Xorg.0.log -- only to find that it had not been created for that boot.  Meaning that X never even tried to start.  When I type startx at cli, X will start and it stays very stable. (Well, I only use my computer for a couple hours at a time, then completely shutdown.  So, we're not talking days of stability testing)

1) How do I get gdm / x to start automatically, instead of the manual start?

2) Some keyboard issues.  Certain keystrokes have been configured to produce different results.  I'm needing a basic US keyboard layout, but somehow the keyboard is set for some other layout.  Ideas on how to correct this are also appreciated.

Cheers!

---

### Post by kansasnoob on 2010-01-12
I had the same issue but I'd created the problem myself doing some testing in a chroot.

Long story short I somehow hosed some of the upstart configuration files and had to run:

```
sudo apt-get install --reinstall upstart
```

Of course the cause of my problem and the cause of yours may be totally different but I don't think it could do any harm to try that.

If you go to Preferences > Keyboard, do you have the USA option available under the Layouts tab? Or if you click on Add is the correct option there?

---

### Post by ranch hand on 2010-01-12
This is a Lucid-testing forum.  You may do better in "General Help" with a prefix of "other OS".

I ca ntell you that I have an updated 9.04>10.04 minimal install running gnome desktop environment and it works very well.

---

### Post by VMC on 2010-01-12
I saw this topic earlier and decided to wait for a reply.

Even though Helena (Mint) is based on karmic, there may be enough differences that it won't work properly.

 Maybe someone over at the Mint farm has accomplished what your asking.

---

### Post by kansasnoob on 2010-01-12
I assume the OP is talking about a dual-boot:

> I just upgraded a Karmic / Helena (Mint) system to Lucid / Helena.

Helena is based on Karmic, so I think (s)he upgraded the Karmic to Lucid and kept Helena separate.

Then again I could be all wet :)

---

### Post by ranch hand on 2010-01-12
Ah, once again proving that I really need to learn to read.

---

### Post by dawynn on 2010-01-13
It is a mint system -- keeping it as cutting-edge as available.  Mint is based on Ubuntu, but tries to be ready for all multimedia codecs out of the box.  Usually, the Mint part is ready within a month or two after Ubuntu releases.

So for now, the mint pieces have to be kept at the Helena level (on par with Karmic).  But the Lucid pieces have all been upgraded.  And it was the upgrade to Lucid that caused the problems.

I'll try the couple things that have been posted here.  If anyone else solves a similar problem, I'm up for suggestions.

Cheers!

---

### Post by ankspo71 on 2010-01-13
Hi,
I'm not using Mint, just plain old Ubuntu 10.04 ;)

When X fails to start, does it bring you to a tty (command line) login? 

If so, you might be able to login with your username and password,
Wait for the next prompt to come up,
Then type in sudo gdm
then enter your sudo password.
Then that should open up the GDM (login window) (if it doesn't fail)

Also, see if you can change your automatic login preferences to manual (or automatic) to see if it helps the problem.

I have only had a few bad start-ups so far... so I was unable to find/fix the problem yet.
good luck.

---

### Post by VMC on 2010-01-13
It probably has nothing to do with Mint/Ubuntu, but the fact that several people have reported either no X or X starts and then freezes after a while.

What specs do you have? Intel perhaps?

---

### Post by dawynn on 2010-01-13
Ding!  Intel.  Yes, I get a cli where I can log in.  I'll try typing gdm to see if that helps.  I was personally stumped that there was no Xorg log for the current session -- as if Xorg never even tried to start.   Normally that's where I look for GUI-related issues.  What logs should I look in for issues that prevent Xorg / gdm from even trying to start?

(BTW, reinstalling upstart did not cure the issue)

---

### Post by ankspo71 on 2010-01-13
sudo nano /var/log/Xorg.0.log   ?

(to navigate in nano... ^+key = Ctrl+key)

There are several other logs located in /var/log/ too.

ls /var/log/

---

### Post by USB_NL on 2010-01-13
I had that problem with a usb livecd presistent boot
after i tried a few steps into the install (eeebuntu 3 JJ 9.04) and then stoped and booted presistently again i had to use startx

i now have it installed fully ;) on my 8g sdcard

---

### Post by VMC on 2010-01-13
> **dawynn said:**
> Ding!  Intel.  Yes, I get a cli where I can log in.  I'll try typing gdm to see if that helps.  I was personally stumped that there was no Xorg log for the current session -- as if Xorg never even tried to start.   Normally that's where I look for GUI-related issues.  What logs should I look in for issues that prevent Xorg / gdm from even trying to start?

(BTW, reinstalling upstart did not cure the issue)

I had this problem with kubuntu and is was hal related. A config file in "/etc/init/kdm.conf". Gnome uses gdm.conf. Somewhere after
"start on ". I looked at my gdm.conf and hal is nowhere in sight. This is jus a stab in the dark, but it fix my exact same issue in kubuntu.

Also check in your home folder for "xsession-errors" and new. Look for any telltale signs.

---

### Post by seeker5528 on 2010-01-13
I think KDM is fixed now, at least it works for me.

Later, Seeker

---

