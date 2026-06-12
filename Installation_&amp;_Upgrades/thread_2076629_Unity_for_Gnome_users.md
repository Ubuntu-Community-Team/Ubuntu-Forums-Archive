---
title: "Unity for Gnome users"
date: 2012-10-26
forum: Installation &amp; Upgrades
---

### Post by moonguide on 2012-10-26
Realizing that I need to migrate from 10.04 by next spring I have installed 12.04 on a second machine. I'm giving Unity a try and I'm slowly discovering how some things are done by trial and error.

Is there a guide for Gnome users on how to do things in Unity?

---

### Post by Cavsfan on 2012-10-26
You can also try out Gnome Classic. Once installed, you would select it at the login screen.

It pretty sweet if you like Gnome.

Just enter this in terminal:
```
sudo apt-get install gnome-session-fallback
```
Then reboot and select it before you login.

---

### Post by Cavsfan on 2012-10-26
In Unity you can type about anything in the Dash (top of Unity panel) to find anything.

---

### Post by moonguide on 2012-10-26
> **Cavsfan said:**
> You can also try out Gnome Classic. Once installed, you would select it at the login screen.

It pretty sweet if you like Gnome.

Just enter this in terminal:
```
sudo apt-get install gnome-session-fallback
```
Then reboot and select it before you login.

$ sudo apt-get install gnome-session-fallback
E: Could not get lock /var/lib/dpkg/loci - open (11: Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

The first thing I did when I logged in was to click on Dash Home. Then I typed "terminal", got three terminal icons, clicked on the first one, Terminal, (not UXTerm or XTerm), and then typed that command. I don't know what else could have a lock on the administration directory.

---

### Post by jocko on 2012-10-26
> **moonguide said:**
>  I don't know what else could have a lock on the administration directory.
Make sure you don't have any other package manager open (update manager/software central/synaptic).

---

### Post by moonguide on 2012-10-26
> **jocko said:**
> Make sure you don't have any other package manager open (update manager/software central/synaptic).

Shouldn't be. At least I hope no package manager can start up on its own right after I boot.

---

### Post by Cavsfan on 2012-10-26
> **moonguide said:**
> Shouldn't be. At least I hope no package manager can start up on its own right after I boot.

Yes, it will pop up to tell you have updates. When that happens to me. I open update manager and then close it.
And like jocko said make sure you don't have Synaptic Package manager or any other package managers open and try it again.

Because that is exactly what that error message mean.

I never use update manager.

I use **sudo apt-get update && sudo apt-get upgrade** any time I want to install updates.
Then if anything is held back. I enter **sudo apt-get dist-upgrade** and that will pull in a new kernel or other new files.

These can easily be made into a scripts by entering **gedit ~/.bashrc** in terminal and adding this to it towards the bottom:

```
# update aliases
alias ud='sudo apt-get update && sudo apt-get upgrade && sudo apt-get clean'
alias ud2='sudo apt-get dist-upgrade'
```

Then you just open terminal and enter **ud** and password to check for updates and **ud2** if anything is held back.

Just logout and backin for and then the scripts will work.

---

### Post by Frogs Hair on 2012-10-26
Here is a Unity guide and there are more available. I use the Gnome Shell as well as Unity and the Classic session is installed by default along with it if your interested.   [http://www.howtoforge.com/introduction-to-the-ubuntu-unity-desktop](http://www.howtoforge.com/introduction-to-the-ubuntu-unity-desktop)

---

### Post by moonguide on 2012-10-26
> **Cavsfan said:**
> Yes, it will pop up to tell you have updates. When that happens to me. I open update manager and then close it.
And like jocko said make sure you don't have Synaptic Package manager or any other package managers open and try it again.

Not sure how to make sure I don't have Synaptic open, so I went ahead and opened it and ran updates from there. Then I re-ran apt-get to get Gnome back, and this time it worked. While more familiar than Unity, it still does some things differently than 10.04. But I'll play with that awhile and see whether I prefer it.

It's not so much that I don't like Unity as it is trying to figure out how to do what I used to be able to do.

Thanks for the pointer.

---

### Post by moonguide on 2012-10-26
> **Frogs Hair said:**
> Here is a Unity guide and there are more available. I use the Gnome Shell as well as Unity and the Classic session is installed by default along with it if your interested.   [http://www.howtoforge.com/introduction-to-the-ubuntu-unity-desktop](http://www.howtoforge.com/introduction-to-the-ubuntu-unity-desktop)

That helps some. Thanks. I shall persevere.

---

### Post by Cavsfan on 2012-10-27
One thing to keep in mind is that when you are in Gnome Classic make sure in CCSM that the Ubuntu Unity Plugin is not checked.
If it is the Unity bar will still be there until you uncheck it. I just experienced that myself. 
I upgraded a 2nd install of Lucid 10.04 LTS to Precise 12.04 LTS last night and just now installed the gnome panel.

If you see compiz break or whatever, just logout and back in and it should  be fixed.

---

### Post by Frogs Hair on 2012-10-27
The guide posted goes back to 11.04. Here  are more .[http://idilix.net/ubuntu-tutorial](http://idilix.net/ubuntu-tutorial)

---

### Post by kurt18947 on 2012-10-27
At least the OP is willing to give the new UIs a fair shot.  That's a distinct improvement over what had seemed prevalent in the past where Ubuntugeddon was deemed imminent.  There is a project called MATE which reproduces the gnome 2  look & feel using gnome 3 underpinnings.   I've tried using it in Linux Mint.  I've used Gnome-shell for quite some time.  If I use Mate or Fallback I put the mouse cursor in the upper left corner or press the 'super' key.  Nothing happens.  What????  No search function.  What????  So yeah, it's a matter of what we're used to.

---

