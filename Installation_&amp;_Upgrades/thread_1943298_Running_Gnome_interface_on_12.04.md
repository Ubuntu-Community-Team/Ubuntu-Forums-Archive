---
title: "Running Gnome interface on 12.04"
date: 2012-03-19
forum: Installation &amp; Upgrades
---

### Post by wpshooter on 2012-03-19
How can I go about running/trying the Gnome interface on 12.04 LIVE CD ?

I found a reference to using the following command:

sudo apt-get install gnome-session-fallback

But when I tried it on the live CD session it came back and gave some message about it not being available.

Is there a simple way to do this without having to reinvent the wheel ?

Thanks.

---

### Post by raja.genupula on 2012-03-19
in a LIVE CD ? 

well try with this 
```
sudo apt-get install gnome-shell
```

---

### Post by wpshooter on 2012-03-19
> **raja.genupula said:**
> in a LIVE CD ? 

well try with this 
```
sudo apt-get install gnome-shell
```

I get the following:

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package gnome-shell is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source

E: Package 'gnome-shell' has no installation candidate

Which this basically the same thing that I got when I tried the command as shown in my original post.

Thanks.

---

### Post by jerrrys on 2012-03-19
Gnome-session-fallback, also known as gnome-classic is not the same as gnome-shell.  Installing gnome-shell will give you a completely different desktop.

You have the right command for installing "fallback", but you must install ubuntu to your computer.  A live session is limited to what it can do.

---

### Post by wpshooter on 2012-03-19
> **jerrrys said:**
> Gnome-session-fallback, also known as gnome-classic is not the same as gnome-shell.  Installing gnome-shell will give you a completely different desktop.

You have the right command for installing "fallback", but you must install ubuntu to your computer.  A live session is limited to what it can do.

Thanks, that is sort of what I was thinking BUT that does not help me very much, since I sort of like to look at a horse before I buy it !!!

---

### Post by cwklinuxguy on 2012-03-19
Desktop environments can be installed and uninstalled as you wish. Install a desktop, try it, and if it's not your cup of tea, remove it!! No biggie :)

You may also be interested in trying the [MATE Desktop Environment]("http://ubuntuforums.org/www.mate-desktop.org"), which is a fork of Gnome 2. It's still got some bugs in there and a few things that need polishing, but all the basic functionality is there.

---

### Post by jerrrys on 2012-03-19
> **wpshooter said:**
> Thanks, that is sort of what I was thinking BUT that does not help me very much, since I sort of like to look at a horse before I buy it !!!

I have not tried this, but I think a persistent install would work.

[http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=persistent+install&sa=Search&cof=FORID:9](http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=persistent+install&sa=Search&cof=FORID:9)

---

### Post by raja.genupula on 2012-03-19
> **jerrrys said:**
> Gnome-session-fallback, also known as gnome-classic is not the same as gnome-shell.  Installing gnome-shell will give you a completely different desktop.

You have the right command for installing "fallback", but you must install ubuntu to your computer.  A live session is limited to what it can do.

Hi Jerry small correction my friend 

[http://www.omgubuntu.co.uk/2011/10/gnome-shell-ubuntu-11-10-guide/](http://www.omgubuntu.co.uk/2011/10/gnome-shell-ubuntu-11-10-guide/)

@OP look at the link

---

### Post by jerrrys on 2012-03-19
Thankyou Raja :)

---

### Post by raja.genupula on 2012-03-20
> **jerrrys said:**
> Thankyou Raja :)

Welcome my friend :)

---

### Post by bumblestiltskin on 2012-04-03
I had a similar problem when trying out the 12.04 beta 2. I wanted to go try out the classic look of the gnome desktop. I was able to get it to work using a USB stick in Persistent mode. Here is how I got Gnome Fallback/Classic to work: 

Open Software Center

From the top panel/menu select "edit > Software Sources..."

From the "Ubuntu Software" tab check "(universe)" and "(multiverse)"

Click the "Close" button to close the Software Center

I don't know how to update sources from the Software Center, so I do it in the terminal

Click on "Dash Home" (top icon of the Unity dock)

In the search field, type "terminal"

Click on terminal to open

In the terminal enter:
```
sudo apt-get update
```

This will update Ubuntu with the Universe and Multiverse package list

From the terminal now enter:
```
sudo apt-get install gnome-session-fallback
```

It should tell you which packages are going to be installed and ask to continue. Enter "Y" to continue

After the install, you will need to log out and then choose Gnome Classic by clicking the arrow to the right of the login box.

Default user is "Ubuntu". Default password is blank -- just hit enter. You should then log into a Gnome 3 desktop that mimics the old Gnome 2 desktop. 

On my install, in order to change or remove items, I need to hold down the banner (windows key) + alt and then right click on the item I want to change. 

Hope this helps.

---

### Post by critin on 2012-04-03
> **wpshooter said:**
> How can I go about running/trying the Gnome interface on 12.04 LIVE CD ?

I found a reference to using the following command:

sudo apt-get install gnome-session-fallback

But when I tried it on the live CD session it came back and gave some message about it not being available.

Is there a simple way to do this without having to reinvent the wheel ?

Thanks.

When I installed 12.04 several weeks ago, I had the choice of several environments at log-in, gnome-classic among them.  I didn't have to install anything.

---

### Post by bumblestiltskin on 2012-04-04
> **critin said:**
> When I installed 12.04 several weeks ago, I had the choice of several environments at log-in, gnome-classic among them.  I didn't have to install anything.

I wonder if it's just the live cd/usb that doesn't install the classic environment.

---

### Post by critin on 2012-04-04
> **bumblestiltskin said:**
> I wonder if it's just the live cd/usb that doesn't install the classic environment.
  
Well, I downloaded the live and installed it--it was there.
I'd seen a post somewhere that Gnome classic was going to be one of several default options at log-in.  Was sure glad to see it.

Obviously-- you don't login on a live so there's no way to know.

---

### Post by critin on 2012-04-04
If no one else has it without adding something, I must have added something too without realizing it.

Today, I found in the Software Center an app called, "Launcher and docking facility for gnome".  (gnome panel) (installed)   I was searching a few weeks ago for something and probably installed this.  Anyway this turns out to be the "gnome panel" that brings in gnome classic.

You might want to check it out.

---

