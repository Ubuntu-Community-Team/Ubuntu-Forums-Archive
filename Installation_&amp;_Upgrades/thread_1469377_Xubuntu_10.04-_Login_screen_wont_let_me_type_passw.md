---
title: "Xubuntu 10.04- Login screen wont let me type password"
date: 2010-05-02
forum: Installation &amp; Upgrades
---

### Post by Imatriceratops on 2010-05-02
Hey guys, I installed Xubuntu 10.04 on my Dell laptop earlier, and all went well until I tried to finally login. A dull black screen is presented (I don't know if that's normal; I expected a pleasant splash screen haha). As a windows user, I can only explain it as looking like a command prompt. The first line asks me for my login (which is my first name). I type it in, press enter, and then it asks me for my password. The problem is, no matter what I press, nothing happens after that. If I just press enter, then it tells me that my login is incorrect. Thanks in advance!

---

### Post by P4man on 2010-05-02
the dull black screen is a console, and you should have a nice gui login. you can enter your password there (nothing is shown on screen, by design, but just type it and hit enter) but that will give only a... console ("dos prompt")

I dont know enough about xubuntu to help troubleshoot after that, but after logging in perhaps try entering

```
startx
```

to get a gui or an error message that can help.  This is not normal though!

---

### Post by Imatriceratops on 2010-05-02
> **P4man said:**
> the dull black screen is a console, and you should have a nice gui login. you can enter your password there (nothing is shown on screen, by design, but just type it and hit enter) but that will give only a... console ("dos prompt")

I dont know enough about xubuntu to help troubleshoot after that, but after logging in perhaps try entering

```
startx
```

to get a gui or an error message that can help.  This is not normal though!

Thanks for the response! Let me try to give a more detailed picture. I power up my computer and it immediately comes up to a black screen with white font at the top that says "Ubuntu 10.04 LTS thecakeisalie tty1" (thecakeisalie is my username, but my user name for logging in is "regan") so below that, it says "thecakeisalie login:" that's where I type "regan". Below that it asks me for a password, but no matter what I type, not even the cursor moves. It just stands still. Despite this, I'll type in the password and press enter, but it says that it's incorrect. Thanks again!

---

### Post by P4man on 2010-05-02
are you sure you installed the right version, and not the ubuntu server?

---

### Post by aysiu on 2010-05-02
> **P4man said:**
> the dull black screen is a console, and you should have a nice gui login. you can enter your password there (nothing is shown on screen, by design, but just type it and hit enter) but that will give only a... console ("dos prompt") I'm so glad you said "by design" and not the untrue but often touted "for security reasons."

I'm not sure what happened here but, yes, simply typing the password and hitting Enter should work. [There is no visual feedback](http://www.psychocats.net/ubuntu/passwordinterminal)

Once you're done, type in (because you can't paste in a fullscreen terminal): ```
sudo apt-get update
sudo apt-get install xubuntu-desktop
sudo service gdm start
```

---

### Post by Chris Atkin on 2010-05-24
Did you ever resolve this one? I have the same problem with 10.04 running as a virtual machine. In the end I selected the on-screen keyboard option on the login screen (using the mouse) and re-started but this is not ideal.

---

### Post by P4man on 2010-05-24
VMware isnt (or wasnt?) compatible with 10.04. Workarounds include changing from apic to pic in the bios settings, or this:
[http://reformedmusings.wordpress.com/2010/04/24/keyboard-issues-with-ubuntu-lucid-10-04-and-vmware-workstation-7-0/](http://reformedmusings.wordpress.com/2010/04/24/keyboard-issues-with-ubuntu-lucid-10-04-and-vmware-workstation-7-0/)

---

