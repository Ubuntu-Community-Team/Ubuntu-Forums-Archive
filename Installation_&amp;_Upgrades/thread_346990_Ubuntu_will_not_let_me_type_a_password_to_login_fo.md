---
title: "Ubuntu will not let me type a password to login for the first time"
date: 2007-01-26
forum: Installation &amp; Upgrades
---

### Post by doublementh on 2007-01-26
I bought the Edgy Eft 6.10 DVD, and I installed it through OEM Mode. So, when I login, I can type a user name that it gave me(sudo, or oem user, or something), but when I type anything under the password, it does nothing. Please help!

---

### Post by taurus on 2007-01-26
Your login name is oem and use the same password that you created during the installing process.  Then, open a terminal and run this command to actual create a regular account for you to use.

Applications -> Accessories -> Termina
```
sudo oem-config-prepare
```

---

### Post by doublementh on 2007-01-26
Thanks, but I mean when I have to enter a password, I can type anything on my keyboard and nothing shows up. I'll then hit enter, and it tells me the login is incorrect. Also ,it crashes frequently telling me my Xserver couldn't be found ,which it tells me, is the graphical display. I have an ATI Radeon X600 videocard.

---

### Post by taurus on 2007-01-26
When you boot up, you see a gdm GUI login screen, right?  And when you installed Edgy on your machine using the alternate method, why didn't you pick the first option to install it instead of using the second option--oem?

---

### Post by doublementh on 2007-01-26
No... I tried the first option, and that didn't work. And no, there is no GUI. It's all text. It says that the Xserver failed to boot, and it said that that was my graphical interface. I don't know what a gdm is. I came from Windows, and I'm a complete Linux newbie.

---

### Post by taurus on 2007-01-26
After login, run

```
sudo dpkg-reconfigure xserver-xorg
```
And if you are not sure about an answer, just use the default.  Use **vesa** as the driver for your graphic card.

And when it's done, see if X works with

```
startx
```

---

### Post by doublementh on 2007-01-26
The problem is that I can't login, and there is no GUI. And it erased My WinXP.

---

### Post by linbetwin on 2007-01-26
If it's "all text" that means it is a console and you can's see the password you are typing, no asterisks or anything. Just make sure you type it correctly, exactly how you typed it during installation. Make sure Caps Lock is not on.

---

### Post by doublementh on 2007-01-26
No! When I type it, it's blank! No asteriks, no characters of any kind!

I hate to say this, but I'm having some serious second thoughts.

---

### Post by kerry_s on 2007-01-26
You can not see the password as you type, it's a feature to keep others from seeing your password, just type it and hit enter.

---

### Post by doublementh on 2007-01-26
D'oh. It worked. I'll run all of the commands and stuff to help get the graphical interface back to what it should be.

---

### Post by doublementh on 2007-01-26
It screws up in the middle of the process.

I don't want to be nasty, but I thought this was linux for human beings, not robots.

---

### Post by kerry_s on 2007-01-26
Last time i checked i was still considered human, although my X would call me something else. Are you calling us robots? If so, "you will be assimilated" i am buntu. Muhaha!

Seriously, we can't help that your computer was built to run windows, for at least 75% of people, they just pop the cd in and boot up to a brand new desktop.
Then again you might be trying to use some low spec piece of crap that can't run a decent OS in the first place. So if you really want to try, provide us with information we can use to help you, most importantly let us know what your using, what kinda specs are you working with.

---

