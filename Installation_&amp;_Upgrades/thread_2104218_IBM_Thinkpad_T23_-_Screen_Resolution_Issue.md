---
title: "IBM Thinkpad T23 - Screen Resolution Issue"
date: 2013-01-12
forum: Installation &amp; Upgrades
---

### Post by Stephan H on 2013-01-12
Hello Forum,

I've just installed the latest Lubuntu on an IBM T23.
But I can't read the screen at all. It's a mess of all colours and the curser looks like a little wiper but it's not clearing the screen.

So cannot open a console either.

I assume it's a screen resolution setting problem.
How can one at least enter the terminal before the GUI starts up?
Maybe there's a solution in it...


Stephan

---

### Post by sudodus on 2013-01-12
For a temporary change, either edit the command behind the menu item (line) in the grub menu, or edit

/boot/grub/grub.cfg

changing the boot options of the following line:

Change the line(s) normally containing [FONT="Courier New"][SIZE="3"]quiet splash[/SIZE][/FONT] to contain [FONT="Courier New"][SIZE="3"][COLOR="red"]text[/COLOR][/SIZE][/FONT] (at the end of the line)

Read more about grub here:

[[COLOR="Red"]https://help.ubuntu.com/community/Grub2[/COLOR]]("https://help.ubuntu.com/community/Grub2")

You can also add some other boot option, read about boot options here:

[[COLOR="red"]https://help.ubuntu.com/community/BootOptions[/COLOR]]("https://help.ubuntu.com/community/BootOptions")

Boot options, that you want to use permanently should be entered into the file [FONT="Courier New"][SIZE="3"]/etc/default/grub[/SIZE][/FONT], and after that you should run ```
sudo update-grub
```

*Edit*: for a quick fix, try if it works with the hotkey combination

***ctrl + alt + F1***
(or ... F2, ... F6) to give you a text screen.

***ctrl + alt + F7***
should go back to the graphics screen.

---

### Post by Stephan H on 2013-01-12
Hmm, tried the boot options.

Is there a way to get these boot options without starting an installation?
As it went now:

- boot from live CD, then see boot options;
- F6, ESC
- VGA set to 788 so changed to 874 (250 colours, 1024x640)
- added 'text' and 'splash' to the end of the line before '--'
- press enter.

It then starts the installation. Not sure if one can chose 'boot from 1st HDD' before.

Acc to [http://www.thinkwiki.org/wiki/Category:T23](http://www.thinkwiki.org/wiki/Category:T23) the resolution should be 1024x768.

Interestingly during installation the screen is clear and correct.
Still wondering where the fault actually comes from.

Stephan

---

### Post by offgridguy on 2013-01-12
Not sure if it's related but there are screen display issues of the thinkpads, by lenovo/IBM
Some info on that in this thread.

[http://ubuntuforums.org/showthread.php?t=2097169](http://ubuntuforums.org/showthread.php?t=2097169)

---

### Post by Stephan H on 2013-01-12
Not really.

But here's a screenshot of what it shows (see attachment).

Strangely it worked with Kubuntu 12.04LTS but it was a bit slow so I thought a lightweight OS was handy.

Stephan

---

### Post by sudodus on 2013-01-12
> **Stephan H said:**
> Hmm, tried the boot options.

Is there a way to get these boot options without starting an installation?
Stephan
Yes, what I described in my previous post is exactly what you ask for: Add the boot options where I suggested :-)

[FONT="Courier New"][SIZE="3"]text[/SIZE][/FONT] is one boot option, [FONT="Courier New"][SIZE="3"]nomodeset[/SIZE][/FONT] is another one ...

---

### Post by sudodus on 2013-01-12
> **Stephan H said:**
> Not really.

But here's a screenshot of what it shows (see attachment).

Strangely it worked with Kubuntu 12.04LTS but it was a bit slow so I thought a lightweight OS was handy.

Stephan
I think that the drivers for graphics are the same for the different flavours of Ubuntu, so when Kubuntu 12.04 LTS works, the other flavours should work too.

I suggest that you try with Lubuntu 12.04 instead of the latest one. If you still have problems, try Xubuntu 12.04 LTS (Yes, Xubuntu 12.04 has 3 years long time support, while Lubuntu 12.04 has 'only' 18 months standard length support).
If you still have problems, install Kubuntu 12.04 LTS again, make sure it works, and then install Lubuntu-desktop or simply LXDE,

```
sudo apt-get install lubuntu-desktop
``` or
```
sudo apt-get install lxde
```
You can switch desktop environment at the login screen

---

### Post by Stephan H on 2013-01-19
> **sudodus said:**
> I think that the drivers for graphics are the same for the different flavours of Ubuntu, so when Kubuntu 12.04 LTS works, the other flavours should work too.

I suggest that you try with Lubuntu 12.04 instead of the latest one. If you still have problems, try Xubuntu 12.04 LTS (Yes, Xubuntu 12.04 has 3 years long time support, while Lubuntu 12.04 has 'only' 18 months standard length support).
If you still have problems, install Kubuntu 12.04 LTS again, make sure it works, and then install Lubuntu-desktop or simply LXDE,

```
sudo apt-get install lubuntu-desktop
``` or
```
sudo apt-get install lxde
```
You can switch desktop environment at the login screen

Well thanks a lot! The lubuntu-desktop worked and the machine is up and running. Guess I can mark this issue as "solved".
Is there an overview somewhere where one can see the desktop packages that are available (from the terminal and currently set sources)?

Next and last thing is (as this machine goes to charity): How am I removing the KDE Plasma, Gnome/Openbox, KDE/Openbox and Openbox options to that it boots straight into the Lubuntu desktop (or just with the netbook option)? I did ```
sudo apt-get remove kubuntu-desktop
``` but it actually didn't change anything. 
It turned out that all the other options don't work- as it looks like because of not enough memory. But that's just how the machine is like.
Need to make it foolproof now though :)

Stephan

---

### Post by sudodus on 2013-01-19
I think you will find this link valuable

[[COLOR="Red"]http://www.psychocats.net/ubuntu/index[/COLOR]]("http://www.psychocats.net/ubuntu/index")

Look at the left column, 'Playing around'

---

